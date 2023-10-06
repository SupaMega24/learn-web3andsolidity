---
title: "Learning JavaScript"
seoDescription: "Dive into JavaScript learning! Explore Rock-Paper-Scissors code, uncovering variables, logic, UI dynamics. Unravel web programming secrets."
datePublished: Fri Oct 06 2023 12:15:47 GMT+0000 (Coordinated Universal Time)
cuid: clnekl6s3000e09l7efid38ih
slug: learning-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696593128613/0a5045ed-1076-49f6-8646-6fb80142f652.png
tags: css, javascript, learning, html5

---

Hello fellow enthusiasts of the digital realm! Today, I'm thrilled to share my exciting adventure delving into the world of JavaScript and game development. Recently, I embarked on a project to create a simple yet engaging Rock-Paper-Scissors game. Although it is currently just a simple 'click to play' game, I'm proud of my effort as I continue to learn and progress. Let me walk you through the code and the key lessons I learned along the way.

[You can play it here!](https://supamega24.github.io/rock-paper-scissors/)

### **The JavaSctipt Code**

Here is a quick look at the JavaScript code I created for the 'rock, paper, scissors game. Although I was able to quickly type the variables and functions that I needed, I did run into some problems with the correct order and whether or not some of my variables should be local or global scope. After a bit of fidgeting and a Dave Chappelle comedy break, I was finally able to piece it together.

NOTE: The accompanying HTML and CSS aren't included in this post.

```javascript
let playerScore = 0;
let computerScore = 0;
let gamesPlayed = 0;

function computerChoice() {
    const choices = ['rock', 'paper', 'scissors'];
    const randomIndex = Math.floor(Math.random() * 3);
    return choices[randomIndex];
}

function playerChoice(choice) {
    const computer = computerChoice();
    if (choice === computer) {
        alert("It's a tie!".toUpperCase());
    } else if ((choice === 'rock' && computer === 'scissors') ||
               (choice === 'paper' && computer === 'rock') ||
               (choice === 'scissors' && computer === 'paper')) {
        playerScore++;
        updateScores();
        alert(`You win! ${choice} beats ${computer}`.toUpperCase());
    } else {
        computerScore++;
        updateScores();
        alert(`Computer wins! ${computer} beats ${choice}`.toUpperCase());
    }
    gamesPlayed++;

    if (gamesPlayed === 5) {
        if (playerScore > computerScore) {
            alert("Player is the champion!".toUpperCase());
        } else if (playerScore < computerScore) {
            alert("Computer is the champion!".toUpperCase());
        } else {
            alert("It's a draw!".toUpperCase());
        }
        
        playerScore = 0;
        computerScore = 0;
        gamesPlayed = 0;
    }
    updateScores();
}

function updateScores() {
    document.getElementById("playerScore").textContent = playerScore;
    document.getElementById("computerScore").textContent = computerScore;
}
```

### **Code Breakdown**

**Setting the Stage: Variables and Initialization:** Firstly, I established the game's foundation with three critical variables: `playerScore`, `computerScore`, and `gamesPlayed`. These variables became the backbone of the game, tracking player and computer scores while also keeping count of the games played.

**Decoding the Computer's Choice:** One of the pivotal aspects was simulating the computer's choice. I designed the `computerChoice()` function, utilizing an array of choices—'rock', 'paper', and 'scissors'. Through JavaScript's random number generation (`Math.random()`) and floor operation (`Math.floor()`), the computer's selection was randomized, simulating human unpredictability.

**Engaging Player Interaction:** The heart of the game resides in the `playerChoice(choice)` function. This function processes the player's input and compares it to the computer's choice, employing conditional statements to determine the winner. Here, I used conditional logic: if the player and computer choices matched, it was a tie; otherwise, I meticulously evaluated winning scenarios and applied the appropriate if/else statement.

**A Simple User Interface:** Integrating JavaScript with HTML, I dynamically updated the user interface. The `updateScores()` function plays a pivotal role, ensuring seamless display of player and computer scores after each round. This interaction between backend logic and frontend representation was a valuable lesson in bridging the gap between code and user experience.

**Champion Declaration and Loop Logic:** Implementing an end-game check, I used a loop to limit the game to five rounds. Once this threshold is reached, the code evaluates the scores and declars a champion. The use of loops and conditionals was key here, showcasing the power of controlled repetition and decision-making in game development.

**Unveiling the Game Flow:**

1. **Initialization:** The game initializes with scores and a games played counter set to zero at the start.
    
2. **Player's Move:** Upon the player's choice, the computer makes its selection randomly.
    
3. **Outcome Evaluation:** Conditional statements compare choices, determining the round's outcome.
    
4. **Score Update:** Scores are updated dynamically on the user interface after each round.
    
5. **Champion Declaration:** After five rounds, the code analyzes scores, identifying the champion and announcing the result.
    

### **Coding Epiphany and Moving Forward**

Through this project, I unearthed the beauty of conditional logic, the thrill of randomization, and the magic of dynamic user interfaces. This venture was more than a coding exercise; it was a comprehensive exploration of fundamental programming concepts and their practical application in game development.

As I journey forward, I'm excited to leverage these newfound skills in more complex projects, further unraveling the mysteries of JavaScript and game design. Stay tuned for more coding adventures; the world of possibilities in the digital realm awaits! Happy coding, fellow developers! 🚀