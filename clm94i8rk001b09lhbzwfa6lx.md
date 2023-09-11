---
title: "CryptoZombies: Lesson 5 Review"
seoDescription: "Learn Solidity basics"
datePublished: Thu Sep 07 2023 12:07:02 GMT+0000 (Coordinated Universal Time)
cuid: clm94i8rk001b09lhbzwfa6lx
slug: cryptozombies-lesson-5-review
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694088172053/45b19a7b-f2bd-4637-beff-b1e2b9f4b144.png
tags: learning, smart-contracts, solidity-basics

---

### **Overview**

In this lesson, I became more familiar with concepts that can be quite challenging, such as ERC-721 and ERC-20 tokens, logical operators like ||, indexed event parameters, overflows, underflows, and natspec documentation. These concepts form the backbone of blockchain development, enabling unique digital assets, fungible tokens, efficient event handling, and secure arithmetic operations. In this article, we'll break down each of these concepts into digestible pieces, along with a breakdown of the code. Let's dive in!

### **Challenging Concepts**

***ERC721:***

In essence, ERC-721 is a set of rules and functions that make it easy to create, trade, and prove ownership of unique digital assets on the Ethereum blockchain. Here is a brief overview:

1. **Tokens with Uniqueness**: Unlike cryptocurrencies like Ether (ETH), which are fungible (interchangeable), ERC-721 tokens are unique. Each ERC-721 token represents something distinct, like digital art, collectibles, or real estate.
    
2. **Ownership Proof**: ERC-721 tokens prove ownership of unique digital or physical items on the blockchain. When you own an ERC-721 token, it means you own a specific item, and this ownership is securely recorded on the blockchain.
    
3. **Indivisible**: You can't divide ERC-721 tokens. If you own a rare digital trading card as an ERC-721 token, you can't split it into smaller parts. It's like owning a physical collectible item; you can't cut it in half.
    
4. **Standardized Interface**: ERC-721 defines a standardized set of functions that any ERC-721 compliant contract must implement. This standardization allows different applications and platforms to work with ERC-721 tokens consistently.
    
5. **Use Cases**: ERC-721 tokens are used for various purposes, such as digital art marketplaces, virtual real estate ownership, unique in-game items, and more. They enable the creation of digital scarcity and provable ownership.
    

***ERC20:***

ERC-20 is a widely adopted standard for fungible tokens on the Ethereum blockchain. Let's break it down simply:

1. **Fungible Tokens**: ERC-20 tokens are fungible, meaning they are interchangeable on a one-to-one basis. If you have one ERC-20 token of a particular type, it's identical in value and function to another token of the same type.
    
2. **Standardized Interface**: ERC-20 defines a standardized set of functions that any ERC-20 compliant token contract must implement. This standardization ensures that different tokens can work seamlessly with various wallets, exchanges, and applications.
    
3. **Transfer of Value**: ERC-20 tokens are often used to represent value or utility within a blockchain application. They can be traded, sent, and received just like cryptocurrencies, such as Ether (ETH).
    
4. **Balance Tracking**: An ERC-20 token contract keeps track of the balances of all token holders. It knows who owns how many tokens, and these balances can change as transfers occur.
    
5. **Decimals**: ERC-20 tokens often include a decimal parameter, which defines how divisible the token can be. For example, a token with 18 decimal places can be divided into very small units, similar to how ETH can be divided into wei.
    
6. **Token Standard**: The ERC-20 standard provides a common framework for creating tokens, making it easier for developers to create new tokens and for users to understand how to interact with them.
    
7. **Use Cases**: ERC-20 tokens are used for various purposes, including Initial Coin Offerings (ICOs), stablecoins like USDT and DAI, and in-app currencies for decentralized applications (dApps).ds
    

***|| Logical OR:***

The `||` operator (logical OR) is used to combine two or more conditions and returns `true` if at least one of the conditions is `true`.

Here's a simple explanation:

* If you have two conditions separated by `||`, like `condition1 || condition2`, the result is `true` if either `condition1` is `true` or `condition2` is `true`, or if both are `true`.
    
* Think of it as a choice between two options. If at least one of the options is valid (true), then the overall result is valid (true).
    

For example:

* `chocolate || strawberry` is true if either chocolate is or strawberry is true, or if both strawberry and chocolate are true.
    

***Indexed:***

In the context of Ethereum and Solidity, the term `indexed` is used in relation to event parameters. An indexed event parameter can be efficiently searched for when filtering events.

Here's a breakdown:

* When an event is defined in a smart contract, you can mark certain parameters as "indexed." These parameters are usually used for filtering and searching events.
    
* Indexing a parameter makes it easier and faster to find specific events that match a particular value for that parameter.
    
* Think of it like an index in a book. If you want to find all occurrences of a specific word or topic in a book, you can use the index at the back of the book to quickly locate the relevant pages. Similarly, indexing event parameters helps you quickly find events with specific values.
    

For example, if you have an event that logs the purchase of items and you index the `_buyer` parameter, you can efficiently search for all purchases made by a specific buyer.

In short, indexing is a way to optimize event data for efficient searching and filtering, making it easier to find and analyze specific events within the Ethereum blockchain.

***Overflows and Underflows:***

Overflows and underflows occur when dealing with numbers that are too large or too small to be represented by the data type being used. Handling overflows and underflows is critical to ensure the security and integrity of the system, as incorrect handling can lead to unintended consequences, such as the loss of funds. Proper data type selection, bounds checking, and safe arithmetic operations are common strategies to prevent these issues.

Here's a simple explanation of each:

1. **Overflow:**
    
    * An overflow happens when a number exceeds the maximum value that can be stored in a data type.
        
    * Think of it as trying to pour more water into a glass than it can hold. The excess spills over, and you lose information.
        
    * In programming, this can lead to unexpected behavior, crashes, or even security vulnerabilities if not handled correctly.
        
2. **Underflow:**
    
    * An underflow occurs when a number becomes smaller than the minimum value represented by the data type.
        
    * It's like trying to take water out of a glass that's already empty; you can't take out more than what's there.
        
    * In programming, underflows can also lead to unexpected behavior and errors.
        

For example, if you're using an 8-bit unsigned integer (which can represent values from 0 to 255) and you add 1 to 255, you'll get an overflow because the result (256) is larger than what an 8-bit integer can hold. Similarly, subtracting 1 from 0 would result in an underflow.

***Natspec:***

Natspec, short for "Natural Specification," is a way to document and explain code in a human-readable format within Ethereum smart contracts. It helps developers and users understand the purpose and usage of smart contract functions. Here's a simple explanation:

* Natspec is like adding comments or documentation to your smart contract code in a way that's easy for humans to understand.
    
* It uses special comment tags like `@notice` and `@param` to provide information about what a function does, what its inputs are, and what it returns.
    
* Think of it as writing explanations in plain language right next to your code to make it clear and understandable, both for other developers who might work with your contract and for users who interact with it.
    

### ***Contract Updates:***

***zombiefeeding.sol:***

* changed modifier from `ownerOf` to `onlyOwnerOf`
    

***zombiefactory.sol:***

* added `SafeMath32` and `SafeMath16`
    

### **New Code Breakdown**

Alright, here is our final solidity code for our app! Let's take a deeper look at it.

**Import Statements**

```solidity
import "./zombieattack.sol";
import "./erc721.sol";
import "./safemath.sol";
```

* This block imports other Solidity contracts and libraries that are needed for this contract to work.
    
* `zombieattack.sol`, `erc721.sol`, and `safemath.sol` are being imported.
    

**Contract Definition**

```solidity
contract ZombieOwnership is ZombieAttack, ERC721 {
```

* This block defines the `ZombieOwnership` contract, which inherits from two other contracts, `ZombieAttack` and `ERC721`.
    
* It's important to note that Solidity allows contracts to inherit from other contracts to reuse their functionality.
    

**SafeMath Library**

```solidity
using SafeMath for uint256;
```

* This block includes the SafeMath library, which provides functions for safe arithmetic operations on `uint256` data types. It helps prevent overflows and underflows.
    

**Mapping**

```solidity
mapping (uint => address) zombieApprovals;
```

* Here, a mapping named `zombieApprovals` is declared. It associates zombie token IDs (of type `uint`) with addresses. This mapping is used to keep track of which addresses are approved to transfer specific zombie tokens.
    

`balanceOf` Function

```solidity
function balanceOf(address _owner) external view returns (uint256) {
    return ownerZombieCount[_owner];
}
```

* This block defines an external view function called `balanceOf`. It takes an address `_owner` as an argument and returns the number of zombies owned by that address.
    
* This function is part of the ERC721 standard, allowing external parties to query the token balance of a specific address.
    

`ownerOf` Function

```solidity
function ownerOf(uint256 _tokenId) external view returns (address) {
    return zombieToOwner[_tokenId];
}
```

* This block defines another external view function called `ownerOf`. It takes a `uint256` `_tokenId` as an argument and returns the address that owns the specified zombie token.
    
* This function is also part of the ERC721 standard and is used to determine the owner of a specific token.
    

`_transfer` Function

```solidity
function _transfer(address _from, address _to, uint256 _tokenId) private {
    ownerZombieCount[_to] = ownerZombieCount[_to].add(1);
    ownerZombieCount[msg.sender] = ownerZombieCount[msg.sender].sub(1);
    zombieToOwner[_tokenId] = _to;
    emit Transfer(_from, _to, _tokenId);
}
```

* This block defines a private function `_transfer`. It's used internally to transfer ownership of a zombie token from one address (`_from`) to another address (`_to`).
    
* It also updates the counts of zombies owned by both addresses and emits a `Transfer` event to notify external applications about the ownership change.
    
    * To clarify the above statement, the `.add(1)` and `.sub(1`) are from SafeMath and add and subtract 1 from the zombie counts.
        

`transferFrom` Function

```solidity
function transferFrom(address _from, address _to, uint256 _tokenId) external payable {
    require(zombieToOwner[_tokenId] == msg.sender || zombieApprovals[_tokenId] == msg.sender);
    _transfer(_from, _to, _tokenId);
}
```

* This block defines an external function `transferFrom`. It allows an address to transfer ownership of a zombie token from `_from` to `_to`, provided that the caller (`msg.sender`) is either the current owner or an approved address.
    
* It calls the internal `_transfer` function to perform the actual transfer.
    

`approve` Function

```solidity
function approve(address _approved, uint256 _tokenId) external payable onlyOwnerOf(_tokenId) {
    zombieApprovals[_tokenId] = _approved;
    emit Approval(msg.sender, _approved, _tokenId);
}
```

* This block defines another external function `approve`. It allows the owner of a zombie token to approve another address (`_approved`) to transfer that specific token.
    
* It also emits an `Approval` event to indicate the approval.
    

### **Final Thoughts**

This has been an amazing journey. The folks over at CryptoZombies have done a great job putting together a learning path to help me become more familiar and understanding of how smart contracts work. However, I likely won't be doing the sixth lesson on the front end. The reason for this is that I'd like to start building things now.

Good luck to you all in your journey.