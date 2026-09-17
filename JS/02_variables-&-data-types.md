# 2. Variables & Data Types ⭐⭐⭐⭐⭐

This is one of the **most important JavaScript topics for React and interviews**.

You should become very comfortable with:

```text
Variables
   ↓
var / let / const
   ↓
Data Types
   ↓
typeof
   ↓
Primitive vs Reference
   ↓
Mutable vs Immutable
   ↓
Type behavior
```

---

# 1. What is a Variable?

A **variable is a named place/reference used to store a value** so we can use that value later in our program.

Example:

```js
let name = "Sai";
```

Here:

```text
let       → keyword
name      → variable name
"Sai"     → value
=         → assignment operator
```

We can then use the variable:

```js
console.log(name);
```

Output:

```text
Sai
```

Another example:

```js
let age = 25;
let city = "Kadapa";

console.log(age);
console.log(city);
```

Output:

```text
25
Kadapa
```

---

# 2. Why do we need variables?

Imagine you are building a student application.

You might need to store:

```text
Student name
Email
Age
Mobile number
Marks
Course
Login status
```

Without variables, you would have to repeatedly write the values.

Instead:

```js
let studentName = "Sai";
let email = "sai@example.com";
let age = 25;
let marks = 85;
```

Now you can reuse them:

```js
console.log(studentName);
console.log(email);
console.log(age);
console.log(marks);
```

In React, you'll constantly work with values like:

```js
const userName = "Sai";
const isLoggedIn = true;
const products = [];
const user = {};
```

So understanding variables is essential.

---

# 3. `var`, `let`, and `const` ⭐⭐⭐⭐⭐

JavaScript provides three keywords for declaring variables:

```js
var
let
const
```

Example:

```js
var name = "Sai";

let age = 25;

const country = "India";
```

All three create variables, but they behave differently.

---

# 4. `var`

`var` is the older way of declaring variables.

```js
var name = "Sai";

console.log(name);
```

Output:

```text
Sai
```

You can change it:

```js
var age = 25;

age = 26;

console.log(age);
```

Output:

```text
26
```

You can also redeclare it:

```js
var name = "Sai";

var name = "John";

console.log(name);
```

Output:

```text
John
```

This behavior is one reason modern JavaScript generally prefers `let` and `const`.

---

# 5. `let`

`let` is the modern way to declare a variable when its value may change.

```js
let age = 25;

age = 26;

console.log(age);
```

Output:

```text
26
```

But you cannot redeclare the same variable in the same scope:

```js
let name = "Sai";

let name = "John";
```

❌ This causes an error.

You can, however, reassign it:

```js
let name = "Sai";

name = "John";
```

✅ Valid.

---

# 6. `const`

`const` is used when the variable binding should not be reassigned.

```js
const country = "India";

console.log(country);
```

You cannot do:

```js
const country = "India";

country = "USA";
```

❌ Error.

So:

```text
let   → can reassign
const → cannot reassign
```

---

# 7. `var` vs `let` vs `const` ⭐⭐⭐⭐⭐

This is a **very common interview question**.

| Feature                      | `var`      | `let` | `const` |
| ---------------------------- | ---------- | ----- | ------- |
| Can reassign?                | Yes        | Yes   | No      |
| Can redeclare in same scope? | Yes        | No    | No      |
| Function scoped?             | Yes        | No    | No      |
| Block scoped?                | No         | Yes   | Yes     |
| Modern preferred usage       | Usually no | Yes   | Yes     |

For modern JavaScript:

```text
Use const by default.
Use let when the value needs to change.
Avoid var in modern code unless you specifically need its behavior.
```

Example:

```js
const name = "Sai";

let age = 25;

age = 26;
```

This is the pattern you'll see frequently in React.

---

# 8. What is Block Scope?

A block is code inside:

```js
{
    // block
}
```

For example:

```js
if (true) {
    let name = "Sai";
}
```

The `let` variable exists only inside that block.

```js
if (true) {
    let name = "Sai";

    console.log(name); // Sai
}

console.log(name); // Error
```

The variable isn't available outside the block.

The same applies to `const`.

---

# 9. `var` is NOT block scoped

Consider:

```js
if (true) {
    var name = "Sai";
}

console.log(name);
```

Output:

```text
Sai
```

`var` is function-scoped rather than block-scoped.

This difference is important:

```text
var
→ function scope

let
→ block scope

const
→ block scope
```

---

# 10. Function Scope

Example:

```js
function test() {
    var name = "Sai";

    console.log(name);
}
```

`name` is available inside the function.

But:

```js
function test() {
    var name = "Sai";
}

console.log(name);
```

❌ Error.

Because `name` belongs to the function scope.

We'll study **scope** in much greater detail later.

---

# 11. Important `const` misunderstanding ⭐⭐⭐⭐⭐

A very common interview trap:

> Does `const` make an object immutable?

**No.**

Consider:

```js
const student = {
    name: "Sai",
    age: 25
};
```

You cannot do:

```js
student = {};
```

❌ You cannot reassign the variable.

But you **can modify properties**:

```js
student.age = 26;
```

✅ This is allowed.

Now:

```js
console.log(student);
```

Output:

```js
{
    name: "Sai",
    age: 26
}
```

So `const` prevents **reassignment of the binding**, not necessarily mutation of the object.

This becomes extremely important when working with **React state and Redux**.

---

# 12. Arrays with `const`

Same concept.

```js
const numbers = [1, 2, 3];
```

You cannot:

```js
numbers = [4, 5, 6];
```

❌

But you can modify the array:

```js
numbers.push(4);
```

Now:

```js
console.log(numbers);
```

Output:

```text
[1, 2, 3, 4]
```

Later, when we study React, we'll learn why we generally prefer creating a **new array/object** rather than directly mutating state.

---

# 13. Data Types ⭐⭐⭐⭐⭐

A **data type tells JavaScript what kind of value something is**.

For example:

```js
let name = "Sai";
```

`name` contains a string.

```js
let age = 25;
```

`age` contains a number.

```js
let isStudent = true;
```

`isStudent` contains a boolean.

JavaScript has several data types.

---

# 14. JavaScript Data Types

The main types can be grouped as:

```text
Data Types
│
├── Primitive
│   ├── String
│   ├── Number
│   ├── BigInt
│   ├── Boolean
│   ├── Undefined
│   ├── Null
│   └── Symbol
│
└── Non-Primitive / Reference
    ├── Object
    ├── Array
    └── Function
```

Let's understand each.

---

# 15. String ⭐⭐⭐

A string represents text.

```js
let name = "Sai";
```

You can use:

```js
"Hello"
```

or:

```js
'Hello'
```

or template literals:

```js
`Hello`
```

Example:

```js
const firstName = "Sai";
const city = "Kadapa";

console.log(firstName);
console.log(city);
```

---

# 16. Number ⭐⭐⭐

JavaScript uses the `number` type for normal numeric values.

```js
let age = 25;
let price = 99.99;
let temperature = -10;
```

All are:

```text
Number
```

Example:

```js
console.log(typeof 25);
```

Output:

```text
number
```

JavaScript's `number` type represents both integers and floating-point numbers.

---

# 17. Boolean ⭐⭐⭐

Boolean has only two values:

```js
true
false
```

Example:

```js
let isLoggedIn = true;

let isAdmin = false;
```

Booleans are extremely common in React.

For example:

```js
const isLoading = true;
```

Then the UI might display:

```text
Loading...
```

---

# 18. Undefined ⭐⭐⭐

A variable can exist without having a value assigned to it.

```js
let name;

console.log(name);
```

Output:

```text
undefined
```

So:

```text
Variable exists
      ↓
No value assigned
      ↓
undefined
```

Another example:

```js
let age;

console.log(typeof age);
```

Output:

```text
undefined
```

---

# 19. Null ⭐⭐⭐⭐

`null` represents an intentional absence of a value.

Example:

```js
let selectedUser = null;
```

This can mean:

> There is currently no selected user.

Later:

```js
selectedUser = {
    name: "Sai"
};
```

So:

```text
undefined
→ value hasn't been assigned

null
→ intentionally no value
```

This distinction is important in JavaScript interviews.

---

# 20. `null` vs `undefined` ⭐⭐⭐⭐⭐

This is a very common interview question.

### Undefined

```js
let value;
```

JavaScript gives:

```text
undefined
```

### Null

```js
let value = null;
```

You intentionally assign:

```text
null
```

Think:

```text
undefined
→ JavaScript doesn't currently have a value

null
→ programmer intentionally says "no value"
```

There is also a famous JavaScript oddity:

```js
typeof null
```

returns:

```text
"object"
```

This is a historical behavior of JavaScript.

Even though `null` is a primitive value.

---

# 21. BigInt ⭐⭐

`BigInt` is used for integers larger than the safe range of JavaScript's normal `Number` type.

Example:

```js
const bigNumber = 123456789012345678901234567890n;
```

Notice the:

```text
n
```

at the end.

You can check:

```js
console.log(typeof bigNumber);
```

Output:

```text
bigint
```

For normal React development, you won't use BigInt frequently, but you should know what it is.

---

# 22. Symbol ⭐⭐

`Symbol` creates a unique value.

Example:

```js
const id1 = Symbol("id");
const id2 = Symbol("id");
```

Even though both have `"id"` as their description:

```js
console.log(id1 === id2);
```

Output:

```text
false
```

Because every Symbol is unique.

Symbol is an advanced JavaScript feature. Know the concept, but don't prioritize it over arrays, objects, functions, promises, etc.

---

# 23. Object ⭐⭐⭐⭐⭐

An object stores data in **key-value pairs**.

Example:

```js
const student = {
    name: "Sai",
    age: 25,
    course: "React"
};
```

Here:

```text
name   → "Sai"
age    → 25
course → "React"
```

You can access values:

```js
console.log(student.name);
```

Output:

```text
Sai
```

Or:

```js
console.log(student["age"]);
```

Output:

```text
25
```

Objects are extremely important in React.

You'll use them for:

```text
Props
State
API responses
Configuration
User data
Redux state
```

---

# 24. Array ⭐⭐⭐⭐⭐

An array stores an ordered collection of values.

```js
const fruits = ["Apple", "Banana", "Mango"];
```

Access values using indexes:

```js
console.log(fruits[0]);
```

Output:

```text
Apple
```

```js
console.log(fruits[1]);
```

Output:

```text
Banana
```

JavaScript arrays can contain different types:

```js
const data = [
    "Sai",
    25,
    true,
    null
];
```

Although technically allowed, in real applications it's usually better for an array to have a meaningful consistent structure.

---

# 25. Function ⭐⭐⭐⭐⭐

Functions are also values in JavaScript.

Example:

```js
function greet() {
    console.log("Hello");
}
```

You can call it:

```js
greet();
```

Functions are extremely important because React components are commonly functions:

```js
function App() {
    return <h1>Hello</h1>;
}
```

So your JavaScript understanding of functions will directly affect your React learning.

---

# 26. Primitive vs Reference Types ⭐⭐⭐⭐⭐

This is one of the most important JavaScript concepts.

### Primitive values

The commonly discussed primitive types are:

```text
String
Number
Boolean
Undefined
Null
BigInt
Symbol
```

They represent individual values.

Example:

```js
let a = 10;
let b = a;

b = 20;

console.log(a);
console.log(b);
```

Output:

```text
10
20
```

Changing `b` doesn't change `a`.

---

# 27. Objects behave differently

Consider:

```js
const user1 = {
    name: "Sai"
};

const user2 = user1;
```

Now:

```js
user2.name = "John";
```

What is:

```js
console.log(user1.name);
```

?

Output:

```text
John
```

Why?

Because `user1` and `user2` refer to the **same object**.

Conceptually:

```text
user1 ─────┐
           ↓
       { name: "Sai" }
           ↑
user2 ─────┘
```

After:

```js
user2.name = "John";
```

both references see:

```text
{ name: "John" }
```

This concept becomes very important for **React state**.

---

# 28. Primitive copying vs object references

Compare these.

### Primitive

```js
let a = 10;
let b = a;

b = 20;
```

Conceptually:

```text
a → 10

b → 10

b changes → 20

a → 10
```

### Object

```js
const a = {
    name: "Sai"
};

const b = a;
```

Conceptually:

```text
a ────┐
      ↓
   Object
      ↑
b ────┘
```

Both refer to the same object.

---

# 29. Mutable vs Immutable ⭐⭐⭐⭐⭐

### Mutable

Something can be changed after creation.

Objects and arrays are mutable by default.

Example:

```js
const user = {
    name: "Sai"
};

user.name = "John";
```

The object changed.

---

### Immutable

The existing value isn't modified; instead, a new value is created.

For example:

```js
const user = {
    name: "Sai"
};

const updatedUser = {
    ...user,
    name: "John"
};
```

Now:

```text
user
→ { name: "Sai" }

updatedUser
→ { name: "John" }
```

This concept is **very important in React and Redux**.

---

# 30. `typeof` Operator ⭐⭐⭐⭐⭐

`typeof` tells you the type of a value.

Example:

```js
console.log(typeof "Hello");
```

Output:

```text
string
```

```js
console.log(typeof 25);
```

Output:

```text
number
```

```js
console.log(typeof true);
```

Output:

```text
boolean
```

```js
console.log(typeof undefined);
```

Output:

```text
undefined
```

---

# 31. `typeof` with objects

```js
const user = {
    name: "Sai"
};

console.log(typeof user);
```

Output:

```text
object
```

For arrays:

```js
const numbers = [1, 2, 3];

console.log(typeof numbers);
```

Surprisingly:

```text
object
```

Arrays are technically objects in JavaScript.

To properly check an array:

```js
Array.isArray(numbers);
```

Output:

```text
true
```

---

# 32. Important `typeof` interview question ⭐⭐⭐⭐⭐

What is:

```js
typeof null
```

?

Answer:

```text
"object"
```

This is a historical JavaScript quirk.

What about:

```js
typeof [];
```

?

```text
"object"
```

And:

```js
Array.isArray([]);
```

returns:

```text
true
```

---

# 33. Special Number values

JavaScript's `Number` type includes some special values.

### `NaN`

Means:

**Not-a-Number**

Example:

```js
console.log("hello" * 5);
```

Result:

```text
NaN
```

Interestingly:

```js
typeof NaN
```

returns:

```text
number
```

Again, a JavaScript quirk.

---

### Infinity

```js
console.log(10 / 0);
```

Result:

```text
Infinity
```

You can also have:

```text
-Infinity
```

---

# 34. Dynamic Typing ⭐⭐⭐⭐⭐

JavaScript is dynamically typed.

For example:

```js
let value = 10;
```

Initially:

```text
value → Number
```

Then:

```js
value = "Hello";
```

Now:

```text
value → String
```

Then:

```js
value = true;
```

Now:

```text
value → Boolean
```

The variable can hold different types during execution.

---

# 35. Static vs Dynamic Typing

### Static typing

Languages such as Java/C# commonly require explicit types.

Conceptually:

```text
int age = 25;
```

The type is explicitly declared.

### JavaScript

```js
let age = 25;
```

JavaScript determines the type from the value.

This is called:

**Dynamic typing.**

---

# 36. Type Conversion ⭐⭐⭐⭐

You'll frequently need to convert one type into another.

For example:

```js
const value = "25";
```

Currently it's a string.

You can convert it:

```js
const number = Number(value);
```

Now:

```text
number → 25
```

We'll study type conversion properly in the next topic on operators/type behavior.

---

# 37. A complete example

Let's combine variables and different data types:

```js
const name = "Sai";
let age = 25;
const isStudent = true;

let address = null;

let phone;

const skills = ["HTML", "CSS", "JavaScript"];

const user = {
    name: "Sai",
    age: 25
};

console.log(name);
console.log(age);
console.log(isStudent);
console.log(address);
console.log(phone);
console.log(skills);
console.log(user);
```

Here:

```text
name       → String
age        → Number
isStudent  → Boolean
address    → Null
phone      → Undefined
skills     → Array
user       → Object
```

---

# 38. ⭐ Interview Questions You Must Know

### 1. What is a variable?

A named reference used to store or refer to a value.

---

### 2. What are the three ways to declare variables?

```text
var
let
const
```

---

### 3. Difference between `var`, `let`, and `const`?

Remember:

```text
var
→ function scoped
→ can redeclare
→ can reassign

let
→ block scoped
→ cannot redeclare in same scope
→ can reassign

const
→ block scoped
→ cannot redeclare in same scope
→ cannot reassign
```

---

### 4. Does `const` make an object immutable?

**No.**

It prevents reassignment of the variable binding, but object properties can still be changed.

```js
const user = {
    name: "Sai"
};

user.name = "John"; // allowed
```

---

### 5. What are JavaScript primitive data types?

```text
String
Number
BigInt
Boolean
Undefined
Null
Symbol
```

---

### 6. Is Array a primitive type?

No.

Arrays are objects in JavaScript.

```js
typeof [];
```

returns:

```text
"object"
```

Use:

```js
Array.isArray([]);
```

to check for an array.

---

### 7. What is the difference between `null` and `undefined`?

```text
undefined
→ no value has been assigned / value is absent

null
→ intentional absence of a value
```

---

### 8. What does `typeof` do?

It returns a string indicating the type of a value.

Example:

```js
typeof "Sai";
```

→ `"string"`

---

### 9. Is JavaScript statically or dynamically typed?

JavaScript is **dynamically typed**.

---

### 10. What is the difference between primitive and reference values?

The key idea is that primitives behave as independent values when copied, while objects/arrays can have multiple variables referring to the same underlying object.

This is particularly important when modifying objects and arrays.

---

# 🎯 What you should practice now

Before moving to the next topic, try these yourself:

### Question 1

What will this print?

```js
let a = 10;
let b = a;

b = 20;

console.log(a);
console.log(b);
```

---

### Question 2

What will this print?

```js
const user1 = {
    name: "Sai"
};

const user2 = user1;

user2.name = "John";

console.log(user1.name);
```

---

### Question 3

What happens here?

```js
const age = 25;

age = 30;
```

---

### Question 4

What are the outputs?

```js
console.log(typeof "Hello");
console.log(typeof 100);
console.log(typeof true);
console.log(typeof undefined);
console.log(typeof null);
console.log(typeof []);
```

---

### Question 5

Which should you normally use?

```text
var
let
const
```

when:

**A.** The value never needs reassignment
**B.** The value needs reassignment
**C.** Modern JavaScript code in general

---

## 🔥 Most important takeaway

For your **React interview preparation**, remember this hierarchy:

```text
                Variables & Data Types
                         │
          ┌──────────────┴──────────────┐
          ↓                             ↓
     var / let / const             Data Types
          │                             │
          ↓                    ┌────────┴────────┐
      Scope basics             ↓                 ↓
                         Primitive          Objects/Arrays
                             │                    │
                             ↓                    ↓
                       String/Number         Reference
                       Boolean/etc.          behavior
                                                  │
                                                  ↓
                                           Immutability
                                                  │
                                                  ↓
                                              React State
```
