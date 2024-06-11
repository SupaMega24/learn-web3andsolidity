---
title: "Building Randomness with Chainlink VRF"
seoTitle: "Chainlink VRF: Creating True Randomness"
seoDescription: "Build decentralized apps with Chainlink VRF for secure, verifiable randomness in Solidity on Ethereum"
datePublished: Sun Jun 09 2024 13:16:59 GMT+0000 (Coordinated Universal Time)
cuid: clx7kjbaa000609l485sxcpla
slug: building-randomness-with-chainlink-vrf
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1717913588360/d3ba01bd-a323-4181-9d74-81e10c82d504.png
tags: learning, blockchain, solidity, smart-contracts

---

Imagine a lottery where the balls are tumbling in a glass sphere, watched by the world. Each number is a smart contract, each draw a transaction, and the entire network stands witness to the spectacle. This isn’t just a game of chance; it’s a demonstration of trust in technology, a showcase of fairness in play

The ***Random Fantasy Team Name Selector*** does not merely pick a name; it orchestrates a symphony of unpredictability, with each note struck by the hammer of cryptographic algorithms. It’s a modern-day oracle, delivering prophecies of randomness that are transparent, tamper-proof, and fair.

# **Overview**

In this series of posts, we will dive into creating a decentralized application using Solidity, the programming language for writing smart contracts on the Ethereum blockchain. Our project currently consists of two main contracts: `RandomTeamSelector` and `TeamNames`. Both of these contracts leverage [Chainlink's Verifiable Random Function (VRF)](https://chain.link/vrf) to ensure secure and verifiable randomness, essential for fair and unpredictable outcomes in our application.

The `RandomTeamSelector` contract is designed to randomly assign team names to participants using names commonly associate with mythical and fantasy creatures. Using Chainlink VRF, this contract can request random values that are used to select from a predefined list of team names. The `TeamNames` contract holds the list of possible team names and provides a function to retrieve a name based on an index.

Chainlink VRF is a reliable source of randomness for smart contracts. It provides cryptographic proof that the random values generated are tamper-proof and verifiably fair. By integrating Chainlink VRF into our Solidity contracts, we ensure that our random team selections are unbiased and transparent.

So, join us as we embark on this journey through the mechanics of the Random Fantasy Team Name Selector, exploring how it harnesses the power of Chainlink VRF to bring verifiable randomness to the blockchain. It’s a story of innovation, a dance of algorithms, and a testament to the ingenuity of decentralized solutions.

---

# The Forge of Creation: Setting the Stage for Smart Contract Development

Before we delve deeper into the intricacies of our Random Team Selector smart contract, let’s take a moment to acknowledge the anvil upon which it was forged. In the modern alchemy of smart contract development, the tools we choose are as crucial as the spells we cast. For this project, we’ve chosen a tool that’s as robust as it is refined: Foundry’s `forge`.

```shell
forge init
```

With a simple `forge init`, we breathed life into our project, creating a structured environment where our smart contract could take shape. Foundry’s suite of tools offers a streamlined workflow for smart contract development, testing, and deployment, ensuring that our code is not only functional but also battle-tested.

And when it came time to provide our contract with the power of randomness, we turned to the repositories of Chainlink contracts. With `forge install`, we summoned the Chainlink contracts into our project, each one a building block in the architecture of our application.

```shell
forge install smartcontractkit/chainlink --no-commit
```

This command is the digital equivalent of drawing water from the well of knowledge, bringing into our midst the Chainlink VRF contracts that would become the cornerstone of our Random Team Selector.

***NOTE: Don't forget your remappings!***

```toml
[solidity]
remappings = [
    "@chainlink/contracts/=lib/chainlink/contracts"
]
```

This update to your `foundry.toml` file sets the remappings for the Chainlink contracts within your Foundry project. It tells Foundry that whenever it encounters an import statement with `@chainlink/contracts/`, it should look in the `lib/chainlink/contracts` directory of your project. This is essential for ensuring that your Solidity files can correctly locate and import the Chainlink contract dependencies.

With this configuration in place, you’re ensuring that your development environment is aware of where to find the Chainlink contracts, allowing your smart contract to seamlessly integrate with Chainlink’s VRF functionality.

So, as we stand at the threshold of creation, let’s take a moment to appreciate the tools that make it all possible. Foundry’s `forge` is more than just a development environment; it’s a crucible where ideas are transformed into reality, where code becomes more than just instructions—it becomes a gateway to new worlds of possibility.

Now, with our stage set and our tools at the ready, let’s continue our journey into the heart of the Random Team Selector smart contract.

---

# The Alchemy of Imports: Weaving the Magic of Randomness

In the realm of Solidity, the `import` statement is akin to the summoning of allies, each bringing their unique powers to enhance our smart contract’s capabilities. In the case of our project, three such imports lay the foundation for its functionality:

```solidity
import {VRFConsumerBaseV2Plus} from "@chainlink/contracts/src/v0.8/vrf/dev/VRFConsumerBaseV2Plus.sol";
import {VRFV2PlusClient} from "@chainlink/contracts/src/v0.8/vrf/dev/libraries/VRFV2PlusClient.sol";
import {TeamNames} from "./TeamNames.sol";
```

Firstly, we invoke `VRFConsumerBaseV2Plus`, a contract from the hallowed libraries of Chainlink. This contract is the bedrock upon which we build our trust in randomness. It’s the guardian that interacts with the Chainlink VRF, ensuring that the randomness we receive is not just a roll of the dice but a cryptographically secure and verifiable act of chance.

Next, we call upon `VRFV2PlusClient`, a library that serves as our conduit to the Chainlink VRF. It’s the spellbook containing the incantations needed to request and receive verifiable random numbers. This library simplifies the interaction with Chainlink VRF, abstracting the complexity of blockchain oracles into a few lines of Solidity code.

Lastly, `TeamNames` emerges from our own domain, a contract that holds the essence of our application—the team names. It’s the treasure chest where the potential outcomes of our random selection are stored, waiting to be matched with the random numbers provided by the Chainlink oracle.

Together, these imports form a trio of trust, randomness, and data, as a powerful digital alliance. They are the first step in our contract’s journey, the initial incantation in the spell that will bring forth the Random Fantasy Team Name Selector into existence.

So, let us continue to weave this spell, line by line, until our smart contract stands complete, ready to bring the fair and exciting game of chance to all who dare to partake in its randomness.

---

# The Heart of the Contract: The Random Team Selector

In the symphony of Solidity, the `contract` declaration is the opening note, the defining statement that brings our smart contract to life. For the *Random Fantasy Team Name Selector*, this declaration is the beginning of its existence:

```solidity
contract RandomTeamSelector is VRFConsumerBaseV2Plus, TeamNames {
    // ...
}
```

Here, we declare that our `RandomTeamSelector` is not just any contract; it’s one that inherits from `VRFConsumerBaseV2Plus` and `TeamNames`. This inheritance is akin to a knight donning two powerful artifacts: one that grants the power of randomness and another that holds the wisdom of team names.

But every knight needs an origin, a beginning to their quest. This is where the `constructor` comes into play:

```solidity
constructor(uint256 subscriptionId) VRFConsumerBaseV2Plus(vrfCoordinator) {
    s_subscriptionId = subscriptionId;
}
```

The `constructor` is the sacred ritual that breathes life into our contract. It takes a `subscriptionId`—a talisman that connects us to the Chainlink VRF service—and binds it to our contract’s soul. This `subscriptionId` is the key to the oracle’s gate, allowing us to request randomness from the Chainlink network. You can get your own ID here:

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717919431451/966037be-ed6b-49d7-9518-f017f352ecd4.png align="center")](https://vrf.chain.link/)

By passing the `vrfCoordinator` to the `VRFConsumerBaseV2Plus` constructor, we establish a link to the Chainlink node that will serve as our intermediary to the oracle. It’s like setting the coordinates for a starship, ensuring that we can navigate the cosmos of randomness with precision.

With these lines of code, the *Random Fantasy Team Name* Selector is no longer just an idea; it becomes a living entity within the blockchain, ready to embark on its mission to bring verifiable randomness to the world.

In the coming sections, we’ll go over the building blocks that give power to our functions.

---

# Crafting the Core: Errors, State Variables, and Events

As we delve into the heart of the our smart contract, we encounter the elements that give it structure and purpose. Like the rules of a board game, these components define how the game is played, what moves are allowed, and what happens when things go awry.

### Custom Errors: The Guardians of Order

In the Solidity realm, errors are the sentinels that guard the gates of functions, ensuring that only those who meet the criteria may pass:

**Errors:**

```solidity
error RandomTeamSelector__AlreadySelected();
error RandomTeamSelector__NoSelectionOptionsAvailable();
error RandomTeamSelector__SelectionNotMade();
error RandomTeamSelector__InvalidTeamChoice();
```

* `RandomTeamSelector__AlreadySelected`: This error is a stern warning that a selection has already been made, barring any attempts to alter fate.
    
* `RandomTeamSelector__NoSelectionOptionsAvailable`: A reminder that one cannot choose from an empty list, this error appears when there are no options to select.
    
* `RandomTeamSelector__SelectionNotMade`: This error emerges when someone seeks a result before the die has been cast.
    
* `RandomTeamSelector__InvalidTeamChoice`: The final guardian, this error rejects any choice that strays from the path of available options.
    

### State Variables: The Pillars of Memory

State variables are the pillars upon which the contract’s memory is built, each holding a piece of information that defines the contract’s state:

**State Variables:**

***NOTE: Yes, I know they are hard coded. I will remedy this in part 3 :)***

```solidity
uint256 private constant SELECTION_ONGOING = 24;
uint256 public s_subscriptionId;
address public vrfCoordinator = 0x9DdfaCa8183c41ad55329BdeeD9F6A8d53168B1B;
bytes32 public s_keyHash = 0x787d74caea10b2b357790d5b5247c2f63d1d91572a9846f780606e4d953677ae;
uint32 public callbackGasLimit = 300000;
uint16 public requestConfirmations = 3;
uint32 public numWords = 3;
```

* `SELECTION_ONGOING`: An arbitrary constant that signifies the ongoing process of selection, like a flag raised high during a tournament.
    
* `s_subscriptionId`: The subscription ID for the Chainlink VRF service, akin to a membership card granting access to the oracle’s wisdom.
    
* `vrfCoordinator`: The address of the Chainlink VRF Coordinator, serving as the contract’s liaison to the oracle network.
    
* `s_keyHash`: A unique identifier for the gas lane, guiding the contract’s requests through the network’s thoroughfares.
    
* `callbackGasLimit`: The breath of the oracle, the amount of computational effort allocated to process the callback of the random number request.
    
* `requestConfirmations`: The number of confirmations the network must reach before the oracle considers the request fulfilled.
    
* `numWords`: The chorus of the contract, the number of random values requested from the oracle. Our contract calls for a trio, `3`, allowing the manager to choose from three fates.
    

***Curiosity Question: How do you know what state variables to use?***

Well, in this case I just looked at the documentation on Chainlink. However, we can dig a bit further. By analyzing the contract’s requirements in terms of data storage, access, cost, logic, and security, a developer can identify the appropriate state variables to use.

* 1. **Contract Purpose**: Understand the core objective of the contract. Is it for token management, decentralized finance (DeFi), gaming, or something else? The purpose dictates the data needed.
        
    2. **Data Requirements**: Identify what data is essential for the contract to operate. For example, a token contract needs variables for total supply, balances, allowances, etc.
        
    3. **Functionality**: Consider the functions the contract will perform. Each function may require specific data to execute its logic, which influences the state variables needed.
        
    4. **Interactions**: Think about how users and other contracts will interact with your contract. Variables might be needed to track ownership, permissions, or interaction history.
        
    5. **Security and Access Control**: Determine what access controls are necessary. State variables can help manage roles, permissions, and restrictions.
        
    6. **Upgradeability**: If the contract might need upgrades, consider state variables that facilitate this, such as addresses pointing to implementation contracts.
        
    7. **Efficiency and Gas Costs**: Be mindful of storage costs on blockchain platforms like Ethereum. Efficiently structured state variables can reduce gas fees.
        
    8. **Compliance and Regulations**: Depending on the jurisdiction and nature of the contract, certain compliance-related variables might be necessary.
        
    9. **Best Practices and Standards**: Follow established patterns and standards in the blockchain domain, such as ERC standards for tokens, which prescribe certain state variables.
        
    10. **Testing and Simulation**: Before finalizing, simulate various scenarios to ensure all necessary state variables are included and functioning as expected.
        

### Structs and Mappings: The Ledger of Choices

The `ManagerSelection` struct and associated mappings are the ledger where choices are recorded, a logbook that keeps track of each manager’s journey through the selection process:

**Struct:**

```solidity
struct ManagerSelection {
    uint256[] teamOptions;
    uint256 selectedTeam;
}
```

The struct serves as a custom data type to encapsulate the selection process for each manager. It has two properties:

* `teamOptions`: This is an array of `uint256` that stores the team IDs available for the manager to choose from. These IDs correspond to the random numbers generated by the Chainlink VRF and represent the different teams that the manager can select as their choice.
    
* `selectedTeam`: This is a `uint256` value that represents the manager’s final choice. Once the manager selects a team from the `teamOptions`, this property is updated to reflect the chosen team ID. Initially, it is set to `0` to indicate that no selection has been made. When the selection process is ongoing, it is set to the constant `SELECTION_ONGOING`, and upon completion, it holds the ID of the selected team.
    

**Mappings:**

```solidity
mapping(uint256 => address) private s_requestToManager;
mapping(address => ManagerSelection) private s_managerSelections;
```

In Solidity, mappings are a key-value data structure that allows you to associate unique keys with corresponding values. Think of them as a collection of pairs, where each key is linked to one value.

* `s_requestToManager`: A mapping that associates VRF request IDs with managers’ addresses, like a guest list at an exclusive event.
    
* `s_managerSelections`: A mapping that stores each manager’s selection details, chronicling their decisions for posterity.
    

***Curiosity Question: Could you explain the structure of mappings?***

The structure of a mapping is defined as follows:

```solidity
mapping(keyType => valueType) visibilityModifier variableName;
```

* **keyType**: This is the data type of the key. It can be any built-in type such as `uint`, `address`, or `bytes32`. Solidity requires keys to be of a type that is comparable, which means custom structs or arrays cannot be used as keys.
    
* **valueType**: This is the data type of the value that the key maps to. It can be any type, including another mapping or an array.
    
* **visibilityModifier**: This defines who can access the mapping. It can be `public`, `private`, or `internal`. If it’s `public`, Solidity automatically creates a getter function for it.
    
* **variableName**: This is the name you give to the mapping.
    

***Curiosity Question: How do you know when to use mappings?***

Mappings are typically used when you need to associate unique keys with specific values and require efficient retrieval and updating of these values. Mappings are ideal in scenarios where:

* You need to track ownership or balances, such as in a token contract.
    
* You want to store user data and retrieve it using identifiers like addresses or IDs.
    
* You’re managing permissions or roles in a contract, associating addresses with their respective permissions.
    
* You need a way to store and look up data without iterating over an entire collection, which can be gas-intensive.
    

### Events: The Herald’s Call

Events in Solidity are the herald’s call, announcing significant occurrences within the contract for all to hear:

**Events:**

```solidity
event SelectionMade(uint256 indexed requestId, address indexed manager);
event SelectionRevealed(uint256 indexed requestId, uint256[] teamValues);
event TeamChosen(address indexed manager, uint256 teamId);
```

* `SelectionMade`: Proclaimed when the selection process begins, like the starting bell of a race.
    
* `SelectionRevealed`: Announced when the random selection is unveiled, akin to the unveiling of a masterpiece.
    
* `TeamChosen`: Declared when a manager makes their choice, marking the moment of commitment.
    

***Curiosity Question: What is the*** `indexed`***keyword in the arguments?***

In Solidity, the `indexed` keyword in event arguments is used to enable these arguments to be searchable and filterable when looking through blockchain logs. When an argument is indexed, it creates a topic that logs can be indexed by, which allows for efficient querying. You can have up to three indexed arguments in an event.

For example, in the `SelectionMade` event:

```solidity
event SelectionMade(uint256 indexed requestId, address indexed manager);
```

* `requestId` is indexed so that you can filter events by specific request IDs.
    
* `manager` is indexed to allow filtering by the manager’s address.
    

This is particularly useful for front-end applications that need to display specific information to users, such as all events related to a particular manager or a specific request. By indexing these arguments, the application can quickly retrieve relevant events without having to process every single event log on the blockchain.

Collectively, the elements in this section form the backbone of the *Random Fantasy Team Name* Selector. They are the rules of engagement, the memory of the contract, and the voice that announces its actions. As we continue to explore the contract, we’ll see these elements in action, orchestrating the dance of randomness and choice.

---

# **Conclusion**

Phew! We've covered a lot so far on our journey. We looked at how the project is set up in Foundry using `forge init` and how chainlink contracts were installed using `forge install` (although their documentation has an alternative to this). We covered the imports and how the contract is set up with it's core elements such as state variables, mappings, and events. Their were also a few ***curious questions*** along the way for those of us, like me, who need a bit more understanding about how things work.

Thank you for reading! Here is what to expect with the rest of the series.

* Part 2: In-depth explanation of our functions
    
* Part 3: Proxy contract and makefile
    
* Part 4: Foundry unit tests
    
* Part 5: Fantasy Team NFTs
    
* Part 6: Deploy scripts
    
* Part 7: Front-end
    

[The code lives here, on Github.](https://github.com/SupaMega24/fantasy-team-vrf)

# **References**

Here are a list of references and materials I have used.

[Chainlink VRF Homepage](https://chain.link/vrf)

[Chainlinl VRF Supscription App](https://vrf.chain.link/)

[Chainlink Docs](https://docs.chain.link/vrf)

[Solidity Docs](https://docs.soliditylang.org/en/v0.8.26/)

[Foundry Docs](https://book.getfoundry.sh/)