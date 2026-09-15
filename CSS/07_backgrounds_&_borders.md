# 7. CSS Backgrounds & Borders ⭐⭐⭐

These properties are used constantly when building real websites.

They help you create:

* Cards
* Buttons
* Hero sections
* Navigation bars
* Image banners
* Rounded containers
* Shadows
* Modern UI designs

We'll cover:

```text
background-color
background-image
background-size
background-position
background-repeat
border
border-radius
box-shadow
```

---

# 1. `background-color`

`background-color` sets the **background color of an element**.

Example:

```css
.box {
    background-color: lightblue;
}
```

HTML:

```html
<div class="box">
    Hello World
</div>
```

The entire box gets a light-blue background.

You can use any CSS color format:

```css
.box {
    background-color: red;
}
```

```css
.box {
    background-color: #3498db;
}
```

```css
.box {
    background-color: rgb(52, 152, 219);
}
```

```css
.box {
    background-color: rgba(52, 152, 219, 0.5);
}
```

---

## Transparent background

You can use:

```css
background-color: transparent;
```

This means the element doesn't have its own background color.

---

# 2. `background-image`

`background-image` places an image **behind the content of an element**.

Example:

```css
.hero {
    background-image: url("hero.jpg");
}
```

HTML:

```html
<section class="hero">
    <h1>Welcome</h1>
</section>
```

The image becomes the background of the section.

---

## File path

If your image is in:

```text
project/
│
├── index.html
├── style.css
│
└── images/
    └── hero.jpg
```

Then from `style.css`:

```css
.hero {
    background-image: url("images/hero.jpg");
}
```

The path is relative to the CSS file.

---

# 3. Background Image vs `<img>` ⭐

This is an important practical distinction.

### `<img>`

```html
<img src="photo.jpg" alt="Student">
```

Use `<img>` when the image is **actual content**.

For example:

* Product image
* Profile photo
* Student photo
* News article image

### `background-image`

```css
.hero {
    background-image: url("hero.jpg");
}
```

Use a background image when the image is primarily **part of the visual design/background**.

For example:

* Hero banner
* Decorative background
* Section background

Easy memory:

```text
<img>             → content image
background-image  → design/background image
```

---

# 4. `background-size` ⭐⭐⭐

This controls **how the background image fits inside the element**.

The two most important values are:

```text
cover
contain
```

---

## `background-size: cover`

```css
.hero {
    background-size: cover;
}
```

`cover` means:

> Make the image large enough to completely cover the element.

The image may be **cropped**.

Example:

```text
Element:

┌──────────────────────────────┐
│                              │
│       BACKGROUND IMAGE       │
│                              │
└──────────────────────────────┘
```

If the image's aspect ratio doesn't match the container, some parts may be cut off.

This is extremely common for hero sections.

Example:

```css
.hero {
    height: 500px;
    background-image: url("hero.jpg");
    background-size: cover;
}
```

---

# 5. `background-size: contain`

```css
.hero {
    background-size: contain;
}
```

`contain` means:

> Scale the entire image so that it fits inside the element without cropping.

The entire image remains visible.

However, you may get empty space around the image.

Conceptually:

```text
┌──────────────────────────────┐
│                              │
│      ┌──────────────┐        │
│      │    IMAGE     │        │
│      └──────────────┘        │
│                              │
└──────────────────────────────┘
```

---

## `cover` vs `contain` ⭐⭐⭐

| `cover`                    | `contain`                              |
| -------------------------- | -------------------------------------- |
| Covers entire container    | Fits entire image                      |
| Image can be cropped       | Image isn't cropped                    |
| May cut some image content | May leave empty space                  |
| Great for hero backgrounds | Great when whole image must be visible |

### Remember:

```text
cover   → cover the box
contain → contain the image
```

For most website hero backgrounds:

```css
background-size: cover;
```

is what you'll commonly use.

---

# 6. `background-position`

`background-position` controls **where the background image is positioned** inside the element.

Example:

```css
.hero {
    background-position: center;
}
```

Common values:

```text
center
top
bottom
left
right
```

You can combine them:

```css
background-position: center center;
```

or:

```css
background-position: center top;
```

---

## Example

```css
.hero {
    background-image: url("hero.jpg");
    background-size: cover;
    background-position: center;
}
```

This is an extremely common combination.

It means:

```text
background image
      ↓
cover the entire hero
      ↓
keep image centered
```

---

## Why is `background-position` important?

Suppose your hero image contains a person's face.

With:

```css
background-position: center;
```

the face may remain visible.

But perhaps the important content is on the left:

```css
background-position: left center;
```

You can control which portion remains visible when `cover` crops the image.

---

# 7. `background-repeat`

By default, background images can repeat if the image is smaller than the element.

Example:

```css
.box {
    background-image: url("pattern.png");
}
```

The image may repeat:

```text
┌──────────────────────────┐
│ 🟦 🟦 🟦 🟦 🟦           │
│ 🟦 🟦 🟦 🟦 🟦           │
│ 🟦 🟦 🟦 🟦 🟦           │
└──────────────────────────┘
```

You can control this using `background-repeat`.

---

## `no-repeat`

```css
.box {
    background-repeat: no-repeat;
}
```

The image appears only once.

This is very common.

---

## Other values

```css
background-repeat: repeat;
```

Repeats horizontally and vertically.

```css
background-repeat: repeat-x;
```

Repeats horizontally.

```css
background-repeat: repeat-y;
```

Repeats vertically.

```css
background-repeat: no-repeat;
```

Doesn't repeat.

---

# 8. Common Background Combination ⭐⭐⭐

You'll frequently see:

```css
.hero {
    background-image: url("hero.jpg");
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}
```

This is worth remembering.

It means:

```text
background-image
→ use the image

background-size: cover
→ cover the entire section

background-position: center
→ keep it centered

background-repeat: no-repeat
→ don't repeat it
```

---

# 9. `border`

You learned the basic border while studying the Box Model.

The `border` property creates a line around an element.

Example:

```css
.box {
    border: 2px solid black;
}
```

The general syntax is:

```css
border: width style color;
```

For example:

```css
border: 3px solid red;
```

means:

```text
3px   → width
solid → style
red   → color
```

---

# 10. Border Styles

Common styles include:

```css
border: 2px solid black;
```

```css
border: 2px dashed black;
```

```css
border: 2px dotted black;
```

```css
border: 2px double black;
```

The most commonly used:

```text
solid
dashed
dotted
```

---

# 11. Individual Borders

You can style each side separately.

```css
.box {
    border-top: 2px solid red;
    border-right: 2px solid blue;
    border-bottom: 2px solid green;
    border-left: 2px solid black;
}
```

You can also set only one border:

```css
.box {
    border-bottom: 1px solid #ddd;
}
```

This is very common for:

* Navbar separators
* Form fields
* Card sections
* Table rows

---

# 12. `border-radius` ⭐⭐⭐

`border-radius` makes the corners of an element **rounded**.

Example:

```css
.card {
    border-radius: 10px;
}
```

Instead of:

```text
┌──────────────┐
│              │
│    CARD      │
│              │
└──────────────┘
```

you get rounded corners:

```text
╭──────────────╮
│              │
│    CARD      │
│              │
╰──────────────╯
```

---

## Different radius values

```css
.card {
    border-radius: 5px;
}
```

Slightly rounded.

```css
.card {
    border-radius: 20px;
}
```

More rounded.

```css
.card {
    border-radius: 50%;
}
```

Can create a circular shape when the element has equal width and height.

Example:

```css
.profile {
    width: 100px;
    height: 100px;
    border-radius: 50%;
}
```

This is commonly used for profile images.

---

# 13. Different Border Radius for Each Corner

You can control individual corners:

```css
.box {
    border-top-left-radius: 20px;
    border-top-right-radius: 10px;
    border-bottom-right-radius: 30px;
    border-bottom-left-radius: 5px;
}
```

Or use shorthand:

```css
.box {
    border-radius: 20px 10px 30px 5px;
}
```

The order follows:

```text
top-left
top-right
bottom-right
bottom-left
```

---

# 14. `box-shadow` ⭐⭐⭐

`box-shadow` adds a shadow around an element.

Example:

```css
.card {
    box-shadow: 0 4px 10px gray;
}
```

Basic syntax:

```text
box-shadow: x-offset y-offset blur color;
```

For example:

```css
box-shadow: 5px 5px 10px gray;
```

means:

```text
5px  → horizontal position
5px  → vertical position
10px → blur
gray → shadow color
```

---

# 15. Understanding `box-shadow`

Consider:

```css
.card {
    box-shadow: 0 4px 10px gray;
}
```

Break it down:

```text
0
↓
No horizontal movement

4px
↓
Shadow moves down

10px
↓
Shadow becomes blurred

gray
↓
Shadow color
```

---

# 16. Negative Shadow Values

You can use negative values.

```css
box-shadow: -5px -5px 10px gray;
```

This moves the shadow:

```text
left
↑
```

instead of:

```text
right
↓
```

You don't need to memorize complicated shadow combinations initially.

Understand the basic syntax first.

---

# 17. Spread Radius

There is an optional fourth length:

```text
x-offset
y-offset
blur
spread
color
```

Example:

```css
.card {
    box-shadow: 0 4px 10px 2px gray;
}
```

Here:

```text
0   → x offset
4px → y offset
10px → blur
2px → spread
gray → color
```

The spread controls how much the shadow expands.

---

# 18. `inset`

You can create an **inner shadow** using `inset`.

```css
.box {
    box-shadow: inset 0 0 10px gray;
}
```

Normal:

```css
box-shadow: 0 4px 10px gray;
```

Shadow appears outside.

With:

```css
box-shadow: inset 0 0 10px gray;
```

Shadow appears inside the element.

For beginner/interview preparation, just know what `inset` does.

---

# 19. Background Gradient ⭐⭐

Although your list says `background-image`, it's useful to know that CSS gradients are also commonly used as background images.

For example:

```css
.box {
    background-image: linear-gradient(to right, blue, purple);
}
```

This creates a gradient.

You can also use:

```css
background: linear-gradient(to right, red, yellow);
```

A gradient doesn't require an actual image file.

This is very common in modern websites.

---

# 20. Background Overlay ⭐⭐⭐

This is particularly useful for hero sections.

Suppose you have:

```css
.hero {
    background-image: url("hero.jpg");
}
```

You may want dark text/image overlay.

You can combine a gradient with the image:

```css
.hero {
    background-image:
        linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
        url("hero.jpg");

    background-size: cover;
    background-position: center;
}
```

The gradient appears over the image.

This is frequently used to make white text readable over a photo.

---

# 21. Complete Hero Example ⭐⭐⭐

### HTML

```html
<section class="hero">
    <h1>Welcome to Inskill</h1>
    <p>Build your skills and your career.</p>
</section>
```

### CSS

```css
.hero {
    min-height: 500px;

    background-image:
        linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
        url("images/hero.jpg");

    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;

    border-radius: 15px;

    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);

    text-align: center;
    padding: 100px 20px;
}

.hero h1 {
    font-size: 40px;
}
```

Notice how several concepts work together:

```text
background-image
        ↓
background-size
        ↓
background-position
        ↓
background-repeat
        ↓
border-radius
        ↓
box-shadow
```

This is much closer to real-world CSS.

---

# 22. Card Example ⭐⭐⭐

A common modern card:

```css
.card {
    width: 350px;
    padding: 25px;

    background-color: white;

    border: 1px solid #ddd;
    border-radius: 12px;

    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}
```

This creates:

```text
        ╭─────────────────────╮
        │                     │
        │       CARD          │
        │                     │
        │                     │
        ╰─────────────────────╯
              ↓ shadow
```

You'll use this pattern constantly in frontend development.

---

# 23. Border vs Box Shadow ⭐⭐

Another useful interview question.

### Border

```css
border: 1px solid #ddd;
```

A **real boundary** around the element.

It participates in the box model.

### Box shadow

```css
box-shadow: 0 4px 10px gray;
```

Creates a visual shadow.

It **doesn't take up layout space** like a border does.

Easy memory:

```text
border     → actual boundary
box-shadow → visual shadow
```

---

# 24. `background` Shorthand

There is also a shorthand property:

```css
background
```

For example:

```css
.hero {
    background: url("hero.jpg") center / cover no-repeat;
}
```

This can represent multiple background properties.

Instead of:

```css
.hero {
    background-image: url("hero.jpg");
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
}
```

you can use:

```css
.hero {
    background: url("hero.jpg") center / cover no-repeat;
}
```

For now, **learn the individual properties first**. Shorthand can come after you're comfortable.

---

# 25. Most Important Combinations to Remember ⭐⭐⭐

### Hero image

```css
.hero {
    background-image: url("hero.jpg");
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}
```

### Card

```css
.card {
    background-color: white;
    border: 1px solid #ddd;
    border-radius: 12px;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}
```

### Circular image

```css
.profile {
    width: 100px;
    height: 100px;
    border-radius: 50%;
}
```

### Gradient

```css
.banner {
    background: linear-gradient(to right, blue, purple);
}
```

---

# 26. Interview Questions ⭐⭐⭐

### Q1. What does `background-size: cover` do?

It scales the background image so that it completely covers the element. Parts of the image may be cropped.

---

### Q2. Difference between `cover` and `contain`?

```text
cover
→ entire element is covered
→ image may be cropped

contain
→ entire image is visible
→ empty space may remain
```

---

### Q3. What does `background-position: center` do?

It positions the background image at the center of the element.

---

### Q4. What does `background-repeat: no-repeat` do?

It prevents the background image from repeating.

---

### Q5. What is `border-radius` used for?

It rounds the corners of an element.

```css
border-radius: 10px;
```

---

### Q6. How do you make a circle using CSS?

Usually:

```css
width: 100px;
height: 100px;
border-radius: 50%;
```

The width and height should be equal for a circle.

---

### Q7. What is `box-shadow`?

It creates a shadow around an element.

```css
box-shadow: 0 4px 10px gray;
```

---

### Q8. Does `box-shadow` take up space?

**No.**

A box shadow is visual and doesn't affect the normal layout size like a border does.

---

### Q9. What is the difference between `border` and `box-shadow`?

```text
border
→ creates a boundary around the element
→ affects box dimensions depending on box-sizing

box-shadow
→ creates a visual shadow
→ doesn't take up layout space
```

---

# 27. Final Cheat Sheet

```text
background-color
→ background color

background-image
→ background image/gradient

background-size
→ controls image size
→ cover / contain

background-position
→ controls image position
→ center / top / bottom / left / right

background-repeat
→ controls repetition
→ repeat / no-repeat / repeat-x / repeat-y

border
→ boundary around element

border-radius
→ rounded corners

box-shadow
→ shadow around element
```

### Most important memory:

```text
background-size: cover
→ cover the box

background-size: contain
→ show the whole image

background-position: center
→ center the image

background-repeat: no-repeat
→ don't repeat

border-radius: 10px
→ rounded corners

border-radius: 50%
→ circle (with equal width/height)

box-shadow
→ visual shadow, doesn't take layout space
```
