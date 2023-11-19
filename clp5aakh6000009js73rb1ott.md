---
title: "Learning JavaScript #100Devs"
seoTitle: "Unlocking Web Magic: #100Devs Journey in JavaScript and DOM Mastery"
seoDescription: "Dive into the coding odyssey with #100Devs, mastering JavaScript's event-driven prowess and dynamic DOM manipulation. Experience interactive web development"
datePublished: Sun Nov 19 2023 09:37:04 GMT+0000 (Coordinated Universal Time)
cuid: clp5aakh6000009js73rb1ott
slug: learning-javascript-100devs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700386373008/aeefe4c1-3fe6-43e4-8413-f7feddcb6882.png
tags: javascript, event-listener, dom-manipulation, learn-coding

---

### **Embarking on the Coding Odyssey with #100Devs**

In the enthralling realm of coding adventures, I've recently set sail on a captivating journey with the #100Devs program alongside the exceptional guide, Leon Noel. His prowess in unraveling the intricacies of coding and providing hands-on opportunities for practice has made this odyssey truly remarkable.

Choosing to navigate the terrain of JavaScript within the #100Devs curriculum, my exploration has led me to the realm of event listeners and the dynamic landscape of the Document Object Model (DOM). With a foundation already laid by prior coding experiences, this chapter has been a fascinating leap into the heart of interactive web development.

This post aims to illuminate the milestones reached on this coding voyage, showcasing the insights gained in wielding event listeners to orchestrate responsive web experiences and delving deeper into the wonders of the DOM. As the journey unfolds, each line of code becomes a stepping stone, shaping a narrative of growth and mastery in the vast coding seas.

Join me as I unveil the discoveries made in the realm of event-driven programming and DOM manipulation. Let's navigate the currents of knowledge together, celebrating the synergy of learning and coding that #100Devs and Leon have graciously bestowed upon this coding odyssey.

%[https://youtu.be/_A20kVsaqIk?si=_1L_QXXgYhtq1ffI] 

### **Is it a Class Day, Boring Day, or The Weekend?**

Though not my inaugural encounter with such code, Leon's instructive approach has facilitated my most profound comprehension to date. In our recent exploration, we delved into a fragment of HTML code designed to receive user input—specifically, the day of the week. Leveraging the `alert()` function, the code originally relayed messages distinguishing whether it was a class day, a mundane one, or the weekend.

My task transformed into a captivating challenge: to transition these messages from simple pop-up alerts to seamlessly integrated displays on the webpage. This endeavor marked a pivotal leap in my understanding, turning what was once a conventional alert system into an engaging and user-friendly interface. Leon's teaching style not only unraveled the intricacies of the code but also transformed a routine task into an opportunity for creative application and enhanced user experience

Let's break down the provided JavaScript code step by step:

**Step 1: Event Listener Setup**

```javascript
document.querySelector('#check').addEventListener('click', check);
```

* **Explanation:**
    
    * The code selects an HTML element with the ID 'check' using `document.querySelector('#check')`.
        
    * It adds an event listener for the 'click' event using `addEventListener`.
        
    * When the element with ID 'check' is clicked, the function `check` will be invoked.
        

**Step 2:** `check` **Function Definition**

```javascript
function check() {
  // Function body
}
```

* **Explanation:**
    
    * The function `check` is defined to handle the logic that executes when the button is clicked.
        

**Step 3: Retrieve Input Value**

```javascript
const day = document.querySelector('#day').value.toLowerCase();
```

* **Explanation:**
    
    * Retrieves the value of the input element with the ID 'day' using `document.querySelector('#day')`.
        
    * Converts the retrieved value to lowercase using `toLowerCase()` to ensure case-insensitive comparisons.
        

**Step 4: Get Message Element**

```javascript
const messageElement = document.getElementById('message');
```

* **Explanation:**
    
    * Retrieves the HTML element with the ID 'message' using `document.getElementById('message')`.
        
    * This element will be used to display the result or message.
        

**Step 5: Check Day and Update Message**

```javascript
if (day === 'wednesday') {
  messageElement.textContent = 'What a boring day.';
} else if (day === 'saturday' || day === 'sunday') {
  messageElement.textContent = "Relax, it's the weekend.";
} else {
  messageElement.textContent = "It's a class day. Let's get it!";
}
```

* **Explanation:**
    
    * Checks the value of the variable `day` using conditional statements.
        
    * Updates the text content of the `messageElement` based on the entered day:
        
        * If the day is 'Wednesday', sets the message to 'What a boring day.'
            
        * If the day is 'Saturday' or 'Sunday', sets the message to "Relax, it's the weekend."
            
        * Otherwise, sets the message to "It's a class day. Let's get it!"
            

In summary, the code sets up an event listener for a button click. When the button is clicked, the `check` function is invoked. The function retrieves the input value, determines the day, and updates a message element based on the entered day. This creates an interactive feature where users receive different messages depending on the day they input.

%[https://codepen.io/Charles-Jones-the-encoder/full/GRzywbM] 

Let's break down some of the other exercises, along with their codepens.

### **Temperature Converter**

Here, my task was to write JavaScript code from a given HTML that would convert a user's input of Celsius to Fahrenheit.

#### **1\. Event Listener: A Gateway to Interaction**

```javascript
document.querySelector('#result').addEventListener('click', convert);
```

At the entrance of our journey stands an event listener, a vigilant guardian waiting for a click on the HTML element with the ID 'result'. This line establishes a connection between a button on our webpage and the JavaScript function `convert()`.

#### **2\. The Conversion Function: Unleashing JavaScript Magic**

```javascript
function convert() {
  let temp = parseFloat(document.querySelector('#celsius').value);
  temp = temp * 9/5 + 32;
  
  const messageElement = document.getElementById('result');
  messageElement.textContent = `Your converted Celsius temperature is ${temp} degrees Fahrenheit`;
}
```

Now, let's step into the heart of the operation: the `convert()` function. This function is triggered by the click event and is designed to convert temperatures from Celsius to Fahrenheit.

* **Extracting Input**: `let temp = parseFloat(document.querySelector('#celsius').value);`
    
* `parseFloat()` ensures that the data from the input is converted into a number
    
* **Temperature Conversion**: `temp = temp * 9/5 + 32;`
    
* **Updating the Result Display**: `const messageElement = document.getElementById('result'); messageElement.textContent = Your converted Celsius temperature is ${temp} degrees Fahrenheit;` The converted temperature is now elegantly displayed on the webpage. The `textContent` property of an HTML element with the ID 'result' is updated with a dynamically generated message.
    

Let's check it out! Enter your Celsius temp in the box and press convert.

%[https://codepen.io/Charles-Jones-the-encoder/pen/vYbpwgb] 

### **The Bachelor 1 - 3**

Each of these exercises challenged me to dig deep and learn how to make objects magically disappear, and then reappear on the screen. As a noob, this was absolutely amazing! Let's break them down one-by-one.

### **Unveiling the Drama: Breaking Down "The Final Rose" Code**

In the world of web development, sometimes the thrill of revealing the final rose can be as exhilarating as any reality show finale. In this breakdown, we dissect a snippet of JavaScript code that orchestrates a dramatic twist, hiding certain elements on a webpage with a click of "The Final Rose" button.

#### **1\. The Grand Entrance: Event Listener**

The show begins with the grand entrance of `document.querySelector('#finalRose').addEventListener('click', hide)`. Think of this line as the host announcing a pivotal moment—the click of the coveted "Final Rose" button triggers a function named `hide`. This event listener sets the stage for the unfolding drama.

#### **2\. Behind the Scenes: The** `hide` **Function**

Cue the suspenseful music as we delve into the backstage workings of the `hide` function:

```javascript
function hide() {
    document.querySelector('#claire').style.display = 'none';
    document.querySelector('#sharleen').style.display = 'none';
    
    const messageElement = document.getElementById('winner');
    messageElement.textContent = 'It was Nikki!';
}
```

**a. Disappearing Act: Hiding Elements**

Here, the script orchestrates a disappearing act worthy of any reality TV twist. `document.querySelector('#claire').style.display = 'none'` and `document.querySelector('#sharleen').style.display = 'none'` are like sending contestants off the stage—elements with IDs 'claire' and 'sharleen' gracefully exit with their `display` property set to 'none', making them invisible.

**b. And the Winner Is...: Updating Content Dynamically**

With a drumroll, the script dynamically updates the content of an element with the ID 'winner':

```javascript
messageElement = document.getElementById('winner');
messageElement.textContent = 'It was Nikki!';
```

This is the climactic reveal, displaying the message "It was Nikki!" on the webpage. The power of JavaScript shines here as it dynamically manipulates content in real-time.

***NOTE: The pics below and hereafter are NOT of the real contestants.***

%[https://codepen.io/Charles-Jones-the-encoder/pen/xxMporo] 

### **Breaking Down the Code: Exploring Dynamic Content Display**

#### **1\. Selecting Elements**

```javascript
const andi = document.querySelector('#andi')
const claire = document.querySelector('#claire')
const sharleen = document.querySelector('#sharleen')
```

* **Explanation:** In this section, three constants (`andi`, `claire`, and `sharleen`) are created, each representing an HTML element selected using `document.querySelector()`. These elements are identified by their respective IDs (`#andi`, `#claire`, and `#sharleen`).
    

#### **2\. Adding Event Listeners**

```javascript
document.querySelector('#andiNext').addEventListener('click', andiNext)
document.querySelector('#claireNext').addEventListener('click', claireNext)
document.querySelector('#sharleenNext').addEventListener('click', sharleenNext)
```

* **Explanation:** Event listeners are attached to three buttons (`#andiNext`, `#claireNext`, and `#sharleenNext`). When these buttons are clicked, the corresponding functions (`andiNext`, `claireNext`, and `sharleenNext`) will be executed.
    

#### **3\. Display Functions**

```javascript
function andiNext(){
    claire.classList.add('hidden')
    sharleen.classList.add('hidden')
    andi.classList.toggle('hidden')
}

function claireNext(){
    sharleen.classList.add('hidden')
    andi.classList.add('hidden')
    claire.classList.toggle('hidden')
}

function sharleenNext(){
    andi.classList.add('hidden')
    claire.classList.add('hidden')
    sharleen.classList.toggle('hidden')
}
```

* **Explanation:** Each of these functions (`andiNext`, `claireNext`, and `sharleenNext`) is responsible for dynamically updating the display of elements. They add the class `hidden` to two elements and toggle the `hidden` class on the third element, effectively hiding and revealing elements based on button clicks.
    

#### **4\. CSS Class: 'hidden'**

```javascript
.hidden {
    display: none;
}
```

* **Explanation:** The `hidden` class in the CSS file sets the `display` property to `none`, ensuring that elements with this class are not visible on the webpage.
    

%[https://codepen.io/Charles-Jones-the-encoder/pen/zYepgOY] 

### **Selecting Multiple Elements at Once**

#### **Part 1: Selecting Contestants**

```javascript
const contestants = document.querySelectorAll('.contestant')
```

Here, we initiate our journey by selecting all elements with the class 'contestant' using the `querySelectorAll` method. These contestants, like characters in a story, are the actors awaiting their cues.

#### **Part 2: Iterating Through Contestants**

```javascript
Array.from(contestants).forEach(element => element.addEventListener('click', checkForRose))
```

Just as a director guides actors on a stage, we iterate through our contestants, converting the NodeList into an array for flexibility. For each contestant, we attach an event listener for the 'click' event, calling the function `checkForRose`. This sets the stage for the next act.

#### **Part 3: Checking for the Rose**

```javascript
function checkForRose(click) {
    if (click.target.classList.contains('rose')) {
        document.querySelector('#nikki').classList.toggle('hidden')
    } else {
        alert("Wrong!");
    }
}
```

The heart of our drama unfolds here. When a contestant is clicked, `checkForRose` is summoned. This function examines whether the clicked contestant possesses the coveted 'rose' by checking its class. If true, it triggers a subtle reveal, toggling the visibility of the element with the id 'nikki'. If false, a dramatic alert declares, "Wrong!"—a moment of tension in our unfolding narrative.

Click on a name to find out the answer to the question below.

%[https://codepen.io/Charles-Jones-the-encoder/pen/GRzyVdB] 

### **In Summary ...**

From determining class days to converting temperatures and orchestrating captivating disappearances and reappearances, the exercises provided hands-on opportunities to apply newfound knowledge. The blog post breaks down each challenge, offering insights into the magic behind interactive web experiences.

The post also highlights the drama of "The Final Rose" and the dynamic content display exercises. It showcases the power of event listeners and the ability to manipulate the DOM, creating engaging and interactive web pages.

The coding odyssey with #100Devs is a celebration of the synergy between learning and coding, shaping a narrative of growth and mastery. As the coding journey unfolds, the post invites readers to join in the exploration, acknowledging the valuable lessons and creative applications bestowed by #100Devs and Leon. The interactive coding exercises, analogies, and real-world applications make this coding odyssey an exhilarating and enriching experience.