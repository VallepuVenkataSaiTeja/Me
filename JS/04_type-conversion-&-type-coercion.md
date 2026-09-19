# 4. Type Conversion & Type Coercion ⭐⭐⭐⭐⭐

This is a **very important JavaScript interview topic**, especially for React, because JavaScript frequently works with values coming from forms, APIs, local storage, URLs, etc.

The main thing you need to understand is:

> **Type Conversion = changing a value's type intentionally.**
> **Type Coercion = JavaScript automatically changing a value's type.**

---

# 1. What is Type Conversion?

Type conversion means **converting one data type into another**.

For example:

```javascript
let age = "25";

console.log(typeof age);
// string

let newAge = Number(age);

console.log(typeof newAge);
// number
```

We manually converted:

```text
"25" → 25
string → number
```

This is called **explicit type conversion**.

---

# 2. What is Type Coercion?

Type coercion happens when **JavaScript automatically converts one type into another** to perform an operation.

Example:

```javascript
let result = "10" + 5;

console.log(result);
```

Output:

```text
105
```

Why?

Because JavaScript sees:

```text
"10" → string
5    → number
```

With `+`, JavaScript converts the number to a string:

```text
"10" + "5"
```

Result:

```text
"105"
```

This is **type coercion**.

---

# 3. Conversion vs Coercion

| Type            | Who performs conversion? | Example        |
| --------------- | ------------------------ | -------------- |
| Type Conversion | You                      | `Number("10")` |
| Type Coercion   | JavaScript               | `"10" - 5`     |

### Conversion

```javascript
Number("10");
```

You explicitly tell JavaScript:

> Convert this string into a number.

### Coercion

```javascript
"10" - 5;
```

JavaScript automatically converts `"10"` to `10`.

---

# 4. Explicit Type Conversion

The most important conversion functions are:

```javascript
String()
Number()
Boolean()
```

Let's understand each one.

---

# 5. String Conversion

You can convert a value to a string using:

```javascript
String()
```

Example:

```javascript
let number = 100;

let result = String(number);

console.log(result);
console.log(typeof result);
```

Output:

```text
100
string
```

The number:

```text
100
```

became:

```text
"100"
```

---

## More examples

```javascript
String(100);
```

Result:

```text
"100"
```

```javascript
String(true);
```

Result:

```text
"true"
```

```javascript
String(false);
```

Result:

```text
"false"
```

```javascript
String(null);
```

Result:

```text
"null"
```

```javascript
String(undefined);
```

Result:

```text
"undefined"
```

---

# 6. Number Conversion

Use:

```javascript
Number()
```

Example:

```javascript
let value = "100";

let result = Number(value);

console.log(result);
console.log(typeof result);
```

Output:

```text
100
number
```

So:

```text
"100" → 100
```

---

## Important Number conversions

### String containing a number

```javascript
Number("100");
```

Output:

```text
100
```

---

### Decimal string

```javascript
Number("10.5");
```

Output:

```text
10.5
```

---

### Empty string

```javascript
Number("");
```

Output:

```text
0
```

This is a common interview question.

---

### Space

```javascript
Number(" ");
```

Output:

```text
0
```

---

### Invalid number

```javascript
Number("hello");
```

Output:

```text
NaN
```

`NaN` means:

> **Not a Number**

---

### Boolean

```javascript
Number(true);
```

Output:

```text
1
```

And:

```javascript
Number(false);
```

Output:

```text
0
```

So:

```text
true  → 1
false → 0
```

---

### null

```javascript
Number(null);
```

Output:

```text
0
```

---

### undefined

```javascript
Number(undefined);
```

Output:

```text
NaN
```

---

# 7. Important Number Conversion Table

| Value       | `Number(value)` |
| ----------- | --------------: |
| `"100"`     |           `100` |
| `"10.5"`    |          `10.5` |
| `""`        |             `0` |
| `" "`       |             `0` |
| `"hello"`   |           `NaN` |
| `true`      |             `1` |
| `false`     |             `0` |
| `null`      |             `0` |
| `undefined` |           `NaN` |

This table is worth remembering for interviews.

---

# 8. Boolean Conversion

Use:

```javascript
Boolean()
```

Example:

```javascript
Boolean(1);
```

Output:

```text
true
```

```javascript
Boolean(0);
```

Output:

```text
false
```

JavaScript has a concept called:

# Truthy and Falsy

This is extremely important.

---

# 9. Falsy Values

A **falsy value** is a value that JavaScript treats as `false` when used in a boolean context.

The important falsy values are:

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

For example:

```javascript
if (0) {
    console.log("Hello");
}
```

Nothing happens because:

```javascript
Boolean(0)
```

is:

```text
false
```

---

## Another example

```javascript
if ("") {
    console.log("Hello");
}
```

Nothing happens because an empty string is falsy.

---

# 10. Truthy Values

Everything that is not falsy is generally **truthy**.

Examples:

```javascript
Boolean(1);
// true

Boolean(-1);
// true

Boolean("hello");
// true

Boolean("0");
// true

Boolean("false");
// true

Boolean([]);
// true

Boolean({});
// true
```

### Important interview trap

Look at this:

```javascript
Boolean("false");
```

Result:

```text
true
```

Why?

Because `"false"` is a **non-empty string**.

It doesn't matter that the text says `"false"`.

---

# 11. Empty Array is Truthy

This surprises many beginners:

```javascript
Boolean([]);
```

Output:

```text
true
```

And:

```javascript
Boolean({});
```

Output:

```text
true
```

So don't think:

```text
empty = false
```

That's not how JavaScript works.

An empty array and empty object are still objects, and objects are truthy.

---

# 12. Type Coercion

Now let's understand automatic conversion.

JavaScript sometimes converts values automatically when operators are used.

---

# 13. `+` Operator and Coercion

Consider:

```javascript
let result = "5" + 2;

console.log(result);
```

Output:

```text
52
```

Why?

Because `+` can mean:

1. Addition
2. String concatenation

When one side is a string, JavaScript often converts the other value to a string.

So:

```javascript
"5" + 2
```

becomes:

```javascript
"5" + "2"
```

Result:

```text
"52"
```

---

# 14. `-` Operator

Now look at:

```javascript
let result = "5" - 2;

console.log(result);
```

Output:

```text
3
```

Why?

The `-` operator is numeric.

JavaScript converts:

```text
"5" → 5
```

Then:

```text
5 - 2
```

Result:

```text
3
```

---

# 15. `*` Operator

```javascript
"5" * 2
```

Output:

```text
10
```

JavaScript converts:

```text
"5" → 5
```

Then:

```text
5 * 2
```

---

# 16. `/` Operator

```javascript
"10" / 2
```

Output:

```text
5
```

Again:

```text
"10" → 10
```

Then:

```text
10 / 2
```

---

# 17. Very Important Interview Example

```javascript
console.log("5" + 2);
console.log("5" - 2);
console.log("5" * 2);
console.log("5" / 2);
```

Output:

```text
52
3
10
2.5
```

Remember:

```text
"5" + 2  → "52"
"5" - 2  → 3
"5" * 2  → 10
"5" / 2  → 2.5
```

This is a classic JavaScript interview question.

---

# 18. `==` and Type Coercion

This connects directly to the previous topic on operators.

`==` is called **loose equality**.

It can perform type coercion.

Example:

```javascript
5 == "5"
```

Result:

```text
true
```

Why?

JavaScript converts:

```text
"5" → 5
```

Then compares:

```text
5 == 5
```

So:

```text
true
```

---

# 19. `===` Does Not Perform This Coercion

Consider:

```javascript
5 === "5"
```

Result:

```text
false
```

Because:

```text
5     → number
"5"   → string
```

Different types.

Therefore:

```javascript
5 === "5"
// false
```

---

# 20. `==` vs `===`

| Operator | Type coercion | Recommended   |
| -------- | ------------- | ------------- |
| `==`     | Yes           | Usually avoid |
| `===`    | No            | Yes           |

For modern JavaScript and React, generally prefer:

```javascript
===
```

instead of:

```javascript
==
```

---

# 21. Important `==` Interview Examples

These are famous JavaScript interview questions.

### Example 1

```javascript
5 == "5"
```

Result:

```text
true
```

But:

```javascript
5 === "5"
```

Result:

```text
false
```

---

### Example 2

```javascript
true == 1
```

Result:

```text
true
```

Because:

```text
true → 1
```

---

### Example 3

```javascript
false == 0
```

Result:

```text
true
```

Because:

```text
false → 0
```

---

### Example 4

```javascript
"" == 0
```

Result:

```text
true
```

The empty string is converted to `0` in this comparison.

---

### Example 5

```javascript
null == undefined
```

Result:

```text
true
```

This is a special rule of loose equality.

But:

```javascript
null === undefined
```

Result:

```text
false
```

---

### Example 6

```javascript
null == 0
```

Result:

```text
false
```

This is another common interview trap.

Do not assume:

```text
null → 0
```

for every operation involving `==`.

---

# 22. `NaN`

`NaN` means:

> Not a Number

Example:

```javascript
let result = Number("hello");

console.log(result);
```

Output:

```text
NaN
```

But there's an interesting fact:

```javascript
typeof NaN
```

returns:

```text
"number"
```

Yes, that's strange.

`NaN` is technically a special numeric value in JavaScript.

---

# 23. Checking for `NaN`

Use:

```javascript
Number.isNaN()
```

Example:

```javascript
let value = Number("hello");

console.log(Number.isNaN(value));
```

Output:

```text
true
```

Another:

```javascript
console.log(Number.isNaN(100));
```

Output:

```text
false
```

---

# 24. `parseInt()`

`parseInt()` converts a string into an integer.

Example:

```javascript
parseInt("100");
```

Result:

```text
100
```

Decimal:

```javascript
parseInt("10.99");
```

Result:

```text
10
```

It extracts the integer portion.

---

# 25. `parseFloat()`

`parseFloat()` can preserve decimal values.

```javascript
parseFloat("10.99");
```

Result:

```text
10.99
```

---

# 26. `Number()` vs `parseInt()`

This is an important distinction.

```javascript
Number("123px");
```

Result:

```text
NaN
```

But:

```javascript
parseInt("123px");
```

Result:

```text
123
```

Why?

`Number()` expects the **whole value** to represent a valid number.

`parseInt()` reads the integer from the beginning until the numeric part ends.

Similarly:

```javascript
parseFloat("10.50px");
```

Result:

```text
10.5
```

---

# 27. Example: User Input in React

This topic becomes especially important in React forms.

Suppose you have:

```jsx
<input type="number" />
```

You might expect the value to automatically be a number.

But input values are commonly received as **strings**.

For example:

```javascript
let age = event.target.value;

console.log(typeof age);
```

You may get:

```text
string
```

Even if the user entered:

```text
25
```

The value can be:

```text
"25"
```

So you might convert it:

```javascript
let age = Number(event.target.value);
```

Now:

```text
"25" → 25
```

This is something you'll use frequently in React forms.

---

# 28. Local Storage Example

Another React-related example is `localStorage`.

Suppose:

```javascript
localStorage.setItem("age", 25);
```

When you retrieve it:

```javascript
let age = localStorage.getItem("age");

console.log(age);
console.log(typeof age);
```

You'll get:

```text
25
string
```

Why?

Because local storage stores data as strings.

So:

```javascript
let age = Number(localStorage.getItem("age"));
```

converts it back to a number.

---

# 29. API Data

Suppose an API gives you:

```javascript
{
    age: "25"
}
```

You might need:

```javascript
let age = Number(data.age);
```

to work with it as a number.

Or you might receive:

```javascript
{
    name: null
}
```

This is where understanding:

```javascript
null
undefined
```

and:

```javascript
??
```

becomes important.

For example:

```javascript
let name = data.name ?? "Guest";
```

If:

```javascript
data.name === null
```

or:

```javascript
data.name === undefined
```

then:

```text
Guest
```

is used.

---

# 30. `||` vs `??`

This is another important React interview concept.

Consider:

```javascript
let count = 0;

console.log(count || 10);
```

Output:

```text
10
```

Why?

Because `0` is falsy.

But:

```javascript
console.log(count ?? 10);
```

Output:

```text
0
```

Because `??` only checks:

```text
null
undefined
```

### Remember

```javascript
0 || 10
// 10
```

But:

```javascript
0 ?? 10
// 0
```

This is very useful when `0` is a valid value.

---

# 31. Truthy/Falsy in React

You will frequently see:

```jsx
{isLoggedIn && <Dashboard />}
```

If:

```javascript
isLoggedIn = true
```

then:

```jsx
<Dashboard />
```

is displayed.

If:

```javascript
isLoggedIn = false
```

then the component isn't displayed.

Why does this work?

Because React/JavaScript uses the truthy/falsy behavior of:

```javascript
&&
```

---

# 32. Another React Example

Suppose:

```javascript
const username = "";
```

You might write:

```jsx
{username || "Guest"}
```

Since:

```text
"" → falsy
```

the result is:

```text
Guest
```

But if:

```javascript
const count = 0;
```

and you write:

```jsx
{count || "No count"}
```

you'll get:

```text
No count
```

even though `0` may be a valid value.

Instead:

```jsx
{count ?? "No count"}
```

gives:

```text
0
```

---

# 33. Common Type Coercion Traps

These are worth practicing.

### 1

```javascript
console.log("10" + 5);
```

Output:

```text
105
```

---

### 2

```javascript
console.log("10" - 5);
```

Output:

```text
5
```

---

### 3

```javascript
console.log(true + 1);
```

Output:

```text
2
```

Because:

```text
true → 1
```

---

### 4

```javascript
console.log(false + 1);
```

Output:

```text
1
```

Because:

```text
false → 0
```

---

### 5

```javascript
console.log(null + 1);
```

Output:

```text
1
```

In numeric context:

```text
null → 0
```

---

### 6

```javascript
console.log(undefined + 1);
```

Output:

```text
NaN
```

Because:

```text
undefined → NaN
```

---

# 34. Very Important: `"0"` vs `0`

Look at:

```javascript
Boolean(0);
```

Result:

```text
false
```

But:

```javascript
Boolean("0");
```

Result:

```text
true
```

Why?

Because:

```text
0
```

is the number zero → falsy.

But:

```text
"0"
```

is a non-empty string → truthy.

This is a **very common interview trap**.

---

# 35. Very Important: `"false"` vs `false`

```javascript
Boolean(false);
```

Result:

```text
false
```

But:

```javascript
Boolean("false");
```

Result:

```text
true
```

Again:

```text
false
```

is a boolean.

While:

```text
"false"
```

is a non-empty string.

---

# 36. A Simple Mental Model

When you see JavaScript code, ask:

### Step 1

**What are the original types?**

```javascript
"5" + 2
```

Types:

```text
string + number
```

### Step 2

**What operator is being used?**

```text
+
```

### Step 3

**Does the operator cause coercion?**

Yes.

### Step 4

**What types will JavaScript convert?**

```text
2 → "2"
```

### Step 5

Final operation:

```javascript
"5" + "2"
```

Result:

```text
"52"
```

This approach will help you solve interview questions instead of memorizing hundreds of examples.

---

# 37. Explicit vs Implicit Conversion

### Explicit

You manually convert:

```javascript
let age = "25";

age = Number(age);
```

You are saying:

> Convert this value to a number.

### Implicit

JavaScript automatically converts:

```javascript
let result = "25" - 5;
```

JavaScript decides:

```text
"25" → 25
```

---

# 38. Most Important Conversion Functions

| Function       | Purpose            | Example              | Result  |
| -------------- | ------------------ | -------------------- | ------- |
| `String()`     | Convert to string  | `String(100)`        | `"100"` |
| `Number()`     | Convert to number  | `Number("100")`      | `100`   |
| `Boolean()`    | Convert to boolean | `Boolean(1)`         | `true`  |
| `parseInt()`   | Parse integer      | `parseInt("10.5")`   | `10`    |
| `parseFloat()` | Parse decimal      | `parseFloat("10.5")` | `10.5`  |

---

# 39. Interview Questions You Must Know

### Q1. What is type conversion?

**Answer:**

Type conversion is the process of converting a value from one data type to another, either explicitly or implicitly.

Example:

```javascript
Number("10");
```

---

### Q2. What is type coercion?

**Answer:**

Type coercion is JavaScript's automatic conversion of one data type into another when performing certain operations.

Example:

```javascript
"10" - 5
```

JavaScript converts `"10"` to `10`.

---

### Q3. Difference between conversion and coercion?

```text
Conversion → developer explicitly converts
Coercion   → JavaScript automatically converts
```

---

### Q4. What is the output?

```javascript
console.log("5" + 2);
```

Answer:

```text
"52"
```

---

### Q5. What is the output?

```javascript
console.log("5" - 2);
```

Answer:

```text
3
```

---

### Q6. What is the output?

```javascript
console.log(true + true);
```

Answer:

```text
2
```

Because:

```text
true → 1
true → 1

1 + 1 = 2
```

---

### Q7. What is the output?

```javascript
console.log(Boolean("false"));
```

Answer:

```text
true
```

Because `"false"` is a non-empty string.

---

### Q8. What is the output?

```javascript
console.log(Boolean([]));
```

Answer:

```text
true
```

An empty array is truthy.

---

### Q9. What is the output?

```javascript
console.log(5 == "5");
console.log(5 === "5");
```

Answer:

```text
true
false
```

---

### Q10. What is the output?

```javascript
console.log(null == undefined);
console.log(null === undefined);
```

Answer:

```text
true
false
```

---

# 40. Coding Practice

Try answering these **without running the code first**.

### Practice 1

```javascript
console.log(Number("50"));
```

### Practice 2

```javascript
console.log(Number("hello"));
```

### Practice 3

```javascript
console.log(String(100));
```

### Practice 4

```javascript
console.log(Boolean(0));
```

### Practice 5

```javascript
console.log(Boolean("0"));
```

### Practice 6

```javascript
console.log("10" + 20);
```

### Practice 7

```javascript
console.log("10" - 20);
```

### Practice 8

```javascript
console.log(true + false);
```

### Practice 9

```javascript
console.log(10 == "10");
```

### Practice 10

```javascript
console.log(10 === "10");
```

### Practice 11

```javascript
console.log(null == undefined);
```

### Practice 12

```javascript
console.log(null === undefined);
```

### Practice 13

```javascript
console.log(Number(""));
```

### Practice 14

```javascript
console.log(Number("100px"));
```

### Practice 15

```javascript
console.log(parseInt("100px"));
```

---

# ⭐ What You Should Remember for React Interviews

Don't try to memorize every strange coercion rule. Focus heavily on these:

```text
1. Explicit vs implicit conversion
2. String()
3. Number()
4. Boolean()
5. Truthy and falsy values
6. == vs ===
7. "5" + 2
8. "5" - 2
9. NaN
10. Number.isNaN()
11. parseInt()
12. parseFloat()
13. null vs undefined
14. || vs ??
15. Form input values are commonly strings
```

### The core idea

```text
TYPE CONVERSION
        ↓
You explicitly change the type
        ↓
Number("10")
        ↓
10
```

```text
TYPE COERCION
        ↓
JavaScript automatically changes the type
        ↓
"10" - 5
        ↓
10 - 5
        ↓
5
```