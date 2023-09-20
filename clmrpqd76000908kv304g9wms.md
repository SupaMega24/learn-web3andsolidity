---
title: "Getter and Enum Functions"
datePublished: Wed Sep 20 2023 12:21:04 GMT+0000 (Coordinated Universal Time)
cuid: clmrpqd76000908kv304g9wms
slug: getter-and-enum-functions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695212281416/6aeb5f8f-8968-479f-9974-931e76259442.png
tags: learning, solidity

---

I know that I previously wrote about what I've learned about Solidity functions, but I've recently picked up two more terms to add to that. These are "getter functions" and "enum functions," which play a crucial role in designing smart contracts. In this blog post, we'll explore what these functions are, why they are important, and how to use them effectively.

## Getter Functions

Getter functions, also known as read-only functions, are an essential part of any smart contract. They provide a way to access the current state or data stored within a contract without modifying that data. Think of them as windows through which you can view, but not touch, the contents of a contract.

```solidity
solidityCopy codefunction getMyData() public view returns (uint) {
    return myData;
}
```

In this example, `getMyData` is a getter function that retrieves the value of the `myData` state variable. The `view` keyword indicates that this function doesn't modify the contract's state, and `returns (uint)` specifies that it returns an unsigned integer.

**Analogy: The Bank Statement**

Imagine you have a bank account, and you want to check your account balance. However, you can't just walk into the bank vault and peek at your account details whenever you want. The bank vault is like a smart contract, and your account balance is one of its state variables—private and inaccessible to anyone but the bank.

So, how do you find out your account balance? You ask the bank for a statement, which they provide regularly. This statement is like a getter function in Solidity. It doesn't allow you to make any changes or transactions in your account; it merely shows you your current balance and recent transactions.

Here's how the analogy fits:

1. **Bank Account**: This is your smart contract, which holds various pieces of information.
    
2. **Bank Statement**: This is the getter function. It's a predefined way for you to access specific information (like your account balance) from your account without being able to alter anything inside the vault (contract).
    
3. **Vault Access**: Just as you can't access the vault directly, external applications and contracts can't directly access the state variables of a smart contract. They need to use getter functions.
    
4. **Security**: The bank statement ensures the security of your account details. Similarly, getter functions in Solidity maintain the integrity and security of contract data by providing controlled read-only access.
    
5. **Information Request**: You can request your bank statement whenever you need it. Similarly, external parties can call getter functions whenever they need specific information from a smart contract.
    

So, in essence, getter functions are like the "bank statements" of smart contracts, allowing external entities to safely inquire about the contract's data without compromising its security or functionality.

### Enum Functions

Enums, short for "enumerations," are user-defined data types in Solidity. Enum functions, or enum-related operations, are functions that work with enum types. Enums are used to define a set of constant values that represent discrete options within a category.

Enum functions are typically straightforward to define. First, you need to create an enum type:

```solidity
solidityCopy codeenum Season { Spring, Summer, Autumn, Winter }
```

Then, you can create functions that utilize this enum:

```solidity
solidityCopy codefunction isSummer(Season season) public pure returns (bool) {
    return season == Season.Summer;
}
```

In this example, `isSummer` is an enum function that checks if a given `Season` value is equal to `Summer`. The `pure` keyword indicates that this function doesn't access contract state.

**Analogy: Days of the Week at a Library**

Imagine you're a librarian, and you want to categorize books based on the day of the week they were borrowed. You can use an `enum` to represent the days of the week:

```solidity
solidityCopy codeenum DaysOfWeek {
    Monday,
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Saturday,
    Sunday
}
```

Now, let's understand how `enum` functions in Solidity are analogous to this library scenario:

1. **Book Categorization**: In your library, you have different books borrowed on different days. These days represent distinct categories, just like the elements in the `enum`.
    
2. **Enum Definition**: You define an `enum` called `DaysOfWeek`, which lists all the days of the week. This is similar to how you create an `enum` in Solidity to define a set of possible values.
    
3. **Labeling Books**: When a book is borrowed, you label it with the day of the week it was borrowed on. This label serves as an identifier for the book within its category. In Solidity, you use `enum` values to label or categorize data.
    
4. **Catalog Search**: Suppose someone wants to find all the books borrowed on a Tuesday. To do this, you write a function in your library system that accepts the day of the week (an `enum` value) as input and returns a list of books borrowed on that day. Similarly, in Solidity, you can write functions that use `enum` values as parameters to filter and retrieve data.
    
5. **Error Prevention**: Using `enum` ensures that you can only categorize books into specific days of the week. You can't mistakenly label a book as "Weekend" because it's not a valid `enum` value. Similarly, `enum` in Solidity restricts the possible values a variable can have, preventing unexpected data.
    
6. **Clear Communication**: When someone asks you for books borrowed on a particular day, they don't need to know the underlying mechanics of your library system. They can simply provide the day (an `enum` value), and your system handles the rest. Similarly, in Solidity, `enum` values make interactions with contracts more human-readable and straightforward.
    

In summary, `enum` functions in Solidity work like your library's categorization system, helping you organize and classify data into predefined categories. Just as your library system simplifies book retrieval based on days of the week, Solidity `enum` values streamline data handling in smart contracts by providing clear, predefined options for categorization and identification.

### **Quiz**

Let's test our knowledge with a multiple-choice quiz based on the blog post:

**1\. What is a getter function in Solidity?**

a. A function that modifies contract state.

b. A function that provides controlled read-only access to contract data.

c. A function that allows external entities to alter contract data.

**2\. Which keyword indicates that a Solidity function is read-only and doesn't modify contract state?**

a. modify

b. view

c. read\_only

**3\. What is an enum in Solidity?**

a. A user-defined data type that represents a set of constant values.

b. A function that modifies contract state.

c. A function that provides external access to contract data.

**4\. How are enum functions in Solidity similar to the "Days of the Week at a Library" analogy?**

a. Enum functions allow you to directly access contract state.

b. Enum functions categorize books based on their titles.

c. Enum functions categorize data into predefined categories, just like days of the week categorize books.

**5\. Why do we use enum values in Solidity?**

a. To allow external entities to modify contract data.

b. To restrict possible variable values and prevent unexpected data.

c. To define complex mathematical operations within contracts.

***Here are the answers!***

Certainly! Here are the answers to the quiz questions:

**1\. What is a getter function in Solidity?**

**Answer: b. A function that provides controlled read-only access to contract data.**

**2\. Which keyword indicates that a Solidity function is read-only and doesn't modify contract state?**

**Answer: b. view**

**3\. What is an enum in Solidity?**

**Answer: a. A user-defined data type that represents a set of constant values.**

**4\. How are enum functions in Solidity similar to the "Days of the Week at a Library" analogy?**

**Answer: c. Enum functions categorize data into predefined categories, just like days of the week categorize books.**

**5\. Why do we use enum values in Solidity?**

**Answer: b. To restrict possible variable values and prevent unexpected data.**