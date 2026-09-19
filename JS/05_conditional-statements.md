# 5. Conditional Statements ⭐⭐⭐

Conditional statements are used when your program needs to **make decisions**.

In simple words:

> **"If this condition is true, do this. Otherwise, do something else."**

You use conditional statements everywhere in JavaScript and React:

* Login/logout
* Showing/hiding components
* Checking user permissions
* Form validation
* API response handling
* Displaying loading/error/success states
* Checking age, marks, price, etc.

---

# 1. What is a Condition?

A condition is an expression that results in:

```javascript
true
```

or:

```javascript
false
```

Example:

```javascript
10 > 5
```

Result:

```text
true
```

Another:

```javascript
10 < 5
```

Result:

```text
false
```

JavaScript uses these `true`/`false` results to make decisions.

---

# 2. `if` Statement

The simplest conditional statement is:

```javascript
if (condition) {
    // code
}
```

Example:

```javascript
let age = 20;

if (age >= 18) {
    console.log("You are an adult");
}
```

Output:

```text
You are an adult
```

### How does it work?

JavaScript checks:

```javascript
age >= 18
```

Since:

```text
20 >= 18
```

is:

```text
true
```

the code inside `{ }` executes.

---

# 3. What if the Condition is False?

```javascript
let age = 15;

if (age >= 18) {
    console.log("You are an adult");
}
```

Nothing is printed.

Why?

Because:

```javascript
15 >= 18
```

is:

```text
false
```

Therefore JavaScript skips the code inside the `if`.

---

# 4. `if...else`

When you want to do one thing if the condition is true and another thing if it's false:

```javascript
if (condition) {
    // true
} else {
    // false
}
```

Example:

```javascript
let age = 15;

if (age >= 18) {
    console.log("You can vote");
} else {
    console.log("You cannot vote");
}
```

Output:

```text
You cannot vote
```

---

# 5. Flow of `if...else`

Think of it like this:

```text
             condition
                 |
          +------+------+
          |             |
        true          false
          |             |
       if block      else block
```

Example:

```javascript
let number = 10;

if (number > 0) {
    console.log("Positive");
} else {
    console.log("Not positive");
}
```

JavaScript checks:

```text
10 > 0
```

Result:

```text
true
```

So:

```text
Positive
```

is printed.

---

# 6. `else if`

What if you have **multiple conditions**?

Use:

```javascript
if (condition1) {

} else if (condition2) {

} else if (condition3) {

} else {

}
```

Example:

```javascript
let marks = 75;

if (marks >= 90) {
    console.log("Grade A");
} else if (marks >= 75) {
    console.log("Grade B");
} else if (marks >= 50) {
    console.log("Grade C");
} else {
    console.log("Fail");
}
```

Output:

```text
Grade B
```

---

# 7. How `else if` Works

JavaScript checks conditions **from top to bottom**.

For:

```javascript
let marks = 75;
```

First:

```javascript
marks >= 90
```

is false.

Then:

```javascript
marks >= 75
```

is true.

So JavaScript executes:

```javascript
console.log("Grade B");
```

and stops checking the remaining `else if` conditions.

---

# 8. Order of Conditions Matters

This is very important.

Consider:

```javascript
let marks = 95;

if (marks >= 50) {
    console.log("Grade C");
} else if (marks >= 90) {
    console.log("Grade A");
}
```

Output:

```text
Grade C
```

Why?

Because JavaScript checks:

```javascript
marks >= 50
```

First.

`95 >= 50` is true.

So it enters that block and doesn't reach:

```javascript
marks >= 90
```

### Correct order:

```javascript
if (marks >= 90) {
    console.log("Grade A");
} else if (marks >= 75) {
    console.log("Grade B");
} else if (marks >= 50) {
    console.log("Grade C");
} else {
    console.log("Fail");
}
```

Usually, when ranges overlap, check the **more specific/higher threshold first**.

---

# 9. Multiple Conditions with Logical Operators

You can combine conditions using:

```javascript
&&
||
!
```

### AND `&&`

Both conditions must be true.

```javascript
let age = 25;
let hasLicense = true;

if (age >= 18 && hasLicense) {
    console.log("You can drive");
}
```

Both must be true:

```text
age >= 18       → true
hasLicense      → true
```

Therefore:

```text
You can drive
```

---

# 10. OR `||`

At least one condition must be true.

```javascript
let isAdmin = false;
let isManager = true;

if (isAdmin || isManager) {
    console.log("Access granted");
}
```

Here:

```text
isAdmin  → false
isManager → true
```

Because one condition is true:

```text
Access granted
```

---

# 11. NOT `!`

`!` reverses a boolean value.

```javascript
let isLoggedIn = false;

if (!isLoggedIn) {
    console.log("Please login");
}
```

Since:

```javascript
isLoggedIn = false
```

then:

```javascript
!isLoggedIn
```

becomes:

```text
true
```

So the message is printed.

---

# 12. Conditions Don't Have to Be Comparisons

You can directly use a variable:

```javascript
let isLoggedIn = true;

if (isLoggedIn) {
    console.log("Welcome");
}
```

Because:

```javascript
isLoggedIn
```

is already `true`.

---

# 13. Truthy and Falsy Conditions

This connects directly to the previous topic.

JavaScript converts values into boolean context.

For example:

```javascript
let username = "";

if (username) {
    console.log("Username exists");
} else {
    console.log("Username is empty");
}
```

Since:

```text
"" → falsy
```

the output is:

```text
Username is empty
```

---

# 14. Common Falsy Values

Remember:

```javascript
false
0
-0
0n
""
null
undefined
NaN
```

These are falsy.

Example:

```javascript
if (0) {
    console.log("Yes");
} else {
    console.log("No");
}
```

Output:

```text
No
```

---

# 15. Truthy Values

These are truthy:

```javascript
"hello"
"0"
"false"
1
-1
[]
{}
function () {}
```

For example:

```javascript
if ("hello") {
    console.log("Hello");
}
```

Output:

```text
Hello
```

---

# 16. Nested `if`

An `if` statement can exist inside another `if`.

Example:

```javascript
let age = 25;
let hasLicense = true;

if (age >= 18) {

    if (hasLicense) {
        console.log("You can drive");
    }

}
```

Here the second condition is checked only if the first condition is true.

---

# 17. Nested `if` with `else`

```javascript
let age = 20;
let hasLicense = false;

if (age >= 18) {

    if (hasLicense) {
        console.log("You can drive");
    } else {
        console.log("You need a license");
    }

} else {
    console.log("You are underage");
}
```

Output:

```text
You need a license
```

---

# 18. Avoid Excessive Nesting

Although nested `if` works, too much nesting makes code difficult to understand.

Instead of:

```javascript
if (age >= 18) {
    if (hasLicense) {
        if (isSober) {
            console.log("Can drive");
        }
    }
}
```

you can often simplify:

```javascript
if (age >= 18 && hasLicense && isSober) {
    console.log("Can drive");
}
```

This is easier to read.

---

# 19. `switch` Statement

`switch` is useful when you're comparing **one value against multiple possible values**.

Syntax:

```javascript
switch (value) {
    case value1:
        // code
        break;

    case value2:
        // code
        break;

    default:
        // code
}
```

Example:

```javascript
let day = 2;

switch (day) {
    case 1:
        console.log("Monday");
        break;

    case 2:
        console.log("Tuesday");
        break;

    case 3:
        console.log("Wednesday");
        break;

    default:
        console.log("Invalid day");
}
```

Output:

```text
Tuesday
```

---

# 20. Why `break` Is Important

Consider:

```javascript
let day = 2;

switch (day) {
    case 1:
        console.log("Monday");

    case 2:
        console.log("Tuesday");

    case 3:
        console.log("Wednesday");
}
```

Output can be:

```text
Tuesday
Wednesday
```

Why?

Because without `break`, JavaScript continues into the following cases.

This is called **fall-through**.

Normally you use:

```javascript
break;
```

to stop execution after a matching case.

---

# 21. `default`

`default` executes when no case matches.

```javascript
let day = 10;

switch (day) {
    case 1:
        console.log("Monday");
        break;

    case 2:
        console.log("Tuesday");
        break;

    default:
        console.log("Invalid day");
}
```

Output:

```text
Invalid day
```

---

# 22. `switch` vs `if...else`

Use `if...else` when you're checking:

```text
ranges
multiple different conditions
complex expressions
```

Example:

```javascript
if (age >= 18 && hasLicense) {
    ...
}
```

Use `switch` when you're checking one value against specific values:

```javascript
switch (role) {
    case "admin":
    case "student":
    case "employee":
}
```

---

# 23. Ternary Operator

The ternary operator is a **short form of `if...else`**.

Syntax:

```javascript
condition ? valueIfTrue : valueIfFalse
```

Example:

```javascript
let age = 20;

let result = age >= 18 ? "Adult" : "Minor";

console.log(result);
```

Output:

```text
Adult
```

This is equivalent to:

```javascript
let result;

if (age >= 18) {
    result = "Adult";
} else {
    result = "Minor";
}
```

---

# 24. Ternary in React ⭐⭐⭐⭐⭐

Ternary operators are extremely common in React.

Example:

```jsx
{isLoggedIn ? <Dashboard /> : <Login />}
```

Meaning:

```text
if isLoggedIn is true
    → show Dashboard

else
    → show Login
```

This is one of the most important conditional-rendering patterns in React.

---

# 25. `&&` Conditional Rendering in React

Another common pattern:

```jsx
{isLoggedIn && <LogoutButton />}
```

Meaning:

```text
if isLoggedIn is true
    → show LogoutButton
```

If false, the component isn't rendered.

---

# 26. `if` vs Ternary in React

For larger logic, use normal JavaScript:

```javascript
if (isLoading) {
    // logic
}
```

For simple value selection or rendering:

```jsx
{isLoading ? <Loading /> : <Content />}
```

### Example

```jsx
function App() {
    const isLoggedIn = true;

    return (
        <div>
            {isLoggedIn ? <h1>Welcome</h1> : <h1>Please Login</h1>}
        </div>
    );
}
```

---

# 27. Don't Overuse Nested Ternaries

This:

```javascript
const result =
    age >= 18
        ? "Adult"
        : age >= 13
        ? "Teenager"
        : "Child";
```

works, but can become difficult to read.

For more complicated conditions, use:

```javascript
if
else if
else
```

or move the logic into a function.

---

# 28. Early Return

This is a very useful pattern in JavaScript and React.

Instead of:

```javascript
function getUserName(user) {

    if (user) {
        return user.name;
    } else {
        return "Guest";
    }

}
```

you can write:

```javascript
function getUserName(user) {

    if (!user) {
        return "Guest";
    }

    return user.name;
}
```

This is called an **early return**.

It reduces nesting.

---

# 29. React Example with Early Return

Very common:

```jsx
function Profile({ user }) {

    if (!user) {
        return <p>Please login</p>;
    }

    return <h1>Welcome {user.name}</h1>;
}
```

This is clean and easy to understand.

---

# 30. A Real-World Login Example

```javascript
let username = "Sai";
let password = "1234";

if (username === "Sai" && password === "1234") {
    console.log("Login successful");
} else {
    console.log("Invalid username or password");
}
```

Here we use:

```javascript
===
```

for exact comparison.

And:

```javascript
&&
```

because both conditions need to be true.

---

# 31. Form Validation Example

```javascript
let username = "";
let password = "";

if (username === "") {
    console.log("Username is required");
} else if (password === "") {
    console.log("Password is required");
} else {
    console.log("Form submitted");
}
```

This type of logic is very common in React applications.

---

# 32. Important Difference: `if` Doesn't Return a Value

Consider:

```javascript
if (age >= 18) {
    console.log("Adult");
}
```

`if` is a statement.

A ternary expression can produce a value:

```javascript
let status = age >= 18 ? "Adult" : "Minor";
```

That's why ternary is useful when assigning a value.

---

# 33. Common Interview Question

### What is the difference between `if...else` and ternary?

`if...else`:

```javascript
if (age >= 18) {
    result = "Adult";
} else {
    result = "Minor";
}
```

Ternary:

```javascript
result = age >= 18 ? "Adult" : "Minor";
```

Ternary is generally useful for **short/simple conditions**.

---

# 34. Common Interview Question

### What is the difference between `==` and `===` in conditions?

```javascript
5 == "5"
```

is:

```text
true
```

because `==` allows type coercion.

But:

```javascript
5 === "5"
```

is:

```text
false
```

because `===` checks type and value.

In conditions, generally prefer:

```javascript
===
```

---

# 35. Common Interview Question

What does this output?

```javascript
let value = 0;

if (value) {
    console.log("A");
} else {
    console.log("B");
}
```

Answer:

```text
B
```

Because:

```text
0 → falsy
```

---

# 36. Common Interview Question

What does this output?

```javascript
let value = "0";

if (value) {
    console.log("A");
} else {
    console.log("B");
}
```

Answer:

```text
A
```

Because:

```text
"0" → non-empty string → truthy
```

---

# 37. Common Interview Question

What does this output?

```javascript
let age = 20;

if (age >= 18) {
    console.log("A");
} else if (age >= 15) {
    console.log("B");
} else {
    console.log("C");
}
```

Output:

```text
A
```

Once the first true condition is found, the remaining `else if` and `else` blocks are skipped.

---

# 38. Common Mistake: Assignment Instead of Comparison

Be careful with:

```javascript
if (age = 18) {
    console.log("Adult");
}
```

This is an **assignment**, not a comparison.

You usually want:

```javascript
if (age === 18) {
    console.log("Adult");
}
```

Remember:

```text
=    → assignment
==   → loose comparison
===  → strict comparison
```

---

# 39. Common Mistake: Using `=` in Conditions

Bad:

```javascript
if (username = "Sai") {
    ...
}
```

Good:

```javascript
if (username === "Sai") {
    ...
}
```

This is a very common beginner mistake.

---

# 40. Common Mistake: Forgetting Braces

You can technically write:

```javascript
if (age >= 18)
    console.log("Adult");
```

But for beginner/interview code, prefer:

```javascript
if (age >= 18) {
    console.log("Adult");
}
```

Braces make the code safer and easier to maintain.

---

# 41. Common Mistake: Wrong Condition Order

Bad:

```javascript
if (marks >= 50) {
    console.log("C");
} else if (marks >= 90) {
    console.log("A");
}
```

For `95`, you'll get:

```text
C
```

because `95 >= 50` is already true.

Better:

```javascript
if (marks >= 90) {
    console.log("A");
} else if (marks >= 50) {
    console.log("C");
}
```

---

# 42. Quick Comparison

| Statement   | Purpose                                     |   |                                         |
| ----------- | ------------------------------------------- | - | --------------------------------------- |
| `if`        | One condition                               |   |                                         |
| `if...else` | Two possible paths                          |   |                                         |
| `else if`   | Multiple conditions                         |   |                                         |
| `switch`    | Compare one value with multiple exact cases |   |                                         |
| `ternary`   | Short `if...else`                           |   |                                         |
| `&&`        | Execute/check when both are true            |   |                                         |
| `           |                                             | ` | Execute/check when at least one is true |
| `!`         | Reverse boolean                             |   |                                         |

---

# 43. What You Need to Know for React ⭐⭐⭐⭐⭐

For React interviews, focus especially on:

### 1. `if...else`

```javascript
if (isLoggedIn) {
    ...
} else {
    ...
}
```

### 2. `else if`

```javascript
if (status === "loading") {
    ...
} else if (status === "success") {
    ...
} else {
    ...
}
```

### 3. Ternary

```jsx
{isLoggedIn ? <Dashboard /> : <Login />}
```

### 4. `&&`

```jsx
{isAdmin && <AdminPanel />}
```

### 5. Truthy/falsy

```javascript
if (user) {
    ...
}
```

### 6. Early return

```jsx
if (!user) {
    return <Login />;
}
```

These patterns appear constantly in React applications.

---

# 44. Practice Questions

Try solving these **before looking at the answers**.

### Q1

What is the output?

```javascript
let age = 20;

if (age >= 18) {
    console.log("Adult");
} else {
    console.log("Minor");
}
```

---

### Q2

```javascript
let number = -5;

if (number > 0) {
    console.log("Positive");
} else if (number < 0) {
    console.log("Negative");
} else {
    console.log("Zero");
}
```

---

### Q3

What is the output?

```javascript
let value = "";

if (value) {
    console.log("A");
} else {
    console.log("B");
}
```

---

### Q4

What is the output?

```javascript
let value = "0";

if (value) {
    console.log("A");
} else {
    console.log("B");
}
```

---

### Q5

Convert this into a ternary:

```javascript
let age = 20;

let result;

if (age >= 18) {
    result = "Adult";
} else {
    result = "Minor";
}
```

---

### Q6

What is the output?

```javascript
let day = 2;

switch (day) {
    case 1:
        console.log("Monday");
        break;

    case 2:
        console.log("Tuesday");
        break;

    default:
        console.log("Invalid");
}
```

---

### Q7

What is wrong here?

```javascript
let age = 20;

if (age = 18) {
    console.log("Adult");
}
```

---

### Q8 — React

What will this do?

```jsx
{isLoggedIn ? <Dashboard /> : <Login />}
```

---

### Q9 — React

What will this do?

```jsx
{isAdmin && <AdminPanel />}
```

---

### Q10 — Interview Level

What is the output?

```javascript
let marks = 95;

if (marks >= 50) {
    console.log("C");
} else if (marks >= 90) {
    console.log("A");
} else {
    console.log("Fail");
}
```

And explain **why**.

---

## ⭐ Final Cheat Sheet

```javascript
// if
if (condition) {
    // code
}

// if...else
if (condition) {
    // true
} else {
    // false
}

// else if
if (condition1) {

} else if (condition2) {

} else {

}

// switch
switch (value) {
    case 1:
        // code
        break;

    case 2:
        // code
        break;

    default:
        // code
}

// ternary
condition ? value1 : value2;

// React conditional rendering
{condition && <Component />}

{condition ? <ComponentA /> : <ComponentB />}
```

### Most important takeaway

Think of conditional statements as:

```text
             CONDITION
                 |
        +--------+--------+
        |                 |
      TRUE              FALSE
        |                 |
      ACTION            OTHER ACTION
```

And for React, become very comfortable with:

```jsx
if
else if
else
? :
&&
!
```
