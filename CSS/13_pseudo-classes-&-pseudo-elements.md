# 13. Pseudo-classes & Pseudo-elements ⭐⭐

This is an important CSS topic for interviews and real-world frontend development.

You should understand:

### Pseudo-classes

* `:hover`
* `:focus`
* `:active`
* `:visited`
* `:first-child`
* `:last-child`
* `:nth-child()`
* `:not()`

### Pseudo-elements

* `::before`
* `::after`
* `::first-letter`
* `::first-line`
* `::selection`

And most importantly:

> **Pseudo-class = selects an element based on its state or position.**
> **Pseudo-element = styles or creates a specific part of an element.**

---

# 1. What is a Pseudo-class?

A **pseudo-class** is a keyword added to a selector to style an element when it is in a particular **state** or matches a particular **condition**.

Syntax:

```css
selector:pseudo-class {
    property: value;
}
```

Example:

```css
button:hover {
    background-color: blue;
}
```

This means:

> When the user moves the mouse over the button, make its background blue.

Notice the single colon:

```css
:hover
:focus
:active
:nth-child()
```

---

# 2. What is a Pseudo-element?

A **pseudo-element** lets you style a specific part of an element or create generated content around an element.

Syntax:

```css
selector::pseudo-element {
    property: value;
}
```

Example:

```css
p::first-letter {
    font-size: 40px;
}
```

This styles only the **first letter** of the paragraph.

Notice the double colon:

```css
::before
::after
::first-letter
::first-line
::selection
```

---

# 3. Pseudo-class vs Pseudo-element

This is a very common interview question.

| Pseudo-class                        | Pseudo-element                     |
| ----------------------------------- | ---------------------------------- |
| Uses `:`                            | Uses `::`                          |
| Represents state/condition          | Represents part of an element      |
| Usually selects an existing element | Styles a part or generated content |
| `:hover`                            | `::before`                         |
| `:focus`                            | `::after`                          |
| `:nth-child()`                      | `::first-letter`                   |
| `:active`                           | `::selection`                      |

### Easy memory

```text
Pseudo-class
→ STATE / CONDITION

Pseudo-element
→ PART / EXTRA CONTENT
```

For example:

```css
button:hover
```

**Hover state** → pseudo-class.

```css
p::first-letter
```

**First letter** → pseudo-element.

---

# 4. `:hover`

`:hover` applies styles when the mouse pointer is over an element.

Syntax:

```css
button:hover {
    background-color: blue;
    color: white;
}
```

HTML:

```html
<button>Login</button>
```

When you move your mouse over the button, the styles apply.

### Real-world usage

Very commonly used for:

* buttons
* navigation links
* cards
* images
* icons

Example:

```css
a {
    color: black;
}

a:hover {
    color: red;
}
```

---

# 5. `:focus`

`:focus` applies when an element receives focus.

Most commonly seen with:

* input
* textarea
* select
* buttons
* links

Example:

```css
input:focus {
    border: 2px solid blue;
}
```

HTML:

```html
<input type="text" placeholder="Enter your name">
```

When you click inside the input, it becomes focused.

### Why is `:focus` important?

It is especially important for **keyboard accessibility**.

For example, when a user presses:

```text
Tab
```

the browser moves focus between interactive elements.

You can provide a visible focus style:

```css
button:focus {
    outline: 2px solid blue;
}
```

---

# 6. `:active`

`:active` applies while an element is being activated.

For a button, this is typically the moment while the user is pressing/clicking it.

```css
button:active {
    transform: scale(0.95);
}
```

The button temporarily becomes slightly smaller while being pressed.

### Common usage

```css
button:hover {
    background-color: blue;
}

button:active {
    transform: scale(0.95);
}
```

So:

```text
:hover  → pointer is over it
:active → being activated/pressed
```

---

# 7. `:visited`

`:visited` styles links that the browser considers already visited.

```css
a:visited {
    color: purple;
}
```

Example:

```html
<a href="https://example.com">Visit Website</a>
```

After visiting the link, the browser may display it using the `:visited` style.

### Important

Browsers restrict some `:visited` styling for privacy reasons, so you cannot freely use every CSS property with visited links.

For interviews, remember:

> `:visited` targets links that have already been visited.

---

# 8. `:first-child`

`:first-child` selects an element if it is the **first child of its parent**.

Example:

```html
<div class="container">
    <p>First</p>
    <p>Second</p>
    <p>Third</p>
</div>
```

CSS:

```css
p:first-child {
    color: red;
}
```

Only:

```text
First
```

becomes red.

### Important point

It means:

> Is this element the first child of its parent?

It does **not** simply mean "find the first `<p>`."

---

# 9. `:last-child`

Selects an element if it is the last child of its parent.

```css
p:last-child {
    color: blue;
}
```

Example:

```html
<div>
    <p>One</p>
    <p>Two</p>
    <p>Three</p>
</div>
```

Only `Three` gets the style.

---

# 10. `:nth-child()`

This is very useful.

`:nth-child()` allows you to select children based on their position.

Example:

```css
li:nth-child(2) {
    color: red;
}
```

This selects the second child.

HTML:

```html
<ul>
    <li>One</li>
    <li>Two</li>
    <li>Three</li>
</ul>
```

Result:

```text
One
Two    ← red
Three
```

---

# 11. `:nth-child(odd)`

Selects odd-positioned children:

```css
li:nth-child(odd) {
    background-color: lightgray;
}
```

Positions:

```text
1 → selected
2 → not selected
3 → selected
4 → not selected
5 → selected
```

Very useful for tables and lists.

---

# 12. `:nth-child(even)`

Selects even-positioned children.

```css
li:nth-child(even) {
    background-color: lightgray;
}
```

Positions:

```text
1 → not selected
2 → selected
3 → not selected
4 → selected
```

---

# 13. `:nth-child(3n)`

You can also use formulas.

```css
li:nth-child(3n) {
    color: red;
}
```

This selects:

```text
3
6
9
12
...
```

Similarly:

```css
li:nth-child(2n) {
    color: blue;
}
```

selects:

```text
2
4
6
8
...
```

---

# 14. `:not()`

`:not()` selects elements that **do not match** a selector.

Example:

```css
p:not(.special) {
    color: gray;
}
```

HTML:

```html
<p>Hello</p>
<p class="special">Special</p>
<p>World</p>
```

The first and third paragraphs become gray.

The `.special` paragraph is excluded.

### Easy memory

```text
:not(.special)
→ everything except .special
```

---

# 15. Practical Pseudo-class Example

Imagine a navigation bar:

```html
<nav>
    <a href="#">Home</a>
    <a href="#">About</a>
    <a href="#">Courses</a>
    <a href="#">Contact</a>
</nav>
```

CSS:

```css
nav a {
    color: black;
    text-decoration: none;
}

nav a:hover {
    color: red;
}

nav a:active {
    color: blue;
}
```

Now:

```text
Normal       → black
Mouse hover  → red
Being clicked → blue
```

This is a very common real-world use.

---

# 16. `::before`

Now let's move to pseudo-elements.

`::before` creates generated content **before the element's content**.

Example:

```css
h2::before {
    content: "★ ";
}
```

HTML:

```html
<h2>Courses</h2>
```

Visual result:

```text
★ Courses
```

### Important

When using `::before`, you normally need:

```css
content: "";
```

or some actual content.

For example:

```css
h2::before {
    content: "★";
}
```

---

# 17. `::after`

`::after` creates generated content after the element's content.

Example:

```css
h2::after {
    content: " →";
}
```

HTML:

```html
<h2>Courses</h2>
```

Result:

```text
Courses →
```

---

# 18. Why `content` is important

This is one of the most important things to remember.

With `::before` and `::after`, you generally use:

```css
content: "";
```

Example:

```css
.box::before {
    content: "";
}
```

Or actual text:

```css
.box::before {
    content: "Hello";
}
```

Without a generated `content` value, `::before` and `::after` generally won't display as generated content.

---

# 19. `::before` Real-world Example

Suppose you want a small red line before every heading.

HTML:

```html
<h2>Our Courses</h2>
```

CSS:

```css
h2::before {
    content: "";
    display: inline-block;
    width: 5px;
    height: 25px;
    background-color: red;
    margin-right: 10px;
}
```

You get something visually like:

```text
▌ Our Courses
```

This is commonly used in website designs.

---

# 20. `::after` Real-world Example

You can create decorative lines.

```css
.title::after {
    content: "";
    display: block;
    width: 60px;
    height: 3px;
    background-color: red;
    margin-top: 8px;
}
```

HTML:

```html
<h2 class="title">About Us</h2>
```

Visual idea:

```text
About Us
────────
```

The line is generated using CSS.

---

# 21. `::first-letter`

Styles only the first letter of an element.

```css
p::first-letter {
    font-size: 40px;
    font-weight: bold;
}
```

HTML:

```html
<p>Welcome to our website.</p>
```

The `W` becomes larger and bold.

This is commonly used for:

* articles
* blogs
* magazines
* decorative paragraphs

---

# 22. `::first-line`

Styles the first line of text.

```css
p::first-line {
    font-weight: bold;
}
```

Example:

```html
<p>
    Welcome to our website. We provide many different courses
    for students and professionals.
</p>
```

The first rendered line gets the style.

### Important

The first line depends on the available width.

If the screen becomes smaller, the first line can change.

---

# 23. `::selection`

`::selection` styles text when the user selects/highlights it.

Example:

```css
::selection {
    background-color: black;
    color: white;
}
```

Now when the user selects text:

```text
Selected text
```

it can appear with your custom selection styling.

Very simple and useful for website customization.

---

# 24. Pseudo-elements can be used for icons/decorations

For example:

```css
.required::after {
    content: " *";
    color: red;
}
```

HTML:

```html
<label class="required">Email</label>
```

Result:

```text
Email *
```

This is useful for indicating required form fields.

---

# 25. `::before` + `::after` with positioning

This is very common in modern CSS.

Example:

```css
.card {
    position: relative;
}

.card::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 5px;
    height: 100%;
    background-color: red;
}
```

Why:

```css
.card {
    position: relative;
}
```

Because the pseudo-element is:

```css
position: absolute;
```

So the card becomes its containing block.

This connects directly with the **Position** topic you already learned.

---

# 26. Important `::before` / `::after` rule

Remember this pattern:

```css
.parent {
    position: relative;
}

.parent::before {
    content: "";
    position: absolute;
}
```

This is extremely common for:

* overlays
* decorative lines
* badges
* background shapes
* icons
* hover effects
* image overlays

---

# 27. Example: Image Overlay

HTML:

```html
<div class="image-box">
    <img src="image.jpg" alt="Course">
</div>
```

CSS:

```css
.image-box {
    position: relative;
}

.image-box::after {
    content: "";
    position: absolute;
    inset: 0;
    background: rgba(0, 0, 0, 0.4);
}
```

Here:

```css
inset: 0;
```

means:

```text
top: 0
right: 0
bottom: 0
left: 0
```

So the pseudo-element covers the entire image box.

---

# 28. Hover Effect Using `::after`

You can create an animated underline.

HTML:

```html
<a href="#" class="nav-link">Home</a>
```

CSS:

```css
.nav-link {
    position: relative;
    text-decoration: none;
}

.nav-link::after {
    content: "";
    position: absolute;
    left: 0;
    bottom: -5px;
    width: 0;
    height: 2px;
    background-color: red;
    transition: width 0.3s;
}

.nav-link:hover::after {
    width: 100%;
}
```

The idea:

```text
Normal:

Home


Hover:

Home
────
```

This is a very common frontend technique.

---

# 29. Important Selector Combination

You can combine a pseudo-class and pseudo-element:

```css
button:hover::after {
    content: " →";
}
```

Meaning:

> When the button is hovered, create content after it.

Another example:

```css
.card:hover::before {
    transform: scaleX(1);
}
```

So you can use:

```text
pseudo-class + pseudo-element
```

together.

---

# 30. Common Pseudo-classes You Should Know

For interview preparation, remember these:

```css
:hover
:focus
:active
:visited
:first-child
:last-child
:nth-child()
:not()
```

There are many more CSS pseudo-classes, but you don't need to memorize every one for a typical beginner/intermediate frontend interview.

---

# 31. Common Pseudo-elements You Should Know

Focus on:

```css
::before
::after
::first-letter
::first-line
::selection
```

These are enough for most beginner/intermediate interviews.

---

# 32. `:hover` vs `:focus`

Very commonly asked.

### `:hover`

Triggered when the pointer is over the element.

```css
button:hover {
    background: blue;
}
```

### `:focus`

Triggered when the element has keyboard/input focus.

```css
input:focus {
    border-color: blue;
}
```

Memory:

```text
:hover → mouse/pointer interaction
:focus → keyboard/input focus
```

Don't assume `:hover` and `:focus` are interchangeable.

---

# 33. `:first-child` vs `:nth-child(1)`

These effectively target the first child position.

```css
li:first-child {
    color: red;
}
```

and:

```css
li:nth-child(1) {
    color: red;
}
```

Both can target the first child.

But `:nth-child()` is more flexible because you can use:

```css
:nth-child(2)
:nth-child(odd)
:nth-child(even)
:nth-child(3n)
```

---

# 34. Important `:nth-child()` Detail

Consider:

```html
<div>
    <h2>Title</h2>
    <p>First paragraph</p>
    <p>Second paragraph</p>
</div>
```

If you write:

```css
p:nth-child(1) {
    color: red;
}
```

the paragraph will **not** be selected.

Why?

Because the first child is:

```html
<h2>
```

The `<p>` is the second child.

So:

```css
p:nth-child(2) {
    color: red;
}
```

would select the first paragraph.

This is a very common interview/troubleshooting point.

---

# 35. `:nth-child()` vs `:nth-of-type()`

You should know the basic difference, but don't spend too much time on it.

`:nth-child()` counts **all children**.

`:nth-of-type()` counts only elements of the **same type**.

Example:

```html
<div>
    <h2>Title</h2>
    <p>First</p>
    <p>Second</p>
</div>
```

With:

```css
p:nth-child(2)
```

the first paragraph is selected because it is child number 2.

With:

```css
p:nth-of-type(1)
```

the first `<p>` is selected because it is the first `<p>`.

### Memory

```text
:nth-child()
→ count all children

:nth-of-type()
→ count same element type
```

For your core CSS preparation, understand the difference; you don't need to memorize every `*-of-type` variant.

---

# 36. Pseudo-class vs Pseudo-element — Interview Answer

If the interviewer asks:

### "What is the difference between pseudo-class and pseudo-element?"

A good answer is:

> A pseudo-class is used to style an element based on its state or condition, such as `:hover`, `:focus`, or `:nth-child()`. A pseudo-element is used to style a specific part of an element or generate content, such as `::before`, `::after`, or `::first-letter`.

That's a strong interview answer.

---

# 37. Quick Practical Example

HTML:

```html
<div class="card">
    <h2>React Course</h2>
    <p>Learn React from basics to advanced.</p>
    <button>Enroll Now</button>
</div>
```

CSS:

```css
.card {
    position: relative;
    padding: 20px;
    border: 1px solid #ddd;
}

.card::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 5px;
    height: 100%;
    background-color: red;
}

button:hover {
    background-color: blue;
    color: white;
}

button:active {
    transform: scale(0.95);
}

button:focus {
    outline: 2px solid black;
}
```

Here we're using several concepts together:

```text
.card::before
→ pseudo-element

button:hover
→ pseudo-class

button:active
→ pseudo-class

button:focus
→ pseudo-class

position: relative + absolute
→ positioning
```

This is exactly how CSS concepts come together in real projects.

---

# 38. Interview Questions

### 1. What is a pseudo-class?

A pseudo-class styles an element based on its state or condition.

Example:

```css
button:hover {
    background: blue;
}
```

---

### 2. What is a pseudo-element?

A pseudo-element styles a specific part of an element or creates generated content.

Example:

```css
p::first-letter {
    font-size: 30px;
}
```

---

### 3. Difference between `:hover` and `::before`?

```text
:hover
→ pseudo-class
→ state

::before
→ pseudo-element
→ generated content/part
```

---

### 4. What does `:nth-child()` do?

It selects an element based on its position among its parent's children.

```css
li:nth-child(2) {
    color: red;
}
```

---

### 5. What does `:not()` do?

It selects elements that do not match a specified selector.

```css
p:not(.special) {
    color: gray;
}
```

---

### 6. Why do we use `content` with `::before` and `::after`?

`content` defines the generated content for those pseudo-elements.

Example:

```css
.box::before {
    content: "";
}
```

or:

```css
.box::before {
    content: "★";
}
```

---

### 7. Can we use `:hover` and `::after` together?

Yes.

```css
button:hover::after {
    content: " →";
}
```

---

### 8. What is the difference between `:first-child` and `:nth-child()`?

`:first-child` specifically targets the first child.

```css
p:first-child {}
```

`:nth-child()` can target different positions or patterns.

```css
p:nth-child(2) {}
p:nth-child(odd) {}
p:nth-child(3n) {}
```

---

# 39. CSS Pseudo Cheat Sheet ⭐

### Pseudo-classes

```css
:hover
```

Mouse/pointer over element.

```css
:focus
```

Element has focus.

```css
:active
```

Element is being activated/pressed.

```css
:visited
```

Visited link.

```css
:first-child
```

First child.

```css
:last-child
```

Last child.

```css
:nth-child(2)
```

Second child.

```css
:nth-child(odd)
```

Odd children.

```css
:nth-child(even)
```

Even children.

```css
:not(.class)
```

Everything except matching selector.

---

### Pseudo-elements

```css
::before
```

Generated content before.

```css
::after
```

Generated content after.

```css
::first-letter
```

First letter.

```css
::first-line
```

First line.

```css
::selection
```

Selected text.

---

# 40. Final Memory Trick

Remember this:

```text
             CSS PSEUDO
                 │
        ┌────────┴────────┐
        ↓                 ↓
   PSEUDO-CLASS      PSEUDO-ELEMENT
        │                 │
     STATE              PART
        │                 │
   :hover              ::before
   :focus              ::after
   :active             ::first-letter
   :visited            ::first-line
   :first-child        ::selection
   :nth-child()
   :not()
```

### The most important things for interviews:

```text
:hover
:focus
:active
:nth-child()
:not()

::before
::after
::first-letter
::selection
```

And remember:

> **Single `:` → pseudo-class → state/condition**
> **Double `::` → pseudo-element → part/generated content**
