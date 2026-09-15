# 11. CSS Grid ⭐⭐

**CSS Grid** is another very important layout system, especially for building:

* Card layouts
* Dashboards
* Product grids
* Image galleries
* Page layouts
* Responsive sections

You already learned **Flexbox**, which is mainly **one-dimensional**.

Grid is mainly used for **two-dimensional layouts**:

```text
Flexbox → 1D → row OR column

Grid    → 2D → rows AND columns
```

You don't need every advanced Grid feature for interviews. We'll focus on the important ones.

---

# 1. What is CSS Grid?

CSS Grid is a layout system that lets you arrange elements into:

* rows
* columns
* cells

Example:

```text
┌─────────┬─────────┬─────────┐
│ Card 1  │ Card 2  │ Card 3  │
├─────────┼─────────┼─────────┤
│ Card 4  │ Card 5  │ Card 6  │
└─────────┴─────────┴─────────┘
```

This is a perfect use case for Grid.

---

# 2. Creating a Grid

You enable Grid using:

```css
.container {
    display: grid;
}
```

Example:

```html
<div class="container">
    <div>Box 1</div>
    <div>Box 2</div>
    <div>Box 3</div>
</div>
```

```css
.container {
    display: grid;
}
```

At this point, the container is a **grid container**, and its direct children become **grid items**.

```text
.container
     ↓
Grid container

Box 1
Box 2
Box 3
     ↓
Grid items
```

---

# 3. `grid-template-columns` ⭐⭐⭐

This is one of the most important Grid properties.

It defines the columns.

Example:

```css
.container {
    display: grid;
    grid-template-columns: 200px 200px 200px;
}
```

This creates 3 columns:

```text
┌────────┬────────┬────────┐
│        │        │        │
│ Col 1  │ Col 2  │ Col 3  │
│        │        │        │
└────────┴────────┴────────┘
```

Each column is `200px`.

---

# 4. Using percentages

You can also use `%`.

```css
.container {
    display: grid;
    grid-template-columns: 33.33% 33.33% 33.33%;
}
```

This creates three roughly equal columns.

But there's an easier and more flexible way.

---

# 5. The `fr` unit ⭐⭐⭐

`fr` means **fraction of the available space**.

Example:

```css
.container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
}
```

This creates three equal columns.

```text
┌──────────┬──────────┬──────────┐
│   1fr    │   1fr    │   1fr    │
└──────────┴──────────┴──────────┘
```

If the container is 900px:

```text
1fr + 1fr + 1fr

900 / 3 = 300px each
```

So:

```text
Column 1 = 300px
Column 2 = 300px
Column 3 = 300px
```

---

# 6. Different `fr` values

You can use different fractions.

```css
.container {
    grid-template-columns: 1fr 2fr;
}
```

Total:

```text
1fr + 2fr = 3fr
```

The available space is divided into 3 parts.

```text
┌────────────┬──────────────────────┐
│    1fr     │         2fr          │
└────────────┴──────────────────────┘
```

The second column is twice as large as the first.

---

# 7. `grid-template-rows`

Just like columns, you can define rows.

```css
.container {
    display: grid;

    grid-template-columns: 1fr 1fr;
    grid-template-rows: 100px 200px;
}
```

Conceptually:

```text
Row 1 → 100px
Row 2 → 200px
```

```text
┌──────────┬──────────┐
│          │          │ 100px
├──────────┼──────────┤
│          │          │
│          │          │ 200px
└──────────┴──────────┘
```

---

# 8. `gap` ⭐⭐⭐

Just like Flexbox, Grid supports `gap`.

```css
.container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 20px;
}
```

This adds space between:

* rows
* columns

```text
┌───────┐ 20px ┌───────┐ 20px ┌───────┐
│ Card  │      │ Card  │      │ Card  │
└───────┘      └───────┘      └───────┘
```

You can also use:

```css
row-gap: 20px;
column-gap: 30px;
```

or:

```css
gap: 20px 30px;
```

Meaning:

```text
row gap    = 20px
column gap = 30px
```

---

# 9. `repeat()` ⭐⭐⭐

Instead of:

```css
grid-template-columns: 1fr 1fr 1fr;
```

you can write:

```css
grid-template-columns: repeat(3, 1fr);
```

Meaning:

```text
3 columns
each = 1fr
```

This is much cleaner.

### Another example

```css
grid-template-columns: repeat(4, 1fr);
```

Creates:

```text
1fr 1fr 1fr 1fr
```

---

# 10. `repeat()` with fixed sizes

You can also write:

```css
grid-template-columns: repeat(3, 200px);
```

Same as:

```css
grid-template-columns: 200px 200px 200px;
```

---

# 11. `minmax()` ⭐⭐

`minmax()` lets you specify a minimum and maximum size.

Example:

```css
grid-template-columns: repeat(3, minmax(200px, 1fr));
```

Meaning:

> Each column should be at least `200px`, but can grow up to `1fr`.

This is very useful for responsive grids.

---

# 12. Responsive Grid — very important ⭐⭐⭐

One of the most useful Grid patterns is:

```css
.container {
    display: grid;
    grid-template-columns: repeat(
        auto-fit,
        minmax(250px, 1fr)
    );
    gap: 20px;
}
```

This allows the browser to automatically fit as many columns as possible.

For example, on a large screen:

```text
┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐
│ Card │ │ Card │ │ Card │ │ Card │
└──────┘ └──────┘ └──────┘ └──────┘
```

On a smaller screen:

```text
┌──────┐ ┌──────┐
│ Card │ │ Card │
└──────┘ └──────┘
```

On mobile:

```text
┌──────────┐
│   Card   │
└──────────┘
```

This is a very useful real-world technique.

You don't necessarily need to memorize `auto-fit` vs `auto-fill` deeply at beginner level, but you should recognize this common pattern:

```css
repeat(auto-fit, minmax(250px, 1fr))
```

---

# 13. Grid items

Suppose:

```html
<div class="container">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
    <div class="item">5</div>
    <div class="item">6</div>
</div>
```

And:

```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
}
```

The browser automatically places them:

```text
┌────────┬────────┬────────┐
│   1    │   2    │   3    │
├────────┼────────┼────────┤
│   4    │   5    │   6    │
└────────┴────────┴────────┘
```

This is called **automatic grid placement**.

---

# 14. `grid-column` ⭐⭐⭐

You can tell an item how many columns it should occupy.

Example:

```css
.item1 {
    grid-column: span 2;
}
```

This item takes two columns:

```text
┌──────────────────┬─────────┐
│      Item 1      │ Item 2  │
│     span 2       │         │
└──────────────────┴─────────┘
```

---

# 15. `grid-row`

Similarly:

```css
.item1 {
    grid-row: span 2;
}
```

The item occupies two rows.

```text
┌────────────┬─────────┐
│            │ Item 2  │
│   Item 1   ├─────────┤
│            │ Item 3  │
└────────────┴─────────┘
```

---

# 16. `grid-column: span 2`

This is very common for dashboard layouts.

Example:

```css
.big-card {
    grid-column: span 2;
}
```

```text
┌───────────────────────┬─────────┐
│                       │ Card 2  │
│       Big Card        │         │
├───────────────────────┼─────────┤
│                       │ Card 3  │
│                       │         │
└───────────────────────┴─────────┘
```

---

# 17. Grid line numbers ⭐⭐

Grid columns have **grid lines**.

Example:

```text
       1        2        3        4
       │        │        │        │
       ↓        ↓        ↓        ↓
       ┌────────┬────────┬────────┐
       │        │        │        │
       │        │        │        │
       └────────┴────────┴────────┘
```

With three columns, there are **four vertical grid lines**.

You can position an item using:

```css
.item {
    grid-column: 1 / 3;
}
```

This means:

```text
start at line 1
end at line 3
```

So it occupies two columns.

---

# 18. `grid-column: 1 / 3` vs `span 2`

These are related:

```css
grid-column: 1 / 3;
```

means:

> Start at grid line 1 and end at grid line 3.

Whereas:

```css
grid-column: span 2;
```

means:

> Occupy two columns from the item's placement position.

For interviews, understanding `span` is usually enough initially.

---

# 19. `grid-area` ⭐⭐

`grid-area` can be used to position an item by specifying its grid lines:

```css
.item {
    grid-area: 1 / 1 / 3 / 3;
}
```

The four values are:

```text
row-start
column-start
row-end
column-end
```

So:

```text
grid-area:
1 / 1 / 3 / 3
↓   ↓   ↓   ↓
row column row column
start start end end
```

This is useful but not as important as the basic Grid properties.

---

# 20. `justify-items`

Controls horizontal alignment of grid items **inside their grid areas**.

```css
.container {
    display: grid;
    justify-items: center;
}
```

Common values:

```text
start
center
end
stretch
```

---

# 21. `align-items`

Grid also has:

```css
align-items: center;
```

This controls alignment along the vertical/cross direction of the grid's items within their areas.

So Grid has alignment concepts similar to Flexbox.

---

# 22. `place-items`

You can combine:

```css
justify-items
align-items
```

using:

```css
place-items: center;
```

Example:

```css
.container {
    display: grid;
    place-items: center;
}
```

This centers the grid items inside their grid areas.

---

# 23. `justify-content` and `align-content` in Grid

Grid also supports:

```css
justify-content
align-content
```

These deal with the **grid itself inside its container**, when there is extra space.

This is different from:

```css
justify-items
align-items
```

which deal with the **items inside their grid areas**.

For beginner interviews, remember:

```text
justify-items
→ item inside its grid cell

align-items
→ item inside its grid cell

justify-content
→ whole grid horizontally

align-content
→ whole grid vertically
```

---

# 24. Grid vs Flexbox ⭐⭐⭐

This is one of the most common interview questions.

### Flexbox

Primarily one-dimensional:

```text
row
OR
column
```

Example:

```text
Logo | Links | Login
```

Flexbox is excellent for:

* navbar
* button groups
* aligning elements
* simple rows/columns

---

### Grid

Two-dimensional:

```text
rows + columns
```

Example:

```text
┌──────┬──────┬──────┐
│  1   │  2   │  3   │
├──────┼──────┼──────┤
│  4   │  5   │  6   │
└──────┴──────┴──────┘
```

Grid is excellent for:

* dashboards
* galleries
* card grids
* page layouts

### Memory:

```text
Flexbox → 1D
Grid    → 2D
```

But remember: both can technically create many types of layouts. This is the **design intent** distinction, not a strict rule.

---

# 25. Real-world Example — Course Cards ⭐⭐⭐

Suppose your React website has courses:

```html
<div class="courses">

    <div class="course-card">
        React
    </div>

    <div class="course-card">
        JavaScript
    </div>

    <div class="course-card">
        CSS
    </div>

    <div class="course-card">
        Node.js
    </div>

</div>
```

CSS:

```css
.courses {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
}

.course-card {
    padding: 30px;
    background: white;
    border-radius: 10px;
}
```

Result:

```text
┌────────────┬────────────┬────────────┐
│   React    │ JavaScript │    CSS     │
├────────────┼────────────┼────────────┤
│   Node.js  │            │            │
└────────────┴────────────┴────────────┘
```

---

# 26. Responsive Course Cards

Better:

```css
.courses {
    display: grid;
    grid-template-columns: repeat(
        auto-fit,
        minmax(250px, 1fr)
    );
    gap: 20px;
}
```

Now the browser adjusts the number of columns depending on available width.

This is extremely useful for responsive websites.

---

# 27. `auto-fit` vs `auto-fill`

You may see:

```css
repeat(auto-fit, minmax(250px, 1fr));
```

and:

```css
repeat(auto-fill, minmax(250px, 1fr));
```

At beginner level, remember:

### `auto-fit`

Fits available columns and allows tracks to expand when possible.

### `auto-fill`

Creates as many possible tracks as fit, potentially preserving empty tracks.

For most common responsive card layouts, you'll frequently see:

```css
repeat(auto-fit, minmax(250px, 1fr))
```

Don't spend too much time memorizing the subtle difference initially.

---

# 28. Grid Example — Dashboard

```html
<div class="dashboard">

    <div class="sidebar">Sidebar</div>

    <div class="header">Header</div>

    <div class="content">Content</div>

</div>
```

Grid can create a layout such as:

```text
┌───────────┬─────────────────────┐
│           │       Header        │
│ Sidebar   ├─────────────────────┤
│           │       Content       │
└───────────┴─────────────────────┘
```

This is one reason Grid is very useful for larger page layouts.

---

# 29. `grid-template-areas` ⭐⭐

You can actually describe a layout using names.

Example:

```css
.dashboard {
    display: grid;

    grid-template-columns: 200px 1fr;

    grid-template-areas:
        "sidebar header"
        "sidebar content";
}
```

Then:

```css
.sidebar {
    grid-area: sidebar;
}

.header {
    grid-area: header;
}

.content {
    grid-area: content;
}
```

This creates:

```text
┌──────────┬────────────────────┐
│          │       Header       │
│ Sidebar  ├────────────────────┤
│          │      Content       │
└──────────┴────────────────────┘
```

This is useful for page-level layouts.

You don't need to master it immediately, but you should recognize it in real projects.

---

# 30. Grid `fr` vs `px`

Consider:

```css
grid-template-columns: 200px 200px 200px;
```

The columns have fixed sizes.

But:

```css
grid-template-columns: 1fr 1fr 1fr;
```

allows them to divide the available space.

For responsive layouts, `fr` is usually much more flexible.

---

# 31. Grid `minmax()` Example

A strong responsive pattern:

```css
.products {
    display: grid;
    grid-template-columns:
        repeat(auto-fit, minmax(250px, 1fr));

    gap: 20px;
}
```

Breakdown:

```text
display: grid
        ↓
Use Grid

repeat(...)
        ↓
Repeat columns

auto-fit
        ↓
Fit as many columns as possible

minmax(250px, 1fr)
        ↓
Minimum = 250px
Maximum = available fraction
```

This is a very useful pattern to know for frontend interviews.

---

# ⭐ Grid Cheat Sheet

### Container properties

```text
display: grid

grid-template-columns
grid-template-rows

gap
row-gap
column-gap

grid-template-areas

justify-items
align-items

justify-content
align-content
```

### Item properties

```text
grid-column
grid-row
grid-area
```

### Important functions/units

```text
fr
repeat()
minmax()
```

---

# ⭐ Most Important Grid Concepts

If you're preparing for interviews, prioritize these:

### 1. Enable Grid

```css
display: grid;
```

### 2. Create columns

```css
grid-template-columns: repeat(3, 1fr);
```

### 3. Create rows

```css
grid-template-rows: 100px 200px;
```

### 4. Add spacing

```css
gap: 20px;
```

### 5. Make an item span columns

```css
grid-column: span 2;
```

### 6. Responsive grid

```css
grid-template-columns:
    repeat(auto-fit, minmax(250px, 1fr));
```

### 7. Understand `fr`

```text
fr = fraction of available space
```

### 8. Understand Grid vs Flexbox

```text
Flexbox → primarily 1D
Grid    → primarily 2D
```

---

# 🎯 Top CSS Grid Interview Questions

### Q1. What is CSS Grid?

> CSS Grid is a two-dimensional CSS layout system used to arrange elements into rows and columns.

### Q2. How do you enable Grid?

```css
display: grid;
```

### Q3. What does `grid-template-columns` do?

> It defines the size and number of grid columns.

### Q4. What does `1fr` mean?

> `1fr` represents one fraction of the available grid space.

### Q5. What does `repeat()` do?

> It allows you to repeat a grid track definition multiple times.

Example:

```css
repeat(3, 1fr);
```

### Q6. What does `gap` do?

> It creates spacing between grid rows and columns.

### Q7. What is `minmax()`?

> It defines a minimum and maximum size for a grid track.

Example:

```css
minmax(200px, 1fr);
```

### Q8. How do you make an item span two columns?

```css
grid-column: span 2;
```

### Q9. Grid vs Flexbox?

> Flexbox is primarily one-dimensional, while Grid is primarily two-dimensional.

### Q10. How would you create a responsive card grid?

```css
.cards {
    display: grid;
    grid-template-columns:
        repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
}
```

---

# 🔥 Flexbox vs Grid — Final Memory

```text
                FLEXBOX              GRID
                  ↓                    ↓
                1D                    2D

             Row / Column        Rows + Columns

              Navbar               Dashboard
            Button groups         Card grids
              Alignment            Gallery
             Small layouts       Page layouts
```

Don't think **"Flexbox is only for rows and Grid is only for columns."** Both can handle different layouts. The important interview distinction is:

> **Flexbox is primarily designed for one-dimensional layout, while Grid is primarily designed for two-dimensional layout.**
