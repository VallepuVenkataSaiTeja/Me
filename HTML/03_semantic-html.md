# 🟡 Level 3 — Semantic HTML ⭐⭐⭐

This is one of the **most important HTML topics for interviews**.

At the end of this section, you should understand not only what `<header>`, `<nav>`, `<main>`, `<section>`, etc. mean, but also **when to use them and when NOT to use them**.

---

# 24. What is Semantic HTML? ⭐⭐⭐

### Simple definition

**Semantic HTML means using HTML elements according to their meaning/purpose, rather than using generic elements everywhere.**

For example, instead of:

```html
<div class="header">
    <div class="navigation">
        ...
    </div>
</div>
```

we can use:

```html
<header>
    <nav>
        ...
    </nav>
</header>
```

The second version tells the browser and developers what those areas **actually represent**.

---

## Semantic vs non-semantic elements

### Semantic

These communicate meaning:

```html
<header>
<nav>
<main>
<section>
<article>
<aside>
<footer>
<figure>
<time>
<address>
```

### Non-semantic

These don't tell you much about their content:

```html
<div>
<span>
```

For example:

```html
<div>
    My Blog
</div>
```

What is this `div`?

Could be:

* header
* footer
* article
* sidebar
* navigation
* anything else

But:

```html
<header>
    My Blog
</header>
```

immediately tells you:

> This is a header.

---

# Why is Semantic HTML important? ⭐⭐⭐

There are several major benefits.

### 1. Accessibility

Screen readers and other assistive technologies can understand the structure of the page better.

For example:

```html
<nav>
    ...
</nav>
```

communicates that this is a navigation region.

---

### 2. SEO

Semantic structure can help search engines better understand the organization and meaning of your content.

Semantic HTML isn't a magic SEO ranking trick, but **clear document structure and meaningful markup are good for search engines**.

---

### 3. Readability

Compare:

```html
<div>
    <div>
        <div>
            ...
        </div>
    </div>
</div>
```

with:

```html
<header>
    <nav>
        ...
    </nav>
</header>
```

The second is much easier for developers to understand.

---

### 4. Maintainability

When another developer opens your code, semantic elements make the page structure obvious.

---

# Important interview answer

### Q: What is semantic HTML?

A strong answer:

> Semantic HTML means using HTML elements that clearly describe the meaning and purpose of their content, such as `<nav>` for navigation, `<article>` for self-contained content, and `<main>` for the primary content. It improves accessibility, maintainability, and can help search engines understand the page structure.

---

# 25. `<header>` ⭐⭐⭐

`<header>` represents **introductory content for a page or a section**.

Example:

```html
<header>
    <h1>My Blog</h1>
    <p>Welcome to my blog.</p>
</header>
```

A header commonly contains:

* Logo
* Site title
* Heading
* Navigation
* Introductory information

---

## Website header

```html
<header>
    <h1>My Website</h1>

    <nav>
        <a href="/">Home</a>
        <a href="/about">About</a>
        <a href="/contact">Contact</a>
    </nav>
</header>
```

---

## Important: `<header>` isn't necessarily only the top of the page

This is a common misconception.

You can have a header associated with a section or article.

```html
<article>

    <header>
        <h2>Understanding JavaScript</h2>
        <p>Published by John</p>
    </header>

    <p>JavaScript is...</p>

</article>
```

So `<header>` means:

> Introductory/header content for its surrounding section or page.

---

## `<header>` vs `<head>` ⭐⭐⭐

Don't confuse them.

### `<head>`

Contains document metadata:

```html
<head>
    <title>My Website</title>
    <meta charset="UTF-8">
</head>
```

Usually not visible as page content.

### `<header>`

Contains introductory page/section content:

```html
<header>
    <h1>My Website</h1>
</header>
```

Visible page content.

Think:

```text
<head>    → information ABOUT the document
<header>  → introductory content IN the document
```

---

# 26. `<nav>` ⭐⭐⭐

`<nav>` represents a **section containing navigation links**.

Example:

```html
<nav>
    <a href="/">Home</a>
    <a href="/about">About</a>
    <a href="/services">Services</a>
    <a href="/contact">Contact</a>
</nav>
```

A more structured example:

```html
<nav>
    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/about">About</a></li>
        <li><a href="/contact">Contact</a></li>
    </ul>
</nav>
```

---

## What belongs inside `<nav>`?

Navigation links such as:

* Main site navigation
* Table of contents
* Pagination/navigation links
* Major navigation areas

---

## Do I need `<nav>` for every link?

**No.**

This is important.

You don't need:

```html
<nav>
    <a href="/privacy">Privacy Policy</a>
</nav>
```

for every individual link.

`<nav>` is for a **major block of navigation links**.

---

# 27. `<main>` ⭐⭐⭐

`<main>` represents the **primary content of the document**.

Example:

```html
<body>

    <header>
        <h1>My Website</h1>
    </header>

    <nav>
        ...
    </nav>

    <main>

        <h2>Welcome</h2>

        <p>
            This is the main content.
        </p>

    </main>

    <footer>
        ...
    </footer>

</body>
```

Think:

```text
Page
│
├── Header
├── Navigation
├── MAIN CONTENT  ← <main>
└── Footer
```

---

## What should NOT normally be inside `<main>`?

Content repeated across multiple pages, such as:

* Site-wide navigation
* Site-wide footer
* Common header content

Those usually belong outside `<main>`.

---

## How many `<main>` elements?

For a normal document, there should generally be **one visible `<main>` element representing the primary content**.

Don't do:

```html
<main>
    Home
</main>

<main>
    About
</main>
```

for two simultaneously visible page areas.

---

# 28. `<section>` ⭐⭐⭐

`<section>` represents a **thematic grouping of content**.

Example:

```html
<section>
    <h2>About Me</h2>

    <p>
        I am a frontend developer.
    </p>
</section>
```

Another:

```html
<section>
    <h2>My Skills</h2>

    <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
    </ul>
</section>
```

---

## Think of `<section>` as:

> "This is a distinct topic/part of this page."

For example:

```text
Homepage
│
├── Hero section
├── About section
├── Skills section
├── Projects section
└── Contact section
```

---

# Should every `<div>` become `<section>`?

**No.**

This is a very common beginner mistake.

Bad:

```html
<section>
    <span>Hello</span>
</section>

<section>
    <span>World</span>
</section>
```

just because you want semantic HTML.

Use `<section>` when there is a **meaningful thematic grouping**.

If you simply need a generic container for styling/layout, use:

```html
<div>
```

---

# `<section>` usually has a heading

A section commonly has a heading that identifies its topic:

```html
<section>
    <h2>Our Services</h2>

    <p>We build websites.</p>
</section>
```

This makes its purpose clearer to both users and assistive technologies.

---

# 29. `<article>` ⭐⭐⭐

`<article>` represents **self-contained content that could stand on its own**.

Examples:

* Blog post
* News article
* Forum post
* Product review
* User comment
* Social media post

Example:

```html
<article>

    <h2>How to Learn HTML</h2>

    <p>
        HTML is the foundation of web development.
    </p>

</article>
```

---

## The key question

When deciding whether to use `<article>`, ask:

> **Could this content make sense independently or be distributed separately?**

If yes, `<article>` may be appropriate.

---

## Blog example

```html
<main>

    <h1>My Blog</h1>

    <article>
        <h2>Learning HTML</h2>
        <p>HTML is used to structure websites.</p>
    </article>

    <article>
        <h2>Learning CSS</h2>
        <p>CSS is used to style websites.</p>
    </article>

</main>
```

Each article is an independent piece of content.

---

# `<article>` can contain `<section>`

Yes.

For example:

```html
<article>

    <header>
        <h2>Learning HTML</h2>
    </header>

    <section>
        <h3>What is HTML?</h3>
        <p>HTML structures web content.</p>
    </section>

    <section>
        <h3>Why Learn HTML?</h3>
        <p>It is fundamental to frontend development.</p>
    </section>

</article>
```

The article is the overall self-contained content.

The sections divide it into related topics.

---

# 30. `<aside>` ⭐⭐⭐

`<aside>` represents content that is **related to the surrounding content but is not part of its main flow**.

Common examples:

* Sidebar
* Related posts
* Advertisements
* Author information
* Related links
* Additional information

Example:

```html
<main>

    <article>
        <h1>Learning HTML</h1>

        <p>
            HTML is used to structure web pages.
        </p>
    </article>

    <aside>
        <h2>Related Articles</h2>

        <ul>
            <li>Learn CSS</li>
            <li>Learn JavaScript</li>
        </ul>
    </aside>

</main>
```

---

# Sidebar example

Visually:

```text
┌───────────────────────────────┐
│           HEADER              │
├───────────────────────────────┤
│                               │
│   MAIN CONTENT    │  ASIDE    │
│                   │           │
│   Article         │ Related   │
│                   │ Articles  │
│                   │           │
├───────────────────────────────┤
│           FOOTER              │
└───────────────────────────────┘
```

The layout itself is normally created with CSS.

The HTML says:

```html
<main>
    ...
</main>

<aside>
    ...
</aside>
```

---

# Important: `<aside>` doesn't always mean "right sidebar"

It doesn't have to physically appear on the right.

CSS can place it:

* Left
* Right
* Above
* Below
* Somewhere else

`<aside>` describes **meaning**, not visual position.

---

# 31. `<footer>` ⭐⭐⭐

`<footer>` represents footer information for a page or section.

Example:

```html
<footer>
    <p>© 2026 My Website</p>
</footer>
```

Common footer content:

* Copyright
* Contact information
* Related links
* Author information
* Legal information

---

## Footer can belong to an article

Just like `<header>`, `<footer>` isn't only for the whole website.

Example:

```html
<article>

    <h2>My Blog Post</h2>

    <p>Content...</p>

    <footer>
        <p>Written by John</p>
    </footer>

</article>
```

Here the footer belongs to the article.

---

# `<header>` and `<footer>` can be nested

For example:

```html
<article>

    <header>
        <h2>HTML Basics</h2>
    </header>

    <p>
        HTML is a markup language.
    </p>

    <footer>
        <p>Written by John</p>
    </footer>

</article>
```

Very useful pattern.

---

# 32. `<figure>` ⭐⭐

`<figure>` represents **self-contained content**, often an image, diagram, illustration, code example, or similar content that is referenced from the main content.

Example:

```html
<figure>

    <img
        src="html-structure.png"
        alt="Diagram showing the structure of an HTML document"
    >

</figure>
```

---

# Why use `<figure>`?

It groups related content into a meaningful unit.

For example:

```html
<figure>

    <img
        src="chart.png"
        alt="Sales increased from January to March"
    >

    <figcaption>
        Sales growth from January to March.
    </figcaption>

</figure>
```

Now the image and its caption are logically connected.

---

# `<figure>` isn't only for images

You can use it for:

### Diagram

```html
<figure>
    <img src="diagram.png" alt="System architecture diagram">
    <figcaption>System architecture.</figcaption>
</figure>
```

### Code

```html
<figure>

    <pre><code>
        console.log("Hello");
    </code></pre>

    <figcaption>
        Example JavaScript code.
    </figcaption>

</figure>
```

---

# 33. `<figcaption>` ⭐⭐

`<figcaption>` provides a **caption for the content inside `<figure>`**.

Example:

```html
<figure>

    <img
        src="mountain.jpg"
        alt="Snow-covered mountain"
    >

    <figcaption>
        A snow-covered mountain during winter.
    </figcaption>

</figure>
```

Think:

```text
<figure>
   │
   ├── Content
   │
   └── <figcaption>
         Caption
       </figcaption>
</figure>
```

---

# Does `<figcaption>` have to come after the image?

No.

It can appear before or after the content inside the `<figure>`.

For example:

```html
<figure>

    <figcaption>
        Company revenue by year
    </figcaption>

    <img
        src="revenue.png"
        alt="Bar chart showing company revenue"
    >

</figure>
```

---

# 34. `<time>` ⭐⭐

`<time>` represents a **specific period in time or date**.

Example:

```html
<p>
    Published on
    <time datetime="2026-09-06">
        September 6, 2026
    </time>
</p>
```

The visible text is:

```text
September 6, 2026
```

The machine-readable value is:

```text
2026-09-06
```

---

# Why use `datetime`?

`datetime` provides a machine-readable representation.

Example:

```html
<time datetime="2026-09-06">
    September 6, 2026
</time>
```

Humans see:

```text
September 6, 2026
```

Machines can understand:

```text
2026-09-06
```

This can be useful to browsers, search engines, and other software.

---

# Time with time

Example:

```html
<time datetime="2026-09-06T10:30">
    10:30 AM
</time>
```

You can also include a timezone/offset where appropriate.

---

# Duration

`<time>` can represent durations too.

Example:

```html
<time datetime="PT2H30M">
    2 hours 30 minutes
</time>
```

The exact datetime syntax can get more advanced, but for interviews, understand the main idea:

> `<time>` provides semantic markup for dates, times, and durations.

---

# 35. `<address>` ⭐⭐

`<address>` represents **contact information for the nearest article or body ancestor**.

This is an important nuance.

Example:

```html
<address>
    Contact:
    <a href="mailto:hello@example.com">
        hello@example.com
    </a>
</address>
```

---

## Article author information

```html
<article>

    <h2>Learning HTML</h2>

    <p>
        HTML is the foundation of the web.
    </p>

    <address>
        Written by
        <a href="mailto:john@example.com">
            John Smith
        </a>
    </address>

</article>
```

Here, the `<address>` represents contact information associated with the article.

---

# Important misconception about `<address>`

Many beginners think:

> `<address>` means physical postal address.

Not necessarily.

It is primarily for **contact information related to the relevant page/article**.

For example:

```html
<address>
    <a href="mailto:contact@example.com">Email us</a>
    <a href="tel:+919876543210">Call us</a>
</address>
```

This is perfectly reasonable.

---

# 🚨 `<address>` vs a physical address

If you simply want to display a postal address, you don't necessarily need `<address>` unless it represents contact information associated with the page/article.

For example, a business contact block might be:

```html
<address>
    123 Main Street<br>
    Bengaluru, Karnataka
</address>
```

That's a valid use when the address is contact information for the relevant content.

---

# ⭐ The Most Important Comparison

You absolutely should know these differences for interviews:

| Element        | Meaning                              |
| -------------- | ------------------------------------ |
| `<header>`     | Introductory/header content          |
| `<nav>`        | Major navigation links               |
| `<main>`       | Primary content of the page          |
| `<section>`    | Thematic grouping                    |
| `<article>`    | Self-contained/distributable content |
| `<aside>`      | Related/secondary content            |
| `<footer>`     | Footer information                   |
| `<figure>`     | Self-contained referenced content    |
| `<figcaption>` | Caption for a figure                 |
| `<time>`       | Date/time/duration                   |
| `<address>`    | Contact information                  |

---

# 🔥 `<section>` vs `<article>` — VERY IMPORTANT

This is one of the most common questions.

### `<section>`

A thematic part of a page.

```html
<section>
    <h2>Our Services</h2>
    <p>We build websites.</p>
</section>
```

Think:

> "A section of a larger document."

### `<article>`

A self-contained piece of content.

```html
<article>
    <h2>How to Learn HTML</h2>
    <p>...</p>
</article>
```

Think:

> "This could stand on its own."

---

# 🔥 `<div>` vs `<section>`

### `<div>`

Generic container:

```html
<div class="card">
    ...
</div>
```

Use it when you need a container but there isn't a more meaningful semantic element.

### `<section>`

Meaningful thematic grouping:

```html
<section>
    <h2>Our Services</h2>
    ...
</section>
```

Don't replace every `div` with `section`.

---

# 🔥 `<section>` vs `<article>`

Ask yourself:

### Question 1

**Does this represent a distinct topic/group within the page?**

→ `<section>`

### Question 2

**Could this content stand alone or be distributed independently?**

→ `<article>`

---

# 🔥 `<nav>` vs `<header>`

They are not interchangeable.

You can have:

```html
<header>

    <h1>My Website</h1>

    <nav>
        ...
    </nav>

</header>
```

Here:

```text
<header>
    → introductory area

<nav>
    → navigation area
```

---

# 🔥 `<main>` vs `<section>`

`<main>` identifies the **primary content of the entire page**.

`<section>` identifies a **thematic group inside the document**.

Example:

```html
<main>

    <section>
        <h2>About Me</h2>
    </section>

    <section>
        <h2>Projects</h2>
    </section>

</main>
```

So:

```text
main
├── section
├── section
└── section
```

---

# 🔥 `<aside>` vs `<section>`

`<section>`:

> This is part of the main thematic content.

`<aside>`:

> This is related/secondary content.

Example:

```html
<main>

    <article>
        <h1>HTML Tutorial</h1>
        <p>...</p>
    </article>

    <aside>
        <h2>Related Tutorials</h2>
        ...
    </aside>

</main>
```

---

# 🏗️ Real-World Semantic HTML Structure

Here's a professional-style example:

```html
<!DOCTYPE html>

<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0"
    >

    <title>My Blog</title>

</head>

<body>

    <header>

        <h1>My Blog</h1>

        <nav>
            <ul>
                <li>
                    <a href="/">Home</a>
                </li>

                <li>
                    <a href="/articles">Articles</a>
                </li>

                <li>
                    <a href="/about">About</a>
                </li>
            </ul>
        </nav>

    </header>


    <main>

        <section>

            <h2>Latest Articles</h2>

            <article>

                <header>
                    <h3>Learning HTML</h3>

                    <p>
                        Published
                        <time datetime="2026-09-06">
                            September 6, 2026
                        </time>
                    </p>
                </header>

                <figure>

                    <img
                        src="html.jpg"
                        alt="HTML code displayed on a computer screen"
                    >

                    <figcaption>
                        Learning the fundamentals of HTML.
                    </figcaption>

                </figure>

                <p>
                    HTML provides the structure of a web page.
                </p>

                <footer>

                    <address>
                        Written by
                        <a href="mailto:john@example.com">
                            John Smith
                        </a>
                    </address>

                </footer>

            </article>

        </section>


        <aside>

            <h2>Related Articles</h2>

            <ul>
                <li>
                    <a href="/css">
                        Learn CSS
                    </a>
                </li>

                <li>
                    <a href="/javascript">
                        Learn JavaScript
                    </a>
                </li>
            </ul>

        </aside>

    </main>


    <footer>

        <p>
            © 2026 My Blog
        </p>

        <address>
            <a href="mailto:hello@example.com">
                hello@example.com
            </a>
        </address>

    </footer>

</body>

</html>
```

---

# 🧠 Understand the Structure

The important part is this:

```text
html
│
├── head
│
└── body
    │
    ├── header
    │   ├── h1
    │   └── nav
    │
    ├── main
    │   │
    │   ├── section
    │   │   │
    │   │   └── article
    │   │       ├── header
    │   │       ├── figure
    │   │       │   └── figcaption
    │   │       └── footer
    │   │
    │   └── aside
    │
    └── footer
```

If you understand this tree, you've understood the **core of semantic HTML**.

---

# 🎯 Interview Questions You Must Know

### Q1. What is semantic HTML?

Use meaningful HTML elements that describe their purpose.

---

### Q2. Why use semantic HTML?

Main reasons:

```text
Accessibility
SEO
Readability
Maintainability
Clear document structure
```

---

### Q3. `<div>` vs `<section>`?

`div` is a generic container.

`section` represents a meaningful thematic grouping.

---

### Q4. `<section>` vs `<article>`?

`section` = thematic grouping.

`article` = self-contained content that can stand on its own.

---

### Q5. What is `<aside>`?

Related or secondary content that is separate from the main flow.

---

### Q6. What is `<main>`?

The primary content of the document.

---

### Q7. Can a page have multiple `<header>` elements?

**Yes.**

For example, the page can have a header and individual articles/sections can have their own headers.

---

### Q8. Can a page have multiple `<footer>` elements?

**Yes.**

A page can have a page-level footer, and articles/sections can have their own footers.

---

### Q9. Is `<header>` the same as `<head>`?

**No.**

```text
<head>   → metadata/resources
<header> → visible introductory content
```

---

### Q10. Does `<nav>` mean every link must be inside it?

**No.**

`<nav>` is for significant navigation sections.

---

# 🚨 Common Beginner Mistakes

### ❌ Everything is a `<div>`

```html
<div>
    <div>
        <div>My Blog</div>
    </div>
</div>
```

Prefer meaningful elements where appropriate:

```html
<header>
    <nav>
        ...
    </nav>
</header>
```

---

### ❌ Using `<section>` just for styling

```html
<section class="red-box">
    Hello
</section>
```

If there's no meaningful thematic section, a `<div>` may be more appropriate.

---

### ❌ Using `<article>` for every card

A UI card isn't automatically an `<article>`.

Ask:

> Is this content independently meaningful/distributable?

If yes, `<article>` may make sense.

If it's simply a visual component, `<div>` may be perfectly appropriate.

---

### ❌ Using `<aside>` just because something is on the side

`aside` is about **semantic relationship**, not physical position.

---

### ❌ Using `<br>` for layout

Don't do:

```html
<header>
    My Website
    <br>
    <br>
    <br>
</header>
```

Use CSS for spacing.

---

# 🧪 Your Level 3 Practice Project

Build a **Blog Website** using only HTML.

Structure it like this:

```text
Website
│
├── header
│   ├── h1
│   └── nav
│
├── main
│   │
│   ├── section
│   │   │
│   │   ├── article
│   │   │   ├── header
│   │   │   ├── figure
│   │   │   │   └── figcaption
│   │   │   └── footer
│   │   │
│   │   └── article
│   │
│   └── aside
│
└── footer
    └── address
```

Use all of these:

```text
<header>
<nav>
<main>
<section>
<article>
<aside>
<footer>
<figure>
<figcaption>
<time>
<address>
```

### ⭐ The most important mental model

Don't memorize semantic tags as isolated definitions.

Think about a real page:

```text
                    PAGE
                      │
       ┌──────────────┴──────────────┐
       │                             │
    HEADER                         MAIN
       │                             │
      NAV                     ┌──────┴──────┐
                              │             │
                           SECTION        ASIDE
                              │
                           ARTICLE
                         ┌────┼────┐
                      HEADER FIGURE FOOTER
                             │
                        FIGCAPTION
```

Once you can look at a website and decide **"this should be `<article>`, this should be `<section>`, this is `<aside>`, and this is just a `<div>`"**, you've genuinely understood semantic HTML.