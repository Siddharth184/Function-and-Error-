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
5. [Setup and Deployment](#setup-and-deployment)
   - [Prerequisites](#prerequisites)
   - [Installation](#installation)
   - [Compiling and Deploying](#compiling-and-deploying)
   - [Interacting with the Contract](#interacting-with-the-contract)
6. [License](#license)
7. [Acknowledgments](#acknowledgments)

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

**Modifiers
onlyOwner
This modifier restricts access to certain functions to only the owner of the contract.**

modifier onlyOwner() {
    require(msg.sender == owner, "Not the contract owner");
    _;
}

