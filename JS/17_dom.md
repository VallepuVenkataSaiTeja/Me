# 17. DOM — Document Object Model ⭐⭐⭐⭐

The **DOM** is an important JavaScript topic, especially for understanding how JavaScript interacts with HTML.

Even though **React usually handles DOM updates for you**, you should understand the DOM well for interviews because React ultimately works with the browser's DOM.

---

# 1. What is the DOM?

**DOM = Document Object Model**

When the browser loads an HTML page, it converts the HTML document into a **tree-like structure of objects**.

JavaScript can then use that structure to:

* find HTML elements
* change text
* change styles
* change attributes
* create elements
* remove elements
* respond to user interactions

### Example HTML

```html
<!DOCTYPE html>
<html>
    <body>
        <h1>Hello</h1>
        <p>Welcome to JavaScript</p>
    </body>
</html>
```

The browser creates a structure approximately like:

```text
Document
   |
   └── html
        |
        └── body
             |
             ├── h1
             │    └── "Hello"
             |
             └── p
                  └── "Welcome to JavaScript"
```

This is the **DOM tree**.

---

# 2. HTML vs DOM

This distinction is important.

### HTML

HTML is the source document:

```html
<h1>Hello</h1>
```

### DOM

The browser creates an object representation of that HTML:

```text
Document
   ↓
HTML Element
   ↓
H1 Element
   ↓
Text Node
```

JavaScript interacts with the **DOM objects**.

---

# 3. Why Do We Need the DOM?

Suppose you have:

```html
<h1>Hello</h1>
```

You want JavaScript to change it to:

```text
Hello Sai
```

JavaScript can access the DOM element and modify it.

```javascript
const heading = document.querySelector("h1");

heading.textContent = "Hello Sai";
```

The HTML displayed in the browser changes.

---

# 4. The `document` Object ⭐⭐⭐⭐⭐

The most important starting point is:

```javascript
document
```

`document` represents the current HTML document/page.

For example:

```javascript
console.log(document);
```

The browser gives you access to the DOM through `document`.

You will frequently use:

```javascript
document.querySelector()
document.querySelectorAll()
document.getElementById()
document.createElement()
```

and many others.

---

# 5. Selecting an Element

Before changing an element, you normally need to **select it**.

There are several ways.

The most important modern methods are:

```javascript
document.getElementById()
document.querySelector()
document.querySelectorAll()
```

---

# 6. `getElementById()` ⭐⭐⭐⭐⭐

HTML:

```html
<h1 id="title">Hello</h1>
```

JavaScript:

```javascript
const heading = document.getElementById("title");

console.log(heading);
```

The important point:

```javascript
document.getElementById("title")
```

looks for:

```html
id="title"
```

---

# 7. Changing Text

Once we have the element:

```javascript
const heading = document.getElementById("title");
```

we can change its text:

```javascript
heading.textContent = "Hello Sai";
```

Example:

```html
<h1 id="title">Hello</h1>

<script>
    const heading = document.getElementById("title");

    heading.textContent = "Hello Sai";
</script>
```

Before:

```text
Hello
```

After:

```text
Hello Sai
```

---

# 8. `querySelector()` ⭐⭐⭐⭐⭐

`querySelector()` allows you to use CSS selectors.

Example:

```html
<h1 id="title">Hello</h1>
```

JavaScript:

```javascript
const heading = document.querySelector("#title");
```

Notice:

```text
#title
```

because `#` represents an ID in CSS selectors.

---

# 9. Selecting a Class

HTML:

```html
<p class="message">Hello</p>
```

JavaScript:

```javascript
const paragraph = document.querySelector(".message");
```

`querySelector()` accepts CSS selectors.

### Examples

```javascript
document.querySelector("#title");
```

ID

```javascript
document.querySelector(".message");
```

Class

```javascript
document.querySelector("p");
```

Element

```javascript
document.querySelector("div p");
```

Nested element

---

# 10. `querySelector()` Returns the First Match

Suppose:

```html
<p class="message">First</p>
<p class="message">Second</p>
<p class="message">Third</p>
```

Then:

```javascript
const message = document.querySelector(".message");

console.log(message.textContent);
```

Output:

```text
First
```

It returns the **first matching element**.

---

# 11. `querySelectorAll()` ⭐⭐⭐⭐⭐

If you want all matching elements:

```javascript
const messages = document.querySelectorAll(".message");
```

For:

```html
<p class="message">First</p>
<p class="message">Second</p>
<p class="message">Third</p>
```

you get a collection containing all three matching elements.

You can use:

```javascript
messages.forEach((message) => {
    console.log(message.textContent);
});
```

Output:

```text
First
Second
Third
```

---

# 12. `querySelector()` vs `querySelectorAll()`

| Method               | Result                 |
| -------------------- | ---------------------- |
| `querySelector()`    | First matching element |
| `querySelectorAll()` | All matching elements  |

Example:

```javascript
document.querySelector(".item");
```

→ first `.item`

```javascript
document.querySelectorAll(".item");
```

→ all `.item` elements

---

# 13. `getElementById()` vs `querySelector()`

### `getElementById()`

```javascript
document.getElementById("title");
```

Only searches by ID.

### `querySelector()`

```javascript
document.querySelector("#title");
```

Can use CSS selectors.

For modern JavaScript, you'll frequently see:

```javascript
document.querySelector()
document.querySelectorAll()
```

---

# 14. Changing `textContent` ⭐⭐⭐⭐⭐

HTML:

```html
<p id="message">Old message</p>
```

JavaScript:

```javascript
const message = document.querySelector("#message");

message.textContent = "New message";
```

Result:

```text
New message
```

---

# 15. `textContent` vs `innerHTML` ⭐⭐⭐⭐⭐

This is a common interview question.

Suppose:

```html
<div id="container"></div>
```

### `textContent`

```javascript
container.textContent = "<h1>Hello</h1>";
```

The browser displays:

```text
<h1>Hello</h1>
```

as text.

It does **not** interpret the HTML.

---

### `innerHTML`

```javascript
container.innerHTML = "<h1>Hello</h1>";
```

Now the browser interprets the HTML.

It creates an actual:

```html
<h1>Hello</h1>
```

element.

### Difference

```text
textContent
    ↓
Treat as text

innerHTML
    ↓
Parse as HTML
```

---

# 16. Important Security Note

Be careful with:

```javascript
element.innerHTML = userInput;
```

If untrusted user input is inserted as HTML, it can create security problems such as **Cross-Site Scripting (XSS)**.

For plain text, prefer:

```javascript
element.textContent = userInput;
```

This is a useful interview point.

---

# 17. Changing CSS with JavaScript

HTML:

```html
<h1 id="title">Hello</h1>
```

JavaScript:

```javascript
const heading = document.querySelector("#title");

heading.style.color = "red";
heading.style.fontSize = "40px";
```

The heading becomes red and larger.

---

# 18. CSS Property Names in JavaScript

CSS:

```css
background-color: blue;
```

JavaScript:

```javascript
element.style.backgroundColor = "blue";
```

CSS uses:

```text
background-color
```

JavaScript uses:

```text
backgroundColor
```

This is called **camelCase**.

More examples:

| CSS                | JavaScript        |
| ------------------ | ----------------- |
| `background-color` | `backgroundColor` |
| `font-size`        | `fontSize`        |
| `margin-top`       | `marginTop`       |
| `border-radius`    | `borderRadius`    |

---

# 19. Changing Attributes ⭐⭐⭐⭐

HTML:

```html
<img id="photo" src="old.jpg">
```

JavaScript:

```javascript
const image = document.querySelector("#photo");

image.setAttribute("src", "new.jpg");
```

Now the image source becomes:

```text
new.jpg
```

---

# 20. `getAttribute()`

To read an attribute:

```javascript
const image = document.querySelector("#photo");

console.log(image.getAttribute("src"));
```

---

# 21. `setAttribute()`

To set/change an attribute:

```javascript
image.setAttribute("src", "new.jpg");
```

General syntax:

```javascript
element.setAttribute("attribute", "value");
```

---

# 22. `removeAttribute()`

You can remove an attribute:

```javascript
element.removeAttribute("disabled");
```

Example:

```html
<button disabled id="btn">Click</button>
```

JavaScript:

```javascript
const button = document.querySelector("#btn");

button.removeAttribute("disabled");
```

The button becomes enabled.

---

# 23. Working with Classes ⭐⭐⭐⭐⭐

Suppose:

```html
<div id="box" class="card"></div>
```

JavaScript gives you:

```javascript
const box = document.querySelector("#box");
```

Then:

```javascript
box.classList
```

allows you to manipulate classes.

---

# 24. `classList.add()`

```javascript
box.classList.add("active");
```

Now:

```html
<div id="box" class="card active"></div>
```

---

# 25. `classList.remove()`

```javascript
box.classList.remove("active");
```

---

# 26. `classList.toggle()` ⭐⭐⭐⭐⭐

`toggle()` adds the class if it doesn't exist and removes it if it does.

```javascript
box.classList.toggle("active");
```

This is very useful for:

* menus
* dark mode
* dropdowns
* showing/hiding elements
* mobile navigation

---

# 27. `classList.contains()`

Check whether an element has a class:

```javascript
if (box.classList.contains("active")) {
    console.log("Active");
}
```

Returns:

```text
true
```

or:

```text
false
```

---

# 28. Creating Elements ⭐⭐⭐⭐⭐

JavaScript can create new HTML elements.

```javascript
const paragraph = document.createElement("p");
```

Now:

```text
paragraph
```

is a new `<p>` DOM element.

---

# 29. Adding Text to the New Element

```javascript
const paragraph = document.createElement("p");

paragraph.textContent = "Hello from JavaScript";
```

Now we have created:

```html
<p>Hello from JavaScript</p>
```

But it isn't necessarily visible yet.

We need to add it to the document.

---

# 30. `appendChild()`

HTML:

```html
<div id="container"></div>
```

JavaScript:

```javascript
const container = document.querySelector("#container");

const paragraph = document.createElement("p");

paragraph.textContent = "Hello";

container.appendChild(paragraph);
```

Result:

```html
<div id="container">
    <p>Hello</p>
</div>
```

---

# 31. Modern `append()`

You can also use:

```javascript
container.append(paragraph);
```

`append()` is more flexible because it can append multiple nodes and text.

Example:

```javascript
container.append(paragraph, "Some text");
```

---

# 32. Removing Elements

Suppose:

```html
<p id="message">Hello</p>
```

You can do:

```javascript
const message = document.querySelector("#message");

message.remove();
```

The element is removed from the DOM.

---

# 33. `removeChild()`

Another approach:

```javascript
const container = document.querySelector("#container");
const message = document.querySelector("#message");

container.removeChild(message);
```

Modern code often uses:

```javascript
message.remove();
```

when you already have the element.

---

# 34. DOM Tree Navigation ⭐⭐⭐⭐

You can move between related elements.

Consider:

```html
<div id="parent">
    <p id="child">Hello</p>
</div>
```

You can get the parent:

```javascript
const child = document.querySelector("#child");

console.log(child.parentElement);
```

---

# 35. `children`

Suppose:

```html
<div id="parent">
    <p>One</p>
    <p>Two</p>
</div>
```

Then:

```javascript
const parent = document.querySelector("#parent");

console.log(parent.children);
```

This gives the child **elements**.

You can access:

```javascript
parent.children[0];
```

and:

```javascript
parent.children[1];
```

---

# 36. `firstElementChild`

```javascript
parent.firstElementChild;
```

Gets the first child element.

---

# 37. `lastElementChild`

```javascript
parent.lastElementChild;
```

Gets the last child element.

---

# 38. `nextElementSibling`

Suppose:

```html
<p id="one">One</p>
<p id="two">Two</p>
<p id="three">Three</p>
```

Then:

```javascript
const first = document.querySelector("#one");

console.log(first.nextElementSibling);
```

gets:

```html
<p id="two">Two</p>
```

---

# 39. `previousElementSibling`

```javascript
const third = document.querySelector("#three");

console.log(third.previousElementSibling);
```

gets:

```html
<p id="two">Two</p>
```

---

# 40. DOM Traversal Cheat Sheet

```text
parentElement
     ↑
     |
element
  ↑  |  ↓
  |  |
previous   next
sibling    sibling

children
   ↓
child elements
```

Common properties:

```javascript
element.parentElement
element.children
element.firstElementChild
element.lastElementChild
element.nextElementSibling
element.previousElementSibling
```

---

# 41. DOM Events ⭐⭐⭐⭐⭐

The DOM becomes much more powerful when combined with **events**.

Examples of browser events:

```text
click
input
change
submit
mouseover
keydown
keyup
focus
blur
```

We'll have a separate **18. Events** topic, but you should understand the basic connection now.

---

# 42. `addEventListener()` ⭐⭐⭐⭐⭐

HTML:

```html
<button id="btn">Click Me</button>
```

JavaScript:

```javascript
const button = document.querySelector("#btn");

button.addEventListener("click", () => {
    console.log("Button clicked");
});
```

When the user clicks:

```text
Button clicked
```

appears in the console.

The function:

```javascript
() => {
    console.log("Button clicked");
}
```

is a **callback**.

This connects our previous topics:

```text
Functions
   ↓
Callbacks
   ↓
Higher-Order Functions
   ↓
DOM Events
```

---

# 43. DOM + Callback Connection

Remember:

```javascript
button.addEventListener("click", handleClick);
```

Here:

```text
addEventListener()
        ↓
Higher-Order Function
        ↓
handleClick
        ↓
Callback
```

The browser calls `handleClick` when the click happens.

---

# 44. Practical DOM Example ⭐⭐⭐⭐⭐

Let's create a small counter.

### HTML

```html
<!DOCTYPE html>
<html>
<head>
    <title>Counter</title>
</head>

<body>

    <h1 id="count">0</h1>

    <button id="increase">Increase</button>

    <script>
        let count = 0;

        const countElement = document.querySelector("#count");
        const button = document.querySelector("#increase");

        button.addEventListener("click", () => {

            count++;

            countElement.textContent = count;
        });
    </script>

</body>
</html>
```

### What happens?

Initially:

```text
0
```

Click:

```text
Increase
```

Then:

```text
1
```

Click again:

```text
2
```

and so on.

---

# 45. Step-by-Step Counter

### Step 1

```javascript
let count = 0;
```

Store the counter value.

### Step 2

```javascript
const countElement = document.querySelector("#count");
```

Find:

```html
<h1 id="count">0</h1>
```

### Step 3

```javascript
const button = document.querySelector("#increase");
```

Find the button.

### Step 4

```javascript
button.addEventListener("click", () => {
```

Listen for clicks.

### Step 5

```javascript
count++;
```

Increase the number.

### Step 6

```javascript
countElement.textContent = count;
```

Update the DOM.

---

# 46. DOM Manipulation Example — To-Do List

HTML:

```html
<input id="taskInput" type="text">

<button id="addButton">
    Add
</button>

<ul id="taskList"></ul>
```

JavaScript:

```javascript
const input = document.querySelector("#taskInput");
const button = document.querySelector("#addButton");
const list = document.querySelector("#taskList");

button.addEventListener("click", () => {

    const task = input.value;

    const li = document.createElement("li");

    li.textContent = task;

    list.appendChild(li);

    input.value = "";
});
```

Now when you enter:

```text
Learn JavaScript
```

and click Add, JavaScript creates:

```html
<li>Learn JavaScript</li>
```

and adds it to the `<ul>`.

This is classic DOM manipulation.

---

# 47. `value` for Form Inputs

For:

```html
<input id="name" type="text">
```

you can get its value:

```javascript
const input = document.querySelector("#name");

console.log(input.value);
```

You can also change it:

```javascript
input.value = "Sai";
```

This is important when working with forms.

---

# 48. `innerText` vs `textContent`

You may see both.

### `textContent`

Gets/sets text content.

```javascript
element.textContent
```

### `innerText`

Represents rendered/visible text more closely and can be affected by CSS/layout.

For most basic DOM manipulation:

```javascript
textContent
```

is usually the clearer choice when you simply need text.

---

# 49. DOM Nodes

The DOM is made up of different kinds of nodes.

Common examples:

```text
Document
Element
Text
Comment
```

For example:

```html
<p>Hello</p>
```

contains:

```text
Element Node
    ↓
   <p>
    ↓
Text Node
    ↓
  Hello
```

For React interviews, you don't need to memorize every node type, but you should understand the basic idea.

---

# 50. DOM vs Virtual DOM ⭐⭐⭐⭐⭐

This is **very important for React interviews**.

### Traditional JavaScript

You can directly manipulate the DOM:

```javascript
document.querySelector("#title").textContent = "Hello";
```

You manually tell the browser what to change.

---

### React

You normally write:

```jsx
<h1>{title}</h1>
```

and change state:

```javascript
setTitle("Hello");
```

React determines what DOM updates are needed.

---

# 51. What is the Virtual DOM?

The **Virtual DOM** is a lightweight JavaScript representation of the UI structure used by React.

Simplified idea:

```text
React State changes
       ↓
React creates/reconciles UI representation
       ↓
Determines necessary changes
       ↓
Updates real DOM
```

Don't think:

> Virtual DOM = a second complete browser DOM.

It is better to think of it as a **JavaScript representation of the UI that React uses during reconciliation**.

---

# 52. DOM vs Virtual DOM

| Real DOM                            | React's Virtual DOM concept         |
| ----------------------------------- | ----------------------------------- |
| Browser's actual document structure | JavaScript representation of UI     |
| Directly manipulated by browser/JS  | Managed by React                    |
| Can be manipulated with DOM APIs    | React calculates/reconciles updates |
| `document.querySelector()`          | JSX/state-driven UI                 |
| Browser DOM                         | React abstraction                   |

---

# 53. Important React Point

Don't say in an interview:

> "React never uses the DOM."

That's incorrect.

React ultimately renders to the **real DOM** in a web application.

The important difference is that React manages UI updates declaratively instead of requiring you to manually manipulate individual DOM elements for normal UI updates.

---

# 54. Imperative vs Declarative UI ⭐⭐⭐⭐⭐

This is a very useful React interview concept.

### Imperative

You tell the browser **how** to change the UI.

```javascript
const heading = document.querySelector("#heading");

heading.textContent = "Hello";
heading.style.color = "red";
```

You explicitly tell it what operations to perform.

---

### Declarative

You describe **what the UI should look like** based on state.

React:

```jsx
<h1>{message}</h1>
```

Then:

```javascript
setMessage("Hello");
```

React handles the necessary DOM updates.

### Mental model

```text
Imperative
→ How should I change the DOM?

Declarative
→ What should the UI look like?
```

React strongly emphasizes the declarative approach.

---

# 55. Common DOM Methods Cheat Sheet

| Method               | Purpose                       |
| -------------------- | ----------------------------- |
| `getElementById()`   | Find element by ID            |
| `querySelector()`    | Find first CSS selector match |
| `querySelectorAll()` | Find all CSS selector matches |
| `createElement()`    | Create element                |
| `appendChild()`      | Add child                     |
| `append()`           | Add content/nodes             |
| `remove()`           | Remove element                |
| `setAttribute()`     | Set attribute                 |
| `getAttribute()`     | Read attribute                |
| `removeAttribute()`  | Remove attribute              |
| `addEventListener()` | Listen for events             |

---

# 56. Common DOM Properties

| Property        | Purpose               |
| --------------- | --------------------- |
| `textContent`   | Get/set text          |
| `innerHTML`     | Get/set HTML          |
| `innerText`     | Get/set rendered text |
| `style`         | Inline styles         |
| `classList`     | Manage classes        |
| `value`         | Form input value      |
| `children`      | Child elements        |
| `parentElement` | Parent element        |

---

# 57. Common `classList` Methods

```javascript
element.classList.add("active");
```

Add.

```javascript
element.classList.remove("active");
```

Remove.

```javascript
element.classList.toggle("active");
```

Toggle.

```javascript
element.classList.contains("active");
```

Check.

---

# 58. Common Mistakes

### Mistake 1 — Forgetting `#`

For:

```html
<h1 id="title">Hello</h1>
```

Correct:

```javascript
document.querySelector("#title");
```

Not:

```javascript
document.querySelector("title");
```

---

### Mistake 2 — Forgetting `.` for class

For:

```html
<p class="message">Hello</p>
```

Correct:

```javascript
document.querySelector(".message");
```

---

### Mistake 3 — Using `querySelector()` when you need all elements

```javascript
document.querySelector(".item");
```

gets only the first matching element.

Use:

```javascript
document.querySelectorAll(".item");
```

for all matching elements.

---

### Mistake 4 — Trying to modify an element that doesn't exist

```javascript
const element = document.querySelector("#doesNotExist");

element.textContent = "Hello";
```

`element` will be `null`, causing an error when you try to access its property.

---

### Mistake 5 — Confusing `textContent` and `innerHTML`

```javascript
element.textContent = "<b>Hello</b>";
```

displays the tags as text.

Whereas:

```javascript
element.innerHTML = "<b>Hello</b>";
```

creates bold HTML.

---

# 59. Interview Questions ⭐⭐⭐⭐⭐

### Q1. What is DOM?

**Answer:**

DOM stands for Document Object Model. It is the browser's object-based representation of an HTML document, organized as a tree of nodes that JavaScript can access and manipulate.

---

### Q2. What is the purpose of the DOM?

It allows JavaScript to interact with HTML elements and dynamically change:

* content
* styles
* attributes
* structure
* event behavior

---

### Q3. What is `document`?

`document` represents the current HTML document and provides APIs for accessing and manipulating the DOM.

---

### Q4. Difference between `querySelector()` and `querySelectorAll()`?

```javascript
querySelector()
```

returns the first matching element.

```javascript
querySelectorAll()
```

returns all matching elements.

---

### Q5. Difference between `textContent` and `innerHTML`?

`textContent` treats the value as text.

`innerHTML` parses the value as HTML.

---

### Q6. How do you create an element?

```javascript
const div = document.createElement("div");
```

---

### Q7. How do you add an element?

```javascript
parent.appendChild(child);
```

or:

```javascript
parent.append(child);
```

---

### Q8. How do you remove an element?

```javascript
element.remove();
```

---

### Q9. How do you change CSS using JavaScript?

```javascript
element.style.color = "red";
```

---

### Q10. How do you add a class?

```javascript
element.classList.add("active");
```

---

### Q11. What is the difference between DOM and Virtual DOM?

The DOM is the browser's actual document structure. React's Virtual DOM concept is a JavaScript representation of UI that React uses during reconciliation before applying necessary updates to the real DOM.

---

### Q12. Does React directly use the DOM?

React web applications ultimately render to and update the real DOM, but React manages those UI updates for you rather than requiring manual DOM manipulation for normal application UI.

---

# 60. Output-Based Interview Questions ⭐⭐⭐⭐⭐

### Question 1

```html
<h1 id="title">Hello</h1>

<script>
    const element = document.querySelector("#title");

    element.textContent = "Welcome";
</script>
```

What appears?

```text
Welcome
```

---

### Question 2

```html
<p class="message">One</p>
<p class="message">Two</p>

<script>
    const element = document.querySelector(".message");

    console.log(element.textContent);
</script>
```

Output:

```text
One
```

Because `querySelector()` returns the first match.

---

### Question 3

```html
<p class="message">One</p>
<p class="message">Two</p>

<script>
    const elements = document.querySelectorAll(".message");

    console.log(elements.length);
</script>
```

Output:

```text
2
```

---

### Question 4

```javascript
const div = document.createElement("div");

div.textContent = "Hello";

console.log(div.textContent);
```

Output:

```text
Hello
```

---

### Question 5

```javascript
const element = document.createElement("p");

element.innerHTML = "<strong>Hello</strong>";
```

The DOM contains a `<strong>` element inside the `<p>`.

Whereas:

```javascript
element.textContent = "<strong>Hello</strong>";
```

contains the literal text:

```text
<strong>Hello</strong>
```

---

# 61. Practical Mini Project — Color Changer

This combines several DOM concepts.

### HTML

```html
<!DOCTYPE html>
<html>

<head>
    <title>Color Changer</title>
</head>

<body>

    <h1 id="title">Hello JavaScript</h1>

    <button id="red">Red</button>
    <button id="blue">Blue</button>
    <button id="green">Green</button>

    <script>

        const title = document.querySelector("#title");

        const redButton = document.querySelector("#red");
        const blueButton = document.querySelector("#blue");
        const greenButton = document.querySelector("#green");

        redButton.addEventListener("click", () => {
            title.style.color = "red";
        });

        blueButton.addEventListener("click", () => {
            title.style.color = "blue";
        });

        greenButton.addEventListener("click", () => {
            title.style.color = "green";
        });

    </script>

</body>

</html>
```

This example uses:

```text
querySelector()
       ↓
DOM selection
       ↓
addEventListener()
       ↓
callback
       ↓
style manipulation
```

So you can see how your previous topics are connecting.

---

# 62. DOM Learning Priority for React ⭐⭐⭐⭐⭐

You don't need to become a DOM expert before learning React.

Focus especially on:

### Must Know

* ⭐⭐⭐⭐⭐ What DOM is
* ⭐⭐⭐⭐⭐ `document`
* ⭐⭐⭐⭐⭐ `querySelector()`
* ⭐⭐⭐⭐⭐ `querySelectorAll()`
* ⭐⭐⭐⭐⭐ `getElementById()`
* ⭐⭐⭐⭐⭐ `textContent`
* ⭐⭐⭐⭐⭐ `innerHTML`
* ⭐⭐⭐⭐⭐ `addEventListener()`
* ⭐⭐⭐⭐⭐ Creating/removing elements
* ⭐⭐⭐⭐⭐ `classList`
* ⭐⭐⭐⭐⭐ DOM vs Virtual DOM
* ⭐⭐⭐⭐⭐ Imperative vs declarative

### Good to Know

* ⭐⭐⭐⭐ `setAttribute()`
* ⭐⭐⭐⭐ `getAttribute()`
* ⭐⭐⭐⭐ `append()`
* ⭐⭐⭐⭐ `appendChild()`
* ⭐⭐⭐⭐ DOM traversal
* ⭐⭐⭐⭐ `value`
* ⭐⭐⭐⭐ `innerText`

---

# 63. Final DOM Cheat Sheet

```text
DOM
│
├── document
│
├── SELECT
│   ├── getElementById()
│   ├── querySelector()
│   └── querySelectorAll()
│
├── CONTENT
│   ├── textContent
│   ├── innerText
│   └── innerHTML
│
├── STYLE
│   └── element.style
│
├── CLASSES
│   └── classList
│       ├── add()
│       ├── remove()
│       ├── toggle()
│       └── contains()
│
├── ATTRIBUTES
│   ├── getAttribute()
│   ├── setAttribute()
│   └── removeAttribute()
│
├── CREATE
│   └── createElement()
│
├── ADD
│   ├── append()
│   └── appendChild()
│
├── REMOVE
│   └── remove()
│
├── TRAVERSAL
│   ├── parentElement
│   ├── children
│   ├── firstElementChild
│   ├── lastElementChild
│   ├── nextElementSibling
│   └── previousElementSibling
│
└── EVENTS
    └── addEventListener()
```

## ⭐ The most important React connection

You should now understand this progression:

```text
JavaScript
    ↓
Functions
    ↓
Callbacks
    ↓
Higher-Order Functions
    ↓
DOM
    ↓
Events
    ↓
React
```

In normal JavaScript, you might write:

```javascript
document.querySelector("#title").textContent = "Hello";
```

In React, you generally don't manually find and update that DOM element. Instead, you change state:

```jsx
setTitle("Hello");
```

and React manages the UI update.