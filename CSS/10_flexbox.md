# 10. CSS Flexbox ⭐⭐⭐

**Flexbox is one of the most important CSS topics for frontend interviews.**

If you work with React, you'll use Flexbox constantly for:

* Navbar layouts
* Buttons
* Cards
* Forms
* Centering elements
* Aligning icons and text
* Responsive layouts
* Horizontal/vertical layouts

The good news is that Flexbox has a small number of important concepts. You don't need to memorize everything.

---

# 1. What is Flexbox?

**Flexbox = Flexible Box Layout**

It is a CSS layout system used to arrange elements in **one direction**:

* horizontally → row
* vertically → column

For example:

```html
<div class="container">
    <div>Box 1</div>
    <div>Box 2</div>
    <div>Box 3</div>
</div>
```

Without Flexbox:

```text
Box 1
Box 2
Box 3
```

With:

```css
.container {
    display: flex;
}
```

you get:

```text
Box 1   Box 2   Box 3
```

---

# 2. Parent and Children

This is the first thing you need to understand.

```html
<div class="container">
    <div class="box">1</div>
    <div class="box">2</div>
    <div class="box">3</div>
</div>
```

Here:

```text
.container
    ↓
Flex container

.box
.box
.box
    ↓
Flex items
```

When you write:

```css
.container {
    display: flex;
}
```

the **parent becomes a flex container**.

Its direct children become **flex items**.

```text
Parent
┌───────────────────────────────┐
│                               │
│  Child 1   Child 2   Child 3 │
│                               │
└───────────────────────────────┘
       ↑          ↑        ↑
   flex items
```

This distinction is extremely important.

---

# 3. `display: flex`

You activate Flexbox using:

```css
.container {
    display: flex;
}
```

Example:

```html
<div class="container">
    <div class="box">Box 1</div>
    <div class="box">Box 2</div>
    <div class="box">Box 3</div>
</div>
```

```css
.container {
    display: flex;
}

.box {
    width: 100px;
    height: 100px;
}
```

The boxes will normally appear in a row.

---

# 4. Main Axis and Cross Axis ⭐⭐⭐

This is one of the most important Flexbox concepts.

Flexbox has two axes:

```text
Main Axis
Cross Axis
```

By default:

```css
flex-direction: row;
```

So:

```text
Main axis →
────────────────────────────→

Cross axis
     ↓
     ↓
     ↓
```

### When direction is `row`

```text
Main axis   → horizontal
Cross axis  ↓ vertical
```

### When direction is `column`

```text
Main axis   ↓ vertical
Cross axis  → horizontal
```

This is important because:

> `justify-content` works along the **main axis**.

> `align-items` works along the **cross axis**.

We'll come back to this.

---

# 5. `flex-direction` ⭐⭐⭐

Controls the direction of flex items.

```css
.container {
    display: flex;
    flex-direction: row;
}
```

There are four values:

```text
row
row-reverse
column
column-reverse
```

---

## `row`

Default:

```css
flex-direction: row;
```

```text
1   2   3
→
```

Items go from left to right in the usual writing direction.

---

## `row-reverse`

```css
flex-direction: row-reverse;
```

```text
3   2   1
←
```

---

## `column`

```css
flex-direction: column;
```

```text
1
2
3
↓
```

---

## `column-reverse`

```css
flex-direction: column-reverse;
```

```text
3
2
1
↑
```

### Interview memory:

```text
row
→ horizontal

column
→ vertical
```

---

# 6. `justify-content` ⭐⭐⭐

This is probably the most commonly used Flexbox property.

It controls how items are distributed along the **main axis**.

Example:

```css
.container {
    display: flex;
    justify-content: center;
}
```

---

## `justify-content: flex-start`

```css
justify-content: flex-start;
```

Items start from the beginning.

```text
[1] [2] [3]
```

---

## `justify-content: flex-end`

```css
justify-content: flex-end;
```

```text
            [1] [2] [3]
```

---

## `justify-content: center`

```css
justify-content: center;
```

```text
       [1] [2] [3]
```

Very commonly used.

---

## `justify-content: space-between`

```css
justify-content: space-between;
```

First item at the start, last item at the end, equal space between them.

```text
[1]        [2]        [3]
```

---

## `space-around`

```css
justify-content: space-around;
```

Space around each item.

Conceptually:

```text
  [1]    [2]    [3]
```

---

## `space-evenly`

```css
justify-content: space-evenly;
```

Equal spacing between items and the container edges.

```text
   [1]     [2]     [3]
```

### Main values to remember:

```text
flex-start
flex-end
center
space-between
space-around
space-evenly
```

---

# 7. `align-items` ⭐⭐⭐

`align-items` controls alignment along the **cross axis**.

Example:

```css
.container {
    display: flex;
    align-items: center;
}
```

Suppose direction is:

```css
flex-direction: row;
```

Then:

```text
justify-content
→ horizontal

align-items
→ vertical
```

---

## Example

```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

This centers items horizontally and vertically **inside the flex container**.

This is extremely useful.

---

# 8. The famous centering code ⭐⭐⭐

You will use this constantly:

```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

If the container has a height:

```css
.container {
    height: 300px;

    display: flex;
    justify-content: center;
    align-items: center;
}
```

The child is centered:

```text
┌───────────────────────────┐
│                           │
│                           │
│          BOX              │
│                           │
│                           │
└───────────────────────────┘
```

### Interview question:

**How do you center an element horizontally and vertically using Flexbox?**

Answer:

```css
display: flex;
justify-content: center;
align-items: center;
```

---

# 9. `align-items` common values

```text
stretch
flex-start
flex-end
center
baseline
```

### `center`

```css
align-items: center;
```

Centers items on the cross axis.

### `flex-start`

```css
align-items: flex-start;
```

Moves them toward the start of the cross axis.

### `flex-end`

```css
align-items: flex-end;
```

Moves them toward the end.

### `stretch`

```css
align-items: stretch;
```

Default in many cases.

Items can stretch across the cross axis when their cross-size is auto.

### `baseline`

Aligns items according to their text baselines.

---

# 10. `flex-wrap` ⭐⭐

By default, flex items try to stay on one line.

```css
.container {
    display: flex;
}
```

If there isn't enough space:

```text
[1] [2] [3] [4] [5]
```

items may become too cramped or overflow depending on their sizing.

Use:

```css
flex-wrap: wrap;
```

Then they can move onto multiple lines.

```text
[1] [2] [3]
[4] [5]
```

Example:

```css
.container {
    display: flex;
    flex-wrap: wrap;
}
```

Very useful for responsive card layouts.

---

# 11. `flex-wrap` values

```text
nowrap
wrap
wrap-reverse
```

Default:

```css
flex-wrap: nowrap;
```

Common choice:

```css
flex-wrap: wrap;
```

---

# 12. `gap` ⭐⭐⭐

`gap` adds space between flex items.

```css
.container {
    display: flex;
    gap: 20px;
}
```

Result:

```text
[Box 1]   [Box 2]   [Box 3]
```

This is usually much cleaner than doing:

```css
.box {
    margin-right: 20px;
}
```

For modern layouts, prefer:

```css
gap: 20px;
```

when you want consistent spacing between flex items.

---

# 13. `row-gap` and `column-gap`

You can control them separately.

```css
.container {
    row-gap: 20px;
    column-gap: 30px;
}
```

Or:

```css
gap: 20px 30px;
```

Meaning:

```text
row gap    = 20px
column gap = 30px
```

---

# 14. `flex-flow`

`flex-flow` is shorthand for:

```text
flex-direction
flex-wrap
```

Instead of:

```css
.container {
    flex-direction: row;
    flex-wrap: wrap;
}
```

you can write:

```css
.container {
    flex-flow: row wrap;
}
```

You don't need to prioritize this for interviews, but you should recognize it.

---

# 15. Flexbox item properties

So far we've mostly discussed **container properties**.

Now let's look at properties applied to individual flex items.

Important ones:

```text
flex
flex-grow
flex-shrink
flex-basis
order
align-self
```

---

# 16. `flex-grow` ⭐⭐

Controls how a flex item can grow when there is extra available space.

Example:

```css
.box1 {
    flex-grow: 1;
}
```

If multiple items have:

```css
.box1 {
    flex-grow: 1;
}

.box2 {
    flex-grow: 1;
}
```

they can share available extra space.

Conceptually:

```text
Before:

[1] [2]

Extra space available

After:

[    1    ] [    2    ]
```

If:

```css
.box1 {
    flex-grow: 2;
}

.box2 {
    flex-grow: 1;
}
```

the available extra space is distributed in a **2:1 ratio**.

---

# 17. `flex-shrink`

Controls how an item can shrink when there isn't enough space.

```css
.box {
    flex-shrink: 1;
}
```

Default is generally:

```css
flex-shrink: 1;
```

If:

```css
.box {
    flex-shrink: 0;
}
```

the item won't shrink due to flex shrinking.

Example:

```css
.box {
    width: 300px;
    flex-shrink: 0;
}
```

This is useful when you don't want a flex item to become smaller than its intended size.

---

# 18. `flex-basis`

Defines the item's initial size along the **main axis** before remaining space is distributed.

Example:

```css
.box {
    flex-basis: 200px;
}
```

For a row:

```text
main axis → horizontal

basis = initial width-like size
```

For a column:

```text
main axis ↓ vertical

basis = initial height-like size
```

That's why `flex-basis` is more general than simply saying "width."

---

# 19. `flex` shorthand ⭐⭐⭐

Instead of writing:

```css
.box {
    flex-grow: 1;
    flex-shrink: 1;
    flex-basis: 0;
}
```

you can write:

```css
.box {
    flex: 1;
}
```

This is extremely common.

For example:

```css
.container {
    display: flex;
}

.box {
    flex: 1;
}
```

Three boxes:

```text
┌─────────────────────────────┐
│     1     │     2     │  3  │
│            equal widths     │
└─────────────────────────────┘
```

They share available space.

---

# 20. `flex: 1` — important interview concept

When you see:

```css
.box {
    flex: 1;
}
```

think:

> "This item should flex and share the available space."

For beginner/interview purposes, that's the key idea.

---

# 21. `order`

By default, flex items appear in HTML order.

```html
<div>1</div>
<div>2</div>
<div>3</div>
```

Result:

```text
1 2 3
```

You can change the visual order:

```css
.box1 {
    order: 3;
}

.box2 {
    order: 1;
}

.box3 {
    order: 2;
}
```

Result:

```text
2 3 1
```

Default:

```css
order: 0;
```

Important:

`order` changes **visual layout order**, not the underlying HTML/DOM order.

So don't use it carelessly for accessibility-sensitive content.

---

# 22. `align-self`

`align-self` allows one flex item to override the container's `align-items`.

Example:

```css
.container {
    display: flex;
    align-items: center;
}

.box2 {
    align-self: flex-start;
}
```

So:

```text
Box 1 → center
Box 2 → start
Box 3 → center
```

Useful when one particular item needs different cross-axis alignment.

---

# 23. `justify-content` vs `align-items` ⭐⭐⭐

This is probably the **#1 Flexbox interview question**.

Suppose:

```css
.container {
    display: flex;
    flex-direction: row;
}
```

Then:

```text
justify-content
→ main axis
→ horizontal

align-items
→ cross axis
→ vertical
```

So:

```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

means:

```text
horizontal center
        +
vertical center
```

---

# 24. But what if direction is column?

This is where beginners often get confused.

```css
.container {
    display: flex;
    flex-direction: column;
}
```

Now the axes change:

```text
Main axis
   ↓

Cross axis
   →
```

Therefore:

```text
justify-content
→ vertical

align-items
→ horizontal
```

### This is the important rule:

> Don't memorize `justify-content = horizontal` and `align-items = vertical`.

Instead memorize:

```text
justify-content → main axis
align-items     → cross axis
```

Then determine the direction.

---

# 25. Example with column

```css
.container {
    display: flex;
    flex-direction: column;

    justify-content: center;
    align-items: center;
}
```

This still centers the child horizontally and vertically.

Why?

```text
column
↓
main axis = vertical

justify-content
→ vertical center

align-items
→ horizontal center
```

---

# 26. `align-content` ⭐⭐

`align-content` is different from `align-items`.

It controls the spacing/alignment of **multiple flex lines** when wrapping occurs.

Example:

```css
.container {
    display: flex;
    flex-wrap: wrap;
    align-content: center;
}
```

This matters when you have:

```text
Line 1: [1] [2] [3]
Line 2: [4] [5] [6]
Line 3: [7] [8]
```

`align-content` controls the arrangement of those lines along the cross axis.

### Important distinction:

```text
align-items
→ items within a flex line

align-content
→ multiple flex lines
```

For most beginner layouts, you'll use `align-items` much more often.

---

# 27. Flexbox Container vs Item Properties

### Container properties

Applied to the parent:

```text
display
flex-direction
flex-wrap
flex-flow
justify-content
align-items
align-content
gap
row-gap
column-gap
```

Example:

```css
.container {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    gap: 20px;
}
```

### Item properties

Applied to children:

```text
flex-grow
flex-shrink
flex-basis
flex
order
align-self
```

---

# 28. Real-world Example — Navbar ⭐⭐⭐

HTML:

```html
<nav class="navbar">
    <div class="logo">Inskill</div>

    <div class="links">
        <a href="#">Home</a>
        <a href="#">About</a>
        <a href="#">Courses</a>
        <a href="#">Contact</a>
    </div>

    <button>Login</button>
</nav>
```

CSS:

```css
.navbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 15px 30px;
}

.links {
    display: flex;
    gap: 20px;
}
```

This is a very common Flexbox pattern.

```text
Logo       Home About Courses Contact       Login
```

---

# 29. Real-world Example — Cards

HTML:

```html
<div class="cards">
    <div class="card">Card 1</div>
    <div class="card">Card 2</div>
    <div class="card">Card 3</div>
</div>
```

CSS:

```css
.cards {
    display: flex;
    gap: 20px;
    flex-wrap: wrap;
}

.card {
    flex: 1;
    min-width: 250px;
}
```

This allows cards to share available space and wrap when necessary.

---

# 30. Real-world Example — Center a Login Form

```html
<div class="login-container">
    <div class="login-box">
        <h2>Login</h2>
        <input type="text">
        <button>Login</button>
    </div>
</div>
```

```css
.login-container {
    min-height: 100vh;

    display: flex;
    justify-content: center;
    align-items: center;
}
```

This centers the login box.

This pattern is extremely useful in real projects.

---

# 31. Flexbox vs Normal Flow

Normal flow:

```text
Box 1
Box 2
Box 3
```

Flexbox:

```text
Box 1   Box 2   Box 3
```

You can control:

* direction
* alignment
* spacing
* wrapping
* size distribution
* ordering

---

# 32. Flexbox vs Grid

You'll learn Grid next.

The simple interview distinction is:

### Flexbox

Designed primarily for **one-dimensional layouts**.

```text
row
OR
column
```

### Grid

Designed for **two-dimensional layouts**.

```text
rows + columns
```

Think:

```text
Flexbox
→ 1D

Grid
→ 2D
```

This is one of the most common interview questions.

---

# 33. A Complete Flexbox Example

```html
<div class="container">

    <div class="box">
        Box 1
    </div>

    <div class="box">
        Box 2
    </div>

    <div class="box">
        Box 3
    </div>

</div>
```

```css
.container {
    display: flex;

    flex-direction: row;
    justify-content: space-between;
    align-items: center;

    flex-wrap: wrap;

    gap: 20px;
}

.box {
    flex: 1;
    min-width: 200px;
    padding: 30px;
    background: lightblue;
}
```

Here:

```text
display: flex
→ activates Flexbox

flex-direction
→ controls direction

justify-content
→ main-axis distribution

align-items
→ cross-axis alignment

flex-wrap
→ allows multiple lines

gap
→ space between items

flex: 1
→ allows items to share available space
```

---

# ⭐ Flexbox Cheat Sheet

## Parent / Container

| Property          | Purpose                          |
| ----------------- | -------------------------------- |
| `display: flex`   | Enables Flexbox                  |
| `flex-direction`  | Row/column direction             |
| `justify-content` | Main-axis alignment              |
| `align-items`     | Cross-axis alignment             |
| `flex-wrap`       | Allows wrapping                  |
| `gap`             | Space between items              |
| `align-content`   | Alignment of multiple flex lines |

## Child / Item

| Property      | Purpose                         |
| ------------- | ------------------------------- |
| `flex-grow`   | Controls growing                |
| `flex-shrink` | Controls shrinking              |
| `flex-basis`  | Initial main-axis size          |
| `flex`        | Shorthand for flex sizing       |
| `order`       | Changes visual order            |
| `align-self`  | Individual cross-axis alignment |

---

# ⭐ Most Important Flexbox Memory

Remember these five things first:

```text
1. display: flex
        ↓
   activates Flexbox

2. flex-direction
        ↓
   row / column

3. justify-content
        ↓
   main axis

4. align-items
        ↓
   cross axis

5. gap
        ↓
   space between items
```

And:

```text
row:
    main axis   → 
    cross axis  ↓

column:
    main axis   ↓
    cross axis  →
```

---

# 🎯 Top Flexbox Interview Questions

### 1. What is Flexbox?

> Flexbox is a CSS one-dimensional layout system used to arrange and align elements in rows or columns.

### 2. How do you enable Flexbox?

```css
display: flex;
```

### 3. What are the two axes?

> Main axis and cross axis.

### 4. What does `justify-content` do?

> It controls the distribution of flex items along the main axis.

### 5. What does `align-items` do?

> It controls the alignment of flex items along the cross axis.

### 6. Difference between `justify-content` and `align-items`?

> `justify-content` works on the main axis, while `align-items` works on the cross axis.

### 7. How do you center an item using Flexbox?

```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

### 8. What does `flex-wrap` do?

> It allows flex items to move onto multiple lines when necessary.

### 9. Difference between Flexbox and Grid?

> Flexbox is primarily one-dimensional, while Grid is two-dimensional.

### 10. What does `gap` do?

> It creates space between flex items.

### 11. What is `flex: 1`?

> It allows a flex item to grow and share available space within the flex container.

### 12. What does `align-self` do?

> It allows an individual flex item to override the container's `align-items` setting.

---

# 🔥 What you should be able to code after this topic

You should now be comfortable creating:

```text
Navbar
├── Logo
├── Navigation links
└── Login button

Cards
├── Card 1
├── Card 2
└── Card 3

Login page
└── Centered login box

Header
├── Left content
├── Center content
└── Right content

Responsive card row
├── Card
├── Card
├── Card
└── Wrap on smaller screens
```
