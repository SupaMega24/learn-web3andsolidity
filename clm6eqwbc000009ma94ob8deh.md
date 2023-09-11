---
title: "CryptoZombies: Lesson 4 Review"
datePublished: Tue Sep 05 2023 14:30:24 GMT+0000 (Coordinated Universal Time)
cuid: clm6eqwbc000009ma94ob8deh
slug: cryptozombies-lesson-4-review
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693923907549/558d1f65-7fb9-42eb-a523-e3d78fa1d82d.png
tags: learning, solidity, smart-contracts, solidity-basics

---

### **Overview**

During this lesson, we build a battle system that tracks wins and losses, defines more ways of leveling up your zombie, and takes payments. We work a bit more with modifiers and get into an if/else statement. I can confidently say that this is the first lesson where felt confident with my code. I was even able to write some of it on my own, albeit a small fraction. Let's dive into the challenging concepts and break down some code to review what we've learned.

### **Challenging Concepts**

***Gas:***

Imagine you're driving a car, and you need fuel to run it. Gas in Ethereum is like the fuel for your smart contracts. Every operation or computation that a smart contract performs requires a certain amount of gas.

Let's dig a little deeper:

1. **Resource Cost**: Gas represents the computational and storage resources consumed by your smart contract. Just as driving your car consumes fuel, executing a smart contract consumes gas.
    
2. **Transaction Fees**: When you want to interact with a smart contract, like sending cryptocurrency or invoking a function, you need to pay for the gas it consumes. This payment is called a "transaction fee" and is typically paid in Ether (ETH), the native cryptocurrency of Ethereum.
    
3. **Preventing Abuse**: Gas limits prevent malicious or poorly written contracts from running indefinitely and clogging the Ethereum network. Contracts with infinite loops or excessive computations will run out of gas and stop.
    
4. **Fairness**: Gas ensures fairness and resource allocation on the Ethereum network. Miners or validators who process transactions and smart contracts are compensated with gas fees for their work.
    
5. **Predictability**: Gas allows you to estimate the cost of executing a smart contract in advance. This predictability is essential for developers and users to know how much a transaction or operation will cost.
    

***Payable Modifier:***

In simple terms, the `payable` modifier in Ethereum smart contracts is like a sign that says "Hey, you can send money to this function."

Here's a bit more detail:

1. **Receiving Ether**: When you mark a function with the `payable` modifier, it means the function can accept Ether (the cryptocurrency of Ethereum) as part of the transaction. People can send Ether to this function.
    
2. **Use Cases**: You might use the `payable` modifier in functions that involve financial transactions, like receiving payments, crowdfunding, or buying something in a decentralized application (DApp).
    
3. **Safety**: It's essential to use `payable` carefully because receiving Ether means handling value, and you want to make sure your contract can handle it securely and accurately.
    
4. **Cost**: Be aware that handling Ether in a smart contract can incur gas costs, so users need to pay gas fees for transactions involving the `payable` function.
    

In short, when you mark a function as `payable`, you're opening a door for your smart contract to receive Ether, enabling various financial interactions on the Ethereum blockchain.

***msg.:***

We've seen `msg.sender` in our previous lessons, but it turns out that there is more to the `msg.` than meets the eye. Think of `msg` as an envelope that contains a letter. The envelope (msg) tells you who sent the letter (msg.sender), how much money (Ether) is inside (msg.value), and what's written in the letter ([msg.data](http://msg.data)). It also has a limited amount of postage (gas) available to deliver the letter.

These properties within `msg` are crucial for smart contracts to make decisions, handle payments, and interact with the Ethereum blockchain in a secure and predictable manner:

1. **msg.sender**: `msg.sender` represents the Ethereum address (an alphanumeric identifier) of the person or contract that initiated the current transaction. It tells you who is sending the transaction.
    
2. **msg.value**: `msg.value` is a property that holds the amount of Ether (the cryptocurrency of Ethereum) sent along with the transaction. It tells you how much Ether is being transferred to the contract.
    
3. [**msg.data**](http://msg.data): [`msg.data`](http://msg.data) is a byte array containing the input data for the function being called in the contract. It includes the function's signature and any parameters passed to it.
    
4. **msg.gas**: `msg.gas` provides information about the amount of gas still available for the current transaction. Gas is used to pay for computation and storage on the Ethereum network, and this property helps you keep track of how much gas is left.
    

***transfer:***

Think of `.transfer()` as placing an envelope with a specific amount of money into a secure mailbox. The mailbox (`.transfer()`) ensures that the money is safely sent to the recipient's address, and it won't get lost or stolen along the way.

So, in code, when you see `.transfer()`, it means you're initiating a secure transfer of a specified amount of Ether from the contract to an Ethereum address. Here's how it works:

1. **Sender and Recipient**: The contract, where the `.transfer()` function is called, is the sender. It's sending Ether to a recipient, which is typically an Ethereum address (either a user's wallet or another contract).
    
2. **Amount**: You specify the amount of Ether you want to send in the `.transfer()` function. This amount is in Wei, the smallest denomination of Ether (1 Ether = 1,000,000,000,000,000,000 Wei).
    
3. **Safety**: The `.transfer()` function is a secure way to send Ether because it handles potential errors, such as if the recipient's address is a contract with malfunctioning code. If an error occurs during the transfer, it reverts the transaction, ensuring that no unintended side effects occur.
    
4. **Gas Limit**: When using `.transfer()`, Ethereum sets a predefined amount of gas for the operation. This limits the computation that can be done during the transfer, preventing excessive gas consumption.
    

***Nonce:***

Think of a nonce as a ticket number you get when waiting in line at a deli or a bakery. Each customer gets a unique number (nonce) in sequential order. The bakery (Ethereum) serves customers in the order of their numbers (nonces), ensuring that everyone gets their order processed correctly and in the right sequence. This helps prevent any confusion or duplication of orders.

The nonce serves two critical purposes:

1. **Ordering**: Nonces ensure that transactions are processed in the correct order. Ethereum nodes process transactions based on their nonce values. If you were to use the same nonce for multiple transactions from the same account, it could lead to conflicts and unpredictable behavior.
    
2. **Security**: Nonces prevent replay attacks. A replay attack is when an attacker resubmits a previous transaction to trick the network into processing it again. With unique nonces, each transaction is a one-time-use token. Once a transaction with a specific nonce is processed, it can't be reused.
    

So, it's essential to use a new nonce for each transaction from an Ethereum account to maintain order, security, and predictability on the blockchain. Ethereum nodes reject transactions with nonces that have already been used for the same account.

***% 100:***

The specific function and purpose of `% 100` in Ethereum smart contracts will depend on the context in which it's used within the contract's logic. It's a versatile operation that can serve various functions based on the programmer's intentions:

1. **Limiting Values**: `% 100` is often used to limit a number within a certain range. For example, if you have a large number and you apply `% 100` to it, the result will always be between 0 and 99. This is useful for ensuring that a value doesn't become too large or to extract the last two digits of a number.
    
2. **Random Number Generation**: In some cases, `% 100` might be used in combination with other operations to generate random numbers. The idea is that by taking the remainder of a larger number divided by 100, you get a seemingly random number between 0 and 99.
    
3. **Formatting**: `% 100` can be used for formatting purposes. For instance, if you have a number representing a percentage, applying `% 100` can convert it into a decimal value between 0 and 1. This is useful for calculations involving percentages.
    
4. **Data Reduction**: When dealing with data that has a wide range of values, `% 100` can be used to reduce the data's granularity. For example, if you're working with timestamps, applying `% 100` to a timestamp might help group data into smaller time intervals.
    

***If Statements:***

If statements are a huge part of coding. I mentioned in an earlier post that learning to code has caused a bit of dizziness from time to time. Well, I if statements have been a huge contributor. Let's see if I can make it a bit easier to understand.

**If Statement in Plain Language**:

1. Imagine you're trying to decide whether to go outside.
    
2. You might say, "If it's sunny, I'll go outside; otherwise, I'll stay inside."
    
3. If it's sunny (the condition is true), you go outside. If it's not sunny (the condition is false), you stay inside.
    

**In Code**:

In programming, you use "if" statements to do similar decision-making. For example, you might say:

```javascript
if (sunny) {
    // Go outside
} else {
    // Stay inside
}
```

Here, `sunny` is a condition. If it's true, the program executes the "Go outside" part. If it's false, it does the "Stay inside" part. It gets more complex than this, but this is the general idea.

### **Contract Updates**

zombiehelper.sol:

* defined `levelUpFee` as a `uint`
    
* created `levelUp` function set to `payable`
    
* created a `withdraw` function
    
* created `setLevelUpFee` function
    

Let's break down what each function does:

1. **Withdraw Function**:
    

```solidity
function withdraw() external onlyOwner {
    address _owner = owner();
    _owner.transfer(address(this).balance);
}
```

* This function is marked as `external`, meaning it can be called from outside the contract.
    
* It has the `onlyOwner` modifier, which ensures that only the owner of the contract can execute this function.
    
* Inside the function, it retrieves the contract's owner's address using `owner()`.
    
* Then, it transfers the balance of the contract (the amount of Ether held by the contract) to the owner's address using `_owner.transfer(address(this).balance)`.
    
    This function allows the contract owner to withdraw the Ether balance from the contract.
    

1. **setLevelUpFee Function**:
    

```solidity
function setLevelUpFee(uint _fee) external onlyOwner {
    levelUpFee = _fee;
}
```

* This function is also marked as `external` and requires the `onlyOwner` modifier, meaning only the contract owner can execute it.
    
* It takes an argument `_fee`, which is the new value for the `levelUpFee`.
    
* It updates the `levelUpFee` variable to the new value provided.
    
    This function allows the contract owner to set the fee required for leveling up a zombie.
    

1. **levelUp Function**:
    

```solidity
function levelUp(uint _zombieId) external payable {
    require(msg.value == levelUpFee);
    zombies[_zombieId].level++;
}
```

* This function is marked as `external` and can be called from outside the contract.
    
* It is also marked as `payable`, which means it can receive Ether when called.
    
* It takes an argument `_zombieId`, which represents the ID of the zombie to level up.
    
* It requires that the value sent with the transaction (`msg.value`) is equal to `levelUpFee`. If not, the function will revert, and the transaction will fail.
    
* If the value is correct, it increases the level of the specified zombie by one.
    
    This function allows users to level up a zombie by sending the appropriate fee in Ether.
    

Overall, these functions demonstrate how you can manage the contract's balance, set parameters, and interact with the contract by sending Ether with transactions.

***zombiefeeding.sol:***

* created `ownerOf` modifer and added it to feedAndMultiply
    

The modifier called `ownerOf` is intended to be used in functions to enforce that only the owner of a specific zombie can execute those functions. Here's what the code does step by step:

1. **Modifier Declaration**:
    
    ```solidity
    modifier ownerOf(uint _zombieId) {
        require(msg.sender == zombieToOwner[_zombieId]);
        _;
    }
    ```
    
    * `modifier ownerOf(uint _zombieId)`: This line declares a modifier named `ownerOf` which takes one argument `_zombieId`. This `_zombieId` is used to specify which zombie's ownership is being checked.
        
2. **Require Statement**:
    
    Inside the modifier, there's a `require` statement:
    
    ```solidity
    require(msg.sender == zombieToOwner[_zombieId]);
    ```
    
    * `require`: This is a keyword used for checking a condition. If the condition inside it is `true`, the function using the modifier proceeds; otherwise, it reverts, rejecting the transaction.
        
    * `msg.sender`: This represents the Ethereum address of the sender of the transaction.
        
    * `zombieToOwner[_zombieId]`: This is a mapping that associates a zombie ID with its owner's Ethereum address. It checks if the sender of the transaction (`msg.sender`) is the owner of the zombie specified by `_zombieId`.
        
3. **Execution Placeholder**:
    
    The `_;` at the end of the modifier indicates where the code of the function that uses this modifier will be inserted. When you apply this modifier to a function, the code within that function will execute at this position.
    

***zombiefactory.sol:***

* added two new items to struct - `winCount` and `lossCount`
    
* modified \_createZombie() definition to include win/loss = 0
    

As we already know by now, the `Zombie` struct is a container that allows you to store various attributes of a zombie, such as its name, DNA, level, readiness, and battle statistics. Each field within the `struct` holds specific information about the zombie's characteristics and progress in the game or application where it's used.

Here's the code for the `Zombie` struct with explanations for `winCount` and `lossCount`:

```solidity
struct Zombie {
    string name;          // Stores the name of the zombie.
    uint dna;             // Stores the DNA of the zombie.
    uint32 level;         // Stores the level of the zombie.
    uint32 readyTime;     // Stores a timestamp indicating when the zombie will be ready.
    uint16 winCount;      // Stores the number of wins the zombie has achieved.
    uint16 lossCount;     // Stores the number of losses the zombie has experienced.
}
```

* `winCount` (uint16): This field is used to keep track of the number of victories the zombie has achieved in battles or competitions. It is represented as a 16-bit unsigned integer (`uint16`), which means it can store positive whole numbers ranging from 0 to 65,535. Each time the zombie wins a battle, this count is incremented.
    
* `lossCount` (uint16): This field is used to keep track of the number of defeats or losses the zombie has experienced in battles or competitions. Like `winCount`, it is also represented as a 16-bit unsigned integer (`uint16`). When the zombie loses a battle, this count is incremented.
    

The two fields, `winCount` and `lossCount`, provide a way to measure and display the success and competitiveness of each zombie within the game. They allow users or the application itself to track the performance of individual zombies in a simple and numeric manner.

Since we now have two new struct items, we add them to the \_createZombie function. They are the purple zeros shown below. Since I've already covered this function in a previous lesson, I'll focus more on the `uint id`, which takes on the new struct values.

```solidity
function _createZombie(string _name, uint _dna) internal {
    uint id = zombies.push(Zombie(_name, _dna, 1, uint32(now + cooldownTime), 0, 0)) - 1;
    zombieToOwner[id] = msg.sender;
    ownerZombieCount[msg.sender]++;
    emit NewZombie(id, _name, _dna);
}
```

1. `uint id = zombies.push(Zombie(_name, _dna, 1, uint32(now + cooldownTime), 0, 0)) - 1;`: This line does several things:
    
    * It creates a new `Zombie` struct with the specified `_name` and `_dna`, along with default values for the `level`, `readyTime`, `winCount`, and `lossCount` fields.
        
    * It adds this new `Zombie` struct to the `zombies` array using the `push` function, which appends it to the end of the array.
        
    * It subtracts 1 from the result of `push`. This is done to obtain the ID of the newly created zombie since array indices start at 0. So, `id` will store the ID of the newly created zombie.
        

In summary, this function creates a new zombie with the specified name and DNA, adds it to the `zombies` array, associates it with an owner, increments the owner's zombie count, and emits an event to inform external observers about the creation of the new zombie.

### **New Contracts: Code Breakdown:**

***zombieattack.sol:***

This code defines a battle system where two zombies can engage in combat, and the outcome is determined by a random number generated using `randMod`. Depending on the outcome, the zombies' statistics are updated accordingly.

```solidity
import "./zombiehelper.sol";

contract ZombieAttack is ZombieHelper {
  uint randNonce = 0;
  uint attackVictoryProbability = 70;

  function randMod(uint _modulus) internal returns(uint) {
    randNonce++;
    return uint(keccak256(abi.encodePacked(now, msg.sender, randNonce))) % _modulus;
  }
```

1. `import "./zombiehelper.sol";`: This line imports the `zombiehelper.sol` contract, making its functions and variables available for use in the `ZombieAttack` contract.
    
2. `contract ZombieAttack is ZombieHelper { ... }`: This declares the `ZombieAttack` contract, which inherits from the `ZombieHelper` contract. Inheritance means that the `ZombieAttack` contract inherits all the functions and variables of the `ZombieHelper` contract.
    
3. `uint randNonce = 0;`: This line initializes an unsigned integer variable `randNonce` and sets its initial value to 0. It will be used to generate pseudo-random numbers.
    
4. `uint attackVictoryProbability = 70;`: This line initializes an unsigned integer variable `attackVictoryProbability` and sets its initial value to 70. It represents the probability of winning an attack and will be used later in the `attack` function.
    
5. `function randMod(uint _modulus) internal returns(uint) { ... }`: This is a function named `randMod`. It is defined as `internal`, which means it can only be called from within the contract. This function generates a pseudo-random number based on the given `_modulus` and some factors like the current time and sender's address.
    
    * `randNonce++;`: Increments the `randNonce` variable to introduce randomness.
        
    * `return uint(keccak256(abi.encodePacked(now, msg.sender, randNonce))) % _modulus;`: Generates a pseudo-random number by hashing the current time, sender's address (`msg.sender`), and incremented `randNonce`, then taking the remainder when divided by `_modulus`.
        

```solidity
function attack(uint _zombieId, uint _targetId) external ownerOf(_zombieId) {
  Zombie storage myZombie = zombies[_zombieId];
  Zombie storage enemyZombie = zombies[_targetId];
  uint rand = randMod(100);
  if (rand <= attackVictoryProbability) {
    myZombie.winCount++;
    myZombie.level++;
    enemyZombie.lossCount++;
    feedAndMultiply(_zombieId, enemyZombie.dna, "zombie");
  } else {
    myZombie.lossCount++;
    enemyZombie.winCount++;
    _triggerCooldown(myZombie);
  }
}
```

1. `function attack(uint _zombieId, uint _targetId) external ownerOf(_zombieId) { ... }`: This is the `attack` function, which can be called externally. It takes two parameters: `_zombieId` representing the ID of the attacking zombie, and `_targetId` representing the ID of the target zombie. The `ownerOf(_zombieId)` modifier ensures that only the owner of `_zombieId` can call this function.
    
    * `Zombie storage myZombie = zombies[_zombieId];`: Retrieves the attacking zombie's data from the `zombies` array and stores it in the `myZombie` variable.
        
    * `Zombie storage enemyZombie = zombies[_targetId];`: Retrieves the target zombie's data from the `zombies` array and stores it in the `enemyZombie` variable.
        
    * `uint rand = randMod(100);`: Generates a random number between 0 and 99 using the `randMod` function and stores it in the `rand` variable.
        
    * The following conditional statements determine the outcome of the attack based on the randomly generated `rand` value:
        
        * If `rand` is less than or equal to `attackVictoryProbability`, the attacking zombie wins the battle. It increments its `winCount` and `level`, while the enemy zombie's `lossCount` is incremented. Then, it calls the `feedAndMultiply` function with appropriate parameters.
            
        * If `rand` is greater than `attackVictoryProbability`, the attacking zombie loses the battle. It increments its `lossCount`, and the enemy zombie's `winCount` is incremented. The `_triggerCooldown` function is called on the attacking zombie.
            

### **Final Thoughts**

That's it for this review. Although this has been an exhaustive process so far, I feel that I have a better understanding of the structures of smart contracts. This is especially true for `structs`. These values can clearly be seen in the parameters of the functions in contracts and their inheritance. I've also gotten a bit more comfortable with function visibility. However, I still need to do some more due diligence as the choice seems to directly impact both security and gas.

Only two more lessons to go for this series!!! Let's get it done!!!