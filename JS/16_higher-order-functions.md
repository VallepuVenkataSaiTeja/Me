# 16. Higher-Order Functions ⭐⭐⭐⭐

Higher-Order Functions (**HOFs**) are an important JavaScript interview topic and are especially useful in **React**, because methods like `map()`, `filter()`, and `reduce()` are based on this concept.

The good news is: **you already know most of the pieces**. You learned functions and callbacks first. Now we're connecting them.

---

# 1. What is a Higher-Order Function?

A **Higher-Order Function** is a function that does at least one of these:

1. **Accepts another function as an argument**
2. **Returns another function**

Or it can do both.

### Simple definition

> A Higher-Order Function is a function that works with other functions.

---

# 2. First Example

```javascript
function greet() {
    console.log("Hello");
}

function execute(callback) {
    callback();
}

execute(greet);
```

Here:

```javascript
execute(greet);
```

`greet` is being passed into `execute()`.

Therefore:

```javascript
execute()
```

is a **Higher-Order Function**.

And:

```javascript
greet
```

is the **callback function**.

### Remember

```text
Higher-Order Function
        ↓
receives another function

Callback
        ↓
function being passed
```

---

# 3. Callback vs Higher-Order Function ⭐⭐⭐⭐⭐

This is a very common interview question.

Consider:

```javascript
function process(callback) {
    callback();
}

function greet() {
    console.log("Hello");
}

process(greet);
```

### `process`

is the:

> Higher-Order Function

because it accepts a function.

### `greet`

is the:

> Callback Function

because it is passed into `process()`.

So:

```text
process → Higher-Order Function
greet   → Callback
```

---

# 4. HOF Can Return a Function

A function doesn't necessarily have to **accept** a function.

It can also **return** a function.

Example:

```javascript
function createGreeting() {

    return function() {
        console.log("Hello");
    };
}

const greet = createGreeting();

greet();
```

Output:

```text
Hello
```

Here:

```javascript
createGreeting()
```

returns a function.

Therefore:

```javascript
createGreeting
```

is a Higher-Order Function.

---

# 5. Arrow Function Version

The same thing can be written:

```javascript
const createGreeting = () => {
    return () => {
        console.log("Hello");
    };
};

const greet = createGreeting();

greet();
```

Output:

```text
Hello
```

---

# 6. HOF Can Accept AND Return a Function

A function can do both.

```javascript
function createMultiplier(number) {

    return function(value) {
        return value * number;
    };
}

const double = createMultiplier(2);

console.log(double(5));
```

Output:

```text
10
```

Let's understand it carefully.

First:

```javascript
createMultiplier(2);
```

returns:

```javascript
function(value) {
    return value * 2;
}
```

That returned function is stored in:

```javascript
double
```

Then:

```javascript
double(5);
```

becomes:

```javascript
5 * 2
```

Result:

```text
10
```

---

# 7. Real-World HOF Example

Imagine we want different types of calculations.

```javascript
function calculate(a, b, operation) {
    return operation(a, b);
}
```

Now we can pass different functions.

### Addition

```javascript
function add(a, b) {
    return a + b;
}

console.log(calculate(10, 5, add));
```

Output:

```text
15
```

### Multiplication

```javascript
function multiply(a, b) {
    return a * b;
}

console.log(calculate(10, 5, multiply));
```

Output:

```text
50
```

The same `calculate()` function works with different behaviors.

That's one of the major benefits of Higher-Order Functions.

---

# 8. Why Do We Use Higher-Order Functions?

HOFs help us:

* reuse code
* avoid repetitive code
* separate logic
* make functions flexible
* create reusable utilities
* write cleaner functional-style JavaScript
* process arrays easily
* create abstractions

---

# 9. Array Methods Are Higher-Order Functions ⭐⭐⭐⭐⭐

This is extremely important.

You have already used:

```javascript
map()
filter()
forEach()
find()
some()
every()
reduce()
sort()
```

Many of these are Higher-Order Functions because they accept callback functions.

---

# 10. `map()` as a Higher-Order Function

Example:

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

Here:

```javascript
(number) => {
    return number * 2;
}
```

is the callback.

And:

```javascript
map()
```

is a Higher-Order Function because it accepts a function.

---

# 11. `filter()` as a Higher-Order Function

```javascript
const numbers = [5, 10, 15, 20];

const result = numbers.filter((number) => {
    return number > 10;
});

console.log(result);
```

Output:

```text
[15, 20]
```

Again:

```javascript
filter()
```

accepts a callback.

Therefore it is a Higher-Order Function.

---

# 12. `forEach()` as a Higher-Order Function

```javascript
const names = ["Sai", "Rahul", "Anu"];

names.forEach((name) => {
    console.log(name);
});
```

Output:

```text
Sai
Rahul
Anu
```

The callback:

```javascript
(name) => {
    console.log(name);
}
```

is passed to `forEach()`.

---

# 13. `find()` as a Higher-Order Function

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

`find()` receives a callback, so it is a Higher-Order Function.

---

# 14. `some()` and `every()`

### `some()`

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

At least one number is even.

---

### `every()`

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

Both accept callbacks.

---

# 15. `reduce()` as a Higher-Order Function ⭐⭐⭐⭐⭐

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

`reduce()` receives this function:

```javascript
(sum, number) => {
    return sum + number;
}
```

Therefore it is a Higher-Order Function.

---

# 16. `sort()` Can Also Accept a Function

This is another useful example.

```javascript
const numbers = [40, 10, 30, 20];

numbers.sort((a, b) => {
    return a - b;
});

console.log(numbers);
```

Output:

```text
[10, 20, 30, 40]
```

The function:

```javascript
(a, b) => a - b
```

is passed to `sort()`.

So `sort()` can also operate as a Higher-Order Function.

---

# 17. HOF Returning a Function ⭐⭐⭐⭐⭐

This pattern is particularly important.

```javascript
function multiplier(x) {

    return function(y) {
        return x * y;
    };
}
```

Now:

```javascript
const double = multiplier(2);
```

`double` becomes approximately:

```javascript
function(y) {
    return 2 * y;
}
```

Therefore:

```javascript
console.log(double(10));
```

Output:

```text
20
```

And:

```javascript
const triple = multiplier(3);

console.log(triple(10));
```

Output:

```text
30
```

One function created multiple specialized functions.

---

# 18. Why Does `double()` Remember `2`?

This is where **closures** come in.

```javascript
function multiplier(x) {

    return function(y) {
        return x * y;
    };
}
```

When:

```javascript
const double = multiplier(2);
```

the returned function remembers:

```javascript
x = 2
```

Even after `multiplier()` has finished.

This is a **closure**.

You'll study closures later in much more detail.

For now remember:

```text
Higher-Order Function
        ↓
returns a function
        ↓
returned function remembers outer variables
        ↓
Closure
```

---

# 19. HOF + Closure Example

```javascript
function createCounter() {

    let count = 0;

    return function() {
        count++;
        return count;
    };
}

const counter = createCounter();

console.log(counter());
console.log(counter());
console.log(counter());
```

Output:

```text
1
2
3
```

Why does `count` remain available?

Because the returned function forms a **closure** over `count`.

This is a very important connection:

```text
Functions
   ↓
Callbacks
   ↓
Higher-Order Functions
   ↓
Closures
```

These concepts build on each other.

---

# 20. Custom Higher-Order Function

You don't need to use built-in methods.

You can create your own HOF.

```javascript
function processNumbers(numbers, callback) {

    const result = [];

    for (const number of numbers) {
        result.push(callback(number));
    }

    return result;
}
```

Now:

```javascript
const numbers = [1, 2, 3, 4];

const result = processNumbers(numbers, (number) => {
    return number * 2;
});

console.log(result);
```

Output:

```text
[2, 4, 6, 8]
```

We've basically created our own simplified version of `map()`.

---

# 21. Another Custom HOF

```javascript
function process(number, callback) {
    return callback(number);
}
```

Then:

```javascript
const result = process(10, (number) => {
    return number * 5;
});

console.log(result);
```

Output:

```text
50
```

Change the callback:

```javascript
const result = process(10, (number) => {
    return number + 5;
});
```

Output:

```text
15
```

The HOF doesn't need to know what operation will happen.

The callback supplies the behavior.

---

# 22. This Is the Main Benefit

Without HOF:

```javascript
function double(number) {
    return number * 2;
}

function triple(number) {
    return number * 3;
}

function square(number) {
    return number * number;
}
```

We may have many separate functions.

With a HOF:

```javascript
function process(number, operation) {
    return operation(number);
}
```

Then:

```javascript
process(5, number => number * 2);
process(5, number => number * 3);
process(5, number => number * number);
```

The same HOF can support many operations.

---

# 23. HOF in React ⭐⭐⭐⭐⭐

Higher-Order Functions are very common in React development.

For example:

```jsx
const users = [
    { id: 1, name: "Sai" },
    { id: 2, name: "Rahul" },
    { id: 3, name: "Anu" }
];
```

We can render:

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

`map()` is a Higher-Order Function.

The callback:

```javascript
(user) => (...)
```

determines what should be produced for each user.

---

# 24. React `filter()` Example

```jsx
function App() {

    const users = [
        { id: 1, name: "Sai", active: true },
        { id: 2, name: "Rahul", active: false },
        { id: 3, name: "Anu", active: true }
    ];

    const activeUsers = users.filter((user) => {
        return user.active;
    });

    return (
        <div>
            {activeUsers.map((user) => (
                <p key={user.id}>
                    {user.name}
                </p>
            ))}
        </div>
    );
}
```

Here we're using two HOFs:

```text
filter()
   ↓
keep active users

map()
   ↓
convert users into JSX
```

This pattern appears constantly in React applications.

---

# 25. Chaining Higher-Order Functions ⭐⭐⭐⭐⭐

You can combine them.

```javascript
const numbers = [1, 2, 3, 4, 5, 6];

const result = numbers
    .filter(number => number % 2 === 0)
    .map(number => number * 10);

console.log(result);
```

Output:

```text
[20, 40, 60]
```

Let's break it down.

First:

```javascript
filter(number => number % 2 === 0)
```

gives:

```text
[2, 4, 6]
```

Then:

```javascript
map(number => number * 10)
```

gives:

```text
[20, 40, 60]
```

---

# 26. HOFs and Functional Programming

Higher-Order Functions are one of the important ideas behind **functional programming**.

Functional programming commonly emphasizes:

* functions as values
* pure functions
* immutability
* composition
* Higher-Order Functions
* avoiding unnecessary mutation

You don't need to become a functional programming expert for React interviews, but understanding these concepts is valuable.

---

# 27. Function Composition

HOFs can help create function composition.

Suppose:

```javascript
const double = number => number * 2;

const addTen = number => number + 10;
```

We could create:

```javascript
function compose(first, second) {
    return function(value) {
        return second(first(value));
    };
}
```

Then:

```javascript
const result = compose(double, addTen);

console.log(result(5));
```

Flow:

```text
5
↓
double(5)
↓
10
↓
addTen(10)
↓
20
```

Output:

```text
20
```

This is a more advanced use of Higher-Order Functions.

For beginner React interviews, understand the concept rather than memorizing complex composition utilities.

---

# 28. HOF vs Normal Function

### Normal function

```javascript
function add(a, b) {
    return a + b;
}
```

It doesn't accept or return a function.

### Higher-Order Function

```javascript
function execute(callback) {
    return callback();
}
```

It accepts a function.

Or:

```javascript
function createFunction() {
    return function() {
        console.log("Hello");
    };
}
```

It returns a function.

---

# 29. Important Interview Question

### Is every function a Higher-Order Function?

**No.**

Example:

```javascript
function add(a, b) {
    return a + b;
}
```

This is a normal function.

But:

```javascript
function execute(callback) {
    callback();
}
```

is a Higher-Order Function because it accepts another function.

---

# 30. Important Interview Question

### Is every callback a Higher-Order Function?

**No.**

A callback is the function being passed.

Example:

```javascript
function greet() {
    console.log("Hello");
}

function execute(callback) {
    callback();
}

execute(greet);
```

Here:

```text
greet    → callback
execute  → Higher-Order Function
```

---

# 31. Important Interview Question

### Can a Higher-Order Function return another function?

Yes.

```javascript
function createGreeting() {

    return function() {
        console.log("Hello");
    };
}
```

Because it returns a function, it qualifies as a Higher-Order Function.

---

# 32. Important Interview Question

### Why is `map()` called a Higher-Order Function?

Because `map()` accepts a function as an argument.

```javascript
numbers.map(number => number * 2);
```

The function:

```javascript
number => number * 2
```

is the callback.

---

# 33. Important Interview Question

### What is the difference between `map()` and a Higher-Order Function?

These aren't directly competing concepts.

`map()` is a specific array method, and `map()` is also an example of a Higher-Order Function because it accepts a callback.

```text
map()
  ↓
Array method
  +
Higher-Order Function
  +
uses callback
```

---

# 34. Output-Based Interview Questions ⭐⭐⭐⭐⭐

## Question 1

```javascript
function execute(callback) {
    return callback();
}

function greet() {
    return "Hello";
}

console.log(execute(greet));
```

### Output

```text
Hello
```

---

## Question 2

```javascript
function createMultiplier(x) {
    return function(y) {
        return x * y;
    };
}

const double = createMultiplier(2);

console.log(double(5));
```

### Output

```text
10
```

---

## Question 3

```javascript
const numbers = [1, 2, 3];

const result = numbers.map(number => number * 2);

console.log(result);
```

### Output

```text
[2, 4, 6]
```

`map()` is the HOF.

The arrow function is the callback.

---

## Question 4

```javascript
function process(value, callback) {
    return callback(value);
}

const result = process(10, value => value + 5);

console.log(result);
```

### Output

```text
15
```

---

## Question 5

```javascript
function createCounter() {
    let count = 0;

    return function() {
        count++;
        return count;
    };
}

const counter = createCounter();

console.log(counter());
console.log(counter());
```

### Output

```text
1
2
```

This combines:

* Higher-Order Function
* Function returning function
* Closure

---

# 35. Common Mistakes

### Mistake 1 — Confusing callback and HOF

```javascript
numbers.map(number => number * 2);
```

Correct understanding:

```text
map() → Higher-Order Function
number => number * 2 → Callback
```

---

### Mistake 2 — Thinking HOF only means accepting a function

A HOF can also **return** a function.

```javascript
function createFunction() {
    return () => {
        console.log("Hello");
    };
}
```

---

### Mistake 3 — Thinking `map()` is just a loop

`map()` does iterate through elements, but its important behavior is:

> It transforms each element and returns a **new array**.

Example:

```javascript
const result = numbers.map(number => number * 2);
```

---

### Mistake 4 — Forgetting to return the callback result

Consider:

```javascript
function process(value, callback) {
    callback(value);
}
```

This does not return the callback's result.

If you want the result:

```javascript
function process(value, callback) {
    return callback(value);
}
```

---

# 36. Callback → HOF → Closure Connection ⭐⭐⭐⭐⭐

These three concepts are closely related.

### Callback

```javascript
function execute(callback) {
    callback();
}
```

A function is passed into another function.

### Higher-Order Function

```javascript
execute()
```

accepts a function.

### Closure

```javascript
function createMultiplier(x) {
    return function(y) {
        return x * y;
    };
}
```

The returned function remembers `x`.

So your JavaScript learning path is building logically:

```text
Functions
    ↓
Functions as values
    ↓
Callbacks
    ↓
Higher-Order Functions
    ↓
Closures
```

This is why learning them in this order is useful.

---

# 37. React Interview Connection ⭐⭐⭐⭐⭐

You should be comfortable seeing code like:

```jsx
{users
    .filter(user => user.active)
    .map(user => (
        <UserCard
            key={user.id}
            user={user}
        />
    ))}
```

Here:

```text
filter()
   ↓
Higher-Order Function
   ↓
callback: user => user.active

map()
   ↓
Higher-Order Function
   ↓
callback: user => (...)
```

This is standard React code.

---

# 38. Quick Comparison Table

| Concept    | Meaning                                 | Example                  |
| ---------- | --------------------------------------- | ------------------------ |
| Function   | Reusable block of code                  | `add()`                  |
| Callback   | Function passed to another function     | `map(x => x * 2)`        |
| HOF        | Function accepting/returning a function | `map()`                  |
| Closure    | Function remembers outer variables      | `createCounter()`        |
| `map()`    | Transform array                         | `[1,2].map(x => x*2)`    |
| `filter()` | Select array items                      | `[1,2].filter(x => x>1)` |
| `reduce()` | Combine array into one result           | sum                      |

---

# 39. Interview Cheat Sheet ⭐⭐⭐⭐⭐

Remember these definitions:

### Callback

> A function passed as an argument to another function.

```javascript
execute(greet);
```

### Higher-Order Function

> A function that accepts another function or returns a function.

```javascript
function execute(callback) {}
```

or:

```javascript
function createFunction() {
    return function() {};
}
```

### `map()`

> A Higher-Order Function that transforms array elements and returns a new array.

### `filter()`

> A Higher-Order Function that keeps elements satisfying a condition.

### `reduce()`

> A Higher-Order Function that processes an array and produces a single accumulated result.

---

# 40. What You Should Be Able to Do Now

Before moving on, you should be able to write these without help:

### Basic HOF

```javascript
function process(value, callback) {
    return callback(value);
}
```

### Passing a callback

```javascript
process(10, value => value * 2);
```

### Returning a function

```javascript
function multiplier(x) {
    return y => x * y;
}
```

### Using array HOFs

```javascript
numbers.map(...)
numbers.filter(...)
numbers.reduce(...)
numbers.find(...)
numbers.some(...)
numbers.every(...)
```

### React

```jsx
users.map(user => ...)
```

and:

```jsx
users
    .filter(user => user.active)
    .map(user => ...)
```

---

# 41. Practice Questions

Try these yourself.

### Practice 1 — Create a HOF

Create:

```javascript
processNumber(number, callback)
```

so this works:

```javascript
processNumber(10, number => number * 2);
```

Expected:

```text
20
```

---

### Practice 2 — Function Returning Function

Create:

```javascript
createMultiplier(5)
```

so:

```javascript
const multiplyByFive = createMultiplier(5);

console.log(multiplyByFive(4));
```

outputs:

```text
20
```

---

### Practice 3 — `map()`

Convert:

```javascript
[1, 2, 3, 4, 5]
```

into:

```javascript
[10, 20, 30, 40, 50]
```

---

### Practice 4 — `filter()`

From:

```javascript
[10, 15, 20, 25, 30]
```

get only numbers greater than `20`.

Expected:

```javascript
[25, 30]
```

---

### Practice 5 — Chaining

From:

```javascript
[1, 2, 3, 4, 5, 6]
```

get the even numbers and multiply each by `100`.

Expected:

```javascript
[200, 400, 600]
```

---

# ⭐ Final Mental Model

The easiest way to remember the whole topic is:

```text
FUNCTION
   ↓
Can be stored/passed/returned
   ↓
CALLBACK
   ↓
Function passed to another function
   ↓
HIGHER-ORDER FUNCTION
   ↓
Function accepts or returns another function
   ↓
COMMON EXAMPLES
   ↓
map()
filter()
reduce()
forEach()
find()
some()
every()
   ↓
REACT
   ↓
users.map(...)
users.filter(...)
event handlers
```

### Most important interview distinction:

```javascript
function execute(callback) {
    callback();
}
```

Here:

```text
execute  = Higher-Order Function
callback = Callback
```

And:

```javascript
function createFunction() {
    return function() {};
}
```

is also a Higher-Order Function because it **returns a function**.