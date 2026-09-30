# 15. Callbacks ⭐⭐⭐⭐⭐

Callbacks are **extremely important for JavaScript and React interviews**.

If you understand callbacks well, the next topics—**Higher-Order Functions, Asynchronous JavaScript, Promises, async/await, Event Loop, and React event handling**—become much easier.

---

# 1. What is a Callback?

A **callback is a function passed as an argument to another function, which is then called later by that function.**

In simple words:

> **Function passed into another function = Callback**

### Basic example

```javascript
function greet() {
    console.log("Hello");
}

function executeFunction(callback) {
    callback();
}

executeFunction(greet);
```

### Output

```text
Hello
```

Let's understand what happened:

```javascript
function greet() {
    console.log("Hello");
}
```

We created a function called `greet`.

Then:

```javascript
function executeFunction(callback) {
    callback();
}
```

`executeFunction()` accepts a function as a parameter.

Here:

```javascript
callback
```

is just a parameter name.

When we do:

```javascript
executeFunction(greet);
```

we are passing the `greet` function into `executeFunction`.

So internally:

```javascript
callback = greet
```

Then:

```javascript
callback();
```

actually executes:

```javascript
greet();
```

---

# 2. Why Are Callbacks Possible?

Because in JavaScript, **functions are first-class values**.

That means a function can be:

* stored in a variable
* passed as an argument
* returned from another function
* stored inside an object or array

For example:

```javascript
function greet() {
    console.log("Hello");
}

const myFunction = greet;

myFunction();
```

Output:

```text
Hello
```

Notice:

```javascript
const myFunction = greet;
```

We are not executing `greet`.

We are storing a reference to the function.

### Important

```javascript
greet
```

means:

> Give me the function.

Whereas:

```javascript
greet()
```

means:

> Execute the function.

This distinction is **very important in React**.

---

# 3. Callback Syntax

A common pattern is:

```javascript
function mainFunction(callback) {
    callback();
}

function myCallback() {
    console.log("Callback executed");
}

mainFunction(myCallback);
```

Think of it like:

```text
mainFunction()
     |
     ↓
receives myCallback
     |
     ↓
callback()
     |
     ↓
myCallback()
```

---

# 4. Callback Using an Arrow Function

You don't always have to create a separate function.

You can directly pass an arrow function.

```javascript
function execute(callback) {
    callback();
}

execute(() => {
    console.log("Hello");
});
```

Output:

```text
Hello
```

This is extremely common in modern JavaScript.

---

# 5. Callback with Parameters

A callback can receive values.

```javascript
function calculate(a, b, callback) {
    const result = a + b;
    callback(result);
}

function display(result) {
    console.log(result);
}

calculate(10, 20, display);
```

Output:

```text
30
```

### Flow

```text
calculate(10, 20, display)
            ↓
        10 + 20
            ↓
          30
            ↓
      display(30)
            ↓
          30
```

---

# 6. Callback with an Arrow Function

The same example can be written more simply:

```javascript
function calculate(a, b, callback) {
    const result = a + b;
    callback(result);
}

calculate(10, 20, (result) => {
    console.log(result);
});
```

Output:

```text
30
```

Or even shorter:

```javascript
calculate(10, 20, result => console.log(result));
```

---

# 7. Very Important: `function` vs `function()`

Consider:

```javascript
function greet() {
    console.log("Hello");
}

execute(greet);
```

This passes the function.

But:

```javascript
execute(greet());
```

does something different.

Here:

```javascript
greet()
```

executes immediately.

For example:

```javascript
function greet() {
    console.log("Hello");
    return 100;
}

function execute(callback) {
    console.log(callback);
}

execute(greet);
```

Output:

```text
[Function: greet]
```

But:

```javascript
execute(greet());
```

First executes:

```javascript
greet();
```

Output:

```text
Hello
```

Then its return value:

```text
100
```

is passed to `execute()`.

So:

### Passing function

```javascript
execute(greet);
```

### Executing function immediately

```javascript
execute(greet());
```

This is one of the most common callback interview questions.

---

# 8. Synchronous Callbacks ⭐⭐⭐⭐⭐

A callback doesn't automatically mean asynchronous.

Callbacks can be **synchronous** or **asynchronous**.

Example:

```javascript
function process(callback) {
    console.log("Start");
    
    callback();
    
    console.log("End");
}

process(() => {
    console.log("Callback");
});
```

Output:

```text
Start
Callback
End
```

The callback executes immediately before `process()` finishes.

This is a **synchronous callback**.

---

# 9. Array Methods Use Callbacks ⭐⭐⭐⭐⭐

This is where callbacks become extremely important.

You have already learned:

* `map()`
* `filter()`
* `forEach()`
* `find()`
* `some()`
* `every()`
* `reduce()`

These methods commonly receive callbacks.

---

# 10. Callback with `forEach()`

```javascript
const numbers = [10, 20, 30];

numbers.forEach(function(number) {
    console.log(number);
});
```

Output:

```text
10
20
30
```

Here:

```javascript
function(number) {
    console.log(number);
}
```

is the callback.

You can write:

```javascript
numbers.forEach((number) => {
    console.log(number);
});
```

---

# 11. How `forEach()` Works

Conceptually, JavaScript does something similar to:

```javascript
for each item:
    callback(item);
```

For:

```javascript
const numbers = [10, 20, 30];
```

the callback is effectively called like:

```javascript
callback(10);
callback(20);
callback(30);
```

---

# 12. `map()` Uses a Callback ⭐⭐⭐⭐⭐

```javascript
const numbers = [1, 2, 3, 4];

const result = numbers.map((number) => {
    return number * 2;
});

console.log(result);
```

Output:

```text
[2, 4, 6, 8]
```

The callback:

```javascript
(number) => {
    return number * 2;
}
```

runs once for each element.

Conceptually:

```text
1 → callback(1) → 2
2 → callback(2) → 4
3 → callback(3) → 6
4 → callback(4) → 8
```

---

# 13. `filter()` Uses a Callback

```javascript
const numbers = [10, 15, 20, 25];

const result = numbers.filter((number) => {
    return number > 15;
});

console.log(result);
```

Output:

```text
[20, 25]
```

The callback must return a condition:

```javascript
number > 15
```

If `true`, the element is kept.

If `false`, it is removed.

---

# 14. `find()` Uses a Callback

```javascript
const numbers = [10, 20, 30, 40];

const result = numbers.find((number) => {
    return number > 20;
});

console.log(result);
```

Output:

```text
30
```

`find()` returns the **first matching element**.

---

# 15. `some()` Uses a Callback

```javascript
const numbers = [1, 3, 5, 8];

const result = numbers.some((number) => {
    return number % 2 === 0;
});

console.log(result);
```

Output:

```text
true
```

Because `8` is even.

---

# 16. `every()` Uses a Callback

```javascript
const numbers = [2, 4, 6, 8];

const result = numbers.every((number) => {
    return number % 2 === 0;
});

console.log(result);
```

Output:

```text
true
```

Every number is even.

---

# 17. `reduce()` Uses a Callback ⭐⭐⭐⭐⭐

`reduce()` is also based on a callback.

```javascript
const numbers = [10, 20, 30];

const total = numbers.reduce((sum, number) => {
    return sum + number;
}, 0);

console.log(total);
```

Output:

```text
60
```

The callback receives values such as:

```text
sum
number
```

Conceptually:

```text
0 + 10 = 10
10 + 20 = 30
30 + 30 = 60
```

---

# 18. Callback Parameters in Array Methods

Callbacks can receive more than one parameter.

For example:

```javascript
const fruits = ["Apple", "Banana", "Mango"];

fruits.forEach((fruit, index, array) => {
    console.log(fruit);
    console.log(index);
});
```

The callback can receive:

```javascript
(element, index, array)
```

Example:

```text
Apple 0
Banana 1
Mango 2
```

Not every method uses every parameter, but these are common.

---

# 19. Callback with `setTimeout()` ⭐⭐⭐⭐⭐

Now callbacks become especially important for **asynchronous JavaScript**.

```javascript
console.log("Start");

setTimeout(() => {
    console.log("Hello");
}, 2000);

console.log("End");
```

Output:

```text
Start
End
Hello
```

Why?

The function:

```javascript
() => {
    console.log("Hello");
}
```

is passed as a callback to:

```javascript
setTimeout()
```

It runs later.

So:

```javascript
setTimeout(callback, 2000);
```

means approximately:

> Run this callback after the timer is ready.

We'll study exactly **why this happens** when we cover:

**Asynchronous JavaScript → Event Loop → Call Stack → Web APIs → Callback Queue**

---

# 20. Callback with Events

Browser events also use callbacks.

Example:

```javascript
button.addEventListener("click", function() {
    console.log("Button clicked");
});
```

The function:

```javascript
function() {
    console.log("Button clicked");
}
```

is a callback.

The browser calls it when the button is clicked.

---

# 21. React Uses Callbacks Everywhere ⭐⭐⭐⭐⭐

Callbacks are extremely important in React.

For example:

```jsx
function App() {

    function handleClick() {
        console.log("Button clicked");
    }

    return (
        <button onClick={handleClick}>
            Click Me
        </button>
    );
}
```

Here:

```jsx
onClick={handleClick}
```

passes the function as a callback/event handler.

React calls it when the user clicks the button.

---

# 22. Don't Write `handleClick()`

This is a very important React interview concept.

### Correct

```jsx
<button onClick={handleClick}>
    Click
</button>
```

### Usually wrong

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

Whereas:

```javascript
handleClick()
```

means:

> Execute the function now.

---

# 23. Passing Arguments in React

Suppose:

```jsx
function handleClick(name) {
    console.log(name);
}
```

You cannot normally do:

```jsx
<button onClick={handleClick("Sai")}>
    Click
</button>
```

because it executes during rendering.

Instead:

```jsx
<button onClick={() => handleClick("Sai")}>
    Click
</button>
```

Now:

```javascript
() => handleClick("Sai")
```

is the callback.

React executes that callback when the button is clicked.

---

# 24. Callback with API Data

A simplified example:

```javascript
function getUser(callback) {

    const user = {
        name: "Sai",
        age: 22
    };

    callback(user);
}

getUser((user) => {
    console.log(user.name);
});
```

Output:

```text
Sai
```

The callback receives the result.

This pattern was historically very common for asynchronous operations.

Modern JavaScript generally uses:

```text
Callbacks
   ↓
Promises
   ↓
async/await
```

for many asynchronous workflows.

---

# 25. Callback Hell ⭐⭐⭐⭐

When callbacks are deeply nested, code can become difficult to read.

Example:

```javascript
getUser(function(user) {

    getOrders(user, function(orders) {

        getPayment(orders, function(payment) {

            sendEmail(payment, function(result) {

                console.log(result);

            });

        });

    });

});
```

This shape is often called:

> **Callback Hell**

or

> **Pyramid of Doom**

The problem isn't that callbacks are bad.

The problem is **too many nested callbacks**, especially for asynchronous operations.

Promises and `async/await` were introduced to make these flows easier to manage.

---

# 26. Callback Hell Example

Imagine:

```text
Get User
   ↓
Get Orders
   ↓
Get Payment
   ↓
Send Email
   ↓
Finish
```

With deeply nested callbacks:

```javascript
getUser(function(user) {
    getOrders(user, function(orders) {
        getPayment(orders, function(payment) {
            sendEmail(payment, function() {
                console.log("Done");
            });
        });
    });
});
```

Later we'll rewrite this using:

```javascript
Promises
```

and:

```javascript
async/await
```

which makes the flow much easier to read.

---

# 27. Callback vs Function

A callback is **not a special type of function**.

A callback is simply a function that is:

> passed to another function to be called by it.

For example:

```javascript
function greet() {
    console.log("Hello");
}
```

By itself, `greet` is simply a function.

But:

```javascript
execute(greet);
```

makes `greet` a callback in that context.

---

# 28. Callback vs Higher-Order Function

These two concepts are related.

### Callback

A function passed to another function:

```javascript
numbers.map(callback);
```

Here `callback` is the callback.

### Higher-Order Function

A function that:

* accepts a function, or
* returns a function, or
* does both.

For example:

```javascript
function execute(callback) {
    callback();
}
```

`execute()` is a **higher-order function** because it accepts a function.

So:

```text
Callback
    ↓
Function passed to another function

Higher-Order Function
    ↓
Function that accepts/returns another function
```

We'll cover Higher-Order Functions next.

---

# 29. Callback with `map()` — React Example ⭐⭐⭐⭐⭐

Suppose we have:

```javascript
const users = [
    { id: 1, name: "Sai" },
    { id: 2, name: "Rahul" },
    { id: 3, name: "Anu" }
];
```

In React:

```jsx
function App() {

    return (
        <div>
            {users.map((user) => (
                <p key={user.id}>
                    {user.name}
                </p>
            ))}
        </div>
    );
}
```

Here:

```javascript
(user) => (...)
```

is a callback passed to:

```javascript
map()
```

This is one of the most common callback patterns you'll see in React.

---

# 30. Callback with `filter()` — React Example

Suppose:

```javascript
const users = [
    { name: "Sai", age: 22 },
    { name: "Rahul", age: 17 },
    { name: "Anu", age: 25 }
];
```

We can filter:

```javascript
const adults = users.filter((user) => {
    return user.age >= 18;
});
```

Result:

```javascript
[
    { name: "Sai", age: 22 },
    { name: "Anu", age: 25 }
]
```

The callback:

```javascript
(user) => user.age >= 18
```

determines whether each user should remain.

---

# 31. Callback Return Values

A callback can return a value.

Example:

```javascript
function calculate(a, b, callback) {
    const result = callback(a, b);
    console.log(result);
}

calculate(10, 5, (a, b) => {
    return a + b;
});
```

Output:

```text
15
```

Another example:

```javascript
calculate(10, 5, (a, b) => {
    return a * b;
});
```

Output:

```text
50
```

The callback determines the operation.

---

# 32. A Callback Can Be Reused

```javascript
function double(number) {
    return number * 2;
}

function triple(number) {
    return number * 3;
}

function process(number, callback) {
    return callback(number);
}

console.log(process(5, double));
console.log(process(5, triple));
```

Output:

```text
10
15
```

This makes functions flexible.

---

# 33. Callback Pattern — Real-World Example

Imagine a function:

```javascript
function loginUser(username, callback) {

    console.log("Logging in...");

    const user = {
        username: username,
        loggedIn: true
    };

    callback(user);
}
```

Then:

```javascript
loginUser("Sai", (user) => {
    console.log("Welcome", user.username);
});
```

Output:

```text
Logging in...
Welcome Sai
```

The callback receives the result of the operation.

---

# 34. Important Callback Mental Model

Remember this:

```javascript
function A(callback) {
    callback();
}

function B() {
    console.log("Hello");
}

A(B);
```

Think:

```text
B
↓
passed into A
↓
A receives B as callback
↓
A calls callback()
↓
B()
↓
Hello
```

---

# 35. Common Callback Mistakes

### Mistake 1: Calling instead of passing

❌

```javascript
setTimeout(greet(), 1000);
```

Usually incorrect.

✅

```javascript
setTimeout(greet, 1000);
```

---

### Mistake 2: Forgetting to call the callback

```javascript
function execute(callback) {
    console.log("Hello");
}
```

The callback isn't executed.

Correct:

```javascript
function execute(callback) {
    console.log("Hello");
    callback();
}
```

---

### Mistake 3: Forgetting `return` in `map()`

❌

```javascript
const numbers = [1, 2, 3];

const result = numbers.map((number) => {
    number * 2;
});

console.log(result);
```

Output:

```text
[undefined, undefined, undefined]
```

Because the callback doesn't return anything.

Correct:

```javascript
const result = numbers.map((number) => {
    return number * 2;
});
```

Or:

```javascript
const result = numbers.map(number => number * 2);
```

---

### Mistake 4: Confusing callback with asynchronous

A callback does **not necessarily mean asynchronous**.

This is synchronous:

```javascript
[1, 2, 3].map(number => number * 2);
```

This is asynchronous:

```javascript
setTimeout(() => {
    console.log("Hello");
}, 1000);
```

Both use callbacks.

---

# 36. Callback vs Promise vs async/await

You'll learn these in upcoming topics.

| Concept       | Main idea                             |
| ------------- | ------------------------------------- |
| Callback      | Pass a function to another function   |
| Promise       | Represents future completion/failure  |
| `async/await` | Cleaner syntax for Promise-based code |

Typical progression:

```text
Callback
   ↓
Callback-based async code
   ↓
Callback Hell
   ↓
Promises
   ↓
async/await
```

---

# 37. Interview Question ⭐⭐⭐⭐⭐

### Q1. What is a callback function?

**Answer:**

A callback is a function passed as an argument to another function and invoked by that function.

Example:

```javascript
function execute(callback) {
    callback();
}

execute(() => {
    console.log("Hello");
});
```

---

### Q2. Are callbacks always asynchronous?

**Answer:**

No.

Callbacks can be synchronous or asynchronous.

Synchronous:

```javascript
numbers.map(callback);
```

Asynchronous:

```javascript
setTimeout(callback, 1000);
```

---

### Q3. Why are callbacks used?

Callbacks allow us to:

* customize behavior
* pass functions as values
* execute code after an operation
* handle events
* process array elements
* handle asynchronous operations

---

### Q4. What is the difference between `fn` and `fn()`?

```javascript
fn
```

references the function.

```javascript
fn()
```

calls/executes the function.

This distinction is especially important in React event handlers.

---

### Q5. Which array methods use callbacks?

Common examples:

```text
map()
filter()
forEach()
find()
findIndex()
some()
every()
reduce()
sort()
```

---

### Q6. What is callback hell?

Callback hell occurs when many callbacks become deeply nested, making asynchronous code difficult to read and maintain.

---

### Q7. Can a callback accept parameters?

Yes.

```javascript
function process(callback) {
    callback("Hello");
}

process((message) => {
    console.log(message);
});
```

Output:

```text
Hello
```

---

# 38. Output-Based Interview Questions ⭐⭐⭐⭐⭐

### Question 1

```javascript
function test(callback) {
    console.log("A");
    callback();
    console.log("B");
}

test(() => {
    console.log("C");
});
```

Output:

```text
A
C
B
```

---

### Question 2

```javascript
function greet() {
    console.log("Hello");
}

function execute(callback) {
    console.log("Start");
    callback();
    console.log("End");
}

execute(greet);
```

Output:

```text
Start
Hello
End
```

---

### Question 3

```javascript
function greet() {
    console.log("Hello");
}

function execute(callback) {
    console.log(callback);
}

execute(greet);
```

The callback is passed as a function reference.

It does **not** execute `greet()`.

---

### Question 4

```javascript
const numbers = [1, 2, 3];

const result = numbers.map((number) => {
    return number * 10;
});

console.log(result);
```

Output:

```text
[10, 20, 30]
```

---

### Question 5

```javascript
console.log("A");

setTimeout(() => {
    console.log("B");
}, 0);

console.log("C");
```

Output:

```text
A
C
B
```

This one is important because it introduces the **Event Loop**.

We'll study exactly why `B` comes last in the asynchronous JavaScript/Event Loop topics.

---

# 39. Callback Cheat Sheet ⭐⭐⭐⭐⭐

```text
CALLBACK
    ↓
A function passed to another function
    ↓
The receiving function calls it
```

### Basic

```javascript
function execute(callback) {
    callback();
}

execute(() => {
    console.log("Hello");
});
```

### Array callbacks

```javascript
map()
filter()
forEach()
find()
some()
every()
reduce()
```

### Async callback

```javascript
setTimeout(() => {
    console.log("Hello");
}, 1000);
```

### React callback

```jsx
<button onClick={handleClick}>
    Click
</button>
```

### React argument

```jsx
<button onClick={() => handleClick("Sai")}>
    Click
</button>
```

### Remember

```text
fn     → reference/pass function
fn()   → execute function
```

---

# 40. What You Must Know for React Interviews

For callbacks, make sure you can confidently explain:

* ✅ What is a callback?
* ✅ Why are functions first-class values?
* ✅ Passing a function as an argument
* ✅ Calling a callback
* ✅ Callback parameters
* ✅ Callback return values
* ✅ Synchronous callbacks
* ✅ Asynchronous callbacks
* ✅ `map()` callback
* ✅ `filter()` callback
* ✅ `forEach()` callback
* ✅ `find()` callback
* ✅ `reduce()` callback
* ✅ `setTimeout()` callback
* ✅ Event callbacks
* ✅ React event handlers
* ✅ `onClick={handleClick}`
* ✅ `onClick={() => handleClick("Sai")}`
* ✅ `handleClick` vs `handleClick()`
* ✅ Callback hell
* ✅ Callback vs Higher-Order Function
* ✅ Callback vs Promise

---

# 41. Practice Problems

Try these yourself before looking at the answers.

### Practice 1

Create a function:

```javascript
function processNumber(number, callback) {

}
```

Call it so that it prints:

```text
20
```

when the number is `10` and the callback doubles it.

---

### Practice 2

Use `map()` to convert:

```javascript
[1, 2, 3, 4, 5]
```

into:

```javascript
[2, 4, 6, 8, 10]
```

---

### Practice 3

Use `filter()` to get numbers greater than `10`:

```javascript
[5, 12, 8, 20, 15]
```

Expected:

```javascript
[12, 20, 15]
```

---

### Practice 4

Create a function:

```javascript
calculate(a, b, callback)
```

Use callbacks to perform:

```text
addition
subtraction
multiplication
```

---

### Practice 5 — React

Create a button that calls:

```javascript
handleClick("Sai")
```

only when the button is clicked.

---

## ⭐ Final Mental Model

If you remember only one thing from this topic:

```text
Function
   ↓
passed to another function
   ↓
receiving function
   ↓
calls it
   ↓
Callback
```

And remember the most important interview distinction:

```javascript
handleClick
```

➡️ pass the function

```javascript
handleClick()
```

➡️ execute the function

That single distinction is extremely important in **JavaScript and React**.