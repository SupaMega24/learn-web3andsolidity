---
title: "CryptoZombies: Lesson 1 Review"
seoTitle: "CryptoZombies Lesson 1 Review"
seoDescription: "A break down and explanation for the first lesson from CryptoZombies Solidity: Beginner to Intermediate Smart Contracts"
datePublished: Mon Aug 28 2023 08:57:29 GMT+0000 (Coordinated Universal Time)
cuid: cllunbyks000o09jp13ag2f2v
slug: cryptozombies-lesson-1-review
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693212811816/9310daf7-08d1-4612-9e89-323926103096.png
tags: solidity, learn-coding, learning-journey, ethereum-smart-contracts, solidity-basics

---

I must say that I thoroughly enjoyed my first lesson. I'm going to take this time to review and go over what I have learned with you. However, if you haven't finished lesson 1 please do so before reading this post. There are too many spoilers below that might negatively impact your learning journey.

### Key Terms/Syntax

Before we start, let's look at some essential vocabulary.

Here's an explanation of each of the key Solidity terms from the lesson:

1. **Contract:** A contract in Solidity is a fundamental building block of Ethereum smart contracts. It represents a collection of data (state variables) and functions that can interact with the Ethereum blockchain. Contracts define the behavior and rules of decentralized applications (DApps) and are written in the Solidity programming language.
    
2. **Function:** A function in Solidity is a block of code that performs a specific task or set of tasks. Functions can be called externally (from outside the contract) or internally (from within the contract). They can read and modify the contract's state, and they can also return values.
    
3. **Variable:** Variables in Solidity are used to store data. They can hold different types of data such as integers, strings, addresses, and more. Variables are used to maintain the state of a contract and to store values that can be used in computations and logic.
    
4. **Struct:** A struct (short for structure) in Solidity is a custom data type that allows you to define a composite data structure consisting of multiple fields with different data types. Structs are useful for creating complex data structures that represent real-world objects or entities.
    
5. **Array:** An array in Solidity is a data structure that can hold multiple elements of the same data type. Arrays can be dynamic (length can change during execution) or fixed-size. They are often used to store collections of data, such as a list of addresses or a sequence of numbers.
    
6. **Compile:** Compilation is the process of converting human-readable Solidity code into machine-readable bytecode that can be executed on the Ethereum Virtual Machine (EVM). Solidity code is compiled using the Solidity compiler. The resulting bytecode is deployed to the blockchain, and users can interact with the compiled smart contract by sending transactions.
    

These terms are foundational to understanding and working with Solidity and smart contracts on the Ethereum blockchain. As we continue to learn and develop in the blockchain space, we'll encounter these concepts frequently and see how they come together to create functional and secure decentralized applications.

### Code Breakdown

Okay, now we are ready to rock! Let's break down the Solidity code step by step to understand its structure and functionality. The code below defines a smart contract named `ZombieFactory`, which is used to create and manage zombie entities on the Ethereum blockchain.

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {
```

* The `pragma` statement specifies the version of the Solidity compiler that should be used to compile the code. In this case, it allows versions greater than or equal to `0.5.0` but less than `0.6.0`.
    
* The `contract ZombieFactory { ... }` block is the main body of the smart contract. It contains the contract's state variables, functions, and other definitions.
    

```solidity
    event NewZombie(uint zombieId, string name, uint dna);
```

* The `event` declaration defines an event named `NewZombie`. Events are used to log information about important occurrences within the smart contract. This event logs the creation of a new zombie and includes the `zombieId`, `name`, and `dna` attributes.
    
* You'll see that this event will be triggered a bit later in our code.
    

```solidity
    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;
```

* These lines declare two `uint` variables, `dnaDigits` and `dnaModulus`. These variables are used for generating random DNA values for zombies. `dnaDigits` specifies the length of the DNA sequence, and `dnaModulus` is a divisor used to keep the DNA within a specific range. The value is calculated as `10` raised to the power of `dnaDigits` (which is `16`).
    
* In Solidity, the double-asterisk (`**`) is used as an exponentiation operator. It raises a number to a specified power. For example: (2\*\*2 = 4)**,** or (3\*\*3 = 27).
    

```solidity
    struct Zombie {
        string name;
        uint dna;
    }
```

* This defines a `struct` named `Zombie` to represent a zombie entity. It contains two attributes: `name` (a string) and `dna` (an unsigned integer representing the zombie's genetic code).
    
* These attributes will be used throughout the contract in the functions to build our zombies. To me, it seems similar to raw materials in a factory.
    

```solidity
    Zombie[] public zombies;
```

* This declares a public array of `Zombie` structs named `zombies`. Public arrays in Solidity automatically create a getter function, allowing external code to access the array's elements.
    
* I consider this to be similar to a list. In this case, new zombies are added to our list (array) when created.
    
* It's important to note that this is located outside of a function to work properly within the contract.
    

```solidity
    function _createZombie(string memory _name, uint _dna) private {
        uint id = zombies.push(Zombie(_name, _dna)) - 1;
        emit NewZombie(id, _name, _dna);
    }
```

* This is a private function `_createZombie` that takes a `_name` (a string) and `_dna` (an unsigned integer) as parameters. It creates a new `Zombie` struct using the provided attributes and pushes it onto the `zombies` array. It also emits the `NewZombie` event to log the creation of the new zombie.
    
* A private function in Solidity is a function that can only be accessed and called from within the same contract where it's defined. It's not accessible from external contracts or transactions.
    
* The attribute 'memory' is used to temporarily store data. When you pass a parameter with the `memory` keyword, you're indicating that the function will read and manipulate the data in temporary memory without modifying the data on the blockchain itself.
    
* So basically this function creates a zombie and places it in our array.
    
* In the second of the code above, we create a variable 'uint id' to be used in the next line as a parameter in emit NewZombie(). The -1 tells the computer to store it at the end of the list.
    
* When you want to record a specific occurrence or action in your contract, you use the `emit` keyword followed by the name of the event and the required arguments. Emitting an event is a way to announce that a certain action has taken place within the contract.
    

```solidity
    function _generateRandomDna(string memory _str) private view returns (uint) {
        uint rand = uint(keccak256(abi.encodePacked(_str)));
        return rand % dnaModulus;
    }
```

* This is another private function `_generateRandomDna` that takes a `_str` (a string) as input. It generates a random number based on the provided string using the `keccak256` hash function. The result is then modulo-ed by `dnaModulus` to ensure the generated DNA value falls within the desired range.
    
* In simple terms, you can think of keccak256 as a magic blender for data. Let's break it down:
    
    1. **Input Data:** Imagine you have any kind of data, like a message, a number, a document, or even a picture. Keccak256 takes this data as input.
        
    2. **Blender:** Think of Keccak256 as a super-powerful blender. You put your data into the blender, and it processes the data in a way that produces a unique fixed-size "fingerprint" for that input.
        
    3. **Output Hash:** The output of the blender is a long string of characters, usually shown as a series of numbers and letters. This is called a "hash." The special thing about Keccak256 is that even a tiny change in the input data will completely change the hash.
        
    4. **Unpredictable:** Changing just a single character of the input data results in a completely different hash. It's almost impossible to predict what the hash will look like based on the original data.
        
    5. **Fixed Size:** No matter how large or small your input data is, the hash that Keccak256 produces is always the same length. This makes it easy to compare hashes and verify data.
        
    6. **One-Way Function:** Once you blend your data with Keccak256, you can't reverse the process to get back your original data. It's like turning an apple into applesauce—you can't turn the sauce back into an apple.
        
    7. **Security and Integrity:** Keccak256 is used in blockchain to ensure the integrity of data. If even a tiny part of the original data changes, the hash will change dramatically, alerting you to any tampering.
        
* Another key attribute of this function is the abi. In summary, `abi.encodePacked` is used to format the input data as raw binary, which is then hashed using Keccak256 to generate a hash value. This hash value is stored as an unsigned integer (`uint`) and is further constrained to a specific range using the modulus operation. The resulting value is the random DNA value used within the contract.
    
* The code in this function was a lot for me to unpack, so I'll break it down a little further the best I can:
    
* Here's a breakdown of the key elements:
    
    1. `abi.encodePacked(_str)`:
        
        * The `abi.encodePacked` function is used to tightly pack the input data `_str` without any padding. It converts the input data into its raw binary representation.
            
        * This is important because the Keccak256 hash function operates on binary data, and using `abi.encodePacked` ensures that the data is treated as raw binary without any extra formatting.
            
    2. `keccak256(...)`:
        
        * `keccak256` is the Keccak256 hash function, a cryptographic hashing algorithm used to create a unique hash value from its input.
            
        * It takes the packed binary data generated by `abi.encodePacked(_str)` and produces a hash value that appears random but is deterministic for the same input.
            
    3. `uint(rand)`:
        
        * After generating the hash using `keccak256`, the result is stored in a variable named `rand`. It's important to note that the output of the `keccak256` function is a hash, which is typically a byte array.
            
        * By using `uint(rand)`, the hash is converted into an unsigned integer type. This is likely done to ensure compatibility with the `dnaModulus` calculation and to provide a number within a certain range.
            
    4. `rand % dnaModulus`:
        
        * The `%` operator calculates the remainder of the division between `rand` and `dnaModulus`. This effectively limits the range of the generated DNA value to be between 0 and `dnaModulus - 1`.
            
        * This step ensures that the DNA value fits within the desired range based on the number of digits specified by `dnaDigits`.
            

```solidity
    function createRandomZombie(string memory _name) public {
        uint randDna = _generateRandomDna(_name);
        _createZombie(_name, randDna);
    }
```

* This public function `createRandomZombie` takes a `_name` parameter and generates a random DNA value using `_generateRandomDna`. It then uses the `_createZombie` function to create a new zombie with the generated DNA and the provided name.
    

Overall, this smart contract allows users to create zombies with random DNA values by calling the `createRandomZombie` function. The contract ensures that DNA values are generated securely and logged through events for transparency. The contract's state variables and private functions work together to manage the creation of zombie entities on the Ethereum blockchain.

### **Review**

Okay, before we go, let's look at what our code is doing step by step.

1. **Contract Declaration:** The code starts by declaring a Solidity contract named `ZombieFactory`.
    
2. **Event Declaration:** An event named `NewZombie` is declared using the `event` keyword. This event will be emitted whenever a new zombie is created, and it will store information about the zombie's ID, name, and DNA.
    
3. **Constants:** Two constants, `dnaDigits` and `dnaModulus`, are defined. `dnaDigits` represents the number of digits in a DNA sequence, and `dnaModulus` is calculated as 10 raised to the power of `dnaDigits`. These constants are used to manage the DNA generation process.
    
4. **Struct Declaration:** A struct named `Zombie` is defined. This struct has two fields: `name` (a string) and `dna` (an unsigned integer).
    
5. **Array Declaration:** An array of `Zombie` structs named `zombies` is declared as public. This array will store all the zombie entities created by the contract.
    
6. **Function: \_createZombie:** This is a private function that creates a new zombie. It takes two parameters: `_name` (the zombie's name) and `_dna` (the zombie's DNA). Inside this function:
    
    * A new zombie is created using the provided `_name` and `_dna`.
        
    * The new zombie is added to the `zombies` array using the `push` function, and the index of the newly added zombie is stored in the `id` variable.
        
    * The `NewZombie` event is emitted, passing the `id`, `_name`, and `_dna` as parameters.
        
7. **Function: \_generateRandomDna:** Another private function is defined to generate random DNA based on a given input string `_str`. Inside this function:
    
    * The `_str` is hashed using the `keccak256` hash function.
        
    * The resulting hash is converted to an unsigned integer and stored in the `rand` variable.
        
    * The random DNA is calculated as `rand` modulo `dnaModulus`, ensuring it fits within the desired range.
        
8. **Function: createRandomZombie:** This is a public function intended to be called by users to create a new random zombie. It takes `_name` (the zombie's name) as a parameter. Inside this function:
    
    * The `_generateRandomDna` function is called with `_name` to generate a random DNA for the zombie.
        
    * The `_createZombie` function is called with `_name` and `randDna` to create the new zombie entity and emit the `NewZombie` event
        

That's it for this review. I will be looking over this again before I move on to lesson 2. I think it will help me as I move into more diffucult parts of our code. I hope this was helpful. For those of you who are more advanced than me, constructive criticism is welcomed as long as it is supportive and can help me improve my skills.