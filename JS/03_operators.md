# 3. JavaScript Operators ⭐⭐⭐⭐⭐

Operators are symbols or keywords that tell JavaScript to **perform an operation on values**.

For example:

```js
let a = 10;
let b = 5;

console.log(a + b);
```

Here:

```text
a + b
```

uses the `+` operator.

Output:

```text
15
```

Operators are used everywhere in JavaScript and React:

```text
Calculations
Conditions
Comparisons
State updates
Form validation
API logic
Filtering
Conditional rendering
```

---

# 1. Types of JavaScript Operators

The important categories are:

```text
Operators
│
├── Arithmetic
├── Assignment
├── Comparison
├── Logical
├── Increment / Decrement
├── String
├── Ternary
├── Nullish Coalescing ??
├── Optional Chaining ?.
├── Bitwise
└── Unary
```

For React interviews, focus heavily on:

```text
⭐⭐⭐⭐⭐ Comparison
⭐⭐⭐⭐⭐ Logical
⭐⭐⭐⭐⭐ Ternary
⭐⭐⭐⭐⭐ Spread
⭐⭐⭐⭐⭐ Optional chaining
⭐⭐⭐⭐⭐ Nullish coalescing
⭐⭐⭐⭐ Arithmetic / Assignment
```

---

# 2. Arithmetic Operators ⭐⭐⭐

Arithmetic operators are used for mathematical calculations.

| Operator | Meaning        |
| -------- | -------------- |
| `+`      | Addition       |
| `-`      | Subtraction    |
| `*`      | Multiplication |
| `/`      | Division       |
| `%`      | Remainder      |
| `**`     | Exponentiation |

---

## Addition `+`

```js
let a = 10;
let b = 5;

console.log(a + b);
```

Output:

```text
15
```

---

## Subtraction `-`

```js
let a = 10;
let b = 5;

console.log(a - b);
```

Output:

```text
5
```

---

## Multiplication `*`

```js
console.log(10 * 5);
```

Output:

```text
50
```

---

## Division `/`

```js
console.log(10 / 5);
```

Output:

```text
2
```

---

# 3. Remainder `%` ⭐⭐⭐

The `%` operator returns the **remainder** after division.

```js
console.log(10 % 3);
```

Output:

```text
1
```

Because:

```text
10 ÷ 3

3 × 3 = 9
remainder = 1
```

Very common use:

### Check even number

```js
let number = 10;

console.log(number % 2 === 0);
```

Output:

```text
true
```

### Check odd number

```js
let number = 7;

console.log(number % 2 !== 0);
```

Output:

```text
true
```

You'll see `%` frequently in coding problems.

---

# 4. Exponentiation `**`

Used for powers.

```js
console.log(2 ** 3);
```

Output:

```text
8
```

Because:

```text
2 × 2 × 2 = 8
```

Another:

```js
console.log(5 ** 2);
```

Output:

```text
25
```

---

# 5. Assignment Operators ⭐⭐⭐⭐

Assignment operators assign values to variables.

The basic assignment operator is:

```js
=
```

Example:

```js
let age = 25;
```

Here:

```text
age = 25
```

means assign `25` to `age`.

---

# 6. Compound Assignment Operators

Instead of:

```js
let count = 10;

count = count + 5;
```

you can write:

```js
let count = 10;

count += 5;
```

Result:

```text
15
```

Common operators:

```text
+=
-=
*=
/=
%=
**=
```

Examples:

```js
let x = 10;

x += 5;  // 15
x -= 3;  // 12
x *= 2;  // 24
x /= 4;  // 6
```

---

# 7. Comparison Operators ⭐⭐⭐⭐⭐

Comparison operators compare values and return:

```text
true
```

or:

```text
false
```

Important operators:

```text
==
===
!=
!==
>
<
>=
<=
```

These are **extremely important** for interviews.

---

# 8. Greater Than `>`

```js
console.log(10 > 5);
```

Output:

```text
true
```

Because 10 is greater than 5.

```js
console.log(3 > 5);
```

Output:

```text
false
```

---

# 9. Less Than `<`

```js
console.log(3 < 5);
```

Output:

```text
true
```

---

# 10. Greater Than or Equal `>=`

```js
console.log(10 >= 10);
```

Output:

```text
true
```

Both are true:

```text
10 > 10   → false
10 >= 10  → true
```

---

# 11. Less Than or Equal `<=`

```js
console.log(5 <= 5);
```

Output:

```text
true
```

---

# 12. `==` Loose Equality ⭐⭐⭐⭐⭐

`==` compares values after allowing JavaScript to perform type conversion when necessary.

Example:

```js
console.log(5 == "5");
```

Output:

```text
true
```

Why?

Because JavaScript converts one side so that the values can be compared.

Conceptually:

```text
5
"5"
 ↓
type conversion
 ↓
equal
```

This behavior is called **type coercion**.

---

# 13. `===` Strict Equality ⭐⭐⭐⭐⭐

`===` checks both:

```text
Value
+
Type
```

Example:

```js
console.log(5 === "5");
```

Output:

```text
false
```

Because:

```text
5   → number
"5" → string
```

Different types.

---

# 14. `==` vs `===` ⭐⭐⭐⭐⭐

This is one of the most common JavaScript interview questions.

### `==`

```js
5 == "5"
```

→ `true`

It allows type coercion.

### `===`

```js
5 === "5"
```

→ `false`

It checks type and value without performing the same implicit coercion.

### General recommendation

In modern JavaScript:

```text
Prefer === over ==
```

unless you have a specific reason to use loose equality.

In React code, you'll usually see:

```js
if (age === 18) {
    ...
}
```

rather than:

```js
if (age == 18) {
    ...
}
```

---

# 15. Not Equal `!=`

```js
console.log(10 != 5);
```

Output:

```text
true
```

Like `==`, `!=` can perform type coercion.

---

# 16. Strict Not Equal `!==` ⭐⭐⭐⭐⭐

Checks both type and value.

```js
console.log(5 !== "5");
```

Output:

```text
true
```

Because:

```text
number !== string
```

In modern JavaScript, prefer:

```text
!== 
```

over:

```text
!=
```

when you want strict comparison.

---

# 17. Logical Operators ⭐⭐⭐⭐⭐

Logical operators are heavily used in JavaScript and React.

There are three primary ones:

```text
&&
||
!
```

---

# 18. AND `&&`

`&&` means **AND**.

For:

```js
A && B
```

both conditions need to be truthy for the overall expression to produce a truthy result.

Example:

```js
let age = 25;

console.log(age > 18 && age < 60);
```

Both are true:

```text
25 > 18 → true
25 < 60 → true
```

Therefore:

```text
true
```

---

# 19. OR `||`

`||` means **OR**.

If at least one operand is truthy, the expression can produce a truthy result.

```js
console.log(10 > 20 || 10 < 20);
```

First:

```text
10 > 20 → false
```

Second:

```text
10 < 20 → true
```

Therefore:

```text
true
```

---

# 20. NOT `!`

`!` reverses a boolean value.

```js
console.log(!true);
```

Output:

```text
false
```

And:

```js
console.log(!false);
```

Output:

```text
true
```

Example:

```js
let isLoggedIn = false;

if (!isLoggedIn) {
    console.log("Please login");
}
```

---

# 21. Logical Operators in React ⭐⭐⭐⭐⭐

You'll use `&&` constantly in React.

Example:

```jsx
{isLoggedIn && <button>Logout</button>}
```

Meaning:

```text
isLoggedIn is true
        ↓
show Logout button
```

If:

```js
isLoggedIn = false
```

the expression doesn't render the button.

This is called **conditional rendering**.

---

# 22. Short-Circuit Evaluation ⭐⭐⭐⭐⭐

This is an important JavaScript concept.

Consider:

```js
true && "Hello"
```

Result:

```text
"Hello"
```

And:

```js
false && "Hello"
```

Result:

```text
false
```

Why?

For `&&`:

```text
First value is falsy
       ↓
JavaScript doesn't need to evaluate further
```

This is called **short-circuiting**.

---

# 23. `||` Short-Circuiting

Example:

```js
const name = "" || "Guest";
```

Result:

```text
"Guest"
```

Because:

```text
"" → falsy
```

So JavaScript evaluates the second value.

Another:

```js
const name = "Sai" || "Guest";
```

Result:

```text
"Sai"
```

Because `"Sai"` is truthy.

This pattern is often used for fallback values.

---

# 24. Ternary Operator ⭐⭐⭐⭐⭐

The ternary operator is a short way of writing an `if...else`.

Syntax:

```js
condition ? valueIfTrue : valueIfFalse
```

Example:

```js
const age = 20;

const result = age >= 18 ? "Adult" : "Minor";

console.log(result);
```

Output:

```text
Adult
```

Equivalent `if...else`:

```js
let result;

if (age >= 18) {
    result = "Adult";
} else {
    result = "Minor";
}
```

---

# 25. Ternary in React ⭐⭐⭐⭐⭐

Very common.

```jsx
{isLoggedIn ? <Dashboard /> : <Login />}
```

Meaning:

```text
isLoggedIn
    │
 ┌──┴──┐
true  false
 ↓      ↓
Dashboard Login
```

This is why you should become comfortable with ternary operators before going deep into React.

---

# 26. Nested Ternary

You technically can do:

```js
const result =
    age >= 18
        ? "Adult"
        : age >= 13
            ? "Teenager"
            : "Child";
```

But too many nested ternaries become difficult to read.

For complex logic, prefer:

```js
if / else if / else
```

or extract the logic into a function.

---

# 27. Increment Operator `++`

Adds 1.

```js
let count = 10;

count++;

console.log(count);
```

Output:

```text
11
```

Equivalent to:

```js
count = count + 1;
```

---

# 28. Decrement Operator `--`

Subtracts 1.

```js
let count = 10;

count--;

console.log(count);
```

Output:

```text
9
```

---

# 29. Prefix vs Postfix ⭐⭐⭐⭐

This is an interview favorite.

### Postfix

```js
let x = 5;

let y = x++;
```

First:

```text
y gets 5
```

Then:

```text
x becomes 6
```

So:

```text
x → 6
y → 5
```

---

### Prefix

```js
let x = 5;

let y = ++x;
```

First:

```text
x becomes 6
```

Then:

```text
y gets 6
```

So:

```text
x → 6
y → 6
```

Remember:

```text
x++ → use first, increment later

++x → increment first, use later
```

---

# 30. String `+` Operator ⭐⭐⭐⭐⭐

The `+` operator behaves differently when strings are involved.

```js
console.log("Hello " + "Sai");
```

Output:

```text
Hello Sai
```

You can combine strings and variables:

```js
const name = "Sai";

console.log("Hello " + name);
```

Output:

```text
Hello Sai
```

---

# 31. Number + String ⭐⭐⭐⭐⭐

This is a common interview question.

```js
console.log(10 + "5");
```

Output:

```text
105
```

Why?

The `+` operator with a string causes string concatenation in this case.

Conceptually:

```text
10
"5"
 ↓
"10" + "5"
 ↓
"105"
```

Compare:

```js
console.log(10 - "5");
```

Output:

```text
5
```

Because `-` doesn't concatenate strings in the same way and JavaScript converts `"5"` to a number.

This is **type coercion**, which we'll study more deeply.

---

# 32. Nullish Coalescing `??` ⭐⭐⭐⭐⭐

This is very useful in modern JavaScript and React.

Syntax:

```js
value ?? fallback
```

It uses the fallback only when the first value is:

```text
null
```

or:

```text
undefined
```

Example:

```js
const name = null;

console.log(name ?? "Guest");
```

Output:

```text
Guest
```

Another:

```js
const name = undefined;

console.log(name ?? "Guest");
```

Output:

```text
Guest
```

But:

```js
const name = "Sai";

console.log(name ?? "Guest");
```

Output:

```text
Sai
```

---

# 33. `??` vs `||` ⭐⭐⭐⭐⭐

This is important.

Consider:

```js
const count = 0;

console.log(count || 10);
```

Result:

```text
10
```

Because `0` is falsy.

But:

```js
console.log(count ?? 10);
```

Result:

```text
0
```

Why?

Because `??` only considers:

```text
null
undefined
```

as missing.

So:

```text
|| → fallback for any falsy value

?? → fallback only for null/undefined
```

This distinction is very useful when dealing with API data.

---

# 34. Optional Chaining `?.` ⭐⭐⭐⭐⭐

Very important for React and API responses.

Suppose:

```js
const user = {
    name: "Sai"
};
```

You can access:

```js
console.log(user.name);
```

But suppose:

```js
const user = null;
```

Then:

```js
console.log(user.name);
```

❌ Error.

Because you're trying to access `name` from `null`.

Instead:

```js
console.log(user?.name);
```

Result:

```text
undefined
```

The `?.` means:

> If the value exists, access the property; otherwise return `undefined` instead of throwing an error.

---

# 35. Optional Chaining with Nested Objects ⭐⭐⭐⭐⭐

Suppose an API returns:

```js
const user = {
    profile: {
        address: {
            city: "Kadapa"
        }
    }
};
```

Without optional chaining:

```js
console.log(user.profile.address.city);
```

Works.

But if `profile` doesn't exist, you'll get an error.

With optional chaining:

```js
console.log(user?.profile?.address?.city);
```

This safely checks each level.

This is very common when displaying API data in React.

---

# 36. Optional Chaining with Functions

You can also use:

```js
user.getName?.();
```

Meaning:

> Call `getName()` only if it exists.

This can be useful when a function/property may be optional.

---

# 37. Spread Operator `...` ⭐⭐⭐⭐⭐

The spread syntax expands values.

### Arrays

```js
const numbers1 = [1, 2, 3];

const numbers2 = [...numbers1, 4, 5];

console.log(numbers2);
```

Output:

```text
[1, 2, 3, 4, 5]
```

It is extremely important for React because it's commonly used to create new arrays.

---

# 38. Spread with Objects ⭐⭐⭐⭐⭐

```js
const user = {
    name: "Sai",
    age: 25
};

const updatedUser = {
    ...user,
    age: 26
};
```

Now:

```text
user
→ { name: "Sai", age: 25 }

updatedUser
→ { name: "Sai", age: 26 }
```

This is a very common React pattern.

For example, updating an object state:

```js
setUser({
    ...user,
    name: "John"
});
```

We'll study this properly when we get to React state.

---

# 39. Rest Operator `...` ⭐⭐⭐⭐

The same `...` syntax can also be used as a **rest parameter**.

Example:

```js
function add(...numbers) {
    console.log(numbers);
}

add(10, 20, 30);
```

Output:

```text
[10, 20, 30]
```

Here:

```text
...numbers
```

collects the remaining arguments into an array.

Important:

```text
Spread
→ expands

Rest
→ collects
```

---

# 40. Unary Operators

Unary operators operate on a single value.

Examples:

```text
typeof
!
++
--
+
-
```

Example:

```js
let value = "25";

console.log(typeof value);
```

Here:

```text
typeof
```

operates on one value.

---

# 41. Unary `+`

You may see:

```js
const value = "25";

console.log(+value);
```

Output:

```text
25
```

It converts the string to a number.

Similarly:

```js
console.log(+"100");
```

→ `100`

This is valid JavaScript but for beginner code, using:

```js
Number(value)
```

is often clearer.

---

# 42. Operator Precedence ⭐⭐⭐

What happens here?

```js
console.log(10 + 5 * 2);
```

Is it:

```text
(10 + 5) × 2 = 30
```

or:

```text
10 + (5 × 2) = 20
```

The answer is:

```text
20
```

Because multiplication has higher precedence than addition.

Use parentheses when you want to make the intention clear:

```js
console.log((10 + 5) * 2);
```

Output:

```text
30
```

For interviews and real code, don't rely too heavily on memorizing every precedence rule—use parentheses when the expression could be confusing.

---

# 43. Bitwise Operators

JavaScript also has bitwise operators:

```text
&
|
^
~
<<
>>
>>>
```

Example:

```js
console.log(5 & 1);
```

These work with binary representations of numbers.

For React/frontend interviews, these are **low priority**.

Know that they exist, but don't spend significant time here now.

---

# 44. Important Operator Truth Table

For logical operators, remember:

### AND `&&`

```text
true  && true  → true
true  && false → false
false && true  → false
false && false → false
```

### OR `||`

```text
true  || true  → true
true  || false → true
false || true  → true
false || false → false
```

### NOT `!`

```text
!true  → false
!false → true
```

---

# 45. A very important JavaScript behavior ⭐⭐⭐⭐⭐

Logical operators don't necessarily return `true` or `false`.

For example:

```js
console.log("Sai" && "React");
```

Output:

```text
React
```

And:

```js
console.log("" && "React");
```

Output:

```text
""
```

Similarly:

```js
console.log("Sai" || "Guest");
```

Output:

```text
Sai
```

This is because `&&` and `||` return one of their operands based on short-circuit evaluation.

This becomes very useful in React.

---

# 46. Real React Example

Imagine:

```js
const isLoggedIn = true;
const userName = "Sai";
```

You can do:

```jsx
{isLoggedIn && <h1>Welcome {userName}</h1>}
```

Or:

```jsx
{isLoggedIn ? (
    <Dashboard />
) : (
    <Login />
)}
```

And with API data:

```jsx
<p>{user?.profile?.name ?? "Guest"}</p>
```

Here you're combining three JavaScript concepts:

```text
?.  → Optional chaining
??  → Nullish coalescing
```

These are **very important modern JavaScript features for React**.

---

# 47. ⭐ Operators You MUST Know for Interviews

Focus on these first:

### Arithmetic

```text
+
-
*
/
%
**
```

### Assignment

```text
=
+=
-=
*=
/=
%=
```

### Comparison

```text
==
===
!=
!==
>
<
>=
<=
```

### Logical

```text
&&
||
!
```

### Increment / Decrement

```text
++
--
```

### Modern JavaScript

```text
?:
??
?.
...
```

---

# 48. Most Important Interview Questions

### Q1. What is the difference between `==` and `===`?

```text
==  → loose equality, allows type coercion
=== → strict equality, checks type and value
```

Prefer `===` in most modern code.

---

### Q2. Difference between `&&` and `||`?

```text
&& → requires both sides to be truthy for a truthy result

|| → returns the first truthy value, otherwise the last value
```

---

### Q3. What is the ternary operator?

A shorthand for a simple conditional expression:

```js
condition ? value1 : value2
```

---

### Q4. Difference between `??` and `||`?

```text
?? → fallback only for null/undefined

|| → fallback for falsy values
```

For example:

```js
0 ?? 10  // 0
0 || 10  // 10
```

---

### Q5. What is optional chaining?

```js
user?.name
```

It safely accesses a property when the object may be `null` or `undefined`.

---

### Q6. What is the spread operator?

It expands elements/properties.

```js
const newArray = [...oldArray, 4];
```

```js
const newUser = {
    ...user,
    age: 26
};
```

---

### Q7. What is the rest operator?

It collects remaining values.

```js
function add(...numbers) {
    // numbers is an array
}
```

---

### Q8. Difference between `x++` and `++x`?

```text
x++ → return/use current value, then increment

++x → increment first, then return/use value
```

---

# 🧠 Practice Questions

Try these **without running the code first**.

### 1.

```js
console.log(10 + 5 * 2);
```

What is the output?

---

### 2.

```js
console.log(5 == "5");
console.log(5 === "5");
```

What are the outputs?

---

### 3.

```js
let x = 10;

x += 5;

console.log(x);
```

---

### 4.

```js
console.log(10 > 5 && 10 < 20);
```

---

### 5.

```js
console.log(false || "Hello");
```

---

### 6.

```js
console.log(true && "React");
```

---

### 7.

```js
const age = 20;

const result = age >= 18 ? "Adult" : "Minor";

console.log(result);
```

---

### 8.

```js
const value = 0;

console.log(value || 100);
console.log(value ?? 100);
```

Pay special attention to why the two outputs differ.

---

### 9.

```js
const user = null;

console.log(user?.name);
```

What happens?

---

### 10. ⭐ Interview-level

What is the output?

```js
let x = 5;

let y = x++;

console.log(x);
console.log(y);
```

And compare it with:

```js
let x = 5;

let y = ++x;

console.log(x);
console.log(y);
```

---

# 🎯 What to master before moving on

You don't need to memorize every operator. Make sure you can **explain and use** these confidently:

```text
                    OPERATORS
                       │
       ┌───────────────┼────────────────┐
       ↓               ↓                ↓
   Arithmetic      Comparison         Logical
       │               │                │
   + - * / %       == === != !==      && || !
       │               │                │
       └───────────────┼────────────────┘
                       ↓
                 Conditional
                       │
                      ?:
                       │
                       ↓
              Modern JavaScript
                 /          \
                ??          ?.
                │            │
             fallback    safe access
                       │
                       ↓
                    Spread
                       ...
                       │
                       ↓
                  React State
```

### 🔥 Especially remember these 6:

```js
===   // strict comparison
&&    // AND / conditional rendering
||    // OR / fallback
?:    // ternary
??    // null/undefined fallback
?.    // safe property access
```
