# 9. Hoisting in JavaScript ⭐⭐⭐⭐⭐

**Hoisting is one of the most important JavaScript interview topics.**

It is especially important because interviewers often give you code like:

```javascript
console.log(x);
var x = 10;
```

and ask:

> **What is the output?**

To answer these questions confidently, you need to understand:

* What is hoisting?
* `var` hoisting
* `let` and `const` hoisting
* Temporal Dead Zone (TDZ)
* Function declaration hoisting
* Function expression hoisting
* Arrow function hoisting
* Scope + hoisting together
* Common interview traps
* React connection

---

# 1. What is Hoisting?

**Hoisting is JavaScript's behavior of processing declarations before executing the code in their scope.**

A simple interview-friendly explanation:

> **JavaScript processes certain declarations before executing the code, which makes it possible to reference some variables or functions before their declaration appears in the source code.**

But be careful:

> **Hoisting does NOT mean JavaScript physically moves your code to the top.**

That's a very common misconception.

---

# 2. Simple Example of Hoisting

Consider:

```javascript
console.log(x);

var x = 10;
```

Output:

```text
undefined
```

Many beginners expect:

```text
ReferenceError
```

But because `var` is hoisted, the declaration is processed before execution.

Conceptually, you can think of it approximately like:

```javascript
var x;

console.log(x);

x = 10;
```

So:

```javascript
console.log(x);
```

sees:

```text
undefined
```

---

# 3. Important: Declaration vs Initialization

This distinction is **extremely important**.

Consider:

```javascript
var x = 10;
```

There are actually two things happening:

```text
Declaration:
var x

Initialization/Assignment:
x = 10
```

During hoisting:

```javascript
var x;
```

is processed first.

But:

```javascript
x = 10;
```

doesn't happen until JavaScript reaches that line during execution.

So:

```javascript
console.log(x);

var x = 10;
```

acts conceptually like:

```javascript
var x;

console.log(x); // undefined

x = 10;
```

---

# 4. Hoisting Does NOT Move the Value

This is wrong:

```text
JavaScript moves:
var x = 10;
to the top
```

Instead, think:

```text
Declaration → processed early
Assignment  → happens where written
```

For:

```javascript
var x = 10;
```

JavaScript processes:

```javascript
var x;
```

before execution.

But:

```javascript
x = 10;
```

happens later.

---

# 5. `var` Hoisting ⭐⭐⭐⭐⭐

`var` declarations are hoisted and initialized with:

```javascript
undefined
```

Example:

```javascript
console.log(x);

var x = 10;
```

Output:

```text
undefined
```

---

# 6. Another `var` Example

```javascript
console.log(a);
console.log(b);

var a = 10;
var b = 20;
```

Output:

```text
undefined
undefined
```

Conceptually:

```javascript
var a;
var b;

console.log(a);
console.log(b);

a = 10;
b = 20;
```

---

# 7. `var` Declaration vs Assignment

Look at:

```javascript
var x = 100;
```

During the setup phase:

```javascript
var x;
```

During execution:

```javascript
x = 100;
```

Therefore:

```javascript
console.log(x);

var x = 100;
```

produces:

```text
undefined
```

not:

```text
100
```

---

# 8. `let` and `const` Hoisting ⭐⭐⭐⭐⭐

This is where interviews become tricky.

You might hear:

> "`let` and `const` are not hoisted."

That's **not technically correct**.

`let` and `const` declarations are also processed during the creation/setup of their scope, but they are **not initialized in the same way as `var`**.

Before their declaration is reached, accessing them results in a:

```text
ReferenceError
```

This period is called the:

# Temporal Dead Zone (TDZ)

---

# 9. Temporal Dead Zone (TDZ) ⭐⭐⭐⭐⭐

Example:

```javascript
console.log(x);

let x = 10;
```

Output:

```text
ReferenceError
```

Why?

Because `x` is in the **Temporal Dead Zone** from the beginning of its scope until the declaration is executed.

---

# 10. Simple TDZ Diagram

For:

```javascript
console.log(x);

let x = 10;
```

Think:

```text
Scope begins
     ↓
x exists but is uninitialized
     ↓
Temporal Dead Zone
     ↓
console.log(x) ❌
     ↓
let x = 10
     ↓
TDZ ends
     ↓
x can now be accessed
```

---

# 11. `let` Example

```javascript
console.log(name);

let name = "Sai";
```

Result:

```text
ReferenceError
```

Not:

```text
undefined
```

This is because `let` doesn't get the `undefined` initialization that `var` gets.

---

# 12. `const` Example

Same behavior:

```javascript
console.log(age);

const age = 22;
```

Result:

```text
ReferenceError
```

So:

```text
var   → undefined before declaration
let   → ReferenceError
const → ReferenceError
```

---

# 13. `var` vs `let` vs `const` ⭐⭐⭐⭐⭐

Memorize this table:

| Feature                                | `var`       | `let`            | `const`          |
| -------------------------------------- | ----------- | ---------------- | ---------------- |
| Declaration processed before execution | ✅           | ✅                | ✅                |
| Initialized immediately to `undefined` | ✅           | ❌                | ❌                |
| TDZ                                    | ❌           | ✅                | ✅                |
| Access before declaration              | `undefined` | ❌ ReferenceError | ❌ ReferenceError |
| Block scoped                           | ❌           | ✅                | ✅                |
| Function scoped                        | ✅           | ✅                | ✅                |

The key difference is:

> **`var` is initialized to `undefined`; `let` and `const` remain uninitialized until execution reaches their declaration.**

---

# 14. Why Is It Called "Temporal" Dead Zone?

"Temporal" refers to **time**.

It's not about a physical area of code.

Example:

```javascript
{
    // TDZ starts

    console.log(x); // ❌

    let x = 10;

    // TDZ ends
}
```

The variable `x` cannot be accessed during the period between entering the scope and executing:

```javascript
let x = 10;
```

---

# 15. TDZ Doesn't Mean the Variable Doesn't Exist

This is an important distinction.

Consider:

```javascript
{
    console.log(x);

    let x = 10;
}
```

It's tempting to say:

> "x doesn't exist yet."

More accurately:

> `x` is already associated with that scope, but it has not been initialized, so accessing it causes a `ReferenceError`.

---

# 16. `var` vs `let` Example ⭐⭐⭐⭐⭐

### `var`

```javascript
console.log(x);

var x = 10;
```

Output:

```text
undefined
```

### `let`

```javascript
console.log(x);

let x = 10;
```

Output:

```text
ReferenceError
```

### `const`

```javascript
console.log(x);

const x = 10;
```

Output:

```text
ReferenceError
```

---

# 17. Function Declaration Hoisting ⭐⭐⭐⭐⭐

Function declarations are also hoisted.

Example:

```javascript
greet();

function greet() {
    console.log("Hello");
}
```

Output:

```text
Hello
```

This works.

Why?

The function declaration is available when the code starts executing.

---

# 18. Function Declaration Example

You can write:

```javascript
sayHello();

function sayHello() {
    console.log("Hello Sai");
}
```

Output:

```text
Hello Sai
```

Unlike a variable assignment, the function declaration can be called before it appears in the source code.

---

# 19. Conceptually Think of Function Hoisting Like This

Original:

```javascript
greet();

function greet() {
    console.log("Hello");
}
```

Conceptually:

```javascript
function greet() {
    console.log("Hello");
}

greet();
```

Again, this is a **conceptual model**, not JavaScript physically moving the text.

---

# 20. Function Declaration vs Function Expression ⭐⭐⭐⭐⭐

This is a very common interview question.

### Function declaration

```javascript
greet();

function greet() {
    console.log("Hello");
}
```

Works.

### Function expression

```javascript
greet();

const greet = function() {
    console.log("Hello");
};
```

Doesn't work.

You'll get:

```text
ReferenceError
```

because `greet` is a `const` variable and is in the TDZ.

---

# 21. Arrow Function Hoisting

Arrow functions are commonly assigned to variables.

Example:

```javascript
greet();

const greet = () => {
    console.log("Hello");
};
```

Result:

```text
ReferenceError
```

Why?

Because:

```javascript
const greet
```

is subject to TDZ.

---

# 22. Arrow Function With `let`

```javascript
greet();

let greet = () => {
    console.log("Hello");
};
```

Result:

```text
ReferenceError
```

Again, `greet` is in the TDZ.

---

# 23. Arrow Function With `var`

Interesting case:

```javascript
greet();

var greet = () => {
    console.log("Hello");
};
```

Result:

```text
TypeError
```

Why?

Conceptually:

```javascript
var greet;

greet();

greet = () => {
    console.log("Hello");
};
```

At the time of the call:

```javascript
greet
```

is:

```text
undefined
```

Trying to call:

```javascript
undefined()
```

produces a `TypeError`.

---

# 24. Very Important Comparison

### Function declaration

```javascript
greet();

function greet() {}
```

✅ Works.

### `var` function expression

```javascript
greet();

var greet = function() {};
```

❌ TypeError.

### `let` function expression

```javascript
greet();

let greet = function() {};
```

❌ ReferenceError.

### `const` function expression

```javascript
greet();

const greet = function() {};
```

❌ ReferenceError.

### `const` arrow function

```javascript
greet();

const greet = () => {};
```

❌ ReferenceError.

---

# 25. Why Different Errors?

This is a great interview question.

### `var`

```javascript
var greet;
greet();
```

`greet` is:

```text
undefined
```

Calling `undefined`:

```text
TypeError
```

### `let` / `const`

```javascript
greet();
let greet = ...
```

`greet` is still in the TDZ.

So:

```text
ReferenceError
```

---

# 26. Function Declaration Parameters

Consider:

```javascript
greet("Sai");

function greet(name) {
    console.log("Hello " + name);
}
```

Output:

```text
Hello Sai
```

The function itself is available before its declaration.

---

# 27. Function Declarations Inside Blocks

Modern JavaScript has some nuanced behavior around function declarations inside blocks, especially across environments and strict mode.

For interview preparation, focus primarily on:

```javascript
function greet() {}
```

at normal function/module scope.

Don't rely on block-level function declarations for production code when a clearer `const` function expression is possible.

---

# 28. Hoisting and Scope ⭐⭐⭐⭐⭐

Let's combine the two concepts.

```javascript
function test() {

    console.log(x);

    var x = 10;
}

test();
```

Output:

```text
undefined
```

Why?

The `var x` is function-scoped and its declaration is hoisted.

Conceptually:

```javascript
function test() {

    var x;

    console.log(x);

    x = 10;
}
```

---

# 29. Hoisting Inside a Block

Consider:

```javascript
function test() {

    if (true) {
        var x = 10;
    }

    console.log(x);
}

test();
```

Output:

```text
10
```

Why?

Because `var` is function-scoped, not block-scoped.

---

# 30. `let` Inside a Block

```javascript
function test() {

    if (true) {
        let x = 10;
    }

    console.log(x);
}

test();
```

Result:

```text
ReferenceError
```

Why?

Because `x` is block-scoped.

---

# 31. Hoisting With Shadowing ⭐⭐⭐⭐⭐

Consider:

```javascript
let x = 10;

function test() {

    let x = 20;

    console.log(x);
}

test();

console.log(x);
```

Output:

```text
20
10
```

The local `x` shadows the global `x`.

---

# 32. The Famous TDZ Interview Question

Look carefully:

```javascript
let x = 10;

function test() {

    console.log(x);

    let x = 20;
}

test();
```

What happens?

Many beginners say:

```text
10
```

But the answer is:

```text
ReferenceError
```

Why?

Inside `test()`:

```javascript
let x = 20;
```

creates a local `x`.

That local `x` is in the TDZ before its declaration is executed.

So JavaScript doesn't continue searching for the global `x`.

Conceptually:

```text
test scope
│
└── x → uninitialized (TDZ)
```

Therefore:

```javascript
console.log(x);
```

❌ ReferenceError.

---

# 33. Another Important Example

```javascript
var x = 10;

function test() {

    console.log(x);

    var x = 20;
}

test();
```

Output:

```text
undefined
```

Why not `10`?

Because the local:

```javascript
var x;
```

is hoisted to the top of the function.

Conceptually:

```javascript
var x = 10;

function test() {

    var x;

    console.log(x);

    x = 20;
}
```

The local `x` shadows the global one.

---

# 34. Compare `var` and `let` Shadowing

### `var`

```javascript
var x = 10;

function test() {
    console.log(x);
    var x = 20;
}

test();
```

Output:

```text
undefined
```

### `let`

```javascript
let x = 10;

function test() {
    console.log(x);
    let x = 20;
}

test();
```

Output:

```text
ReferenceError
```

Both have a local `x`, but their initialization behavior differs.

---

# 35. Hoisting and `const`

Consider:

```javascript
const x = 10;

console.log(x);
```

Works normally.

But:

```javascript
console.log(x);

const x = 10;
```

gives:

```text
ReferenceError
```

Because `x` is in the TDZ.

---

# 36. Can You Access a `var` Before Declaration?

Yes, but you get:

```text
undefined
```

Example:

```javascript
console.log(x);

var x = 100;
```

Output:

```text
undefined
```

However, this does **not** mean you should write code this way.

Modern JavaScript generally prefers declaring variables before using them.

---

# 37. Best Practice ⭐⭐⭐⭐⭐

Even though JavaScript allows:

```javascript
console.log(x);

var x = 10;
```

avoid writing code like this.

Prefer:

```javascript
const x = 10;

console.log(x);
```

Or:

```javascript
let x = 10;

console.log(x);
```

This makes the code easier to read and reduces confusion.

---

# 38. Hoisting and React

Hoisting matters in React because React applications contain:

* functions
* variables
* components
* imports
* event handlers
* callbacks

Example:

```jsx
function App() {

    handleClick();

    function handleClick() {
        console.log("Clicked");
    }

    return <h1>Hello</h1>;
}
```

This works because `handleClick` is a function declaration.

---

# 39. React Arrow Function Example

Consider:

```jsx
function App() {

    handleClick();

    const handleClick = () => {
        console.log("Clicked");
    };

    return <h1>Hello</h1>;
}
```

This gives:

```text
ReferenceError
```

because `handleClick` is declared with `const` and is in the TDZ.

---

# 40. React Components and Hoisting

Consider:

```jsx
const App = () => {
    return <h1>Hello</h1>;
};

export default App;
```

This is common React code.

You should not assume:

```javascript
App
```

can safely be used before the `const` declaration.

For example:

```jsx
console.log(App);

const App = () => {
    return <h1>Hello</h1>;
};
```

will result in:

```text
ReferenceError
```

---

# 41. Function Component Declaration

You can also write:

```jsx
function App() {
    return <h1>Hello</h1>;
}

export default App;
```

Function declarations have different hoisting behavior.

For example:

```jsx
console.log(App);

function App() {
    return <h1>Hello</h1>;
}
```

The function declaration is available.

---

# 42. Imports and Hoisting

You'll also hear that ES module imports are processed before normal module code executes.

For example:

```javascript
import React from "react";
import User from "./User";
```

Modules have their own execution and binding rules.

For your React interviews, the main things to remember are:

```text
function declaration → callable before declaration
var variable → undefined before initialization
let variable → TDZ
const variable → TDZ
arrow function stored in let/const → TDZ behavior
```

---

# 43. Hoisting vs Scope

These are different concepts.

### Scope asks:

> Where can I access this variable?

### Hoisting asks:

> What happens to a declaration during the setup of its scope before execution?

Example:

```javascript
function test() {

    var x = 10;

}
```

Scope:

```text
x belongs to test()
```

Hoisting:

```text
var x declaration is processed before execution
```

---

# 44. Hoisting vs TDZ

### Hoisting

Declarations are processed before execution.

### TDZ

`let` and `const` cannot be accessed from the beginning of their scope until their declaration is executed.

So:

```text
let / const
     ↓
processed in scope
     ↓
uninitialized
     ↓
TDZ
     ↓
declaration executes
     ↓
initialized
```

---

# 45. Hoisting Interview Cheat Sheet ⭐⭐⭐⭐⭐

Memorize this:

```text
VAR
↓
Declaration processed
↓
Initialized as undefined
↓
Can be accessed before declaration
↓
Result: undefined
```

```text
LET / CONST
↓
Declaration processed
↓
Not initialized
↓
TDZ
↓
Access before declaration
↓
ReferenceError
```

```text
FUNCTION DECLARATION
↓
Function available before declaration
↓
Can be called before declaration
```

```text
FUNCTION EXPRESSION / ARROW FUNCTION
↓
Depends on variable declaration
↓
const / let → ReferenceError before declaration
↓
var → TypeError when called before assignment
```

---

# 46. Most Important Examples to Memorize

### Example 1 — `var`

```javascript
console.log(a);
var a = 10;
```

Output:

```text
undefined
```

---

### Example 2 — `let`

```javascript
console.log(a);
let a = 10;
```

Output:

```text
ReferenceError
```

---

### Example 3 — `const`

```javascript
console.log(a);
const a = 10;
```

Output:

```text
ReferenceError
```

---

### Example 4 — Function declaration

```javascript
greet();

function greet() {
    console.log("Hello");
}
```

Output:

```text
Hello
```

---

### Example 5 — Function expression

```javascript
greet();

const greet = function() {
    console.log("Hello");
};
```

Output:

```text
ReferenceError
```

---

### Example 6 — Arrow function

```javascript
greet();

const greet = () => {
    console.log("Hello");
};
```

Output:

```text
ReferenceError
```

---

### Example 7 — `var` function expression

```javascript
greet();

var greet = function() {
    console.log("Hello");
};
```

Output:

```text
TypeError
```

---

# 47. Common Interview Mistakes ❌

### Mistake 1

> "`let` and `const` are not hoisted."

More accurate:

> `let` and `const` declarations are processed/hoisted, but they remain uninitialized in the TDZ until execution reaches their declaration.

---

### Mistake 2

> "Hoisting moves code to the top."

Not exactly.

Hoisting is a behavior of how JavaScript handles declarations during execution setup.

---

### Mistake 3

> "`var x = 10` is completely hoisted."

No.

The declaration is processed:

```javascript
var x;
```

The assignment happens later:

```javascript
x = 10;
```

---

### Mistake 4

> "All functions can be called before declaration."

Not all.

This works:

```javascript
function test() {}
```

But this doesn't:

```javascript
const test = () => {};
```

before the declaration.

---

# 48. Interview Questions ⭐⭐⭐⭐⭐

You should be able to answer these without hesitation:

### Basic

1. What is hoisting?
2. Does JavaScript physically move declarations to the top?
3. What gets hoisted?
4. Are variables hoisted?
5. Are functions hoisted?

### `var`

6. What happens when accessing a `var` before declaration?
7. Why does `var` return `undefined`?

### `let` / `const`

8. Are `let` and `const` hoisted?
9. What is the Temporal Dead Zone?
10. Why does accessing `let` before declaration give `ReferenceError`?
11. Why does accessing `const` before declaration give `ReferenceError`?

### Functions

12. Are function declarations hoisted?
13. Are function expressions hoisted?
14. Are arrow functions hoisted?
15. Difference between function declaration and function expression regarding hoisting?

### Advanced

16. What is the difference between hoisting and scope?
17. What is TDZ?
18. What happens when a local variable shadows a global variable?
19. How does hoisting work inside a function?
20. How does hoisting affect React functional components?

---

# 49. One-Minute Interview Answer

If an interviewer asks:

**"Explain hoisting in JavaScript."**

A strong answer is:

> **Hoisting is JavaScript's behavior where declarations are processed during the setup of their scope before the code executes. `var` declarations are initialized with `undefined`, so accessing them before the declaration gives `undefined`. `let` and `const` are also processed but remain uninitialized in the Temporal Dead Zone until their declaration is executed, so accessing them early causes a `ReferenceError`. Function declarations are available before their position in the code, while function expressions and arrow functions follow the hoisting behavior of the variable they're assigned to.**

---

# 50. Final Mental Model 🧠

Think of JavaScript execution in two broad stages:

```text
              JavaScript Execution
                      │
          ┌───────────┴───────────┐
          ↓                       ↓
   Setup / Creation          Execution
          │                       │
          │                       │
          ├── var → undefined     │
          │                       │
          ├── let → uninitialized │
          │      (TDZ)             │
          │                       │
          ├── const → uninitialized
          │      (TDZ)             │
          │                       │
          └── function declaration
              available             │
                                  ↓
                         Code runs line by line
```

The most important thing to remember:

```text
var
→ hoisted + initialized undefined

let
→ hoisted/processed + uninitialized
→ TDZ
→ ReferenceError if accessed early

const
→ hoisted/processed + uninitialized
→ TDZ
→ ReferenceError if accessed early

function declaration
→ available before declaration

function expression / arrow
→ follows variable declaration rules
```

### ⭐ For your React interview preparation

Make sure you can confidently explain these four examples:

```javascript
console.log(a);
var a = 10;       // undefined
```

```javascript
console.log(a);
let a = 10;       // ReferenceError
```

```javascript
greet();

function greet() {} // works
```

```javascript
greet();

const greet = () => {}; // ReferenceError
```

These patterns cover a large part of the **hoisting questions asked in JavaScript/React interviews**.