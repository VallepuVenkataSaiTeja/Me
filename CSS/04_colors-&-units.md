# 4. CSS Colors & Units 🎨📏

Now let's learn **Colors and Units**. These are used in almost every CSS project.

You don't need to memorize every possible color format or CSS unit. For your **frontend + React interview preparation**, focus on the ones you listed.

---

# Part A — CSS Colors 🎨

CSS provides different ways to specify a color.

The most important ones are:

```text
1. Color names
2. HEX
3. RGB
4. RGBA
5. HSL
```

---

# 1. Color Names

The simplest way is to use a predefined color name.

```css
h1 {
    color: red;
}
```

Some common colors:

```css
color: red;
color: blue;
color: green;
color: yellow;
color: orange;
color: purple;
color: pink;
color: black;
color: white;
color: gray;
```

Example:

```html
<h1>Hello World</h1>
```

```css
h1 {
    color: blue;
}
```

The text becomes blue.

---

## Background color

You can also use color names for backgrounds:

```css
body {
    background-color: lightblue;
}
```

Or:

```css
button {
    background-color: red;
    color: white;
}
```

### Limitation

Color names are easy, but there aren't enough names for precise designs.

For example, a designer might give you:

```text
#3498db
```

So you need HEX, RGB, etc.

---

# 2. HEX Colors ⭐⭐⭐

HEX is extremely common in real-world CSS.

HEX means **hexadecimal color**.

Example:

```css
h1 {
    color: #ff0000;
}
```

This represents red.

A HEX color normally looks like:

```text
#RRGGBB
```

Where:

```text
RR → Red
GG → Green
BB → Blue
```

Each pair can range from:

```text
00 → 255
```

---

## Common HEX Colors

```css
#ff0000   /* red */
#00ff00   /* green */
#0000ff   /* blue */
#000000   /* black */
#ffffff   /* white */
```

Let's understand:

```text
#ff0000
││││││
││ ││ │
││ ││ └── Blue = 00
││ └───── Green = 00
└──────── Red = ff
```

So:

```text
#ff0000 → Red
#00ff00 → Green
#0000ff → Blue
```

---

## Shorthand HEX

Some HEX colors can be shortened.

For example:

```css
#ffffff
```

can be written as:

```css
#fff
```

And:

```css
#ff0000
```

can be:

```css
#f00
```

The shorthand works when each pair contains identical characters:

```text
#RRGGBB
 ↓
#RGB
```

Examples:

```css
#ffffff → #fff
#000000 → #000
#ff0000 → #f00
#00ff00 → #0f0
#0000ff → #00f
```

---

# 3. RGB ⭐⭐

RGB means:

**Red + Green + Blue**

Syntax:

```css
rgb(red, green, blue)
```

Each value is generally between:

```text
0 → 255
```

Example:

```css
h1 {
    color: rgb(255, 0, 0);
}
```

This is red.

Why?

```text
Red   = 255
Green = 0
Blue  = 0
```

---

## RGB examples

```css
rgb(255, 0, 0)     /* red */
rgb(0, 255, 0)     /* green */
rgb(0, 0, 255)     /* blue */
rgb(0, 0, 0)       /* black */
rgb(255, 255, 255) /* white */
```

Think:

```text
rgb(R, G, B)
```

---

## Mixing colors

For example:

```css
rgb(255, 255, 0)
```

means:

```text
Red   = 255
Green = 255
Blue  = 0
```

Result:

**Yellow**

Another:

```css
rgb(255, 0, 255)
```

Result:

**Magenta**

---

# 4. RGBA ⭐⭐

RGBA is RGB + **Alpha**.

Alpha controls **transparency/opacity**.

Syntax:

```css
rgba(red, green, blue, alpha)
```

Alpha usually ranges from:

```text
0 → completely transparent
1 → completely opaque
```

Example:

```css
background-color: rgba(0, 0, 0, 0.5);
```

This means:

```text
Black
50% opacity
```

---

## Alpha examples

```css
rgba(255, 0, 0, 1)
```

Fully visible red.

```css
rgba(255, 0, 0, 0.5)
```

50% transparent red.

```css
rgba(255, 0, 0, 0)
```

Completely transparent red.

---

## Where is RGBA useful?

Very useful for:

### Overlays

```css
.hero {
    background-color: rgba(0, 0, 0, 0.6);
}
```

### Shadows

```css
box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
```

### Transparent backgrounds

```css
.card {
    background-color: rgba(255, 255, 255, 0.8);
}
```

You'll see this frequently in frontend projects.

---

# 5. HSL ⭐⭐

HSL means:

```text
H → Hue
S → Saturation
L → Lightness
```

Syntax:

```css
hsl(hue, saturation, lightness)
```

Example:

```css
h1 {
    color: hsl(0, 100%, 50%);
}
```

This is red.

---

## H — Hue

Hue represents the actual color.

It uses degrees:

```text
0°   → Red
120° → Green
240° → Blue
```

Think of it as a color wheel.

```text
        0° Red
          ↑
          |
240° -----+----- 120°
Blue              Green
```

---

## S — Saturation

Saturation controls how intense the color is.

```text
0%   → no color / gray
100% → fully saturated
```

Example:

```css
hsl(0, 100%, 50%);
```

Fully saturated red.

---

## L — Lightness

Lightness controls how light or dark the color is.

```text
0%   → black
50%  → normal color
100% → white
```

Example:

```css
hsl(0, 100%, 50%);
```

Red.

```css
hsl(0, 100%, 25%);
```

Darker red.

```css
hsl(0, 100%, 75%);
```

Lighter red.

---

# HEX vs RGB vs HSL

You don't need to memorize complicated conversions.

Just understand what each is good at.

| Format     | Example           | Main idea                |
| ---------- | ----------------- | ------------------------ |
| Color name | `red`             | Simple predefined color  |
| HEX        | `#ff0000`         | Very common in designs   |
| RGB        | `rgb(255,0,0)`    | Red/Green/Blue values    |
| RGBA       | `rgba(0,0,0,.5)`  | RGB + transparency       |
| HSL        | `hsl(0,100%,50%)` | Hue/Saturation/Lightness |

### For frontend work:

**HEX + RGB/RGBA + basic HSL** is enough.

---

# Part B — CSS Units 📏

Units tell CSS **how large something should be**.

For example:

```css
p {
    font-size: 20px;
}
```

Here:

```text
20 → number
px → unit
```

The important units for you are:

```text
px
%
rem
em
vw
vh
```

---

# 1. `px` ⭐⭐⭐

`px` means **pixels**.

Example:

```css
h1 {
    font-size: 40px;
}

.box {
    width: 300px;
    height: 200px;
}
```

You're explicitly specifying a size.

```text
300px → 300 CSS pixels
```

### Good for:

* Borders
* Small fixed sizes
* Icons
* Precise dimensions
* Some spacing

Example:

```css
button {
    border: 1px solid black;
}
```

---

# 2. `%` ⭐⭐⭐

`%` is a **relative unit**.

It is generally calculated relative to the relevant parent/container dimension or property context.

Example:

```html
<div class="parent">
    <div class="child"></div>
</div>
```

```css
.parent {
    width: 1000px;
}

.child {
    width: 50%;
}
```

The child becomes:

```text
50% of 1000px = 500px
```

So:

```text
Parent → 1000px
Child  → 50% = 500px
```

---

## Common use

```css
.container {
    width: 80%;
}
```

This allows the container to adjust with its containing block.

Very useful for responsive websites.

---

# 3. `rem` ⭐⭐⭐

`rem` means:

**Root EM**

It is relative to the **root (`html`) font size**.

Typically browsers start with:

```css
html {
    font-size: 16px;
}
```

Therefore:

```text
1rem = 16px
```

Example:

```css
p {
    font-size: 1rem;
}
```

Usually:

```text
1rem = 16px
```

---

## More examples

Assuming root font size is 16px:

```text
1rem   = 16px
2rem   = 32px
1.5rem = 24px
0.5rem = 8px
```

Example:

```css
h1 {
    font-size: 2rem;
}
```

Usually:

```text
2 × 16px = 32px
```

---

## Why is `rem` useful?

It's very useful for:

* Font sizes
* Padding
* Margin
* Consistent spacing

Example:

```css
.card {
    padding: 1.5rem;
    margin: 2rem;
}
```

If the root font size changes, the sizes scale accordingly.

For modern responsive/accessibility-friendly CSS, **`rem` is very useful**.

---

# 4. `em` ⭐⭐

`em` is also a relative unit, but its behavior depends on the **font size of the relevant element/parent context**.

This is where beginners often get confused.

Consider:

```css
.parent {
    font-size: 20px;
}

.child {
    font-size: 2em;
}
```

The child's font size is:

```text
2 × 20px = 40px
```

So:

```text
Parent font-size → 20px
Child 2em       → 40px
```

---

# `em` vs `rem` ⭐⭐⭐

This is an important interview question.

### `rem`

Relative to the **root (`html`) font size**.

### `em`

Relative to the **relevant font-size context**, often the parent when setting a child's font size.

Example:

```css
html {
    font-size: 16px;
}

.parent {
    font-size: 20px;
}

.child {
    font-size: 2em;
}
```

The child:

```text
2em = 2 × 20px = 40px
```

But:

```css
.child {
    font-size: 2rem;
}
```

means:

```text
2rem = 2 × 16px = 32px
```

So:

```text
em  → based on local font-size context
rem → based on root font-size
```

### Simple memory trick:

```text
em  → element/local context
rem → root
```

---

# 5. `vw` ⭐⭐⭐

`vw` means:

**Viewport Width**

`1vw` = **1% of the viewport's width**.

The viewport is basically the visible browser area.

If viewport width is:

```text
1000px
```

Then:

```text
1vw = 10px
```

Therefore:

```text
50vw = 500px
```

Example:

```css
.box {
    width: 50vw;
}
```

The width is 50% of the viewport width.

---

## Example

If your browser width is:

```text
1200px
```

Then:

```text
1vw  = 12px
50vw = 600px
100vw = 1200px
```

---

# 6. `vh` ⭐⭐⭐

`vh` means:

**Viewport Height**

`1vh` = **1% of the viewport's height**.

If viewport height is:

```text
800px
```

Then:

```text
1vh = 8px
```

Therefore:

```text
50vh = 400px
100vh = 800px
```

Example:

```css
.hero {
    height: 100vh;
}
```

This makes the hero approximately the height of the viewport.

---

# `vw` vs `vh`

Very simple:

```text
vw → viewport width
vh → viewport height
```

Example:

```css
.box {
    width: 50vw;
    height: 50vh;
}
```

Meaning:

```text
Width  → 50% of viewport width
Height → 50% of viewport height
```

---

# 7. Comparing All Six Units

Let's assume:

```text
Viewport:
Width  = 1200px
Height = 800px

Root font-size:
16px
```

Then:

| Unit  | Example | Approximate meaning                  |
| ----- | ------: | ------------------------------------ |
| `px`  |  `20px` | 20 CSS pixels                        |
| `%`   |   `50%` | 50% of relevant containing dimension |
| `rem` |  `2rem` | 32px                                 |
| `em`  |   `2em` | 2 × relevant font-size context       |
| `vw`  |  `50vw` | 600px                                |
| `vh`  |  `50vh` | 400px                                |

---

# 8. Real-World Example

Let's build a simple responsive hero:

```html
<section class="hero">
    <h1>Welcome to Inskill</h1>
    <p>Learn. Build. Grow.</p>
</section>
```

CSS:

```css
.hero {
    width: 100%;
    min-height: 70vh;
    padding: 3rem;
    text-align: center;
}

.hero h1 {
    font-size: 3rem;
}

.hero p {
    font-size: 1.2rem;
}
```

Here we're combining different units:

```text
100% → width
70vh → viewport-based height
3rem → spacing
3rem → heading size
1.2rem → paragraph size
```

This is much closer to how you'll actually write CSS in projects.

---

# 9. Which Units Should You Actually Use?

Don't worry about using every unit everywhere.

For your frontend development, a good starting approach is:

### `px`

Use for things like:

```css
border: 1px solid black;
```

and small fixed dimensions where appropriate.

### `%`

Use for:

```css
width: 100%;
```

and container-based responsive sizing.

### `rem`

Use heavily for:

```css
font-size
padding
margin
gap
```

### `em`

Understand it well, but don't force yourself to use it everywhere.

### `vw`

Useful for:

```text
viewport-based widths
responsive typography/layouts
```

### `vh`

Useful for:

```text
hero sections
full-screen sections
viewport-based layouts
```

---

# ⭐ Interview Questions You Should Know

### 1. What is the difference between `px` and `%`?

`px` is a fixed CSS length unit, while `%` is relative to the relevant containing/property context.

---

### 2. What is `rem`?

`rem` is relative to the font size of the root `<html>` element.

---

### 3. What is `em`?

`em` is a relative unit based on the relevant font-size context; when used for an element's font size, it is based on the inherited/parent font size.

---

### 4. Difference between `em` and `rem`?

```text
em  → local/element font-size context
rem → root html font-size
```

---

### 5. What is `vw`?

`vw` represents 1% of the viewport width.

```text
100vw = viewport width
```

---

### 6. What is `vh`?

`vh` represents 1% of the viewport height.

```text
100vh = viewport height
```

---

### 7. What is HEX?

HEX is a hexadecimal representation of color, commonly written as:

```text
#RRGGBB
```

---

### 8. Difference between RGB and RGBA?

```text
RGB  → Red + Green + Blue
RGBA → Red + Green + Blue + Alpha
```

Alpha controls transparency.

---

# 🎯 What You Should Master

For your CSS interview preparation, remember these:

```text
COLORS
│
├── Color names
├── HEX ⭐⭐⭐
├── RGB ⭐⭐
├── RGBA ⭐⭐
└── HSL ⭐

UNITS
│
├── px  ⭐⭐⭐
├── %   ⭐⭐⭐
├── rem ⭐⭐⭐
├── em  ⭐⭐
├── vw  ⭐⭐⭐
└── vh  ⭐⭐⭐
```

The **most important distinction** to understand before moving on is:

```text
px  → fixed length
%   → relative to containing context
rem → relative to root font size
em  → relative to local font-size context
vw  → relative to viewport width
vh  → relative to viewport height
```