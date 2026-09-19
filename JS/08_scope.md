# 8. Scope in JavaScript ⭐⭐⭐⭐⭐

**Scope is one of the most important JavaScript concepts for interviews and React.**

If you understand scope properly, topics like **closures, `this`, callbacks, modules, and React components** become much easier.

---

# 1. What is Scope?

**Scope determines where a variable can be accessed in your JavaScript code.**

In simple words:

> **Scope = Where a variable is available to use.**

Example:

```javascript
let name = "Sai";

console.log(name);
```

Here `name` is accessible because it was declared in the same/global scope.

But:

```javascript
function greet() {
    let message = "Hello";
}

console.log(message);
```

This gives:

```text
ReferenceError: message is not defined
```

Why?

Because `message` exists only inside the `greet()` function.

---

# 2. Why Do We Need Scope?

Imagine you have:

```javascript
let name = "Sai";
```

and another part of your application also needs a variable called `name`.

Without proper scope, variables could interfere with each other.

Scope helps JavaScript:

* control variable accessibility
* prevent accidental variable conflicts
* keep variables private
* organize large applications
* manage memory
* create closures
* make functions/components independent

This is especially important in React because every component has its own variables and functions.

---

# 3. Types of Scope

For interview purposes, understand these:

1. **Global Scope**
2. **Function Scope**
3. **Block Scope**
4. **Lexical Scope**
5. **Module Scope**

Let's understand each one.

---

# 4. Global Scope ⭐⭐⭐⭐

A variable declared outside functions and blocks is generally in the **global scope**.

Example:

```javascript
let name = "Sai";

function greet() {
    console.log(name);
}

greet();
```

Output:

```text
Sai
```

Why?

`name` is globally accessible, so the function can access it.

### Example

```javascript
let age = 22;

console.log(age);

function test() {
    console.log(age);
}

test();
```

Output:

```text
22
22
```

The function can access the global variable.

---

# 5. Global Scope Example

```javascript
let username = "Sai";

function login() {
    console.log(username);
}

function logout() {
    console.log(username);
}

login();
logout();
```

Output:

```text
Sai
Sai
```

Both functions can access `username`.

---

# 6. Problem With Too Many Global Variables

Suppose you have:

```javascript
let username = "Sai";
let age = 22;
let email = "sai@gmail.com";
let phone = "9999999999";
let address = "Kadapa";
```

If a large application has thousands of variables in global scope, variable conflicts can become a problem.

That's why we usually keep variables inside:

* functions
* blocks
* modules
* components

whenever possible.

---

# 7. Function Scope ⭐⭐⭐⭐⭐

A variable declared inside a function is accessible only inside that function.

Example:

```javascript
function greet() {
    let message = "Hello";

    console.log(message);
}

greet();
```

Output:

```text
Hello
```

But:

```javascript
function greet() {
    let message = "Hello";
}

console.log(message);
```

Output:

```text
ReferenceError
```

Because `message` belongs to the function's scope.

---

# 8. Function Scope With `let`

```javascript
function test() {
    let x = 10;

    console.log(x);
}

test();
```

`x` can be used inside `test()`.

But not outside:

```javascript
console.log(x);
```

❌ Error.

---

# 9. Function Scope With `const`

Same behavior:

```javascript
function test() {
    const x = 10;

    console.log(x);
}

test();
```

`x` exists only inside the function.

---

# 10. Function Scope With `var` ⭐⭐⭐⭐⭐

`var` is also **function-scoped**.

```javascript
function test() {
    var x = 10;

    console.log(x);
}

test();
```

Works.

But:

```javascript
console.log(x);
```

outside the function gives an error.

---

# 11. Block Scope ⭐⭐⭐⭐⭐

A **block** is code inside `{ }`.

For example:

```javascript
{
    let x = 10;
}
```

The `{ }` creates a block.

Variables declared with:

* `let`
* `const`

are **block-scoped**.

Example:

```javascript
{
    let name = "Sai";

    console.log(name);
}
```

Output:

```text
Sai
```

But:

```javascript
{
    let name = "Sai";
}

console.log(name);
```

❌ Error.

---

# 12. What Counts as a Block?

Examples include:

### `if`

```javascript
if (true) {
    let x = 10;
}
```

### `for`

```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

### `while`

```javascript
while (true) {
    let x = 10;
    break;
}
```

### Standalone block

```javascript
{
    let x = 10;
}
```

---

# 13. `let` and Block Scope ⭐⭐⭐⭐⭐

Example:

```javascript
if (true) {
    let message = "Hello";

    console.log(message);
}

console.log(message);
```

Output:

```text
Hello
ReferenceError
```

The second `console.log()` cannot access `message`.

---

# 14. `const` and Block Scope

Same thing:

```javascript
if (true) {
    const age = 22;

    console.log(age);
}
```

Works.

Outside:

```javascript
console.log(age);
```

❌ Error.

---

# 15. What About `var`?

This is an important interview question.

`var` does **not** have block scope.

Example:

```javascript
if (true) {
    var name = "Sai";
}

console.log(name);
```

Output:

```text
Sai
```

This surprises many beginners.

Why?

Because `var` is function-scoped, not block-scoped.

---

# 16. `var` vs `let` Scope ⭐⭐⭐⭐⭐

Compare:

### `var`

```javascript
if (true) {
    var x = 10;
}

console.log(x);
```

Output:

```text
10
```

### `let`

```javascript
if (true) {
    let x = 10;
}

console.log(x);
```

Output:

```text
ReferenceError
```

### `const`

```javascript
if (true) {
    const x = 10;
}

console.log(x);
```

Output:

```text
ReferenceError
```

So remember:

| Keyword | Function Scope | Block Scope |
| ------- | -------------- | ----------- |
| `var`   | ✅              | ❌           |
| `let`   | ✅              | ✅           |
| `const` | ✅              | ✅           |

This table is **very important for interviews**.

---

# 17. Nested Scope ⭐⭐⭐⭐⭐

Scopes can exist inside other scopes.

Example:

```javascript
let a = 10;

function outer() {
    let b = 20;

    function inner() {
        let c = 30;

        console.log(a);
        console.log(b);
        console.log(c);
    }

    inner();
}

outer();
```

Output:

```text
10
20
30
```

Why can `inner()` access all three?

Because of the **scope chain**.

---

# 18. Scope Chain ⭐⭐⭐⭐⭐

This is extremely important.

When JavaScript tries to find a variable, it searches:

**Current scope → Parent scope → Parent's parent → Global scope**

Example:

```javascript
let a = 10;

function outer() {
    let b = 20;

    function inner() {
        let c = 30;

        console.log(c);
        console.log(b);
        console.log(a);
    }

    inner();
}

outer();
```

When JavaScript sees:

```javascript
console.log(c);
```

It looks in `inner()`:

```text
inner scope
```

Finds `c`.

For:

```javascript
console.log(b);
```

It looks:

```text
inner scope
    ↓
outer scope
```

Finds `b`.

For:

```javascript
console.log(a);
```

It looks:

```text
inner scope
    ↓
outer scope
    ↓
global scope
```

Finds `a`.

This is called the **scope chain**.

---

# 19. Important Rule: Inner Can Access Outer

Example:

```javascript
let a = 10;

function outer() {
    let b = 20;

    function inner() {
        let c = 30;

        console.log(a);
        console.log(b);
        console.log(c);
    }

    inner();
}

outer();
```

`inner()` can access:

```text
c → own scope
b → outer scope
a → global scope
```

---

# 20. Important Rule: Outer Cannot Access Inner

This is the opposite.

```javascript
function outer() {

    function inner() {
        let secret = "Hello";
    }

    console.log(secret);
}

outer();
```

❌ Error.

Why?

`secret` belongs to `inner()`.

The outer function cannot go inside the inner function and access its variables.

Remember:

> **Inner scope can access outer scope, but outer scope cannot access inner scope.**

---

# 21. Simple Scope Diagram

Think of it like this:

```text
GLOBAL
│
├── a
│
└── outer()
    │
    ├── b
    │
    └── inner()
        │
        └── c
```

`inner()` can access:

```text
c
b
a
```

`outer()` can access:

```text
b
a
```

Global can access:

```text
a
```

Global cannot access:

```text
b
c
```

---

# 22. Lexical Scope ⭐⭐⭐⭐⭐

**Lexical scope** means that scope is determined by **where the code is written**, not where the function is called.

This is an important interview concept.

Example:

```javascript
let name = "Sai";

function outer() {

    let message = "Hello";

    function inner() {
        console.log(message);
    }

    inner();
}

outer();
```

`inner()` can access `message` because `inner()` was **written inside** `outer()`.

That's lexical scope.

---

# 23. Another Lexical Scope Example

```javascript
let x = 10;

function test() {
    console.log(x);
}

function another() {
    let x = 20;

    test();
}

another();
```

What is the output?

```text
10
```

Not:

```text
20
```

Why?

Because `test()` was defined in the global scope.

Its scope is determined by **where it was defined**, not where it was called.

This is a very common interview question.

---

# 24. Lexical Scope vs Dynamic Scope

JavaScript uses **lexical scope**.

### Lexical scope

Scope depends on:

> Where the function is written.

### Dynamic scope

Scope would depend on:

> Where the function is called.

JavaScript uses lexical scope.

So:

```javascript
let x = 10;

function test() {
    console.log(x);
}

function another() {
    let x = 20;
    test();
}

another();
```

Output:

```text
10
```

---

# 25. Scope and `var`, `let`, `const`

Let's combine everything.

```javascript
var a = 10;
let b = 20;
const c = 30;

function test() {

    var x = 40;
    let y = 50;
    const z = 60;

}
```

Here:

```text
Global:
a
b
c

Function test():
x
y
z
```

Outside `test()`:

```javascript
console.log(x);
```

❌ Error.

---

# 26. Block Scope Example

```javascript
function test() {

    if (true) {

        var a = 10;
        let b = 20;
        const c = 30;

    }

    console.log(a);
    console.log(b);
    console.log(c);
}

test();
```

Output:

```text
10
ReferenceError
ReferenceError
```

Why?

`a` uses `var`, so it is function-scoped.

`b` and `c` use `let` and `const`, so they are block-scoped.

---

# 27. Scope in Loops ⭐⭐⭐⭐⭐

This is another important interview topic.

Consider:

```javascript
for (let i = 0; i < 3; i++) {
    console.log(i);
}

console.log(i);
```

Output:

```text
0
1
2
ReferenceError
```

Because `i` is block-scoped.

---

# 28. What Happens With `var`?

```javascript
for (var i = 0; i < 3; i++) {
    console.log(i);
}

console.log(i);
```

Output:

```text
0
1
2
3
```

Because `var` does not have block scope.

This is one reason modern JavaScript generally prefers:

```javascript
let
const
```

over:

```javascript
var
```

---

# 29. Scope and Functions

Functions create their own scope.

Example:

```javascript
function first() {
    let a = 10;

    function second() {
        let b = 20;

        console.log(a);
        console.log(b);
    }

    second();
}

first();
```

Scope structure:

```text
Global
  ↓
first()
  ↓
second()
```

`second()` can access variables from `first()`.

---

# 30. Scope and Closures ⭐⭐⭐⭐⭐

Scope is directly connected to **closures**.

Consider:

```javascript
function outer() {

    let count = 0;

    function inner() {
        count++;
        console.log(count);
    }

    return inner;
}

const counter = outer();

counter();
counter();
counter();
```

Output:

```text
1
2
3
```

Why can `inner()` still access `count` even after `outer()` has finished?

Because of a **closure**.

A closure allows a function to remember variables from its outer lexical scope.

We'll study closures later in detail.

For now remember:

> **Closures are built on lexical scope.**

---

# 31. Scope in React ⭐⭐⭐⭐⭐

Scope is very important in React.

Consider:

```jsx
function App() {

    const name = "Sai";

    function greet() {
        console.log(name);
    }

    return (
        <button onClick={greet}>
            Click
        </button>
    );
}
```

Here:

```text
App component scope
│
├── name
│
└── greet()
```

`greet()` can access:

```javascript
name
```

because `name` is in its outer lexical scope.

---

# 32. React Component Scope

Example:

```jsx
function User() {

    const name = "Sai";
    const age = 22;

    return (
        <div>
            <h1>{name}</h1>
            <p>{age}</p>
        </div>
    );
}
```

`name` and `age` belong to the `User` function's scope.

They are not automatically available outside:

```jsx
function User() {
    const name = "Sai";
}

console.log(name);
```

❌ Error.

---

# 33. React Event Handler and Scope

```jsx
function App() {

    const name = "Sai";

    function handleClick() {
        alert(name);
    }

    return (
        <button onClick={handleClick}>
            Click
        </button>
    );
}
```

When the button is clicked, `handleClick()` can access `name`.

Why?

Because of lexical scope.

This becomes especially important when you learn:

* callbacks
* closures
* state
* hooks
* event handlers

---

# 34. Module Scope ⭐⭐⭐⭐

Modern JavaScript applications commonly use modules.

Example:

### `user.js`

```javascript
const username = "Sai";

export { username };
```

### `app.js`

```javascript
import { username } from "./user.js";

console.log(username);
```

Variables inside a module are normally scoped to that module unless explicitly exported.

This is called **module scope**.

React applications use modules heavily:

```javascript
import React from "react";
import User from "./User";
import Header from "./Header";
```

Each file can have its own scope.

---

# 35. Global vs Function vs Block Scope

Here's the important comparison:

| Scope    | Where variable is accessible               |
| -------- | ------------------------------------------ |
| Global   | Throughout applicable global code          |
| Function | Inside the function                        |
| Block    | Inside `{}` block                          |
| Module   | Inside the module unless exported/imported |
| Lexical  | Based on where code is written             |

---

# 36. `var`, `let`, `const` Scope Comparison

Memorize this:

| Feature                  | `var`     | `let` | `const` |
| ------------------------ | --------- | ----- | ------- |
| Function scoped          | ✅         | ✅     | ✅       |
| Block scoped             | ❌         | ✅     | ✅       |
| Can reassign             | ✅         | ✅     | ❌       |
| Can redeclare same scope | ✅         | ❌     | ❌       |
| Recommended today        | Usually ❌ | ✅     | ✅       |

---

# 37. Common Scope Mistake #1

### Wrong thinking:

```javascript
if (true) {
    let username = "Sai";
}

console.log(username);
```

You might think:

> "The variable was created above, so I can use it."

No.

`username` belongs to the `if` block.

---

# 38. Common Scope Mistake #2

Thinking `var` is block-scoped:

```javascript
if (true) {
    var x = 10;
}

console.log(x);
```

This works because `var` is function-scoped.

---

# 39. Common Scope Mistake #3

Thinking function scope works both ways.

```javascript
function test() {
    let x = 10;
}

console.log(x);
```

❌ Not allowed.

The outside cannot access the function's local variables.

---

# 40. Common Scope Mistake #4

Confusing lexical scope with where a function is called.

```javascript
let x = "global";

function test() {
    console.log(x);
}

function run() {
    let x = "local";
    test();
}

run();
```

Output:

```text
global
```

Because `test()` was defined in the global scope.

---

# 41. Interview Output Question ⭐⭐⭐⭐⭐

### Question 1

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

Why?

The function has its own local `x`.

---

# 42. Interview Output Question 2

```javascript
let x = 10;

function test() {
    console.log(x);
}

test();
```

Output:

```text
10
```

The function doesn't have a local `x`, so JavaScript searches the outer scope.

---

# 43. Interview Output Question 3

```javascript
let x = 10;

function test() {
    let x = 20;

    function inner() {
        let x = 30;
        console.log(x);
    }

    inner();
}

test();
```

Output:

```text
30
```

Why?

JavaScript first checks the current scope.

It finds:

```javascript
let x = 30;
```

---

# 44. Interview Output Question 4 ⭐⭐⭐⭐⭐

```javascript
let x = 10;

function test() {
    console.log(x);

    let x = 20;
}

test();
```

What happens?

It gives:

```text
ReferenceError
```

This is related to **Temporal Dead Zone (TDZ)**.

`x` exists in the function's scope but cannot be accessed before its declaration.

We'll connect this more deeply with hoisting/TDZ.

---

# 45. Interview Output Question 5

```javascript
if (true) {
    var a = 10;
    let b = 20;
}

console.log(a);
console.log(b);
```

Output:

```text
10
ReferenceError
```

Because:

```text
var → function scoped
let → block scoped
```

---

# 46. Interview Output Question 6 ⭐⭐⭐⭐⭐

```javascript
let x = 10;

function outer() {

    let x = 20;

    function inner() {
        console.log(x);
    }

    return inner;
}

const fn = outer();

fn();
```

Output:

```text
20
```

Why?

`inner()` remembers the lexical environment where it was created.

This is a **closure**.

---

# 47. Important Scope Rules to Memorize

### Rule 1

Inner scope can access outer scope.

```text
inner → outer → global
```

### Rule 2

Outer scope cannot access inner scope.

```text
outer ❌→ inner
```

### Rule 3

JavaScript uses lexical scope.

```text
Scope depends on where code is written.
```

### Rule 4

`var` is function-scoped.

### Rule 5

`let` and `const` are block-scoped.

### Rule 6

Functions create their own scope.

### Rule 7

Blocks create scope for `let` and `const`.

### Rule 8

Scope chain is used to find variables.

### Rule 9

Closures depend on lexical scope.

---

# 48. Scope vs Hoisting

These concepts are related but different.

### Scope

Answers:

> **Where can I access this variable?**

### Hoisting

Answers:

> **What happens to declarations during JavaScript's execution setup?**

Example:

```javascript
function test() {
    console.log(x);

    var x = 10;
}
```

`x` is function-scoped, but `var` declaration is hoisted.

So scope and hoisting are separate concepts.

You already studied hoisting earlier, so keep this distinction clear.

---

# 49. Scope vs Closure

### Scope

Determines where variables are accessible.

### Closure

Allows a function to remember/access variables from its outer lexical scope even after the outer function has finished.

Think:

```text
Scope
   ↓
Lexical Scope
   ↓
Scope Chain
   ↓
Closure
```

These concepts are strongly connected.

---

# 50. Scope in React — What You Should Know for Interviews

You should be comfortable explaining this:

```jsx
function Counter() {

    const message = "Hello";

    function handleClick() {
        console.log(message);
    }

    return (
        <button onClick={handleClick}>
            Click
        </button>
    );
}
```

Interview explanation:

> "`message` is inside the `Counter` component's function scope. `handleClick` is also defined inside `Counter`, so due to JavaScript's lexical scoping, `handleClick` can access `message`."

That's a strong React + JavaScript answer.

---

# 51. Real-World React Example

Later you'll write code like:

```jsx
function UserProfile({ name }) {

    const greeting = `Hello ${name}`;

    function handleClick() {
        console.log(greeting);
    }

    return (
        <button onClick={handleClick}>
            {greeting}
        </button>
    );
}
```

Here:

```text
UserProfile scope
│
├── name
├── greeting
│
└── handleClick()
       │
       └── can access greeting
```

This is lexical scope + closure behavior.

---

# 52. Interview Questions You Must Know ⭐⭐⭐⭐⭐

### Beginner

1. What is scope in JavaScript?
2. What is global scope?
3. What is function scope?
4. What is block scope?
5. What is lexical scope?
6. What is the scope chain?
7. What is module scope?

### Very important

8. Difference between `var`, `let`, and `const` scope?
9. Why is `var` function-scoped?
10. Why are `let` and `const` block-scoped?
11. Can an inner function access variables from an outer function?
12. Can an outer function access variables from an inner function?
13. What is lexical scoping?
14. What is the scope chain?
15. How is scope related to closures?
16. How does scope work inside React components?

### Output-based

17. Predict the output of nested scopes.
18. Predict the output of `var` inside an `if`.
19. Predict the output of `let` inside a loop.
20. Predict the output when the same variable name exists in multiple scopes.
21. Explain why a variable gives `ReferenceError` before declaration.

---

# 53. One-Minute Interview Answer

If the interviewer asks:

**"What is scope in JavaScript?"**

You can answer:

> **Scope determines where a variable can be accessed in JavaScript. JavaScript has global, function, block, and module scopes. `var` is function-scoped, while `let` and `const` are block-scoped. JavaScript uses lexical scoping, meaning a function's scope is determined by where it is defined. When looking for a variable, JavaScript follows the scope chain from the current scope to its outer scopes. Lexical scope is also the foundation for closures.**

That's an excellent interview-level answer.

---

# 54. Scope Cheat Sheet ⭐⭐⭐⭐⭐

```text
SCOPE
│
├── Global Scope
│
├── Function Scope
│      └── var
│
├── Block Scope
│      ├── let
│      └── const
│
├── Module Scope
│
└── Lexical Scope
       │
       └── Scope Chain
              │
              └── Closures
```

### Remember:

```javascript
var   → function scoped
let   → block scoped
const → block scoped
```

And:

```text
Current scope
      ↓
Outer scope
      ↓
Outer scope
      ↓
Global scope
```

This search process is the **scope chain**.

---

# 55. What You Should Practice

Before moving to the next topic, practice predicting the output of these:

### Practice 1

```javascript
let name = "Global";

function test() {
    let name = "Local";
    console.log(name);
}

test();
console.log(name);
```

### Practice 2

```javascript
if (true) {
    let x = 10;
}

console.log(x);
```

### Practice 3

```javascript
if (true) {
    var x = 10;
}

console.log(x);
```

### Practice 4

```javascript
let x = 10;

function outer() {
    let x = 20;

    function inner() {
        console.log(x);
    }

    inner();
}

outer();
```

### Practice 5

```javascript
let x = 10;

function test() {
    console.log(x);
}

function run() {
    let x = 20;
    test();
}

run();
```

For each one, don't just find the output—**explain which scope JavaScript searches first and why.**