# 6. CSS Typography & Text ⭐⭐⭐

**Typography** means controlling how text looks and how readable it is on a webpage.

In real projects, you'll use typography everywhere:

* Navbar text
* Headings
* Paragraphs
* Buttons
* Forms
* Cards
* Website content

The main properties you need to know are:

```text
font-family
font-size
font-weight
font-style
line-height
letter-spacing
text-align
text-decoration
text-transform
text-shadow
```

Let's understand each one.

---

# 1. `font-family`

`font-family` controls **which font is used** for your text.

```css
body {
    font-family: Arial;
}
```

Now all text inside the body will use Arial unless another rule overrides it.

Example:

```css
h1 {
    font-family: Georgia;
}

p {
    font-family: Arial;
}
```

So:

```text
Heading → Georgia
Paragraph → Arial
```

---

## Multiple fonts / fallback fonts

Usually you shouldn't depend on only one font.

```css
body {
    font-family: Arial, sans-serif;
}
```

This means:

```text
Try Arial
   ↓
If unavailable → use sans-serif
```

Another example:

```css
body {
    font-family: "Times New Roman", Times, serif;
}
```

The browser tries them from left to right.

---

## Generic font families

The most important ones are:

```text
serif
sans-serif
monospace
cursive
fantasy
```

### `serif`

Fonts with small decorative strokes.

```css
h1 {
    font-family: Georgia, serif;
}
```

### `sans-serif`

Clean fonts without decorative strokes.

```css
body {
    font-family: Arial, sans-serif;
}
```

Very common for websites.

### `monospace`

Every character has approximately the same width.

Common for:

* Code
* Terminal text
* Programming examples

```css
code {
    font-family: monospace;
}
```

---

# 2. `font-size`

`font-size` controls **how large the text is**.

```css
h1 {
    font-size: 40px;
}

p {
    font-size: 18px;
}
```

You can use different units:

```css
h1 {
    font-size: 2rem;
}
```

or:

```css
h1 {
    font-size: 40px;
}
```

For modern responsive websites, `rem` is commonly useful.

Example:

```css
html {
    font-size: 16px;
}

h1 {
    font-size: 2rem;
}
```

Therefore:

```text
2rem = 32px
```

assuming the root font size is 16px.

---

# 3. `font-weight`

`font-weight` controls **how thick/bold the text is**.

Example:

```css
h1 {
    font-weight: bold;
}
```

You can also use numbers:

```css
h1 {
    font-weight: 700;
}
```

Common values:

```text
100 → very thin
200
300 → light
400 → normal
500 → medium
600 → semi-bold
700 → bold
800
900 → very bold
```

For example:

```css
.normal {
    font-weight: 400;
}

.bold {
    font-weight: 700;
}
```

Generally:

```text
400 = normal
700 = bold
```

are the most important values to remember.

---

# 4. `font-style`

`font-style` controls whether text is **normal, italic, or oblique**.

Most commonly:

```css
p {
    font-style: italic;
}
```

Output:

```text
This text is italic.
```

Normal:

```css
p {
    font-style: normal;
}
```

The common values are:

```text
normal
italic
oblique
```

### Example

```css
.normal {
    font-style: normal;
}

.italic {
    font-style: italic;
}
```

---

# 5. `line-height` ⭐⭐⭐

`line-height` controls the **vertical space between lines of text**.

This is extremely important for readability.

Example:

```css
p {
    line-height: 1.6;
}
```

Suppose:

```css
p {
    font-size: 16px;
    line-height: 1.6;
}
```

The approximate line height becomes:

```text
16 × 1.6 = 25.6px
```

So each line gets around 25.6px of vertical space.

---

## Why is `line-height` important?

Without enough line spacing:

```text
This is a paragraph with
lines that are very close
together and difficult to read.
```

With proper line height:

```text
This is a paragraph with

lines that have enough

vertical spacing and are

easier to read.
```

For paragraphs, values around:

```css
line-height: 1.5;
```

to:

```css
line-height: 1.8;
```

are often comfortable, depending on the font and design.

---

## `line-height` can use different values

### Number

```css
p {
    line-height: 1.5;
}
```

This is often preferred because it scales with the font size.

### Pixels

```css
p {
    line-height: 24px;
}
```

### Other length units

```css
p {
    line-height: 1.5rem;
}
```

For general text, understanding unitless values like `1.5` is especially useful.

---

# 6. `letter-spacing`

`letter-spacing` controls the **horizontal space between characters**.

Example:

```css
h1 {
    letter-spacing: 2px;
}
```

It produces:

```text
H e l l o
```

with additional spacing between characters.

Normal:

```css
h1 {
    letter-spacing: normal;
}
```

You can also use negative values:

```css
h1 {
    letter-spacing: -1px;
}
```

This brings letters closer together.

---

## Practical example

For headings:

```css
h1 {
    letter-spacing: 1px;
}
```

For uppercase navigation:

```css
.nav-link {
    letter-spacing: 0.5px;
}
```

Don't use extremely large spacing because it can hurt readability.

---

# 7. `text-align`

`text-align` controls the **horizontal alignment of inline content/text** inside an element.

Common values:

```text
left
center
right
justify
```

### Left

```css
p {
    text-align: left;
}
```

```text
Hello World
```

### Center

```css
h1 {
    text-align: center;
}
```

```text
          Hello World
```

### Right

```css
p {
    text-align: right;
}
```

```text
                    Hello World
```

### Justify

```css
p {
    text-align: justify;
}
```

The browser adjusts spacing so lines generally align with both sides of the text area.

This is sometimes used for article-style content.

---

# 8. `text-decoration`

`text-decoration` adds or removes decorations from text.

Common example:

```css
a {
    text-decoration: none;
}
```

This removes the default underline from links.

---

## Underline

```css
p {
    text-decoration: underline;
}
```

Example:

```text
Hello World
───────────
```

---

## Line-through

```css
p {
    text-decoration: line-through;
}
```

Example:

```text
H̶e̶l̶l̶o̶
```

Useful for:

* Old prices
* Deleted text
* Completed tasks

---

## Overline

```css
p {
    text-decoration: overline;
}
```

---

## Common real-world example

Browser links normally have an underline:

```html
<a href="#">Home</a>
```

You can remove it:

```css
a {
    text-decoration: none;
}
```

Then when the user hovers:

```css
a:hover {
    text-decoration: underline;
}
```

This is very common.

---

# 9. `text-transform`

`text-transform` changes the **capitalization/display of text**.

It does not change the original HTML text; it changes how the text is displayed.

Main values:

```text
none
uppercase
lowercase
capitalize
```

---

## `uppercase`

```css
h1 {
    text-transform: uppercase;
}
```

HTML:

```html
<h1>Hello World</h1>
```

Displayed as:

```text
HELLO WORLD
```

---

## `lowercase`

```css
h1 {
    text-transform: lowercase;
}
```

Displayed:

```text
hello world
```

---

## `capitalize`

```css
p {
    text-transform: capitalize;
}
```

For example:

```text
hello world from inskill
```

becomes approximately:

```text
Hello World From Inskill
```

---

## `none`

```css
p {
    text-transform: none;
}
```

Displays the text normally.

---

# 10. `text-shadow`

`text-shadow` adds a **shadow behind text**.

Syntax:

```css
text-shadow: x-offset y-offset blur color;
```

Example:

```css
h1 {
    text-shadow: 2px 2px 4px gray;
}
```

Meaning:

```text
2px → horizontal offset
2px → vertical offset
4px → blur
gray → shadow color
```

---

## Example

```css
h1 {
    color: white;
    text-shadow: 2px 2px 5px black;
}
```

This is commonly used on text placed over images.

For example:

```text
┌─────────────────────────────────┐
│                                 │
│       Welcome to Inskill        │
│              ↓                  │
│           shadow                │
│                                 │
└─────────────────────────────────┘
```

---

# 11. Multiple Text Shadows

You can add multiple shadows by separating them with commas.

```css
h1 {
    text-shadow:
        2px 2px 3px gray,
        -2px -2px 3px black;
}
```

You don't need to use this frequently as a beginner, but you should know that multiple shadows are possible.

---

# 12. Putting Everything Together ⭐

Let's create a simple website heading and paragraph.

### HTML

```html
<div class="content">
    <h1>Welcome to Inskill</h1>

    <p>
        Learn web development and build your career
        with practical skills.
    </p>
</div>
```

### CSS

```css
.content {
    text-align: center;
}

h1 {
    font-family: Arial, sans-serif;
    font-size: 40px;
    font-weight: 700;
    font-style: normal;
    line-height: 1.2;
    letter-spacing: 1px;
    text-transform: uppercase;
    text-shadow: 2px 2px 4px gray;
}

p {
    font-family: Arial, sans-serif;
    font-size: 18px;
    font-weight: 400;
    line-height: 1.6;
    letter-spacing: 0.5px;
    text-align: center;
}
```

Here we're controlling almost every aspect of the typography.

---

# 13. Shorthand: `font`

There is also a `font` shorthand property.

Instead of:

```css
h1 {
    font-style: italic;
    font-weight: 700;
    font-size: 30px;
    line-height: 1.5;
    font-family: Arial, sans-serif;
}
```

You can write:

```css
h1 {
    font: italic 700 30px/1.5 Arial, sans-serif;
}
```

The general order is:

```text
font-style
font-weight
font-size / line-height
font-family
```

### Important

You **should understand individual properties first**.

For interviews, know that `font` is a shorthand, but you don't need to use shorthand everywhere.

---

# 14. `font-family` vs `font-style` vs `font-weight`

These are easy to confuse.

### `font-family`

Which typeface?

```css
font-family: Arial;
```

### `font-size`

How large?

```css
font-size: 20px;
```

### `font-weight`

How thick?

```css
font-weight: 700;
```

### `font-style`

Normal or italic?

```css
font-style: italic;
```

Think:

```text
Family → Which font?
Size   → How big?
Weight → How thick?
Style  → Italic/normal?
```

---

# 15. `line-height` vs `letter-spacing`

Another common interview question.

### `line-height`

Controls **vertical space between lines**.

```css
p {
    line-height: 1.6;
}
```

### `letter-spacing`

Controls **horizontal space between letters**.

```css
p {
    letter-spacing: 1px;
}
```

Easy memory:

```text
line-height     → line spacing
letter-spacing  → letter spacing
```

---

# 16. Typography Example for a Card

This is closer to what you'll actually write in a project.

```html
<div class="card">
    <h2>React JS Course</h2>

    <p>
        Learn React from fundamentals to advanced concepts.
    </p>

    <button>Enroll Now</button>
</div>
```

```css
.card {
    width: 350px;
    padding: 25px;
}

.card h2 {
    font-family: Arial, sans-serif;
    font-size: 24px;
    font-weight: 700;
    line-height: 1.2;
    letter-spacing: 0.5px;
    text-align: center;
}

.card p {
    font-family: Arial, sans-serif;
    font-size: 16px;
    font-weight: 400;
    line-height: 1.6;
    text-align: left;
}

.card button {
    font-size: 16px;
    font-weight: 600;
    text-transform: uppercase;
}
```

This combination is much more important in real development than memorizing isolated properties.

---

# 17. Important Interview Questions ⭐⭐⭐

### Q1. What does `font-family` do?

It specifies the typeface used to display text.

```css
font-family: Arial, sans-serif;
```

---

### Q2. What does `font-weight` do?

It controls the thickness/boldness of text.

```css
font-weight: 700;
```

---

### Q3. What is the difference between `font-weight` and `font-style`?

```text
font-weight → thickness/boldness
font-style  → normal/italic/oblique
```

---

### Q4. What does `line-height` control?

It controls the vertical space occupied by lines of text.

---

### Q5. What does `letter-spacing` do?

It controls the spacing between individual characters.

---

### Q6. What does `text-transform` do?

It changes the displayed capitalization of text.

```css
text-transform: uppercase;
```

---

### Q7. How do you remove underline from a link?

```css
a {
    text-decoration: none;
}
```

---

### Q8. How do you center text?

```css
text-align: center;
```

---

### Q9. How do you add a shadow to text?

```css
h1 {
    text-shadow: 2px 2px 4px gray;
}
```

---

# 18. Quick Cheat Sheet

| Property          | Purpose                | Example             |
| ----------------- | ---------------------- | ------------------- |
| `font-family`     | Font type              | `Arial, sans-serif` |
| `font-size`       | Text size              | `20px`              |
| `font-weight`     | Text thickness         | `700`               |
| `font-style`      | Italic/normal          | `italic`            |
| `line-height`     | Line spacing           | `1.6`               |
| `letter-spacing`  | Letter spacing         | `1px`               |
| `text-align`      | Text alignment         | `center`            |
| `text-decoration` | Underline/line-through | `none`              |
| `text-transform`  | Capitalization         | `uppercase`         |
| `text-shadow`     | Text shadow            | `2px 2px 4px gray`  |

### The easiest way to remember:

```text
font-family     → Which font?
font-size       → How big?
font-weight     → How thick?
font-style      → Italic or normal?
line-height     → Space between lines
letter-spacing  → Space between letters
text-align      → Where is text aligned?
text-decoration → Underline etc.
text-transform  → Uppercase/lowercase
text-shadow     → Shadow behind text
```

## ⭐ What matters most for interviews

Make sure you can confidently explain and use:

1. `font-family`
2. `font-size`
3. `font-weight`
4. `line-height`
5. `text-align`
6. `text-decoration`
7. `text-transform`
8. `letter-spacing`
9. `text-shadow`
