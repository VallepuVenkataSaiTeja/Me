## 🚀 JavaScript — Interview-Ready Roadmap

### 1. JavaScript Fundamentals ⭐⭐⭐

Start here and make these very strong.

* What is JavaScript?
* Why JavaScript?
* JavaScript vs HTML vs CSS
* How JavaScript runs in the browser
* Adding JS to HTML

  * Inline
  * Internal
  * External
* `console.log()`
* Comments
* Statements
* Case sensitivity

### 2. Variables & Data Types ⭐⭐⭐

* `var`
* `let`
* `const`
* Variable naming rules
* Primitive data types

  * String
  * Number
  * Boolean
  * Undefined
  * Null
  * BigInt
  * Symbol
* Non-primitive

  * Object
  * Array
* `typeof`
* Dynamic typing
* Mutable vs immutable

**Interview questions:**

* `var` vs `let` vs `const`
* `null` vs `undefined`
* Primitive vs reference types

---

### 3. Operators ⭐⭐⭐

* Arithmetic
* Assignment
* Comparison
* Logical
* Increment/decrement
* Ternary operator
* Nullish coalescing `??`
* Optional chaining `?.`
* Spread `...`
* Rest `...`

Especially understand:

```js
== 
===
!=
!==
```

and:

```js
&&
||
!
```

---

### 4. Type Conversion & Coercion ⭐⭐⭐

Very important for interviews.

* String conversion
* Number conversion
* Boolean conversion
* Implicit conversion
* Explicit conversion
* Truthy and falsy values
* `==` vs `===`

Example:

```js
console.log("5" + 2); // "52"
console.log("5" - 2); // 3
```

You should understand **why** this happens.

---

### 5. Conditional Statements ⭐⭐⭐

* `if`
* `else`
* `else if`
* Nested conditions
* `switch`
* Ternary operator

Example:

```js
if (age >= 18) {
    console.log("Adult");
} else {
    console.log("Minor");
}
```

---

### 6. Loops ⭐⭐⭐

* `for`
* `while`
* `do...while`
* Nested loops
* `break`
* `continue`

Then learn:

```js
for...of
for...in
```

Important distinction:

```js
for...of
```

→ values

```js
for...in
```

→ keys/properties

---

# 7. Functions ⭐⭐⭐⭐⭐

This is **extremely important for React**.

Learn:

* Function declaration
* Function expression
* Arrow functions
* Parameters
* Arguments
* Return
* Default parameters
* Rest parameters
* Callback functions
* Higher-order functions
* Anonymous functions
* Immediately Invoked Function Expression (IIFE)

Example:

```js
function add(a, b) {
    return a + b;
}
```

Arrow:

```js
const add = (a, b) => {
    return a + b;
};
```

Short form:

```js
const add = (a, b) => a + b;
```

---

# 8. Scope ⭐⭐⭐⭐⭐

Very important interview topic.

Understand:

* Global scope
* Function scope
* Block scope
* Lexical scope
* Scope chain

Example:

```js
let name = "Sai";

function test() {
    let age = 25;

    console.log(name);
    console.log(age);
}
```

You should understand **why `name` is accessible inside the function**.

---

# 9. Hoisting ⭐⭐⭐⭐⭐

Learn hoisting for:

* `var`
* `let`
* `const`
* Functions

Understand:

```js
console.log(a);

var a = 10;
```

versus:

```js
console.log(a);

let a = 10;
```

Also learn the:

**Temporal Dead Zone (TDZ)**

---

# 10. Strings ⭐⭐⭐

Learn:

* String creation
* String indexing
* `length`
* `toUpperCase()`
* `toLowerCase()`
* `trim()`
* `includes()`
* `startsWith()`
* `endsWith()`
* `slice()`
* `substring()`
* `replace()`
* `replaceAll()`
* `split()`
* Template literals

Example:

```js
const name = "Sai";

console.log(`Hello ${name}`);
```

---

# 11. Arrays ⭐⭐⭐⭐⭐

This is **extremely important for React**.

Learn:

* Creating arrays
* Indexing
* Adding/removing elements
* `push()`
* `pop()`
* `shift()`
* `unshift()`
* `slice()`
* `splice()`
* `concat()`

Then master:

### Array methods

```js
forEach()
map()
filter()
reduce()
find()
findIndex()
some()
every()
includes()
sort()
reverse()
```

Especially:

```js
map()
filter()
reduce()
find()
forEach()
```

You will use these constantly in React.

Example:

```js
const numbers = [1, 2, 3, 4];

const result = numbers.map(num => num * 2);

console.log(result);
```

---

# 12. Objects ⭐⭐⭐⭐⭐

Very important for JavaScript and React.

Learn:

* Creating objects
* Properties
* Methods
* Accessing properties
* Dot notation
* Bracket notation
* Adding properties
* Updating properties
* Deleting properties
* Nested objects
* Object destructuring

Example:

```js
const student = {
    name: "Sai",
    age: 25,
    course: "React"
};
```

Access:

```js
student.name
```

or:

```js
student["name"]
```

---

# 13. Destructuring ⭐⭐⭐⭐⭐

Very important in modern JavaScript and React.

### Array destructuring

```js
const numbers = [10, 20];

const [a, b] = numbers;
```

### Object destructuring

```js
const student = {
    name: "Sai",
    age: 25
};

const { name, age } = student;
```

You'll see this **everywhere in React**.

---

# 14. Spread & Rest Operators ⭐⭐⭐⭐⭐

Understand:

```js
...
```

But know that it has different uses.

### Spread

```js
const a = [1, 2];
const b = [...a, 3, 4];
```

Objects:

```js
const user = {
    name: "Sai"
};

const newUser = {
    ...user,
    age: 25
};
```

### Rest

```js
function add(...numbers) {
    console.log(numbers);
}
```

---

# 15. DOM ⭐⭐⭐⭐

Since JavaScript works with webpages, learn the DOM.

Understand:

* What is DOM?
* `document`
* `getElementById()`
* `querySelector()`
* `querySelectorAll()`
* Changing text
* Changing HTML
* Changing styles
* Creating elements
* Removing elements
* Adding classes
* Attributes

Example:

```js
const heading = document.querySelector("h1");

heading.textContent = "Hello JavaScript";
```

You don't need to become a DOM expert because React handles much of this for you.

---

# 16. Events ⭐⭐⭐⭐⭐

Very important for React.

Learn:

* Click
* Input
* Change
* Submit
* Mouse events
* Keyboard events
* Event object
* Event bubbling
* Event capturing
* `preventDefault()`
* `stopPropagation()`

Example:

```js
button.addEventListener("click", function () {
    console.log("Clicked");
});
```

---

# 17. Callbacks ⭐⭐⭐⭐⭐

Understand:

**A function passed to another function.**

Example:

```js
function greet(name, callback) {
    callback(name);
}

greet("Sai", function(name) {
    console.log("Hello " + name);
});
```

This leads directly into:

* Higher-order functions
* Array methods
* Asynchronous JavaScript

---

# 18. Higher-Order Functions ⭐⭐⭐⭐

A function that:

* accepts another function
* returns another function
* or both

Example:

```js
function calculate(a, b, operation) {
    return operation(a, b);
}

calculate(10, 5, (a, b) => a + b);
```

Very useful for understanding React patterns.

---

# 19. `this` Keyword ⭐⭐⭐⭐⭐

Important interview topic.

Understand `this` in:

* Global context
* Object methods
* Regular functions
* Arrow functions
* Constructor functions
* Event handlers

Especially:

### Regular function

```js
function test() {
    console.log(this);
}
```

### Arrow function

```js
const test = () => {
    console.log(this);
};
```

Understand **why they behave differently**.

---

# 20. Closures ⭐⭐⭐⭐⭐

One of the most important JavaScript interview topics.

Example:

```js
function outer() {
    let count = 0;

    return function inner() {
        count++;
        console.log(count);
    };
}

const counter = outer();

counter();
counter();
```

You need to understand **how `inner()` remembers `count` even after `outer()` has finished executing.**

---

# 21. Execution Context & Call Stack ⭐⭐⭐⭐⭐

Understand conceptually:

* Global execution context
* Function execution context
* Call stack
* Execution phases
* Memory creation
* Execution phase

Example:

```js
function one() {
    two();
}

function two() {
    console.log("Hello");
}

one();
```

Understand how the call stack works.

---

# 22. Asynchronous JavaScript ⭐⭐⭐⭐⭐

**Extremely important for React.**

Learn:

* Synchronous vs asynchronous
* Blocking vs non-blocking
* `setTimeout()`
* `setInterval()`
* Callbacks
* Callback hell
* Promises
* Promise states
* `.then()`
* `.catch()`
* `.finally()`
* `async`
* `await`
* `try...catch`

Example:

```js
async function getData() {
    try {
        const response = await fetch(url);
        const data = await response.json();

        console.log(data);
    } catch (error) {
        console.log(error);
    }
}
```

---

# 23. Promises ⭐⭐⭐⭐⭐

Master:

```js
Pending
Fulfilled
Rejected
```

And:

```js
.then()
.catch()
.finally()
```

Also learn:

```js
Promise.all()
Promise.allSettled()
Promise.race()
Promise.any()
```

---

# 24. Event Loop ⭐⭐⭐⭐⭐

Very common interview topic.

Understand:

```text
Call Stack
     ↓
Web APIs
     ↓
Callback Queue
     ↓
Microtask Queue
     ↓
Event Loop
```

Especially understand why:

```js
console.log("A");

setTimeout(() => {
    console.log("B");
}, 0);

console.log("C");
```

outputs:

```text
A
C
B
```

---

# 25. Fetch API & APIs ⭐⭐⭐⭐⭐

Very important for React development.

Learn:

* What is an API?
* HTTP basics
* GET
* POST
* PUT
* PATCH
* DELETE
* `fetch()`
* JSON
* Request
* Response
* Headers
* Status codes
* Error handling

Example:

```js
const response = await fetch("https://example.com/users");

const data = await response.json();

console.log(data);
```

---

# 26. Error Handling ⭐⭐⭐

Learn:

```js
try
catch
finally
throw
```

Example:

```js
try {
    // code
} catch (error) {
    console.log(error);
}
```

---

# 27. Modules ⭐⭐⭐⭐⭐

Very important for React.

Learn:

### Export

```js
export default App;
```

and:

```js
export { add, subtract };
```

### Import

```js
import App from "./App";
```

and:

```js
import { add } from "./math";
```

Understand:

* Default export
* Named export
* Import/export
* Module scope

---

# 28. Local Storage & Session Storage ⭐⭐⭐

Useful for frontend applications.

```js
localStorage.setItem("name", "Sai");
```

```js
localStorage.getItem("name");
```

```js
localStorage.removeItem("name");
```

Also:

```js
sessionStorage
```

Understand JSON:

```js
JSON.stringify()
JSON.parse()
```

---

# 29. ES6+ Modern JavaScript ⭐⭐⭐⭐⭐

You should be comfortable with modern JS syntax.

Important features:

* `let`
* `const`
* Arrow functions
* Template literals
* Destructuring
* Spread
* Rest
* Default parameters
* Modules
* Classes
* Promises
* `async/await`
* Optional chaining
* Nullish coalescing
* `for...of`
* `Map`
* `Set`

---

# 30. Map, Set & Other Data Structures ⭐⭐⭐

Learn:

### Map

```js
const map = new Map();
```

### Set

```js
const set = new Set();
```

Understand when to use them instead of objects/arrays.

---

# 31. Object & Array Advanced Methods ⭐⭐⭐⭐

Know:

```js
Object.keys()
Object.values()
Object.entries()
Object.assign()
```

and:

```js
Array.from()
Array.isArray()
```

Also understand shallow copying.

---

# 32. Shallow Copy vs Deep Copy ⭐⭐⭐⭐⭐

Very important when working with React state.

Understand:

```js
const newUser = { ...user };
```

versus nested objects.

Also learn:

```js
structuredClone()
```

and why simply using spread doesn't deeply copy nested objects.

---

# 33. Immutability ⭐⭐⭐⭐⭐

**Very important for React.**

Understand why we avoid directly modifying existing state/data.

Bad:

```js
user.name = "John";
```

Better:

```js
const newUser = {
    ...user,
    name: "John"
};
```

This concept becomes extremely important when you learn React state and Redux Toolkit.

---

# 34. Prototypes & Prototype Chain ⭐⭐⭐⭐

For interviews, understand:

* Prototype
* `__proto__`
* `prototype`
* Prototype chain
* Inheritance
* `Object.create()`

You don't need to spend as much time here as on arrays, functions, promises, or closures.

---

# 35. Classes & OOP ⭐⭐⭐

Learn:

* Class
* Constructor
* Methods
* `extends`
* `super`
* Inheritance
* Encapsulation
* Static methods

Example:

```js
class Student {
    constructor(name) {
        this.name = name;
    }

    greet() {
        console.log(`Hello ${this.name}`);
    }
}
```

Know this for interviews, but **don't prioritize it over functional JavaScript** for React.

---

# 36. JavaScript Interview Concepts ⭐⭐⭐⭐⭐

After completing the above, specifically practice:

* `var` vs `let` vs `const`
* `==` vs `===`
* `null` vs `undefined`
* Primitive vs reference
* Mutable vs immutable
* Shallow vs deep copy
* Scope
* Scope chain
* Hoisting
* TDZ
* Closures
* `this`
* Arrow vs regular functions
* Callback
* Higher-order function
* Promise
* Async/await
* Event loop
* Call stack
* Microtask vs macrotask
* Event bubbling
* Event delegation
* Debouncing
* Throttling
* Prototype
* Currying
* Memoization

---

# ⭐ What YOU should prioritize for React

You don't need to give every topic equal importance.

### 🔴 Must master

```text
Variables
Data Types
Operators
Conditions
Loops
Functions
Scope
Hoisting
Arrays
Objects
Destructuring
Spread / Rest
Array Methods
Callbacks
Higher-Order Functions
Closures
this
Promises
async/await
Fetch/API
Event Loop
Modules
Immutability
Shallow vs Deep Copy
```

### 🟡 Should know

```text
DOM
Events
Error Handling
Local Storage
Map / Set
Classes
Prototypes
Debouncing
Throttling
```

### 🟢 Learn later

```text
Currying
Memoization
Generators
Iterators
Symbols
WeakMap
WeakSet
Proxy
Advanced metaprogramming
```

You **don't need to master the green topics before starting React**.

---

# 🧭 Recommended learning order for you

Since you've already been studying CSS and React fundamentals, I would do JavaScript in this exact sequence:

```text
1. JavaScript Fundamentals
        ↓
2. Variables & Data Types
        ↓
3. Operators
        ↓
4. Type Conversion
        ↓
5. Conditions
        ↓
6. Loops
        ↓
7. Functions
        ↓
8. Scope
        ↓
9. Hoisting
        ↓
10. Strings
        ↓
11. Arrays
        ↓
12. Objects
        ↓
13. Destructuring
        ↓
14. Spread & Rest
        ↓
15. Callbacks
        ↓
16. Higher-Order Functions
        ↓
17. DOM
        ↓
18. Events
        ↓
19. this
        ↓
20. Closures
        ↓
21. Execution Context & Call Stack
        ↓
22. Async JavaScript
        ↓
23. Promises
        ↓
24. async/await
        ↓
25. Event Loop
        ↓
26. Fetch & APIs
        ↓
27. Error Handling
        ↓
28. Modules
        ↓
29. Local Storage
        ↓
30. Map & Set
        ↓
31. Immutability
        ↓
32. Shallow vs Deep Copy
        ↓
33. Prototypes
        ↓
34. Classes / OOP
        ↓
35. Interview Questions
        ↓
36. JavaScript Coding Problems
```

### 🎯 Most important connection to React

When you start React seriously, these JavaScript topics will keep appearing:

| JavaScript      | Where you'll use it in React |
| --------------- | ---------------------------- |
| Functions       | Components                   |
| Arrow functions | Components, callbacks        |
| Objects         | Props/state                  |
| Arrays          | Lists                        |
| `map()`         | Rendering lists              |
| `filter()`      | Filtering UI                 |
| Destructuring   | Props/state                  |
| Spread          | Updating state               |
| Callbacks       | Event handlers               |
| Closures        | Hooks                        |
| Promises        | API calls                    |
| `async/await`   | API calls                    |
| Modules         | React files                  |
| Immutability    | State management             |
| `this`          | Some JS/interview concepts   |
| ES6+            | Almost everywhere            |
| Event loop      | Async behavior               |
| Fetch           | Backend/API integration      |

**For your interview preparation, I would not just explain these as a syllabus. We can go through them one by one like we did with React:** concept → simple example → line-by-line explanation → common mistakes → interview questions → coding practice.
