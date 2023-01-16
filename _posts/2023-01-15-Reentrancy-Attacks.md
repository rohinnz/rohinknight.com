---
layout: post
title:  "How to Prevent Reentrancy Attacks in Solidity"
date:   2023-01-15 17:00:00 +1300
categories: solidity
---
A reentrancy attack is where an attacker is able to exploit a smart contract by called a function and then calling that same function again before the first call to that function has finished.

This is attack is performed by the attacker deployig their own smart contract with a fallback() function.

In the following example, the fallback() function on the Attack contract is called whenever eth is sent to the the contract. This call happens before the Bank contract can update the sender's balance.
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;

// Vulnerable contract - reentrancy attack is possible
contract Bank1 {
    mapping(address => uint256) internal _balances;

    function deposit() external payable {
        _balances[msg.sender] += msg.value;
    }

    function withdraw() external {
        uint256 balance = _balances[msg.sender];

        (bool sent, ) = msg.sender.call{value: balance}("");
        require(sent, "withdraw failed");

        _balances[msg.sender] = 0;
    }
}

contract Attack {
    Bank private bank;

    constructor(address bankAddress) {
        bank = ABank(bankAddress);
    }

    fallback() external payable {
        if (address(bank).balance >= 0.01 ether) {
            bank.withdraw();
        }
    }

    function attack() external payable {
        bank.deposit{value: msg.value}();
        bank.withdraw();
    }
}
```

There are two ways to prevent a reentrancy attack: 
1. Reentrancy Guard
2. CEI (Checks, Effects, Interactions) Pattern

**Reentrancy Guard**

With the reentrancy guard, reentrant calls to the function are prevented when a flag is set. This flag is set at the start of the function and removed at the end.

Example reentrancy guard modifier:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;

contract ReentrancyGuard {
    bool internal _locked;

    modifier nonReentrant() {
        require(!_locked, "Reentrancy forbidden");
        _locked = true;
        _;
        _locked = false;
    }
}
```

If you need to use a Reentrancy Guard, it is best to use the [Open Zeppelin Reentrancy Guard](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/security/ReentrancyGuard.sol) because it is cheaper on gas.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;

import "@openzeppelin/contracts/security/ReentrancyGuard.sol";

// Contract using Reentrancy Guard
contract Bank2 is ReentrancyGuard {
    mapping(address => uint256) internal _balances;

    function deposit() external payable {
        _balances[msg.sender] += msg.value;
    }

    function withdraw() external nonReentrant {
        uint256 balance = _balances[msg.sender];

        (bool sent, ) = msg.sender.call{value: balance}("");
        require(sent, "withdraw failed");

        _balances[msg.sender] = 0;
    }
}
```

**CEI Pattern**

With the CEI (Checks, Effects, Interactions) pattern, we only send the ETH at the end of the function after we've done all
the updates. This appraoch uses less gas than the Reentrancy Guard.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;

// Contract using CEI (Checks, Effects, Interactions) pattern
// Attackers balance updated before ETH is sent
contract Bank3 {
    mapping(address => uint256) internal _balances;

    function deposit() external payable {
      _balances[msg.sender] += msg.value;
    }

    function withdraw() external {
        uint256 balance = _balances[msg.sender];
        _balances[msg.sender] = 0;

        (bool sent, ) = msg.sender.call{value: balance}("");
        require(sent, "withdraw failed");
    }
}

```


**Contract Tests**

We can test these contracts using [Hardhat](https://hardhat.org/). The full source code for these examples is avaialble here:<br />[github.com/rohinnz/Solidity-Reentrancy-Attack-Example](https://github.com/rohinnz/Solidity-Reentrancy-Attack-Example)

In the following tests, the attacker is able to steal all the ETH from Bank1 by just depositing 0.01 ETH and then calling withdraw() multiple times.

For Bank2 and Bank3, the attacker is unable to steal any ETH.
```typescript
import { expect } from "chai";
import { ethers } from "hardhat";
import { Contract } from "ethers";

describe("Banks", function () {
  const ONE_ETH = ethers.utils.parseEther("1");

  async function setupBank(bankName: string): Promise<Contract> {
    const Bank = await ethers.getContractFactory(bankName);
    const bank = await Bank.deploy();
    await bank.deployed();
    
    // Deposit 1 ETH and confirm
    bank.deposit({value: ONE_ETH});
    return bank;
  }

  async function setupAttack(bank: Contract): Promise<Contract> {
    const [_, otherAccount] = await ethers.getSigners();
    const Attack = await ethers.getContractFactory("Attack");
    const attack = await Attack.connect(otherAccount).deploy(bank.address);

    await attack.deployed();
    return attack;
  }

  it("Attack Bank 1", async function () {
    const bank = await setupBank("Bank1");
    const attack = await setupAttack(bank);

    await attack.attack({ 
      value: ethers.utils.parseEther("0.01")
    });

    // Confirm attack was successful
    expect(await bank.provider.getBalance(bank.address)).to.equal(0);
  });

  // Bank 2 uses reentrancy guard
  it("Attack Bank 2", async function () {
    const bank = await setupBank("Bank2");
    const attack = await setupAttack(bank);

    await expect(attack.attack({ 
      value: ethers.utils.parseEther("0.01")
    })).to.be.revertedWith("withdraw failed");

    // Confirm attack failed
    expect(await bank.provider.getBalance(bank.address)).to.equal(ONE_ETH);
  });

  // Bank 3 uses CEI (Checks, Effects, Interactions) pattern
  it("Attack Bank 3", async function () {
    const bank = await setupBank("Bank3");
    const attack = await setupAttack(bank);

    await expect(attack.attack({ 
      value: ethers.utils.parseEther("0.01")
    })).to.be.revertedWith("withdraw failed");

    // Confirm attack failed
    expect(await bank.provider.getBalance(bank.address)).to.equal(ONE_ETH);
  });
});
```
