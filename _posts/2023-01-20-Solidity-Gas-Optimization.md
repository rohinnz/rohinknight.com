---
layout: post
title: "Optimizing Smart Contract Gas Costs"
date: 2023-01-20 21:00:00 +1300
categories: solidity
---

In this example we are going to optimize a solidity function that calculates the total of all values in the array. The full source code is available [here](https://gist.github.com/rohinnz/82d5d162829e2707891ce04742ae33d8).

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;

contract Totals {
  uint256[] internal array;
  uint256 public total;

  constructor() {
    array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  }

  function updateTotal() external { // gas: 55,541
    total = 0;

    for (uint256 i = 0; i < array.length; i++) {
      total += array[i];
    }

    require(total == 55);
  }
}
```

If we execute the *updateTotal* function in [Remix](https://remix.ethereum.org/) we will find it has an execution cost of 55,541 gas.

There are five optimizations we can make to get the execution cost down to 47,718 gas.

## Optimization #1 - Write to storage once

The storage variable *total* is being updated in every iteration of the for loop.

Writing to memory is cheaper than writing to storage, so we should calculate the total in memory first and then assign it to storage at the end.

This saves 2207 gas.

```solidity
  function updateTotal() external { // gas: 53,334
    uint256 newTotal = 0;

    for (uint256 i = 0; i < array.length; i++) {
      newTotal += array[i];
    }

    total = newTotal;
    require(total == 55);
  }

```
## Optimization #2 - Cache array length

It is cheaper to read from memory than storage. We should store the array length in a variable and read that in each iteration of the for loop instead.

This saves an extra 1110 gas.

```solidity
  function updateTotal() external { // gas: 52,224 
    uint256 arrayLength = array.length;
    uint256 newTotal = 0;

    for (uint256 i = 0; i < arrayLength; i++) {
      newTotal += array[i];
    }

    total = newTotal;
    require(total == 55);
  }
  
```

## Optimization #3 - Use unchecked for addition
Since solidity 0.8.0, the compiler automatically adds checks for interger overflow and underflow and throws an exception if they occur.

Because we are confident *newTotal* and *i* will not overflow, we can remove these checks by wrapping them in an unchecked block.

This saves an extra 2954 gas.

```solidity
  function updateTotal() external { // gas: 49,270 
    uint256 arraySize = array.length;
    uint256 newTotal = 0;

    for (uint256 i = 0; i < arraySize; ) {
      unchecked {
        newTotal += array[i];
        i++;
      }
    }

    total = newTotal;
    require(total == 55);
  }

```

## Optimization #4 - Use pre-increment for i

Pre-increment is cheaper than post-increment.

This will save an extra 117 gas.

```solidity
  function updateTotal() external { // gas: 49,153 
    uint256 arraySize = array.length;
    uint256 newTotal = 0;

    for (uint256 i = 0; i < arraySize;) {
      unchecked {
        newTotal += array[i];
        ++i;
      }
    }

    total = newTotal;
    require(total == 55);
  }

```

## Optimization #5 - Remove array bounds checking

The last fix we can do is remove array bounds checking. To do this we need to access the array elements using [Yul](https://docs.soliditylang.org/en/v0.8.17/yul.html).

This will save an additional 1443 gas.

```solidity
  // Remove array bounds check
  function updateTotal() external { // gas: 47,710 
    uint256 arraySize = array.length;
    uint256 newTotal = 0;
    uint256 arraySlot;

    assembly {
      arraySlot := array.slot
    }

    // Solidity stores the elements for dynamic storage arrays
    // at the keccak256 location of the array's slot.
    // This is so the array can be expanded without colliding
    // with other storage data.
    bytes32 arrayLocation = keccak256(abi.encode(arraySlot));

    for (uint256 i = 0; i < arraySize; ) {
      assembly {
        newTotal := add(newTotal, sload(add(arrayLocation, i)))
      }
      unchecked {
        ++i;
      }
    }

    total = newTotal;
    require(total == 55);
  }
}
```

## Q&A
### Why not remove the explicit zero initializations?

I have read some suggestions that removing the explicit zero initialization for memory variables can also save gas because memory variables will always be initialized to zero by default.

This is not correct, but may appear to be if using the wrong test. E.g.
```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.17;

contract AssignZeroTest {
  function assignZeroV1() external { // gas: 21,186
      uint256 value;
  }

  function assignZeroV2() external { // gas: 21,208 
      uint256 value = 0;
  }
}
```

The above test is flawed because it does not take into account the gas cost to lookup a function. If you swap the function names you'll then find the gas costs are also swapped.

The Solidity compiler creates a hash of each function using the keccak256 and then stores the first four bytes of that hash in the assembly as the function selector. The underlying assembly for looking up a function is basically checking if a function selector matches the hash and if not then moving to comparing the next.

If we now write this test the correct way, both functions will return the same gas cost:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.17;

contract AssignZeroTestV1 { // gas: 21,186 
  function assignZeroV1() external {
      uint256 value = 0;
  }
}

contract AssignZeroTestV2 { // gas: 21,186 
  function assignZeroV2() external {
      uint256 value = 0;
  }
}
```
