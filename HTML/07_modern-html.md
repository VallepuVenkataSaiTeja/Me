Absolutely. Let’s continue with **🟠 Level 7 — Modern HTML ⭐⭐**.

This level is important because these features come up in **modern frontend development and interviews**, especially `data-*`, responsive images, `<dialog>`, `<template>`, `<picture>`, Canvas, and SVG.

---

# 🟠 Level 7 — Modern HTML ⭐⭐

## 83. `data-*` Attributes

### What are `data-*` attributes?

`data-*` attributes allow you to store **custom data** directly on HTML elements.

The attribute must start with:

```html
data-
```

Example:

```html
<button data-user-id="101" data-role="admin">
    View User
</button>
```

Here:

```html
data-user-id="101"
data-role="admin"
```

are custom data attributes.

### Why use them?

They are useful when JavaScript needs some information associated with an HTML element.

For example:

```html
<button data-product-id="5001">
    Add to Cart
</button>
```

JavaScript can determine which product was clicked.

---

### Accessing `data-*` using JavaScript

HTML:

```html
<button id="btn" data-user-id="101" data-role="admin">
    View User
</button>
```

JavaScript:

```javascript
const button = document.querySelector("#btn");

console.log(button.dataset.userId);
console.log(button.dataset.role);
```

Output:

```text
101
admin
```

### Important conversion

HTML:

```html
data-user-id
```

JavaScript:

```javascript
element.dataset.userId
```

Hyphenated names become camelCase.

```text
data-user-name → dataset.userName
data-product-id → dataset.productId
data-user-role → dataset.userRole
```

### Setting data

```javascript
button.dataset.status = "active";
```

This produces:

```html
data-status="active"
```

### Removing data

```javascript
delete button.dataset.status;
```

### Interview question

**Q: Why use `data-*` instead of inventing arbitrary HTML attributes?**

Because `data-*` is the standard HTML mechanism for storing custom, non-semantic data on elements.

Don't do:

```html
<button user-id="101">
```

Prefer:

```html
<button data-user-id="101">
```

### Important distinction

`data-*` is good for **small pieces of element-related data**.

Don't use it as a replacement for your application's entire data/state management system.

---

# 84. `<details>`

`<details>` creates a native expandable/collapsible section.

Example:

```html
<details>
    <p>HTML stands for HyperText Markup Language.</p>
</details>
```

The browser provides the expandable behavior.

Usually you use it with `<summary>`.

```html
<details>
    <summary>What is HTML?</summary>

    <p>
        HTML is the standard markup language for creating web pages.
    </p>
</details>
```

Result conceptually:

```text
▶ What is HTML?
```

Clicking it:

```text
▼ What is HTML?

  HTML is the standard markup language...
```

### Why is `<details>` useful?

Common uses:

* FAQ sections
* Additional information
* Help text
* Documentation
* Expandable explanations
* Settings/details

### Open by default

Use the `open` attribute:

```html
<details open>
    <summary>HTML Information</summary>

    <p>This section is open initially.</p>
</details>
```

Without `open`:

```html
<details>
```

starts collapsed.

With:

```html
<details open>
```

starts expanded.

### Interview question

**Q: Can `<details>` create an accordion without JavaScript?**

Yes, basic expandable/collapsible behavior can be created using native HTML.

---

# 85. `<summary>`

`<summary>` provides the **visible label** for a `<details>` element.

Example:

```html
<details>
    <summary>What is CSS?</summary>

    <p>CSS is used to style HTML documents.</p>
</details>
```

Think of it like:

```text
<details>
    ├── <summary> ← clickable heading
    └── content
</details>
```

### Important

`<summary>` is normally used as the first child of `<details>`:

```html
<details>
    <summary>Question</summary>

    <p>Answer</p>
</details>
```

### FAQ example

```html
<h2>Frequently Asked Questions</h2>

<details>
    <summary>What is HTML?</summary>
    <p>HTML structures web pages.</p>
</details>

<details>
    <summary>What is CSS?</summary>
    <p>CSS styles web pages.</p>
</details>

<details>
    <summary>What is JavaScript?</summary>
    <p>JavaScript adds behavior and interactivity.</p>
</details>
```

This is a great example of using **native HTML functionality instead of unnecessary JavaScript**.

---

# 86. `<dialog>`

`<dialog>` represents a **dialog box/modal**.

Example:

```html
<dialog id="myDialog">
    <h2>Delete Account?</h2>

    <p>Are you sure you want to delete your account?</p>

    <button>Cancel</button>
    <button>Delete</button>
</dialog>
```

Modern browsers provide native dialog functionality.

---

## Opening a dialog

With JavaScript:

```javascript
const dialog = document.querySelector("#myDialog");

dialog.showModal();
```

This opens it as a modal dialog.

Conceptually:

```text
        ┌─────────────────────────┐
        │ Delete Account?         │
        │                         │
        │ Are you sure?           │
        │                         │
        │ Cancel     Delete       │
        └─────────────────────────┘
```

---

## `show()` vs `showModal()`

This is an important interview question.

### `show()`

```javascript
dialog.show();
```

Opens a non-modal dialog.

The user can generally still interact with the rest of the page.

### `showModal()`

```javascript
dialog.showModal();
```

Opens a modal dialog.

The dialog becomes the active interaction layer and the rest of the document is normally inert.

### Closing

```javascript
dialog.close();
```

You can also give it a return value:

```javascript
dialog.close("confirmed");
```

Then:

```javascript
console.log(dialog.returnValue);
```

gives:

```text
confirmed
```

---

## Dialog with buttons

```html
<dialog id="dialog">
    <h2>Welcome</h2>

    <p>Welcome to our website.</p>

    <button id="closeBtn">Close</button>
</dialog>

<button id="openBtn">Open Dialog</button>

<script>
    const dialog = document.querySelector("#dialog");

    document.querySelector("#openBtn").addEventListener("click", () => {
        dialog.showModal();
    });

    document.querySelector("#closeBtn").addEventListener("click", () => {
        dialog.close();
    });
</script>
```

### Why `<dialog>` is useful

Historically, developers often created modals using:

```html
<div class="modal">
```

and then implemented everything with CSS and JavaScript.

`<dialog>` provides a semantic/native mechanism for dialogs and modal interactions.

### Interview question

**Q: Difference between `<dialog>` and `<details>`?**

| Element     | Purpose                  |
| ----------- | ------------------------ |
| `<details>` | Expand/collapse content  |
| `<dialog>`  | Dialog/modal interaction |

---

# 87. `<template>`

`<template>` contains HTML that is **not rendered immediately**.

Example:

```html
<template id="userTemplate">
    <div class="user-card">
        <h2>User Name</h2>
        <p>User Email</p>
    </div>
</template>
```

You won't immediately see the card on the page.

The template acts like a reusable HTML blueprint.

---

## Why use `<template>`?

Imagine you need to generate 100 user cards.

Instead of constructing HTML manually in JavaScript:

```javascript
element.innerHTML = `
    <div>
        ...
    </div>
`;
```

you can define the structure in HTML.

```html
<template id="cardTemplate">
    <article class="card">
        <h2></h2>
        <p></p>
    </article>
</template>
```

Then clone it with JavaScript.

---

## Example

```html
<template id="cardTemplate">
    <article class="card">
        <h2 class="name"></h2>
        <p class="email"></p>
    </article>
>

<div id="container"></div>
```

JavaScript:

```javascript
const template = document.querySelector("#cardTemplate");
const container = document.querySelector("#container");

const card = template.content.cloneNode(true);

card.querySelector(".name").textContent = "Rahul";
card.querySelector(".email").textContent = "rahul@example.com";

container.appendChild(card);
```

Now the generated card appears.

### Key interview point

The content inside `<template>` is **inert until it is instantiated/cloned**.

Think:

```text
<template>
      ↓
HTML blueprint
      ↓
cloneNode()
      ↓
actual DOM
```

---

# 88. `<picture>`

`<picture>` is used when you need **art direction or different image sources depending on conditions**.

Example:

```html
<picture>
    <source media="(max-width: 600px)" srcset="mobile.jpg">

    <img src="desktop.jpg" alt="Mountain landscape">
</picture>
```

The browser can choose:

```text
Mobile screen  → mobile.jpg
Desktop screen → desktop.jpg
```

### Why is `<img>` still required?

This is important.

`<picture>` is a wrapper/container for alternative sources.

The actual fallback/rendering element is:

```html
<img>
```

Example:

```html
<picture>
    <source media="(max-width: 600px)" srcset="mobile.jpg">
    <source media="(max-width: 1200px)" srcset="tablet.jpg">

    <img src="desktop.jpg" alt="Mountain">
</picture>
```

### `<picture>` is especially useful for:

* Different crops on mobile/desktop
* Different image formats
* Art direction
* Performance optimization

---

# 89. `srcset`

`srcset` allows you to provide **multiple versions of an image** so the browser can choose an appropriate one.

Example:

```html
<img
    src="image-800.jpg"
    srcset="
        image-400.jpg 400w,
        image-800.jpg 800w,
        image-1200.jpg 1200w
    "
    alt="Mountain"
>
```

The browser chooses an appropriate image based on factors such as:

* viewport size
* device pixel density
* image dimensions
* browser calculations

### What does `400w` mean?

It means:

```text
400w = image resource is 400 CSS pixels wide
```

It does **not** mean:

```text
400px display width
```

That's an important interview distinction.

---

## `srcset` with `sizes`

For width-based responsive images, you will often see:

```html
<img
    src="image-800.jpg"
    srcset="
        image-400.jpg 400w,
        image-800.jpg 800w,
        image-1200.jpg 1200w
    "
    sizes="
        (max-width: 600px) 100vw,
        (max-width: 1000px) 50vw,
        800px
    "
    alt="Mountain"
>
```

### What does `sizes` tell the browser?

It gives the browser an estimate of **how wide the image will be displayed** under different conditions.

For example:

```html
sizes="(max-width: 600px) 100vw, 800px"
```

means approximately:

```text
viewport ≤ 600px → image displayed around viewport width
otherwise        → image displayed around 800px
```

This helps the browser choose a suitable source from `srcset`.

---

# 90. Responsive Images

Responsive images are images that adapt to different:

* screen sizes
* viewport widths
* device pixel densities
* layouts
* network/performance requirements

There are two major concepts you should understand:

### 1. Resolution switching

Same image, different resolutions.

```html
<img
    src="image-800.jpg"
    srcset="
        image-400.jpg 400w,
        image-800.jpg 800w,
        image-1200.jpg 1200w
    "
    sizes="100vw"
    alt="Landscape"
>
```

The browser chooses an appropriate resolution.

---

### 2. Art direction

Different image composition/crop for different screens.

Use:

```html
<picture>
```

Example:

```html
<picture>
    <source
        media="(max-width: 600px)"
        srcset="portrait.jpg"
    >

    <img
        src="landscape.jpg"
        alt="Person standing on a mountain"
    >
</picture>
```

Here you're not merely changing resolution.

You're changing the **image itself**.

---

## `srcset` vs `<picture>`

Very common interview question:

| Feature              | `srcset`                | `<picture>` |
| -------------------- | ----------------------- | ----------- |
| Multiple resolutions | ✅                       | ✅           |
| Art direction        | ❌                       | ✅           |
| Different crops      | ❌                       | ✅           |
| Different formats    | Limited/common patterns | ✅           |
| Uses `<img>`         | Yes                     | Yes         |

### Easy memory trick

**`srcset` = "Which size?"**

**`<picture>` = "Which image?"**

---

# Modern image format example

You can use `<picture>` to offer modern formats:

```html
<picture>
    <source srcset="image.avif" type="image/avif">
    <source srcset="image.webp" type="image/webp">

    <img src="image.jpg" alt="Beautiful landscape">
</picture>
```

The browser can choose a supported format.

The JPEG acts as a fallback.

---

# 91. `<canvas>`

`<canvas>` provides a drawing surface that JavaScript can manipulate.

Basic HTML:

```html
<canvas id="myCanvas" width="500" height="300">
    Your browser does not support canvas.
</canvas>
```

Canvas itself doesn't automatically draw things.

JavaScript does the drawing.

---

## Basic canvas example

```html
<canvas id="canvas" width="400" height="200"></canvas>

<script>
    const canvas = document.querySelector("#canvas");
    const ctx = canvas.getContext("2d");

    ctx.fillRect(50, 50, 150, 80);
</script>
```

`getContext("2d")` gives you a 2D drawing context.

---

## Drawing a rectangle

```javascript
ctx.fillRect(50, 50, 150, 80);
```

Conceptually:

```text
          150px
     ┌───────────────┐
     │               │
80px │   rectangle   │
     │               │
     └───────────────┘
```

---

## Drawing a circle

```javascript
ctx.beginPath();

ctx.arc(
    100,   // x
    100,   // y
    50,    // radius
    0,
    Math.PI * 2
);

ctx.fill();
```

---

## Drawing text

```javascript
ctx.font = "30px Arial";
ctx.fillText("Hello", 50, 100);
```

---

## Canvas use cases

Common examples:

* Games
* Charts
* Drawing applications
* Image manipulation
* Animations
* Data visualization
* Signature pads

### Important interview point

Canvas is primarily a **raster/pixel-based drawing surface**.

Once something is drawn, individual objects aren't automatically represented as DOM elements.

---

# Canvas vs SVG

This is a **very important interview comparison**.

| Canvas                                         | SVG                                     |
| ---------------------------------------------- | --------------------------------------- |
| Raster-based drawing surface                   | Vector graphics                         |
| Pixel-based                                    | Shape/path based                        |
| JavaScript commonly controls drawing           | SVG elements exist in DOM               |
| Great for many rapidly changing objects        | Great for scalable interactive graphics |
| Games/complex animations                       | Icons/charts/diagrams                   |
| Doesn't automatically expose each shape as DOM | Individual elements can be targeted     |
| Resolution-dependent drawing surface           | Resolution-independent                  |

### Simple rule

Use:

```text
Canvas → pixels / games / lots of dynamic drawing
SVG    → vectors / icons / diagrams / scalable graphics
```

---

# 92. SVG Basics

SVG means:

**Scalable Vector Graphics**

SVG is an XML-based markup language for describing vector graphics.

You can write SVG directly inside HTML.

Example:

```html
<svg width="200" height="200">
    <circle
        cx="100"
        cy="100"
        r="50"
        fill="blue"
    />
</svg>
```

The SVG contains a circle.

---

## Why is SVG called "vector"?

Instead of storing individual pixels, SVG describes shapes mathematically.

For example:

```html
<circle
    cx="100"
    cy="100"
    r="50"
/>
```

The browser knows:

```text
center = (100,100)
radius = 50
```

So it can render the circle at different sizes without the same kind of pixel scaling issue as a raster image.

---

# Common SVG elements

## `<svg>`

Root/container:

```html
<svg width="300" height="200">
</svg>
```

---

## `<circle>`

```html
<circle
    cx="100"
    cy="100"
    r="50"
/>
```

Important attributes:

```text
cx = center x
cy = center y
r  = radius
```

---

## `<rect>`

```html
<rect
    x="20"
    y="20"
    width="150"
    height="80"
/>
```

---

## `<line>`

```html
<line
    x1="10"
    y1="10"
    x2="200"
    y2="100"
/>
```

---

## `<polygon>`

```html
<polygon points="100,10 150,100 50,100" />
```

Useful for shapes such as triangles.

---

## `<path>`

`<path>` is one of the most powerful SVG elements.

Example:

```html
<path d="M 10 10 L 100 100" />
```

The `d` attribute describes the path.

You don't need to memorize path syntax for basic HTML interviews, but you should know that:

```html
<path>
```

is used to define complex shapes.

---

# SVG styling

SVG can be styled using attributes:

```html
<circle
    cx="100"
    cy="100"
    r="50"
    fill="red"
    stroke="black"
    stroke-width="3"
/>
```

Or CSS:

```html
<style>
    .circle {
        fill: red;
        stroke: black;
        stroke-width: 3;
    }
</style>

<svg width="200" height="200">
    <circle
        class="circle"
        cx="100"
        cy="100"
        r="50"
    />
</svg>
```

---

# SVG can be interactive

Because SVG elements can exist in the DOM, JavaScript can target them.

Example:

```html
<svg width="200" height="200">
    <circle
        id="circle"
        cx="100"
        cy="100"
        r="50"
    />
</svg>

<script>
    const circle = document.querySelector("#circle");

    circle.addEventListener("click", () => {
        console.log("Circle clicked");
    });
</script>
```

This is one reason SVG is excellent for interactive diagrams and visualizations.

---

# SVG as an image

You can also use SVG as an external image:

```html
<img
    src="logo.svg"
    alt="Company logo"
>
```

This is extremely common.

---

# SVG vs PNG/JPEG

### SVG

Vector:

```text
Shape → mathematically described
```

Excellent for:

* logos
* icons
* diagrams
* simple illustrations

### PNG/JPEG

Raster:

```text
Image → pixels
```

Excellent for:

* photographs
* complex textures
* detailed photographic images

---

# ⭐ `<picture>` vs `srcset` vs SVG vs Canvas

This is worth memorizing for interviews.

| Technology  | Main purpose                             |
| ----------- | ---------------------------------------- |
| `srcset`    | Choose appropriate image resolution      |
| `<picture>` | Choose image source/art direction/format |
| SVG         | Scalable vector graphics                 |
| Canvas      | Dynamic pixel-based drawing              |

---

# 🔥 Putting Level 7 Together

Here's a small modern HTML page using several of these concepts:

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Modern HTML</title>
</head>

<body>

    <button
        data-user-id="101"
        data-role="admin"
    >
        View User
    </button>

    <h1>Modern HTML Demo</h1>

    <!-- Details -->
    <details>
        <summary>What is HTML?</summary>

        <p>
            HTML is used to structure web pages.
        </p>
    </details>

    <!-- Dialog -->
    <dialog id="loginDialog">

        <h2>Login</h2>

        <p>Please enter your credentials.</p>

        <button onclick="loginDialog.close()">
            Close
        </button>

    </dialog>

    <button onclick="loginDialog.showModal()">
        Open Login
    </button>

    <!-- Responsive Image -->
    <picture>

        <source
            media="(max-width: 600px)"
            srcset="mobile.jpg"
        >

        <img
            src="desktop.jpg"
            srcset="
                desktop-800.jpg 800w,
                desktop-1200.jpg 1200w
            "
            sizes="100vw"
            alt="Mountain landscape"
        >

    </picture>

    <!-- SVG -->
    <svg width="200" height="200">

        <circle
            cx="100"
            cy="100"
            r="50"
            fill="blue"
        />

    </svg>

    <!-- Template -->
    <template id="userCard">

        <article>
            <h2 class="name"></h2>
            <p class="email"></p>
        </article>

    </template>

    <!-- Canvas -->
    <canvas
        id="canvas"
        width="300"
        height="150"
    >
    </canvas>

</body>

</html>
```

---

# 🧠 Level 7 Interview Cheat Sheet

| Topic             | Remember                               |
| ----------------- | -------------------------------------- |
| `data-*`          | Store custom data on HTML elements     |
| `dataset`         | JavaScript API for `data-*`            |
| `<details>`       | Expand/collapse content                |
| `<summary>`       | Clickable label for `<details>`        |
| `<dialog>`        | Native dialog/modal                    |
| `show()`          | Non-modal dialog                       |
| `showModal()`     | Modal dialog                           |
| `<template>`      | Inert reusable HTML blueprint          |
| `<picture>`       | Multiple image sources/art direction   |
| `srcset`          | Multiple image resolutions             |
| `sizes`           | Tells browser expected display width   |
| Responsive images | Serve appropriate image for conditions |
| `<canvas>`        | JavaScript drawing surface             |
| SVG               | Scalable vector graphics               |
| `<circle>`        | SVG circle                             |
| `<rect>`          | SVG rectangle                          |
| `<path>`          | Complex SVG shapes                     |

---

# 🎯 Most Important Interview Questions

### Beginner

**1. What are `data-*` attributes?**

Custom HTML attributes for storing element-specific data.

**2. What is `<details>` used for?**

Native expandable/collapsible content.

**3. What is `<summary>`?**

The visible clickable label for `<details>`.

**4. What is `<dialog>`?**

A native HTML element for dialogs and modal interactions.

**5. What is `<template>`?**

A container for HTML that isn't rendered immediately and can be cloned/instantiated later.

---

### Intermediate

**6. Difference between `srcset` and `<picture>`?**

`srcset` primarily provides alternative image resources/resolutions; `<picture>` provides conditional sources and is especially useful for art direction and format selection.

**7. What does `sizes` do?**

It tells the browser the expected rendered width of an image under different viewport conditions, helping it select an appropriate `srcset` candidate.

**8. Why use responsive images?**

To avoid unnecessarily downloading large images on smaller displays and improve performance.

**9. Canvas vs SVG?**

Canvas is a pixel-oriented drawing surface; SVG uses vector elements that remain part of the document structure.

**10. Why is SVG scalable?**

Because it describes graphics using vector shapes/paths rather than fixed pixels.

---

# 🔥 Advanced Interview Questions

### Q11. Does `<picture>` replace `<img>`?

**No.**

Usually:

```html
<picture>
    <source ...>
    <img ...>
</picture>
```

`<img>` is the actual image element/fallback.

---

### Q12. Does `srcset="image-400.jpg 400w"` mean the image will display at 400px?

**No.**

`400w` describes the intrinsic width of that source for the browser's responsive-image selection algorithm. The rendered size is determined by the layout/CSS and the `sizes` information.

---

### Q13. Does `<template>` display its content?

Not directly.

```html
<template>
    <p>Hello</p>
</template>
```

doesn't simply render that paragraph into the page.

The template is used as an inert blueprint until its content is instantiated.

---

### Q14. Can SVG be manipulated with JavaScript?

Yes.

For inline SVG:

```javascript
document.querySelector("circle")
```

can select an SVG element.

---

### Q15. Can SVG be styled with CSS?

Yes.

```css
circle {
    fill: blue;
}
```

---

### Q16. Can Canvas elements be selected individually from the DOM?

Not in the same way as SVG shapes.

If you draw a circle onto a canvas:

```javascript
ctx.arc(...);
ctx.fill();
```

the circle isn't automatically a separate DOM element.

That's a major difference between Canvas and SVG.

---

# 🏆 What You Should Be Able to Build After Level 7

You should now be comfortable building:

### 1. FAQ

```html
<details>
    <summary>What is HTML?</summary>
    <p>HTML structures content.</p>
</details>
```

### 2. Modal

```html
<dialog id="modal">
    <h2>Welcome</h2>
</dialog>
```

### 3. Responsive image

```html
<img
    src="small.jpg"
    srcset="
        small.jpg 400w,
        medium.jpg 800w,
        large.jpg 1200w
    "
    sizes="100vw"
    alt="Landscape"
>
```

### 4. Art-directed image

```html
<picture>
    <source
        media="(max-width: 600px)"
        srcset="mobile.jpg"
    >

    <img src="desktop.jpg" alt="Landscape">
</picture>
```

### 5. Dynamic HTML template

```html
<template id="card">
    <article>
        <h2></h2>
        <p></p>
    </article>
</template>
```

### 6. SVG icon/diagram

```html
<svg>
    <circle cx="50" cy="50" r="30"></circle>
</svg>
```

### 7. Canvas drawing

```html
<canvas id="canvas"></canvas>
```

with JavaScript drawing on it.

---

# 🧩 Level 7 Mental Model

Remember the level like this:

```text
MODERN HTML
│
├── Custom Data
│   └── data-*
│
├── Native UI
│   ├── <details>
│   ├── <summary>
│   └── <dialog>
│
├── HTML Templates
│   └── <template>
│
├── Responsive Images
│   ├── <picture>
│   ├── <source>
│   ├── srcset
│   └── sizes
│
└── Graphics
    ├── <canvas>
    └── SVG
        ├── <circle>
        ├── <rect>
        ├── <line>
        ├── <polygon>
        └── <path>
```