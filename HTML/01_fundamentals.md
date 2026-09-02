Absolutely. Let’s go through **Level 1 — HTML Fundamentals** properly, from zero to interview-ready. The goal is not just to memorize tags, but to understand **what HTML is, how it works, and why each concept matters**.

# 🟢 Level 1 — HTML Fundamentals

## 1. What is HTML?

**HTML = HyperText Markup Language.**

HTML is the standard markup language used to **structure content on web pages**.

Think of a website like a house:

* **HTML** → structure of the house 🏠
* **CSS** → appearance/design 🎨
* **JavaScript** → behavior/functionality ⚙️

For example:

```html
<h1>Hello World</h1>
<p>Welcome to my website.</p>
```

Here:

* `<h1>` tells the browser: "This is the main heading."
* `<p>` tells the browser: "This is a paragraph."

HTML doesn't primarily tell the browser **how something should look**. It tells the browser **what the content means and how it is structured**.

---

# 2. Why is HTML called a "Markup Language"?

HTML is **not a programming language** in the traditional sense.

It doesn't have things like:

```text
if
else
for
while
functions
```

Instead, HTML uses **markup/tags** to describe content.

Example:

```html
<h1>My Portfolio</h1>
<p>I am a frontend developer.</p>
```

The browser interprets this structure and creates the page.

So:

```text
HTML
 ↓
Browser reads HTML
 ↓
Browser creates DOM
 ↓
Page appears on screen
```

---

# 3. What is HyperText?

**HyperText** means text that can contain links to other documents/pages.

Example:

```html
<a href="https://example.com">Visit Website</a>
```

The user can click the link and navigate somewhere else.

That's the **HyperText** part of HTML.

---

# 4. What is an HTML Tag?

A tag is written using angle brackets:

```html
<h1>
```

Example:

```html
<h1>Hello</h1>
```

Here:

```text
<h1>       → opening tag
Hello      → content
</h1>      → closing tag
```

Together they form an HTML element.

---

# 5. What is an HTML Element?

An **HTML element** generally consists of:

```text
Opening tag
     ↓
   <p>
   Hello
   </p>
     ↑
Closing tag
```

Example:

```html
<p>Hello World</p>
```

The entire thing is an **element**.

### Important distinction

**Tag:**

```html
<p>
```

**Element:**

```html
<p>Hello World</p>
```

This distinction can appear in interviews.

---

# 6. Opening and Closing Tags

Most HTML elements have an opening and closing tag.

Example:

```html
<h1>Welcome</h1>
```

Opening:

```html
<h1>
```

Closing:

```html
</h1>
```

Notice the `/` in the closing tag.

Another example:

```html
<p>This is a paragraph.</p>
```

---

# 7. Void Elements

Some HTML elements **do not have closing tags**.

These are commonly called **void elements**.

Examples:

```html
<img>
<br>
<hr>
<input>
<meta>
<link>
```

For example:

```html
<img src="profile.jpg" alt="Profile photo">
```

You don't write:

```html
<img></img>
```

That's incorrect HTML.

### Common void elements to remember

```text
area
base
br
col
embed
hr
img
input
link
meta
param
source
track
wbr
```

You don't need to memorize all of them immediately, but know the concept.

---

# 8. HTML Attributes

Attributes provide **additional information about an element**.

Example:

```html
<a href="https://example.com">Google</a>
```

Here:

```text
href
```

is an attribute.

Another example:

```html
<img src="photo.jpg" alt="My photo">
```

Attributes:

```text
src
alt
```

General structure:

```html
<tag attribute="value">
```

Example:

```html
<p class="description">Hello</p>
```

Here:

```text
class     → attribute
"description" → attribute value
```

---

# 9. Why Are Attributes Important?

Attributes control or describe an element.

Example:

```html
<a href="https://google.com">
    Google
</a>
```

Without `href`, the `<a>` element doesn't know where the link should go.

Image:

```html
<img src="cat.jpg" alt="A cat">
```

`src` tells the browser where the image is.

`alt` describes the image.

---

# 10. Global Attributes

Some attributes can be used on many different HTML elements.

These are called **global attributes**.

Important ones:

### `id`

```html
<div id="header"></div>
```

An `id` should identify a particular element.

### `class`

```html
<p class="text">Hello</p>
```

Classes are commonly used for CSS and JavaScript.

### `title`

```html
<p title="This is additional information">
    Hello
</p>
```

### `style`

```html
<p style="color: red;">Hello</p>
```

Although possible, inline styling is generally avoided in larger projects.

### `hidden`

```html
<p hidden>Hello</p>
```

The element is hidden from normal rendering.

### `lang`

Usually placed on `<html>`:

```html
<html lang="en">
```

This tells browsers and assistive technologies the primary language.

---

# 11. HTML Document Structure ⭐⭐⭐

This is one of the **most important things to understand**.

A normal HTML document looks like this:

```html
<!DOCTYPE html>

<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>My Website</title>
</head>

<body>

    <h1>Hello World</h1>
    <p>Welcome to my website.</p>

</body>

</html>
```

Let's understand every part.

---

# 12. `<!DOCTYPE html>`

At the top:

```html
<!DOCTYPE html>
```

This tells the browser that the document should be interpreted using **modern HTML standards**.

It is called the **DOCTYPE declaration**.

Important:

It is **not an HTML element**.

Interview question:

### Q: What is `DOCTYPE`?

Answer:

> `<!DOCTYPE html>` is a declaration that tells the browser to use standards mode for the document and interpret it as modern HTML.

You don't need to memorize the old HTML4/XHTML doctypes unless specifically asked.

---

# 13. `<html>`

The root element is:

```html
<html>
```

Everything in the HTML document is generally inside it.

Example:

```html
<html>
    
    <head>
        ...
    </head>

    <body>
        ...
    </body>

</html>
```

Think:

```text
<html>
   |
   |--- <head>
   |
   |--- <body>
```

---

# 14. `lang` Attribute

A good document starts with:

```html
<html lang="en">
```

`lang="en"` means the primary language is English.

For Hindi:

```html
<html lang="hi">
```

For French:

```html
<html lang="fr">
```

This is useful for:

* Accessibility
* Screen readers
* Search engines
* Browser language handling

---

# 15. `<head>`

The `<head>` contains **metadata and resources about the document**.

Example:

```html
<head>

    <meta charset="UTF-8">

    <meta name="viewport"
          content="width=device-width, initial-scale=1.0">

    <title>My Website</title>

</head>
```

The `<head>` is **not where the visible page content normally goes**.

Common things inside `<head>`:

```html
<title>
<meta>
<link>
<style>
<script>
```

---

# 16. `<title>`

Example:

```html
<title>My Portfolio</title>
```

This defines the document's title.

You'll usually see it in:

* Browser tabs
* Bookmarks
* Search engine results in many contexts

Example:

```html
<head>
    <title>John's Portfolio</title>
</head>
```

The browser tab may display:

```text
John's Portfolio
```

---

# 17. `<meta charset="UTF-8">`

Example:

```html
<meta charset="UTF-8">
```

This specifies the character encoding.

UTF-8 supports a very large range of characters.

For example:

```text
Hello
नमस्ते
你好
こんにちは
😀
```

Without appropriate encoding, characters may sometimes be displayed incorrectly.

For modern HTML documents, UTF-8 is the standard choice.

---

# 18. Viewport Meta Tag ⭐⭐⭐

You'll frequently see:

```html
<meta name="viewport"
      content="width=device-width, initial-scale=1.0">
```

This is important for responsive websites.

It tells mobile browsers how to size and scale the page's viewport.

Break it down:

```text
width=device-width
```

means the viewport width should correspond to the device's width.

```text
initial-scale=1.0
```

sets the initial zoom level.

You should know this for frontend interviews.

---

# 19. `<body>`

The `<body>` contains the content that makes up the page.

Example:

```html
<body>

    <h1>My Website</h1>

    <p>Welcome!</p>

    <button>Click Me</button>

</body>
```

This is the part users interact with and see as page content.

---

# 20. Headings `<h1>` to `<h6>` ⭐⭐⭐

HTML provides six heading levels:

```html
<h1>Main Heading</h1>

<h2>Section Heading</h2>

<h3>Subsection Heading</h3>

<h4>Heading</h4>

<h5>Heading</h5>

<h6>Heading</h6>
```

Hierarchy:

```text
h1
 ├── h2
 │    ├── h3
 │    └── h3
 └── h2
      └── h3
```

### Important

Don't choose headings only based on their default visual size.

For example, don't do:

```html
<h1>This is small text</h1>
```

just because CSS makes it look good.

Use headings according to **document structure and meaning**.

CSS controls the appearance.

---

# 21. Should a Page Have Only One `<h1>`?

You may hear:

> "A page must have exactly one h1."

That's an oversimplification.

Modern HTML does not impose a universal rule that there can only ever be one `<h1>`. However, for most normal pages, having a clear primary heading is a **good practical approach**.

Example:

```html
<h1>My Portfolio</h1>

<h2>About Me</h2>

<h2>Projects</h2>

<h2>Contact</h2>
```

This gives a clear hierarchy.

---

# 22. Paragraph `<p>`

Use `<p>` for paragraphs.

```html
<p>
    HTML is used to structure web pages.
</p>
```

You can have multiple paragraphs:

```html
<p>HTML provides structure.</p>

<p>CSS provides presentation.</p>

<p>JavaScript provides behavior.</p>
```

---

# 23. `<br>` — Line Break

`<br>` creates a line break.

Example:

```html
<p>
    Hello<br>
    World
</p>
```

Output conceptually:

```text
Hello
World
```

### Important interview point

Don't use `<br>` to create large page spacing.

Bad:

```html
<p>Hello</p>
<br>
<br>
<br>
<br>
<p>World</p>
```

Use CSS for layout and spacing.

`<br>` should represent a **meaningful line break**, such as in an address or poem.

---

# 24. `<hr>` — Thematic Break

Example:

```html
<p>Chapter 1</p>

<hr>

<p>Chapter 2</p>
```

`<hr>` represents a **thematic break** between sections of content.

It isn't simply "a horizontal line."

CSS can control its visual appearance.

---

# 25. Text Formatting Elements

HTML provides elements with different meanings.

### `<strong>`

Indicates strong importance.

```html
<p>
    <strong>Warning:</strong> Save your work.
</p>
```

### `<b>`

Draws attention stylistically without conveying the same semantic meaning as `<strong>`.

```html
<p>This is <b>bold-looking</b> text.</p>
```

For important content, prefer:

```html
<strong>
```

rather than using `<b>` just for emphasis.

---

# 26. `<em>`

Indicates emphasis.

```html
<p>
    You <em>must</em> complete this task.
</p>
```

### `<i>`

Typically represents text set apart from normal prose, such as terms, foreign words, or other conventional alternate voice.

```html
<p>
    The word <i>bonjour</i> is French.
</p>
```

Don't think simply:

```text
em = italic
i = italic
```

That's only about typical default appearance.

Their **meaning** is different.

---

# 27. `<mark>`

Highlights text.

```html
<p>
    This is <mark>important</mark>.
</p>
```

---

# 28. `<small>`

Represents side comments or small print.

```html
<p>
    Price: ₹999
    <small>Terms and conditions apply.</small>
</p>
```

---

# 29. `<del>`

Represents deleted content.

```html
<p>
    Price:
    <del>₹1999</del>
    ₹999
</p>
```

---

# 30. `<ins>`

Represents inserted content.

```html
<p>
    New price:
    <ins>₹999</ins>
</p>
```

---

# 31. `<sub>` — Subscript

Example:

```html
H<sub>2</sub>O
```

Displays conceptually:

```text
H₂O
```

Useful for chemical formulas.

---

# 32. `<sup>` — Superscript

Example:

```html
x<sup>2</sup>
```

Displays:

```text
x²
```

Useful for mathematical expressions and footnote references.

---

# 33. HTML Comments

Comments are written:

```html
<!-- This is a comment -->
```

The browser doesn't display the comment as page content.

Example:

```html
<!-- Navigation starts here -->

<nav>
    ...
</nav>
```

Comments are useful for developers.

### Important

Comments are **not secure storage**.

Don't put passwords or secrets inside:

```html
<!-- password: 12345 -->
```

Users can inspect the HTML source.

---

# 34. Nesting HTML Elements ⭐⭐⭐

Elements can be placed inside other elements.

Example:

```html
<p>
    Hello <strong>World</strong>
</p>
```

Here:

```text
p
└── strong
```

Another example:

```html
<div>
    <h1>My Website</h1>

    <p>
        Welcome to my website.
    </p>
</div>
```

The structure is:

```text
div
├── h1
└── p
```

This is called **nesting**.

---

# 35. Correct Nesting

Correct:

```html
<p>
    This is <strong>important</strong>.
</p>
```

Incorrect:

```html
<p>
    This is <strong>important.
</p>
</strong>
```

The element opened last should generally be closed first.

Think:

```text
Open A
   Open B
      Close B
Close A
```

Like:

```html
<div>
    <p>Hello</p>
</div>
```

---

# 36. Whitespace in HTML

HTML generally collapses consecutive spaces and line breaks in normal text.

For example:

```html
<p>Hello        World</p>
```

will normally render roughly as:

```text
Hello World
```

If you need specific spacing/layout, use CSS rather than adding lots of spaces.

---

# 37. HTML Entities

Some characters have special meaning in HTML.

For example:

```html
<
>
&
```

can be represented using character references.

Examples:

```html
&lt;
&gt;
&amp;
```

So:

```html
<p>5 &lt; 10</p>
```

renders:

```text
5 < 10
```

Common ones:

| Entity   | Meaning            |
| -------- | ------------------ |
| `&lt;`   | `<`                |
| `&gt;`   | `>`                |
| `&amp;`  | `&`                |
| `&quot;` | `"`                |
| `&apos;` | `'`                |
| `&nbsp;` | non-breaking space |

You don't need to memorize every entity.

---

# 38. `<div>` — Generic Block Container

You'll see `<div>` everywhere.

Example:

```html
<div>
    <h2>About Me</h2>
    <p>I am a developer.</p>
</div>
```

`div` is a **generic container**.

It has no special semantic meaning by itself.

This becomes particularly important when we study **semantic HTML** later.

---

# 39. `<span>` — Generic Inline Container

`span` is another generic container, commonly used within text.

Example:

```html
<p>
    My name is <span>John</span>.
</p>
```

Generally:

```text
div   → generic block-level container
span  → generic inline container
```

But remember: modern CSS layout is more flexible than simply thinking "div = block, span = inline." Their default display behavior is what differs; CSS can change it.

---

# 40. `div` vs `span`

Very common interview question.

### `div`

```html
<div>Hello</div>
<div>World</div>
```

Typically behaves as a block-level element.

### `span`

```html
<span>Hello</span>
<span>World</span>
```

Typically behaves as an inline element.

Conceptually:

```text
div:
Hello
World

span:
Hello World
```

But neither is inherently semantic.

---

# 41. HTML Case Sensitivity

HTML tag names are generally **case-insensitive**, but you should write them in lowercase.

Good:

```html
<h1>Hello</h1>
```

Avoid:

```html
<H1>Hello</H1>
```

Use consistent lowercase style.

---

# 42. File Extension

HTML files normally use:

```text
.html
```

Example:

```text
index.html
about.html
contact.html
```

A common starting page is:

```text
index.html
```

---

# 43. Your First Complete HTML Page

Put everything together:

```html
<!DOCTYPE html>

<html lang="en">

<head>
    <meta charset="UTF-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0"
    >

    <title>My First Website</title>
</head>

<body>

    <h1>My First Website</h1>

    <p>
        Hello! I am learning HTML.
    </p>

    <p>
        HTML is used to structure web pages.
    </p>

    <hr>

    <h2>About Me</h2>

    <p>
        I am learning frontend development.
    </p>

</body>

</html>
```

You should be able to explain **every line** of this code.

---

# 🎯 Level 1 Interview Questions

After completing this level, you should confidently answer:

### Basic

1. What is HTML?
2. What does HTML stand for?
3. Is HTML a programming language?
4. What is an HTML tag?
5. What is an HTML element?
6. What are attributes?
7. What are void elements?
8. What is nesting?

### Document structure

9. What is `DOCTYPE`?
10. What is the purpose of `<html>`?
11. What is `<head>`?
12. What is `<body>`?
13. What is `<title>`?
14. Why do we use `<meta charset="UTF-8">`?
15. Why do we use the viewport meta tag?
16. Why use `lang="en"`?

### Content

17. What are `h1`–`h6`?
18. What is the difference between `<p>` and `<br>`?
19. What is `<hr>`?
20. What is the difference between `<strong>` and `<b>`?
21. What is the difference between `<em>` and `<i>`?
22. What are `<sub>` and `<sup>`?

### Containers

23. What is `<div>`?
24. What is `<span>`?
25. Difference between `div` and `span`?
26. Why shouldn't you use `div` for everything?

---

# 🧪 Practice — Don't Skip This

Create an `index.html` and build this structure **without copying the answer from above**:

```text
My Portfolio
│
├── Introduction
│   └── Paragraph about yourself
│
├── Skills
│   └── Paragraph
│
├── Education
│   └── Paragraph
│
└── Contact
    └── Paragraph
```

Requirements:

* Use `<!DOCTYPE html>`
* Use `html lang`
* Use `<head>`
* Add charset
* Add viewport
* Add `<title>`
* Use `<h1>`
* Use `<h2>`
* Use `<p>`
* Use `<strong>`
* Use `<em>`
* Use `<hr>`
* Add an HTML comment
* Properly nest everything

### The key thing to remember

Don't try to memorize 100 tags.

For **Level 1**, understand this mental model:

```text
HTML
│
├── Document
│   ├── DOCTYPE
│   └── html
│
├── Head
│   ├── charset
│   ├── viewport
│   └── title
│
└── Body
    ├── Headings
    ├── Paragraphs
    ├── Text elements
    ├── Containers
    └── Other content
```

Once this is solid, **Level 2 should be Links + Images + Lists**, followed by **Semantic HTML and Forms**, which are the most important parts for frontend interviews.
