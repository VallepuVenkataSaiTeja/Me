# 11. Arrays in JavaScript ⭐⭐⭐⭐⭐

Arrays are **one of the most important JavaScript topics for React interviews**.

You will use arrays constantly in React for:

* Rendering lists
* API data
* Managing collections of objects
* Adding/removing items
* Searching data
* Filtering data
* Sorting data
* Updating state
* Creating dropdowns
* Shopping carts
* Tables
* Todo lists

For React, these are especially important:

```text
map()
filter()
find()
some()
every()
reduce()
```

We'll learn everything from the basics to interview level.

---

# 1. What Is an Array?

An **array is a data structure used to store multiple values in a single variable**.

Example:

```javascript
const fruits = ["Apple", "Banana", "Mango"];
```

Instead of:

```javascript
const fruit1 = "Apple";
const fruit2 = "Banana";
const fruit3 = "Mango";
```

we can use:

```javascript
const fruits = ["Apple", "Banana", "Mango"];
```

---

# 2. Array Indexing ⭐⭐⭐⭐⭐

Arrays use **zero-based indexing**.

```javascript
const fruits = ["Apple", "Banana", "Mango"];
```

The indexes are:

```text
Value:    Apple     Banana     Mango
Index:      0          1         2
```

So:

```javascript
console.log(fruits[0]);
```

Output:

```text
Apple
```

```javascript
console.log(fruits[1]);
```

Output:

```text
Banana
```

```javascript
console.log(fruits[2]);
```

Output:

```text
Mango
```

---

# 3. Getting the Array Length ⭐⭐⭐⭐⭐

Use:

```javascript
.length
```

Example:

```javascript
const fruits = ["Apple", "Banana", "Mango"];

console.log(fruits.length);
```

Output:

```text
3
```

Remember:

> `.length` tells you the number of elements, not the last index.

For:

```javascript
["Apple", "Banana", "Mango"]
```

we have:

```text
length = 3
last index = 2
```

Therefore:

```javascript
array.length - 1
```

gives the last index.

---

# 4. Getting the Last Element ⭐⭐⭐⭐⭐

Traditional way:

```javascript
const fruits = ["Apple", "Banana", "Mango"];

console.log(fruits[fruits.length - 1]);
```

Output:

```text
Mango
```

Modern way:

```javascript
console.log(fruits.at(-1));
```

Output:

```text
Mango
```

---

# 5. Arrays Can Store Different Data Types

JavaScript arrays can contain different types:

```javascript
const data = [
    "Sai",
    22,
    true,
    null,
    undefined
];
```

Even objects and arrays:

```javascript
const data = [
    "Sai",
    22,
    { city: "Kadapa" },
    [1, 2, 3]
];
```

Although JavaScript allows this, in real applications you usually keep arrays logically consistent.

For example:

```javascript
const users = [
    { name: "Sai", age: 22 },
    { name: "Raj", age: 24 }
];
```

This is very common in React.

---

# 6. Checking Whether Something Is an Array ⭐⭐⭐⭐⭐

You might think:

```javascript
typeof []
```

would return:

```text
array
```

But:

```javascript
console.log(typeof []);
```

Output:

```text
object
```

Instead use:

```javascript
Array.isArray([]);
```

Output:

```text
true
```

Example:

```javascript
console.log(Array.isArray([1, 2, 3]));
```

```text
true
```

```javascript
console.log(Array.isArray("Hello"));
```

```text
false
```

### Interview question:

**How do you check whether a value is an array?**

Answer:

```javascript
Array.isArray(value)
```

---

# 7. Creating an Array

### Array literal — preferred

```javascript
const fruits = ["Apple", "Banana", "Mango"];
```

### `new Array()`

```javascript
const fruits = new Array("Apple", "Banana", "Mango");
```

The literal syntax is usually simpler and preferred:

```javascript
[]
```

---

# 8. Empty Array

```javascript
const users = [];
```

You can add elements later.

```javascript
users.push("Sai");

console.log(users);
```

Output:

```javascript
["Sai"]
```

---

# 9. Changing an Array Element ⭐⭐⭐⭐⭐

Unlike strings, arrays are **mutable**.

Example:

```javascript
const fruits = ["Apple", "Banana", "Mango"];

fruits[1] = "Orange";

console.log(fruits);
```

Output:

```javascript
["Apple", "Orange", "Mango"]
```

The array changed.

---

# 10. Arrays Are Mutable ⭐⭐⭐⭐⭐

This is an important difference:

### String

```javascript
const name = "Sai";

name[0] = "R";
```

Doesn't change the string.

### Array

```javascript
const fruits = ["Apple", "Banana"];

fruits[0] = "Mango";
```

Changes the array.

So:

```text
String → immutable
Array  → mutable
```

---

# 11. `const` Array Can Still Be Modified ⭐⭐⭐⭐⭐

This often confuses beginners.

```javascript
const fruits = ["Apple", "Banana"];

fruits.push("Mango");

console.log(fruits);
```

Output:

```javascript
["Apple", "Banana", "Mango"]
```

Why does this work if it's `const`?

Because `const` prevents **reassigning the variable**, not modifying the array's contents.

This:

```javascript
fruits = ["Orange"];
```

❌ is not allowed.

But:

```javascript
fruits.push("Mango");
```

✅ is allowed.

---

# 12. `push()` ⭐⭐⭐⭐⭐

Adds an element to the **end** of an array.

```javascript
const fruits = ["Apple", "Banana"];

fruits.push("Mango");

console.log(fruits);
```

Output:

```javascript
["Apple", "Banana", "Mango"]
```

`push()` changes the original array.

---

# 13. `push()` Returns the New Length

Important interview question:

```javascript
const fruits = ["Apple", "Banana"];

const result = fruits.push("Mango");

console.log(result);
```

Output:

```text
3
```

Not the array.

`push()` returns the **new array length**.

---

# 14. `pop()` ⭐⭐⭐⭐⭐

Removes the last element.

```javascript
const fruits = ["Apple", "Banana", "Mango"];

const result = fruits.pop();

console.log(result);
console.log(fruits);
```

Output:

```text
Mango
```

```javascript
["Apple", "Banana"]
```

`pop()` returns the removed element.

---

# 15. `shift()` ⭐⭐⭐⭐

Removes the first element.

```javascript
const fruits = ["Apple", "Banana", "Mango"];

const result = fruits.shift();

console.log(result);
console.log(fruits);
```

Output:

```text
Apple
```

Array becomes:

```javascript
["Banana", "Mango"]
```

---

# 16. `unshift()` ⭐⭐⭐⭐

Adds an element to the beginning.

```javascript
const fruits = ["Banana", "Mango"];

fruits.unshift("Apple");

console.log(fruits);
```

Output:

```javascript
["Apple", "Banana", "Mango"]
```

---

# 17. Important Mutation Methods

Memorize this:

| Method      | Action                | Mutates array? |
| ----------- | --------------------- | -------------- |
| `push()`    | Add to end            | ✅              |
| `pop()`     | Remove from end       | ✅              |
| `shift()`   | Remove from beginning | ✅              |
| `unshift()` | Add to beginning      | ✅              |

---

# 18. `splice()` ⭐⭐⭐⭐⭐

`splice()` is used to **add, remove, or replace elements** at a particular position.

Syntax:

```javascript
array.splice(start, deleteCount, item1, item2, ...)
```

Example:

```javascript
const fruits = ["Apple", "Banana", "Mango"];

fruits.splice(1, 1);

console.log(fruits);
```

Output:

```javascript
["Apple", "Mango"]
```

It starts at index `1` and removes `1` element.

---

# 19. `splice()` Add Elements

```javascript
const fruits = ["Apple", "Mango"];

fruits.splice(1, 0, "Banana");

console.log(fruits);
```

Output:

```javascript
["Apple", "Banana", "Mango"]
```

Explanation:

```text
start = 1
deleteCount = 0
add = "Banana"
```

---

# 20. `splice()` Replace Elements

```javascript
const fruits = ["Apple", "Banana", "Mango"];

fruits.splice(1, 1, "Orange");

console.log(fruits);
```

Output:

```javascript
["Apple", "Orange", "Mango"]
```

---

# 21. `splice()` Mutates the Original Array

This is important:

```javascript
const numbers = [1, 2, 3, 4];

numbers.splice(1, 2);

console.log(numbers);
```

Output:

```javascript
[1, 4]
```

The original array changed.

---

# 22. `slice()` vs `splice()` ⭐⭐⭐⭐⭐

This is one of the **most common interview questions**.

### `slice()`

Creates a new array.

```javascript
const numbers = [1, 2, 3, 4];

const result = numbers.slice(1, 3);

console.log(result);
console.log(numbers);
```

Output:

```javascript
[2, 3]
```

Original:

```javascript
[1, 2, 3, 4]
```

`slice()` does **not** mutate the original array.

---

### `splice()`

Changes the original array.

```javascript
const numbers = [1, 2, 3, 4];

numbers.splice(1, 2);

console.log(numbers);
```

Output:

```javascript
[1, 4]
```

### Remember:

```text
slice  → copy/extract → does NOT mutate
splice → add/remove   → mutates
```

---

# 23. `concat()` ⭐⭐⭐

Combines arrays.

```javascript
const a = [1, 2];
const b = [3, 4];

const result = a.concat(b);

console.log(result);
```

Output:

```javascript
[1, 2, 3, 4]
```

The original arrays aren't changed.

---

# 24. Spread Operator for Combining Arrays ⭐⭐⭐⭐⭐

You already learned spread.

```javascript
const a = [1, 2];
const b = [3, 4];

const result = [...a, ...b];

console.log(result);
```

Output:

```javascript
[1, 2, 3, 4]
```

In React, this is extremely important for immutable state updates.

---

# 25. `indexOf()` ⭐⭐⭐⭐

Finds the first index of an element.

```javascript
const fruits = ["Apple", "Banana", "Mango"];

console.log(fruits.indexOf("Banana"));
```

Output:

```text
1
```

If not found:

```javascript
console.log(fruits.indexOf("Orange"));
```

Output:

```text
-1
```

---

# 26. `includes()` ⭐⭐⭐⭐⭐

Checks whether an array contains an element.

```javascript
const fruits = ["Apple", "Banana", "Mango"];

console.log(fruits.includes("Banana"));
```

Output:

```text
true
```

Not found:

```javascript
console.log(fruits.includes("Orange"));
```

Output:

```text
false
```

---

# 27. `find()` ⭐⭐⭐⭐⭐

`find()` is **extremely important for React interviews**.

It returns the **first element** that satisfies a condition.

Example:

```javascript
const numbers = [10, 20, 30, 40];

const result = numbers.find((number) => number > 20);

console.log(result);
```

Output:

```text
30
```

Why?

The first number greater than `20` is:

```text
30
```

---

# 28. `find()` With Objects

This is very common in React.

```javascript
const users = [
    { id: 1, name: "Sai" },
    { id: 2, name: "Raj" },
    { id: 3, name: "John" }
];

const user = users.find((user) => user.id === 2);

console.log(user);
```

Output:

```javascript
{ id: 2, name: "Raj" }
```

---

# 29. `find()` Returns `undefined` If Not Found

```javascript
const users = [
    { id: 1, name: "Sai" },
    { id: 2, name: "Raj" }
];

const user = users.find((user) => user.id === 5);

console.log(user);
```

Output:

```text
undefined
```

---

# 30. `findIndex()` ⭐⭐⭐⭐

Returns the index of the first matching element.

```javascript
const numbers = [10, 20, 30, 40];

const index = numbers.findIndex((number) => number > 20);

console.log(index);
```

Output:

```text
2
```

Because:

```text
numbers[2] = 30
```

---

# 31. `filter()` ⭐⭐⭐⭐⭐

`filter()` returns a **new array containing all elements that satisfy a condition**.

Example:

```javascript
const numbers = [10, 20, 30, 40];

const result = numbers.filter((number) => number > 20);

console.log(result);
```

Output:

```javascript
[30, 40]
```

---

# 32. `find()` vs `filter()` ⭐⭐⭐⭐⭐

This is very important.

### `find()`

Returns **one element**:

```javascript
const result = numbers.find((n) => n > 20);
```

Result:

```text
30
```

### `filter()`

Returns **an array**:

```javascript
const result = numbers.filter((n) => n > 20);
```

Result:

```javascript
[30, 40]
```

Remember:

```text
find   → first matching element
filter → all matching elements
```

---

# 33. `map()` ⭐⭐⭐⭐⭐

`map()` is probably the **most important array method for React**.

It creates a **new array by transforming every element**.

Example:

```javascript
const numbers = [1, 2, 3, 4];

const result = numbers.map((number) => number * 2);

console.log(result);
```

Output:

```javascript
[2, 4, 6, 8]
```

---

# 34. How `map()` Works

Original:

```text
[1, 2, 3, 4]
```

Function:

```javascript
number * 2
```

Each element:

```text
1 → 2
2 → 4
3 → 6
4 → 8
```

Result:

```text
[2, 4, 6, 8]
```

---

# 35. `map()` With Objects

```javascript
const users = [
    { name: "Sai", age: 22 },
    { name: "Raj", age: 24 }
];

const names = users.map((user) => user.name);

console.log(names);
```

Output:

```javascript
["Sai", "Raj"]
```

---

# 36. `map()` in React ⭐⭐⭐⭐⭐

This is one of the most important React patterns.

Suppose:

```javascript
const users = [
    { id: 1, name: "Sai" },
    { id: 2, name: "Raj" },
    { id: 3, name: "John" }
];
```

You can render:

```jsx
<ul>
    {users.map((user) => (
        <li key={user.id}>
            {user.name}
        </li>
    ))}
</ul>
```

Result:

```text
Sai
Raj
John
```

This is why you must master `map()` before becoming interview-ready in React.

---

# 37. Why Does React Need `key`?

When rendering a list:

```jsx
{users.map((user) => (
    <li key={user.id}>
        {user.name}
    </li>
))}
```

React uses `key` to identify individual list items.

Prefer a stable unique ID:

```jsx
key={user.id}
```

Avoid using array index when items can be reordered, inserted, or deleted.

---

# 38. `forEach()` ⭐⭐⭐⭐

`forEach()` executes a function for every element.

```javascript
const numbers = [1, 2, 3];

numbers.forEach((number) => {
    console.log(number);
});
```

Output:

```text
1
2
3
```

---

# 39. `map()` vs `forEach()` ⭐⭐⭐⭐⭐

Very common interview question.

### `map()`

Returns a new array:

```javascript
const result = numbers.map((n) => n * 2);
```

Result:

```javascript
[2, 4, 6]
```

### `forEach()`

Does not create a transformed result array:

```javascript
numbers.forEach((n) => {
    console.log(n * 2);
});
```

### Remember:

```text
map     → transform → returns new array
forEach → perform action → returns undefined
```

---

# 40. `some()` ⭐⭐⭐⭐

Checks whether **at least one element** satisfies a condition.

```javascript
const numbers = [10, 20, 30, 40];

const result = numbers.some((number) => number > 30);

console.log(result);
```

Output:

```text
true
```

Because `40 > 30`.

---

# 41. `some()` Example

```javascript
const users = [
    { name: "Sai", age: 22 },
    { name: "Raj", age: 17 }
];

const hasAdult = users.some((user) => user.age >= 18);

console.log(hasAdult);
```

Output:

```text
true
```

---

# 42. `every()` ⭐⭐⭐⭐

Checks whether **all elements** satisfy a condition.

```javascript
const numbers = [10, 20, 30];

const result = numbers.every((number) => number > 5);

console.log(result);
```

Output:

```text
true
```

But:

```javascript
const numbers = [10, 20, 3];

console.log(numbers.every((number) => number > 5));
```

Output:

```text
false
```

Because `3` doesn't satisfy the condition.

---

# 43. `some()` vs `every()` ⭐⭐⭐⭐⭐

Remember:

```text
some()  → at least ONE passes
every() → ALL must pass
```

Example:

```javascript
[1, 2, 3].some(n => n > 2)
```

→ `true`

Because `3` passes.

```javascript
[1, 2, 3].every(n => n > 0)
```

→ `true`

All pass.

---

# 44. `reduce()` ⭐⭐⭐⭐⭐

`reduce()` is one of the most important array methods for interviews.

It reduces an array to a **single value**.

Example:

```javascript
const numbers = [1, 2, 3, 4];

const total = numbers.reduce((sum, number) => {
    return sum + number;
}, 0);

console.log(total);
```

Output:

```text
10
```

---

# 45. Understanding `reduce()`

Start:

```text
sum = 0
```

Then:

```text
0 + 1 = 1
1 + 2 = 3
3 + 3 = 6
6 + 4 = 10
```

Final result:

```text
10
```

---

# 46. `reduce()` Syntax

```javascript
array.reduce((accumulator, currentValue) => {
    // logic
}, initialValue);
```

Important terms:

```text
accumulator  → stores the result
currentValue → current array element
initialValue → starting value
```

---

# 47. `reduce()` Example: Sum

```javascript
const numbers = [10, 20, 30];

const total = numbers.reduce(
    (sum, number) => sum + number,
    0
);

console.log(total);
```

Output:

```text
60
```

---

# 48. `reduce()` Example: Find Maximum

```javascript
const numbers = [10, 50, 20, 80, 30];

const max = numbers.reduce((maximum, number) => {
    return number > maximum ? number : maximum;
}, numbers[0]);

console.log(max);
```

Output:

```text
80
```

---

# 49. `reduce()` Example: Count Items

```javascript
const fruits = ["Apple", "Banana", "Apple", "Mango", "Apple"];

const count = fruits.reduce((result, fruit) => {
    result[fruit] = (result[fruit] || 0) + 1;
    return result;
}, {});

console.log(count);
```

Result:

```javascript
{
    Apple: 3,
    Banana: 1,
    Mango: 1
}
```

This is a common interview-style problem.

---

# 50. `sort()` ⭐⭐⭐⭐

Sorts an array.

But there is a **very important trap**.

```javascript
const numbers = [10, 2, 30, 4];

numbers.sort();

console.log(numbers);
```

You may expect:

```javascript
[2, 4, 10, 30]
```

But JavaScript sorts values as strings by default.

Result:

```javascript
[10, 2, 30, 4]
```

depending on lexicographic ordering.

---

# 51. Correct Numeric Sorting ⭐⭐⭐⭐⭐

Ascending:

```javascript
const numbers = [10, 2, 30, 4];

numbers.sort((a, b) => a - b);

console.log(numbers);
```

Result:

```javascript
[2, 4, 10, 30]
```

Descending:

```javascript
numbers.sort((a, b) => b - a);
```

Result:

```javascript
[30, 10, 4, 2]
```

---

# 52. Important: `sort()` Mutates the Array

```javascript
const numbers = [3, 1, 2];

numbers.sort();

console.log(numbers);
```

The original array changes.

This matters a lot in React state.

Instead of:

```javascript
numbers.sort();
```

you may use:

```javascript
const sorted = [...numbers].sort((a, b) => a - b);
```

Now the original array isn't mutated.

---

# 53. `reverse()` ⭐⭐⭐

Reverses an array **in place**.

```javascript
const numbers = [1, 2, 3];

numbers.reverse();

console.log(numbers);
```

Output:

```javascript
[3, 2, 1]
```

It mutates the original array.

Non-mutating pattern:

```javascript
const reversed = [...numbers].reverse();
```

---

# 54. `join()` ⭐⭐⭐⭐

Converts an array to a string.

```javascript
const fruits = ["Apple", "Banana", "Mango"];

console.log(fruits.join(", "));
```

Output:

```text
Apple, Banana, Mango
```

Without separator:

```javascript
fruits.join("")
```

gives:

```text
AppleBananaMango
```

---

# 55. `flat()` ⭐⭐⭐

Flattens nested arrays.

```javascript
const numbers = [1, [2, 3], [4, 5]];

console.log(numbers.flat());
```

Output:

```javascript
[1, 2, 3, 4, 5]
```

---

# 56. Nested Arrays

Example:

```javascript
const numbers = [
    [1, 2],
    [3, 4]
];
```

You can flatten:

```javascript
const result = numbers.flat();

console.log(result);
```

Output:

```javascript
[1, 2, 3, 4]
```

---

# 57. `flatMap()` ⭐⭐⭐

Combines:

```text
map + flat
```

Example:

```javascript
const numbers = [1, 2, 3];

const result = numbers.flatMap((number) => [number, number * 2]);

console.log(result);
```

Output:

```javascript
[1, 2, 2, 4, 3, 6]
```

This is useful but less important than `map`, `filter`, and `reduce` for beginner React interviews.

---

# 58. `Array.from()` ⭐⭐⭐

Creates an array from an iterable or array-like value.

Example:

```javascript
const result = Array.from("Hello");

console.log(result);
```

Output:

```javascript
["H", "e", "l", "l", "o"]
```

You can also create arrays:

```javascript
const numbers = Array.from({ length: 5 }, (_, index) => index + 1);

console.log(numbers);
```

Output:

```javascript
[1, 2, 3, 4, 5]
```

---

# 59. `Array.of()` ⭐⭐

Creates an array from the provided values.

```javascript
const numbers = Array.of(1, 2, 3);

console.log(numbers);
```

Output:

```javascript
[1, 2, 3]
```

Less important for your React preparation.

---

# 60. Important: `map()` Does Not Mutate the Original

```javascript
const numbers = [1, 2, 3];

const result = numbers.map((number) => number * 2);

console.log(numbers);
console.log(result);
```

Output:

```javascript
[1, 2, 3]
```

```javascript
[2, 4, 6]
```

This is why `map()` works so well with React.

---

# 61. Important: `filter()` Does Not Mutate

```javascript
const numbers = [1, 2, 3, 4];

const result = numbers.filter((number) => number > 2);

console.log(numbers);
console.log(result);
```

Output:

```javascript
[1, 2, 3, 4]
```

```javascript
[3, 4]
```

---

# 62. Mutation vs Non-Mutation ⭐⭐⭐⭐⭐

This is **very important for React**.

### Mutating methods

```text
push()
pop()
shift()
unshift()
splice()
sort()
reverse()
```

These modify the original array.

### Non-mutating/common functional methods

```text
map()
filter()
find()
findIndex()
some()
every()
slice()
concat()
```

These return values/new arrays without changing the original array.

---

# 63. Why Immutability Matters in React ⭐⭐⭐⭐⭐

Suppose:

```jsx
const [users, setUsers] = useState([
    { id: 1, name: "Sai" }
]);
```

Avoid directly changing:

```javascript
users.push(newUser);
```

Instead:

```javascript
setUsers([...users, newUser]);
```

Why?

Because React state updates should be performed by creating a new array rather than mutating the existing state directly.

---

# 64. Adding an Item in React

Suppose:

```javascript
const [items, setItems] = useState(["Apple", "Banana"]);
```

To add `"Mango"`:

```javascript
setItems([...items, "Mango"]);
```

Result:

```javascript
["Apple", "Banana", "Mango"]
```

---

# 65. Removing an Item in React

Suppose:

```javascript
const [items, setItems] = useState([
    "Apple",
    "Banana",
    "Mango"
]);
```

Remove `"Banana"`:

```javascript
setItems(items.filter((item) => item !== "Banana"));
```

Result:

```javascript
["Apple", "Mango"]
```

This is an extremely common React pattern.

---

# 66. Updating an Object Inside an Array ⭐⭐⭐⭐⭐

Suppose:

```javascript
const users = [
    { id: 1, name: "Sai" },
    { id: 2, name: "Raj" }
];
```

You want to change Raj's name.

Use `map()`:

```javascript
const updatedUsers = users.map((user) =>
    user.id === 2
        ? { ...user, name: "Rahul" }
        : user
);
```

Result:

```javascript
[
    { id: 1, name: "Sai" },
    { id: 2, name: "Rahul" }
]
```

This pattern is **very important for React interviews**.

---

# 67. Array of Objects — React Example ⭐⭐⭐⭐⭐

Consider:

```javascript
const students = [
    {
        id: 1,
        name: "Sai",
        course: "React"
    },
    {
        id: 2,
        name: "Raj",
        course: "Java"
    }
];
```

Render:

```jsx
{students.map((student) => (
    <div key={student.id}>
        <h3>{student.name}</h3>
        <p>{student.course}</p>
    </div>
))}
```

This pattern appears constantly in React applications.

---

# 68. Chaining Array Methods ⭐⭐⭐⭐⭐

You can combine methods.

Example:

```javascript
const numbers = [1, 2, 3, 4, 5, 6];

const result = numbers
    .filter((number) => number % 2 === 0)
    .map((number) => number * 10);

console.log(result);
```

Output:

```javascript
[20, 40, 60]
```

Step 1:

```text
[1,2,3,4,5,6]
```

`filter()`:

```text
[2,4,6]
```

Then `map()`:

```text
[20,40,60]
```

---

# 69. More Complex Chaining

```javascript
const users = [
    { name: "Sai", age: 22 },
    { name: "Raj", age: 17 },
    { name: "John", age: 25 }
];

const names = users
    .filter((user) => user.age >= 18)
    .map((user) => user.name);

console.log(names);
```

Output:

```javascript
["Sai", "John"]
```

This style is extremely useful in React.

---

# 70. `find()` vs `filter()` vs `map()` ⭐⭐⭐⭐⭐

Memorize this table:

| Method        | Purpose                      | Returns               |
| ------------- | ---------------------------- | --------------------- |
| `map()`       | Transform every item         | New array             |
| `filter()`    | Select matching items        | New array             |
| `find()`      | Find first matching item     | Element / `undefined` |
| `findIndex()` | Find first matching position | Number                |
| `some()`      | Check if any matches         | Boolean               |
| `every()`     | Check if all match           | Boolean               |
| `reduce()`    | Combine into one result      | Any value             |
| `forEach()`   | Perform action for each      | `undefined`           |

This table is **very important for React interviews**.

---

# 71. A Simple Way to Remember Them

Think about a student array:

```javascript
const students = [...]
```

### Want to change every student?

```javascript
map()
```

### Want only students who passed?

```javascript
filter()
```

### Want one specific student?

```javascript
find()
```

### Want to know if at least one student passed?

```javascript
some()
```

### Want to know if every student passed?

```javascript
every()
```

### Want to calculate total marks?

```javascript
reduce()
```

---

# 72. Array Destructuring ⭐⭐⭐⭐⭐

You already learned destructuring, but arrays are where it is commonly used.

```javascript
const colors = ["red", "green", "blue"];

const [first, second, third] = colors;

console.log(first);
console.log(second);
console.log(third);
```

Output:

```text
red
green
blue
```

---

# 73. Skipping Array Elements

```javascript
const colors = ["red", "green", "blue"];

const [first, , third] = colors;

console.log(first);
console.log(third);
```

Output:

```text
red
blue
```

---

# 74. Rest With Arrays

```javascript
const numbers = [1, 2, 3, 4, 5];

const [first, ...rest] = numbers;

console.log(first);
console.log(rest);
```

Output:

```text
1
```

```javascript
[2, 3, 4, 5]
```

---

# 75. Spread With Arrays

Copy an array:

```javascript
const numbers = [1, 2, 3];

const copy = [...numbers];

console.log(copy);
```

You now have a new array.

This is very important in React.

---

# 76. Copying an Array Is Not the Same as Deep Copy

Consider:

```javascript
const users = [
    { name: "Sai" }
];

const copy = [...users];
```

The outer array is new, but the object inside is still the same reference.

So:

```text
new array
   ↓
same object reference
```

This leads into your later topics:

* shallow copy
* deep copy
* immutability

We'll cover those separately.

---

# 77. Common Array Mistake #1 ❌

Using:

```javascript
for (let i = 0; i <= array.length; i++)
```

Usually wrong.

Correct:

```javascript
for (let i = 0; i < array.length; i++)
```

Why?

For:

```javascript
["A", "B", "C"]
```

length is:

```text
3
```

Valid indexes:

```text
0, 1, 2
```

There is no index `3`.

---

# 78. Common Array Mistake #2 ❌

Confusing `slice()` and `splice()`.

Remember:

```text
slice  → doesn't mutate
splice → mutates
```

---

# 79. Common Array Mistake #3 ❌

Using `map()` without returning anything.

Incorrect:

```javascript
const result = numbers.map((number) => {
    number * 2;
});
```

Result:

```javascript
[undefined, undefined, undefined]
```

Correct:

```javascript
const result = numbers.map((number) => {
    return number * 2;
});
```

Or:

```javascript
const result = numbers.map((number) => number * 2);
```

---

# 80. Common Array Mistake #4 ❌

Using `filter()` when you need `find()`.

If you need one user:

```javascript
const user = users.find((user) => user.id === 2);
```

If you need all matching users:

```javascript
const usersList = users.filter((user) => user.age > 18);
```

---

# 81. Common Array Mistake #5 ❌

Mutating React state.

Avoid:

```javascript
items.push(newItem);
setItems(items);
```

Prefer:

```javascript
setItems([...items, newItem]);
```

---

# 82. Common Array Mistake #6 ❌

Using `sort()` directly on React state.

Instead of:

```javascript
items.sort();
```

prefer:

```javascript
const sortedItems = [...items].sort();
```

Then update state if necessary.

---

# 83. Interview Output Question ⭐⭐⭐⭐⭐

What is the output?

```javascript
const numbers = [1, 2, 3];

const result = numbers.map((number) => number * 2);

console.log(numbers);
console.log(result);
```

Answer:

```javascript
[1, 2, 3]
```

```javascript
[2, 4, 6]
```

---

# 84. Interview Output Question

```javascript
const numbers = [1, 2, 3, 4];

const result = numbers.filter((number) => number % 2 === 0);

console.log(result);
```

Answer:

```javascript
[2, 4]
```

---

# 85. Interview Output Question

```javascript
const numbers = [10, 20, 30];

const result = numbers.find((number) => number > 15);

console.log(result);
```

Answer:

```text
20
```

Remember:

`find()` stops at the first match.

---

# 86. Interview Output Question

```javascript
const numbers = [1, 2, 3];

console.log(numbers.some((number) => number > 2));
```

Answer:

```text
true
```

---

# 87. Interview Output Question

```javascript
const numbers = [1, 2, 3];

console.log(numbers.every((number) => number > 0));
```

Answer:

```text
true
```

---

# 88. Interview Output Question

```javascript
const numbers = [1, 2, 3];

const result = numbers.reduce(
    (sum, number) => sum + number,
    0
);

console.log(result);
```

Answer:

```text
6
```

---

# 89. Interview Output Question ⭐⭐⭐⭐⭐

What is the output?

```javascript
const numbers = [10, 2, 30];

numbers.sort();

console.log(numbers);
```

The important point is:

> JavaScript's default `sort()` compares elements as strings.

So don't assume numeric sorting.

Correct numeric sorting:

```javascript
numbers.sort((a, b) => a - b);
```

---

# 90. Interview Question: Is `map()` Mutating?

Answer:

> **No. `map()` creates and returns a new array. It doesn't modify the original array itself.**

Example:

```javascript
const numbers = [1, 2, 3];

const result = numbers.map(n => n * 2);
```

Original:

```javascript
[1, 2, 3]
```

New:

```javascript
[2, 4, 6]
```

---

# 91. Interview Question: Is `filter()` Mutating?

No.

```javascript
const result = numbers.filter(...);
```

It returns a new array.

---

# 92. Interview Question: Is `splice()` Mutating?

Yes.

```javascript
numbers.splice(...)
```

changes the original array.

---

# 93. Interview Question: Is `sort()` Mutating?

Yes.

```javascript
numbers.sort(...)
```

changes the original array.

---

# 94. Interview Question: Is `reverse()` Mutating?

Yes.

```javascript
numbers.reverse()
```

changes the original array.

---

# 95. Array Methods — Mutation Cheat Sheet ⭐⭐⭐⭐⭐

### Mutate original:

```text
push()
pop()
shift()
unshift()
splice()
sort()
reverse()
```

### Usually return a new result:

```text
map()
filter()
slice()
concat()
flat()
flatMap()
```

### Search/check:

```text
find()
findIndex()
includes()
indexOf()
some()
every()
```

### Reduce:

```text
reduce()
```

---

# 96. Real React Example — Todo List ⭐⭐⭐⭐⭐

Suppose:

```javascript
const todos = [
    { id: 1, text: "Learn JavaScript", completed: true },
    { id: 2, text: "Learn React", completed: false },
    { id: 3, text: "Learn Redux", completed: false }
];
```

### Render:

```jsx
{todos.map((todo) => (
    <div key={todo.id}>
        {todo.text}
    </div>
))}
```

### Get completed todos:

```javascript
const completedTodos = todos.filter(
    (todo) => todo.completed
);
```

### Find a specific todo:

```javascript
const todo = todos.find(
    (todo) => todo.id === 2
);
```

### Check whether any todo is completed:

```javascript
const hasCompleted = todos.some(
    (todo) => todo.completed
);
```

This is exactly the kind of array manipulation you'll do in React applications.

---

# 97. Array Methods You MUST Know for React ⭐⭐⭐⭐⭐

If your goal is **React interview readiness**, prioritize them like this:

### Extremely important

```text
map()
filter()
find()
reduce()
some()
every()
```

### Very important

```text
push()
pop()
slice()
splice()
includes()
indexOf()
sort()
```

### Important

```text
forEach()
shift()
unshift()
concat()
join()
reverse()
```

### Good to know

```text
flat()
flatMap()
Array.from()
Array.of()
```

---

# 98. The Big Picture

You should now be able to look at:

```javascript
const users = [
    { id: 1, name: "Sai", age: 22 },
    { id: 2, name: "Raj", age: 17 },
    { id: 3, name: "John", age: 25 }
];
```

and know how to do all of these:

### Get names

```javascript
users.map(user => user.name);
```

### Get adults

```javascript
users.filter(user => user.age >= 18);
```

### Find Raj

```javascript
users.find(user => user.name === "Raj");
```

### Check if anyone is under 18

```javascript
users.some(user => user.age < 18);
```

### Check if everyone is over 18

```javascript
users.every(user => user.age >= 18);
```

### Count users

```javascript
users.length;
```

### Find user index

```javascript
users.findIndex(user => user.id === 2);
```

This is the foundation of **real React data handling**.

---

# 99. ⭐ Array Interview Cheat Sheet

```text
Array
│
├── Access
│   ├── arr[index]
│   ├── arr.at()
│   └── arr.length
│
├── Add / Remove
│   ├── push()
│   ├── pop()
│   ├── shift()
│   └── unshift()
│
├── Modify
│   └── splice()
│
├── Copy / Extract
│   └── slice()
│
├── Transform
│   └── map()
│
├── Filter
│   └── filter()
│
├── Search
│   ├── find()
│   ├── findIndex()
│   ├── includes()
│   └── indexOf()
│
├── Check
│   ├── some()
│   └── every()
│
├── Combine
│   ├── concat()
│   └── spread (...)
│
├── Reduce
│   └── reduce()
│
├── Sort
│   ├── sort()
│   └── reverse()
│
└── Convert
    ├── split()
    └── join()
```

---

# 🎯 What You Should Master Before Moving On

For your **React interview preparation**, make sure you can explain and code these without looking at notes:

1. ⭐⭐⭐⭐⭐ Array indexing
2. ⭐⭐⭐⭐⭐ `.length`
3. ⭐⭐⭐⭐⭐ `push`, `pop`, `shift`, `unshift`
4. ⭐⭐⭐⭐⭐ `slice` vs `splice`
5. ⭐⭐⭐⭐⭐ `map`
6. ⭐⭐⭐⭐⭐ `filter`
7. ⭐⭐⭐⭐⭐ `find`
8. ⭐⭐⭐⭐⭐ `some`
9. ⭐⭐⭐⭐⭐ `every`
10. ⭐⭐⭐⭐⭐ `reduce`
11. ⭐⭐⭐⭐⭐ `sort`
12. ⭐⭐⭐⭐⭐ Array of objects
13. ⭐⭐⭐⭐⭐ Array destructuring
14. ⭐⭐⭐⭐⭐ Spread operator with arrays
15. ⭐⭐⭐⭐⭐ Immutable array updates in React
16. ⭐⭐⭐⭐⭐ Rendering arrays using `map()`
17. ⭐⭐⭐⭐⭐ React `key` when rendering lists

### The most important mental model:

```text
map()     → transform every item
filter()  → keep matching items
find()    → get first matching item
some()    → does at least one match?
every()   → do all match?
reduce()  → combine everything into one result
```

Once these six methods are comfortable, a **large part of JavaScript data manipulation used in React** becomes much easier.
