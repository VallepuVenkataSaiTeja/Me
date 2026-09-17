# 1. JavaScript Fundamentals ⭐⭐⭐

JavaScript fundamentals are the foundation for everything you'll do later:

```text
JavaScript
   ↓
Functions
   ↓
Arrays / Objects
   ↓
DOM / Events
   ↓
Async JavaScript
   ↓
React
   ↓
Redux Toolkit
```

If the fundamentals are weak, React concepts like **props, state, hooks, callbacks, and Redux** become harder.

---

# 1. What is JavaScript?

**JavaScript is a programming language used to make web pages interactive and dynamic.**

HTML gives the webpage its **structure**.

CSS gives it **style**.

JavaScript gives it **behavior**.

For example, imagine a button:

```html
<button>Click Me</button>
```

HTML creates the button.

CSS could make it:

```text
Blue
Rounded
Large
```

JavaScript can make something happen when you click it:

```text
Click button
     ↓
JavaScript runs
     ↓
Display "Hello!"
```

For example:

```js
document.querySelector("button").addEventListener("click", function () {
    alert("Hello!");
});
```

So you can think of it as:

```text
HTML       → Structure
CSS        → Appearance
JavaScript → Behavior
```

---

# 2. Why do we need JavaScript?

Without JavaScript, most websites would be mostly static.

For example:

```text
Click Login
      ↓
Validate username/password
      ↓
Show error if incorrect
      ↓
Send data to server
      ↓
Show dashboard
```

JavaScript can handle the interaction between the user and the webpage.

### Common things JavaScript does

**1. Change webpage content**

```js
document.getElementById("message").textContent = "Hello";
```

**2. Handle user actions**

```text
Click
Submit
Type
Hover
Scroll
Key press
```

**3. Validate forms**

```text
Email is required
Password must contain 8 characters
```

**4. Communicate with APIs**

```text
React App
   ↓
JavaScript
   ↓
API
   ↓
Database
```

**5. Create interactive applications**

Examples:

* Shopping websites
* Banking applications
* Social media
* Dashboards
* Online learning platforms
* Chat applications

And with React, JavaScript is used to build large frontend applications.

---

# 3. Is JavaScript only for browsers?

No.

This is an important point.

JavaScript was originally designed primarily for browsers, but today it can run in many environments.

For example:

### Browser

```text
Chrome
Firefox
Safari
Edge
```

### Server

With **Node.js**, JavaScript can run on the server.

```text
Browser
   ↓
JavaScript

Server
   ↓
Node.js
   ↓
JavaScript
```

So JavaScript can be used for both frontend and backend development.

---

# 4. JavaScript vs HTML vs CSS

This is a very common beginner/interview question.

| Technology | Purpose          |
| ---------- | ---------------- |
| HTML       | Structure        |
| CSS        | Styling          |
| JavaScript | Behavior / Logic |

Example:

```html
<button id="btn">Click Me</button>
```

HTML creates the button.

```css
#btn {
    background: blue;
    color: white;
}
```

CSS styles the button.

```js
document.getElementById("btn").onclick = function () {
    alert("Button clicked!");
};
```

JavaScript adds behavior.

### Easy way to remember

```text
HTML       → What is on the page?
CSS        → How does it look?
JavaScript → What does it do?
```

---

# 5. How JavaScript runs

Suppose you have:

```js
console.log("Hello");
```

The browser has a **JavaScript engine** that reads and executes JavaScript.

Different browsers use different JavaScript engines.

For example:

```text
Chrome / Edge → V8
Firefox       → SpiderMonkey
Safari        → JavaScriptCore
```

You don't need to memorize all of these for beginner-level interviews, but knowing that browsers use a **JavaScript engine** is useful.

For example:

```text
Your JavaScript code
        ↓
JavaScript Engine
        ↓
Execution
        ↓
Result
```

---

# 6. Where can you write JavaScript?

There are three common ways to put JavaScript into an HTML page.

---

## A. Inline JavaScript

JavaScript is written directly inside an HTML element.

```html
<button onclick="alert('Hello')">
    Click Me
</button>
```

This works, but it is generally **not preferred** for larger applications.

Why?

Because HTML and JavaScript become mixed together.

---

# 7. Internal JavaScript

JavaScript can be written inside a `<script>` tag.

```html
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript</title>
</head>

<body>

    <button onclick="showMessage()">Click Me</button>

    <script>
        function showMessage() {
            alert("Hello JavaScript");
        }
    </script>

</body>
</html>
```

Here:

```html
<script>
```

tells the browser that JavaScript code is coming.

---

# 8. External JavaScript ⭐

This is the preferred approach for normal projects.

HTML:

```html
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript</title>
</head>

<body>

    <h1>Hello</h1>

    <script src="script.js"></script>

</body>
</html>
```

Then create:

```text
script.js
```

Inside:

```js
console.log("Hello JavaScript");
```

So:

```text
index.html
     ↓
script.js
```

The HTML loads the JavaScript file.

### Why external JavaScript is better?

Because it keeps:

```text
HTML → Structure
CSS  → Styling
JS   → Logic
```

separate.

This becomes especially important when working with larger applications.

---

# 9. `console.log()` ⭐⭐⭐

You will use this constantly while learning JavaScript.

```js
console.log("Hello World");
```

It prints information to the browser's developer console.

For example:

```js
let name = "Sai";

console.log(name);
```

Output:

```text
Sai
```

You can also print multiple values:

```js
let name = "Sai";
let age = 25;

console.log(name, age);
```

Output:

```text
Sai 25
```

---

# 10. How to open the console

In Chrome:

```text
Right click
     ↓
Inspect
     ↓
Console
```

You can then type:

```js
console.log("Hello");
```

and press Enter.

You'll see:

```text
Hello
```

This is one of the most important tools you'll use when learning JavaScript.

---

# 11. JavaScript Comments

Comments are text that JavaScript does not execute.

They are useful for explaining code.

### Single-line comment

```js
// This is a comment

console.log("Hello");
```

JavaScript ignores:

```js
// This is a comment
```

### Multi-line comment

```js
/*
    This is a
    multi-line comment
*/

console.log("Hello");
```

---

# 12. JavaScript Statements

A **statement** is an instruction given to JavaScript.

Example:

```js
let name = "Sai";
```

That's an instruction.

Another:

```js
console.log(name);
```

Another:

```js
let age = 25;
```

So:

```js
let name = "Sai";
let age = 25;
console.log(name);
```

contains multiple JavaScript statements.

---

# 13. Semicolon `;`

JavaScript statements can usually end with a semicolon.

```js
let name = "Sai";
let age = 25;

console.log(name);
```

JavaScript also allows:

```js
let name = "Sai"
let age = 25

console.log(name)
```

because JavaScript has something called **Automatic Semicolon Insertion (ASI)**.

For beginners, I recommend being consistent and using semicolons:

```js
let name = "Sai";
console.log(name);
```

You don't need to obsess over semicolons at this stage.

---

# 14. JavaScript is Case-Sensitive ⭐⭐⭐

This is important.

These are different:

```js
let name = "Sai";
let Name = "John";
```

JavaScript considers:

```text
name
```

and:

```text
Name
```

to be two different variables.

Similarly:

```js
console.log()
```

is correct.

But:

```js
Console.log()
```

is different and will cause an error because `Console` and `console` are different identifiers.

### Remember:

```text
name ≠ Name
age  ≠ Age
console ≠ Console
```

---

# 15. JavaScript Identifiers

An **identifier** is the name you give to something in JavaScript.

For example:

```js
let name = "Sai";
```

Here:

```text
name
```

is an identifier.

Other examples:

```js
let age = 25;
let studentName = "Sai";
let totalMarks = 500;
```

Identifiers can represent:

* Variables
* Functions
* Classes
* Objects, etc.

---

# 16. JavaScript Naming Rules

There are rules for variable names.

### Valid

```js
let name;
let age;
let studentName;
let _name;
let $price;
```

### Cannot start with a number

This is invalid:

```js
let 123name;
```

But this is valid:

```js
let name123;
```

### Spaces aren't allowed

Invalid:

```js
let student name;
```

Use:

```js
let studentName;
```

### Reserved words cannot normally be used

For example:

```js
let class;
```

is invalid because `class` is a JavaScript keyword.

---

# 17. Naming convention: camelCase ⭐⭐⭐

In JavaScript, you'll commonly see **camelCase**.

Example:

```js
let studentName;
let phoneNumber;
let emailAddress;
let totalMarks;
let passedOutYear;
```

Not:

```js
let student_name;
```

Although underscores are technically allowed, JavaScript projects commonly use camelCase.

---

# 18. JavaScript Keywords

JavaScript has reserved keywords that have special meanings.

Examples:

```js
let
const
var
if
else
for
while
function
return
class
new
this
try
catch
```

You can't normally use these as variable names.

For example:

```js
let let = 10;
```

❌ Invalid.

---

# 19. JavaScript is dynamically typed ⭐⭐⭐⭐

This is an important concept.

In JavaScript, you don't have to explicitly declare the data type of a variable.

For example:

```js
let value = 10;
```

JavaScript knows:

```text
value → Number
```

Then you can do:

```js
value = "Hello";
```

Now:

```text
value → String
```

The same variable can hold different types at different times.

Example:

```js
let value = 10;

console.log(value);

value = "Hello";

console.log(value);
```

Output:

```text
10
Hello
```

This is called **dynamic typing**.

We'll study data types properly in the next topic.

---

# 20. JavaScript is interpreted or compiled?

This question can be confusing.

You may hear:

> "JavaScript is an interpreted language."

That is an oversimplification.

Modern JavaScript engines use techniques such as:

* Parsing
* Compilation
* Just-in-time (JIT) compilation
* Optimization

For interview purposes, a safe understanding is:

> JavaScript is a high-level programming language whose execution is handled by a JavaScript engine, and modern engines use both interpretation and JIT compilation techniques.

You don't need to go deeply into the engine internals yet.

---

# 21. JavaScript is single-threaded ⭐⭐⭐⭐

This is an important concept that will become very important when we study **asynchronous JavaScript and the event loop**.

JavaScript's main execution model uses a single call stack, meaning it executes one piece of JavaScript code at a time on that stack.

For example:

```js
console.log("A");
console.log("B");
console.log("C");
```

Output:

```text
A
B
C
```

It doesn't execute:

```text
A and B and C
```

simultaneously on the same JavaScript call stack.

Later we'll learn how JavaScript handles things like:

```js
setTimeout()
fetch()
Promises
```

without simply freezing the whole application.

That's where the **event loop** comes in.

---

# 22. JavaScript is object-based

JavaScript works heavily with objects.

For example:

```js
const student = {
    name: "Sai",
    age: 25,
    course: "React"
};
```

You can access:

```js
student.name;
```

which gives:

```text
Sai
```

Objects become extremely important when you learn:

* Props
* State
* APIs
* JSON
* Redux
* React applications

---

# 23. JavaScript can manipulate the DOM

The **DOM (Document Object Model)** represents an HTML document as objects that JavaScript can interact with.

Suppose HTML is:

```html
<h1 id="title">Hello</h1>
```

JavaScript can find it:

```js
const heading = document.getElementById("title");
```

Then change it:

```js
heading.textContent = "Hello Sai";
```

The webpage changes from:

```text
Hello
```

to:

```text
Hello Sai
```

We'll study DOM separately because it's an important topic.

---

# 24. JavaScript can respond to events

An **event** is something that happens in the webpage.

Examples:

```text
Click
Submit
Input
Mouse movement
Keyboard press
Page load
```

Example:

```html
<button id="btn">Click Me</button>
```

JavaScript:

```js
const button = document.getElementById("btn");

button.addEventListener("click", function () {
    console.log("Button clicked");
});
```

When the user clicks:

```text
Click button
     ↓
Event occurs
     ↓
JavaScript function executes
     ↓
"Button clicked"
```

This concept is extremely important for React.

---

# 25. A small complete JavaScript example

Let's combine the fundamentals.

### HTML

```html
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript Fundamentals</title>
</head>

<body>

    <h1 id="title">Welcome</h1>

    <button id="btn">Click Me</button>

    <script src="script.js"></script>

</body>
</html>
```

### JavaScript

```js
const button = document.getElementById("btn");

button.addEventListener("click", function () {
    console.log("Button clicked");

    document.getElementById("title").textContent = "Hello JavaScript";
});
```

### What happens?

Initially:

```text
Welcome

[ Click Me ]
```

You click the button.

JavaScript:

```text
Find button
    ↓
Listen for click
    ↓
User clicks
    ↓
Function runs
    ↓
Print message
    ↓
Change heading
```

The webpage becomes:

```text
Hello JavaScript

[ Click Me ]
```

This tiny example already combines:

* JavaScript
* DOM
* Variables
* Functions
* Events
* `console.log()`

---

# 26. Important interview questions from Fundamentals

You should be able to answer these in your own words.

### Q1. What is JavaScript?

**Answer:**

> JavaScript is a high-level programming language primarily used to add logic and interactivity to web applications. It can run in browsers and also outside browsers using environments such as Node.js.

---

### Q2. What is the difference between HTML, CSS and JavaScript?

```text
HTML       → Structure
CSS        → Styling
JavaScript → Behavior and logic
```

---

### Q3. Is JavaScript case-sensitive?

Yes.

```js
let name = "Sai";
let Name = "John";
```

These are different identifiers.

---

### Q4. Where can JavaScript run?

Common environments include:

```text
Web browsers
Node.js
Other JavaScript runtimes
```

---

### Q5. What is `console.log()`?

It is a commonly used JavaScript function for displaying values/messages in the developer console, mainly for debugging and inspecting program behavior.

---

### Q6. What is a JavaScript engine?

A JavaScript engine is software that parses and executes JavaScript code.

Examples include:

```text
V8
SpiderMonkey
JavaScriptCore
```

---

### Q7. Is JavaScript dynamically typed?

Yes.

The type associated with a value can change during execution, and variables don't require an explicit type declaration.

```js
let value = 10;

value = "Hello";
```

---

### Q8. Is JavaScript single-threaded?

The main JavaScript execution model uses a single call stack. Asynchronous behavior is handled through the host environment and mechanisms such as the event loop.

We'll study this in detail later.

---

# 27. What you should remember from this topic

Don't try to memorize everything.

Make sure you understand these:

```text
                 JavaScript Fundamentals
                         │
        ┌────────────────┼────────────────┐
        ↓                ↓                ↓
     Purpose          Execution        Syntax
        │                │                │
   Web behavior      JS Engine       Statements
   Interactivity     Browser         Comments
   Logic             Node.js         Case-sensitive
                                      Naming
                         │
                         ↓
                    Core concepts
                         │
          ┌──────────────┼──────────────┐
          ↓              ↓              ↓
       Dynamic        Single main      Objects
        typing         call stack
```

And remember this development progression:

```text
HTML
 ↓
CSS
 ↓
JavaScript
 ↓
DOM + Events
 ↓
Modern JavaScript
 ↓
Async JavaScript
 ↓
React
 ↓
Redux Toolkit
```

## ⭐ Next topic: 2. Variables & Data Types

This is where we'll go much deeper into:

```text
var
let
const

String
Number
Boolean
Undefined
Null
BigInt
Symbol
Object
Array

typeof
Primitive vs Non-primitive
Mutable vs Immutable
```

Especially **`var` vs `let` vs `const`**, because that is one of the most frequently asked JavaScript interview questions.
