# 🟢 Level 2 — Links, Images & Lists

This level is **very important for HTML interviews** because links, images, and lists are used constantly in real websites.

We'll cover each topic from **basic → practical → interview level**.

---

# 13. Anchor `<a>`

The `<a>` element is used to create a **hyperlink**.

Basic syntax:

```html
<a href="https://www.google.com">Google</a>
```

Here:

```text
<a>                    → anchor element
href                   → destination
https://www.google.com → URL
Google                 → clickable text
```

When the user clicks **Google**, the browser navigates to that URL.

---

## Basic structure

```html
<a href="URL">Link Text</a>
```

Example:

```html
<a href="https://example.com">Visit Example</a>
```

---

## Link to another page

Suppose your project contains:

```text
project/
│
├── index.html
├── about.html
└── contact.html
```

You can write:

```html
<a href="about.html">About Us</a>
<a href="contact.html">Contact Us</a>
```

This is a **relative URL**.

---

## Link to a section on the same page

You can use an element's `id`.

```html
<h2 id="about">About Us</h2>
```

Then:

```html
<a href="#about">Go to About</a>
```

Clicking the link moves the browser to:

```html
<h2 id="about">
```

The `#` means you're referring to an element ID on the current page.

---

## Link to another page's section

You can also do:

```html
<a href="about.html#team">Our Team</a>
```

And on `about.html`:

```html
<h2 id="team">Our Team</h2>
```

---

# 14. Absolute vs Relative URLs ⭐⭐⭐

This is a very common interview topic.

There are two major types:

```text
Absolute URL
Relative URL
```

---

# Absolute URL

An absolute URL contains the complete address.

Example:

```html
<a href="https://www.google.com">Google</a>
```

Another:

```html
<img src="https://example.com/images/logo.png" alt="Company logo">
```

The URL tells the browser exactly where the resource is located.

### Examples

```text
https://example.com/about
https://example.com/images/logo.png
https://example.com/products/phone
```

---

# Relative URL

A relative URL describes a location **relative to the current document or URL context**.

Suppose:

```text
website/
│
├── index.html
├── about.html
│
└── images/
    └── logo.png
```

From `index.html`:

```html
<a href="about.html">About</a>
```

And:

```html
<img src="images/logo.png" alt="Logo">
```

These are relative paths.

---

## Current directory

```html
<a href="about.html">About</a>
```

Means:

> Find `about.html` relative to the current document location.

---

## Child directory

```html
<img src="images/logo.png" alt="Logo">
```

Means:

> Go into the `images` directory and find `logo.png`.

---

## Parent directory `../`

Suppose:

```text
website/
│
├── index.html
│
└── pages/
    └── about.html
```

Inside `about.html`:

```html
<a href="../index.html">Home</a>
```

`..` means:

> Go up one directory.

So:

```text
pages/
   ↓
..
   ↓
website/
```

---

## Root-relative URL

You may also see:

```html
<a href="/about">About</a>
```

The `/` at the beginning means the path starts from the **site's root**.

This is different from:

```html
<a href="about.html">About</a>
```

which is relative to the current location.

---

## Interview question

### Q: What is the difference between absolute and relative URLs?

**Answer:**

> An absolute URL contains the complete resource address, such as `https://example.com/about`. A relative URL specifies the resource location relative to the current document or site context, such as `about.html` or `../images/logo.png`.

---

# 15. `target` ⭐⭐⭐

The `target` attribute specifies **where the linked document should open**.

Example:

```html
<a href="https://google.com" target="_blank">
    Google
</a>
```

This commonly opens the link in a new tab.

---

## Common target values

### `_self`

```html
<a href="about.html" target="_self">
    About
</a>
```

Opens in the current browsing context.

This is generally the default.

---

### `_blank`

```html
<a href="https://google.com" target="_blank">
    Google
</a>
```

Opens in a new browsing context, commonly a new tab.

---

### `_parent`

```html
<a href="page.html" target="_parent">
    Page
</a>
```

Relevant when working with nested browsing contexts such as iframes.

---

### `_top`

```html
<a href="page.html" target="_top">
    Page
</a>
```

Loads into the top-level browsing context.

Again, these are primarily relevant when dealing with frames/iframes.

---

# Important: `_blank` and `rel` ⭐⭐⭐

You'll often see:

```html
<a
    href="https://example.com"
    target="_blank"
    rel="noopener noreferrer"
>
    Example
</a>
```

Why?

Because when opening another site in a new browsing context, `rel="noopener"` prevents the newly opened page from using the opener relationship to access the opening page's `window` in the way older browsers allowed.

For modern browsers, `noopener` behavior is generally handled automatically for `_blank`, but explicitly using it remains common and clear.

`noreferrer` additionally prevents the browser from sending the referring URL in the `Referer` header and also implies `noopener`.

For interviews, remember:

```text
target="_blank"
       +
rel="noopener noreferrer"
```

is a common secure pattern.

---

# 16. `rel` ⭐⭐⭐

`rel` means **relationship**.

It tells the browser the relationship between the current document and the linked resource.

Example:

```html
<a
    href="https://example.com"
    rel="noopener noreferrer"
>
    Example
</a>
```

---

## Common `rel` values

### `noopener`

```html
rel="noopener"
```

Controls the opener relationship.

Commonly used with:

```html
target="_blank"
```

---

### `noreferrer`

```html
rel="noreferrer"
```

Tells the browser not to send the referring URL in the `Referer` header.

It also implies `noopener` in modern HTML behavior.

---

### `nofollow`

```html
<a href="https://example.com" rel="nofollow">
    Example
</a>
```

This can be used to indicate that you don't want search engines to associate your site's ranking signals with the linked page in the normal way.

Common in certain user-generated or paid-link scenarios.

---

### `sponsored`

```html
<a href="https://example.com" rel="sponsored">
    Sponsored Link
</a>
```

Used for paid/sponsored links.

---

### `ugc`

Means **user-generated content**.

```html
<a href="https://example.com" rel="ugc">
    User Link
</a>
```

Useful for links posted by users, such as in comments or forums.

---

## Multiple `rel` values

You can use multiple values separated by spaces:

```html
<a
    href="https://example.com"
    target="_blank"
    rel="noopener noreferrer"
>
    Example
</a>
```

---

# 17. Email and Telephone Links ⭐⭐

The `<a>` element isn't only for websites.

You can create email links.

## Email

```html
<a href="mailto:hello@example.com">
    Email Us
</a>
```

When clicked, the browser can open the user's configured email application.

---

## Email with subject

```html
<a href="mailto:hello@example.com?subject=Job%20Opportunity">
    Send Email
</a>
```

The `%20` represents a space in a URL.

You can also encode other values appropriately.

---

## Telephone link

```html
<a href="tel:+919876543210">
    Call Us
</a>
```

On compatible mobile devices, this can open the phone/dialing interface.

---

## SMS

You may also encounter:

```html
<a href="sms:+919876543210">
    Send SMS
</a>
```

Browser/device support varies.

---

## Important interview point

`mailto:` and `tel:` are **URI schemes** used with links.

Example:

```text
mailto:
tel:
```

---

# 18. Images `<img>` ⭐⭐⭐

The `<img>` element embeds an image into a page.

Basic syntax:

```html
<img src="photo.jpg" alt="Profile photo">
```

Important attributes:

```text
src
alt
```

---

## `src`

`src` means **source**.

It tells the browser where the image comes from.

Example:

```html
<img src="images/profile.jpg" alt="Profile photo">
```

The browser looks for:

```text
images/profile.jpg
```

---

## Absolute image URL

```html
<img
    src="https://example.com/images/logo.png"
    alt="Company logo"
>
```

---

## Relative image URL

```html
<img
    src="images/logo.png"
    alt="Company logo"
>
```

---

## `<img>` is a void element

You don't write:

```html
<img></img>
```

Instead:

```html
<img src="photo.jpg" alt="Photo">
```

---

# 19. `alt` ⭐⭐⭐

`alt` means **alternative text**.

Example:

```html
<img
    src="dog.jpg"
    alt="Golden retriever sitting in a park"
>
```

The `alt` describes the image.

---

# Why is `alt` important?

There are several reasons.

### 1. Accessibility

Screen readers can read the alternative text to users who cannot see the image.

For example:

```html
<img
    src="profile.jpg"
    alt="John Smith smiling"
>
```

A screen reader can communicate the image's description.

---

### 2. When the image doesn't load

If the image can't be loaded, the alternative text provides useful information.

---

### 3. Meaningful content

If an image communicates information, its `alt` should communicate that information.

Bad:

```html
<img src="sales-chart.png" alt="image">
```

Better:

```html
<img
    src="sales-chart.png"
    alt="Sales increased by 25 percent from January to March"
>
```

---

# Decorative images

If an image is purely decorative and doesn't add meaningful information:

```html
<img src="decorative-line.png" alt="">
```

An empty `alt` tells assistive technology that the image is decorative and can generally be skipped.

### Important

Don't omit `alt` on normal content images.

Prefer:

```html
alt=""
```

for intentionally decorative images rather than:

```html
<!-- no alt -->
```

---

# What should NOT be in `alt`?

Don't write unnecessary things like:

```html
alt="Image of a dog"
```

Usually:

```html
alt="Golden retriever running in a park"
```

is better.

The screen reader already knows it's an image.

---

# 20. Image Dimensions ⭐⭐

You can specify dimensions:

```html
<img
    src="photo.jpg"
    alt="Mountain"
    width="600"
    height="400"
>
```

This gives the browser intrinsic dimensions for the image.

---

## Why specify width and height?

One important reason is **layout stability**.

If the browser knows the image dimensions before the image finishes loading, it can reserve the appropriate space.

This helps reduce unexpected layout movement.

---

## HTML vs CSS dimensions

You can use:

```html
<img
    src="photo.jpg"
    alt="Mountain"
    width="600"
    height="400"
>
```

Or CSS:

```css
img {
    width: 600px;
    height: 400px;
}
```

In modern websites, CSS is commonly used to control presentation.

HTML `width` and `height` still provide useful intrinsic sizing information.

---

# Responsive images

You don't want every image to overflow on mobile.

A common CSS rule is:

```css
img {
    max-width: 100%;
    height: auto;
}
```

This allows an image to shrink with its container while maintaining its aspect ratio.

---

# Important: Don't distort images

Suppose the original image is:

```text
1200 × 800
```

Its aspect ratio is:

```text
1200 / 800 = 1.5
```

If you force:

```text
600 × 600
```

you can distort it.

Usually you want to preserve the aspect ratio.

---

# 21. Ordered Lists `<ol>` ⭐⭐

An ordered list represents items where **order matters**.

Example:

```html
<ol>
    <li>Wake up</li>
    <li>Have breakfast</li>
    <li>Go to work</li>
</ol>
```

The browser typically displays:

```text
1. Wake up
2. Have breakfast
3. Go to work
```

---

# `<ol>` and `<li>`

`<ol>` means:

> Ordered List

`<li>` means:

> List Item

Structure:

```text
<ol>
   |
   ├── <li>
   ├── <li>
   └── <li>
```

Example:

```html
<ol>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ol>
```

---

# `start`

You can specify where numbering starts.

```html
<ol start="5">
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ol>
```

Result:

```text
5. HTML
6. CSS
7. JavaScript
```

---

# `reversed`

You can reverse the numbering.

```html
<ol reversed>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ol>
```

Conceptually:

```text
3. HTML
2. CSS
1. JavaScript
```

---

# `type`

You may encounter:

```html
<ol type="A">
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ol>
```

Possible numbering styles include:

```text
1
A
a
I
i
```

In modern development, CSS is often preferred for visual list styling.

---

# 22. Unordered Lists `<ul>` ⭐⭐⭐

An unordered list represents items where **the order doesn't matter**.

Example:

```html
<ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ul>
```

Typically:

```text
• HTML
• CSS
• JavaScript
```

---

# Real-world use of `<ul>`

Navigation menus frequently use lists.

Example:

```html
<nav>
    <ul>
        <li><a href="index.html">Home</a></li>
        <li><a href="about.html">About</a></li>
        <li><a href="contact.html">Contact</a></li>
    </ul>
</nav>
```

This is a very common professional pattern.

---

# Why use `<ul>` for navigation?

Because a navigation menu is logically a **list of links**.

The CSS can then make it look like:

```text
Home | About | Contact
```

even though semantically it is still a list.

---

# Nested Lists ⭐⭐

Lists can contain other lists.

Example:

```html
<ul>
    <li>
        Frontend
        <ul>
            <li>HTML</li>
            <li>CSS</li>
            <li>JavaScript</li>
        </ul>
    </li>

    <li>
        Backend
        <ul>
            <li>Node.js</li>
            <li>PHP</li>
        </ul>
    </li>
</ul>
```

Structure:

```text
Frontend
├── HTML
├── CSS
└── JavaScript

Backend
├── Node.js
└── PHP
```

---

# `<ol>` vs `<ul>` ⭐⭐⭐

This is an important interview question.

### `<ol>`

Use when **order matters**.

Examples:

* Steps to install software
* Ranking
* Recipe instructions
* Top 10 list

```html
<ol>
    <li>Download</li>
    <li>Install</li>
    <li>Run</li>
</ol>
```

### `<ul>`

Use when **order doesn't matter**.

Examples:

* Navigation links
* Features
* Shopping items
* Skills

```html
<ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ul>
```

---

# 23. Description Lists `<dl>` ⭐⭐

This is less commonly used than `<ul>` and `<ol>`, but it is useful and can come up in interviews.

A description list represents **terms and their associated descriptions/details**.

Basic structure:

```html
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language</dd>

    <dt>CSS</dt>
    <dd>Cascading Style Sheets</dd>
</dl>
```

Three elements:

```text
<dl> → Description List
<dt> → Description Term
<dd> → Description Details
```

---

# `<dl>`

The parent container:

```html
<dl>
    ...
</dl>
```

It represents a description list.

---

# `<dt>`

The term/name:

```html
<dt>HTML</dt>
```

Think:

```text
What is being described?
```

---

# `<dd>`

The description/detail:

```html
<dd>HyperText Markup Language</dd>
```

Think:

```text
What is the information associated with the term?
```

---

# Real-world example

Suppose you're displaying product specifications:

```html
<dl>
    <dt>Brand</dt>
    <dd>Apple</dd>

    <dt>Storage</dt>
    <dd>256 GB</dd>

    <dt>Color</dt>
    <dd>Black</dd>
</dl>
```

Conceptually:

```text
Brand
    Apple

Storage
    256 GB

Color
    Black
```

---

# Another example — FAQ

You can use a description list for term/answer-style content:

```html
<dl>
    <dt>What is HTML?</dt>
    <dd>HTML is used to structure web content.</dd>

    <dt>What is CSS?</dt>
    <dd>CSS is used to style web content.</dd>
</dl>
```

However, for a fully interactive FAQ, other semantic structures such as `<details>`/`<summary>` may be more appropriate depending on the design.

---

# Multiple `<dd>` elements

A term can have multiple descriptions.

```html
<dl>
    <dt>Frontend Developer</dt>

    <dd>Works with HTML, CSS and JavaScript.</dd>

    <dd>Builds user interfaces for web applications.</dd>
</dl>
```

---

# Multiple `<dt>` elements

Multiple terms can share a description.

```html
<dl>
    <dt>HTML</dt>
    <dt>HyperText Markup Language</dt>

    <dd>A markup language used to structure web documents.</dd>
</dl>
```

---

# 🔥 Complete Example — Level 2

Let's combine everything we've learned.

```html
<!DOCTYPE html>

<html lang="en">

<head>
    <meta charset="UTF-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0"
    >

    <title>Frontend Developer</title>
</head>

<body>

    <h1>Frontend Developer</h1>

    <!-- Navigation -->
    <nav>
        <ul>
            <li>
                <a href="index.html">Home</a>
            </li>

            <li>
                <a href="about.html">About</a>
            </li>

            <li>
                <a href="contact.html">Contact</a>
            </li>
        </ul>
    </nav>

    <hr>

    <!-- Profile -->
    <h2>About Me</h2>

    <img
        src="images/profile.jpg"
        alt="Frontend developer working on a laptop"
        width="400"
        height="300"
    >

    <p>
        I am learning
        <strong>HTML</strong>,
        <strong>CSS</strong>,
        and
        <strong>JavaScript</strong>.
    </p>

    <!-- Skills -->
    <h2>Skills</h2>

    <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
        <li>React</li>
    </ul>

    <!-- Learning order -->
    <h2>Learning Roadmap</h2>

    <ol>
        <li>Learn HTML</li>
        <li>Learn CSS</li>
        <li>Learn JavaScript</li>
        <li>Learn React</li>
    </ol>

    <!-- Contact -->
    <h2>Contact</h2>

    <p>
        <a href="mailto:hello@example.com">
            Email Me
        </a>
    </p>

    <p>
        <a href="tel:+919876543210">
            Call Me
        </a>
    </p>

    <!-- Description list -->
    <h2>Technologies</h2>

    <dl>
        <dt>HTML</dt>
        <dd>Used to structure web pages.</dd>

        <dt>CSS</dt>
        <dd>Used to style web pages.</dd>

        <dt>JavaScript</dt>
        <dd>Used to add behavior and interactivity.</dd>
    </dl>

    <hr>

    <footer>
        <p>
            © 2026 My Portfolio
        </p>
    </footer>

</body>

</html>
```

---

# 🧠 Interview Cheat Sheet

| Topic              | Remember                                      |
| ------------------ | --------------------------------------------- |
| `<a>`              | Creates hyperlinks                            |
| `href`             | Specifies destination                         |
| Absolute URL       | Complete URL                                  |
| Relative URL       | Relative to current location/context          |
| `target="_blank"`  | Opens in a new browsing context               |
| `target="_self"`   | Current browsing context                      |
| `rel`              | Describes relationship to linked resource     |
| `noopener`         | Controls opener relationship                  |
| `noreferrer`       | Prevents referrer information from being sent |
| `mailto:`          | Email link                                    |
| `tel:`             | Telephone link                                |
| `<img>`            | Embeds an image                               |
| `src`              | Image source                                  |
| `alt`              | Alternative text                              |
| `width` / `height` | Intrinsic image dimensions                    |
| `<ol>`             | Ordered list                                  |
| `<ul>`             | Unordered list                                |
| `<li>`             | List item                                     |
| `<dl>`             | Description list                              |
| `<dt>`             | Description term                              |
| `<dd>`             | Description/details                           |

---

# ⭐ Top Interview Questions From Level 2

Make sure you can explain these **without looking at notes**:

### 1. What is `<a>` used for?

Creates a hyperlink to another resource or location.

### 2. What is `href`?

Specifies the destination of the hyperlink.

### 3. Absolute vs relative URL?

```text
Absolute:
https://example.com/about

Relative:
about.html
../images/logo.png
```

### 4. What does `target="_blank"` do?

Opens the link in a new browsing context, commonly a new tab.

### 5. Why use `rel="noopener"`?

It controls the opener relationship and prevents the opened page from accessing the opener through the `window.opener` mechanism.

### 6. What is `alt`?

Alternative text that provides a textual representation of an image's meaning, especially important for accessibility and when an image can't be displayed.

### 7. What is the difference between `<ol>` and `<ul>`?

```text
<ol> → order matters
<ul> → order doesn't matter
```

### 8. What is `<dl>`?

A description list containing terms/details using `<dt>` and `<dd>`.

### 9. Why should navigation often use `<ul>`?

Because a navigation menu is naturally a list of links, while `<nav>` identifies the navigation region.

### 10. Is `<img>` a normal element with a closing tag?

No. `<img>` is a **void element**.

---

# 🎯 What You Should Practice Now

Create this folder:

```text
html-level-2/
│
├── index.html
├── about.html
├── contact.html
└── images/
    └── profile.jpg
```

Build a small **portfolio website** containing:

```text
Home
│
├── Navigation
│   ├── Home
│   ├── About
│   └── Contact
│
├── Profile Image
│
├── Skills → <ul>
│
├── Learning Roadmap → <ol>
│
├── Technologies → <dl>
│
└── Contact
    ├── Email
    └── Phone
```

While building it, deliberately practice:

```text
<a>
href
absolute URL
relative URL
target
rel
mailto:
tel:
<img>
src
alt
width
height
<ul>
<ol>
<li>
<dl>
<dt>
<dd>
```

