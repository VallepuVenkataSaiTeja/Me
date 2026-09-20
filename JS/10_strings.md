# 10. Strings in JavaScript ⭐⭐⭐

Strings are very common in JavaScript and **very important for React**, because you'll constantly work with:

* User names
* Email addresses
* Form inputs
* API responses
* Search text
* Messages
* URLs
* Dynamic UI text

Let's learn strings from **beginner → interview level**.

---

# 1. What is a String?

A **string** is a sequence of characters used to represent text.

Examples:

```javascript
let name = "Sai";
let city = "Kadapa";
let message = "Hello World!";
```

Here:

```text
"Sai"          → string
"Kadapa"       → string
"Hello World!" → string
```

You can check with:

```javascript
console.log(typeof name);
```

Output:

```text
string
```

---

# 2. Creating Strings

JavaScript provides three common ways.

### Double quotes

```javascript
let name = "Sai";
```

### Single quotes

```javascript
let name = 'Sai';
```

### Backticks

```javascript
let name = `Sai`;
```

All three create strings.

---

# 3. Single vs Double Quotes

These are usually equivalent:

```javascript
let name1 = "Sai";
let name2 = 'Sai';
```

Both contain:

```text
Sai
```

The important thing is to be consistent in your codebase.

---

# 4. Backticks / Template Literals ⭐⭐⭐⭐⭐

Backticks are extremely important in modern JavaScript.

```javascript
let name = `Sai`;
```

But their biggest advantage is **template interpolation**.

```javascript
let name = "Sai";
let age = 22;

let message = `My name is ${name} and I am ${age} years old.`;

console.log(message);
```

Output:

```text
My name is Sai and I am 22 years old.
```

---

# 5. Why `${}` Is Useful

Instead of doing:

```javascript
let name = "Sai";
let age = 22;

let message = "My name is " + name + " and I am " + age + " years old.";
```

you can write:

```javascript
let message = `My name is ${name} and I am ${age} years old.`;
```

This is cleaner.

---

# 6. Template Literals in React ⭐⭐⭐⭐⭐

You'll use this frequently in React.

```jsx
function App() {
    const name = "Sai";

    return <h1>Hello {name}</h1>;
}
```

And in JavaScript:

```javascript
const message = `Welcome, ${name}`;
```

Template literals are especially useful when constructing:

* messages
* URLs
* API endpoints
* CSS class names
* dynamic text

---

# 7. String Length ⭐⭐⭐⭐⭐

Use:

```javascript
.length
```

Example:

```javascript
let name = "Sai";

console.log(name.length);
```

Output:

```text
3
```

Another example:

```javascript
let message = "Hello World";

console.log(message.length);
```

Output:

```text
11
```

Remember:

> `.length` is a **property**, not a function.

So use:

```javascript
name.length
```

not:

```javascript
name.length()
```

---

# 8. Spaces Count in `.length`

Consider:

```javascript
let name = "Sai Teja";

console.log(name.length);
```

Output:

```text
8
```

Why?

Characters:

```text
S a i _ T e j a
1 2 3 4 5 6 7 8
```

The space is also a character.

---

# 9. Accessing Characters ⭐⭐⭐⭐⭐

Strings use **zero-based indexing**.

```javascript
let name = "Sai";
```

Positions:

```text
Character:  S   a   i
Index:      0   1   2
```

You can access:

```javascript
console.log(name[0]);
console.log(name[1]);
console.log(name[2]);
```

Output:

```text
S
a
i
```

---

# 10. First Character

```javascript
let name = "Sai";

console.log(name[0]);
```

Output:

```text
S
```

---

# 11. Last Character ⭐⭐⭐⭐

Use:

```javascript
string[string.length - 1]
```

Example:

```javascript
let name = "Sai";

console.log(name[name.length - 1]);
```

Output:

```text
i
```

Why?

```text
length = 3

last index = 3 - 1
          = 2
```

So:

```javascript
name[2]
```

is:

```text
i
```

---

# 12. `.at()` Method ⭐⭐⭐⭐

Modern JavaScript also provides:

```javascript
.at()
```

Example:

```javascript
let name = "Sai";

console.log(name.at(0));
console.log(name.at(-1));
```

Output:

```text
S
i
```

The nice thing is that negative indexes work:

```javascript
name.at(-1)
```

means the last character.

---

# 13. `charAt()` ⭐⭐⭐

Another way:

```javascript
let name = "Sai";

console.log(name.charAt(0));
```

Output:

```text
S
```

For most modern code, you'll commonly see:

```javascript
name[0]
```

or:

```javascript
name.at(0)
```

---

# 14. Strings Are Immutable ⭐⭐⭐⭐⭐

This is **very important for interviews**.

Strings in JavaScript are **immutable**.

That means you cannot directly change an individual character.

Example:

```javascript
let name = "Sai";

name[0] = "R";

console.log(name);
```

Output:

```text
Sai
```

The string wasn't changed.

---

# 15. How to Change a String

Instead of modifying the original character, create a new string.

```javascript
let name = "Sai";

name = "Raj";

console.log(name);
```

Output:

```text
Raj
```

Or:

```javascript
let name = "Sai";

name = "R" + name.slice(1);

console.log(name);
```

Output:

```text
Rai
```

---

# 16. Why Are Strings Immutable?

When you do:

```javascript
let name = "Sai";
```

you can't do:

```javascript
name[0] = "R";
```

and expect:

```text
Rai
```

Instead, string methods generally return **new strings**.

For example:

```javascript
let name = "sai";

let upperName = name.toUpperCase();

console.log(name);
console.log(upperName);
```

Output:

```text
sai
SAI
```

The original wasn't changed.

---

# 17. `toUpperCase()` ⭐⭐⭐⭐

Converts a string to uppercase.

```javascript
let name = "sai";

console.log(name.toUpperCase());
```

Output:

```text
SAI
```

---

# 18. `toLowerCase()` ⭐⭐⭐⭐

Converts a string to lowercase.

```javascript
let name = "SAI";

console.log(name.toLowerCase());
```

Output:

```text
sai
```

Very useful for case-insensitive comparisons.

---

# 19. Real Example: Case-Insensitive Comparison

Suppose:

```javascript
let input = "SAI";
```

and you want to check whether the user entered `"sai"`.

Instead of:

```javascript
if (input === "sai") {
```

you can use:

```javascript
if (input.toLowerCase() === "sai") {
    console.log("Matched");
}
```

---

# 20. `trim()` ⭐⭐⭐⭐⭐

`trim()` removes whitespace from the beginning and end.

```javascript
let name = "   Sai   ";

console.log(name.trim());
```

Output:

```text
Sai
```

This is extremely common with form inputs.

---

# 21. `trimStart()`

Removes whitespace from the beginning.

```javascript
let name = "   Sai   ";

console.log(name.trimStart());
```

Result:

```text
"Sai   "
```

---

# 22. `trimEnd()`

Removes whitespace from the end.

```javascript
let name = "   Sai   ";

console.log(name.trimEnd());
```

Result:

```text
"   Sai"
```

---

# 23. `includes()` ⭐⭐⭐⭐⭐

Checks whether a string contains another string.

```javascript
let message = "Hello Sai";

console.log(message.includes("Sai"));
```

Output:

```text
true
```

Example:

```javascript
console.log(message.includes("Raj"));
```

Output:

```text
false
```

---

# 24. `includes()` Is Case-Sensitive

```javascript
let name = "Sai";

console.log(name.includes("sai"));
```

Output:

```text
false
```

Because:

```text
Sai
sai
```

are different strings.

For case-insensitive searching:

```javascript
let name = "Sai";

console.log(name.toLowerCase().includes("sai"));
```

Output:

```text
true
```

---

# 25. `startsWith()` ⭐⭐⭐

Checks whether a string starts with a particular value.

```javascript
let url = "https://example.com";

console.log(url.startsWith("https"));
```

Output:

```text
true
```

---

# 26. `endsWith()` ⭐⭐⭐

Checks whether a string ends with a particular value.

```javascript
let file = "resume.pdf";

console.log(file.endsWith(".pdf"));
```

Output:

```text
true
```

Useful for checking file extensions.

---

# 27. `indexOf()` ⭐⭐⭐⭐⭐

Returns the position of the first occurrence of a value.

```javascript
let message = "Hello World";

console.log(message.indexOf("World"));
```

Output:

```text
6
```

Because:

```text
H e l l o _ W o r l d
0 1 2 3 4 5 6 7 8 9 10
```

---

# 28. `indexOf()` When Not Found

```javascript
let message = "Hello World";

console.log(message.indexOf("Sai"));
```

Output:

```text
-1
```

So:

```text
index >= 0
```

means the value was found.

---

# 29. `lastIndexOf()` ⭐⭐⭐

Finds the last occurrence.

```javascript
let text = "hello hello";

console.log(text.lastIndexOf("hello"));
```

Output:

```text
6
```

---

# 30. `search()` ⭐⭐⭐

`search()` searches for a pattern and returns its index.

```javascript
let text = "Hello World";

console.log(text.search("World"));
```

Output:

```text
6
```

It is especially useful with regular expressions.

```javascript
let text = "Hello 123";

console.log(text.search(/\d/));
```

Output:

```text
6
```

---

# 31. `slice()` ⭐⭐⭐⭐⭐

`slice()` extracts part of a string.

Syntax:

```javascript
string.slice(start, end)
```

Example:

```javascript
let text = "JavaScript";

console.log(text.slice(0, 4));
```

Output:

```text
Java
```

Important:

> The `end` index is **not included**.

---

# 32. Understanding `slice()`

```javascript
let text = "JavaScript";
```

Indexes:

```text
J a v a S c r i p t
0 1 2 3 4 5 6 7 8 9
```

```javascript
text.slice(0, 4)
```

takes:

```text
0 1 2 3
```

Result:

```text
Java
```

---

# 33. `slice()` With One Argument

```javascript
let text = "JavaScript";

console.log(text.slice(4));
```

Output:

```text
Script
```

It means:

> Start at index 4 and continue to the end.

---

# 34. `slice()` With Negative Index ⭐⭐⭐⭐

```javascript
let text = "JavaScript";

console.log(text.slice(-6));
```

Output:

```text
Script
```

Negative indexes count from the end.

---

# 35. `substring()` ⭐⭐⭐

Another method for extracting strings:

```javascript
let text = "JavaScript";

console.log(text.substring(0, 4));
```

Output:

```text
Java
```

For most everyday code, `slice()` is often easier to reason about, especially because `slice()` supports negative indexes.

---

# 36. `substr()` ⚠️

You may see:

```javascript
substr()
```

in older code.

It is **deprecated/legacy** and should generally not be used in new code.

Prefer:

```javascript
slice()
```

or:

```javascript
substring()
```

---

# 37. `replace()` ⭐⭐⭐⭐⭐

Replaces a matching part of a string.

```javascript
let text = "Hello World";

let result = text.replace("World", "Sai");

console.log(result);
```

Output:

```text
Hello Sai
```

Important:

`replace()` returns a new string.

---

# 38. `replace()` Replaces the First Match

```javascript
let text = "apple apple";

console.log(text.replace("apple", "banana"));
```

Output:

```text
banana apple
```

Only the first match is replaced.

---

# 39. `replaceAll()` ⭐⭐⭐⭐

To replace all matching occurrences:

```javascript
let text = "apple apple";

console.log(text.replaceAll("apple", "banana"));
```

Output:

```text
banana banana
```

---

# 40. `split()` ⭐⭐⭐⭐⭐

`split()` converts a string into an array.

This is very important.

```javascript
let fruits = "apple,banana,mango";

let result = fruits.split(",");

console.log(result);
```

Output:

```javascript
["apple", "banana", "mango"]
```

Now you have an array.

---

# 41. Splitting by Spaces

```javascript
let name = "Sai Teja";

console.log(name.split(" "));
```

Output:

```javascript
["Sai", "Teja"]
```

---

# 42. Splitting Into Individual Characters

```javascript
let word = "Hello";

console.log(word.split(""));
```

Output:

```javascript
["H", "e", "l", "l", "o"]
```

---

# 43. `split()` and React

Suppose an API returns:

```javascript
const skills = "HTML,CSS,JavaScript,React";
```

You can convert it to an array:

```javascript
const skillList = skills.split(",");
```

Result:

```javascript
["HTML", "CSS", "JavaScript", "React"]
```

Then React can render it using `.map()`:

```jsx
{skillList.map((skill) => (
    <li key={skill}>{skill}</li>
))}
```

This connects strings directly with your React knowledge.

---

# 44. `concat()` ⭐⭐

You can join strings with `concat()`:

```javascript
let first = "Hello";
let second = "World";

console.log(first.concat(" ", second));
```

Output:

```text
Hello World
```

However, modern JavaScript usually prefers:

```javascript
`${first} ${second}`
```

or:

```javascript
first + " " + second
```

---

# 45. String Concatenation With `+`

```javascript
let firstName = "Sai";
let lastName = "Teja";

let fullName = firstName + " " + lastName;

console.log(fullName);
```

Output:

```text
Sai Teja
```

---

# 46. String Concatenation and Type Coercion

Remember your previous topic:

```javascript
console.log("Age: " + 22);
```

Output:

```text
Age: 22
```

The number is converted to a string.

Another example:

```javascript
console.log("5" + 2);
```

Output:

```text
52
```

Because `+` can perform string concatenation.

---

# 47. Escape Characters ⭐⭐⭐

Sometimes you need special characters inside strings.

### New line

```javascript
let message = "Hello\nWorld";

console.log(message);
```

Output:

```text
Hello
World
```

### Tab

```javascript
let message = "Hello\tWorld";
```

### Quote inside a string

```javascript
let message = "He said \"Hello\"";
```

Output:

```text
He said "Hello"
```

---

# 48. Using Different Quotes

You can sometimes avoid escaping:

```javascript
let message = 'He said "Hello"';
```

Or:

```javascript
let message = "It's good";
```

---

# 49. Multiline Strings

With backticks:

```javascript
let message = `
Hello Sai,
Welcome to JavaScript.
Good luck with your interview preparation!
`;

console.log(message);
```

Template literals can contain multiple lines.

---

# 50. Comparing Strings ⭐⭐⭐⭐

You can use:

```javascript
===
```

Example:

```javascript
let a = "hello";
let b = "hello";

console.log(a === b);
```

Output:

```text
true
```

---

# 51. String Comparison Is Case-Sensitive

```javascript
console.log("Hello" === "hello");
```

Output:

```text
false
```

Because:

```text
H ≠ h
```

---

# 52. String Comparison With `<` and `>`

JavaScript can compare strings lexicographically.

```javascript
console.log("apple" < "banana");
```

Output:

```text
true
```

The comparison is based on Unicode code point ordering.

For normal beginner/interview work, focus more on:

```javascript
===
```

and case normalization.

---

# 53. Convert Other Values to Strings ⭐⭐⭐⭐

Use:

```javascript
String()
```

Example:

```javascript
let number = 123;

let text = String(number);

console.log(text);
console.log(typeof text);
```

Output:

```text
123
string
```

---

# 54. `.toString()`

You can also use:

```javascript
let number = 123;

console.log(number.toString());
```

Output:

```text
123
```

But be careful with:

```javascript
null.toString()
```

and:

```javascript
undefined.toString()
```

These cause errors.

`String(null)` is safer when you explicitly want conversion:

```javascript
String(null)
```

gives:

```text
"null"
```

---

# 55. Common String Methods Cheat Sheet ⭐⭐⭐⭐⭐

| Method           | Purpose                     |
| ---------------- | --------------------------- |
| `.length`        | Get length                  |
| `.at()`          | Get character               |
| `.charAt()`      | Get character               |
| `.toUpperCase()` | Uppercase                   |
| `.toLowerCase()` | Lowercase                   |
| `.trim()`        | Remove outer whitespace     |
| `.trimStart()`   | Remove beginning whitespace |
| `.trimEnd()`     | Remove ending whitespace    |
| `.includes()`    | Check if contained          |
| `.startsWith()`  | Check beginning             |
| `.endsWith()`    | Check ending                |
| `.indexOf()`     | Find first index            |
| `.lastIndexOf()` | Find last index             |
| `.slice()`       | Extract part                |
| `.substring()`   | Extract part                |
| `.replace()`     | Replace first match         |
| `.replaceAll()`  | Replace all matches         |
| `.split()`       | Convert string to array     |
| `.concat()`      | Join strings                |

---

# 56. Very Important String Methods for React

For your React interviews, prioritize:

```text
⭐⭐⭐⭐⭐ .length
⭐⭐⭐⭐⭐ .toUpperCase()
⭐⭐⭐⭐⭐ .toLowerCase()
⭐⭐⭐⭐⭐ .trim()
⭐⭐⭐⭐⭐ .includes()
⭐⭐⭐⭐⭐ .slice()
⭐⭐⭐⭐⭐ .split()
⭐⭐⭐⭐⭐ .replace()
⭐⭐⭐⭐⭐ template literals
⭐⭐⭐⭐⭐ string indexing
```

You don't need to memorize every obscure string method.

---

# 57. Real-World Example: Username Validation

Suppose:

```javascript
let username = "   Sai   ";
```

You can clean it:

```javascript
username = username.trim();
```

Then:

```javascript
console.log(username);
```

Output:

```text
Sai
```

Then:

```javascript
if (username.toLowerCase() === "sai") {
    console.log("Username matched");
}
```

This is a realistic form-validation pattern.

---

# 58. Real-World Example: Email Validation

Basic checks:

```javascript
let email = "sai@gmail.com";

if (email.includes("@") && email.endsWith(".com")) {
    console.log("Looks valid");
}
```

This isn't a complete email validator, but it demonstrates useful string methods.

---

# 59. Real-World Example: Extract Username From Email

```javascript
let email = "sai@gmail.com";

let username = email.split("@")[0];

console.log(username);
```

Output:

```text
sai
```

Step by step:

```javascript
email.split("@")
```

produces:

```javascript
["sai", "gmail.com"]
```

Then:

```javascript
[0]
```

gets:

```text
sai
```

---

# 60. Real-World Example: Get File Extension

```javascript
let fileName = "resume.pdf";

let extension = fileName.split(".").pop();

console.log(extension);
```

Output:

```text
pdf
```

This combines:

* `split()`
* arrays
* `.pop()`

---

# 61. Real-World Example: Capitalize First Letter

JavaScript doesn't have a built-in `capitalize()` method.

You can write:

```javascript
let name = "sai";

let result = name[0].toUpperCase() + name.slice(1);

console.log(result);
```

Output:

```text
Sai
```

Step by step:

```javascript
name[0]
```

→ `"s"`

```javascript
name[0].toUpperCase()
```

→ `"S"`

```javascript
name.slice(1)
```

→ `"ai"`

Then:

```text
"S" + "ai"
```

→ `"Sai"`

---

# 62. Real-World Example: Reverse a String

A common interview coding question:

```javascript
let text = "hello";

let result = text.split("").reverse().join("");

console.log(result);
```

Output:

```text
olleh
```

What's happening?

### Step 1

```javascript
text.split("")
```

```javascript
["h", "e", "l", "l", "o"]
```

### Step 2

```javascript
.reverse()
```

```javascript
["o", "l", "l", "e", "h"]
```

### Step 3

```javascript
.join("")
```

```text
olleh
```

---

# 63. `join()` — Related to Strings ⭐⭐⭐⭐

`join()` is actually an **array method**, but it's commonly used with strings.

```javascript
let letters = ["H", "e", "l", "l", "o"];

console.log(letters.join(""));
```

Output:

```text
Hello
```

With a separator:

```javascript
let words = ["Hello", "World"];

console.log(words.join(" "));
```

Output:

```text
Hello World
```

---

# 64. Important: `split()` vs `join()`

Remember this pair:

```text
String
   ↓ split()
Array
```

and:

```text
Array
   ↓ join()
String
```

Example:

```javascript
let text = "Hello World";

let arr = text.split(" ");

console.log(arr);
```

```javascript
["Hello", "World"]
```

Then:

```javascript
let result = arr.join(" ");

console.log(result);
```

```text
Hello World
```

---

# 65. String Immutability ⭐⭐⭐⭐⭐

This interview question is very common:

**"Are JavaScript strings mutable?"**

Answer:

> **No. Strings are immutable in JavaScript. String methods return new strings rather than modifying the original string.**

Example:

```javascript
let text = "hello";

text.toUpperCase();

console.log(text);
```

Output:

```text
hello
```

Because you didn't store the returned string.

Correct:

```javascript
text = text.toUpperCase();

console.log(text);
```

Output:

```text
HELLO
```

---

# 66. `replace()` Doesn't Modify the Original

```javascript
let text = "Hello World";

text.replace("World", "Sai");

console.log(text);
```

Output:

```text
Hello World
```

Correct:

```javascript
text = text.replace("World", "Sai");
```

Now:

```text
Hello Sai
```

---

# 67. String Methods Can Be Chained ⭐⭐⭐⭐

You can combine methods.

Example:

```javascript
let name = "   sai   ";

let result = name.trim().toUpperCase();

console.log(result);
```

Output:

```text
SAI
```

Another:

```javascript
let text = "Hello World";

let result = text.toLowerCase().includes("world");

console.log(result);
```

Output:

```text
true
```

This is called **method chaining**.

---

# 68. Important Interview Question

What is the output?

```javascript
let text = "hello";

console.log(text.toUpperCase());
console.log(text);
```

Answer:

```text
HELLO
hello
```

Why?

Because strings are immutable.

---

# 69. Important Interview Question

```javascript
let text = "JavaScript";

console.log(text.slice(4, 10));
```

Indexes:

```text
J a v a S c r i p t
0 1 2 3 4 5 6 7 8 9
```

`slice(4, 10)`:

```text
Script
```

Output:

```text
Script
```

---

# 70. Important Interview Question

```javascript
let text = "Hello";

console.log(text.includes("hello"));
```

Output:

```text
false
```

Because `includes()` is case-sensitive.

---

# 71. Important Interview Question

```javascript
let text = "JavaScript";

console.log(text.indexOf("Script"));
```

Output:

```text
4
```

---

# 72. Important Interview Question

```javascript
let text = "Hello";

console.log(text[10]);
```

Output:

```text
undefined
```

There is no character at index 10.

---

# 73. Important Interview Question

```javascript
let text = "Hello";

console.log(text.at(-1));
```

Output:

```text
o
```

This is a useful modern JavaScript feature.

---

# 74. Strings and `null` / `undefined`

Be careful:

```javascript
let value = null;

console.log(value.length);
```

This causes an error because `null` doesn't have string properties.

In React/API data, you may receive:

```javascript
const username = user?.name ?? "";
```

Then safely work with it:

```javascript
username.trim()
```

This connects directly with the `?.` and `??` operators you already learned.

---

# 75. Strings + React Form Inputs ⭐⭐⭐⭐⭐

This is especially important for you.

HTML inputs normally give you **string values**.

For example:

```jsx
<input
    type="text"
    value={name}
    onChange={(e) => setName(e.target.value)}
/>
```

Here:

```javascript
e.target.value
```

is a string.

Even for:

```jsx
<input type="number" />
```

the `value` from the input event is commonly a string.

So you may need:

```javascript
Number(e.target.value)
```

when you actually need a number.

This connects your **Strings + Type Conversion + React Forms** knowledge.

---

# 76. Strings + Conditional Rendering

You may write:

```jsx
{username && <p>Hello {username}</p>}
```

If `username` is:

```javascript
""
```

it's falsy.

If:

```javascript
"Sai"
```

it's truthy.

So your previous knowledge of:

* strings
* truthy/falsy
* logical operators
* React rendering

all work together.

---

# 77. Strings + API Data

Suppose an API gives:

```javascript
{
    name: "Sai",
    email: "SAI@GMAIL.COM"
}
```

You might normalize:

```javascript
const email = user.email.trim().toLowerCase();
```

Result:

```text
sai@gmail.com
```

This is very common in real applications.

---

# 78. String Methods You Should Memorize

For interviews, remember these groups:

### Access

```javascript
str.length
str[index]
str.at(index)
str.charAt(index)
```

### Case

```javascript
str.toUpperCase()
str.toLowerCase()
```

### Whitespace

```javascript
str.trim()
str.trimStart()
str.trimEnd()
```

### Search

```javascript
str.includes()
str.indexOf()
str.lastIndexOf()
str.startsWith()
str.endsWith()
```

### Extract

```javascript
str.slice()
str.substring()
```

### Modify/Create new string

```javascript
str.replace()
str.replaceAll()
```

### Convert

```javascript
str.split()
```

### Combine

```javascript
array.join()
```

---

# 79. Most Important Interview Questions ⭐⭐⭐⭐⭐

You should be able to answer:

1. What is a string in JavaScript?
2. How do you create a string?
3. What is a template literal?
4. What is string interpolation?
5. How do you find string length?
6. How do you access a character?
7. How do you get the last character?
8. What is `.at()`?
9. Are strings mutable or immutable?
10. What does `toUpperCase()` do?
11. What does `trim()` do?
12. What does `includes()` return?
13. Difference between `indexOf()` and `includes()`?
14. What does `slice()` do?
15. Difference between `slice()` and `substring()`?
16. Difference between `replace()` and `replaceAll()`?
17. What does `split()` do?
18. How do you reverse a string?
19. How do you convert a string to uppercase?
20. How do you compare strings?
21. Why is `"Hello" === "hello"` false?
22. How do you check whether a string starts/ends with something?
23. How do you remove spaces from user input?
24. How do you convert a string to an array?
25. How are strings commonly used in React forms?

---

# 80. ⭐ String Cheat Sheet

```javascript
const str = "JavaScript";
```

```javascript
str.length
// 10
```

```javascript
str[0]
// "J"
```

```javascript
str.at(-1)
// "t"
```

```javascript
str.toUpperCase()
// "JAVASCRIPT"
```

```javascript
str.toLowerCase()
// "javascript"
```

```javascript
str.includes("Script")
// true
```

```javascript
str.startsWith("Java")
// true
```

```javascript
str.endsWith("ipt")
// true
```

```javascript
str.indexOf("Script")
// 4
```

```javascript
str.slice(0, 4)
// "Java"
```

```javascript
str.replace("Java", "Type")
// "TypeScript"
```

```javascript
"a,b,c".split(",")
// ["a", "b", "c"]
```

```javascript
["a", "b", "c"].join("-")
// "a-b-c"
```

```javascript
"   Sai   ".trim()
// "Sai"
```

---

# 🎯 What You Need to Master for React Interviews

Don't try to memorize every string method equally.

Focus heavily on:

**⭐⭐⭐⭐⭐**

* String indexing
* `.length`
* Template literals
* String immutability
* `.toUpperCase()`
* `.toLowerCase()`
* `.trim()`
* `.includes()`
* `.indexOf()`
* `.slice()`
* `.replace()`
* `.split()`
* `split()` + `join()`
* String comparison
* Strings in React form inputs

And especially understand this relationship:

```text
String
   │
   ├── trim()
   ├── toLowerCase()
   ├── includes()
   ├── slice()
   ├── replace()
   └── split()
             ↓
           Array
             ↓
           map()
             ↓
       React rendering
```

That connection between **JavaScript strings → arrays → `map()` → React UI** is particularly useful in real React development.