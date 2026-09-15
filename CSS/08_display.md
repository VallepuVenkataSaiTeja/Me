# 8. CSS `display` ⭐⭐

The `display` property is very important because it controls **how an HTML element behaves in the layout**.

The main values you should know are:

```text
block
inline
inline-block
none
```

And later, you'll use:

```text
flex
grid
```

But we'll learn Flexbox and Grid separately.

---

# 1. What is `display`?

The `display` property tells the browser **how an element should be laid out**.

Example:

```css
.box {
    display: block;
}
```

You can change the default behavior of HTML elements.

For example, a `<span>` is normally inline:

```html
<span>Hello</span>
<span>World</span>
```

But you can make it behave like a block:

```css
span {
    display: block;
}
```

Now the spans appear on separate lines.

---

# 2. `display: block` ⭐⭐⭐

A block-level element generally:

* Starts on a new line
* Takes the available width by default
* Allows `width` and `height`
* Allows `margin` and `padding`

Common block elements:

```text
<div>
<p>
<h1> - <h6>
<section>
<header>
<footer>
<nav>
```

Example:

```html
<div class="box">Box 1</div>
<div class="box">Box 2</div>
```

```css
.box {
    display: block;
    background-color: lightblue;
}
```

Result:

```text
┌─────────────────────────────┐
│ Box 1                       │
└─────────────────────────────┘

┌─────────────────────────────┐
│ Box 2                       │
└─────────────────────────────┘
```

Each starts on a new line.

---

## Width and height with block

```css
.box {
    display: block;
    width: 300px;
    height: 100px;
}
```

This works because block elements accept explicit width and height.

---

# 3. `display: inline` ⭐⭐⭐

An inline element stays **within the same line** as surrounding content when space is available.

Common inline elements:

```text
<span>
<a>
<strong>
<em>
```

Example:

```html
<span>Hello</span>
<span>World</span>
```

Normally:

```text
Hello World
```

rather than:

```text
Hello
World
```

---

## Inline elements don't behave like block elements

Consider:

```css
span {
    display: inline;
    width: 300px;
    height: 100px;
}
```

The `width` and `height` do **not work in the normal way you might expect** for an inline element.

That's an important distinction.

---

# 4. `display: inline-block` ⭐⭐⭐

`inline-block` combines important characteristics of both.

It:

* Stays on the same line like `inline`
* Accepts `width` and `height` like `block`

Example:

```html
<span class="box">One</span>
<span class="box">Two</span>
<span class="box">Three</span>
```

```css
.box {
    display: inline-block;
    width: 100px;
    height: 50px;
    padding: 10px;
    background-color: lightblue;
}
```

They can appear next to each other:

```text
┌──────────┐ ┌──────────┐ ┌──────────┐
│   One    │ │   Two    │ │  Three   │
└──────────┘ └──────────┘ └──────────┘
```

This was historically useful for creating simple horizontal layouts before Flexbox became the standard approach.

---

# 5. Block vs Inline vs Inline-block ⭐⭐⭐

This is one of the most important things to understand.

| Feature               | `block` | `inline`                                | `inline-block` |
| --------------------- | ------- | --------------------------------------- | -------------- |
| New line?             | Yes     | No                                      | No             |
| Width works?          | Yes     | Not normally                            | Yes            |
| Height works?         | Yes     | Not normally                            | Yes            |
| Can sit side-by-side? | No      | Yes                                     | Yes            |
| Padding?              | Yes     | Yes, but behavior differs               | Yes            |
| Margin?               | Yes     | Horizontal mainly in normal inline flow | Yes            |

### Easy memory:

```text
block
→ new line
→ width/height work

inline
→ same line
→ width/height don't work normally

inline-block
→ same line
→ width/height work
```

---

# 6. `display: none` ⭐⭐⭐

`display: none` completely removes an element from the layout.

Example:

```css
.box {
    display: none;
}
```

HTML:

```html
<div class="box">
    You cannot see me.
</div>
```

The element doesn't appear.

More importantly:

> It doesn't occupy space in the layout.

Example:

```html
<div>Box 1</div>

<div class="hidden">Box 2</div>

<div>Box 3</div>
```

```css
.hidden {
    display: none;
}
```

The layout behaves approximately like:

```text
Box 1

Box 3
```

There is no empty space reserved for Box 2.

---

# 7. `display: none` vs `visibility: hidden` ⭐⭐⭐

This is a very common interview question.

### `display: none`

```css
.box {
    display: none;
}
```

The element:

```text
❌ Not visible
❌ Doesn't occupy space
```

### `visibility: hidden`

```css
.box {
    visibility: hidden;
}
```

The element:

```text
❌ Not visible
✅ Still occupies space
```

Example:

```text
display: none:

┌───────┐
│ Box 1 │
└───────┘
┌───────┐
│ Box 3 │
└───────┘
```

With `visibility: hidden`:

```text
┌───────┐
│ Box 1 │
└───────┘

   [empty space]

┌───────┐
│ Box 3 │
└───────┘
```

### Remember:

```text
display: none
→ disappears + no space

visibility: hidden
→ disappears + space remains
```

---

# 8. `display` and HTML Elements

Many HTML elements have default display behaviors.

For example:

```text
<div>      → block
<p>        → block
<h1>       → block
<section>  → block
<span>     → inline
<a>        → inline
<strong>   → inline
```

But these are **default browser styles**, not permanent rules.

You can change them.

For example:

```css
span {
    display: block;
}
```

Now the `<span>` behaves as a block-level box.

---

# 9. Converting Inline to Block

Suppose:

```html
<a href="#">Home</a>
<a href="#">About</a>
<a href="#">Contact</a>
```

Links are normally inline.

You can make them block-level:

```css
a {
    display: block;
}
```

Now:

```text
Home
About
Contact
```

Each occupies its own line.

This can be useful for things like mobile menus.

---

# 10. Converting Block to Inline

You can also do the opposite:

```css
div {
    display: inline;
}
```

Now the div participates in inline formatting.

However, you generally shouldn't change every block element to inline without a reason.

---

# 11. `inline-block` Practical Example

Suppose you have three buttons:

```html
<button>Login</button>
<button>Register</button>
<button>Contact</button>
```

You could style them as:

```css
button {
    display: inline-block;
    width: 120px;
    padding: 10px;
}
```

They can appear next to one another while still accepting dimensions.

Today, **Flexbox is usually preferred for controlling groups of elements**, but understanding `inline-block` is still important.

---

# 12. Important: `display` Is Not the Same as `position`

Don't confuse these two.

### `display`

Controls **how an element participates in layout**.

```css
display: block;
display: inline;
display: flex;
display: grid;
```

### `position`

Controls **how an element is positioned**.

```css
position: static;
position: relative;
position: absolute;
position: fixed;
position: sticky;
```

You'll learn `position` next.

Easy memory:

```text
display  → layout behavior
position → positioning behavior
```

---

# 13. `display: flex`

You don't need to deeply learn Flexbox yet, because it's the next major layout topic.

But you should recognize:

```css
.container {
    display: flex;
}
```

This changes the container into a **flex container**.

Its children become flex items.

For example:

```html
<div class="container">
    <div>One</div>
    <div>Two</div>
    <div>Three</div>
</div>
```

```css
.container {
    display: flex;
}
```

Conceptually:

```text
┌───────┐ ┌───────┐ ┌───────┐
│  One  │ │  Two  │ │ Three │
└───────┘ └───────┘ └───────┘
```

We'll learn all of this in **Flexbox**.

---

# 14. `display: grid`

Similarly:

```css
.container {
    display: grid;
}
```

creates a grid container.

Example:

```text
┌────────┐ ┌────────┐
│   1    │ │   2    │
├────────┼─┼────────┤
│   3    │ │   4    │
└────────┘ └────────┘
```

We'll learn Grid separately.

---

# 15. A Real-World Navbar Example

Consider:

```html
<nav>
    <a href="#">Home</a>
    <a href="#">About</a>
    <a href="#">Courses</a>
    <a href="#">Contact</a>
</nav>
```

You might want the links side-by-side.

Modern CSS would typically use Flexbox:

```css
nav {
    display: flex;
}
```

But older/simple layouts could use:

```css
nav a {
    display: inline-block;
    padding: 10px 20px;
}
```

So understanding `display` helps you understand **why Flexbox works**.

---

# 16. A Very Important Concept: Parent vs Child

When you write:

```css
.container {
    display: flex;
}
```

you're changing the **parent's layout behavior**.

The children:

```html
<div class="container">
    <div>One</div>
    <div>Two</div>
</div>
```

become flex items.

Similarly:

```css
.container {
    display: grid;
}
```

changes how its children participate in the grid.

This parent-child relationship is fundamental to CSS layouts.

---

# 17. Common Interview Questions ⭐⭐⭐

### Q1. What is the `display` property?

`display` controls how an element participates in the layout and how it is rendered in relation to surrounding elements.

---

### Q2. Difference between block and inline?

```text
block:
→ starts on a new line
→ width/height can be specified

inline:
→ stays in the same line
→ width/height don't work normally
```

---

### Q3. What is `inline-block`?

`inline-block` allows an element to sit inline with other elements while still accepting width and height.

---

### Q4. What does `display: none` do?

It removes the element from the layout and makes it not rendered.

---

### Q5. Difference between `display: none` and `visibility: hidden`?

```text
display: none
→ hidden
→ no layout space

visibility: hidden
→ hidden
→ layout space remains
```

---

### Q6. Can you change the default display behavior of an HTML element?

Yes.

For example:

```css
span {
    display: block;
}
```

---

### Q7. What is the difference between `display: flex` and `display: block`?

```text
block
→ normal block layout

flex
→ creates a flex formatting context
→ provides powerful control over child layout
```

You'll learn Flexbox in detail later.

---

# 18. Most Important Things to Remember

```text
display: block;
```

```text
→ new line
→ width/height work
```

---

```text
display: inline;
```

```text
→ same line
→ width/height don't work normally
```

---

```text
display: inline-block;
```

```text
→ same line
→ width/height work
```

---

```text
display: none;
```

```text
→ invisible
→ no space
```

---

```text
visibility: hidden;
```

```text
→ invisible
→ space remains
```

---

# 19. Final Cheat Sheet ⭐

| Property                | Behavior                                    |
| ----------------------- | ------------------------------------------- |
| `display: block`        | New line, takes available width             |
| `display: inline`       | Same line, width/height don't work normally |
| `display: inline-block` | Same line + width/height work               |
| `display: none`         | Removed from layout                         |
| `visibility: hidden`    | Hidden but space remains                    |
| `display: flex`         | Flexbox layout                              |
| `display: grid`         | Grid layout                                 |

### One-line interview memory:

> **Block starts a new line, inline stays in the same line, inline-block stays inline while allowing dimensions, and `display: none` removes the element from the layout.**

---

## What you should know before moving ahead

For your **CSS interview preparation**, be confident with:

```text
✅ block
✅ inline
✅ inline-block
✅ none
✅ display vs visibility
✅ display vs position
✅ basic idea of flex and grid
```
