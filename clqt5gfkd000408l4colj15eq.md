---
title: "Navigating the Blockchain Maze"
seoTitle: "Learn Solidity"
seoDescription: "Learn Solidity and Foundry"
datePublished: Sun Dec 31 2023 07:07:50 GMT+0000 (Coordinated Universal Time)
cuid: clqt5gfkd000408l4colj15eq
slug: navigating-the-blockchain-maze
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704005600464/20047fb0-f770-43d1-a5b2-da2636ca5c8f.png
tags: solidity, learn-coding, learning-journey

---

Hello, fellow blockchain wanderers! In this series, I'd like to take you on a quiet stroll through the realms of Solidity and Foundry. It's a journey filled with subtle nuances, where visibility, structs, mapping, and the mystical triad of memory, storage, and calldata gently beckon us to explore. It's also part of my personal learning experience through this course by Patrick Collins - [**Solidity Blockchain Developer Foundry Full Course 2023**](https://www.youtube.com/playlist?list=PL2-Nvp2Kn0FPH2xU3IbKrrkae-VVXs1vk)**.**

Let's dive into what I have learned so far. First, we will look at some of the key concepts. Then we will break down the code from the lesson.

## ***Key Concepts***

### **The Visibility Conundrum**

In the magical land of Solidity, visibility is the cloak that defines who can see and interact with our functions and variables. It's like the VIP section of a party, but with more blockchain jargon.

Imagine you're throwing a party in your smart contract, and you want certain functions to be exclusive to only the coolest addresses in town. That's where visibility comes in. Public, private, and internal are the bouncers controlling the access to your contract's VIP room. Public functions are the life of the party, private functions are backstage passes, and internal functions are the hidden gems accessible only to the contract's family members.

### **The Marvelous World of Structs**

Now, let's talk about structs – the superheroes of data organization in Solidity. Think of structs as the Avengers, each member having its own set of powers. These structured data types allow us to group related variables under a single name, making our code more organized and readable. Like Iron Man's suit, structs can hold various data types, creating a powerhouse of information.

For instance, if we were building a decentralized superhero registry, a struct could encapsulate the hero's name, powers, and favorite pizza topping all in one neat package. Now that's efficiency, even for caped crusaders!

### **Mapping: The Treasure Map of Solidity**

Ahoy, mateys! If structs are the Avengers, mapping is the treasure map guiding us to the loot. In Solidity, mapping is a powerful way to store key-value pairs. It's like having an X on the blockchain where you can dig up your precious data.

Picture a pirate's chest where each key opens a compartment filled with booty. Whether it's storing the balance of different wallets or mapping addresses to their corresponding superpowers, mapping is the go-to tool for navigating the vast seas of blockchain data.

### **Memory, Storage, and Calldata: The Trifecta of Ethereum Storage**

Now, let's dive into the trippy trio of memory, storage, and calldata – the storage realms where our data resides. These three are like the different rooms in our blockchain mansion, each serving a unique purpose.

Memory is the short-term memory of our functions – it's volatile and disappears when the function execution ends. Storage, on the other hand, is the permanent storage of our contract – the long-term memory where data is stored between function calls. Finally, calldata is the reading room where function arguments are stored during execution.

Think of it like ordering pizza. Memory is where you store the temporary craving for a slice, storage is where you keep the leftover pizza for future cravings, and calldata is the order slip the delivery person uses to know your toppings.

## ***Code Breakdown***

### **Overview**

The Solidity contract below is named `SimpleStorage`. It allows storing and retrieving of a favorite number, as well as adding people with their favorite numbers to a list and associating names with favorite numbers. There are several key components:

1. **State Variables**: The contract has a state variable `myFavNum` which is a `uint256` (unsigned integer of 256 bits). This variable is public, meaning it can be accessed from outside the contract. It is also initialized to 0.
    
2. **Struct**: The contract defines a struct named `Person`. A struct in Solidity is a custom data type that allows you to group together variables under one name. Here, the `Person` struct has two properties: `favNum` (`uint256`) and `name` (`string`).
    
3. **Dynamic Array**: The contract also declares a dynamic array of `Person` structs named `listOfPeople`. This array is also public.
    
4. **Mapping**: The contract uses a mapping to associate a `string` (the person's name) with a `uint256` (their favorite number). This mapping is also public.
    
5. **Functions**: The contract has three functions:
    

* `store`: This function takes a `uint256` as input and assigns it to `myFavNum`.
    
* `retrieve`: This function returns the value of `myFavNum`.
    
* `addPerson`: This function takes a `string` and a `uint256` as inputs, creates a new `Person` struct with these values, adds it to `listOfPeople`, and also adds the name-to-favorite number association to `nameToFavNum`.
    

Let's break down this Solidity smart contract step by step.

### **Breakdown**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

contract SimpleStorage {

    uint256 public myFavNum; // 0 initialized
```

In the first few lines, we define a Solidity contract named `SimpleStorage`. The `uint256 public myFavNum;` declares a public variable named `myFavNum` of type `uint256` (unsigned integer with 256 bits). The `public` keyword means that this variable is accessible from outside the contract, and it is automatically given a getter function.

```solidity
    struct Person {
        uint256 favNum;
        string name;
    }
```

Next, we define a structure (`struct`) named `Person`. It has two members: `favNum` (an unsigned integer) and `name` (a string). This structure will be used to represent individuals with their favorite numbers and names.

```solidity
    // Dynamic[] vs Static[n] arrays
    Person[] public listOfPeople;
```

Here, we declare a dynamic array `listOfPeople` that can store instances of the `Person` struct. It's dynamic because its size can change during execution. This array is made public, meaning it has an automatically generated getter function allowing external code to access it.

```solidity
    mapping(string => uint256) public nameToFavNum;
```

The `mapping` named `nameToFavNum` associates names (strings) with favorite numbers (uint256). This is a key-value store, where you can look up a person's name to find their favorite number. As with the other variables, this mapping is public, meaning there's a generated getter function.

```solidity
    function store(uint256 _favNum) public {
        myFavNum = _favNum;
    }
```

The `store` function allows someone to change the value of `myFavNum` by passing a new favorite number `_favNum`. The function is marked as `public`, making it callable from outside the contract.

```solidity
    function retrieve() public view returns (uint256) {
        return myFavNum;
    }
```

The `retrieve` function is a view function, meaning it doesn't modify the state of the blockchain. It simply returns the current value of `myFavNum`. This function is also marked as `public`.

```solidity
    function addPerson(string memory _name, uint256 _favNum) public {
        listOfPeople.push(Person(_favNum, _name));
        nameToFavNum[_name] = _favNum;
    }
}
```

Finally, the `addPerson` function allows for adding a new person to the `listOfPeople` array and updating the `nameToFavNum` mapping with their name and favorite number. The function is `public` and takes two parameters: `_name` (a string) and `_favNum` (an unsigned integer).

In summary, this Solidity contract is a simple storage and management system for people's favorite numbers and names, showcasing the usage of public variables, structs, dynamic arrays, and mappings.