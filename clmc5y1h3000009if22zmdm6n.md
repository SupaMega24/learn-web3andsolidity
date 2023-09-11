---
title: "Road2web3: NFT Smart Contract ERC721"
seoDescription: "Learning Solidity smart contracts and NFTs"
datePublished: Sat Sep 09 2023 15:10:37 GMT+0000 (Coordinated Universal Time)
cuid: clmc5y1h3000009if22zmdm6n
slug: road2web3-nft-smart-contract-erc721
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694271672933/d8afbadd-7330-47fd-b1a9-0acc71ccdb96.png
tags: learning, solidity, web3, nft

---

### **Overview**

In this reflection, I delve into the journey as an aspiring developer. I will share my review of challenge one from [Alchemy's Road to web3](https://docs.alchemy.com/docs/welcome-to-the-road-to-web3) as I venture into the fascinating world of blockchain and NFTs. Armed with curiosity and a desire to understand the technology behind the buzz, I will first reflect on my overall experience with the challenge. Then, I'll go through some new and challenging concepts and explain them to the best of my ability (remember, I'm still a noob). Finally, I'll break down the code used for my NFT.

### **Reflection**

1. Who are you, and what is your software development background?
    
    * My name is Charlie, and I'm an aspiring developer. I fell down this rabbit hole about a month ago while job searching. I noticed that a plethora of positions (even those not directly related to coding) were looking for people with an understanding of the technology. So, I decided to see what this was all about and genuinely fell in love. I am simply amazed by the future possibilities.
        
2. Why did you want to complete this lesson?
    
    * Other than the fact that it is the first on the list, I knew absolutely nothing about NFTs. Honestly, before I began this journey I believed they were a get-rich-quick scam. On the business side, this is debatable. However, development and technology are what really interest me.
        
3. When did you complete the project?
    
    * Today - September 9th, 2023
        
4. What technologies did you use?
    
    * Alchemy App, OpenZeppelin Contract Wizard, Remix, Replit, Opensea Testnets, MetaMask Wallet, Filebase, and ChatGPT.
        
5. What did you enjoy about the tutorial?
    
    * The tutorial was well structured and the video gave a bit more insight. I was able to use both text and video to help guide me through the process.
        
6. How do you think you can use this technology to build useful applications in the future? What are some specific example applications?
    
    * I've spent most of my professional life in education. Therefore, I'd love to be able to take what I've learned and apply it to the benefit of students. After completing these challenges, I plan to start my own project that will benefit immigrants and refugees. At the moment, I'm not sure how I'll use NFTs outside of badges and certificates along my learning paths. However, I'm sure further lessons will help me gain a deeper understanding of their potential uses. Perhaps they could be used for continuing education credits.
        
7. Who would you recommend this project to?
    
    * 100% I'm coming here from cryptoZombies. So far, I feel like this is the logical next step as it allows learners to start building and to get familiar with excellent tools such as OpenZeppelin.
        

### **New Concepts**

***OpenZeppelin Contract Wizard:***

[OpenZeppelin's Contract Wizard](https://docs.openzeppelin.com/contracts/4.x/wizard) is absolutely amazing! It is a helpful tool for simplifying the process of creating secure smart contracts by providing a user-friendly interface and templates for common contract functionalities. It allows you to customize contract parameters, deploy contracts to the Ethereum blockchain, and interact with them seamlessly while adhering to best practices in smart contract development.

***URI and URI Storage:***

You can think of URI as a link or address, and URI storage is where these links are securely stored within the smart contract to access important information, like the characteristics of unique tokens in the case of NFTs. Let's look a bit deeper.

**URI (Uniform Resource Identifier):**

* A URI is like a digital address or a link that helps you find something on the internet.
    
* Think of it as a web URL (Uniform Resource Locator) or a path to a specific resource, like a website, a file, or data stored somewhere.
    
* In Solidity, a URI is often used to point to external content, like metadata for tokens in NFTs (Non-Fungible Tokens).
    

**URI Storage:**

* URI storage refers to where the URI information is stored within a smart contract.
    
* It's like having a safe place in your contract where you keep the addresses (URIs) of important data or content.
    
* In the case of NFTs, the URI storage would hold the links to the metadata for each unique token, which might include details like the token's name, image, and other information.
    

Here are a few other concepts that I had to become more familiar with during this challenge. Some of them I've encountered before and am still learning, while others are new.

**Mintable:**

* "Mintable" means that new tokens or assets can be created or "minted" within a smart contract.
    
* It's often used with NFTs or other digital assets where new items can be generated over time, like collectible cards in a game.
    

**Enumerable:**

* "Enumerable" means you can count, list, or iterate through items in a structured way.
    
* It's often used for collections of items, like tokens, allowing you to list and retrieve items based on their unique identifiers.
    

**Constructor:**

* A `constructor` is a special function in a smart contract that runs only once when the contract is deployed.
    
* It's used to set initial values, perform setup tasks, or allocate resources for the contract.
    
* Think of it as the setup phase when you create a new instance of a contract.
    

**View Visibility:**

* `view` is a visibility modifier used for functions. Functions marked as "view" don't change the contract's state.
    
* They are read-only and don't modify any data, making them suitable for reading contract data without consuming gas.
    

**Metadata:**

* "Metadata" refers to additional information or descriptions associated with something.
    
* In smart contracts, metadata can include details about tokens, such as their name, symbol, image URL, or other attributes.
    
* Metadata is often used in NFTs to provide information about the token's content.
    

**Counters:**

* "Counters" are variables used to keep track of numbers or quantities within a smart contract.
    
* They're often employed to manage token IDs, track balances, or count occurrences of events.
    
* Think of counters as digital tally counters used to keep score or count items in the contract.
    

### **Code Breakdown**

Okay, let's break down this Solidity smart contract step by step:

1. **SPDX License Identifier and Pragma Directive:**
    
    ```solidity
    // SPDX-License-Identifier: MIT
    pragma solidity ^0.8.9;
    ```
    
    * The SPDX-License-Identifier at the top specifies the license under which the contract's source code is released. In this case, it's the MIT License, which is a permissive open-source license.
        
    * The `pragma solidity` statement defines the version of the Solidity compiler to be used. The caret (^) symbol means the contract is compatible with Solidity versions equal to or greater than 0.8.9.
        
2. **Imports:**
    
    ```solidity
    import "@openzeppelin/contracts@4.9.3/token/ERC721/ERC721.sol";
    import "@openzeppelin/contracts@4.9.3/token/ERC721/extensions/ERC721Enumerable.sol";
    import "@openzeppelin/contracts@4.9.3/token/ERC721/extensions/ERC721URIStorage.sol";
    import "@openzeppelin/contracts@4.9.3/access/Ownable.sol";
    import "@openzeppelin/contracts@4.9.3/utils/Counters.sol";
    import "@openzeppelin/contracts/utils/math/SafeMath.sol";
    ```
    
    * This contract imports several Solidity libraries from the OpenZeppelin project. These libraries provide pre-built and tested implementations of standard functions for ERC721 tokens, enumerable tokens, URI storage, access control, counting, and safe mathematical operations.
        
3. **Contract Inheritance:**
    
    ```solidity
    contract PieToken is ERC721, ERC721Enumerable, ERC721URIStorage, Ownable {
    ```
    
    * The `PieToken` contract is defined, inheriting from four other contracts: `ERC721`, `ERC721Enumerable`, `ERC721URIStorage`, and `Ownable`.
        
    * Inheritance allows `PieToken` to reuse the functionalities and variables defined in these parent contracts.
        
4. **Using Statements for Libraries:**
    
    ```solidity
    using Counters for Counters.Counter;
    using SafeMath for uint256;
    ```
    
    * The `using` statements allow the contract to use functions provided by the `Counters` and `SafeMath` libraries. These libraries are imported earlier and are used for counting and safe mathematical operations, respectively.
        
5. **State Variables:**
    
    ```solidity
    mapping(address => uint) public mintedCount;
    uint256 public maxMintPerUser = 5;
    ```
    
    * `mintedCount` is a public state variable that is a mapping, associating Ethereum addresses (users) with the number of tokens they have minted.
        
    * `maxMintPerUser` is a public state variable that sets the maximum number of tokens each user can mint, which is initially set to 5.
        
6. **Counters Counter and MAX\_SUPPLY:**
    
    ```solidity
    Counters.Counter private _tokenIdCounter;
    uint256 MAX_SUPPLY = 10000;
    ```
    
    * `_tokenIdCounter` is a private state variable from the `Counters` library. It is used to keep track of the token IDs as they are minted.
        
    * `MAX_SUPPLY` is a constant that defines the maximum supply of tokens allowed, set to 10,000 in this contract.
        
7. **Constructor:**
    
    ```solidity
    constructor() ERC721("PieToken", "PTK") {}
    ```
    
    * This is the constructor function. It is executed only once when the contract is deployed.
        
    * It calls the constructor of the parent `ERC721` contract and initializes the token's name as "PieToken" and symbol as "PTK."
        
8. **safeMint Function:**
    
    ```solidity
    function safeMint(address to, string memory uri) public {
    ```
    
    * `safeMint` is a public function that allows users to safely mint (create) new tokens.
        
    * It takes two parameters: `to` (the address of the recipient) and `uri` (a URI to associate with the minted token).
        
    
    ```solidity
        uint256 tokenId = _tokenIdCounter.current();
        require(tokenId <= MAX_SUPPLY, "I'm sorry, but all NFTs have been minted.");
        require(mintedCount[to].add(1) <= 5, "Exceeded user maximum mint limit.");
        _tokenIdCounter.increment();
        _safeMint(to, tokenId);
        _setTokenURI(tokenId, uri);
        mintedCount[to].add(1);
    }
    ```
    
    * It retrieves the current token ID, checks if it's within the allowed supply, and ensures the user hasn't exceeded their minting limit (5 tokens).
        
    * If the conditions are met, it increments the token ID counter, mints a new token to the recipient, associates the URI with the token, and increments the user's minting count.
        
9. **Overrides:**
    

The contract provides several override functions required by Solidity due to its inheritance from multiple parent contracts. These overrides ensure that the contract adheres to the ERC721 standard and its extensions:

\- `_beforeTokenTransfer`: A function called before a token transfer. - `_burn`: A function called to burn (destroy) a token. - `tokenURI`: A function to retrieve the URI of a token. - `supportsInterface`: A function to check which interfaces the contract supports.

This contract, `PieToken`, is an implementation of an ERC721 token with additional functionalities for limiting minting per user and handling metadata URIs for tokens. Users can mint tokens within the specified limit, and the contract enforces these restrictions while following the ERC721 standard.

### **Final Thoughts**

In conclusion, this journey has been enlightening, and I'm excited about the possibilities that lie ahead as I continue to explore the vast world of blockchain and smart contract development. As I am still learning, supporting and constructive criticism of any errors found in this post would be helpful. Thanks for your time!