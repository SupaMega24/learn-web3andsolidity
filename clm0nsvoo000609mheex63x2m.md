---
title: "CryptoZombies: Lesson 2 Review"
seoTitle: "CryptoZombies Lesson 2 Explained"
seoDescription: "Learning solidity by building a zombie game"
datePublished: Fri Sep 01 2023 13:57:16 GMT+0000 (Coordinated Universal Time)
cuid: clm0nsvoo000609mheex63x2m
slug: cryptozombies-lesson-2-review
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693576382892/0defcfa4-f4c4-40db-afeb-4dd9c6ae0c5b.png
tags: learning, solidity, smart-contracts, solidity-basics

---

### **Overview**

Although I was able to solve all of the chapters fairly well, this lesson was still very challenging. The writers did a great job of presenting and setting up the tasks. However, I didn't fully grasp everything that I was doing. This is 100% on me. I simple just don't have the knowledge and experience yet. Oh, and my cat was constantly begging me to play fetch (but that's a whole other story). Speaking of cats, I got to create a CatZombie by feeding off of CryptoKitties.

There were several new concepts introduced such as require, inheritance, internal vs. external functions, interface, msg.sender, and multiple returns. It's not the terms themselves, but the actual use in the code that gave me a few dizzy spells. Before we get into the code, I'd like to take some time to go over the challenging concepts that I have mentioned above.

### **Challenging Concepts**

***Require:***

In Solidity, the `require` statement is like a rule checker. It's used to say, "If something isn't the way I expect it to be, stop right here and don't do anything else."

Imagine you're making a sandwich. Before you start, you might say, "I require that I have both bread and peanut butter." If you don't have both of those things, you stop making the sandwich because you can't make it the way you want.

In Solidity, it's similar. You could say, "I require that the sender of this action is the owner of a certain thing." If that's not true, the contract stops doing whatever it was trying to do because it's not allowed to continue if the condition isn't met. It helps make sure everything is safe and follows the rules.

***Inheritance:***

Imagine you're building different types of vehicles in a game. You start by creating a basic vehicle with some common features like wheels and color. Then, you decide to create more specialized vehicles like cars and bikes.

Instead of starting from scratch for each specialized vehicle, you can use the features from the basic vehicle and just add or modify what's needed. This way, you save time and make sure all vehicles share the same basic qualities.

Inheritance is a bit like that. You can create a basic "parent" contract with common functions and data. Then, you can create "child" contracts that inherit from the parent. Child contracts automatically have the features of the parent contract and can also add their own unique features or changes.

So, just like building vehicles, inheritance lets you reuse code, save time, and keep your contracts organized and consistent.

***Interval vs. external functions:***

In simple terms, internal functions are like private helpers within a family, while external functions are like public services available to everyone. However, it's a little deeper than that because you also have to consider private and public functions. It is essential to know the difference when coding your functions in a contract. Assigned incorrectly could hamper the versatility of the function. Let's look at these a bit more closely:

1. **Internal vs. Private Functions:**
    
    * **Internal Functions:** These functions can be thought of as "family functions." They are like helpers within the same contract "family." They can be accessed by other functions within the same contract, **including derived contracts (contracts that inherit from this one)**. This allows for code reusability and organization within the contract hierarchy.
        
    * **Private Functions:** Private functions are even more restricted. They are like personal secrets known only to a single function. They can only be accessed and used within the exact function they are defined in. Not even other functions within the same contract can use them. Private functions are useful for encapsulating logic that should remain hidden from other parts of the contract.
        
2. **External vs. Public Functions:**
    
    * **External Functions:** These functions can be thought of as "services provided to the outside world." They can be called by anyone, including external accounts and other contracts. External functions are typically used as entry points to interact with the contract. The function's arguments and return values are serialized for external communication.
        
    * **Public Functions:** Public functions are like open doors. They provide access not only to external entities but also to other functions within the same contract and derived contracts. Public functions are often used to expose core functionalities of the contract that need to be accessible both internally and externally.
        

***Interface:***

An interface is like a contract between two things that want to communicate but don't necessarily know each other's details. It's like speaking the same language without knowing all the inner workings.

Imagine you're building a robot and a remote control. The robot knows how to follow commands from the remote, but it doesn't need to know how the remote works inside. The remote just needs to send the right signals to control the robot.

In Solidity, an interface is a bit like that. It's a way to say, "Hey, as long as you understand these specific commands, we can work together." It helps different parts of a program connect without needing to know everything about each other.

We will see this in action later when we change one of our private functions to internal so that when the contract is inherited the function can still be used by the new contract.

***msg.sender:***

`msg.sender` is like a return address in a letter. It tells a smart contract who's sending a transaction or calling a function. Just like you'd write your address on an envelope, `msg.sender` identifies the sender of an action on the blockchain.

***Multiple Returns:***

I found this to be very interesting because (as far as I know) this can't be done in Python or Javascript. In Solidity, multiple returns mean that a function can give back more than one piece of information at once. It's like getting multiple items when you order a combo meal at a fast-food restaurant.

Imagine you're ordering a burger combo. You get a burger, fries, and a drink all together. This eliminates the need to create a separate function to return each of the items individually. This sounds simple enough, but there is a bit more to cover on this topic. We'll revisit it when we review the code.

### **Code Breakdown: zombiefactory.sol Updates**

While most of our work took place in a new file called `zombiefeeding.sol`, there were some additions and updates to our original file `zombiefactory.sol`. You may notice that the files are named according to the contracts that they carry. For this review, I'll start with the additions and updates first.

```solidity
mapping (uint => address) public zombieToOwner;
mapping (address => uint) ownerZombieCount;
```

Those two lines of code are setting up mappings in our smart contract. Let's break them down in simple terms:

1. At first, `=>` threw me off a bit. I remember seeing it the first lesson, but didn't think much of it at the time. Then I realized that it is quite similar to 'key: value' used in Python dictionaries. Think of a dictionary where addresses are like words, and strings are like their corresponding definitions. The `=>` symbol serves as a way to connect a word (address) to its definition (string) within the mapping.
    
2. **Mapping** `zombieToOwner` (`uint => address`):
    
    * This is like a record book that keeps track of which zombie belongs to which owner. It associates a zombie's unique identifier (uint) with the owner's Ethereum address (address).
        
    * For example, if you have a zombie with ID 123, this mapping would tell you which Ethereum address owns that zombie.
        
    * The `public` keyword means that other people and contracts can read this information directly from the blockchain.
        
3. **Mapping** `ownerZombieCount` (`address => uint`):
    
    * This is like a counter that shows how many zombies an owner has. It associates an owner's Ethereum address (address) with the number of zombies they own (uint).
        
    * For instance, if an Ethereum address owns 3 zombies, this mapping would store that count as 3.
        

In essence, these mappings help keep track of zombie ownership and how many zombies each owner has. They're like organized databases that make it easy to find out who owns what and how many.

In our first lesson, we had the following code for our `_createZombie` function.

```solidity
   function _createZombie(string memory _name, uint _dna) private {
        uint id = zombies.push(Zombie(_name, _dna)) - 1;
        emit NewZombie(id, _name, _dna);
    }
```

For lesson 2, we boosted our function as shown below.

```solidity
function _createZombie(string memory _name, uint _dna) internal {
        uint id = zombies.push(Zombie(_name, _dna)) - 1;
        zombieToOwner[id] = msg.sender;
        ownerZombieCount[msg.sender]++;
        emit NewZombie(id, _name, _dna);
    }
```

You can easily notice that the function was changed from private to internal. We know that this will allow the function to be used in another contract if it is inherited. More on this when we create our new file. Additionally, two more lines were added to the code between `uint id` and `emit NewZombie`. Let's take a look at what this means.

1. **Create Zombie and Get ID:**
    
    * A new zombie is created using the provided `_name` and `_dna`. The `Zombie(_name, _dna)` part creates a new `Zombie` struct with the given name and DNA.
        
    * `zombies.push(...)` adds this new zombie to the `zombies` array and returns the new length of the array. Subtracting `1` gives the index (ID) of the newly added zombie.
        
2. **Associate Zombie ID with Sender:**
    
    * The ID of the newly created zombie is associated with the address of the sender (`msg.sender`) in the `zombieToOwner` mapping. This means the sender of the transaction (the person or contract calling this function) is marked as the owner of this zombie.
        
3. **Increment Zombie Count for Sender:**
    
    * The count of zombies owned by the sender's address is incremented in the `ownerZombieCount` mapping. This keeps track of how many zombies each address owns.
        
4. **Emit NewZombie Event:**
    
    * An event named `NewZombie` is emitted, indicating that a new zombie was created. This event includes the zombie's ID, name, and DNA. This helps external applications and contracts know that a new zombie was added to the system.
        

In simple terms, this function creates a new zombie, associates it with the sender's address, updates the count of zombies owned by the sender, and lets the world know about the creation through an event. It's like adding a new member to a club, noting who the member is, updating their count, and announcing it to everyone.

I must admit that the code is starting to get more and more difficult for me at this point. While I understand the code after doing a bit of research, it still escapes me later. This - I hope - will decrease with time, practice, and experience. But I digress; let's move on!

### **New File: zombiefeeding.sol**

```solidity
// Importing Other Contracts
import "./zombiefactory.sol";
```

This section imports the content of another Solidity file named `zombiefactory.sol`. When a contract is imported, it means that the content of one Solidity file is made accessible to another. This allows you to reuse code, organize your project into multiple files, and maintain a modular structure. Here's what happens when a contract is imported:

1. **Code Reusability:** You can define common functions, data structures, or state variables in one Solidity file and then reuse them in multiple contracts across different files. This promotes code reusability and reduces redundancy.
    
2. **Modularization:** Large projects can become complex and hard to manage if all the code is in a single file. By splitting your code into multiple files, each file can focus on a specific aspect of your project, making it easier to understand and maintain.
    
3. **Readability:** Importing contracts allows you to keep your codebase clean and organized. Other developers will be able to easily understand the structure of your project by looking at the imports and can follow the logic without getting lost in a single monolithic file.
    
4. **Namespace Separation:** Each contract in Solidity has its own namespace. Importing a contract makes the imported contract's functions and state variables available within the importing contract's namespace. This means you can avoid naming conflicts between contracts.
    

---

```solidity
// Interface for CryptoKitties
contract KittyInterface {
  function getKitty(uint256 _id) external view returns (
    bool isGestating,
    bool isReady,
    uint256 cooldownIndex,
    uint256 nextActionAt,
    uint256 siringWithId,
    uint256 birthTime,
    uint256 matronId,
    uint256 sireId,
    uint256 generation,
    uint256 genes
  );
}
```

In this section, we define an interface named `KittyInterface`. Interfaces in Solidity are a way to connect your smart contract with external code or contracts, typically those you don't control or that exist outside your program. This interface specifies a function `getKitty` that takes a kitty ID as input and returns various details about a CryptoKitty.

---

```solidity
// Main Contract: ZombieFeeding
contract ZombieFeeding is ZombieFactory {
```

Here, we declare the main contract named `ZombieFeeding`, and it inherits from the `ZombieFactory` contract. Inheritance allows `ZombieFeeding` to use the functions and state variables of `ZombieFactory`. As long as the functions from the inherited contract are not private. Private functions are the most restricted in terms of visibility, and they are only accessible within the contract where they are defined. They cannot be accessed or overridden in derived contracts.

---

```solidity
// Setting the CryptoKitties Address
address ckAddress = 0x06012c8cf97BEaD5deAe237070F9587f8E7A266d;

// Creating a KittyInterface Instance
KittyInterface kittyContract = KittyInterface(ckAddress);
```

This section sets up an address (`ckAddress`) representing the Ethereum address of the CryptoKitties smart contract. Then, it creates an instance of the `KittyInterface` contract named `kittyContract` using this address. This instance will be used to interact with CryptoKitties' functions. An "instance" typically refers to a specific occurrence or instantiation of a contract. It's an individual contract created from a contract template (also known as a contract class or contract blueprint).

---

```solidity
// feedAndMultiply Function
function feedAndMultiply(uint _zombieId, uint _targetDna, string memory _species) public {
  require(msg.sender == zombieToOwner[_zombieId]);
  Zombie storage myZombie = zombies[_zombieId];
  _targetDna = _targetDna % dnaModulus;
  uint newDna = (myZombie.dna + _targetDna) / 2;
  if (keccak256(abi.encodePacked(_species)) == keccak256(abi.encodePacked("kitty"))) {
    newDna = newDna - newDna % 100 + 99;
  }
  _createZombie("NoName", newDna);
}
```

Ultimately, this function is where creatures (zombies and "kitties") can be fed to modify the DNA of a zombie. The function checks ownership, calculates a new DNA, and possibly modifies it based on the species of the creature being fed. Finally, it creates a new zombie with the updated DNA. This one is really difficult for me to fully grasp, so I've had to spend some time on it. Here's how I understand it so far.

1. **Function Declaration:**
    
    * This code defines a function named `feedAndMultiply`.
        
    * It takes three parameters:
        
        * `uint _zombieId`: The ID of the zombie that is being fed.
            
        * `uint _targetDna`: The DNA data of the creature being used for feeding.
            
        * `string memory _species`: A string representing the species of the creature (e.g., "kitty").
            
2. **Require Statement:**
    
    * `require(msg.sender == zombieToOwner[_zombieId]);` checks a condition before proceeding with the function. It verifies that the sender of the transaction (`msg.sender`) is the owner of the zombie with the specified `_zombieId`. If this condition is not met, the function will revert (stop executing).
        
3. **Zombie Data Retrieval:**
    
    * `Zombie storage myZombie = zombies[_zombieId];` retrieves the data of the zombie with the given `_zombieId` from the `zombies` array and stores it in a local variable `myZombie`. The `storage` keyword indicates that `myZombie` is a reference to the storage location of the zombie in the array.
        
4. **DNA Manipulation:**
    
    * `_targetDna = _targetDna % dnaModulus;` calculates the remainder of `_targetDna` when divided by `dnaModulus`. This ensures that `_targetDna` stays within a certain range defined by `dnaModulus`.
        
    * `uint newDna = (myZombie.dna + _targetDna) / 2;` calculates a new DNA value by averaging the existing DNA of the zombie (`myZombie.dna`) with the modified `_targetDna`.
        
5. **Species Check:**
    
    * `if (keccak256(abi.encodePacked(_species)) == keccak256(abi.encodePacked("kitty"))) { ... }` checks if the `_species` parameter is equal to "kitty." This check is case-insensitive, and it uses the `keccak256` hash function to compare the strings.
        
    * If the species is "kitty," it modifies the `newDna` value by subtracting the remainder when divided by 100 and adding 99. CryptoZombies has set the last two digits of cat-zombies to be 99. Therefore, 99 will be added as the last two digits of their DNA.
        
6. **Creating a New Zombie:**
    
    * `_createZombie("NoName", newDna);` calls a function named `_createZombie` with the parameters "NoName" (a placeholder name) and the calculated `newDna`. This function creates a new zombie with the provided data.
        

---

```solidity
// feedOnKitty Function
function feedOnKitty(uint _zombieId, uint _kittyId) public {
  uint kittyDna;
  (,,,,,,,,,kittyDna) = kittyContract.getKitty(_kittyId);
  feedAndMultiply(_zombieId, kittyDna, "kitty");
}
```

In summary, this function retrieves the DNA of a CryptoKitty using the `kittyContract.getKitty` function, assigns it to the `kittyDna` variable while ignoring other values in the tuple, and then calls another function (`feedAndMultiply`) to use that DNA to modify the zombie's DNA based on the CryptoKitty's DNA.

1. `uint kittyDna;`: This line declares a local variable named `kittyDna` of type `uint` (unsigned integer). It's creating a placeholder variable to store the DNA of the CryptoKitty.
    
2. `(,,,,,,,,,kittyDna) = kittyContract.getKitty(_kittyId);`: This line is where the action happens. Let's break it down further:
    
    * `kittyContract.getKitty(_kittyId)`: This is a function call to a contract named `kittyContract`. It's calling the `getKitty` function on that contract and passing `_kittyId` as an argument. The function likely returns a tuple with multiple values, including the DNA of the CryptoKitty.
        
    * `(,,,,,,,,,kittyDna)`: This part is a tuple assignment. It's saying "ignore the first nine values in the tuple and assign the tenth value (genes) to the `kittyDna` variable." The commas represent placeholders for the values being ignored.
        
    
    So, this line effectively retrieves the DNA of the CryptoKitty using `kittyContract.getKitty(_kittyId)` and assigns it to the `kittyDna` variable while ignoring the other values in the tuple.
    
3. `feedAndMultiply(_zombieId, kittyDna, "kitty");`: After obtaining the `kittyDna`, this line calls the `feedAndMultiply` function, passing `_zombieId` (the ID of the zombie), `kittyDna` (the DNA of the CryptoKitty), and the string "kitty" as arguments.
    

### **Final Review:**

In summary, this code is part of a larger system for managing zombies and their interactions with CryptoKitties. It inherits functionality from another contract, interfaces with CryptoKitties to retrieve genetic data, and allows zombies to be fed and potentially modified based on that data. Here's a final review of what is happening in the code, step by step.

1. **Importing Other Contracts:**
    
    * The code starts with an import statement: `import "./zombiefactory.sol";`. This brings in the content of the first file named `zombiefactory.sol`. It's common to split contracts into multiple files for better organization.
        
2. **Interface for CryptoKitties:**
    
    * `contract KittyInterface { ... }` defines an interface named `KittyInterface`. An interface in Solidity is like a blueprint that other contracts can use to interact with the contract that adheres to this interface.
        
    * It declares a function `getKitty` that takes a kitty ID as input and returns various details about a CryptoKitty.
        
3. **Main Contract: ZombieFeeding:**
    
    * `contract ZombieFeeding is ZombieFactory { ... }` declares a new contract called `ZombieFeeding`, which inherits from the `ZombieFactory` contract. Inheritance allows `ZombieFeeding` to use the functions and state variables of `ZombieFactory`.
        
4. **Setting the CryptoKitties Address:**
    
    * `address ckAddress = 0x06012c8cf97BEaD5deAe237070F9587f8E7A266d;` sets the Ethereum address of the CryptoKitties smart contract. This address is used to interact with CryptoKitties.
        
5. **Creating a KittyInterface Instance:**
    
    * `KittyInterface kittyContract = KittyInterface(ckAddress);` creates an instance of the `KittyInterface` contract using the previously set CryptoKitties address. This instance, `kittyContract`, is used to interact with CryptoKitties' functions.
        
6. **feedAndMultiply Function:**
    
    * `function feedAndMultiply(uint _zombieId, uint _targetDna, string memory _species) public { ... }` is a function that takes three parameters: `_zombieId`, `_targetDna`, and `_species`. It's used to feed a zombie and potentially create a new zombie.
        
    * The function checks if the sender of the transaction is the owner of the specified zombie.
        
    * It calculates a new DNA for the zombie by combining the current zombie's DNA (`myZombie.dna`) with the `_targetDna` provided as an argument.
        
    * If `_species` is "kitty," it modifies the new DNA to make it more "kitty-like."
        
    * Finally, it calls the `_createZombie` function to create a new zombie with the modified DNA.
        
7. **feedOnKitty Function:**
    
    * `function feedOnKitty(uint _zombieId, uint _kittyId) public { ... }` is a function used to feed a zombie with the genetic data of a CryptoKitty.
        
    * It calls the `getKitty` function from the `kittyContract` using `_kittyId` to fetch the DNA of the CryptoKitty.
        
    * Then, it calls the `feedAndMultiply` function to feed the zombie with the obtained DNA, specifying the `_species` as "kitty."
        

Well, it has taken me a bit longer to put this all together. However, it is part of the journey. I honestly do feel that I'm learning and understanding what is happening in the code more than I would by just doing the lessons. I'm a noob and you can probably pook holes in my article all day. But, I'm learning. When reviewing like this, I often come across terms that I'm unfamiliar with and have to dig a bit deeper.

One more thing before I go. CryptoZombies showed the JavaScript and web3.js implementation code that interacts with our contract at the end of the lesson. I am tempted to do a quick breakdown of that before moving on to lesson 3. The reason for this is that we will need JavaScript for the front-end for our final lesson. If I do, it will be brief.