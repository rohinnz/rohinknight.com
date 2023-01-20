---
layout: post
title: "Optimizing Smart Contract Gas Costs"
date: 2023-01-20 21:00:00 +1300
categories: solidity
---

In this example we are going to optimize a solidity function that calculates the total of all values in the array.

The execution cost is currently 55,541 gas.

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
## Fix #1 - Write to storage once

The storage variable *total* is being updated in every iteration of the for loop.

Writing to memory is cheaper than writing to storage, so we should calculate the total in memory first and then assign it to storage at the end.

This saves 2207 gas.

```solidity
  function updateTotalV2() external { // gas: 53,334
    uint256 newTotal = 0;

    for (uint256 i = 0; i < array.length; i++) {
      newTotal += array[i];
    }

    total = newTotal;
    require(total == 55);
  }

```
## Fix #2 - Cache array length

It is cheaper to read from memory than storage. We should store the array length in a variable and read that in each iteration of the for loop instead.

This saves an extra 1110 gas.

```solidity
  function updateTotalV3() external { // gas: 52,224 
    uint256 arrayLength = array.length;
    uint256 newTotal = 0;

    for (uint256 i = 0; i < arrayLength; i++) {
      newTotal += array[i];
    }

    total = newTotal;
    require(total == 55);
  }
  
```

## Fix #3 - Use unchecked for addition
If we know that addition to *newTotal* and *i* will not overflow, we can remove the overflow checks by wrapping them in an unchecked block.

This saves an extra 2954 gas.

```solidity
  function updateTotalV4() external { // gas: 49,270 
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

## Fix #4 - Use pre-increment for i

Pre-increment is cheaper than post-increment

This will save an extra 117 gas.

```solidity
  function updateTotalV5() external { // gas: 49,153 
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

## Fix 5 - Remove array bounds checking

The last fix we can do is remove array bounds checking.
To do this we need to access the array elements using [Yul](https://docs.soliditylang.org/en/v0.8.17/yul.html).

This will save an additional 1443 gas.

```solidity
  // Remove array bounds check
  function updateTotalV7() external { // gas: 47,710 
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

## Why not remove the explicit zero initializations?

I have read some suggestions that removing the explicit zero initialization for memory variables can also save gas because memory variables will always be initialized to zero by default.

However, when I tested removing the zero assignemnts for *newTotal* and *i*, it appears to actually increased the gas consumtion by 8.

```solidity
  function updateTotalV7() external { // gas: 47,718 
    uint256 arraySize = array.length;
    uint256 newTotal;
    uint256 arraySlot;

    assembly {
      arraySlot := array.slot
    }

    bytes32 location = keccak256(abi.encode(arraySlot));

    for (uint256 i; i < arraySize; ) {
      assembly {
        newTotal := add(newTotal, sload(add(location, i)))
      }
      unchecked {
        ++i;
      }
    }

    total = newTotal;
    require(total == 55);
  }
```
