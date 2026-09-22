# 13. Destructuring ⭐⭐⭐⭐⭐

**Destructuring** is one of the most important JavaScript concepts for React.

You will use it constantly with:

* Objects
* Arrays
* Function parameters
* React props
* React state
* API responses
* `useState`
* `useEffect`
* Function return values

The basic idea is simple:

> **Destructuring lets you take values from an object or array and store them directly in variables.**

---

# 1. What is Destructuring?

Without destructuring:

```javascript
const user = {
    name: "Sai",
    age: 22,
    city: "Bengaluru"
};

const name = user.name;
const age = user.age;
const city = user.city;

console.log(name);
console.log(age);
console.log(city);
```

With destructuring:

```javascript
const user = {
    name: "Sai",
    age: 22,
    city: "Bengaluru"
};

const { name, age, city } = user;

console.log(name);
console.log(age);
console.log(city);
```

Output:

```text
Sai
22
Bengaluru
```

Instead of repeatedly writing:

```javascript
user.name
user.age
user.city
```

you can extract them directly.

---

# 2. Two Types of Destructuring

There are two main types:

### 1. Object Destructuring ⭐⭐⭐⭐⭐

```javascript
const { name, age } = user;
```

### 2. Array Destructuring ⭐⭐⭐⭐⭐

```javascript
const [first, second] = numbers;
```

The syntax tells you what you're destructuring:

```text
Object → {}
Array  → []
```

This distinction is extremely important.

---

# 3. Object Destructuring ⭐⭐⭐⭐⭐

Suppose:

```javascript
const student = {
    name: "Sai",
    age: 22,
    course: "React"
};
```

Without destructuring:

```javascript
const name = student.name;
const age = student.age;
const course = student.course;
```

With destructuring:

```javascript
const { name, age, course } = student;
```

Now you can directly use:

```javascript
console.log(name);
console.log(age);
console.log(course);
```

Output:

```text
Sai
22
React
```

---

# 4. How Object Destructuring Works

Look at:

```javascript
const { name, age } = student;
```

JavaScript essentially says:

```text
Find the "name" property → create variable name
Find the "age" property  → create variable age
```

So:

```javascript
const { name } = student;
```

is roughly equivalent to:

```javascript
const name = student.name;
```

And:

```javascript
const { age } = student;
```

is roughly:

```javascript
const age = student.age;
```

---

# 5. You Don't Have to Extract Everything

Suppose:

```javascript
const user = {
    name: "Sai",
    age: 22,
    city: "Bengaluru",
    country: "India"
};
```

You only need the name:

```javascript
const { name } = user;

console.log(name);
```

Output:

```text
Sai
```

You can extract only the properties you need.

---

# 6. Destructuring With Different Variable Names ⭐⭐⭐⭐⭐

Suppose:

```javascript
const user = {
    name: "Sai",
    age: 22
};
```

You want the variable to be called `userName` instead of `name`.

Write:

```javascript
const { name: userName } = user;

console.log(userName);
```

Output:

```text
Sai
```

### Important syntax

```javascript
const { propertyName: variableName } = object;
```

For example:

```javascript
const { name: userName } = user;
```

means:

```text
Object property → name
Variable → userName
```

---

# 7. Common Beginner Confusion

This:

```javascript
const { name: userName } = user;
```

does **not** mean:

```text
rename the object's property
```

The original object is unchanged.

```javascript
console.log(user);
```

still gives:

```javascript
{
    name: "Sai",
    age: 22
}
```

Only the local variable is named differently.

---

# 8. Default Values ⭐⭐⭐⭐⭐

Suppose the property doesn't exist:

```javascript
const user = {
    name: "Sai"
};

const { age } = user;

console.log(age);
```

Output:

```text
undefined
```

You can provide a default:

```javascript
const { age = 22 } = user;

console.log(age);
```

Output:

```text
22
```

So:

```javascript
const { age = 22 } = user;
```

means:

> If `age` exists, use it. Otherwise use `22`.

---

# 9. Existing Value Beats Default

Consider:

```javascript
const user = {
    name: "Sai",
    age: 25
};

const { age = 22 } = user;

console.log(age);
```

Output:

```text
25
```

The default `22` is used only when the property value is `undefined`.

---

# 10. `null` and Default Values

This is an important interview detail.

```javascript
const user = {
    age: null
};

const { age = 22 } = user;

console.log(age);
```

Output:

```text
null
```

The default does **not** apply to `null`.

The default applies when the value is `undefined`.

---

# 11. Nested Object Destructuring ⭐⭐⭐⭐⭐

Consider:

```javascript
const user = {
    name: "Sai",
    address: {
        city: "Bengaluru",
        state: "Karnataka"
    }
};
```

Without destructuring:

```javascript
const city = user.address.city;
const state = user.address.state;
```

With nested destructuring:

```javascript
const {
    address: { city, state }
} = user;

console.log(city);
console.log(state);
```

Output:

```text
Bengaluru
Karnataka
```

---

# 12. Nested Destructuring With Renaming

You can combine techniques:

```javascript
const user = {
    name: "Sai",
    address: {
        city: "Bengaluru"
    }
};

const {
    address: { city: userCity }
} = user;

console.log(userCity);
```

Output:

```text
Bengaluru
```

---

# 13. Array Destructuring ⭐⭐⭐⭐⭐

Now let's look at arrays.

Suppose:

```javascript
const numbers = [10, 20, 30];
```

Without destructuring:

```javascript
const first = numbers[0];
const second = numbers[1];
const third = numbers[2];
```

With destructuring:

```javascript
const [first, second, third] = numbers;
```

Now:

```javascript
console.log(first);
console.log(second);
console.log(third);
```

Output:

```text
10
20
30
```

---

# 14. Array Destructuring Works by Position

This is the biggest difference between object and array destructuring.

Given:

```javascript
const numbers = [10, 20, 30];
```

```javascript
const [a, b, c] = numbers;
```

means:

```text
a → first item
b → second item
c → third item
```

The variable names don't matter.

For example:

```javascript
const [x, y, z] = numbers;
```

still gives:

```text
x → 10
y → 20
z → 30
```

### Remember:

```text
Object destructuring → property names
Array destructuring  → positions
```

---

# 15. Skipping Array Values ⭐⭐⭐⭐⭐

Suppose:

```javascript
const numbers = [10, 20, 30];
```

You only want the first and third values.

You can skip the second:

```javascript
const [first, , third] = numbers;

console.log(first);
console.log(third);
```

Output:

```text
10
30
```

The empty space between commas means:

> Skip this value.

---

# 16. Array Destructuring With Default Values

```javascript
const numbers = [10];

const [first, second = 20] = numbers;

console.log(first);
console.log(second);
```

Output:

```text
10
20
```

Because there is no second element.

---

# 17. Existing Value Beats Default

```javascript
const numbers = [10, 50];

const [first, second = 20] = numbers;

console.log(second);
```

Output:

```text
50
```

Because the second value already exists.

---

# 18. Rest Operator With Array Destructuring ⭐⭐⭐⭐⭐

This is very important.

Suppose:

```javascript
const numbers = [10, 20, 30, 40, 50];
```

You want the first value separately and the remaining values together.

```javascript
const [first, ...remaining] = numbers;

console.log(first);
console.log(remaining);
```

Output:

```text
10
[20, 30, 40, 50]
```

Here:

```javascript
...remaining
```

collects the remaining values.

This is called the **rest pattern**.

---

# 19. Rest Must Be Last

Correct:

```javascript
const [first, ...remaining] = numbers;
```

Incorrect:

```javascript
const [...remaining, last] = numbers;
```

The rest element must be the final element in the destructuring pattern.

---

# 20. Object Rest Destructuring ⭐⭐⭐⭐⭐

Rest also works with objects.

```javascript
const user = {
    name: "Sai",
    age: 22,
    city: "Bengaluru"
};

const { name, ...otherDetails } = user;

console.log(name);
console.log(otherDetails);
```

Output:

```text
Sai
{
    age: 22,
    city: "Bengaluru"
}
```

Here:

```javascript
const { name, ...otherDetails } = user;
```

means:

```text
name → take name separately
otherDetails → collect the remaining properties
```

---

# 21. Destructuring Function Parameters ⭐⭐⭐⭐⭐

This is **extremely important for React**.

Suppose:

```javascript
const user = {
    name: "Sai",
    age: 22
};

function displayUser(user) {
    console.log(user.name);
    console.log(user.age);
}

displayUser(user);
```

You can destructure directly in the function parameter:

```javascript
function displayUser({ name, age }) {
    console.log(name);
    console.log(age);
}

displayUser(user);
```

Output:

```text
Sai
22
```

This is very common in React components.

---

# 22. React Props + Destructuring ⭐⭐⭐⭐⭐

Consider:

```jsx
<Student name="Sai" age={22} />
```

A component can receive:

```javascript
function Student(props) {
    console.log(props.name);
    console.log(props.age);
}
```

But we commonly destructure props:

```javascript
function Student({ name, age }) {
    console.log(name);
    console.log(age);
}
```

This:

```javascript
function Student({ name, age })
```

means:

> Take the `name` and `age` properties from the props object.

---

# 23. React Component Example

```jsx
function Student({ name, age, course }) {
    return (
        <div>
            <h2>{name}</h2>
            <p>Age: {age}</p>
            <p>Course: {course}</p>
        </div>
    );
}
```

Then:

```jsx
<Student
    name="Sai"
    age={22}
    course="React"
/>
```

React passes an object conceptually like:

```javascript
{
    name: "Sai",
    age: 22,
    course: "React"
}
```

And the component destructures it:

```javascript
function Student({ name, age, course })
```

This is one of the most common uses of object destructuring in React.

---

# 24. Destructuring `useState()` ⭐⭐⭐⭐⭐

This is perhaps the most famous example of **array destructuring** in React.

You will often see:

```javascript
const [count, setCount] = useState(0);
```

`useState(0)` returns an array conceptually like:

```javascript
[
    currentValue,
    functionToUpdateValue
]
```

So:

```javascript
const [count, setCount] = useState(0);
```

uses **array destructuring**.

You could think of it as:

```javascript
const result = useState(0);

const count = result[0];
const setCount = result[1];
```

But destructuring makes it much cleaner:

```javascript
const [count, setCount] = useState(0);
```

---

# 25. Why Are the Names `count` and `setCount`?

Array destructuring works by **position**, not name.

For example:

```javascript
const [x, y] = useState(0);
```

would technically work.

But React convention is:

```javascript
const [count, setCount] = useState(0);
```

because:

```text
count    → current state
setCount → state update function
```

---

# 26. `useState()` Is a Great Interview Example

If an interviewer asks:

> Give an example of array destructuring in React.

A good answer is:

```javascript
const [count, setCount] = useState(0);
```

Because `useState()` returns an array, and we extract its two elements using array destructuring.

---

# 27. Destructuring Function Return Values

A function can return an array:

```javascript
function getUser() {
    return ["Sai", 22];
}

const [name, age] = getUser();

console.log(name);
console.log(age);
```

Output:

```text
Sai
22
```

This is another practical use of array destructuring.

---

# 28. Object Returned From Function

A function can also return an object:

```javascript
function getUser() {
    return {
        name: "Sai",
        age: 22
    };
}

const { name, age } = getUser();

console.log(name);
console.log(age);
```

So:

```text
Function returns array → array destructuring
Function returns object → object destructuring
```

---

# 29. Swapping Variables ⭐⭐⭐⭐⭐

One of the classic uses of array destructuring is swapping values.

Normally:

```javascript
let a = 10;
let b = 20;
```

You might use a temporary variable.

With destructuring:

```javascript
[a, b] = [b, a];
```

Now:

```javascript
console.log(a);
console.log(b);
```

Output:

```text
20
10
```

Very clean.

---

# 30. Destructuring With `let` and `const`

You can use:

```javascript
const [a, b] = [10, 20];
```

or:

```javascript
let [a, b] = [10, 20];
```

For reassignment later, use `let`.

Example:

```javascript
let [a, b] = [10, 20];

[a, b] = [b, a];
```

---

# 31. Destructuring in Loops ⭐⭐⭐⭐

Suppose:

```javascript
const users = [
    { name: "Sai", age: 22 },
    { name: "Rahul", age: 23 }
];
```

You could write:

```javascript
for (const user of users) {
    console.log(user.name);
}
```

Or destructure directly:

```javascript
for (const { name, age } of users) {
    console.log(name, age);
}
```

Output:

```text
Sai 22
Rahul 23
```

---

# 32. Destructuring With `Object.entries()`

Remember:

```javascript
Object.entries(user)
```

returns:

```javascript
[
    ["name", "Sai"],
    ["age", 22]
]
```

You can destructure those pairs:

```javascript
Object.entries(user).forEach(([key, value]) => {
    console.log(key, value);
});
```

Here:

```javascript
[key, value]
```

is array destructuring.

This is a nice example combining concepts.

---

# 33. Destructuring With `map()`

Suppose:

```javascript
const users = [
    { id: 1, name: "Sai" },
    { id: 2, name: "Rahul" },
    { id: 3, name: "Anil" }
];
```

Without destructuring:

```javascript
const names = users.map(user => user.name);
```

With destructuring:

```javascript
const names = users.map(({ name }) => name);
```

Result:

```javascript
["Sai", "Rahul", "Anil"]
```

This is very common in React code.

---

# 34. Destructuring With `filter()`

```javascript
const users = [
    { name: "Sai", age: 22 },
    { name: "Rahul", age: 17 },
    { name: "Anil", age: 25 }
];

const adults = users.filter(({ age }) => age >= 18);

console.log(adults);
```

Result:

```javascript
[
    { name: "Sai", age: 22 },
    { name: "Anil", age: 25 }
]
```

Again:

```javascript
({ age })
```

is object destructuring.

---

# 35. Destructuring With Default Function Parameters

You can combine destructuring and default values.

```javascript
function greet({ name = "Guest" }) {
    console.log(`Hello ${name}`);
}

greet({});
```

Output:

```text
Hello Guest
```

And:

```javascript
greet({ name: "Sai" });
```

Output:

```text
Hello Sai
```

---

# 36. Default Object Parameter ⭐⭐⭐⭐

There is an important difference between:

```javascript
function greet({ name = "Guest" }) {
    console.log(name);
}
```

and:

```javascript
function greet({ name = "Guest" } = {}) {
    console.log(name);
}
```

The second version also handles:

```javascript
greet();
```

because it defaults the entire argument to `{}`.

Without the `= {}`:

```javascript
greet();
```

would cause an error because JavaScript can't destructure `undefined`.

---

# 37. Renaming + Default Value

You can combine both:

```javascript
const user = {
    name: "Sai"
};

const {
    name: userName,
    age: userAge = 22
} = user;

console.log(userName);
console.log(userAge);
```

Output:

```text
Sai
22
```

---

# 38. Nested Array Destructuring

Destructuring can also be nested.

```javascript
const numbers = [
    [10, 20],
    [30, 40]
];

const [[a, b], [c, d]] = numbers;

console.log(a);
console.log(b);
console.log(c);
console.log(d);
```

Output:

```text
10
20
30
40
```

This is less common in beginner React code but useful to understand.

---

# 39. Object + Array Destructuring Together

Real API data can be complex.

```javascript
const user = {
    name: "Sai",
    skills: ["JavaScript", "React"]
};
```

You can write:

```javascript
const {
    name,
    skills: [firstSkill, secondSkill]
} = user;

console.log(name);
console.log(firstSkill);
console.log(secondSkill);
```

Output:

```text
Sai
JavaScript
React
```

---

# 40. Very Important: Destructuring Does Not Mutate the Original Object

Consider:

```javascript
const user = {
    name: "Sai",
    age: 22
};

const { name } = user;
```

The original object is still:

```javascript
{
    name: "Sai",
    age: 22
}
```

Destructuring simply extracts values/references into variables.

It doesn't remove properties from the original object.

---

# 41. Destructuring and Primitive Values

For objects:

```javascript
const { name } = user;
```

works based on property names.

For arrays:

```javascript
const [first] = numbers;
```

works based on position.

### The easiest way to remember:

```text
{} → object → match property names

[] → array → match positions
```

---

# 42. Object vs Array Destructuring

| Feature       | Object                | Array                                       |
| ------------- | --------------------- | ------------------------------------------- |
| Syntax        | `{}`                  | `[]`                                        |
| Matching      | Property name         | Position                                    |
| Example       | `{name}`              | `[first]`                                   |
| Rename        | `{name: userName}`    | `[first]` simply choose a new variable name |
| Skip          | Not normally relevant | `[first, , third]`                          |
| Rest          | `{name, ...rest}`     | `[first, ...rest]`                          |
| React example | Props                 | `useState()`                                |

---

# 43. Destructuring vs Spread vs Rest ⭐⭐⭐⭐⭐

These three are often confused.

## Destructuring

**Extracts values.**

```javascript
const { name } = user;
```

Think:

> Take something out.

---

## Spread

**Expands/copies values.**

```javascript
const newUser = {
    ...user
};
```

Think:

> Spread things out.

---

## Rest

**Collects remaining values.**

```javascript
const { name, ...otherDetails } = user;
```

Think:

> Gather the rest.

### Mental model

```text
Destructuring → TAKE OUT
Spread        → SPREAD OUT
Rest          → COLLECT THE REST
```

The same `...` syntax can represent spread or rest depending on where it appears.

---

# 44. Common Mistakes

## Mistake 1: Using array syntax for an object

Wrong:

```javascript
const [name] = user;
```

If `user` is an object, use:

```javascript
const { name } = user;
```

---

## Mistake 2: Using object syntax for an array

Wrong:

```javascript
const { first } = numbers;
```

If you want the first array element:

```javascript
const [first] = numbers;
```

---

## Mistake 3: Confusing renaming syntax

```javascript
const { name: userName } = user;
```

This means:

```text
property = name
variable = userName
```

Not the other way around.

---

## Mistake 4: Forgetting default values only apply to `undefined`

```javascript
const { age = 22 } = { age: null };
```

Result:

```text
null
```

not:

```text
22
```

---

## Mistake 5: Rest isn't allowed in the middle

Wrong:

```javascript
const [first, ...middle, last] = numbers;
```

Correct:

```javascript
const [first, ...rest] = numbers;
```

---

# 45. Interview Questions ⭐⭐⭐⭐⭐

### Q1. What is destructuring?

**Answer:**

Destructuring is a JavaScript syntax that allows us to extract values from objects or arrays and assign them to variables.

---

### Q2. What is the difference between object and array destructuring?

**Answer:**

Object destructuring matches values using **property names**:

```javascript
const { name } = user;
```

Array destructuring matches values using **position**:

```javascript
const [first, second] = numbers;
```

---

### Q3. What is the output?

```javascript
const user = {
    name: "Sai",
    age: 22
};

const { name } = user;

console.log(name);
```

Answer:

```text
Sai
```

---

### Q4. What is the output?

```javascript
const numbers = [10, 20, 30];

const [first, , third] = numbers;

console.log(third);
```

Answer:

```text
30
```

---

### Q5. How do you rename a destructured property?

```javascript
const { name: userName } = user;
```

Now the variable is:

```javascript
userName
```

---

### Q6. How do you provide a default value?

```javascript
const { age = 18 } = user;
```

If `age` is `undefined`, it uses `18`.

---

### Q7. What is this?

```javascript
const [count, setCount] = useState(0);
```

Answer:

> Array destructuring.

`useState()` returns an array containing the current state value and its updater function.

---

### Q8. Why is destructuring common in React?

Because React frequently works with objects and arrays:

* Props are objects.
* `useState()` returns an array.
* API responses commonly contain objects/arrays.
* Event/data objects can be destructured.
* Function parameters can be destructured.

---

# 46. Output-Based Interview Questions 🧠

### Question 1

```javascript
const user = {
    name: "Sai",
    age: 22
};

const { name: username } = user;

console.log(username);
```

Output:

```text
Sai
```

---

### Question 2

```javascript
const numbers = [10, 20, 30];

const [a, b] = numbers;

console.log(a);
console.log(b);
```

Output:

```text
10
20
```

---

### Question 3

```javascript
const numbers = [10, 20];

const [a, b, c = 30] = numbers;

console.log(c);
```

Output:

```text
30
```

---

### Question 4

```javascript
const user = {
    name: "Sai",
    age: 22
};

const { name, ...rest } = user;

console.log(rest);
```

Output:

```javascript
{
    age: 22
}
```

---

### Question 5 ⭐

```javascript
const numbers = [10, 20, 30, 40];

const [first, ...rest] = numbers;

console.log(first);
console.log(rest);
```

Output:

```text
10
[20, 30, 40]
```

---

# 47. Coding Practice

Try these yourself.

### Practice 1 — Object Destructuring

```javascript
const employee = {
    name: "Sai",
    age: 22,
    role: "Frontend Developer"
};
```

Extract:

```text
name
age
role
```

using destructuring.

---

### Practice 2 — Rename

From:

```javascript
const user = {
    name: "Sai"
};
```

create a variable called:

```text
userName
```

using destructuring.

---

### Practice 3 — Array Destructuring

```javascript
const colors = ["red", "green", "blue"];
```

Extract:

```text
firstColor
thirdColor
```

while skipping `"green"`.

---

### Practice 4 — Rest

```javascript
const numbers = [10, 20, 30, 40, 50];
```

Extract:

```text
first
```

and store the remaining values in:

```text
remaining
```

---

### Practice 5 — React

Explain what this means:

```javascript
const [count, setCount] = useState(0);
```

You should be able to explain:

1. Why `[]`?
2. What is `count`?
3. What is `setCount`?
4. Why is this called destructuring?
5. What does `useState(0)` return?

---

# 48. Destructuring Cheat Sheet ⭐⭐⭐⭐⭐

### Object

```javascript
const { name, age } = user;
```

### Rename

```javascript
const { name: userName } = user;
```

### Default

```javascript
const { age = 18 } = user;
```

### Nested

```javascript
const {
    address: { city }
} = user;
```

### Object rest

```javascript
const { name, ...rest } = user;
```

### Array

```javascript
const [first, second] = numbers;
```

### Skip

```javascript
const [first, , third] = numbers;
```

### Array default

```javascript
const [first = 10] = numbers;
```

### Array rest

```javascript
const [first, ...rest] = numbers;
```

### Function parameter

```javascript
function greet({ name }) {
    console.log(name);
}
```

### React props

```javascript
function User({ name, age }) {
    return <h2>{name}</h2>;
}
```

### React state

```javascript
const [count, setCount] = useState(0);
```

---

# 49. The Most Important Mental Model

Remember these four patterns:

```javascript
const { name } = user;
```

**Object → property name**

```javascript
const [first] = numbers;
```

**Array → position**

```javascript
const { name, ...rest } = user;
```

**Object → extract one + collect remaining**

```javascript
const [first, ...rest] = numbers;
```

**Array → extract one + collect remaining**

And for React:

```javascript
const { name, age } = props;
```

means:

> Get properties from the props object.

While:

```javascript
const [count, setCount] = useState(0);
```

means:

> Get values from the array returned by `useState()`.

---

## ⭐ React Interview Priority

For your React interview preparation, make sure you can write these **without thinking**:

```javascript
const { name, age } = user;
```

```javascript
const { name: userName } = user;
```

```javascript
const { age = 18 } = user;
```

```javascript
const [first, second] = numbers;
```

```javascript
const [first, , third] = numbers;
```

```javascript
const [first, ...rest] = numbers;
```

```javascript
function User({ name, age }) {
    // ...
}
```

```javascript
const [count, setCount] = useState(0);
```

If these are comfortable, you're in a strong position for the next JavaScript topics and for React code.