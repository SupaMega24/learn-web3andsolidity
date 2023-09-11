---
title: "CryptoZombies: Lesson 2.1 Review"
seoTitle: "JavaScript and Solidity for Cryptozombies"
seoDescription: "In this review, we look at the JavaScript code given at the end of cryptozombies lesson 2 and how the code compares to Solidity."
datePublished: Sat Sep 02 2023 05:07:22 GMT+0000 (Coordinated Universal Time)
cuid: clm1kba1m000c09l2dt7e4r3o
slug: cryptozombies-lesson-21-review
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693631092048/48c460e7-6d31-4039-ae2f-51e89fda4625.png
tags: javascript, solidity, web3, learn-coding, solidity-basics

---

### **Overview:**

The use of JavaScript and the web3.js library is related to blockchain development, specifically for interacting with the Ethereum blockchain. Here's what these components typically imply:

1. **JavaScript** is a versatile programming language commonly used for web development. In this context, it could be used on the front-end (in a web browser) or on the back-end (using Node.js) for blockchain-related tasks.
    
2. **web3.js** is a popular JavaScript library specifically designed for interacting with Ethereum blockchain smart contracts and the Ethereum network. It provides a set of tools and APIs to send transactions, query data from the blockchain, and work with Ethereum smart contracts. web3.js is commonly used for both front-end and back-end development in Ethereum-related projects.
    

Given this information, the code provided by [Cryptozombies](https://cryptozombies.io/en/course) is most likely part of a larger web application that interacts with the Ethereum blockchain using web3.js. Depending on the specific use case and architecture of the application, this code could be integrated into the front-end (web browser) or back-end (Node.js server) to enable Ethereum blockchain interactions and handle related tasks. Let's break down the code to try and understand it better.

### **JavaScript Terms I Learned:**

The following terms from the code are new to me, so I thought I'd do a bit more digging to learn more. That way we can understand them more clearly when we dive into the code breakdown and how these terms compare with Solidity.

***var and let:***

While JavaScript's `var` and `let` keywords and Solidity have some similarities in terms of variable declarations, they are fundamentally different languages designed for different purposes. Here's how they compare to variable declarations in Solidity:

1. **Variable Declaration**:
    
    * **JavaScript (var)**: In JavaScript, `var` is used to declare variables that can hold different types of data, including numbers, strings, objects, and more. JavaScript is a dynamically typed language, so the data type of a `var` variable can change during runtime.
        
    * **JavaScript (let)**: In JavaScript, `let` is used to declare variables that can hold different types of data, just like `var`. However, variables declared with `let` have block scope, which means they are limited to the nearest enclosing pair of curly braces `{}`.
        
    * **Solidity**: In Solidity, you declare variables using specific data types like `uint`, `string`, `address`, etc. Solidity is a statically typed language, meaning variable types are defined at compile time and cannot change during execution.
        
2. **Scope**:
    
    * **JavaScript (var)**: Variables declared with `var` have function or global scope, depending on where they are declared. They are not block-scoped, meaning they are not limited to the nearest enclosing pair of curly braces `{}`.
        
    * **JavaScript (let)**: Variables declared with `let` have block scope, meaning they are limited to the block (within curly braces) where they are declared. This provides better isolation and prevents unintentional variable shadowing.
        
    * **Solidity**: Solidity variables can have different types of scope:
        
        * State variables: Stored on the Ethereum blockchain and have global scope across all functions in a contract.
            
        * Local variables: Limited to the function or block where they are declared.
            
3. **Hoisting**:
    
    * **JavaScript (var)**: Variables declared with `var` are hoisted to the top of their function or global context during execution, meaning their declarations are moved to the top before code execution.
        
    * **JavaScript (let)**: Variables declared with `let` are also hoisted to the top of their block scope but are not initialized. This means they are not accessible before the point in the code where they are declared.
        
    * **Solidity**: Solidity does not have the concept of hoisting, as it is not relevant to blockchain smart contracts.
        
4. **Typing**:
    
    * **JavaScript (var and let)**: JavaScript is dynamically typed, which means that `var` and `let` can change their data type during runtime. This flexibility can lead to unexpected behavior if not carefully managed.
        
    * **Solidity**: Solidity is statically typed, meaning variable types are explicitly defined and cannot change during execution. This provides greater predictability and safety in smart contract development.
        

In summary, while both JavaScript and Solidity involve variable declarations, their similarities are mostly superficial. The key differences lie in their type systems, scope rules, and intended use cases.

***web3.eth:***

In general, `web3.eth` in JavaScript is a part of the Web3.js library and is used to interact with the Ethereum blockchain, while Solidity is a smart contract programming language that is used to write the logic of smart contracts that run on the Ethereum blockchain. These two components serve different purposes in the Ethereum ecosystem, with `web3.eth` being the interface for off-chain interactions and Solidity being the language for on-chain smart contract development. Here's how they compare:

1. `web3.eth` in JavaScript:
    
    * **Purpose**: In JavaScript, `web3.eth` is part of the Web3.js library, which provides a JavaScript interface for interacting with the Ethereum blockchain. `web3.eth` offers a wide range of functionalities for interacting with the Ethereum network, including querying blockchain data, sending transactions, managing accounts, and more.
        
    * **Usage**: Developers use `web3.eth` to connect to an Ethereum node (local or remote) and perform various blockchain-related tasks. For example, you can use it to send Ether, query the balance of an Ethereum address, call smart contract functions, and listen for blockchain events.
        
2. `web3.eth` Counterpart in Solidity:
    
    * **Purpose**: In Solidity, there is no direct equivalent to `web3.eth` because Solidity is a programming language specifically designed for writing smart contracts that run on the Ethereum Virtual Machine (EVM). Solidity smart contracts are deployed on the Ethereum blockchain and contain code that can be executed when transactions are sent to them.
        
    * **Usage**: In Solidity, you define state variables, functions, and events within smart contracts. These smart contracts can interact with the Ethereum blockchain's state and execute logic based on transactions and messages sent to them. While Solidity can read blockchain state variables and emit events, it does not have the capabilities of a JavaScript library like `web3.eth` for connecting to the Ethereum network.
        

***$.get:***

In JavaScript, `$.get` is a mechanism for making HTTP GET requests to external resources, while Solidity is a smart contract programming language that operates within the Ethereum blockchain environment. These two components serve different purposes: `$.get` is for off-chain HTTP interactions, whereas Solidity is for on-chain smart contract development and execution.

Let's compare the usage of `$.get` in JavaScript to its counterpart in Solidity:

1. `$.get` **in JavaScript**:
    
    * **Purpose**: `$.get` is typically used in JavaScript with libraries like jQuery or Axios(I'm not familiar with these yet, but I believe we will need jQuery when we do front end) to make HTTP GET requests to external resources, such as web APIs or servers. It allows you to retrieve data from external sources and handle the response in your JavaScript code.
        
    * **Usage**: You use `$.get` to send a GET request to a specified URL and provide a callback function to process the data returned by the request. This is commonly used for fetching data from web services, loading content dynamically, or interacting with external APIs.
        
2. **Counterpart in Solidity**:
    
    * **Purpose**: In Solidity, there is no direct equivalent to `$.get` because Solidity is a language for writing smart contracts on the Ethereum blockchain. Solidity contracts operate on the blockchain's decentralized and immutable ledger and do not make HTTP requests to external sources.
        
    * **Usage**: Solidity contracts define smart contract logic, state variables, and functions. They can receive transactions and messages from external parties and execute code based on predefined rules. Solidity contracts can read data from the blockchain's state and perform computations within the EVM but do not interact with external APIs or web services directly.
        

### **Code Breakdown:**

Okay, let's try to break down the provided JavaScript code block by block:

```javascript
// Define the ABI (Application Binary Interface) of the smart contract.
var abi = /* abi generated by the compiler */

// Create a contract instance using web3.js, specifying the ABI.
var ZombieFeedingContract = web3.eth.contract(abi);

// Provide the Ethereum address of the deployed contract.
var contractAddress = /* our contract address on Ethereum after deploying */

// Create an instance of the contract at the specified address.
var ZombieFeeding = ZombieFeedingContract.at(contractAddress);
```

* The code begins by defining the ABI (Application Binary Interface) of a smart contract. The ABI describes the methods and data structures of the contract. The actual ABI content is not provided in the code and should be generated by a Solidity compiler or obtained from the contract's source code.
    
* It creates a contract instance using web3.js. `web3.eth.contract(abi)` is used to create an instance of the contract by specifying its ABI. This instance allows interactions with the contract's functions.
    
* Here, you should provide the Ethereum address of the deployed smart contract. The contract instance (`ZombieFeeding`) will interact with the contract at this address.
    

```javascript
// Define zombie and kitty IDs.
let zombieId = 1;
let kittyId = 1;

// Construct the API URL to fetch data about a CryptoKitty.
let apiUrl = "https://api.cryptokitties.co/kitties/" + kittyId;

// Send an HTTP GET request to the CryptoKitties API.
$.get(apiUrl, function(data) {
    // Handle the API response in this callback.
    let imgUrl = data.image_url;
    // Do something to display the image.
});
```

* The code defines `zombieId` and `kittyId`, which appear to be IDs for a zombie and a CryptoKitty, respectively.
    
* It constructs the API URL used to fetch data about a CryptoKitty. The `kittyId` is appended to the base URL of the CryptoKitties API.
    
* The code sends an HTTP GET request to the CryptoKitties API using `$.get()`. It specifies a callback function to handle the API response, which contains data about the CryptoKitty.
    

```javascript
// Set up a click event handler for elements with class "kittyImage".
$(".kittyImage").click(function(e) {
    // Call the contract's `feedOnKitty` method with zombieId and kittyId.
    ZombieFeeding.feedOnKitty(zombieId, kittyId);
});
```

* It sets up a click event handler for elements with the class "kittyImage." When an element with this class is clicked, the provided function is executed.
    
* Inside the click event handler, it calls the `feedOnKitty` method of the `ZombieFeeding` contract, passing the `zombieId` and `kittyId` as arguments. This action triggers an interaction with the smart contract, involving feeding a zombie with a CryptoKitty.
    

```javascript
// Listen for a NewZombie event from our contract so we can display it.
ZombieFactory.NewZombie(function(error, result) {
    if (error) return;
    // This function will display the zombie, like in lesson 1.
    generateZombie(result.zombieId, result.name, result.dna);
});
```

* It sets up an event listener for the "NewZombie" event emitted by a contract named `ZombieFactory`. When a "NewZombie" event occurs, the provided callback function is executed.
    
* Inside the callback function, it checks for errors (`if (error) return;`) and, assuming no errors, calls a function called `generateZombie` with information about the new zombie (zombieId, name, and DNA). This function is responsible for displaying information about a newly created zombie.
    

Alright! So we are now at the stage where we can see our smart contract interacting with web applications. I'm excited, tired, and dizzy at the same time. Researching and compiling this information is a challenge, but I'm up for it. See you all for the lesson 3 review!