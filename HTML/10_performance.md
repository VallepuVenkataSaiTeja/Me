Absolutely. Now we move to **🔴 Level 10 — Performance ⭐⭐**.

This section is especially useful for frontend interviews because interviewers often ask questions like:

* `async` vs `defer`?
* What does `loading="lazy"` do?
* What is preload?
* What is prefetch?
* How do responsive images improve performance?
* How would you optimize images?
* Why can too many scripts slow down a page?

---

# 🔴 Level 10 — HTML Performance ⭐⭐

The basic goal is:

> **Send fewer resources, send appropriately sized resources, and avoid blocking the browser unnecessarily.**

Your HTML can have a major impact on how quickly a page becomes usable.

---

# 115. `async`

`async` is an attribute used with external `<script>` elements.

Example:

```html
<script
    src="analytics.js"
    async
></script>
```

It tells the browser that the script can be **downloaded without blocking HTML parsing**.

---

## Without `async`

Consider:

```html
<script src="app.js"></script>
```

Conceptually:

```text
HTML parsing
     ↓
encounter script
     ↓
download script
     ↓
execute script
     ↓
continue HTML parsing
```

The parser is blocked while the classic script is fetched/executed.

---

## With `async`

```html
<script
    src="analytics.js"
    async
></script>
```

Conceptually:

```text
HTML parsing ────────────────→ continues
                 \
                  ↓
              download
                  ↓
              execute
```

The download happens in parallel with HTML parsing.

When the script is ready, the browser can execute it, potentially interrupting parsing at that point.

---

# Important property of `async`

If you have:

```html
<script async src="one.js"></script>
<script async src="two.js"></script>
```

**Do not assume they execute in document order.**

They execute when their downloads are ready.

For example:

```text
two.js downloads first
       ↓
two.js executes

one.js downloads later
       ↓
one.js executes
```

So `async` is good for **independent scripts**.

Examples:

* analytics
* metrics
* independent third-party functionality

It is usually not appropriate when:

```text
script B depends on script A
```

---

# 116. `defer`

`defer` is also used with external classic scripts.

```html
<script
    src="app.js"
    defer
></script>
```

The browser can download the script while continuing to parse HTML.

But deferred scripts execute **after the document has been parsed**, and classic deferred scripts preserve their document order.

Conceptually:

```text
HTML parsing ────────────────→ complete
       │
       └── download app.js ──→
                                ↓
                         execute deferred script
```

---

# `async` vs `defer`

This is one of the **most important Level 10 interview questions**.

| Feature                                    | `async`           | `defer`   |
| ------------------------------------------ | ----------------- | --------- |
| Downloads while HTML parses                | ✅                 | ✅         |
| Blocks parser during download              | ❌                 | ❌         |
| Execution waits for HTML parsing to finish | ❌                 | ✅         |
| Execution order preserved                  | ❌                 | ✅         |
| Good for independent scripts               | ✅                 | Sometimes |
| Good for scripts depending on DOM          | Usually not ideal | ✅         |

### Memory trick

```text
async
  ↓
"Execute whenever ready."

defer
  ↓
"Wait until HTML parsing is done."
```

---

# Example

### `async`

```html
<script
    async
    src="analytics.js"
></script>
```

Good candidate because analytics may not depend on your page's other scripts.

### `defer`

```html
<script
    defer
    src="app.js"
></script>
```

Good for application code that needs the document to have been parsed.

---

# Important interview nuance

`async` and `defer` primarily matter for **classic external scripts**.

For module scripts:

```html
<script
    type="module"
    src="app.js"
></script>
```

module scripts are deferred by default.

---

# 117. `<script>`

The `<script>` element is used to embed or reference JavaScript.

Example:

```html
<script src="app.js"></script>
```

Or inline:

```html
<script>
    console.log("Hello");
</script>
```

---

# External vs inline JavaScript

### External

```html
<script src="app.js"></script>
```

Advantages include:

* caching
* separation of concerns
* maintainability
* reuse

### Inline

```html
<script>
    console.log("Hello");
</script>
```

Useful for small pieces of code, but large application logic is generally kept in external files.

---

# Where should scripts go?

Historically, scripts were often placed at the bottom of `<body>`:

```html
<body>

    ...

    <script src="app.js"></script>
</body>
```

This allowed much of the HTML to be parsed before the script blocked parsing.

With modern HTML, a common approach is:

```html
<head>
    <script
        src="app.js"
        defer
    ></script>
</head>
```

This allows the browser to discover the script early while deferring its execution until HTML parsing is complete.

---

# Classic script behavior

For:

```html
<script src="app.js"></script>
```

the browser generally:

```text
Parse HTML
   ↓
Encounter script
   ↓
Fetch script
   ↓
Execute script
   ↓
Continue parsing
```

That can delay page parsing.

---

# Why can JavaScript hurt performance?

JavaScript can:

* block parsing in some cases
* consume CPU
* create large JavaScript bundles
* execute expensive code
* cause layout/style work
* delay interactivity

Therefore, don't load and execute unnecessary JavaScript.

---

# 118. Lazy Loading

Lazy loading means:

> **Don't load a resource until it is likely to be needed.**

Imagine a page containing:

```text
Top of page
   ↓
Hero image
   ↓
10 articles
   ↓
20 images
   ↓
Footer
```

The user initially sees only the top portion.

Loading all 20 images immediately may waste bandwidth.

Lazy loading allows off-screen resources to be loaded closer to when they are needed.

---

# Why lazy loading helps

Potential benefits:

* less initial network traffic
* faster initial page loading
* lower bandwidth usage
* less work during initial rendering

---

# Common use case

```html
<img
    src="large-image.jpg"
    loading="lazy"
    alt="Mountain"
>
```

The browser can defer loading the image until it approaches the viewport.

---

# 119. `loading="lazy"`

The `loading` attribute can be used for resources such as images and iframes.

Example:

```html
<img
    src="product.jpg"
    loading="lazy"
    alt="Black backpack"
>
```

For an iframe:

```html
<iframe
    src="https://example.com"
    loading="lazy"
    title="Example content"
></iframe>
```

---

# `loading="lazy"` vs `loading="eager"`

### Lazy

```html
loading="lazy"
```

Requests loading later when appropriate.

### Eager

```html
loading="eager"
```

Requests normal/immediate loading behavior.

---

# Should every image be lazy-loaded?

**No.**

This is an important interview trap.

You generally don't want to lazily load an image that is critical to the initial view.

For example, a prominent hero/LCP image may need to be available quickly.

Instead:

```html
<img
    src="hero.jpg"
    alt="..."
>
```

while below-the-fold images may use:

```html
<img
    src="article.jpg"
    loading="lazy"
    alt="..."
>
```

---

# Simple rule

```text
Above the fold / critical
        ↓
Don't blindly lazy-load

Below the fold
        ↓
loading="lazy" is often useful
```

---

# 120. `preload`

`preload` tells the browser:

> **This resource is important for the current page; fetch it early.**

It is commonly used with `<link>`.

Example:

```html
<link
    rel="preload"
    href="/fonts/my-font.woff2"
    as="font"
    type="font/woff2"
    crossorigin
>
```

---

# Why use preload?

Suppose a resource is discovered relatively late but is important to the initial page.

Preload can tell the browser about it earlier.

Common candidates include:

* important fonts
* critical images
* important stylesheets
* certain media resources

---

# Image preload example

```html
<link
    rel="preload"
    as="image"
    href="/images/hero.webp"
>
```

The browser can start fetching that important image earlier.

---

# Important: don't preload everything

This is a common mistake:

```text
preload
preload
preload
preload
preload
preload
```

If everything is marked high priority, you've defeated the purpose.

Preload should be used for **resources that are genuinely important to the current page's early rendering**.

---

# `preload` vs `loading="lazy"`

They have opposite intentions.

```text
preload
   ↓
"Get this important resource early."

lazy loading
   ↓
"Don't get this until it's needed."
```

---

# 121. `prefetch`

`prefetch` tells the browser:

> **This resource may be useful for a future navigation or future use.**

Example:

```html
<link
    rel="prefetch"
    href="/dashboard.html"
>
```

The idea is:

```text
Current page
     ↓
User may click Dashboard later
     ↓
Browser can potentially fetch dashboard resource ahead of time
```

---

# `preload` vs `prefetch`

Very important interview question.

|                 | `preload`      | `prefetch`            |
| --------------- | -------------- | --------------------- |
| Purpose         | Current page   | Future navigation/use |
| Priority intent | More important | Lower-priority/future |
| Mental model    | "Need soon"    | "Might need later"    |

### Memory trick

```text
PRELOAD
   ↓
Load it before it's normally discovered/needed.

PREFETCH
   ↓
Fetch it because I may need it later.
```

---

# Don't confuse preload with prefetch

### Current page:

```html
<link
    rel="preload"
    as="image"
    href="/hero.webp"
>
```

### Potential future page:

```html
<link
    rel="prefetch"
    href="/next-page.html"
>
```

---

# 122. Responsive Images

You learned this in Level 7, but it is extremely important for performance.

The problem:

Suppose a phone displays an image at:

```text
300px wide
```

but you send:

```text
2400px wide image
```

You're potentially transferring much more data than necessary.

---

# `srcset`

Provide multiple image sizes:

```html
<img
    src="image-800.jpg"
    srcset="
        image-400.jpg 400w,
        image-800.jpg 800w,
        image-1200.jpg 1200w
    "
    sizes="100vw"
    alt="Mountain landscape"
>
```

The browser can select an appropriate candidate.

---

# Why responsive images improve performance

Instead of:

```text
Every device
     ↓
huge.jpg
```

you can provide:

```text
Small screen → smaller image
Medium       → medium image
Large        → larger image
```

Conceptually:

```text
          Responsive Images

Phone ───────→ 400px image
Tablet ──────→ 800px image
Desktop ─────→ 1200px image
```

This can significantly reduce unnecessary image bytes.

---

# `sizes`

For width-descriptor `srcset`, `sizes` helps the browser estimate how large the image will appear.

Example:

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

Think:

```text
srcset → "Here are the files I have."

sizes → "Here's roughly how wide I expect the image to appear."

Browser → "I'll choose an appropriate file."
```

---

# `<picture>` for art direction

Sometimes the issue isn't resolution.

You might want a different crop.

```html
<picture>

    <source
        media="(max-width: 600px)"
        srcset="portrait-crop.jpg"
    >

    <img
        src="landscape-crop.jpg"
        alt="Person standing on a mountain"
    >

</picture>
```

This is **art direction**.

---

# 123. Image Optimization

Images are often among the largest resources on a webpage.

Optimizing them can have a major performance impact.

---

# 1. Choose appropriate dimensions

Don't upload:

```text
4000 × 3000
```

if the page only needs:

```text
400 × 300
```

Resize images appropriately.

---

# 2. Choose an appropriate format

Common formats include:

```text
JPEG
PNG
WebP
AVIF
SVG
```

General tendencies:

### JPEG

Good for:

* photographs
* complex images

### PNG

Useful when you need:

* lossless image data
* transparency
* graphics where PNG is appropriate

### WebP

Modern image format with broad browser support and useful compression characteristics.

### AVIF

Modern image format that can provide strong compression and image quality, depending on the image and encoding settings.

### SVG

Excellent for:

* logos
* icons
* diagrams
* vector graphics

---

# 3. Compress images

Example:

```text
Original:
4 MB

Optimized:
500 KB
```

The exact savings depend heavily on the image and encoding settings.

The goal is to reduce file size while maintaining acceptable visual quality.

---

# 4. Use responsive images

Instead of:

```html
<img src="huge-image.jpg">
```

use:

```html
<img
    src="medium.jpg"
    srcset="
        small.jpg 400w,
        medium.jpg 800w,
        large.jpg 1200w
    "
    sizes="100vw"
    alt="Landscape"
>
```

---

# 5. Lazy-load non-critical images

```html
<img
    src="article-image.jpg"
    loading="lazy"
    alt="Article illustration"
>
```

Useful when the image is below the initial viewport.

---

# 6. Don't lazy-load everything

For an important hero image:

```html
<img
    src="hero.webp"
    alt="..."
>
```

You may instead optimize its priority through appropriate resource loading strategies rather than delaying it.

---

# 7. Specify dimensions

Remember this from responsive images:

```html
<img
    src="photo.jpg"
    width="800"
    height="600"
    alt="Mountain landscape"
>
```

Why?

The browser can reserve the appropriate space before the image finishes loading.

That can help reduce **layout shifts**.

---

# 8. Use CSS for responsive display

For example:

```css
img {
    max-width: 100%;
    height: auto;
}
```

This lets an image shrink within its container.

---

# 🔥 Image Performance Example

Suppose your webpage has:

```text
Hero image       2.5 MB
Article image 1  1.5 MB
Article image 2  1.7 MB
Article image 3  1.2 MB
Article image 4  1.4 MB
```

Total:

```text
8.3 MB
```

That's potentially a lot for a page's images.

You could improve it with:

```text
1. Resize images
2. Compress images
3. Use modern formats where appropriate
4. Use srcset
5. Use sizes
6. Lazy-load below-the-fold images
7. Optimize the critical hero image
```

---

# 🔥 Complete Performance-Oriented Example

```html
<!DOCTYPE html>

<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0"
    >

    <title>Performance Optimized Page</title>

    <!-- Important font -->
    <link
        rel="preload"
        href="/fonts/inter.woff2"
        as="font"
        type="font/woff2"
        crossorigin
    >

    <!-- JavaScript -->
    <script
        src="/app.js"
        defer
    ></script>

</head>

<body>

    <header>

        <!-- Critical/hero image -->
        <img
            src="/images/hero-800.webp"
            srcset="
                /images/hero-400.webp 400w,
                /images/hero-800.webp 800w,
                /images/hero-1200.webp 1200w
            "
            sizes="100vw"
            width="1200"
            height="600"
            alt="Developer working at a desk"
        >

    </header>

    <main>

        <article>

            <h1>Frontend Performance</h1>

            <p>
                Learn how to optimize your HTML for performance.
            </p>

            <!-- Below-the-fold image -->
            <img
                src="/images/example-800.webp"
                srcset="
                    /images/example-400.webp 400w,
                    /images/example-800.webp 800w
                "
                sizes="100vw"
                width="800"
                height="500"
                loading="lazy"
                alt="Performance optimization example"
            >

        </article>

    </main>

</body>

</html>
```

This demonstrates several performance principles:

```text
defer
  ↓
Don't block HTML parsing unnecessarily

preload
  ↓
Fetch an important resource early

srcset + sizes
  ↓
Choose an appropriate image resource

width + height
  ↓
Reserve image space

loading="lazy"
  ↓
Delay non-critical image loading
```

---

# 🧠 `async` vs `defer` — Memorize This

This is probably the **#1 interview topic in this section**.

```text
                    SCRIPT
                      │
             ┌────────┴────────┐
             │                 │
           async             defer
             │                 │
       Download parallel   Download parallel
             │                 │
       Execute when ready  Wait for HTML parsing
             │                 │
       Order NOT guaranteed  Order preserved
             │                 │
       Independent scripts   DOM-dependent scripts
```

Example:

```html
<script async src="analytics.js"></script>

<script defer src="app.js"></script>
```

---

# 🧠 `preload` vs `prefetch`

Another important one:

```text
                RESOURCE HINTS
                      │
             ┌────────┴────────┐
             │                 │
          preload           prefetch
             │                 │
       Current page        Future need
             │                 │
          Important          Maybe useful
             │                 │
          "Need soon"       "Might need later"
```

---

# 🧠 Lazy Loading vs Preload

They have almost opposite goals:

```text
PRELOAD
   ↓
"Get this important thing early."

LAZY
   ↓
"Wait until this thing is actually needed."
```

Don't blindly combine them for the same resource.

---

# 🎯 Most Important Interview Questions

### Q1. What is `async`?

It allows an external classic script to download without blocking HTML parsing and execute as soon as it is ready.

---

### Q2. What is `defer`?

It allows an external classic script to download while HTML parsing continues, then executes it after document parsing, preserving order among deferred classic scripts.

---

### Q3. `async` vs `defer`?

```text
async  → execute when ready
defer  → execute after parsing
```

And:

```text
async  → execution order isn't guaranteed
defer  → order is preserved
```

---

### Q4. What is lazy loading?

Deferring the loading of resources until they're likely to be needed.

---

### Q5. What does `loading="lazy"` do?

It gives the browser permission to defer loading of an image or iframe until it approaches being needed/visible.

---

### Q6. Should all images use `loading="lazy"`?

**No.**

Critical above-the-fold images should not be blindly lazy-loaded.

---

### Q7. What is preload?

A resource hint telling the browser that a resource is important for the current page and should be fetched early.

---

### Q8. What is prefetch?

A resource hint indicating that a resource may be useful in the future, such as during a later navigation.

---

### Q9. Preload vs prefetch?

```text
preload  → current page
prefetch → future page/use
```

---

### Q10. How do responsive images improve performance?

They allow the browser to select an appropriately sized image instead of unnecessarily downloading a much larger image.

---

### Q11. What is `srcset`?

It provides multiple image resources so the browser can choose an appropriate candidate based on the rendering conditions.

---

### Q12. What is `sizes`?

It describes the expected rendered width of an image under different viewport conditions, helping the browser choose from `srcset`.

---

### Q13. How do you optimize images?

A good answer:

> "I would use appropriate dimensions, compress images, choose suitable formats such as WebP or AVIF where appropriate, use responsive images with `srcset` and `sizes`, lazy-load non-critical images, provide width and height to help reserve layout space, and prioritize critical images."

---

# 🚨 Common Performance Mistakes

## ❌ Mistake 1: Making every script synchronous

```html
<script src="analytics.js"></script>
<script src="chat.js"></script>
<script src="app.js"></script>
```

Depending on the application, this can introduce unnecessary parser blocking.

Consider whether scripts should be:

```html
<script defer src="app.js"></script>
```

or:

```html
<script async src="analytics.js"></script>
```

---

## ❌ Mistake 2: Using `async` for dependent scripts

```html
<script async src="library.js"></script>
<script async src="app.js"></script>
```

If `app.js` depends on `library.js`, this is dangerous because execution order isn't guaranteed.

---

## ❌ Mistake 3: Lazy-loading the hero image

```html
<img
    src="hero.jpg"
    loading="lazy"
    alt="Hero"
>
```

Don't automatically lazy-load critical above-the-fold content.

---

## ❌ Mistake 4: Preloading everything

```text
preload everything
       ↓
too many high-priority requests
       ↓
resource contention
```

Preload should be selective.

---

## ❌ Mistake 5: Serving a huge image to a phone

```html
<img src="4000px-image.jpg">
```

when the phone only needs a small version.

Prefer responsive images.

---

## ❌ Mistake 6: No image dimensions

```html
<img src="photo.jpg" alt="Photo">
```

Providing:

```html
width="800"
height="600"
```

can help the browser reserve space for the image.

---

# 🏆 The Performance Formula

For HTML performance, remember:

```text
                PERFORMANCE
                     │
       ┌─────────────┼─────────────┐
       │             │             │
    JavaScript     Images       Resources
       │             │             │
   async/defer   srcset/sizes   preload
       │             │             │
    scripts      lazy loading    prefetch
                     │
                 compression
                     │
                  formats
```

Or even simpler:

> **Don't block unnecessarily + don't download unnecessarily + don't download more than you need.**

That single principle explains a huge part of frontend performance optimization.