# 1. CSS Basics

## 1. What is CSS?

**CSS = Cascading Style Sheets**

CSS is used to **style and design HTML elements**.

HTML is responsible for the **structure/content**, while CSS controls the **appearance**.

For example, HTML:

```html id="zq4f1p"
<h1>Hello World</h1>
<p>Welcome to my website.</p>
```

Without CSS, the browser gives you its default styling.

With CSS:

```css id="f9k1q4"
h1 {
    color: blue;
    font-size: 40px;
}

p {
    color: gray;
}
```

Now the heading becomes blue and larger, and the paragraph becomes gray.

### Think of it like this

```text id="8o7v2p"
HTML → Structure
CSS  → Design
JavaScript → Behavior
```

For example, for a button:

```text id="g7n2as"
HTML       → Creates the button
CSS        → Makes it beautiful
JavaScript → Makes it do something
```

---

# 2. CSS Syntax

CSS follows a specific syntax.

```css id="9h1zqv"
selector {
    property: value;
}
```

For example:

```css id="4q3y6k"
h1 {
    color: red;
    font-size: 40px;
}
```

There are three important parts:

### Selector

```css id="v7m0tc"
h1
```

The selector tells CSS **which HTML element you want to style**.

### Property

```css id="6m3p2k"
color
```

The property tells CSS **what you want to change**.

### Value

```css id="7w8h4r"
red
```

The value tells CSS **how you want that property to look**.

So:

```css id="c5d8x2"
h1 {
    color: red;
}
```

means:

> Select all `<h1>` elements and make their text red.

---

## Multiple properties

You can add multiple properties inside one rule:

```css id="4j9s2n"
h1 {
    color: blue;
    font-size: 40px;
    text-align: center;
}
```

Here:

```text id="5m7v3c"
color       → property
blue        → value

font-size   → property
40px        → value

text-align  → property
center      → value
```

Each declaration ends with a semicolon:

```css id="y3n8q1"
color: blue;
font-size: 40px;
```

---

# 3. Inline CSS

**Inline CSS** means writing CSS directly inside the HTML element using the `style` attribute.

Example:

```html id="9f2m4k"
<h1 style="color: red;">Hello World</h1>
```

You can have multiple properties:

```html id="t8k3p1"
<h1 style="color: red; font-size: 40px; text-align: center;">
    Hello World
</h1>
```

### Advantages

* Very quick for testing
* Easy for a small one-time style

### Disadvantages

* Difficult to maintain
* Creates repeated code
* Mixes HTML and CSS
* Not suitable for large websites

For example, imagine 50 buttons:

```html id="1j8v6a"
<button style="background: blue; color: white;">Button 1</button>
<button style="background: blue; color: white;">Button 2</button>
<button style="background: blue; color: white;">Button 3</button>
```

That's bad practice.

---

# 4. Internal CSS

**Internal CSS** means putting CSS inside a `<style>` tag in the HTML document.

Example:

```html id="q5s7w2"
<!DOCTYPE html>
<html>
<head>

    <style>
        h1 {
            color: blue;
            font-size: 40px;
        }

        p {
            color: gray;
        }
    </style>

</head>

<body>

    <h1>Hello World</h1>
    <p>Welcome to my website.</p>

</body>
</html>
```

The CSS is written inside:

```html id="z2m8x4"
<style>
    ...
</style>
```

### When is internal CSS useful?

It can be useful when:

* Creating a small webpage
* Testing something
* You have styles specific to one HTML page

But for larger websites, external CSS is generally better.

---

# 5. External CSS ⭐

**External CSS** means creating a separate `.css` file.

For example:

```text id="c8x2m1"
project/
│
├── index.html
└── style.css
```

### `style.css`

```css id="w6p3r8"
h1 {
    color: blue;
    font-size: 40px;
}

p {
    color: gray;
}
```

Then connect it to your HTML.

### `index.html`

```html id="v4k9s2"
<!DOCTYPE html>
<html>

<head>
    <link rel="stylesheet" href="style.css">
</head>

<body>

    <h1>Hello World</h1>
    <p>Welcome to my website.</p>

</body>

</html>
```

This is the **most common approach for normal websites**.

---

# 6. How to Connect CSS with HTML ⭐

For external CSS, use:

```html id="g2w5m9"
<link rel="stylesheet" href="style.css">
```

Usually this goes inside `<head>`:

```html id="n7c4p2"
<head>
    <link rel="stylesheet" href="style.css">
</head>
```

### What does it mean?

```html id="r8m1v6"
<link
    rel="stylesheet"
    href="style.css"
>
```

`link` → tells the browser to load another resource.

`rel="stylesheet"` → tells the browser that the resource is a CSS stylesheet.

`href="style.css"` → tells the browser where the CSS file is.

---

## Folder example

Suppose your project looks like:

```text id="v2q8m6"
my-website/
│
├── index.html
│
└── css/
    └── style.css
```

Then:

```html id="k6r1p9"
<link rel="stylesheet" href="css/style.css">
```

Because `style.css` is inside the `css` folder.

---

## Another example

```text id="a8m3q5"
my-website/
│
├── pages/
│   └── about.html
│
└── css/
    └── style.css
```

From `about.html`, you would need:

```html id="p7w2n4"
<link rel="stylesheet" href="../css/style.css">
```

`../` means:

> Go one folder up.

Understanding file paths is important when working with CSS.

---

# 7. CSS Comments

CSS comments are notes written in your CSS code.

Syntax:

```css id="q9v4m2"
/* This is a CSS comment */
```

Example:

```css id="x3k8p1"
/* Heading styles */

h1 {
    color: blue;
    font-size: 40px;
}
```

The browser **does not apply anything inside the comment**.

You can also write a comment across multiple lines:

```css id="m5r2t7"
/*
   This section contains
   the website heading styles.
*/

h1 {
    color: blue;
}
```

---

## Why use comments?

Comments help you organize your CSS.

For example:

```css id="c4v8n2"
/* Navbar */

.navbar {
    background-color: black;
}

/* Hero Section */

.hero {
    height: 500px;
}

/* Footer */

.footer {
    background-color: gray;
}
```

This becomes especially useful when your CSS file becomes large.

---

# 8. Properties and Values ⭐

This is one of the most important basic concepts.

A CSS declaration looks like:

```css id="p8m3w6"
property: value;
```

Examples:

```css id="h2q7v9"
color: red;
font-size: 20px;
width: 500px;
height: 300px;
text-align: center;
background-color: black;
```

Here:

| Property           | Value    |
| ------------------ | -------- |
| `color`            | `red`    |
| `font-size`        | `20px`   |
| `width`            | `500px`  |
| `height`           | `300px`  |
| `text-align`       | `center` |
| `background-color` | `black`  |

### Important

A property and its value work together:

```css id="j4n8q2"
color: red;
```

`color` tells CSS **what to change**.

`red` tells CSS **what value to use**.

---

# 9. Putting Everything Together

Let's create a small example.

### HTML

```html id="e5w9k2"
<!DOCTYPE html>
<html>

<head>
    <link rel="stylesheet" href="style.css">
</head>

<body>

    <h1>Welcome to My Website</h1>

    <p>This is my first CSS page.</p>

    <button>Click Me</button>

</body>

</html>
```

### CSS

```css id="u7m3p8"
/* Main heading */

h1 {
    color: blue;
    font-size: 40px;
    text-align: center;
}

/* Paragraph */

p {
    color: gray;
    font-size: 18px;
}

/* Button */

button {
    background-color: blue;
    color: white;
    padding: 10px 20px;
}
```

Here you can see the complete relationship:

```text id="k3p7w1"
HTML
 │
 ├── h1
 ├── p
 └── button
       ↓
      CSS
       ↓
 Selector → Property → Value
```

For example:

```css id="d6v2n9"
button {
    background-color: blue;
}
```

```text id="h8q4m1"
button            → Selector
background-color  → Property
blue              → Value
```

---

# 10. Inline vs Internal vs External

Remember this simple table:

| Type     | Where?               | Recommended? |
| -------- | -------------------- | ------------ |
| Inline   | Inside HTML element  | ❌ Usually no |
| Internal | `<style>` tag        | ⚠️ Sometimes |
| External | Separate `.css` file | ✅ Yes        |

For your frontend development, **focus primarily on external CSS**.

---

# 11. One Important Concept: CSS Rule

You will frequently hear the term **CSS rule**.

This:

```css id="s5k8q2"
h1 {
    color: blue;
    font-size: 40px;
}
```

is a **CSS rule**.

It consists of:

```text id="n4w7m3"
Selector
   ↓
  h1
   ↓
Declaration Block
   ↓
{
   color: blue;
   font-size: 40px;
}
```

And each:

```css id="j8p3v6"
color: blue;
```

is called a **declaration**.

So remember:

```text id="r2m6k9"
CSS Rule
│
├── Selector
│
└── Declaration Block
      │
      ├── Declaration
      ├── Declaration
      └── Declaration
```

---

# 🎯 What you should remember from CSS Basics

Don't memorize everything. Make sure you understand these:

### 1. CSS purpose

> CSS is used to style and layout HTML elements.

### 2. Basic syntax

```css id="v9q2m5"
selector {
    property: value;
}
```

### 3. Three ways to write CSS

```text id="x4k8p1"
Inline
Internal
External ⭐
```

### 4. External CSS connection

```html id="m7w3q9"
<link rel="stylesheet" href="style.css">
```

### 5. Property + value

```css id="c2n6v8"
color: red;
```

### 6. CSS comments

```css id="p4r9k1"
/* Comment */
```

### 7. CSS rule

```css id="t8m3q6"
p {
    color: blue;
    font-size: 18px;
}
```
