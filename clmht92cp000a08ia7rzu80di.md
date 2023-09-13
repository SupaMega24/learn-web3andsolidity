---
title: "State Variables: Review"
seoDescription: "Basics of Solidity, smart contracts, and state variables"
datePublished: Wed Sep 13 2023 14:01:54 GMT+0000 (Coordinated Universal Time)
cuid: clmht92cp000a08ia7rzu80di
slug: state-variables-review
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694613590085/0dee67ed-d2c6-4919-adc6-e86ce4141de9.png
tags: learning, solidity, web3, smart-contracts, learncodeonline

---

### **Overview**

In Solidity, state variables are used to represent and store data on the Ethereum blockchain. They have a specific storage location on the blockchain and persist between function calls. State variables are declared at the contract level, meaning they are part of the contract's storage and are not limited to the scope of a specific function.

Let's see what some code might look like:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ExampleContract {
    // State variables
    uint256 public myNumber;  // A public state variable that can be read by anyone
    address public owner;    // A public state variable to store an Ethereum address

    // Constructor to initialize state variables
    constructor() {
        myNumber = 42;
        owner = msg.sender;  // The sender of the transaction is set as the owner
    }

    // Function to update the state variable
    function setMyNumber(uint256 _newNumber) public {
        require(msg.sender == owner, "Only the owner can change this value");
        myNumber = _newNumber;
    }
}
```

In the above example, `myNumber` and `owner` are state variables of the `ExampleContract`. They are declared at the contract level and can be accessed and modified by functions within the contract.

Key points to remember about state variables in Solidity:

1. They are stored on the Ethereum blockchain and have a persistent state.
    
2. You can specify the visibility of state variables using access modifiers like `public`, `internal`, `private`, or `internal`.
    
3. State variables are gas-costly to modify, so you should carefully design your contracts to minimize storage changes.
    
4. State variables can be read by external contracts and users.
    
5. You can initialize state variables in the constructor or set them in functions with appropriate access control (as shown in the example).
    
6. State variables have a default value if not explicitly initialized. For example, numeric types like `uint256` have a default value of 0, and addresses have a default value of `address(0)`.
    
7. Modifying state variables may require transactions and gas fees. Reading them is generally free and can be done using constant (view or pure) functions.
    

Keep in mind that state variables play a crucial role in smart contract development, and careful consideration of their design and usage is essential to ensure the security and efficiency of your contracts on the Ethereum blockchain. Let's delve a bit deeper to learn more.

### **Analogy**

Imagine you're managing a library, and you have a ledger that keeps track of all the books in your library. In this analogy:

1. **The Ledger:** The ledger itself represents the blockchain or the contract's storage. It's where you record all the important information about the books (state) in your library.
    
2. **State Variables:** Each entry in the ledger is like a state variable. For example, you have a column for the book title, another for the author, one for the publication year, and so on. These columns are similar to state variables, each holding a specific piece of information about the books.
    
3. **Initialization:** When you first open the library, you initialize the ledger with some default values. For instance, you might record the current date as the library's opening date. Similarly, in a Solidity contract, you initialize state variables in the constructor function.
    
4. **Updates:** As books are borrowed or returned, you update the ledger. If a new book arrives, you add a new entry. If a book is checked out, you mark it as "borrowed." In Solidity, you update state variables with transactions, changing their values as needed based on the contract's logic.
    
5. **Privacy and Access Control:** Some parts of the ledger might be public, like the book titles and authors, which anyone can see. Others might be private, like the library's financial records, which only the library manager (the owner) can access. Similarly, in Solidity, you can control the visibility of state variables using access modifiers like `public`, `private`, and so on.
    
6. **Historical Record:** The ledger provides a historical record of all activities related to the library's books. Similarly, Solidity state variables maintain a historical record of changes made to them on the blockchain, accessible to anyone who wants to inspect the blockchain's history.
    

In the analogy of a library ledger, we can create a simplified Solidity smart contract to represent this concept. The contract will have state variables to keep track of books in the library, and functions to update and access this information. Here's a basic example:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Library {
    // Struct to represent a book
    struct Book {
        string title;
        string author;
        uint256 publicationYear;
        bool isCheckedOut;
    }

    // Mapping to store books by their unique identifiers (ISBN)
    mapping(uint256 => Book) public books;

    // Address of the library owner
    address public owner;

    // Event to log book checkout
    event BookCheckedOut(uint256 indexed isbn, address borrower);

    constructor() {
        owner = msg.sender;
    }

    // Function to add a new book to the library
    function addBook(uint256 isbn, string memory title, string memory author, uint256 publicationYear) public {
        require(msg.sender == owner, "Only the owner can add books.");
        require(!books[isbn].isCheckedOut, "Book with this ISBN is already checked out.");
        
        books[isbn] = Book(title, author, publicationYear, false);
    }

    // Function to check out a book
    function checkOutBook(uint256 isbn) public {
        require(!books[isbn].isCheckedOut, "Book is already checked out.");
        
        books[isbn].isCheckedOut = true;
        emit BookCheckedOut(isbn, msg.sender);
    }

    // Function to check if a book is available
    function isBookAvailable(uint256 isbn) public view returns (bool) {
        return !books[isbn].isCheckedOut;
    }
}
```

In this Solidity contract:

* `Book` is defined as a struct to represent individual books, with attributes like title, author, publication year, and a boolean flag to indicate if the book is checked out.
    
* `books` is a mapping that stores books by their unique ISBN (an unsigned integer).
    
* `owner` is an address variable representing the library owner.
    
* The constructor sets the owner to the contract deployer.
    
* `addBook` allows the owner to add new books to the library.
    
* `checkOutBook` lets anyone borrow a book, marking it as checked out.
    
* `isBookAvailable` checks whether a book is available for borrowing.
    

This contract simulates the management of books in a library using Solidity state variables and functions. It's important to note that I am a noob who is still learning. In a real-world scenario, additional features and security measures would definitely be needed.

### **Examples**

Here are some examples of state variables that I have encountered in my learning. We'll explore different data types, access modifiers, and use cases for state variables.

1. **Simple State Variable:**
    
    ```solidity
    // Simple state variable to store an integer
    uint256 public myNumber;
    
    constructor() {
        myNumber = 42; // Initialize myNumber to 42 in the constructor
    }
    ```
    
    In this example, `myNumber` is a state variable of type `uint256`. It's publicly accessible, and its initial value is set to 42 in the constructor.
    
2. **State Variable with Access Control:**
    
    ```solidity
    address public owner;
    uint256 private secretNumber;
    
    constructor() {
        owner = msg.sender; // Initialize owner to the contract deployer's address
        secretNumber = 12345; // Initialize secretNumber privately
    }
    
    function changeSecretNumber(uint256 _newSecret) public {
        require(msg.sender == owner, "Only the owner can change the secret number");
        secretNumber = _newSecret;
    }
    ```
    
    Here, `owner` is publicly readable but can only be modified by the contract deployer. `secretNumber` is private and can only be changed by the owner through the `changeSecretNumber` function.
    
3. **State Variable Arrays:**
    
    ```solidity
    // Dynamic array of integers
    uint256[] public numbers;
    
    constructor() {
        numbers.push(1);
        numbers.push(2);
        numbers.push(3);
    }
    
    function addNumber(uint256 _newNumber) public {
        numbers.push(_newNumber);
    }
    ```
    
    In this case, we have a dynamic array `numbers` of type `uint256`. The `addNumber` function allows you to add elements to this array.
    
4. **Mapping State Variable:**
    
    ```solidity
    // Mapping to store balances of users
    mapping(address => uint256) public balances;
    
    function deposit() public payable {
        balances[msg.sender] += msg.value;
    }
    ```
    
    This example uses a mapping to store the balances of users. When someone calls the `deposit` function and sends Ether, their balance in the `balances` mapping is updated.
    
5. **Struct State Variable:**
    
    ```solidity
    struct Person {
        string name;
        uint256 age;
    }
    
    Person[] public people;
    
    function addPerson(string memory _name, uint256 _age) public {
        Person memory newPerson = Person(_name, _age);
        people.push(newPerson);
    }
    ```
    
    Here, we define a `Person` struct and maintain an array of people as a state variable. The `addPerson` function allows you to add new people to the array.
    
6. **Enum State Variable:**
    
    ```solidity
    enum State { Inactive, Active, Paused }
    State public state;
    
    constructor() {
        state = State.Inactive;
    }
    
    function activate() public {
        state = State.Active;
    }
    ```
    
    This example uses an `enum` to represent different states. The `state` state variable can be changed using the `activate` function.
    

These are some very basic examples. I hope to become more fluent in Solidity coding through practice, reviewing my notes above, and engaging in other communities sush as Alchemy and Daily Devs. As always, constructive criticism is welcome. I'm sure I've made some learning points above. See you in the next post.