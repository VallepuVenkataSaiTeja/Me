# 2. CSS Selectors ⭐

CSS selectors are used to **select HTML elements that you want to style**.

Think of a selector as telling CSS:

> **"Which HTML element(s) should I apply this style to?"**

Basic structure:

```css
selector {
    property: value;
}
```

For example:

```css
p {
    color: blue;
}
```

Here `p` is the **selector**.

It means:

> Select all `<p>` elements and make their text blue.

---

# 1. Element Selector

The **element selector** selects HTML elements by their tag name.

### HTML

```html
<h1>Hello</h1>
<p>Welcome</p>
<p>This is CSS.</p>
```

### CSS

```css
p {
    color: blue;
}
```

Both `<p>` elements become blue.

```text
<p>Welcome</p>       → selected
<p>This is CSS.</p>  → selected
<h1>Hello</h1>       → not selected
```

You can select any HTML element:

```css
h1 {
    color: red;
}

button {
    background-color: blue;
}

input {
    border: 1px solid gray;
}

div {
    padding: 20px;
}
```

### When to use?

Use an element selector when you want **all elements of that type** to have a particular style.

---

# 2. Class Selector ⭐⭐⭐

A class selector selects elements using the `class` attribute.

In CSS, a class starts with:

```css
.
```

### HTML

```html
<p class="text">Hello</p>
<p class="text">Welcome</p>
<p>Normal paragraph</p>
```

### CSS

```css
.text {
    color: blue;
}
```

The first two paragraphs become blue.

```text
.text → selected
.text → selected
p     → not selected
```

### Why are classes important?

Classes are probably the **most commonly used selectors** in real-world CSS.

For example:

```html
<button class="btn">Login</button>
<button class="btn">Register</button>
```

```css
.btn {
    background-color: blue;
    color: white;
    padding: 10px 20px;
}
```

Both buttons receive the same style.

---

## One class can be used on many elements

```html
<h1 class="title">Welcome</h1>

<p class="title">Hello</p>

<button class="title">Click</button>
```

```css
.title {
    color: red;
}
```

All three elements are selected.

That's why classes are useful for **reusable styles**.

---

# 3. ID Selector ⭐⭐⭐

An ID selector selects an element using its `id`.

In CSS, an ID starts with:

```css
#
```

### HTML

```html
<h1 id="main-title">Welcome</h1>
```

### CSS

```css
#main-title {
    color: red;
}
```

The `<h1>` becomes red.

---

## Class vs ID

This is important.

### Class

```html
<p class="text">Hello</p>
<p class="text">Welcome</p>
```

```css
.text {
    color: blue;
}
```

A class can be used on **many elements**.

### ID

```html
<h1 id="main-title">Welcome</h1>
```

```css
#main-title {
    color: red;
}
```

An ID is intended to identify **one unique element within a page**.

### Simple way to remember

```text
class → reusable
id    → unique
```

For styling, **classes are generally preferred**.

---

# 4. Universal Selector `*`

The universal selector selects **all elements**.

Syntax:

```css
* {
    property: value;
}
```

Example:

```css
* {
    margin: 0;
    padding: 0;
}
```

This applies to all elements.

```text
html       → selected
body       → selected
h1         → selected
p          → selected
div        → selected
button     → selected
input      → selected
...
```

A common use is:

```css
* {
    box-sizing: border-box;
}
```

You'll see this frequently in projects.

---

# 5. Group Selector

Suppose you want the same style for multiple different elements.

Without grouping:

```css
h1 {
    color: blue;
}

h2 {
    color: blue;
}

p {
    color: blue;
}
```

This works, but it's repetitive.

With a **group selector**:

```css
h1, h2, p {
    color: blue;
}
```

The comma means:

> Select `h1`, `h2`, and `p`.

### HTML

```html
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<p>Paragraph</p>
```

All three become blue.

---

## Another example

```css
.btn, .link, .nav-item {
    font-size: 16px;
}
```

This selects all elements having:

```text
.btn
.link
.nav-item
```

---

# 6. Descendant Selector ⭐⭐⭐

This is very important.

A descendant selector selects an element **inside another element**, at any level.

Syntax:

```css
parent child {
    property: value;
}
```

Notice there is a **space** between them.

---

## Example

### HTML

```html
<div class="container">

    <p>Hello</p>

</div>
```

CSS:

```css
.container p {
    color: blue;
}
```

This means:

> Select every `<p>` that is inside `.container`.

---

## Multiple levels

Consider:

```html
<div class="container">

    <section>

        <p>Hello</p>

    </section>

</div>
```

CSS:

```css
.container p {
    color: red;
}
```

The paragraph is still selected.

Why?

Because `<p>` is a **descendant** of `.container`.

```text
.container
    │
    └── section
          │
          └── p  ← selected
```

It doesn't matter that `<section>` is between them.

---

# 7. Child Selector `>` ⭐⭐⭐

The child selector selects an element that is a **direct child** of another element.

Syntax:

```css
parent > child {
    property: value;
}
```

The important difference is:

```text
space → descendant
>     → direct child
```

---

## Example

### HTML

```html
<div class="container">

    <p>Hello</p>

    <section>
        <p>Welcome</p>
    </section>

</div>
```

CSS:

```css
.container > p {
    color: blue;
}
```

Which `<p>` is selected?

Only:

```html
<p>Hello</p>
```

Because it is directly inside `.container`.

The second `<p>` is inside `<section>`.

```text
.container
│
├── p              ← selected
│
└── section
      │
      └── p        ← NOT selected
```

---

## Descendant vs Child

This is one of the most important things to understand.

### Descendant

```css
.container p {
    color: red;
}
```

Selects:

```text
.container
    └── p
```

and:

```text
.container
    └── div
         └── p
```

and:

```text
.container
    └── section
         └── div
              └── p
```

Basically, **any level inside**.

---

### Child

```css
.container > p {
    color: red;
}
```

Only selects:

```text
.container
    └── p
```

It does **not** select:

```text
.container
    └── div
         └── p
```

### Remember:

```text
A B      → B anywhere inside A
A > B    → B directly inside A
```

---

# 8. Attribute Selector ⭐⭐

Attribute selectors select elements based on their HTML attributes.

Basic syntax:

```css
[attribute] {
    property: value;
}
```

---

## Example

### HTML

```html
<input type="text">
<input type="email">
<input type="password">
```

CSS:

```css
[type] {
    border: 1px solid blue;
}
```

This selects all elements that have a `type` attribute.

---

## Select a specific attribute value

You can write:

```css
input[type="text"] {
    background-color: lightgray;
}
```

This selects only:

```html
<input type="text">
```

It doesn't select:

```html
<input type="email">
<input type="password">
```

---

## Another example

HTML:

```html
<a href="https://example.com">Example</a>
<a href="about.html">About</a>
```

CSS:

```css
a[href="about.html"] {
    color: red;
}
```

Only the About link is selected.

---

# Attribute Selector Variations

You don't need to memorize all of these immediately, but you should know the common ones.

### `[attribute]`

Element has the attribute.

```css
input[required] {
    border: 1px solid red;
}
```

---

### `[attribute="value"]`

Exact value.

```css
input[type="email"] {
    background: lightblue;
}
```

---

### `[attribute^="value"]`

Attribute value **starts with** something.

```css
a[href^="https"] {
    color: green;
}
```

Means:

> Select links whose `href` starts with `https`.

---

### `[attribute$="value"]`

Attribute value **ends with** something.

```css
img[src$=".png"] {
    border: 1px solid black;
}
```

---

### `[attribute*="value"]`

Attribute value **contains** something.

```css
a[href*="google"] {
    color: blue;
}
```

---

# ⭐ All Selectors Together

Let's take one HTML example:

```html
<div class="container">

    <h1 id="title">Welcome</h1>

    <p class="text">Hello</p>

    <p class="text">Welcome to CSS</p>

    <div>
        <p>Nested paragraph</p>
    </div>

    <input type="email">

</div>
```

Now different selectors:

### Element

```css
p {
    color: red;
}
```

Selects **all paragraphs**.

---

### Class

```css
.text {
    color: blue;
}
```

Selects paragraphs with class `text`.

---

### ID

```css
#title {
    color: green;
}
```

Selects the element with ID `title`.

---

### Universal

```css
* {
    box-sizing: border-box;
}
```

Selects everything.

---

### Group

```css
h1, p {
    font-family: Arial;
}
```

Selects all `h1` and `p` elements.

---

### Descendant

```css
.container p {
    color: purple;
}
```

Selects all paragraphs inside `.container`, including nested ones.

---

### Child

```css
.container > p {
    color: orange;
}
```

Selects only the paragraphs directly inside `.container`.

---

### Attribute

```css
input[type="email"] {
    border: 2px solid blue;
}
```

Selects email inputs.

---

# 🔥 Selector Cheat Sheet

| Selector        | Meaning         | Example            |
| --------------- | --------------- | ------------------ |
| `p`             | Element         | `p {}`             |
| `.box`          | Class           | `.box {}`          |
| `#header`       | ID              | `#header {}`       |
| `*`             | Everything      | `* {}`             |
| `h1, p`         | Group           | `h1, p {}`         |
| `.box p`        | Descendant      | `.box p {}`        |
| `.box > p`      | Direct child    | `.box > p {}`      |
| `[type]`        | Has attribute   | `[type] {}`        |
| `[type="text"]` | Exact attribute | `[type="text"] {}` |

---

# 🧠 The Most Important Difference

Make sure you can understand this:

```css
.container p
```

vs

```css
.container > p
```

### `.container p`

**Any paragraph inside `.container`:**

```text
.container
├── p              ✓
└── div
    └── p          ✓
```

### `.container > p`

**Only direct paragraph children:**

```text
.container
├── p              ✓
└── div
    └── p          ✗
```

This distinction becomes very useful when working with **React component layouts, navigation bars, cards, and nested elements**.

---

# 🎯 What You Need to Master

For now, don't try to memorize every possible selector.

Master these:

```text
1. Element       p
2. Class         .class
3. ID            #id
4. Universal     *
5. Group         h1, p
6. Descendant    .parent p
7. Child         .parent > p
8. Attribute     input[type="text"]
```

And especially remember:

```text
.       → class
#       → id
,       → group
(space) → descendant
>       → direct child
[]      → attribute
*       → all
```