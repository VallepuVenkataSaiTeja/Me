# 17. CSS DevTools & Debugging ⭐⭐

This is the **last major topic in your CSS roadmap**, and it is very important for interviews and real-world development.

You may know CSS properties very well, but in real projects you will often face problems like:

* "Why is my CSS not working?"
* "Why is this element not centered?"
* "Why is my margin not applying?"
* "Why is my color being overridden?"
* "Why is `z-index` not working?"
* "Why does it look good on desktop but break on mobile?"
* "Which CSS rule is actually being applied?"

**Chrome DevTools** helps you answer these questions.

---

# 1. What is CSS DevTools?

**DevTools (Developer Tools)** is a set of browser tools that lets you inspect and debug HTML, CSS, JavaScript, network requests, etc.

In Chrome:

```text
Right click → Inspect
```

or:

```text
F12
```

or:

```text
Ctrl + Shift + I
```

On Mac:

```text
Cmd + Option + I
```

You will see something like:

```text
┌─────────────────────────────────────────────┐
│                 Web Page                    │
├─────────────────────────────────────────────┤
│                                             │
│              Your Website                  │
│                                             │
├─────────────────────────────────────────────┤
│ Elements | Console | Sources | Network ...  │
│                                             │
│ HTML / CSS / Box Model / Computed           │
└─────────────────────────────────────────────┘
```

---

# 2. Why is DevTools important?

Suppose you write:

```css
.box {
    color: red;
}
```

But the text is still blue.

Instead of randomly changing CSS, you can inspect the element and immediately see:

* which CSS rule is applied
* which rule is overridden
* which stylesheet contains the rule
* whether the property is inherited
* the actual computed value
* the element's dimensions
* margin/padding/border
* layout information

This makes debugging much faster.

---

# 3. The Elements Tab

The **Elements** tab is probably the most important DevTools section for CSS.

Example HTML:

```html
<div class="card">
    <h2>Hello</h2>
    <p>Welcome to my website</p>
</div>
```

Inspect the `.card`.

DevTools will show something similar to:

```html
<div class="card">
    <h2>Hello</h2>
    <p>Welcome to my website</p>
</div>
```

And on the right you will see CSS.

```css
.card {
    width: 300px;
    padding: 20px;
    background: white;
}
```

You can **temporarily modify the CSS directly inside DevTools**.

For example:

```css
.card {
    width: 500px;
}
```

The webpage immediately changes.

### Important

These changes are normally **temporary**.

If you refresh the page, your changes disappear unless you save them through appropriate DevTools workflows.

---

# 4. Inspect Element

One of the most common debugging techniques:

### Step 1

Right-click an element.

```text
Right click → Inspect
```

### Step 2

DevTools selects that HTML element.

### Step 3

Look at the CSS rules.

For example:

```html
<button class="login-btn">
    Login
</button>
```

You can inspect it and see:

```css
.login-btn {
    background: blue;
    color: white;
    padding: 10px 20px;
}
```

This is useful for understanding exactly what is happening.

---

# 5. Styles Tab

The **Styles** panel shows the CSS rules affecting the selected element.

Example:

```css
.card {
    padding: 20px;
    color: red;
}
```

You might see:

```text
element.style

.card
    padding: 20px
    color: red

body
    color: black
```

You can modify values directly.

For example:

```css
padding: 20px;
```

Change to:

```css
padding: 50px;
```

The browser updates immediately.

---

# 6. Overridden CSS

This is one of the **most important things to understand**.

Suppose you have:

```css
p {
    color: red;
}
```

Later:

```css
p {
    color: blue;
}
```

The second rule wins because both selectors have the same specificity and the second rule comes later.

DevTools might show:

```text
p {
    color: red;   ❌ crossed out
}

p {
    color: blue;  ✅ active
}
```

The crossed-out property means:

> This CSS declaration exists, but it is not currently winning.

---

# 7. Example of Specificity Debugging

HTML:

```html
<p class="text">Hello</p>
```

CSS:

```css
p {
    color: red;
}

.text {
    color: blue;
}
```

What color will the text be?

```text
Blue
```

Why?

Because:

```text
p
↓
element selector
```

has lower specificity than:

```text
.text
↓
class selector
```

DevTools helps you see this immediately.

---

# 8. `element.style`

DevTools allows you to add inline styles.

Suppose:

```html
<div class="box">
    Hello
</div>
```

You can add:

```css
element.style {
    color: red;
}
```

This effectively behaves like:

```html
<div class="box" style="color: red;">
    Hello
</div>
```

It is useful for testing.

For example, if you aren't sure whether changing:

```css
margin-top: 50px;
```

will fix your layout, you can test it directly in DevTools.

---

# 9. Computed Tab

The **Computed** panel shows the final CSS values actually being used by the browser.

This is extremely useful.

Suppose you have:

```css
.box {
    width: 50%;
}
```

The computed value might be something like:

```text
width: 450px
```

because the parent has a certain width.

You can search the Computed panel for properties such as:

```text
display
width
height
margin
padding
position
color
font-size
```

---

# 10. Styles vs Computed

This is an important interview question.

### Styles

Shows:

> CSS rules that are affecting the element.

### Computed

Shows:

> The final calculated values being used by the browser.

Think:

```text
Styles
   ↓
"What CSS rules exist?"

Computed
   ↓
"What value is actually being used?"
```

---

# 11. Box Model in DevTools ⭐⭐⭐

This is one of the most useful features.

When you inspect an element, DevTools usually shows its box model.

Conceptually:

```text
              MARGIN
    ┌──────────────────────────┐
    │          BORDER          │
    │   ┌──────────────────┐   │
    │   │     PADDING      │   │
    │   │  ┌────────────┐  │   │
    │   │  │  CONTENT   │  │   │
    │   │  └────────────┘  │   │
    │   └──────────────────┘   │
    └──────────────────────────┘
```

You can see values like:

```text
margin: 20px
border: 2px
padding: 15px
width: 300px
height: 100px
```

This is extremely useful when an element appears:

> "Too big"

or

> "Too far away"

or

> "Not aligned properly."

---

# 12. Debugging Margin and Padding

Suppose you have:

```css
.card {
    padding: 20px;
    margin: 50px;
}
```

But you don't understand why the card is positioned so far away.

Inspect it.

DevTools will visually highlight:

```text
margin
padding
border
content
```

Usually different colors are used by the browser to make each area easy to identify.

This lets you immediately understand where the extra space comes from.

---

# 13. Check Element Dimensions

DevTools can show an element's dimensions.

For example:

```text
width: 300px
height: 200px
```

This helps answer questions like:

> Why is my button wider than expected?

> Why is my image overflowing?

> Why does my container have extra width?

---

# 14. Debugging `width: 100%`

A very common problem:

```css
.box {
    width: 100%;
    padding: 20px;
}
```

Depending on `box-sizing`, the element may become wider than expected.

Using:

```css
* {
    box-sizing: border-box;
}
```

often makes sizing easier.

DevTools lets you inspect the actual dimensions and box model.

---

# 15. Debugging Flexbox

Suppose:

```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

But the elements aren't behaving as expected.

Inspect the container.

DevTools can identify:

```text
display: flex
flex-direction
justify-content
align-items
gap
flex-wrap
```

Modern browsers also provide visual Flexbox controls/overlays.

You can use them to understand:

```text
Main axis
Cross axis
Flex items
Spacing
Alignment
```

---

# 16. Example: Flexbox Debugging

HTML:

```html
<div class="container">
    <div>One</div>
    <div>Two</div>
    <div>Three</div>
</div>
```

CSS:

```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

If something isn't centered, inspect `.container`.

Check:

```text
display
justify-content
align-items
height
width
flex-direction
```

You might discover:

```css
.container {
    height: 50px;
}
```

when you expected:

```css
.container {
    height: 300px;
}
```

The problem wasn't necessarily `align-items`; it could be the container's height.

---

# 17. Debugging Grid

DevTools can also help with CSS Grid.

Example:

```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
}
```

Inspect the container.

You can see the grid structure and, in supported browsers, enable a **Grid overlay**.

This helps visualize:

```text
Column 1 | Column 2 | Column 3
---------|----------|---------
   1     |    2     |    3
---------|----------|---------
   4     |    5     |    6
```

Very useful when debugging:

```css
grid-template-columns
grid-template-rows
gap
grid-column
grid-row
```

---

# 18. Responsive Device Mode ⭐⭐⭐

This is extremely important for responsive websites.

In Chrome DevTools:

```text
Toggle device toolbar
```

Shortcut:

```text
Ctrl + Shift + M
```

You can simulate different screen sizes.

For example:

```text
Mobile
Tablet
Laptop
Desktop
```

You might see:

```text
375 × 667
768 × 1024
1024 × 768
1440 × 900
```

This allows you to test responsive CSS.

---

# 19. Why Responsive Debugging Matters

Suppose your desktop website looks perfect:

```text
Desktop
┌───────────────────────────────┐
│ Logo Home About Contact       │
│                               │
│ Card  Card  Card              │
└───────────────────────────────┘
```

But mobile looks like:

```text
Mobile
┌──────────────┐
│ Logo Home... │ → overflow
│              │
│ Card Card    │ → too wide
│              │
└──────────────┘
```

DevTools allows you to switch to mobile dimensions and identify the problem.

---

# 20. Testing Media Queries

Suppose:

```css
@media (max-width: 768px) {
    .container {
        flex-direction: column;
    }
}
```

Resize the browser or use device mode.

At:

```text
> 768px
```

the desktop style applies.

At:

```text
≤ 768px
```

the media query applies.

DevTools helps you see which media-query rules are currently active.

---

# 21. Debugging `display: none`

Suppose an element disappeared.

HTML:

```html
<div class="menu">
    Menu
</div>
```

CSS:

```css
.menu {
    display: none;
}
```

Inspect the element.

You will immediately see:

```css
display: none;
```

This tells you why it isn't visible.

---

# 22. Debugging `visibility: hidden`

Another possibility:

```css
.menu {
    visibility: hidden;
}
```

The element still occupies space but isn't visible.

DevTools helps identify this difference.

### Remember:

```css
display: none;
```

→ removed from layout.

```css
visibility: hidden;
```

→ invisible but still occupies space.

---

# 23. Debugging `opacity`

Maybe you have:

```css
.box {
    opacity: 0;
}
```

The element exists but is completely transparent.

DevTools makes this easy to find.

---

# 24. Debugging `z-index` ⭐⭐⭐

A very common issue:

> "I set `z-index: 9999`, but my element is still behind another element."

Inspect both elements.

Check:

```css
position
z-index
```

Remember:

```css
z-index
```

doesn't work in every situation the way beginners expect.

It interacts with **stacking contexts**.

For basic debugging, first check:

```css
position: relative;
```

or:

```css
position: absolute;
```

or:

```css
position: fixed;
```

and then inspect the relevant stacking context.

---

# 25. Debugging `position: absolute`

Suppose:

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

If `.child` appears in the wrong location, inspect `.child`.

Then check its parent.

The important question is:

> Which element is acting as the containing block?

Usually, an absolutely positioned element is positioned relative to an appropriate positioned ancestor.

---

# 26. Debugging Inheritance

Suppose:

```css
body {
    color: blue;
}
```

and:

```html
<div>
    <p>Hello</p>
</div>
```

The `<p>` may inherit the color.

In DevTools you can see inherited styles.

This helps when you wonder:

> "Where did this color/font come from?"

---

# 27. Debugging Fonts

Suppose you wrote:

```css
body {
    font-family: Arial;
}
```

but your text looks different.

Inspect the element.

Check:

```text
font-family
font-size
font-weight
line-height
```

The Computed panel can help identify the final values.

---

# 28. Debugging `overflow`

Very common problem:

```text
Website has horizontal scrolling
```

You can inspect the page and look for elements that are wider than the viewport.

Common causes:

```css
width: 100vw;
```

large fixed widths:

```css
width: 1000px;
```

long unbroken text:

```text
ThisIsAVeryLongTextWithoutSpaces...
```

or negative/large positioning.

DevTools helps identify the element causing overflow.

---

# 29. Debugging Images

Suppose an image is too large.

```css
img {
    width: 100%;
}
```

You can inspect:

```text
width
height
max-width
object-fit
```

A common responsive pattern is:

```css
img {
    max-width: 100%;
    height: auto;
}
```

---

# 30. Force `:hover`, `:focus`, etc.

This is a very useful DevTools feature.

Suppose:

```css
button:hover {
    background: red;
}
```

Normally you need to move your mouse over the button.

DevTools allows you to force states such as:

```text
:hover
:active
:focus
:visited
```

This is useful when debugging hover styles.

---

# 31. Example: Debugging Hover

CSS:

```css
button {
    background: blue;
}

button:hover {
    background: red;
}
```

If hover isn't working:

1. Inspect button.
2. Open element states.
3. Force `:hover`.
4. Check the Styles panel.

You can see whether:

```css
button:hover
```

is being applied.

---

# 32. Debugging `:focus`

Forms often use:

```css
input:focus {
    border-color: blue;
}
```

If it isn't working:

Inspect the input and force/check:

```text
:focus
```

Then inspect the CSS rule.

---

# 33. Finding the CSS File

Suppose DevTools shows:

```css
.card {
    padding: 20px;
}
```

You can often click the source reference.

It may take you to:

```text
style.css:45
```

Meaning:

```text
style.css
Line 45
```

This is very useful for large projects.

---

# 34. Disabled CSS

You can temporarily disable a CSS property by clicking its checkbox.

For example:

```css
.card {
    width: 300px;
    padding: 20px;
    margin: 30px;
}
```

Disable:

```css
padding: 20px;
```

and see what changes.

This helps determine:

> Is padding causing my layout problem?

You can test properties one by one.

---

# 35. Add CSS Directly in DevTools

You can also test new CSS.

For example:

```css
border: 2px solid red;
```

This is a great debugging trick.

If you don't know where an element actually is:

```css
outline: 2px solid red;
```

This makes it easy to see.

---

# 36. `outline` for Debugging

One of my favorite simple debugging tricks:

```css
* {
    outline: 1px solid red;
}
```

This visually shows all elements.

Example:

```text
┌──────────────────────────────┐
│ body                         │
│ ┌──────────────────────────┐ │
│ │ header                   │ │
│ └──────────────────────────┘ │
│ ┌──────────────────────────┐ │
│ │ main                     │ │
│ │ ┌──────┐ ┌──────┐       │ │
│ │ │ card │ │ card │       │ │
│ │ └──────┘ └──────┘       │ │
│ └──────────────────────────┘ │
└──────────────────────────────┘
```

It can quickly reveal:

* unexpected margins
* unexpected widths
* overflowing elements
* incorrect containers

Don't leave this debugging rule in production.

---

# 37. Debugging a CSS Problem — Proper Workflow ⭐⭐⭐

This is the workflow I recommend remembering for interviews and real projects.

### Step 1 — Inspect the element

```text
Right click → Inspect
```

### Step 2 — Check the HTML

Make sure you selected the correct element.

### Step 3 — Check Styles

Look for:

```text
Applied rules
Overridden rules
Inherited rules
```

### Step 4 — Check Computed

Find the final value.

### Step 5 — Check Box Model

Look at:

```text
width
height
padding
border
margin
```

### Step 6 — Check layout

For Flexbox:

```text
display
flex-direction
justify-content
align-items
gap
```

For Grid:

```text
grid-template-columns
grid-template-rows
gap
```

### Step 7 — Check positioning

Look at:

```text
position
top
right
bottom
left
z-index
```

### Step 8 — Test responsive sizes

Use:

```text
Device Toolbar
```

### Step 9 — Temporarily modify CSS

Try:

```css
border: 2px solid red;
```

or change:

```css
width
margin
padding
display
position
```

### Step 10 — Apply the fix to your actual CSS file

Remember that DevTools changes are primarily for testing.

---

# 38. Example: Debugging a Centering Problem

Suppose:

```html
<div class="container">
    <div class="box">
        Hello
    </div>
</div>
```

CSS:

```css
.container {
    display: flex;
    justify-content: center;
}

.box {
    width: 200px;
}
```

You expected the box to be vertically and horizontally centered.

But it isn't.

Inspect `.container`.

You discover:

```css
.container {
    display: flex;
    justify-content: center;
}
```

There is no:

```css
align-items: center;
```

So you add:

```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

But there is another issue.

The container needs height:

```css
.container {
    min-height: 100vh;
}
```

Final:

```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
}
```

This is exactly the type of problem DevTools helps you solve.

---

# 39. Example: Why is My Color Not Working?

HTML:

```html
<p class="text">Hello</p>
```

CSS:

```css
p {
    color: red;
}

.text {
    color: blue;
}
```

You expect red but get blue.

Inspect the element.

DevTools shows:

```css
p {
    color: red;   ❌
}

.text {
    color: blue;  ✅
}
```

Now you immediately know:

```text
Class specificity > element specificity
```

No guessing required.

---

# 40. Example: Why is My Margin Not Working?

Suppose:

```css
h1 {
    margin-top: 50px;
}
```

But visually nothing seems to change.

Inspect the element.

Check:

```text
margin
```

Then check:

* Is another rule overriding it?
* Is the element inline?
* Is margin collapsing involved?
* Is the parent layout affecting it?
* Is another element covering the visual effect?
* Is the value actually applied?

DevTools helps you investigate instead of guessing.

---

# 41. Example: Mobile Overflow

Suppose mobile has horizontal scrolling.

Use:

```text
Ctrl + Shift + M
```

Switch to a mobile width.

Inspect suspicious elements.

Look for:

```css
width: 1000px;
```

or:

```css
width: 100vw;
```

or:

```css
margin-left: 200px;
```

or:

```css
position: absolute;
```

or large fixed padding.

Then inspect the Box Model.

You can identify the element causing the overflow.

---

# 42. Console Tab

The **Console** is primarily used for JavaScript debugging, but it is still useful when working with frontend applications.

For example:

```js
console.log("Hello");
```

You will see:

```text
Hello
```

If there is a JavaScript error:

```text
Uncaught ReferenceError
```

the Console can help identify it.

For CSS-only debugging, **Elements + Styles + Computed + Box Model** are generally more important.

---

# 43. Sources Tab

The **Sources** tab lets you inspect source files loaded by the website.

You can find things such as:

```text
HTML
CSS
JavaScript
images
```

For beginner CSS debugging, you don't need to master Sources.

Just understand:

> It helps you locate and inspect the files that make up your webpage.

---

# 44. Network Tab

The **Network** tab is also extremely useful in real projects.

It helps you see things like:

```text
CSS files
JS files
Images
Fonts
API requests
```

For example, if your CSS isn't loading, Network can help determine whether:

```text
style.css
```

was successfully loaded.

This can reveal problems like:

```text
404 Not Found
```

---

# 45. Common CSS Problems and What to Check

| Problem                    | Check                                       |
| -------------------------- | ------------------------------------------- |
| Color not working          | Specificity / overridden styles             |
| Margin not working         | Box model / display / margin collapse       |
| Padding not working        | Box model / overridden rule                 |
| Element not visible        | `display`, `visibility`, `opacity`          |
| Element behind another     | `position`, `z-index`, stacking context     |
| Flex not working           | `display: flex`, parent dimensions          |
| Grid not working           | `display: grid`, columns/rows               |
| Element not centered       | Flex/Grid/alignment/container size          |
| Mobile overflow            | Fixed widths / padding / positioning        |
| Hover not working          | `:hover`, specificity                       |
| Font wrong                 | `font-family`, inheritance, computed styles |
| Width unexpected           | `box-sizing`, padding, border               |
| Absolute element misplaced | Positioned ancestor                         |
| CSS file not working       | File path / Network tab                     |
| Media query not working    | Viewport width / selector / order           |

---

# 46. Very Important: CSS Debugging Mindset

When CSS doesn't work, **don't randomly change values**.

Instead ask:

### Question 1

**Is the CSS rule being applied?**

Check Styles.

### Question 2

**Is another rule overriding it?**

Look for crossed-out properties.

### Question 3

**What is the final value?**

Check Computed.

### Question 4

**What is the element's size?**

Check Box Model.

### Question 5

**Is the parent affecting it?**

Check parent layout.

### Question 6

**Is responsive CSS changing it?**

Check media queries/device mode.

This mindset is more important than memorizing DevTools buttons.

---

# 47. DevTools Interview Questions

### Q1. What is Chrome DevTools?

**Answer:**

Chrome DevTools is a set of browser tools used to inspect, test, and debug HTML, CSS, JavaScript, network requests, and webpage performance.

---

### Q2. How do you inspect an HTML element?

**Answer:**

Right-click the element and select **Inspect**, or open DevTools using `F12` / `Ctrl + Shift + I`.

---

### Q3. How do you find why a CSS property isn't working?

**Answer:**

I inspect the element, check the Styles panel for applied and overridden rules, check specificity and inheritance, and then use the Computed panel to verify the final value.

---

### Q4. What does a crossed-out CSS property mean?

**Answer:**

It means that the declaration exists but is currently overridden by another CSS rule or is otherwise not the winning declaration.

---

### Q5. What is the difference between Styles and Computed?

**Answer:**

**Styles** shows CSS rules affecting the element, while **Computed** shows the final calculated values actually used by the browser.

---

### Q6. How do you debug responsive design?

**Answer:**

I use the browser's Device Toolbar to test different viewport sizes and inspect which media queries and CSS rules are being applied.

---

### Q7. How do you debug Flexbox?

**Answer:**

I inspect the flex container and check `display`, `flex-direction`, `justify-content`, `align-items`, `gap`, `flex-wrap`, and the container's dimensions.

---

### Q8. How do you debug `z-index`?

**Answer:**

I inspect the elements involved and check their `position`, `z-index`, and stacking contexts.

---

### Q9. How do you find what is causing horizontal scrolling?

**Answer:**

I use responsive/device mode, inspect elements that extend beyond the viewport, and check their width, margin, padding, positioning, and overflow.

---

### Q10. Can you modify CSS using DevTools?

**Answer:**

Yes. You can temporarily change CSS properties, add new properties, disable declarations, and test different values directly in DevTools.

---

# 48. Most Important DevTools Features to Remember

For a CSS interview, focus on these:

```text
1. Inspect Element
        ↓
2. Styles
        ↓
3. Computed
        ↓
4. Box Model
        ↓
5. Flexbox debugging
        ↓
6. Grid debugging
        ↓
7. Responsive Device Mode
        ↓
8. :hover / :focus states
        ↓
9. Overridden CSS
        ↓
10. Console / Network basics
```

---

# 49. Your CSS Interview Cheat Sheet

You can remember this simple debugging formula:

```text
CSS not working?
       ↓
Inspect Element
       ↓
Check Styles
       ↓
Check overridden rules
       ↓
Check specificity
       ↓
Check inheritance
       ↓
Check Computed
       ↓
Check Box Model
       ↓
Check Parent
       ↓
Check Flex/Grid
       ↓
Check Position/Z-index
       ↓
Check Responsive rules
```

### DevTools shortcuts

| Action          | Shortcut              |
| --------------- | --------------------- |
| Open DevTools   | `F12`                 |
| Open DevTools   | `Ctrl + Shift + I`    |
| Device Toolbar  | `Ctrl + Shift + M`    |
| Inspect element | Right-click → Inspect |

---

# 50. CSS Roadmap Complete 🎯

You have now covered the complete CSS roadmap:

```text
1.  CSS Basics
2.  Selectors
3.  Cascade + Inheritance + Specificity
4.  Colors + Units
5.  Box Model ⭐⭐⭐
6.  Typography & Text
7.  Backgrounds & Borders
8.  Display ⭐⭐
9.  Position ⭐⭐⭐
10. Flexbox ⭐⭐⭐
11. Grid ⭐⭐
12. Responsive Design ⭐⭐⭐
13. Pseudo-classes + Pseudo-elements ⭐⭐
14. Transform + Transition + Animation
15. CSS Variables ⭐⭐
16. calc() + min() + max() + clamp() ⭐⭐
17. DevTools + CSS Debugging ⭐⭐
```

### The highest-priority interview topics

If you are short on revision time, prioritize:

```text
⭐⭐⭐ Box Model
⭐⭐⭐ Position
⭐⭐⭐ Flexbox
⭐⭐⭐ Responsive Design

⭐⭐ Grid
⭐⭐ Pseudo-classes
⭐⭐ CSS Variables
⭐⭐ calc/min/max/clamp
⭐⭐ DevTools
```

And especially make sure you can **write these from memory**, not just explain them:

```css
display: flex;

justify-content: center;
align-items: center;

position: relative;
position: absolute;

display: grid;
grid-template-columns: repeat(3, 1fr);

@media (max-width: 768px) {
    /* responsive CSS */
}

:root {
    --primary-color: blue;
}

width: min(90%, 1200px);

font-size: clamp(24px, 5vw, 60px);
```
