# BookStore Smart Contract

## Overview

The `BookStore` smart contract is a Solidity-based smart contract designed to facilitate the management and purchase of books in a decentralized manner. It allows users to add new books to the store, purchase books, and query book prices and quantities. The contract also keeps track of the books purchased by each buyer.

## Features

- **Add New Books**: Add books to the store with a title, price, and quantity.
- **Purchase Books**: Buy books from the store, with automatic handling of payments and change.
- **Query Prices and Quantities**: Retrieve the price and available quantity of books.
- **Track Purchases**: Keep track of the number of books purchased by each address.

## Contract Functions

### `addBook(string memory _title, uint _price, uint _quantity)`

Adds a new book to the store with the specified title, price, and quantity.

- `_title`: The title of the book.
- `_price`: The price of the book in wei.
- `_quantity`: The quantity of the book available in stock.

**Modifiers**:
- Requires that `_price` and `_quantity` are greater than 0.

### `purchaseBook(string memory _title, uint _quantity)`

Allows users to purchase a specified quantity of a book.

- `_title`: The title of the book to purchase.
- `_quantity`: The quantity of the book to purchase.

**Modifiers**:
- Requires that the book is in stock and the buyer has sent enough funds.
- Adjusts stock and records the purchase.
- Refunds any excess funds sent by the buyer.

**Events**:
- Emits `BookPurchased` event when a purchase is made.

### `getBookPrice(string memory _title)`

Returns the price of the specified book.

- `_title`: The title of the book.

**Modifiers**:
- Requires that the book exists.

### `getBookQuantity(string memory _title)`

Returns the available quantity of the specified book.

- `_title`: The title of the book.

**Modifiers**:
- Requires that the book exists.

### `getNumberOfPurchasedBooks(address _buyer, string memory _title)`

Returns the number of books purchased by a specified address.

- `_buyer`: The address of the buyer.
- `_title`: The title of the book.

**Modifiers**:
- Requires that the buyer has purchased the book.

## Events

### `BookPurchased(address buyer, string title, uint quantity)`

Emitted when a book is purchased, including the buyer’s address, the book title, and the quantity purchased.

## Deployment

1. **Compile the Contract**: Use a Solidity compiler compatible with version 0.8.0 or later.
2. **Deploy**: Deploy the contract using a tool like HardHat, Remix, or Truffle.

## Example Usage

### Adding a Book

```solidity
bookStore.addBook("The Great Gatsby", 1 ether, 10);
