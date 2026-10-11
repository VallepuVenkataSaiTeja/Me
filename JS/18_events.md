# 17.7 DOM — Events ⭐⭐⭐

**DOM Events are one of the most important JavaScript topics for interviews and real-world frontend development.**

So far, we learned how JavaScript can **find, modify, create, and remove HTML elements**.

Events answer the next important question:

> **How do we make a webpage respond when the user does something?**

For example:

- User clicks a button → run some code
- User types in an input → update something
- User submits a form → validate data
- User moves the mouse → change something
- User presses a keyboard key → perform an action
- User selects an option → update the UI

---

# 1. What is a DOM Event?

An **event** is something that happens in the browser.

Examples:

```text
User clicks a button
        ↓
click event

User types in input
        ↓
input event

User submits form
        ↓
submit event

User presses keyboard key
        ↓
keydown event

User moves mouse
        ↓
mousemove event
```

JavaScript can **listen for these events** and execute code when they happen.

---

# 2. Simple Example

### HTML

```html
<button id="btn">Click Me</button>
```

### JavaScript

```javascript
const button = document.getElementById("btn");

button.addEventListener("click", function () {
    alert("Button clicked!");
});
```

When the user clicks:

```text
Click button
     ↓
click event occurs
     ↓
event listener detects it
     ↓
function runs
     ↓
alert appears
```

---

# 3. `addEventListener()` ⭐⭐⭐

The most important method for handling events is:

```javascript
element.addEventListener();
```

### Syntax

```javascript
element.addEventListener("event", function () {
    // code
});
```

Example:

```javascript
button.addEventListener("click", function () {
    console.log("Clicked!");
});
```

There are three important parts:

```javascript
button.addEventListener("click", function () {
    console.log("Clicked!");
});
```

### Part 1

```javascript
button
```

The element we want to monitor.

### Part 2

```javascript
"click"
```

The event we want to listen for.

### Part 3

```javascript
function () {
    console.log("Clicked!");
}
```

The code that runs when the event happens.

---

# 4. Why Use `addEventListener()`?

You might see older code like:

```javascript
button.onclick = function () {
    alert("Clicked");
};
```

This works.

But generally, prefer:

```javascript
button.addEventListener("click", function () {
    alert("Clicked");
});
```

because `addEventListener()` is more flexible and allows multiple listeners.

---

# 5. `onclick` vs `addEventListener()` ⭐⭐⭐

### `onclick`

```javascript
button.onclick = function () {
    console.log("Hello");
};
```

### `addEventListener()`

```javascript
button.addEventListener("click", function () {
    console.log("Hello");
});
```

The important difference is that assigning `onclick` repeatedly replaces the previous handler:

```javascript
button.onclick = function () {
    console.log("First");
};

button.onclick = function () {
    console.log("Second");
};
```

Only `"Second"` runs.

With `addEventListener()`:

```javascript
button.addEventListener("click", function () {
    console.log("First");
});

button.addEventListener("click", function () {
    console.log("Second");
});
```

Both can run.

```text
First
Second
```

### Interview answer

> `addEventListener()` is generally preferred because multiple listeners can be attached to the same event and it provides better event management.

---

# 6. Common DOM Events ⭐⭐⭐

You should know these events very well.

## Mouse events

```text
click
dblclick
mousedown
mouseup
mousemove
mouseenter
mouseleave
mouseover
mouseout
```

---

## Keyboard events

```text
keydown
keyup
keypress
```

`keydown` and `keyup` are the important modern ones.

---

## Form events

```text
submit
input
change
focus
blur
```

---

## Window events

```text
load
DOMContentLoaded
resize
scroll
```

We'll study many of these individually.

---

# 7. `click` Event ⭐⭐⭐

Probably the most commonly used DOM event.

### HTML

```html
<button id="btn">Click Me</button>
```

### JavaScript

```javascript
const btn = document.getElementById("btn");

btn.addEventListener("click", function () {
    console.log("Button clicked");
});
```

Every click runs the function.

---

# 8. Double Click — `dblclick`

You can listen for a double click:

```javascript
btn.addEventListener("dblclick", function () {
    console.log("Double clicked");
});
```

The function runs when the user double-clicks.

---

# 9. Mouse Events

There are several mouse events.

### `mousedown`

Fires when the mouse button is pressed down.

```javascript
element.addEventListener("mousedown", function () {
    console.log("Mouse button pressed");
});
```

### `mouseup`

Fires when the mouse button is released.

```javascript
element.addEventListener("mouseup", function () {
    console.log("Mouse button released");
});
```

---

# 10. `mouseenter`

Fires when the mouse enters an element.

```javascript
box.addEventListener("mouseenter", function () {
    console.log("Mouse entered");
});
```

---

# 11. `mouseleave`

Fires when the mouse leaves an element.

```javascript
box.addEventListener("mouseleave", function () {
    console.log("Mouse left");
});
```

A simple hover-style example:

```javascript
box.addEventListener("mouseenter", function () {
    box.style.backgroundColor = "blue";
});

box.addEventListener("mouseleave", function () {
    box.style.backgroundColor = "white";
});
```

---

# 12. `mouseover` vs `mouseenter`

This is a common interview question.

Both happen when the mouse enters an element, but they behave differently with child elements.

### `mouseenter`

Doesn't bubble from child elements.

### `mouseover`

Can fire again when moving between the parent and its child elements.

For basic hover behavior, `mouseenter` / `mouseleave` are often easier to reason about.

---

# 13. Keyboard Events ⭐⭐⭐

JavaScript can detect keyboard actions.

The important events are:

```text
keydown
keyup
```

---

# 14. `keydown`

Fires when a key is pressed.

```javascript
document.addEventListener("keydown", function () {
    console.log("Key pressed");
});
```

If you press:

```text
A
```

the event occurs.

---

# 15. `keyup`

Fires when the key is released.

```javascript
document.addEventListener("keyup", function () {
    console.log("Key released");
});
```

Sequence:

```text
Press key
   ↓
keydown

Release key
   ↓
keyup
```

---

# 16. Detecting Which Key Was Pressed

This is where the **Event Object** becomes important.

```javascript
document.addEventListener("keydown", function (event) {
    console.log(event.key);
});
```

If you press:

```text
A
```

you may get:

```text
a
```

If you press Enter:

```text
Enter
```

If you press Escape:

```text
Escape
```

If you press ArrowUp:

```text
ArrowUp
```

---

# 17. `event.key`

Example:

```javascript
document.addEventListener("keydown", function (event) {
    console.log("You pressed:", event.key);
});
```

Possible output:

```text
You pressed: a
```

or:

```text
You pressed: Enter
```

or:

```text
You pressed: ArrowDown
```

We'll study the **Event Object** in much more detail in the next topic.

---

# 18. Practical Example — Press Enter

Suppose:

```html
<input id="username" type="text">
```

JavaScript:

```javascript
const input = document.getElementById("username");

input.addEventListener("keydown", function (event) {

    if (event.key === "Enter") {
        console.log("Enter pressed");
    }

});
```

Now pressing Enter inside the input runs the code.

---

# 19. `input` Event ⭐⭐⭐

The `input` event fires whenever the value of an input changes due to user input.

### HTML

```html
<input id="name" type="text">
```

### JavaScript

```javascript
const input = document.getElementById("name");

input.addEventListener("input", function () {
    console.log(input.value);
});
```

If the user types:

```text
S
Sa
Sai
Sai T
Sai Te
```

the event fires as the value changes.

This is extremely useful for:

- Live search
- Character counters
- Form validation
- Live previews
- Filtering data

---

# 20. `change` Event

The `change` event is used when the value has been changed and the browser considers the change committed.

For a text input, it generally fires after the user changes the value and then leaves the field.

```javascript
input.addEventListener("change", function () {
    console.log("Value changed");
});
```

For controls such as `<select>`, it fires when the selected value changes.

---

# 21. `input` vs `change` ⭐⭐⭐

Very important interview comparison.

### `input`

Fires as the user changes the value.

```text
Type S
 ↓
input

Type Sa
 ↓
input

Type Sai
 ↓
input
```

### `change`

Fires when the change is committed.

For text inputs, this is commonly after leaving the field.

```text
Type Sai
 ↓
Leave input
 ↓
change
```

For a `<select>`, `change` fires when the selected option changes.

---

# 22. `focus` Event

Fires when an element receives focus.

```javascript
input.addEventListener("focus", function () {
    console.log("Input focused");
});
```

For example:

```text
Click inside input
       ↓
focus event
```

---

# 23. `blur` Event

Fires when an element loses focus.

```javascript
input.addEventListener("blur", function () {
    console.log("Input lost focus");
});
```

Sequence:

```text
Click input
    ↓
focus

Click somewhere else
    ↓
blur
```

Very useful for form validation.

---

# 24. Form `submit` Event ⭐⭐⭐

Suppose:

```html
<form id="loginForm">

    <input type="text">

    <button type="submit">
        Login
    </button>

</form>
```

JavaScript:

```javascript
const form = document.getElementById("loginForm");

form.addEventListener("submit", function () {
    console.log("Form submitted");
});
```

The `submit` event belongs to the **form**, not the button.

---

# 25. Why `submit` Is Better Than Button `click`

You might write:

```javascript
button.addEventListener("click", function () {
    // submit logic
});
```

But a form can also be submitted by:

- Clicking the submit button
- Pressing Enter in an appropriate form field
- Other browser/form mechanisms

Therefore, for form submission logic, listen for:

```javascript
form.addEventListener("submit", ...)
```

rather than relying only on the button's `click`.

---

# 26. Important: `preventDefault()`

When a form is submitted, the browser normally performs its default form action, which may navigate/reload the page.

You can prevent that:

```javascript
form.addEventListener("submit", function (event) {

    event.preventDefault();

    console.log("Form submission stopped");

});
```

This is extremely common in JavaScript applications.

For example:

```javascript
form.addEventListener("submit", function (event) {

    event.preventDefault();

    // Validate form
    // Send data using fetch()
    // Show success message

});
```

We'll study `preventDefault()` properly with the Event Object.

---

# 27. `load` Event

The `load` event occurs when a resource has finished loading.

For the window:

```javascript
window.addEventListener("load", function () {
    console.log("Page fully loaded");
});
```

This waits for the page's resources, such as images, to load as well.

---

# 28. `DOMContentLoaded`

Another important event:

```javascript
document.addEventListener("DOMContentLoaded", function () {
    console.log("DOM is ready");
});
```

It fires when the HTML has been parsed and the DOM is ready.

It does **not** wait for every image/resource to finish loading.

### Difference

```text
DOMContentLoaded
    ↓
HTML parsed + DOM ready

load
    ↓
Page resources finished loading
```

We'll study these in detail later in the roadmap.

---

# 29. `scroll` Event

You can detect scrolling:

```javascript
window.addEventListener("scroll", function () {
    console.log("Page scrolling");
});
```

Used for:

- Sticky headers
- Scroll animations
- Back-to-top buttons
- Lazy loading
- Navigation effects

---

# 30. `resize` Event

Fires when the browser window changes size.

```javascript
window.addEventListener("resize", function () {
    console.log("Window resized");
});
```

For example:

```javascript
window.addEventListener("resize", function () {
    console.log(window.innerWidth);
});
```

This can tell you the current viewport width.

---

# 31. Events Can Change CSS

DOM events become very powerful when combined with the CSS techniques from the previous topic.

Example:

### HTML

```html
<button id="btn">Toggle</button>

<div id="box">
    Hello World
</div>
```

### CSS

```css
.active {
    background-color: blue;
    color: white;
}
```

### JavaScript

```javascript
const btn = document.getElementById("btn");
const box = document.getElementById("box");

btn.addEventListener("click", function () {
    box.classList.toggle("active");
});
```

Now:

```text
Click
 ↓
Event
 ↓
JavaScript
 ↓
classList.toggle()
 ↓
CSS changes
```

This is the basic foundation of interactive webpages.

---

# 32. Event Handler

A function that runs when an event occurs is commonly called an **event handler**.

Example:

```javascript
function handleClick() {
    console.log("Clicked");
}
```

Then:

```javascript
button.addEventListener("click", handleClick);
```

Here:

```text
handleClick
    ↓
Event handler
```

---

# 33. Don't Call the Function Immediately

This is an important mistake beginners make.

### Correct

```javascript
button.addEventListener("click", handleClick);
```

### Incorrect

```javascript
button.addEventListener("click", handleClick());
```

Why?

Because:

```javascript
handleClick()
```

means:

> Execute the function now.

But:

```javascript
handleClick
```

means:

> Give the function to the event listener so it can execute it later.

---

# 34. Anonymous Function as Event Handler

You can directly write:

```javascript
button.addEventListener("click", function () {
    console.log("Clicked");
});
```

This is called an **anonymous function** because it doesn't have a name.

---

# 35. Arrow Function

You can also use an arrow function:

```javascript
button.addEventListener("click", () => {
    console.log("Clicked");
});
```

Or:

```javascript
button.addEventListener("click", () => console.log("Clicked"));
```

All are valid.

---

# 36. Removing an Event Listener ⭐⭐⭐

You can remove an event listener using:

```javascript
removeEventListener()
```

But there is an important requirement.

You need the **same function reference**.

### Correct

```javascript
function handleClick() {
    console.log("Clicked");
}

button.addEventListener("click", handleClick);

button.removeEventListener("click", handleClick);
```

The listener is removed.

---

# 37. Why This Doesn't Work

This is a common interview question.

```javascript
button.addEventListener("click", function () {
    console.log("Clicked");
});

button.removeEventListener("click", function () {
    console.log("Clicked");
});
```

This does **not** remove the listener.

Why?

Because these are two different function objects.

Even though the code looks identical:

```javascript
function () {
    console.log("Clicked");
}
```

they are separate function references.

---

# 38. Event Listener Options

You can provide a third argument:

```javascript
element.addEventListener(
    "click",
    handleClick,
    options
);
```

One commonly discussed option is:

```javascript
{ once: true }
```

Example:

```javascript
button.addEventListener("click", function () {
    console.log("Clicked once");
}, { once: true });
```

The event listener automatically removes itself after the first event.

```text
First click
    ↓
Runs

Second click
    ↓
Doesn't run
```

---

# 39. Real Example — Show/Hide Password

This combines events and DOM manipulation.

### HTML

```html
<input id="password" type="password">

<button id="toggleBtn">
    Show Password
</button>
```

### JavaScript

```javascript
const password = document.getElementById("password");
const toggleBtn = document.getElementById("toggleBtn");

toggleBtn.addEventListener("click", function () {

    if (password.type === "password") {

        password.type = "text";
        toggleBtn.textContent = "Hide Password";

    } else {

        password.type = "password";
        toggleBtn.textContent = "Show Password";

    }

});
```

Flow:

```text
Click button
    ↓
click event
    ↓
Check input type
    ↓
Change type
    ↓
Change button text
```

This is exactly how many real UI interactions are built.

---

# 40. Real Example — Live Character Counter

### HTML

```html
<textarea id="message"></textarea>

<p>
    Characters:
    <span id="count">0</span>
</p>
```

### JavaScript

```javascript
const message = document.getElementById("message");
const count = document.getElementById("count");

message.addEventListener("input", function () {
    count.textContent = message.value.length;
});
```

If the user types:

```text
Hello
```

the page shows:

```text
Characters: 5
```

This demonstrates why the `input` event is useful.

---

# 41. Real Example — Form Validation

```html
<form id="form">

    <input id="username" type="text">

    <button type="submit">
        Submit
    </button>

</form>

<p id="error"></p>
```

JavaScript:

```javascript
const form = document.getElementById("form");
const username = document.getElementById("username");
const error = document.getElementById("error");

form.addEventListener("submit", function (event) {

    event.preventDefault();

    if (username.value === "") {

        error.textContent = "Username is required";

    } else {

        error.textContent = "Form submitted successfully";

    }

});
```

Flow:

```text
Submit form
    ↓
submit event
    ↓
preventDefault()
    ↓
Check input
    ↓
Show error/success
```

---

# 42. Event Types You Should Memorize

For interview preparation, know these groups.

### Mouse

```javascript
click
dblclick
mousedown
mouseup
mouseenter
mouseleave
mouseover
mouseout
mousemove
```

### Keyboard

```javascript
keydown
keyup
```

### Form

```javascript
submit
input
change
focus
blur
```

### Window/Document

```javascript
load
DOMContentLoaded
resize
scroll
```

---

# 43. Event Flow

A basic event interaction looks like:

```text
User action
     ↓
Browser detects action
     ↓
Event is created
     ↓
Event listener runs
     ↓
JavaScript executes
     ↓
DOM changes
     ↓
User sees updated UI
```

Example:

```text
User clicks button
        ↓
click event
        ↓
addEventListener()
        ↓
function runs
        ↓
classList.toggle()
        ↓
CSS changes
```

---

# 44. Important Event Terminology

### Event

Something that happens.

```text
click
```

### Event listener

Code that waits for an event.

```javascript
button.addEventListener("click", handler);
```

### Event handler

The function that executes.

```javascript
function handler() {
    console.log("Clicked");
}
```

### Event object

An object containing information about the event.

```javascript
button.addEventListener("click", function (event) {
    console.log(event);
});
```

We'll study the event object in the **next topic**.

---

# 45. Common Beginner Mistakes

### Mistake 1

```javascript
button.addEventListener("onclick", function () {});
```

❌ Wrong.

Use:

```javascript
button.addEventListener("click", function () {});
```

The event name is:

```text
click
```

not:

```text
onclick
```

---

### Mistake 2

```javascript
button.addEventListener("click", handleClick());
```

❌ Calls the function immediately.

Use:

```javascript
button.addEventListener("click", handleClick);
```

---

### Mistake 3

Trying to attach an event before the element exists.

For example, if your script executes before the HTML button has been parsed:

```javascript
const button = document.getElementById("btn");
```

could produce:

```text
null
```

Then:

```javascript
button.addEventListener(...)
```

causes an error.

This is one reason script placement and `DOMContentLoaded` matter.

---

# ⭐ Interview Questions

## Q1. What is a DOM event?

> A DOM event is an action or occurrence detected by the browser, such as a click, key press, input change, form submission, or page load, which JavaScript can respond to.

---

## Q2. How do you attach an event listener?

```javascript
element.addEventListener("click", function () {
    console.log("Clicked");
});
```

---

## Q3. What is the difference between `onclick` and `addEventListener()`?

`onclick` assigns a single event handler and assigning it again replaces the previous one.

`addEventListener()` allows multiple listeners and provides more flexible event handling.

---

## Q4. What is the difference between `input` and `change`?

`input` generally fires immediately as the user changes the value.

`change` fires when the change is committed; for text fields, commonly after the field loses focus.

---

## Q5. What is `preventDefault()`?

It prevents the browser's default action for an event.

Example:

```javascript
form.addEventListener("submit", function (event) {
    event.preventDefault();
});
```

---

## Q6. How do you remove an event listener?

```javascript
function handleClick() {
    console.log("Clicked");
}

button.addEventListener("click", handleClick);

button.removeEventListener("click", handleClick);
```

The same function reference must be used.

---

## Q7. What is the difference between `mouseenter` and `mouseover`?

`mouseenter` doesn't bubble from child elements, while `mouseover` can fire when moving between an element and its descendants.

---

# ⭐ Final Cheat Sheet

```text
DOM EVENTS
│
├── Mouse
│   ├── click
│   ├── dblclick
│   ├── mousedown
│   ├── mouseup
│   ├── mouseenter
│   ├── mouseleave
│   ├── mouseover
│   └── mouseout
│
├── Keyboard
│   ├── keydown
│   └── keyup
│
├── Forms
│   ├── input
│   ├── change
│   ├── focus
│   ├── blur
│   └── submit
│
└── Browser
    ├── load
    ├── DOMContentLoaded
    ├── resize
    └── scroll
```

The most important syntax to remember is:

```javascript
element.addEventListener("event", function () {
    // code to execute
});
```

And the most important events for interviews are:

```text
⭐⭐⭐ click
⭐⭐⭐ input
⭐⭐⭐ change
⭐⭐⭐ submit
⭐⭐⭐ keydown
⭐⭐⭐ keyup
⭐⭐⭐ focus
⭐⭐⭐ blur
⭐⭐⭐ mouseenter
⭐⭐⭐ mouseleave
⭐⭐⭐ DOMContentLoaded
⭐⭐⭐ load
```