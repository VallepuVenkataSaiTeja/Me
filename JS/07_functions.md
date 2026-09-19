# 7. Functions ⭐⭐⭐⭐⭐

Functions are one of the **most important topics in JavaScript and React**.

If you understand functions well, many React concepts become much easier:

* Components are functions
* Event handlers are functions
* Callbacks are functions
* `map()` uses functions
* `filter()` uses functions
* Hooks are functions
* `useEffect()` receives a function
* API functions are commonly written as functions
* Redux actions/reducers involve functions

So this topic is worth learning thoroughly.

---

# 1. What is a Function?

A function is a **reusable block of code designed to perform a specific task**.

For example:

```javascript
function greet() {
    console.log("Hello");
}
```

We have created a function called:

```text
greet
```

But the code doesn't execute just because we created the function.

We need to **call** it:

```javascript
greet();
```

Output:

```text
Hello
```

---

# 2. Why Do We Need Functions?

Without functions:

```javascript
console.log("Hello Sai");
console.log("Hello Rahul");
console.log("Hello John");
```

You may end up repeating code.

With a function:

```javascript
function greet(name) {
    console.log("Hello " + name);
}

greet("Sai");
greet("Rahul");
greet("John");
```

Output:

```text
Hello Sai
Hello Rahul
Hello John
```

The same logic can be reused with different data.

---

# 3. Basic Function Syntax

```javascript
function functionName() {
    // code
}
```

Example:

```javascript
function greet() {
    console.log("Hello");
}
```

The general structure is:

```text
function
   ↓
function name
   ↓
function greet() {
    ↓
  function body
}
```

---

# 4. Calling a Function

Creating a function:

```javascript
function greet() {
    console.log("Hello");
}
```

Calling it:

```javascript
greet();
```

The parentheses:

```javascript
()
```

are important when calling the function.

---

# 5. Function Declaration

The example above is called a **function declaration**.

```javascript
function greet() {
    console.log("Hello");
}
```

Another example:

```javascript
function add() {
    console.log(10 + 20);
}
```

Call it:

```javascript
add();
```

Output:

```text
30
```

---

# 6. Parameters

Functions can receive information.

Example:

```javascript
function greet(name) {
    console.log("Hello " + name);
}
```

Here:

```javascript
name
```

is called a **parameter**.

When calling:

```javascript
greet("Sai");
```

`"Sai"` is the **argument**.

Output:

```text
Hello Sai
```

---

# 7. Parameter vs Argument ⭐⭐⭐⭐⭐

This is a common interview question.

### Parameter

The variable defined in the function:

```javascript
function greet(name) {
    // name = parameter
}
```

### Argument

The actual value passed when calling the function:

```javascript
greet("Sai");
// "Sai" = argument
```

Easy way:

```text
Parameter → placeholder
Argument  → actual value
```

---

# 8. Multiple Parameters

A function can accept multiple parameters.

```javascript
function add(a, b) {
    console.log(a + b);
}
```

Call:

```javascript
add(10, 20);
```

Output:

```text
30
```

Here:

```text
a = 10
b = 20
```

---

# 9. More Examples

```javascript
function multiply(a, b) {
    console.log(a * b);
}

multiply(5, 4);
```

Output:

```text
20
```

Another:

```javascript
function introduce(name, age) {
    console.log("My name is " + name);
    console.log("I am " + age + " years old");
}

introduce("Sai", 25);
```

Output:

```text
My name is Sai
I am 25 years old
```

---

# 10. Return Statement ⭐⭐⭐⭐⭐

One of the most important concepts is:

```javascript
return
```

Example:

```javascript
function add(a, b) {
    return a + b;
}
```

Now:

```javascript
let result = add(10, 20);

console.log(result);
```

Output:

```text
30
```

The function returns:

```text
30
```

---

# 11. `console.log()` vs `return`

This is extremely important.

Consider:

```javascript
function add(a, b) {
    console.log(a + b);
}
```

Calling:

```javascript
let result = add(10, 20);
```

The function prints:

```text
30
```

But:

```javascript
console.log(result);
```

gives:

```text
undefined
```

Why?

Because the function didn't return anything.

---

## Compare

### `console.log()`

```javascript
function add(a, b) {
    console.log(a + b);
}
```

Its purpose is to **display something**.

### `return`

```javascript
function add(a, b) {
    return a + b;
}
```

Its purpose is to **send a value back to the caller**.

---

# 12. Function Return Example

```javascript
function square(number) {
    return number * number;
}

let result = square(5);

console.log(result);
```

Output:

```text
25
```

Flow:

```text
square(5)
    ↓
number = 5
    ↓
5 * 5
    ↓
25
    ↓
return 25
    ↓
result = 25
```

---

# 13. `return` Stops the Function

Example:

```javascript
function test() {
    console.log("A");

    return;

    console.log("B");
}
```

Call:

```javascript
test();
```

Output:

```text
A
```

`"B"` is never printed.

Once JavaScript executes:

```javascript
return;
```

the function ends.

---

# 14. Returning Different Types

A function can return any JavaScript value.

### String

```javascript
function getName() {
    return "Sai";
}
```

### Number

```javascript
function getAge() {
    return 25;
}
```

### Boolean

```javascript
function isLoggedIn() {
    return true;
}
```

### Array

```javascript
function getNumbers() {
    return [10, 20, 30];
}
```

### Object

```javascript
function getUser() {
    return {
        name: "Sai",
        age: 25
    };
}
```

---

# 15. Function Without Parameters

```javascript
function sayHello() {
    return "Hello";
}

console.log(sayHello());
```

Output:

```text
Hello
```

---

# 16. Function With Parameters

```javascript
function sayHello(name) {
    return "Hello " + name;
}

console.log(sayHello("Sai"));
```

Output:

```text
Hello Sai
```

---

# 17. Default Parameters ⭐⭐⭐⭐

You can provide a default value for a parameter.

```javascript
function greet(name = "Guest") {
    console.log("Hello " + name);
}
```

If you provide a value:

```javascript
greet("Sai");
```

Output:

```text
Hello Sai
```

If you don't:

```javascript
greet();
```

Output:

```text
Hello Guest
```

---

# 18. Why Default Parameters Are Useful

Without a default:

```javascript
function greet(name) {
    console.log("Hello " + name);
}

greet();
```

Output:

```text
Hello undefined
```

With:

```javascript
function greet(name = "Guest") {
    console.log("Hello " + name);
}
```

we get:

```text
Hello Guest
```

---

# 19. Function Expression

A function can also be stored inside a variable.

```javascript
const greet = function () {
    console.log("Hello");
};
```

Then call:

```javascript
greet();
```

Output:

```text
Hello
```

This is called a **function expression**.

---

# 20. Function Declaration vs Function Expression

### Function Declaration

```javascript
function greet() {
    console.log("Hello");
}
```

### Function Expression

```javascript
const greet = function () {
    console.log("Hello");
};
```

Both create functions, but their behavior around hoisting is different.

We'll discuss hoisting in detail in the upcoming **Hoisting** topic.

---

# 21. Arrow Functions ⭐⭐⭐⭐⭐

Arrow functions are a modern and extremely important way of writing functions.

Normal function:

```javascript
function add(a, b) {
    return a + b;
}
```

Arrow function:

```javascript
const add = (a, b) => {
    return a + b;
};
```

Both can perform the same operation.

---

# 22. Arrow Function Syntax

Basic:

```javascript
const greet = () => {
    console.log("Hello");
};
```

With one parameter:

```javascript
const greet = (name) => {
    console.log("Hello " + name);
};
```

Multiple parameters:

```javascript
const add = (a, b) => {
    return a + b;
};
```

---

# 23. Arrow Function with One Parameter

You can omit parentheses around a single parameter.

Instead of:

```javascript
const square = (number) => {
    return number * number;
};
```

you can write:

```javascript
const square = number => {
    return number * number;
};
```

Both are valid.

For consistency, many teams still use parentheses:

```javascript
(number) => ...
```

---

# 24. Arrow Function Implicit Return ⭐⭐⭐⭐⭐

If the arrow function contains a single expression, you can return it without writing `return`.

Instead of:

```javascript
const add = (a, b) => {
    return a + b;
};
```

you can write:

```javascript
const add = (a, b) => a + b;
```

This is called an **implicit return**.

---

# 25. More Implicit Return Examples

```javascript
const square = number => number * number;
```

Then:

```javascript
console.log(square(5));
```

Output:

```text
25
```

Another:

```javascript
const greet = name => "Hello " + name;
```

Then:

```javascript
console.log(greet("Sai"));
```

Output:

```text
Hello Sai
```

---

# 26. Explicit vs Implicit Return

### Explicit return

```javascript
const add = (a, b) => {
    return a + b;
};
```

### Implicit return

```javascript
const add = (a, b) => a + b;
```

Both return the same result.

---

# 27. Arrow Functions and React ⭐⭐⭐⭐⭐

You will see arrow functions everywhere in React.

For example:

```jsx
const handleClick = () => {
    console.log("Button clicked");
};
```

Then:

```jsx
<button onClick={handleClick}>
    Click
</button>
```

Another example:

```jsx
const users = ["Sai", "Rahul", "John"];

const names = users.map((user) => user);
```

And:

```jsx
users.map(user => <p>{user}</p>)
```

Understanding arrow functions is essential for React.

---

# 28. Functions as Values

In JavaScript, functions are **first-class values**.

That means you can:

* store a function in a variable
* pass a function as an argument
* return a function from another function
* store functions inside objects/arrays

Example:

```javascript
const greet = function () {
    console.log("Hello");
};
```

The function is stored in:

```text
greet
```

You can then call:

```javascript
greet();
```

---

# 29. Passing a Function as an Argument

This is extremely important.

```javascript
function greet() {
    console.log("Hello");
}

function executeFunction(fn) {
    fn();
}

executeFunction(greet);
```

Output:

```text
Hello
```

Here:

```javascript
greet
```

is passed as an argument.

Inside:

```javascript
fn();
```

calls the function.

This concept leads directly to **callbacks**.

---

# 30. Callback Function Preview ⭐⭐⭐⭐⭐

A callback is simply a function passed to another function to be called later/by that function.

Example:

```javascript
function greet(name) {
    console.log("Hello " + name);
}

function processUser(callback) {
    callback("Sai");
}

processUser(greet);
```

Output:

```text
Hello Sai
```

Here:

```javascript
greet
```

is the callback function.

We'll study callbacks in much more detail later.

---

# 31. Function Returning a Function

Because functions are values, a function can return another function.

Example:

```javascript
function outer() {

    function inner() {
        console.log("Hello");
    }

    return inner;
}
```

Then:

```javascript
const result = outer();

result();
```

Output:

```text
Hello
```

This concept becomes very important when we study:

**Closures.**

---

# 32. Function Scope

Variables created inside a function generally belong to that function's scope.

Example:

```javascript
function test() {
    let message = "Hello";

    console.log(message);
}

test();
```

This works.

But:

```javascript
console.log(message);
```

outside the function doesn't work because `message` is local to the function.

This connects to the **Scope** topic we'll study later.

---

# 33. Local vs Global Variables

```javascript
let globalName = "Sai";

function test() {
    let localName = "Rahul";

    console.log(globalName);
    console.log(localName);
}
```

Inside the function, both can be accessed.

But outside:

```javascript
console.log(localName);
```

doesn't work.

The function's local variable isn't accessible outside its scope.

---

# 34. Rest Parameters in Functions ⭐⭐⭐⭐

Suppose you don't know how many arguments will be passed.

You can use:

```javascript
...
```

called the **rest parameter**.

Example:

```javascript
function add(...numbers) {
    console.log(numbers);
}

add(10, 20, 30, 40);
```

Output:

```text
[10, 20, 30, 40]
```

All arguments are collected into an array called:

```text
numbers
```

---

# 35. Rest Parameter Example

You can combine it with `reduce()`:

```javascript
function add(...numbers) {
    return numbers.reduce((total, number) => total + number, 0);
}

console.log(add(10, 20, 30));
```

Output:

```text
60
```

Don't worry if `reduce()` isn't fully clear yet. We'll cover it under arrays.

---

# 36. Arguments Object

Traditional functions have access to an `arguments` object.

Example:

```javascript
function test(a, b) {
    console.log(arguments);
}

test(10, 20);
```

It contains the arguments passed to the function.

However, modern JavaScript generally prefers **rest parameters**:

```javascript
function test(...args) {
    console.log(args);
}
```

because `args` is a real array.

---

# 37. Important Difference: `arguments` and Arrow Functions

Arrow functions do **not** have their own `arguments` object.

For example:

```javascript
const test = () => {
    console.log(arguments);
};
```

You shouldn't use `arguments` this way inside an arrow function.

Use:

```javascript
const test = (...args) => {
    console.log(args);
};
```

This distinction can appear in interviews.

---

# 38. Functions Can Have Objects as Parameters

Example:

```javascript
function greetUser(user) {
    console.log("Hello " + user.name);
}

const user = {
    name: "Sai",
    age: 25
};

greetUser(user);
```

Output:

```text
Hello Sai
```

This is very common in React.

---

# 39. React Components Are Functions

This is one of the most important connections.

A React functional component looks like:

```jsx
function Welcome() {
    return <h1>Hello</h1>;
}
```

This is a JavaScript function.

It returns JSX.

Another form:

```jsx
const Welcome = () => {
    return <h1>Hello</h1>;
};
```

So understanding JavaScript functions is essential before going deeper into React.

---

# 40. React Props Are Function Parameters

Suppose:

```jsx
function Welcome(props) {
    return <h1>Hello {props.name}</h1>;
}
```

Here:

```javascript
props
```

is effectively the function parameter.

You can also destructure it:

```jsx
function Welcome({ name }) {
    return <h1>Hello {name}</h1>;
}
```

This connects functions directly to the **Props** topic you already studied.

---

# 41. React Event Handlers Are Functions

Example:

```jsx
function App() {

    const handleClick = () => {
        console.log("Clicked");
    };

    return (
        <button onClick={handleClick}>
            Click Me
        </button>
    );
}
```

Here:

```javascript
handleClick
```

is a function.

React calls it when the button is clicked.

---

# 42. Important: Don't Call the Function Immediately

Correct:

```jsx
<button onClick={handleClick}>
    Click
</button>
```

Usually incorrect:

```jsx
<button onClick={handleClick()}>
    Click
</button>
```

Why?

```javascript
handleClick
```

means:

> Give React the function.

But:

```javascript
handleClick()
```

means:

> Execute the function immediately.

This distinction is extremely important in React.

---

# 43. Passing Arguments to React Event Handlers

Suppose:

```jsx
const handleClick = (name) => {
    console.log(name);
};
```

You shouldn't normally write:

```jsx
<button onClick={handleClick("Sai")}>
```

because it calls the function during rendering.

Instead:

```jsx
<button onClick={() => handleClick("Sai")}>
    Click
</button>
```

The arrow function waits until the click happens.

---

# 44. Pure Functions ⭐⭐⭐⭐⭐

A pure function is a function that:

1. Given the same input, always produces the same output.
2. Doesn't cause unwanted side effects.

Example:

```javascript
function add(a, b) {
    return a + b;
}
```

Every time:

```javascript
add(2, 3)
```

returns:

```text
5
```

---

# 45. Impure Function

Example:

```javascript
let count = 0;

function increment() {
    count++;
}
```

The function changes external state:

```javascript
count
```

Therefore it has a side effect.

This distinction becomes important in React, especially when thinking about state and rendering.

---

# 46. Function Declaration Hoisting

This is an important interview topic.

You can sometimes call a function declaration before it appears in the code:

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

This happens because function declarations are hoisted.

We'll study **hoisting** separately in detail.

---

# 47. Function Expression Hoisting Difference

Consider:

```javascript
greet();

const greet = function () {
    console.log("Hello");
};
```

This does **not** work like the function declaration example.

Similarly:

```javascript
greet();

const greet = () => {
    console.log("Hello");
};
```

doesn't allow you to call `greet` before its initialization.

This is an important distinction between:

```text
function declaration
```

and:

```text
function expression / arrow function assigned to const
```

---

# 48. `return` Without a Value

You can write:

```javascript
function test() {
    return;
}
```

The function returns:

```javascript
undefined
```

Example:

```javascript
const result = test();

console.log(result);
```

Output:

```text
undefined
```

---

# 49. A Function Can Have Multiple Returns

Example:

```javascript
function checkAge(age) {

    if (age >= 18) {
        return "Adult";
    }

    return "Minor";
}
```

If:

```javascript
checkAge(20);
```

returns:

```text
Adult
```

If:

```javascript
checkAge(15);
```

returns:

```text
Minor
```

Once a `return` executes, the function stops.

---

# 50. Functions Calling Other Functions

Functions can call other functions.

```javascript
function add(a, b) {
    return a + b;
}

function calculate() {
    const result = add(10, 20);

    console.log(result);
}

calculate();
```

Output:

```text
30
```

This is extremely common in real applications.

---

# 51. Function Naming Best Practices

Function names should generally describe what the function does.

Good:

```javascript
getUser()
calculateTotal()
validateForm()
handleClick()
fetchUsers()
```

Not ideal:

```javascript
abc()
test1()
x()
doStuff()
```

For React, you'll often see names such as:

```javascript
handleClick
handleSubmit
handleChange
fetchData
```

---

# 52. Normal Function vs Arrow Function

Here's the basic comparison:

| Feature         | Normal Function      | Arrow Function          |
| --------------- | -------------------- | ----------------------- |
| Syntax          | `function test() {}` | `const test = () => {}` |
| Parameters      | Yes                  | Yes                     |
| Return          | Yes                  | Yes                     |
| Implicit return | No                   | Yes                     |
| Own `this`      | Yes                  | No                      |
| Own `arguments` | Yes                  | No                      |
| Common in React | Yes                  | Very common             |

The `this` difference is **very important** and we'll study it in detail in the `this` topic.

---

# 53. The Most Important Arrow Function Difference: `this`

Normal function:

```javascript
function test() {
    console.log(this);
}
```

Arrow function:

```javascript
const test = () => {
    console.log(this);
};
```

Arrow functions don't create their own `this`; they use the surrounding lexical `this`.

Don't worry if this isn't completely clear yet.

When we reach:

**`this` Keyword ⭐⭐⭐⭐⭐**

we'll study this properly with examples.

---

# 54. Function Execution Flow

Consider:

```javascript
function add(a, b) {
    const result = a + b;
    return result;
}

const answer = add(10, 20);

console.log(answer);
```

Execution:

```text
add(10, 20)
     ↓
a = 10
b = 20
     ↓
result = 30
     ↓
return 30
     ↓
answer = 30
     ↓
console.log(answer)
     ↓
30
```

Understanding this flow will help later with:

* Call stack
* Execution context
* Closures
* Async JavaScript

---

# 55. Common Interview Questions

## Q1. What is a function?

A function is a reusable block of code designed to perform a particular task.

---

## Q2. What is the difference between parameter and argument?

```javascript
function add(a, b) {
}
```

`a` and `b` are parameters.

```javascript
add(10, 20);
```

`10` and `20` are arguments.

---

## Q3. What does `return` do?

`return` sends a value back to the caller and immediately terminates the function.

---

## Q4. Difference between `return` and `console.log()`?

```javascript
console.log()
```

displays a value.

```javascript
return
```

sends a value back from the function.

---

## Q5. What is a function declaration?

```javascript
function greet() {
    console.log("Hello");
}
```

---

## Q6. What is a function expression?

```javascript
const greet = function () {
    console.log("Hello");
};
```

---

## Q7. What is an arrow function?

An arrow function is a shorter function syntax introduced in modern JavaScript.

```javascript
const add = (a, b) => a + b;
```

---

## Q8. What is an implicit return?

When an arrow function returns a single expression without explicitly using `return`:

```javascript
const add = (a, b) => a + b;
```

---

## Q9. What is a callback?

A callback is a function passed to another function to be invoked by that function.

Example:

```javascript
function process(callback) {
    callback();
}
```

---

## Q10. Are functions first-class citizens in JavaScript?

Yes.

Functions can be:

```text
stored in variables
passed as arguments
returned from functions
stored in arrays
stored in objects
```

---

# 56. Interview Output Questions

### Question 1

```javascript
function add(a, b) {
    return a + b;
}

console.log(add(5, 10));
```

Output:

```text
15
```

---

### Question 2

```javascript
function test() {
    console.log("A");
    return;
    console.log("B");
}

test();
```

Output:

```text
A
```

---

### Question 3

```javascript
function greet(name = "Guest") {
    return "Hello " + name;
}

console.log(greet());
```

Output:

```text
Hello Guest
```

---

### Question 4

```javascript
const square = number => number * number;

console.log(square(4));
```

Output:

```text
16
```

---

### Question 5

```javascript
function test() {
    return 10;
}

const result = test();

console.log(result);
```

Output:

```text
10
```

---

### Question 6

What happens here?

```javascript
function test() {
    console.log("Hello");
}

const result = test();

console.log(result);
```

Output:

```text
Hello
undefined
```

Why?

Because the function doesn't explicitly return anything.

---

# 57. Practice Questions

Try these yourself.

### Q1

Create a function:

```text
add(a, b)
```

that returns the sum.

Expected:

```javascript
add(10, 20);
// 30
```

---

### Q2

Create:

```text
multiply(a, b)
```

Expected:

```javascript
multiply(5, 4);
// 20
```

---

### Q3

Create:

```text
isEven(number)
```

that returns:

```text
true
```

if the number is even and:

```text
false
```

otherwise.

---

### Q4

Create:

```text
getFullName(firstName, lastName)
```

Expected:

```javascript
getFullName("Sai", "Teja");
// "Sai Teja"
```

---

### Q5

Write the following using an arrow function:

```javascript
function square(number) {
    return number * number;
}
```

---

### Q6

What is the difference between:

```javascript
const greet = () => {
    console.log("Hello");
};
```

and:

```javascript
const greet = () => console.log("Hello");
```

---

### Q7

What is the difference between:

```javascript
function greet(name) {}
```

and:

```javascript
function greet() {}
```

---

### Q8

What will this return?

```javascript
function test() {
    console.log("Hello");
}

const result = test();

console.log(result);
```

---

### Q9

What is wrong with this React code?

```jsx
<button onClick={handleClick()}>
    Click
</button>
```

How should it normally be written?

---

### Q10 — Interview Level

Explain the difference between:

```javascript
function add(a, b) {
    return a + b;
}
```

and:

```javascript
const add = (a, b) => a + b;
```

---

# ⭐ Final Cheat Sheet

### Function declaration

```javascript
function greet() {
    console.log("Hello");
}
```

### Calling

```javascript
greet();
```

### Parameters

```javascript
function greet(name) {
    console.log(name);
}
```

### Arguments

```javascript
greet("Sai");
```

### Return

```javascript
function add(a, b) {
    return a + b;
}
```

### Function expression

```javascript
const greet = function () {
    console.log("Hello");
};
```

### Arrow function

```javascript
const greet = () => {
    console.log("Hello");
};
```

### Arrow function with parameters

```javascript
const add = (a, b) => {
    return a + b;
};
```

### Implicit return

```javascript
const add = (a, b) => a + b;
```

### Default parameter

```javascript
function greet(name = "Guest") {
    console.log(name);
}
```

### Rest parameter

```javascript
function add(...numbers) {
    // numbers is an array
}
```

### Callback

```javascript
function execute(callback) {
    callback();
}
```

---

# ⭐ What You Must Master for React

For your React interview preparation, make sure you are very comfortable with:

```text
1. Function declarations
2. Function expressions
3. Arrow functions ⭐⭐⭐⭐⭐
4. Parameters and arguments ⭐⭐⭐⭐⭐
5. return ⭐⭐⭐⭐⭐
6. Default parameters
7. Rest parameters
8. Callback functions ⭐⭐⭐⭐⭐
9. Functions as first-class values
10. Function scope
11. Pure vs impure functions
12. `this` in normal vs arrow functions ⭐⭐⭐⭐⭐
13. Functions as React components ⭐⭐⭐⭐⭐
14. Functions as event handlers ⭐⭐⭐⭐⭐
15. Functions passed as props ⭐⭐⭐⭐⭐
```

The most important mental model is:

```text
FUNCTION
   ↓
Receive input
   ↓
Process input
   ↓
Return output
```

For example:

```javascript
function add(a, b) {
    return a + b;
}
```

```text
10 ──┐
     ├──> add() ──> 30
20 ──┘
```

And remember this React connection:

```jsx
const handleClick = () => {
    console.log("Clicked");
};
```

Here `handleClick` is a JavaScript function.

```jsx
<button onClick={handleClick}>
    Click
</button>
```

React receives that function and calls it when the event occurs.