# 6. Loops ⭐⭐⭐

Loops are used when you want to **repeat a block of code multiple times**.

Instead of writing:

```javascript
console.log(1);
console.log(2);
console.log(3);
console.log(4);
console.log(5);
```

you can use a loop:

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

Output:

```text
1
2
3
4
5
```

Loops are very important for JavaScript interviews and are especially useful in React when working with arrays and data.

---

# 1. Why Do We Need Loops?

Imagine you have 1,000 students:

```javascript
let students = [
    "Sai",
    "Rahul",
    "John",
    // ... 997 more
];
```

You don't want to write:

```javascript
console.log(students[0]);
console.log(students[1]);
console.log(students[2]);
// ...
```

Instead, you can loop through the array.

```javascript
for (let i = 0; i < students.length; i++) {
    console.log(students[i]);
}
```

This is one of the most common uses of loops.

---

# 2. Types of Loops in JavaScript

The important loops are:

```text
1. for
2. while
3. do...while
4. for...of
5. for...in
```

You'll also need to understand:

```text
break
continue
nested loops
```

And later, when we study arrays, you'll learn:

```text
forEach()
map()
filter()
reduce()
```

These are not technically loop statements, but they're extremely important for JavaScript and React.

---

# 3. `for` Loop ⭐⭐⭐⭐⭐

The `for` loop is one of the most important loops.

Syntax:

```javascript
for (initialization; condition; increment/decrement) {
    // code
}
```

Example:

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

Output:

```text
1
2
3
4
5
```

---

# 4. Understanding the Three Parts

Look at:

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

There are three important parts:

```text
        initialization
              ↓
for (let i = 1; i <= 5; i++)
                 ↑          ↑
             condition    increment
```

### Part 1: Initialization

```javascript
let i = 1;
```

This runs **once** at the beginning.

It creates the counter:

```text
i = 1
```

---

### Part 2: Condition

```javascript
i <= 5
```

Before every iteration, JavaScript checks this condition.

If:

```text
true
```

the loop executes.

If:

```text
false
```

the loop stops.

---

### Part 3: Increment

```javascript
i++
```

After each iteration, `i` increases by 1.

So:

```text
1 → 2 → 3 → 4 → 5 → 6
```

When:

```text
i = 6
```

the condition:

```javascript
6 <= 5
```

is false.

The loop stops.

---

# 5. Step-by-Step Execution

For:

```javascript
for (let i = 1; i <= 3; i++) {
    console.log(i);
}
```

Execution:

```text
i = 1
↓
1 <= 3 → true
↓
print 1
↓
i++ → 2

2 <= 3 → true
↓
print 2
↓
i++ → 3

3 <= 3 → true
↓
print 3
↓
i++ → 4

4 <= 3 → false
↓
STOP
```

Output:

```text
1
2
3
```

Understanding this flow is very important for interviews.

---

# 6. Counting Backwards

You can also decrease the counter.

```javascript
for (let i = 5; i >= 1; i--) {
    console.log(i);
}
```

Output:

```text
5
4
3
2
1
```

Here:

```javascript
i--
```

means:

```text
i = i - 1
```

---

# 7. Increment by 2

You don't have to increase by exactly 1.

```javascript
for (let i = 0; i <= 10; i += 2) {
    console.log(i);
}
```

Output:

```text
0
2
4
6
8
10
```

Because:

```javascript
i += 2
```

means:

```javascript
i = i + 2
```

---

# 8. Print Odd Numbers

```javascript
for (let i = 1; i <= 10; i += 2) {
    console.log(i);
}
```

Output:

```text
1
3
5
7
9
```

---

# 9. Print Even Numbers

```javascript
for (let i = 2; i <= 10; i += 2) {
    console.log(i);
}
```

Output:

```text
2
4
6
8
10
```

---

# 10. Loop Through an Array Using `for`

Suppose:

```javascript
let fruits = ["Apple", "Banana", "Mango"];
```

You can use:

```javascript
for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i]);
}
```

Output:

```text
Apple
Banana
Mango
```

Remember:

```javascript
fruits.length
```

is:

```text
3
```

And array indexes are:

```text
0 → Apple
1 → Banana
2 → Mango
```

So the loop uses:

```javascript
i < fruits.length
```

not:

```javascript
i <= fruits.length
```

---

# 11. Very Common Mistake: `<=` Instead of `<`

Correct:

```javascript
for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i]);
}
```

Incorrect:

```javascript
for (let i = 0; i <= fruits.length; i++) {
    console.log(fruits[i]);
}
```

Why?

If length is:

```text
3
```

valid indexes are:

```text
0
1
2
```

There is no index `3`.

So normally:

```javascript
i < array.length
```

is used.

---

# 12. `while` Loop

A `while` loop repeats code **while a condition is true**.

Syntax:

```javascript
while (condition) {
    // code
}
```

Example:

```javascript
let i = 1;

while (i <= 5) {
    console.log(i);
    i++;
}
```

Output:

```text
1
2
3
4
5
```

---

# 13. How `while` Works

Initially:

```javascript
let i = 1;
```

Then:

```javascript
while (i <= 5)
```

JavaScript checks the condition.

```text
1 <= 5 → true
```

Print:

```text
1
```

Then:

```javascript
i++;
```

Now:

```text
i = 2
```

It checks again.

Eventually:

```text
i = 6
```

Then:

```text
6 <= 5 → false
```

Loop stops.

---

# 14. Important: Update the Variable

Look at this:

```javascript
let i = 1;

while (i <= 5) {
    console.log(i);
}
```

This is a problem.

Why?

`i` never changes.

It stays:

```text
1
```

So:

```text
1 <= 5
```

will always be true.

This creates an **infinite loop**.

You usually need:

```javascript
i++;
```

inside the loop.

---

# 15. `for` vs `while`

### `for`

Good when you know how many times you want to repeat something.

```javascript
for (let i = 0; i < 10; i++) {
    console.log(i);
}
```

### `while`

Useful when repetition depends on a condition and the number of iterations isn't necessarily known beforehand.

```javascript
while (userHasNotFinished) {
    // continue
}
```

Simple rule:

```text
Known number of iterations → for
Condition-controlled repetition → while
```

This isn't an absolute rule, but it's a useful guideline.

---

# 16. `do...while`

`do...while` is similar to `while`, but there is one major difference:

> **The code executes at least once.**

Syntax:

```javascript
do {
    // code
} while (condition);
```

Example:

```javascript
let i = 1;

do {
    console.log(i);
    i++;
} while (i <= 5);
```

Output:

```text
1
2
3
4
5
```

---

# 17. `while` vs `do...while`

Consider:

```javascript
let i = 10;

while (i < 5) {
    console.log(i);
}
```

Output:

```text
nothing
```

Because:

```text
10 < 5
```

is false before the loop starts.

Now:

```javascript
let i = 10;

do {
    console.log(i);
} while (i < 5);
```

Output:

```text
10
```

Why?

Because `do...while` executes the code **before checking the condition**.

---

# 18. Important Difference

### `while`

```text
check condition
      ↓
true → execute
false → stop
```

### `do...while`

```text
execute first
      ↓
check condition
      ↓
true → repeat
false → stop
```

---

# 19. `for...of` ⭐⭐⭐⭐⭐

`for...of` is very useful for iterating over **values**.

Example:

```javascript
let fruits = ["Apple", "Banana", "Mango"];

for (let fruit of fruits) {
    console.log(fruit);
}
```

Output:

```text
Apple
Banana
Mango
```

This is simpler than:

```javascript
for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i]);
}
```

---

# 20. Understanding `for...of`

Given:

```javascript
let fruits = ["Apple", "Banana", "Mango"];
```

This:

```javascript
for (let fruit of fruits)
```

means:

```text
Take each value from fruits
and store it in fruit
```

Iterations:

```text
fruit = "Apple"
fruit = "Banana"
fruit = "Mango"
```

---

# 21. `for...of` with Strings

`for...of` also works with strings.

```javascript
let name = "Sai";

for (let character of name) {
    console.log(character);
}
```

Output:

```text
S
a
i
```

---

# 22. `for...in` ⭐⭐⭐⭐⭐

`for...in` is primarily used to iterate over **property keys** of an object.

Example:

```javascript
let user = {
    name: "Sai",
    age: 25,
    city: "Kadapa"
};

for (let key in user) {
    console.log(key);
}
```

Output:

```text
name
age
city
```

Here `key` contains the property names.

---

# 23. Getting Object Values with `for...in`

You can use:

```javascript
let user = {
    name: "Sai",
    age: 25,
    city: "Kadapa"
};

for (let key in user) {
    console.log(user[key]);
}
```

Output:

```text
Sai
25
Kadapa
```

Why?

If:

```javascript
key = "name"
```

then:

```javascript
user[key]
```

becomes:

```javascript
user["name"]
```

which gives:

```text
Sai
```

---

# 24. `for...of` vs `for...in` ⭐⭐⭐⭐⭐

This is a **very common interview question**.

### `for...of`

Gets:

```text
VALUES
```

Example:

```javascript
let fruits = ["Apple", "Banana"];

for (let fruit of fruits) {
    console.log(fruit);
}
```

Output:

```text
Apple
Banana
```

### `for...in`

Gets:

```text
KEYS / PROPERTY NAMES
```

Example:

```javascript
let user = {
    name: "Sai",
    age: 25
};

for (let key in user) {
    console.log(key);
}
```

Output:

```text
name
age
```

### Easy way to remember:

```text
for...of → values
for...in → keys
```

---

# 25. Should You Use `for...in` with Arrays?

Technically, `for...in` can iterate over array indexes, but it's generally **not the preferred choice for arrays**.

Example:

```javascript
let fruits = ["Apple", "Banana", "Mango"];

for (let index in fruits) {
    console.log(index);
}
```

Output:

```text
0
1
2
```

For arrays, prefer:

```javascript
for...of
```

or later:

```javascript
forEach()
map()
```

For objects:

```javascript
for...in
```

is often appropriate.

---

# 26. `break`

`break` immediately stops a loop.

Example:

```javascript
for (let i = 1; i <= 10; i++) {

    if (i === 5) {
        break;
    }

    console.log(i);
}
```

Output:

```text
1
2
3
4
```

When:

```javascript
i === 5
```

becomes true:

```javascript
break;
```

stops the entire loop.

---

# 27. `continue`

`continue` skips the **current iteration** and moves to the next iteration.

Example:

```javascript
for (let i = 1; i <= 5; i++) {

    if (i === 3) {
        continue;
    }

    console.log(i);
}
```

Output:

```text
1
2
4
5
```

When `i` is `3`, JavaScript skips:

```javascript
console.log(i);
```

and continues with `4`.

---

# 28. `break` vs `continue`

This is important.

### `break`

```text
STOP THE ENTIRE LOOP
```

### `continue`

```text
SKIP CURRENT ITERATION
```

Example:

```javascript
for (...) {

    if (...) {
        break;
    }
}
```

The loop ends completely.

But:

```javascript
for (...) {

    if (...) {
        continue;
    }
}
```

Only the current iteration is skipped.

---

# 29. Nested Loops

A loop inside another loop is called a **nested loop**.

Example:

```javascript
for (let i = 1; i <= 3; i++) {

    for (let j = 1; j <= 3; j++) {
        console.log(i, j);
    }

}
```

Output:

```text
1 1
1 2
1 3
2 1
2 2
2 3
3 1
3 2
3 3
```

---

# 30. How Nested Loops Work

For:

```javascript
for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 3; j++) {
        console.log(i, j);
    }
}
```

When:

```text
i = 1
```

the inner loop runs completely:

```text
1 1
1 2
1 3
```

Then:

```text
i = 2
```

inner loop runs again:

```text
2 1
2 2
2 3
```

Then:

```text
i = 3
```

inner loop runs again:

```text
3 1
3 2
3 3
```

---

# 31. Multiplication Table

Nested loops can be used for tables.

For example:

```javascript
let number = 5;

for (let i = 1; i <= 10; i++) {
    console.log(number * i);
}
```

Output:

```text
5
10
15
20
25
30
35
40
45
50
```

---

# 32. Looping Through an Array

Given:

```javascript
let students = [
    "Sai",
    "Rahul",
    "John",
    "Priya"
];
```

Using `for`:

```javascript
for (let i = 0; i < students.length; i++) {
    console.log(students[i]);
}
```

Using `for...of`:

```javascript
for (let student of students) {
    console.log(student);
}
```

Both produce:

```text
Sai
Rahul
John
Priya
```

---

# 33. Why This Matters for React

In React, you frequently have arrays like:

```javascript
const students = [
    "Sai",
    "Rahul",
    "John"
];
```

You need to display them.

Later you'll usually use:

```javascript
students.map(...)
```

For example:

```jsx
{students.map((student) => (
    <p>{student}</p>
))}
```

This is one reason understanding loops and array iteration is essential before learning React deeply.

We'll cover `map()` in detail when we reach **Arrays**.

---

# 34. Looping Through API Data

Suppose an API returns:

```javascript
const users = [
    {
        name: "Sai",
        age: 25
    },
    {
        name: "Rahul",
        age: 24
    }
];
```

You can iterate:

```javascript
for (let user of users) {
    console.log(user.name);
}
```

Output:

```text
Sai
Rahul
```

In React, this same concept becomes:

```jsx
users.map(user => (
    <p>{user.name}</p>
))
```

---

# 35. Infinite Loops

An infinite loop is a loop that never ends.

Example:

```javascript
let i = 1;

while (i <= 5) {
    console.log(i);
}
```

Problem:

```javascript
i
```

never changes.

Therefore:

```text
i = 1
```

forever.

The condition:

```text
1 <= 5
```

remains true.

---

# 36. Another Infinite Loop

Be careful with:

```javascript
for (let i = 1; i <= 5; i--) {
    console.log(i);
}
```

You are decreasing `i`:

```text
1
0
-1
-2
-3
...
```

But the condition is:

```javascript
i <= 5
```

which continues to be true.

So this can become an infinite loop.

---

# 37. Loop Scope

Consider:

```javascript
for (let i = 0; i < 3; i++) {
    console.log(i);
}
```

The variable:

```javascript
i
```

is block-scoped because we used `let`.

You cannot normally access it outside the loop:

```javascript
console.log(i);
```

This gives an error because `i` exists only inside the loop.

This connects to the earlier topic:

**Scope.**

---

# 38. `var` in Loops

You may see older JavaScript code like:

```javascript
for (var i = 0; i < 3; i++) {
    console.log(i);
}
```

Because `var` is function-scoped rather than block-scoped, its behavior outside the loop differs from `let`.

Modern JavaScript generally prefers:

```javascript
let i
```

for loop counters.

---

# 39. `forEach()` — Preview

You'll learn this properly with arrays, but it's useful to know.

Given:

```javascript
let fruits = ["Apple", "Banana", "Mango"];
```

You can write:

```javascript
fruits.forEach(function(fruit) {
    console.log(fruit);
});
```

Or with an arrow function:

```javascript
fruits.forEach((fruit) => {
    console.log(fruit);
});
```

Output:

```text
Apple
Banana
Mango
```

This is another way to iterate over arrays.

---

# 40. Traditional Loops vs Array Methods

You'll eventually see:

```javascript
for
while
do...while
for...of
for...in
```

and:

```javascript
forEach()
map()
filter()
reduce()
```

Don't confuse them.

The first group contains **loop statements**.

The second group contains **array methods** that can be used to process/iterate over arrays.

For React, the second group becomes particularly important.

---

# 41. Which Loop Should You Use?

A useful interview-level guideline:

| Situation                        | Usually use  |
| -------------------------------- | ------------ |
| Known number of repetitions      | `for`        |
| Condition-based repetition       | `while`      |
| Must execute at least once       | `do...while` |
| Iterate over array/string values | `for...of`   |
| Iterate over object keys         | `for...in`   |
| Simple array iteration           | `forEach()`  |
| Create a new transformed array   | `map()`      |
| Select matching elements         | `filter()`   |
| Calculate one accumulated result | `reduce()`   |

The last four will become very important when we reach **Arrays**.

---

# 42. Common Interview Question: `for` vs `for...of`

### `for`

Gives you more control over the index:

```javascript
let fruits = ["Apple", "Banana"];

for (let i = 0; i < fruits.length; i++) {
    console.log(i, fruits[i]);
}
```

Output:

```text
0 Apple
1 Banana
```

### `for...of`

Directly gives you the value:

```javascript
for (let fruit of fruits) {
    console.log(fruit);
}
```

Output:

```text
Apple
Banana
```

---

# 43. Common Interview Question: `for...of` vs `for...in`

Remember this:

```text
for...of → values
for...in → keys
```

Example:

```javascript
const user = {
    name: "Sai",
    age: 25
};

for (let key in user) {
    console.log(key);
}
```

Gives:

```text
name
age
```

But:

```javascript
const numbers = [10, 20, 30];

for (let number of numbers) {
    console.log(number);
}
```

Gives:

```text
10
20
30
```

---

# 44. Common Interview Question: `break` vs `continue`

### `break`

```javascript
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        break;
    }

    console.log(i);
}
```

Output:

```text
1
2
```

Loop completely stops.

### `continue`

```javascript
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        continue;
    }

    console.log(i);
}
```

Output:

```text
1
2
4
5
```

Only `3` is skipped.

---

# 45. Common Interview Question

What is the output?

```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

Answer:

```text
0
1
2
3
4
```

Not `5`.

Because the condition is:

```javascript
i < 5
```

When:

```text
i = 5
```

the condition becomes false.

---

# 46. Common Interview Question

What is the output?

```javascript
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        continue;
    }

    console.log(i);
}
```

Answer:

```text
1
2
4
5
```

---

# 47. Common Interview Question

What is the output?

```javascript
let i = 1;

while (i <= 3) {
    console.log(i);
    i++;
}
```

Answer:

```text
1
2
3
```

---

# 48. Common Interview Question

What is the output?

```javascript
let i = 10;

do {
    console.log(i);
} while (i < 5);
```

Answer:

```text
10
```

Because `do...while` executes once before checking the condition.

---

# 49. Practice Questions

Try these yourself before checking the answers.

### Q1

Print numbers from `1` to `10`.

```javascript
// write your code
```

---

### Q2

Print numbers from `10` to `1`.

```javascript
// write your code
```

---

### Q3

Print only even numbers from `1` to `20`.

```javascript
// write your code
```

---

### Q4

Print only odd numbers from `1` to `20`.

```javascript
// write your code
```

---

### Q5

Calculate the sum from `1` to `10`.

Expected:

```text
55
```

---

### Q6

Print this array:

```javascript
const fruits = ["Apple", "Banana", "Mango", "Orange"];
```

using:

```javascript
for
```

---

### Q7

Print the same array using:

```javascript
for...of
```

---

### Q8

Print all keys:

```javascript
const user = {
    name: "Sai",
    age: 25,
    city: "Kadapa"
};
```

using:

```javascript
for...in
```

---

### Q9

What is the output?

```javascript
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        break;
    }

    console.log(i);
}
```

---

### Q10

What is the output?

```javascript
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        continue;
    }

    console.log(i);
}
```

---

### Q11 — Interview Level

What is the difference between:

```javascript
for (let item of items)
```

and:

```javascript
for (let item in items)
```

---

### Q12 — React Related

Suppose:

```javascript
const users = ["Sai", "Rahul", "John"];
```

How would you display every user in React?

You'll eventually use:

```jsx
users.map(...)
```

We'll cover exactly how and why `map()` works in the **Arrays** topic.

---

# ⭐ Final Cheat Sheet

```javascript
// 1. for
for (let i = 0; i < 5; i++) {
    console.log(i);
}

// 2. while
let i = 0;

while (i < 5) {
    console.log(i);
    i++;
}

// 3. do...while
let j = 0;

do {
    console.log(j);
    j++;
} while (j < 5);

// 4. for...of
for (let value of array) {
    console.log(value);
}

// 5. for...in
for (let key in object) {
    console.log(key);
}

// 6. break
break;

// 7. continue
continue;
```

### ⭐ The most important things to remember

```text
for           → general-purpose loop
while         → condition-based loop
do...while    → executes at least once
for...of      → values
for...in      → keys
break         → stop loop
continue      → skip current iteration
```

And for your **React interview preparation**, pay special attention to:

```text
for
for...of
forEach()
map()
filter()
reduce()
```