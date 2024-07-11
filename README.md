# Function-and-Error-
# Solidity Smart Contract Example

This repository contains a simple smart contract written in Solidity. The contract demonstrates the use of `require()`, `assert()`, and `revert()` statements to handle errors and enforce conditions within the Ethereum blockchain environment.

## Table of Contents

1. [Introduction](#introduction)
2. [Contract Overview](#contract-overview)
3. [Functions and Modifiers](#functions-and-modifiers)
   - [Constructor](#constructor)
   - [Modifiers](#modifiers)
   - [Functions](#functions)
4. [Error Handling](#error-handling)
   - [require()](#require)
   - [assert()](#assert)
   - [revert()](#revert)
5. [License](#license)
6. [Acknowledgments](#acknowledgments)

## Introduction

This Solidity smart contract example illustrates the basic use of Solidity's built-in error handling mechanisms: `require()`, `assert()`, and `revert()`. These are crucial for ensuring the security and reliability of smart contracts.

## Contract Overview

The contract, `ExampleContract`, includes functionalities for depositing and withdrawing Ether, and demonstrates how to use Solidity's error handling functions. The contract has two state variables:

- `owner`: the address of the contract owner.
- `balance`: the balance of the contract.

## Functions and Modifiers

### Constructor

The constructor sets the `owner` to the address that deploys the contract.

```solidity
constructor() {
    owner = msg.sender;
}
```
Modifiers
onlyOwner
This modifier restricts access to certain functions to only the owner of the contract.

```solidity
modifier onlyOwner() {
    require(msg.sender == owner, "Not the contract owner");
    _;
}
```

Functions
`deposit`
Allows users to deposit Ether into the contract. It requires the sent value to match the specified amount.

```solidity
function deposit(uint256 amount) public payable {
    require(msg.value == amount, "Sent value does not match the specified amount");
    balance += amount;
}
```
`withdraw`
Allows the owner to withdraw Ether from the contract. It ensures there is sufficient balance before proceeding.

```solidity
function withdraw(uint256 amount) public onlyOwner {
    require(amount <= balance, "Insufficient balance");
    balance -= amount;
    payable(owner).transfer(amount);
}
```
`testAssert`
Demonstrates the use of assert() to check conditions that should always be true.

```solidity

function testAssert() public view {
    assert(balance >= 0);
}
```
`testRevert`
Demonstrates the use of revert() to forcefully revert a transaction with a custom error message.

```solidity

function testRevert() public pure {
    revert("This is a forced revert");
}
```
# Error Handling
require()
Used to validate inputs and conditions. If a condition is not met, the transaction is reverted with an error message.

assert()
Used to check for conditions that should never be false. If the condition is false, the transaction is reverted and all gas is consumed.

revert()
Explicitly reverts a transaction with an optional error message.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments
Solidity Documentation
Truffle Suite
OpenZeppelin for their extensive library and guides on secure smart contract development.
