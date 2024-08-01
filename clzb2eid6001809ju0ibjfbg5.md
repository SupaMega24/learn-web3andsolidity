---
title: "Account Abstraction: The zkSync Way"
datePublished: Thu Aug 01 2024 09:19:51 GMT+0000 (Coordinated Universal Time)
cuid: clzb2eid6001809ju0ibjfbg5
slug: account-abstraction-the-zksync-way
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/EbbqeyHpbto/upload/6888494486dfa3ea5394b8cdc3b0e597.jpeg
tags: learning, solidity, web3, smart-contracts, account-abstraction

---

### Benefits of Account Abstraction

Welcome, everyone! Today, we're diving into the fascinating world of **Account Abstraction**, a concept that's gaining traction in the realm of web3 development.

**If you already have a good idea about what it is and want to learn how to build it, then you can**[**jump straight to the free course here on CyfrinUpdraft**](https://updraft.cyfrin.io/)**.**

Think of it as a toolkit that can make using blockchain systems easier, more flexible, and more secure. But why is it so beneficial? Let’s break it down.

**1\. Enhanced Flexibility**

Traditional blockchain accounts are pretty rigid. They operate under a set of predefined rules, much like a one-size-fits-all t-shirt. But instead of a t-shirt, you've got a wallet. In order to use that wallet, you need to keep up with a traditional password plus:

* a set of seed phrases that can be anywhere from 12 to 24 words long
    
* a very long private key
    
* if you lose your private key or it gets stolen, say bye to your funds
    
* only one way to handle transactions
    

Account abstraction, on the other hand, allows users to define their own rules for how their accounts should work. Imagine customizing that t-shirt to fit perfectly – that's the kind of flexibility we're talking about. This means you can tailor the way transactions are handled, define custom authorization logic, and even integrate advanced security features. You could even have someone else pay for your transactions.

**2\. Improved Security**

Security is a huge deal in the blockchain world. With account abstraction, you can enhance the security of your accounts by incorporating multi-signature wallets or smart contracts that can control access. This is like having a vault that requires multiple keys to open – one key simply isn’t enough. It adds layers of protection against hacks and unauthorized access, making your assets much safer.

**3\. Better User Experience**

Let’s be honest, interacting with the blockchain can sometimes be a bit daunting, especially for newcomers. Account abstraction can simplify this process. It allows for features like meta-transactions, where a third party can pay for your transaction fees, making the experience smoother and more user-friendly. Think of it as going to a theme park where someone else buys your tickets – you just enjoy the rides.

**4\. Interoperability**

Account abstraction facilitates better interoperability between different blockchain networks. It’s like speaking multiple languages – you can easily communicate and interact with different systems without much hassle. This can pave the way for more cohesive and connected blockchain ecosystems, where moving assets or data across different networks becomes seamless.

**5\. Customizable Recovery Options**

Losing access to your account can be a nightmare. With traditional accounts, losing your private key often means losing access to your assets forever. Account abstraction can introduce customizable recovery options, such as social recovery, where trusted contacts can help you regain access. It's like having a spare key to your house with a trusted friend – you’re never completely locked out.

In summary, account abstraction is a game-changer in the blockchain space. It brings flexibility, security, improved user experience, interoperability, and customizable recovery options. It's like upgrading from a basic phone to a smart one – once you experience it, you'll wonder how you ever managed without it.

Next up, we'll explore what zkSync has to do with account abstraction. Stay tuned!

### What's zkSync Got to Do With It?

By now, you’re probably wondering, “What’s zkSync got to do with account abstraction?” Great question! Let’s dive into it.

**What is zkSync?**

Before we get into the relationship between the two, let’s quickly understand what zkSync is. [zkSync](https://zksync.io/) is a Layer 2 scaling solution for Ethereum. It uses zero-knowledge rollups (zk-rollups) to bundle multiple transactions into a single one, which is then verified on the Ethereum mainnet. This process significantly reduces transaction fees and increases the throughput, making the Ethereum network more scalable and efficient.

**Account Abstraction on zkSync**

zkSync leverages the concept of account abstraction to enhance the user experience and security of its platform. Let’s delve into a specific aspect of zkSync that makes account abstraction so powerful: the smart accounts and paymasters. This might sound a bit technical at first, but don’t worry – we’ll break it down step by step.

**What are Smart Accounts and Paymasters?**

On Ethereum, there are two types of accounts: externally owned accounts (EOAs) and contract accounts. EOAs can initiate transactions, while contract accounts can implement arbitrary logic. This separation can be burdensome for users.

zkSync Era addresses this issue by allowing accounts to both initiate transactions and implement arbitrary logic, essentially combining EOAs and contract account functionality into one. Furthermore **Account Abstraction** fundamentally changes how accounts operate by introducing the concepts of smart accounts and paymasters.

**Smart Accounts**

Smart accounts in zkSync are fully programmable, allowing for various customizations that enhance security, flexibility, and user experience. Here’s how:

**1\. Custom Signature Schemes**

Smart accounts can use custom signature schemes beyond the standard Ethereum signatures. This includes support for advanced cryptographic methods, enhancing security and allowing users to choose the signature method that best fits their needs.

**2\. Native Multi-Signature Capabilities**

Multi-signature (multi-sig) capabilities are built directly into smart accounts. This means you can require multiple approvals for transactions, adding an extra layer of security. It’s like having a safe that needs multiple keys to open – ensuring that no single point of failure can compromise your assets.

**3\. Spending Limits**

Smart accounts can enforce spending limits, either on a per-transaction basis or over a specified period. This feature helps in managing risk by preventing excessive withdrawals and ensuring that even if an account is compromised, the potential damage is minimized.

**4\. Application-Specific Restrictions**

You can set up smart accounts with application-specific restrictions. For instance, an account could be programmed to interact only with certain dApps or smart contracts, adding a layer of control over how funds are used. This is particularly useful for organizations that need to ensure funds are used according to predefined rules and policies.

**Paymasters**

Paymasters are another innovative feature in zkSync that can sponsor transactions for users, allowing them to pay transaction fees in ERC20 tokens instead of ETH. This significantly enhances the user experience by making it more accessible and flexible.

**1\. Transaction Fee Sponsorship**

Paymasters can cover the gas fees for users, enabling transactions without the need for users to hold ETH. This is particularly beneficial for new users who might not have ETH or for applications aiming to streamline the onboarding process.

**2\. ERC20 Token Payments**

With paymasters, users can pay transaction fees in ERC20 tokens. This flexibility means users aren’t restricted to using ETH for fees, making the overall process more convenient and user-friendly. It’s like being able to pay for groceries with any currency, not just cash.

**3\. Enhanced User Experience**

By sponsoring transaction fees and allowing payments in various tokens, paymasters make interacting with zkSync more intuitive and less cumbersome. This ease of use is crucial for the broader adoption of blockchain technology, as it lowers the barriers to entry for everyday users.

Up next, we'll delve into the different types of transactions that can be enabled through account abstraction in zkSync. Stay with us!

### Transaction Type 113 Lifecycle

**What is Transaction Type 113?**

Transaction Type 113 is a specialized transaction designed to facilitate account abstraction on zkSync. It allows for the inclusion of custom logic within transactions, enabling more complex operations and greater flexibility compared to standard transactions.

It's important to note that transactions in zkSync have a lifecycle or phases that they go through to completion. If we were to create a minimal account abstraction account at simple level, our lifecycle would look something like this.

### Two-Phase Lifecycle of Transactions in zkSync

Let’s dive into the two-phase lifecycle of transactions in zkSync, which ensures efficient, secure, and reliable processing of transactions. We’ll break it down into two key phases: Validation and Execution.

***NOTE: I learned the following breakdown in my course at*** [***CyfrinUpdraft***](https://updraft.cyfrin.io/)***.***

---

**Phase 1: Validation**

The validation phase ensures that all transactions are checked for correctness and are ready for processing. Here’s a step-by-step breakdown:

**1\. Transaction Submission:**

The user initiates the transaction through the “zkSync API client,” which acts as a lightweight node that interacts with zkSync’s infrastructure. This client submits the transaction for validation.

**2\. Nonce Check:**

The zkSync API client first checks that the transaction nonce is unique. It does this by querying the `NonceHolder` system contract to ensure that the nonce hasn’t been used already. This step prevents replay attacks and ensures transaction uniqueness.

**3\. Transaction Validation:**

The zkSync API client then calls the `validateTransaction` function. This function must update the nonce to prevent any potential conflicts with future transactions. It’s crucial that this step is executed properly to maintain transaction order and integrity.

**4\. Nonce Update Verification:**

After updating the nonce, the zkSync API client verifies that the nonce was indeed updated correctly. This step ensures that the transaction state is consistent and that no conflicts arise.

**5\. Payment Preparation:**

Next, the zkSync API client handles payment for the transaction. It calls `payForTransaction` if the transaction fees are paid directly. If a paymaster is involved, the client uses `prepareForPaymaster` and `validateAndPayForPaymasterTransaction` to prepare and verify the payment process.

**6\. Bootloader Payment Verification:**

Finally, the zkSync API client confirms that the bootloader, which processes and finalizes the transaction, has been paid. This step ensures that all necessary fees are covered before moving on to execution.

---

**Phase 2: Execution**

Once validation is complete, the transaction moves to the execution phase, where it is processed and finalized. Here’s how it works:

**1\. Transaction Submission to Main Node/Sequencer:**

The validated transaction is passed from the zkSync API client to the main node or sequencer. As of now, these roles are fulfilled by the same entity. This step transitions the transaction from validation to actual execution.

**2\. Transaction Execution:**

The main node or sequencer then calls the `executeTransaction` function. This function performs the core operations of the transaction, updating account states and processing the transaction as specified.

**3\. Post-Transaction Handling (if applicable):**

If a paymaster was involved in the transaction, the `postTransaction` function is called. This function handles any final steps required for transactions that use a paymaster, ensuring that all aspects of the transaction are completed correctly.

---

In summary, the two-phase lifecycle of transactions in zkSync involves rigorous validation and precise execution steps. During the Validation phase, transactions are checked for correctness, nonce uniqueness, and proper payment. The Execution phase then processes the transaction, ensuring all operations are carried out as intended. This structured approach helps zkSync maintain high efficiency, security, and reliability for all transactions.

Next, we’ll explore the system contracts that play a vital role in zkSync’s architecture.

### System Contracts in zkSync

In blockchain systems like zkSync, a system contract is a special type of smart contract that performs essential functions for the protocol's operation. Unlike user contracts, which are created by and interact with end-users, system contracts are pre-deployed and manage core aspects of the protocol's infrastructure. They handle critical operations such as nonce management, transaction validation, contract deployment, and more.

System contracts are integral to the protocol’s stability and performance. They ensure that transactions are processed correctly, that state changes are managed efficiently, and that the system operates securely and reliably.

---

**Key System Contracts in zkSync**

Here are some, but not all, of the system contracts used in zkSync:

**1\. Bootloader**

**Role:**

* **Transaction Finalization:** The `Bootloader` contract is sort of super-admin. It is responsible for the final stages of transaction processing. It ensures that transactions are correctly processed and finalized, and that all necessary steps are completed.
    
* **Transaction Processing:** It handles the core logic needed to process transactions efficiently and securely.
    

---

**2\. ContractDeployer**

**Role:**

* **Contract Deployment:** The `ContractDeployer` contract manages the deployment of new contracts within the zkSync ecosystem. It is used to deploy both user contracts and other system contracts.
    
* **Deployment Management:** This contract ensures that new contracts are deployed correctly, incrementing the deployed nonce, and ensuring that the constructor in a single contract is never called twice.
    

---

**3\. Constants**

**Role:**

* **Define Protocol Constants:** The `Constants` contract contains a collection of constant variables, including addresses and other important values used throughout the protocol.
    
* **Ensure Consistency:** By centralizing these values, the `Constants` contract helps maintain consistency across the protocol and makes it easier to manage protocol-wide parameters.
    

---

**4\. NonceHolder**

**Role:**

* **Manage Nonces:** The `NonceHolder` contract is responsible for managing nonces, which are essential for ensuring that each transaction is unique. It tracks the latest nonce for each user and prevents replay attacks.
    
* **Prevent Duplicate Transactions:** By managing and updating nonces, this contract ensures that old or duplicate transactions cannot be processed.
    

---

**5\. DefaultAccount**

**Role:**

* **Default Account Management:** The `DefaultAccount` contract provides default functionality for account operations within zkSync. It is used to handle default account-related processes and interactions.
    
* **Account Operations:** This contract ensures that basic account operations are managed correctly and efficiently.
    

---

**6\. TransactionHelper**

**Role:**

* **Assist with Transaction Operations:** The `TransactionHelper` contract provides utility functions and helper methods for transaction-related operations. It aids in tasks such as transaction validation, fee calculations, and calculating the suggested signed hash of a transaction.
    
* **Utility Functions:** It simplifies and optimizes transaction operations by offering reusable functions and logic.
    

---

**7\. IAccount**

**Role:**

* **Account Interface:** The `IAccount` contract defines the interface for accounts within zkSync. It sets out the functions and methods that accounts must implement, ensuring consistency and compatibility across different account types.
    
* **Account Management:** This interface provides a standardized way for accounts to interact with the zkSync protocol, facilitating smooth operations and integrations.
    

---

In summary, system contracts in zkSync play a vital role in maintaining the protocol’s functionality and performance. Each contract serves a specific purpose, from managing nonces and deploying contracts to handling default account operations and providing utility functions. Understanding these contracts helps in appreciating how zkSync operates and maintains its high standards of efficiency, security, and reliability.

Next, we’ll explore where you can learn more about zkSync and account abstraction. Stay tuned!

### Where Can I Learn More?

While there are a few good platforms that you can learn Account Abstraction like [Alchemy](https://www.alchemy.com/overviews/what-is-account-abstraction) and their [YouTube](https://www.youtube.com/playlist?list=PLMj8NvODurfE9yPZ2beXSjuEgVtVcY1a6). I believe that the absolute best resource for learning not only account abstraction but web3 development and security is [**CyfrinUpdraft**](https://updraft.cyfrin.io/)**.** There, you will find up-to-date courses from beginner to Advanced. It's 100% free, no games no gimmicks. Check it out for yourself.