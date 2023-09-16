---
title: "Solidity Functions"
seoDescription: "Learn about Solidity functions and take a short quiz to test your knowledge."
datePublished: Sat Sep 16 2023 15:04:23 GMT+0000 (Coordinated Universal Time)
cuid: clmm5sz7l000a09id9fm3hue6
slug: solidity-functions
tags: learning, solidity, solidity-basics, learn-solidity

---

### **Overview**

Think of Solidity functions as the architects of Ethereum smart contracts, carefully designing the interactive blueprints that power decentralized applications (DApps). These functions are the cornerstone of every Solidity smart contract, allowing us to manipulate contract state and control execution. In this article, we'll embark on an in-depth exploration of Solidity functions, uncovering their diverse types, access modifiers, and common usage patterns.

## The Blueprint of a Solidity Function

### Declaring Functions

Solidity functions begin with the `function` keyword, followed by the function's name and optional parameters enclosed within parentheses. Here's a standard function declaration:

```solidity
function performTask(uint256 param1, string memory param2) public {
    // The function's logic resides here
}
```

In this illustration, "performTask" is the function's name, and "uint256 param1" and "string memory param2" are its parameters. These are enclosed within parentheses and specify the input values that the function expects. Each parameter consists of a data type and a name. They are separated by commas.

"Public" is an access modifier, which we will discuss further.

### Function Modifiers

Function modifiers, when applied before a function's definition, alter its behavior or restrict access. For example, the "public" modifier grants external access to the function, while the "view" modifier indicates that the function does not alter the contract state.

```solidity
function readOnlyFunction() public view {
    // This function's logic exclusively reads the contract state
}
```

### Visibility of Functions

Solidity functions come in various visibility levels:

* `public`: Offers external access to the function.
    
* `internal`: Restricts access to within the contract and derived contracts.
    
* `private`: Limits access to within the contract.
    
* `external`: Resembles "public" but offers cost-efficient external calls.
    

Let's expand on this a bit. Understanding the different visibility levels is essential for controlling who can access and call your functions within a smart contract.

1. **Public Visibility**:
    
    * **Keyword**: `public`
        
    * **Access**: Any external entity, including other contracts and external transactions, can call a public function.
        
    * **Common Use**: Public functions are often used for actions that need to be accessible and callable from outside the contract. For example, functions that allow users to interact with the contract, such as transferring tokens or querying data.
        
    
    Example:
    
    ```solidity
    function transferTokens(address to, uint256 amount) public {
        // Logic to transfer tokens and update balances
    }
    ```
    
2. **Internal Visibility**:
    
    * **Keyword**: `internal`
        
    * **Access**: Functions with internal visibility can only be accessed from within the contract and any derived contracts (i.e., contracts that inherit from the current contract).
        
    * **Common Use**: Internal functions are typically used for helper functions or functions that should not be exposed to external entities. They can be utilized to factor out common logic in a contract.
        
    
    Example:
    
    ```solidity
    function _updateBalance(address account, uint256 amount) internal {
        // Update the balance internally
    }
    ```
    
3. **Private Visibility**:
    
    * **Keyword**: `private`
        
    * **Access**: Private functions are the most restricted. They can only be accessed from within the current contract.
        
    * **Common Use**: Private functions are used for internal bookkeeping, helper functions, or any logic that should be completely hidden from the outside world. They are not accessible even to derived contracts.
        
    
    Example:
    
    ```solidity
    function _calculateInterest() private returns (uint256) {
        // Calculate interest privately
    }
    ```
    
4. **External Visibility**:
    
    * **Keyword**: `external`
        
    * **Access**: Similar to public functions, external functions can be called externally, but they are more gas-efficient when called from outside the contract. External functions cannot be accessed internally within the contract itself.
        
    * **Common Use**: External functions are suitable for operations that need to be accessible externally, such as contract interaction and interface implementations.
        
    
    Example:
    
    ```solidity
    function someExternalFunction(address otherContract) external {
        // Perform an operation with an external contract
    }
    ```
    

Choosing the appropriate visibility level for your functions is crucial for maintaining security and access control in your smart contracts. Careful consideration of who should have access to specific functions is essential for the overall design and functionality of your decentralized application.

### Function Return Types

Functions in Solidity can return data to the caller using the "returns" keyword. Return types can be scalar (e.g., "uint256," "bool") or complex (e.g., arrays, structs).

```solidity
function fetchNumber() public view returns (uint256) {
    // Return a uint256 value
    return someValue;
}
```

The `returns` keyword is used in function declarations to specify the data type(s) that a function will return. Whether a function includes `returns` or not depends on whether the function is meant to return a value or not.

1. **Functions without** `returns`: Functions that don't include a `returns` statement are typically used for actions that don't return any data to the caller. These functions are often used for state changes or operations that modify the blockchain state in some way. For example, functions that update state variables, perform calculations, or trigger events may not need a return statement because they are not expected to produce a result that the caller needs.
    
    Example:
    
    ```solidity
    function updateValue(uint256 newValue) public {
        // Update a state variable without returning any data
        myStateVariable = newValue;
    }
    ```
    
2. **Functions with** `returns`: Functions that include a `returns` statement are used when you want the function to return one or more values to the caller. These functions are typically used for querying data from the contract or performing read-only operations that don't modify the contract's state. The `returns` statement specifies the data type(s) of the value(s) that the function will return.
    
    Example:
    
    ```solidity
    function getValue() public view returns (uint256) {
        // Return the value of a state variable
        return myStateVariable;
    }
    ```
    
    In this example, the `getValue` function is declared with a `returns (uint256)` statement, indicating that it returns a `uint256` value.
    
3. **Functions with multiple return values:** Solidity allows functions to return multiple values by specifying them within parentheses in the `returns` statement.
    
    Example:
    
    ```solidity
    function getValues() public view returns (uint256, string memory) {
        // Return multiple values
        return (myStateVariable, "Hello, World!");
    }
    ```
    
    Here, the `getValues` function returns both a `uint256` and a `string`.
    

In summary, the presence or absence of the `returns` statement in a Solidity function declaration indicates whether the function is intended to return data to the caller. Functions without `returns` are typically used for state-changing operations, while functions with `returns` are used for querying and returning data from the contract. Multiple return values can also be specified using the `returns` statement.

## Types of Functions and Their Applications

### State-Altering Functions

State-altering functions change the contract's state and typically require a transaction for execution. These functions are often marked as "public" or "external" and are responsible for tasks like token transfers, balance updates, and ownership changes.

```solidity
function transferTokens(address to, uint256 amount) public {
    // Logic to transfer tokens and update balances
}
```

### Read-Only Functions

Read-only functions are incapable of altering the contract's state; they are marked as "view" or "pure." These functions are crucial for retrieving data from the blockchain without incurring gas costs.

```solidity
function checkBalance(address account) public view returns (uint256) {
    // Retrieve an account's balance
}
```

### Constructor Functions

The constructor is a unique function that runs exclusively during contract deployment. Its primary role is initializing the contract's state variables and performing setup tasks.

```solidity
constructor() {
    owner = msg.sender;
}
```

Let's use a coffee-related analogy to explain a constructor in Solidity:

**Constructor in Solidity = Brewing a Fresh Cup of Coffee**

1. **Coffee Preparation**:
    
    * **Constructor**: In Solidity, a constructor is akin to preparing the coffee maker before brewing a fresh cup. It sets the stage for the contract's operation.
        
    * **Brewing Coffee**: Brewing coffee begins with preparing the coffee maker, ensuring you have the right amount of coffee grounds, water, and settings adjusted for the desired strength.
        
2. **Ingredients and Configuration**:
    
    * **Constructor**: During contract deployment, the constructor specifies the initial state variables and configurations, just as you select the type of coffee, water temperature, and cup size.
        
    * **Brewing Coffee**: When brewing coffee, you choose the specific ingredients (coffee beans or grounds), water-to-coffee ratio, and other parameters that define the coffee's flavor and characteristics.
        
3. **Unique Coffee Blends**:
    
    * **Constructor**: Each Solidity contract can have its own constructor, tailored to define the unique characteristics and functions of that contract, much like selecting different coffee blends or flavors.
        
    * **Brewing Coffee**: Different coffee blends or types (e.g., Colombian, Ethiopian, French Roast) offer distinct taste profiles and experiences, much like how different contracts have unique purposes and features.
        
4. **One-Time Brewing**:
    
    * **Constructor**: The constructor is executed only once during contract deployment, establishing the initial contract conditions. It doesn't run again once the contract is deployed.
        
    * **Brewing Coffee**: Brewing a cup of coffee is a one-time process. Once you've brewed a cup, you don't need to set up the coffee maker again until you're ready for the next brew.
        
5. **Serving Satisfaction**:
    
    * **Constructor**: The constructor aims to set the stage for successful contract interactions, much like brewing coffee aims to provide a satisfying and enjoyable coffee-drinking experience.
        
    * **Brewing Coffee**: Brewing coffee sets the stage for enjoying a delicious cup of coffee that satisfies your taste buds and energizes you for the day.
        

In both cases, whether it's a Solidity contract or brewing coffee, the constructor or coffee preparation process is essential for defining the initial conditions and configurations. It ensures that everything is in place for a successful outcome, whether in the world of smart contracts or the world of coffee enthusiasts.

## Function Modifiers and Access Control

Modifiers play a pivotal role in imposing access controls and conditions on functions. They are particularly valuable for ensuring that only authorized users can execute specific functions.

```solidity
modifier onlyOwner() {
    require(msg.sender == owner, "Only the owner can invoke this function");
    _; // Proceed with the function logic if the condition is met
}

function transferOwnership(address newOwner) public onlyOwner {
    // Logic to transfer contract ownership
}
```

Let's use a traffic-related analogy to explain modifiers:

1. **Traffic Signals and Rules**:
    
    * **Modifiers**: In Solidity, modifiers are like traffic signals and rules on the road. They control and regulate the flow of functions and transactions within a smart contract.
        
    * **Traffic Signals**: Traffic signals and road rules dictate how vehicles move on the road, ensuring safety and order.
        
2. **Traffic Light Colors**:
    
    * **Modifiers:** Think of modifiers as traffic light colors. Each modifier serves as a signal that can allow, restrict, or modify the behavior of a function.
        
    * **Traffic Light Colors**: Traffic lights use different colors (green, yellow, red) to indicate when to proceed, slow down, or stop. Similarly, modifiers signal when a function can execute, under what conditions, or if it's restricted.
        
3. **Stop Sign** (Access Control Modifier):
    
    * **Modifiers**: An access control modifier, like "onlyOwner," is similar to a stop sign. It restricts access to certain functions, allowing only authorized parties to proceed.
        
    * **Stop Sign**: A stop sign at an intersection mandates that vehicles come to a complete halt before proceeding. Similarly, an "onlyOwner" modifier ensures that only the contract owner can execute a specific function.
        
4. **Speed Limit** (Validation Modifier):
    
    * **Modifiers**: Validation modifiers, like "require," can be compared to speed limits. They impose conditions that must be met before a function can proceed.
        
    * **Speed Limit**: Speed limits on the road set maximum allowable speeds. If you exceed the limit, you are required to slow down. In Solidity, the "require" modifier ensures that specific conditions are met before executing the function.
        
5. **Turn Signals** (Behavior Modifier):
    
    * **Modifiers**: Behavior modifiers, such as "before" or "after," are like turn signals. They dictate actions to be taken before or after a function's execution.
        
    * **Turn Signals**: In driving, using turn signals informs others of your intended actions. Behavior modifiers signal what actions or conditions should be executed before or after a function runs.
        
6. **Traffic Cop** (Custom Modifiers):
    
    * **Modifiers**: Custom modifiers act like traffic cops. They enforce specific rules and conditions unique to the contract's requirements.
        
    * **Traffic Cop**: A traffic cop can direct traffic, handle special situations, and enforce localized rules. Similarly, custom modifiers in Solidity enforce specific contract-specific conditions and behaviors.
        

In both scenarios, whether on the road or in a smart contract, modifiers are crucial for enforcing rules, ensuring safety, and controlling the flow of actions. They play a vital role in maintaining order and preventing unwanted or unsafe behavior.

## Best Practices

* **Maintain Function Simplicity**: Adhere to the Single Responsibility Principle (SRP) and keep functions focused on specific tasks.
    
* **Leverage Modifiers**: Harness modifiers for access control and input validation.
    
* **Guard Against Gas Limits**: Be gas-conscious and avoid loops and blocking calls within functions.
    
* **Thorough Testing**: Rigorously test functions and edge cases using tools such as Truffle and Remix.
    

### **Quiz**

Let's test what we have learned. The answers are at the bottom. I suggest writing your answers down and checking them at the end of the quiz.

Here's a 10-question multiple-choice quiz to help *solidify* what we've learned:

**Question 1:** What is the general structure of a Solidity function?

A. functionName(parameters) visibility modifiers returns (returnType) { ... }

B. functionName(parameters) visibility returns (returnType) { ... }

C. functionName(parameters) modifiers returns (returnType) { ... }

D. functionName(parameters) { ... }

**Question 2:** What is the purpose of the "public" access modifier in a Solidity function?

A. It restricts access to within the contract and derived contracts.

B. It allows external entities to call the function.

C. It makes the function view-only.

D. It prevents the function from being executed.

**Question 3:** Which visibility level in Solidity restricts access to within the contract and derived contracts?

A. public

B. internal

C. private

D. external

**Question 4:** When is a constructor function executed in Solidity?

A. Whenever the contract is deployed.

B. Whenever an external function is called.

C. It runs continuously in the background.

D. It is executed only once during contract deployment.

**Question 5:** What is the primary role of a constructor in Solidity?

A. To modify the contract state.

B. To define external functions.

C. To initialize the contract's state variables and perform setup tasks.

D. To return values to the caller.

**Question 6:** In Solidity, which keyword is used to specify the data type(s) that a function will return?

A. returns

B. view

C. memory

D. pure

**Question 7:** Which type of Solidity function can change the contract's state and typically requires a transaction?

A. Constructor functions

B. Read-only functions

C. State-altering functions

D. Modifier functions

**Question 8:** What is the primary purpose of modifiers in Solidity?

A. To modify the behavior of a function.

B. To declare variables.

C. To create new functions.

D. To define state variables.

**Question 9:** Which modifier is commonly used for access control, allowing only authorized users to execute a specific function?

A. view

B. internal

C. require

D. onlyOwner

**Question 10:** Which of the following is NOT a common visibility level for Solidity functions?

A. internal

B. protected

C. public

D. external

**<mark>Answers:</mark>**

1. A
    
2. B
    
3. B
    
4. D
    
5. C
    
6. A
    
7. C
    
8. A
    
9. D
    
10. B
    

## Conclusion

In the world of Ethereum smart contracts, Solidity functions are akin to master architects, constructing the foundations of decentralized applications. Understanding the diverse types, modifiers, and best practices associated with Solidity functions is paramount when crafting secure, efficient, and dependable smart contracts. By harnessing the capabilities of Solidity functions, you embark on a journey to revolutionize the blockchain landscape, redefining the way we interact with this groundbreaking technology.