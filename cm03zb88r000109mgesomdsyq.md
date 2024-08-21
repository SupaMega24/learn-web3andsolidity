---
title: "Demystifying EIPs: The Blueprint for Ethereum's Evolution"
datePublished: Wed Aug 21 2024 14:58:39 GMT+0000 (Coordinated Universal Time)
cuid: cm03zb88r000109mgesomdsyq
slug: demystifying-eips-the-blueprint-for-ethereums-evolution
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/IlUq1ruyv0Q/upload/4a90d8cdd5237cd7be8ed741b487e9ff.jpeg
tags: ethereum, web3

---

---

### **Overview**

How does Ethereum keep continuously improving and evolving over time? It all starts with Ethereum Improvement Proposals (EIPs). In this post, we’ll break down the EIP process, exploring the different stages that every proposal goes through before becoming part of the Ethereum network. Whether you’re a budding smart contract developer or a curious security researcher, understanding EIPs is key to navigating and contributing to this innovative space. Plus, we’ve included interactive tools like flashcards and a quiz to help solidify your learning! Ready to dive in? Let’s get started.

---

## Let's Clear the Air First

**What exactly are EIPs?**

Think of **Ethereum Improvement Proposals (EIPs)** like blueprints for upgrading Ethereum. They're like a group project where someone says, "Hey, here's an idea to make things better!" That idea could be anything from a minor tweak to a massive overhaul. If you’ve ever worked on a team project where someone suggests a new approach to doing something—like switching to a shared online document instead of emailing everyone individually—that’s basically what an EIP is for the Ethereum network.

---

**Why should I care about EIPs?**

EIPs are the building blocks of Ethereum's evolution. Imagine you're playing your favorite video game, and every few months, there’s an update that adds new levels, fixes bugs, or gives your character new powers. That’s what EIPs do for Ethereum—they keep it fresh, secure, and better to use. Without EIPs, the network could get stuck with outdated systems and vulnerabilities, which is like still using dial-up internet in the age of fiber optics. Not fun, right?

---

**How will EIPs help me as a future smart contract developer or security researcher?**

If you're aiming to build smart contracts or break into Ethereum security research, understanding EIPs is like knowing the rulebook before you start playing the game. For developers, EIPs lay out the tools and standards you'll use to create smart contracts—it's like knowing what all the power-ups in a game do before you start playing. For security researchers, knowing EIPs helps you spot potential vulnerabilities and understand how changes to the network affect security. In a way, it’s like learning the blueprint of a building before you go in to make sure it’s structurally sound.

---

## EIP Status Terms: What They Are and Why They Matter

EIP Status Terms are like the different stages of development that an idea goes through before it becomes part of Ethereum. Each term represents a checkpoint in the journey of an EIP, from the moment someone suggests it to the point where it’s either fully adopted or shelved. Think of it like developing an app: there are stages like brainstorming, prototyping, beta testing, and release. Understanding these terms helps you keep track of where an EIP is in its lifecycle and how close it is to impacting the Ethereum network.

### 1\. **Idea**

**Meaning:** This is the very first stage, where someone has an idea but hasn’t formalized it into a proposal yet. It’s still in the brainstorming phase.  
**Example:** Imagine this like sketching out an idea for a new app on a napkin while hanging out with friends. The idea isn’t detailed yet, but the seed has been planted. For example, the concept behind EIP-721 (non-fungible tokens) started here before evolving into a concrete proposal.

### 2\. **Draft**

**Meaning:** After the idea is more thought-out, it’s written up as a draft. This stage is the rough outline of the proposal and is open to community feedback.  
**Example:** Think of it like when you take that napkin sketch and turn it into a more detailed project plan. You’re still open to changes and suggestions. EIP-1559, which changed how Ethereum's transaction fees work, started as a draft and underwent revisions based on community input.

### 3\. **Review**

**Meaning:** The EIP is now under active review by the community. At this point, people are diving deeper into the proposal, pointing out strengths, weaknesses, and areas for improvement.  
**Example:** Imagine this like putting your app prototype into beta testing, where users try it out and provide feedback. EIP-2981, which proposed a standard for royalties on NFTs, went through this review stage where the community provided critical insights and suggestions for improvement.

### 4\. **Last Call**

**Meaning:** The EIP has been reviewed, revised, and is now in its final stage before it becomes official. If necessary changes are required, it will revert the EIP to Review.  
**Example:** This is like the final round of beta testing before your app goes live—everything’s been tweaked, and you’re just making sure no last-minute issues pop up. EIP-20 (ERC-20 token standard) reached this point after extensive community discussion.

### 5\. **Final**

**Meaning:** The EIP has successfully passed all reviews, and the community accepts it as official. It’s now part of Ethereum.  
**Example:** This is the app release stage—it’s officially live for everyone to use. For instance, EIP-20 (ERC-20 token standard) became final and is now the foundation for many tokens on Ethereum.

### 6\. **Stagnant**

**Meaning:** The EIP has not seen any progress for six months or more. It’s on pause, though it could be picked up again later.  
**Example:** It’s like an app idea that you started working on but haven’t touched in months because other things took priority. EIP-2070, which proposed changes to Ethereum’s virtual machine, became stagnant when development stopped for an extended period.

### 7\. **Withdrawn**

**Meaning:** The author or the community has decided to pull the proposal. The idea didn’t work out or was no longer relevant.  
**Example:** This is like deciding to scrap your app project because it no longer solves the problem you intended, or a better solution exists. EIP-1234, which proposed delaying Ethereum’s “[difficulty bomb](https://www.investopedia.com/terms/d/difficulty-bomb.asp),” was withdrawn after other solutions were found.

### 8\. **Living**

**Meaning:** This is a special category of EIP that remains active and continuously evolves. It is a living document that can be updated over time.  
**Example:** Think of this as an app that continuously gets updates and new features. EIP-1, which defines the EIP process itself, is a living document that adapts as the process evolves.

---

### Common Questions About EIP Status Terms

1. **Do the stages in the EIP process always get followed consecutively?**  
    **A:** Not always. While the process typically follows a consecutive flow from Idea to Final, some EIPs may skip stages or revert to an earlier stage for revisions. For example, an EIP in "Review" might need to go back to "Draft" if significant changes are proposed.
    
2. **Can an EIP be moved back from "Final" to a previous stage?**  
    **A:** No, once an EIP is marked as "Final," it’s considered fully accepted and implemented. However, if issues arise, a new EIP would need to be proposed to modify or improve the existing implementation.
    
3. **What happens if an EIP in "Stagnant" status is picked up again?**  
    **A:** If work resumes on a "Stagnant" EIP, it can move back into "Draft" or "Review" status. The key is that it must see progress and updates to be reactivated.
    
4. **Can a withdrawn EIP be re-established and move forward again?**  
    **A:** Yes, a withdrawn EIP can be revisited. The author can resubmit the proposal, potentially with modifications based on previous feedback, and it can restart the EIP process. It is considered a new proposal and given a new EIP number.
    
5. **Can multiple EIPs be in the same status at the same time?**  
    **A:** Yes, multiple EIPs can be in the same stage concurrently. For example, many EIPs can be in "Draft" or "Review" at any given time, depending on how many proposals are active in the community.
    
6. **What differentiates a "Living" EIP from a "Final" one?**  
    **A:** A "Final" EIP is considered complete and does not change, while a "Living" EIP is continuously updated as the Ethereum network evolves. Living EIPs typically serve as ongoing standards or processes that need adjustments over time.
    
7. **Why might an EIP become stagnant, and what impact does that have on Ethereum's development?**  
    **A:** An EIP might become stagnant due to lack of interest, unresolved issues, or the emergence of better alternatives. Stagnant EIPs don’t impact Ethereum unless they are revived and move forward, so their effect on the network is neutral unless development resumes.
    
8. **How does the community decide to accept or reject an EIP during the "Review" and "Last Call" stages?**  
    **A:** The community reviews the proposal based on technical merit, security, potential impact on the network, and feedback from developers. Consensus is often achieved through discussion, and sometimes additional testing is required before a decision is made.
    

---

## Enhance Your Learning!

Learning about EIPs can be a lot to digest, so we've created some interactive tools to help you reinforce your understanding. Below, you’ll find two activities: **Flashcards** and a **Matching Quiz Game**. These will help you get more familiar with the EIP terms and their meanings in a fun and engaging way.

### Flashcards

Use the flashcards to quiz yourself on the definitions of EIP Status Terms. Here’s how it works:

* **Read the definition** on the front of the card.
    
* **Click the card** to flip it and reveal the term on the back.
    
* **Click the arrow** button at the bottom to move to the next flashcard.
    

This is a great way to test your memory and reinforce your learning at your own pace!

[You can get started here](https://quizlet.com/933290054/flashcards?funnelUUID=725ddf91-3730-4950-9825-a58cc50cfc6a)!

### Matching Quiz Game

Ready for a challenge? Test your knowledge with our matching quiz:

* **Click on a term** card to reveal it.
    
* **Click on the definition** card you think matches the term.
    
* If you’re correct, both cards will **disappear**. If not, try again until you get it right!
    

Keep going until all the cards are gone—this game will help you lock in those terms for good!

[Challenge yourself here!](https://quizlet.com/933290054/match?funnelUUID=f5ca5c2d-6f28-4cc7-a5bd-3116d716903a)

---

## Conclusion

In this post, we've explored the key stages of Ethereum Improvement Proposals (EIPs) and why they're essential to the evolution of the Ethereum network. From the initial spark of an idea to the final implementation, understanding these status terms is crucial for anyone looking to get involved in Ethereum development or security. Whether you're a smart contract developer or a security researcher, being familiar with the EIP process will help you navigate the ecosystem more effectively and keep up with its continuous evolution.

To deepen your understanding of Ethereum development and security, be sure to check out [**Cyfrin Updraft**](https://updraft.cyfrin.io/). It’s a fantastic resource where you can enhance your skills, learn best practices, and stay updated on the latest in blockchain technology. Keep building, keep learning, and take your expertise to the next level!

---

### **Free Resources**

[Cyfrin Updraft Courses](https://updraft.cyfrin.io/) - Learn for free at your own pace.

[Ethereum EIP GitHub Repo](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1.md) - Straight from the horse's mouth!

[PDF of this Post](https://acrobat.adobe.com/id/urn:aaid:sc:VA6C2:01fa9052-731a-4366-90a2-07b53df4d4e4) - Take it with you to read off-line.