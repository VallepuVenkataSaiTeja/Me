# 9. CSS Position ⭐⭐⭐

`position` is one of the **most important CSS topics for interviews and real projects**.

It controls **how an element is positioned on the page**.

The main values you need to know are:

1. `static`
2. `relative` ⭐⭐⭐
3. `absolute` ⭐⭐⭐
4. `fixed` ⭐⭐⭐
5. `sticky` ⭐⭐⭐

And you should understand:

* `top`
* `right`
* `bottom`
* `left`
* `z-index`
* `relative + absolute` relationship

---

# 1. What is `position`?

Normally, HTML elements appear on the page according to the normal document flow.

For example:

```html
<div>Box 1</div>
<div>Box 2</div>
<div>Box 3</div>
```

They appear one after another.

CSS `position` allows you to change **where an element is positioned**.

Basic syntax:

```css
.box {
    position: relative;
}
```

---

# 2. `position: static`

`static` is the **default position** of almost every HTML element.

```css
.box {
    position: static;
}
```

The element follows the normal document flow.

Important:

With `static`, these generally don't move the element:

```css
top: 20px;
left: 30px;
right: 10px;
bottom: 20px;
```

Example:

```css
.box {
    position: static;
    top: 50px;
}
```

`top: 50px` won't have the expected positioning effect because the element is static.

### Interview point

> `static` is the default positioning value, and offset properties like `top`, `left`, `right`, and `bottom` don't reposition it.

---

# 3. `position: relative` ⭐⭐⭐

This is **very important**.

```css
.box {
    position: relative;
}
```

A relative element:

* stays in the normal document flow
* can be moved using `top`, `left`, `right`, `bottom`
* keeps its original space in the layout

Example:

```css
.box {
    position: relative;
    left: 50px;
}
```

The box moves **50px to the right**.

But its original space is still reserved.

### Think of it like this:

```text
Original:

[ BOX ]

After left: 50px:

[    BOX ]

Original space is still reserved.
```

---

## Example

```html
<div class="box">Hello</div>
```

```css
.box {
    width: 200px;
    height: 100px;
    background: lightblue;

    position: relative;
    left: 50px;
}
```

The box moves right by `50px`.

---

# 4. Why is `relative` so important?

Because it is commonly used as a **reference point for an absolutely positioned child**.

This combination is extremely important:

```css
.parent {
    position: relative;
}

.child {
    position: absolute;
}
```

We'll see why shortly.

---

# 5. `position: absolute` ⭐⭐⭐

`absolute` removes the element from the normal document flow.

```css
.box {
    position: absolute;
}
```

Then you can position it using:

```css
top
right
bottom
left
```

Example:

```css
.box {
    position: absolute;
    top: 20px;
    left: 30px;
}
```

The element is positioned according to its **containing block**, typically the nearest ancestor that establishes positioning.

This is where `relative + absolute` becomes important.

---

# 6. `relative + absolute` ⭐⭐⭐

This is one of the most common CSS patterns.

Suppose we have:

```html
<div class="card">
    <span class="badge">New</span>
</div>
```

We want the badge to appear in the **top-right corner of the card**.

Use:

```css
.card {
    position: relative;
}

.badge {
    position: absolute;
    top: 10px;
    right: 10px;
}
```

### What happens?

The `.card` becomes the reference point.

```text
┌──────────────────────────┐
│                    New   │ ← badge
│                          │
│          CARD            │
│                          │
└──────────────────────────┘
```

The badge is positioned relative to the card.

---

# 7. Why `position: relative` on the parent?

This is a very common interview question.

Consider:

```css
.parent {
    position: relative;
}

.child {
    position: absolute;
    top: 0;
    right: 0;
}
```

The child looks for its **nearest positioned ancestor**.

A positioned ancestor is generally an ancestor whose `position` is not `static`, such as:

```css
relative
absolute
fixed
sticky
```

So:

```text
Parent
  ↓
position: relative
  ↓
Child
  ↓
position: absolute
```

The child uses that parent as its positioning reference.

### Easy memory:

> **Relative parent → Absolute child**

This pattern is used everywhere.

---

# 8. What happens without `position: relative`?

Suppose:

```css
.card {
    /* no position */
}

.badge {
    position: absolute;
    top: 10px;
    right: 10px;
}
```

If `.card` isn't a positioned ancestor, the badge will look for the next suitable ancestor.

If none exists, its containing block is based on the relevant page/root containing block.

So it may end up positioned relative to the page rather than your card.

That's why we commonly write:

```css
.card {
    position: relative;
}
```

---

# 9. `position: absolute` and normal flow

This is another important difference.

### Relative

```css
.box {
    position: relative;
    left: 50px;
}
```

The element **still occupies its original space**.

### Absolute

```css
.box {
    position: absolute;
    left: 50px;
}
```

The element is **removed from normal document flow**.

Think:

```text
relative
→ moves visually
→ original space remains

absolute
→ removed from normal flow
→ other elements behave as if it isn't there
```

---

# 10. `position: fixed` ⭐⭐⭐

`fixed` positions an element relative to the **viewport**.

```css
.box {
    position: fixed;
}
```

For example:

```css
.button {
    position: fixed;
    right: 20px;
    bottom: 20px;
}
```

The button stays at the bottom-right of the screen.

```text
┌─────────────────────────────┐
│                             │
│          Website            │
│                             │
│                             │
│                       [ + ] │
└─────────────────────────────┘
```

Even when you scroll, it can remain in that location.

---

# 11. Real-world example of `fixed`

A floating WhatsApp/contact button:

```css
.contact-button {
    position: fixed;
    right: 20px;
    bottom: 20px;
}
```

Another common example:

```css
.navbar {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
}
```

The navbar stays attached to the viewport while scrolling.

### Important

When using a fixed navbar, the content may go underneath it.

So you often add something like:

```css
body {
    padding-top: 70px;
}
```

depending on the navbar's actual height.

---

# 12. `position: sticky` ⭐⭐⭐

`sticky` is extremely useful for headers and navigation.

```css
.header {
    position: sticky;
    top: 0;
}
```

It behaves somewhat like a normal element initially.

When you scroll and it reaches:

```css
top: 0;
```

it sticks there.

### Think:

```text
Before scrolling:

HEADER
────────────
CONTENT


After scrolling:

HEADER ← sticks here
────────────
CONTENT
CONTENT
CONTENT
```

---

# 13. Sticky vs Fixed

This is a common interview question.

### Fixed

```css
position: fixed;
top: 0;
```

The element is attached to the viewport.

### Sticky

```css
position: sticky;
top: 0;
```

The element behaves normally until it reaches the specified offset, then sticks within its scrolling context.

Simple memory:

```text
fixed
→ always attached to viewport

sticky
→ normal first
→ sticks when scrolling reaches its position
```

---

# 14. `top`, `right`, `bottom`, `left`

These properties control the offset of positioned elements.

Example:

```css
.box {
    position: absolute;
    top: 20px;
    left: 30px;
}
```

Means:

```text
20px from top
30px from left
```

---

## `top`

```css
top: 20px;
```

Moves/offsets the element from the top edge of its containing block.

---

## `right`

```css
right: 20px;
```

Offsets it from the right.

---

## `bottom`

```css
bottom: 20px;
```

Offsets it from the bottom.

---

## `left`

```css
left: 20px;
```

Offsets it from the left.

---

# 15. You can use negative values

For example:

```css
.badge {
    position: absolute;
    top: -10px;
    right: -10px;
}
```

This can place a badge slightly outside the parent's top-right corner.

```text
       [New]
┌─────────────────┐
│                 │
│      CARD       │
│                 │
└─────────────────┘
```

Very common in UI design.

---

# 16. `inset`

CSS also provides a shorthand called `inset`.

Instead of:

```css
.box {
    top: 10px;
    right: 20px;
    bottom: 30px;
    left: 40px;
}
```

You can write:

```css
.box {
    inset: 10px 20px 30px 40px;
}
```

The order is the same as margin/padding:

```text
top
right
bottom
left
```

You don't need to memorize `inset` deeply for beginner interviews, but you should recognize it.

---

# 17. `z-index` ⭐⭐⭐

`z-index` controls which positioned elements appear **in front of or behind each other** when they overlap.

Example:

```css
.box1 {
    position: absolute;
    z-index: 1;
}

.box2 {
    position: absolute;
    z-index: 2;
}
```

`.box2` will generally appear above `.box1` when they're competing in the same stacking context.

Think:

```text
z-index: 3
   ↑
z-index: 2
   ↑
z-index: 1
```

Higher stacking level generally appears in front.

---

# 18. Example of `z-index`

```html
<div class="box red"></div>
<div class="box blue"></div>
```

```css
.box {
    width: 100px;
    height: 100px;
    position: absolute;
}

.red {
    background: red;
    left: 50px;
    top: 50px;
    z-index: 1;
}

.blue {
    background: blue;
    left: 80px;
    top: 80px;
    z-index: 2;
}
```

Because:

```css
.blue {
    z-index: 2;
}
```

the blue box appears above the red box where they overlap.

---

# 19. Important: `z-index` isn't just "bigger number = always on top"

This is a slightly more advanced but useful interview point.

`z-index` works within **stacking contexts**.

So this isn't always enough:

```css
.child {
    z-index: 999999;
}
```

It doesn't guarantee the element will appear above everything on the page.

For beginner/interview level, remember:

> `z-index` controls stacking order, but stacking contexts can affect the result.

---

# 20. `relative` vs `absolute`

Very important comparison:

| `relative`                            | `absolute`                              |
| ------------------------------------- | --------------------------------------- |
| Remains in normal flow                | Removed from normal flow                |
| Original space remains                | Original space does not remain          |
| Can use `top/left/etc.`               | Can use `top/left/etc.`                 |
| Often used as parent reference        | Often used for overlays/badges          |
| Moves relative to its normal position | Positioned relative to containing block |

### Memory:

```text
relative
→ move yourself

absolute
→ position yourself inside a reference
```

---

# 21. `fixed` vs `absolute`

| Absolute                                | Fixed                                |
| --------------------------------------- | ------------------------------------ |
| Positioned relative to containing block | Positioned relative to viewport      |
| Removed from normal flow                | Removed from normal flow             |
| Usually scrolls with page               | Usually stays fixed during scrolling |
| Common for badges/overlays              | Common for floating buttons/navbars  |

---

# 22. `sticky` vs `fixed`

| Sticky                       | Fixed                                |
| ---------------------------- | ------------------------------------ |
| Starts in normal flow        | Not in normal flow                   |
| Sticks after reaching offset | Attached to viewport immediately     |
| Usually requires `top`, etc. | Usually uses `top/right/bottom/left` |
| Useful for section headers   | Useful for fixed navbars/buttons     |

---

# 23. Real Example — Card Badge

HTML:

```html
<div class="card">
    <span class="badge">New</span>

    <h2>React Course</h2>
    <p>Learn React from basics.</p>
</div>
```

CSS:

```css
.card {
    width: 300px;
    padding: 30px;
    background: white;
    border: 1px solid #ddd;
    
    position: relative;
}

.badge {
    position: absolute;
    top: 10px;
    right: 10px;

    background: red;
    color: white;
    padding: 5px 10px;
}
```

This is a **very common real-world use** of positioning.

---

# 24. Real Example — Image Overlay

HTML:

```html
<div class="image-box">
    <img src="image.jpg" alt="Course">
    <div class="overlay">React Course</div>
</div>
```

CSS:

```css
.image-box {
    position: relative;
}

.image-box img {
    width: 100%;
    display: block;
}

.overlay {
    position: absolute;
    bottom: 0;
    left: 0;

    width: 100%;
    padding: 15px;

    background: rgba(0, 0, 0, 0.6);
    color: white;
}
```

Result conceptually:

```text
┌─────────────────────────┐
│                         │
│         IMAGE           │
│                         │
│                         │
├─────────────────────────┤
│    React Course         │ ← absolute
└─────────────────────────┘
```

---

# 25. Real Example — Centering with Absolute

A common technique:

```css
.parent {
    position: relative;
    height: 300px;
}

.child {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```

Why?

First:

```css
top: 50%;
left: 50%;
```

puts the child's **top-left corner** at the center.

Then:

```css
transform: translate(-50%, -50%);
```

moves it back by half of its own width and height.

Result:

```text
┌─────────────────────────┐
│                         │
│                         │
│        CONTENT          │
│                         │
│                         │
└─────────────────────────┘
```

You'll learn `transform` more fully in Topic 14.

---

# 26. Important difference: `position` vs `display`

You learned `display` in Topic 8.

Remember:

```text
display
→ controls layout behavior

position
→ controls positioning
```

For example:

```css
.box {
    display: flex;
    position: relative;
}
```

These two properties can be used together.

`display: flex` controls how the **children are arranged**.

`position: relative` controls how the element itself is positioned and can provide a reference for absolute children.

---

# 27. The most important pattern to memorize

If you remember only one pattern from this topic, remember this:

```css
.parent {
    position: relative;
}

.child {
    position: absolute;
    top: 0;
    right: 0;
}
```

Used for:

* badges
* icons
* image overlays
* close buttons
* notification dots
* card labels
* dropdown decorations
* UI overlays

---

# 28. Position Cheat Sheet

| Position   | Main idea                                                  |
| ---------- | ---------------------------------------------------------- |
| `static`   | Default normal positioning                                 |
| `relative` | Stays in flow, can offset itself                           |
| `absolute` | Removed from flow, positioned relative to containing block |
| `fixed`    | Attached to viewport                                       |
| `sticky`   | Normal until scroll threshold, then sticks                 |

### Offset properties

```text
top
right
bottom
left
```

### Stacking

```text
z-index
```

---

# 29. Interview Questions ⭐

### Q1. What is CSS `position`?

> `position` controls how an element is positioned in the document.

---

### Q2. What is the default position?

> `static`.

---

### Q3. Difference between relative and absolute?

> `relative` keeps the element in normal flow and allows it to be offset from its normal position. `absolute` removes the element from normal flow and positions it relative to its containing block.

---

### Q4. Why do we use `position: relative` on a parent?

> It commonly establishes the parent as the containing block for an absolutely positioned child.

---

### Q5. Does absolute positioning remove an element from normal flow?

> Yes.

---

### Q6. Does relative positioning remove an element from normal flow?

> No. The element keeps its original space.

---

### Q7. What is `position: fixed`?

> It positions an element relative to the viewport, so it can remain in the same screen position while scrolling.

---

### Q8. What is `position: sticky`?

> It behaves normally until a specified offset is reached during scrolling, then sticks within its scrolling context.

---

### Q9. What does `z-index` do?

> It controls the stacking order of overlapping elements within the relevant stacking contexts.

---

### Q10. Can `top`, `left`, `right`, and `bottom` be used with `static`?

> They don't reposition a statically positioned element.

---

# ⭐ Final Memory Trick

```text
STATIC
↓
Normal/default

RELATIVE
↓
Normal + can move
↓
Keeps its space

ABSOLUTE
↓
Removed from flow
↓
Positioned using a containing block

FIXED
↓
Attached to viewport
↓
Stays while scrolling

STICKY
↓
Normal first
↓
Sticks during scrolling
```

And the most important real-world pattern:

```css
.card {
    position: relative;
}

.badge {
    position: absolute;
    top: 10px;
    right: 10px;
}
```
