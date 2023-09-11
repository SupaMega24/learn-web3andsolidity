---
title: "Basics of Smart Contracts"
datePublished: Sat Sep 09 2023 16:16:36 GMT+0000 (Coordinated Universal Time)
cuid: clmc8avve000008icgoi36nx6
slug: basics-of-smart-contracts
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694275180103/63a0e869-2b4c-48d3-84f7-dd20eb1366c2.png
tags: solidity, smart-contracts, learn-coding

---

# Understanding the Basics of Smart Contract Structure

Smart contracts are programs that run on the blockchain and encode business logic that executes when certain conditions are met. Let's discuss some of the basic code structures used in smart contract development. These explanations will be brief, but we'll dive deeper into them individually in upcoming posts.

## State Variables

```solidity
// Mapping to store account balances 
mapping(address => uint256) public balances;

// User defined struct to store data
struct User {
  uint id;
  string name;
}

// Array of User structs
User[] public users;
```

State variables are values that are permanently stored in contract storage. They are declared outside of functions at the contract level. Some examples:

* **Balances** - Used to store token or ETH balances for different addresses. Often declared as `mapping(address => uint256)`.
    
* **Structs** - Custom data types that group variables together. Useful for storing related data.
    
* **Mappings** - Key-value store that maps keys to values. Used for storing and looking up data.
    

State variables hold their value between function calls. They make up the contract's persistent state.

## Functions

```solidity
// Public function
function deposit() public payable {
  balances[msg.sender] += msg.value;
}

// Private function 
function _transfer(address from, address to, uint amount) private {
  //...
}

// View function (doesn't modify state)
function getBalance(address addr) public view returns (uint) {
  return balances[addr];
}

// Pure function (doesn't access state)
function add(uint x, uint y) pure public returns (uint) {
  return x + y;
}
```

Functions contain the logic that gets executed when a transaction invokes the contract. They can read and modify state variables.

Some function types:

* **Public** - Can be called externally by users or other contracts.
    
* **Private** - Can only be called within the contract.
    
* **View** - Read-only, don't modify state.
    
* **Pure** - Compute, but don't read/modify state.
    

## Constructors

```solidity
// Constructor
constructor() {
  owner = msg.sender;
}
```

Constructors are special functions that initialize contract state when deployed. They set starting values for state variables.

Constructors run only once when the contract is first deployed to the blockchain. Useful for setup logic.

## Events

```solidity
// Transfer event 
event Transfer(address indexed from, address indexed to, uint amount);
```

Events emit log information that external applications can listen for and act on.

They don't modify state, but notify listeners that something happened. For example, a `Transfer` event in an ERC20 token.

## Modifiers

```solidity
// Restrict access modifier
modifier onlyOwner() {
  require(msg.sender == owner);
  _;
}

function withdraw(uint amount) onlyOwner public {
   // Code here executes after modifier
}
```

Modifiers are reusable chunks of code that can execute before/after a function. They can:

* Restrict access (require sender to be contract owner)
    
* Validate inputs
    
* Guard against reentrancy hacks
    

Useful for encapsulating common logic and applying protections to functions.

## Inheritance

```solidity
import "./ERC20.sol"; 

contract MyToken is ERC20 {
  // Inherits ERC20 functions and state
}
```

Contracts can inherit variables and functions from other contracts by using the `is` keyword.

For example, many tokens inherit from the OpenZeppelin ERC20 implementation.

This allows for code reuse and extension.

## Libraries

```solidity
library Math {
  function divide(uint x, uint y) internal pure returns (uint) {
    require(y > 0);
    return x / y; 
  }
}

contract MyContract {
  using Math for uint;
  // Can call `num.divide(y)`
}
```

Libraries are reusable contracts that contain logic that can be shared between multiple contracts.

They help avoid code duplication. For example, a Math library for safe math operations.

# Conclusion

These are some of the core components that make up a contract's structure and logic in Solidity. By understanding these building blocks, we can start architecting more complex smart contracts. I will be expanding on these components in future posts as I learn more about them.