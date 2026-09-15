# 15. CSS Variables (Custom Properties) ⭐⭐

CSS Variables are also called **CSS Custom Properties**.

They are very useful in modern frontend development, especially when working with **React**, because they make your CSS easier to maintain, reuse, and customize.

The main things you need to understand are:

* What CSS variables are
* Why we use them
* Creating variables with `--`
* Using variables with `var()`
* Global variables
* Local/component variables
* Fallback values
* Changing variables
* Variables with colors, spacing, fonts, etc.
* Dark mode/theming
* CSS variables vs normal CSS values
* Interview questions

---

# 1. What are CSS Variables?

Normally, you might write the same value many times:

```css
button {
    background-color: blue;
}

header {
    background-color: blue;
}

.card {
    border-color: blue;
}

a {
    color: blue;
}
```

If you later decide:

```text
blue → red
```

you have to change it in multiple places.

CSS variables solve this problem.

You define the value once:

```css
:root {
    --primary-color: blue;
}
```

Then use it:

```css
button {
    background-color: var(--primary-color);
}

header {
    background-color: var(--primary-color);
}

a {
    color: var(--primary-color);
}
```

Now if you change:

```css
--primary-color: red;
```

all those elements can update automatically.

### Simple memory

```text
CSS Variable
→ store a reusable CSS value
→ use it with var()
```

---

# 2. Syntax for Creating a CSS Variable

CSS custom properties start with **two hyphens**:

```css
--variable-name: value;
```

Example:

```css
:root {
    --primary-color: blue;
}
```

Here:

```text
--primary-color
```

is the variable name.

And:

```text
blue
```

is its value.

---

# 3. Using a CSS Variable

Use:

```css
var(--variable-name)
```

Example:

```css
button {
    background-color: var(--primary-color);
}
```

Complete example:

```css
:root {
    --primary-color: blue;
}

button {
    background-color: var(--primary-color);
}
```

So:

```text
--primary-color
        ↓
      blue
        ↓
var(--primary-color)
```

---

# 4. Why Do We Need CSS Variables?

Imagine a website has:

```text
Primary color → blue
Secondary color → gray
Spacing → 20px
Border radius → 10px
```

Without variables:

```css
button {
    background: blue;
    border-radius: 10px;
}

.card {
    border-radius: 10px;
}

.header {
    background: blue;
}

.footer {
    background: gray;
}
```

With variables:

```css
:root {
    --primary-color: blue;
    --secondary-color: gray;
    --border-radius: 10px;
    --spacing: 20px;
}
```

Then:

```css
button {
    background: var(--primary-color);
    border-radius: var(--border-radius);
    padding: var(--spacing);
}

.card {
    border-radius: var(--border-radius);
}

.header {
    background: var(--primary-color);
}
```

Now your design values are centralized.

---

# 5. `:root`

You'll frequently see:

```css
:root {
    --primary-color: blue;
}
```

`:root` represents the document's root element.

For a normal HTML document, this is essentially the `<html>` element.

Example:

```css
:root {
    --primary-color: #3498db;
    --secondary-color: #333;
    --spacing: 20px;
}
```

Variables defined on `:root` can normally be inherited and used throughout the document.

### Interview memory

> `:root` is commonly used to define global CSS custom properties.

---

# 6. Complete Example

HTML:

```html
<div class="card">
    <h2>React Course</h2>
    <p>Learn React JS.</p>
    <button>Enroll Now</button>
</div>
```

CSS:

```css
:root {
    --primary-color: #3498db;
    --text-color: #333;
    --card-padding: 20px;
    --radius: 10px;
}

.card {
    padding: var(--card-padding);
    border-radius: var(--radius);
    color: var(--text-color);
}

button {
    background-color: var(--primary-color);
    color: white;
    border-radius: var(--radius);
}
```

Now imagine you change:

```css
--primary-color: red;
```

The button automatically uses red.

---

# 7. CSS Variable Names

Variable names must begin with:

```text
--
```

Examples:

```css
--primary-color
--secondary-color
--font-size
--spacing
--border-radius
--header-height
```

You can use names that describe their purpose.

Good:

```css
--primary-color
```

Less useful:

```css
--color1
```

Prefer meaningful names.

---

# 8. Variables Can Store Different Types of Values

CSS variables aren't limited to colors.

### Color

```css
:root {
    --primary-color: blue;
}
```

### Font size

```css
:root {
    --heading-size: 32px;
}
```

### Spacing

```css
:root {
    --spacing: 20px;
}
```

### Border radius

```css
:root {
    --radius: 10px;
}
```

### Font family

```css
:root {
    --main-font: Arial, sans-serif;
}
```

Use them:

```css
h1 {
    font-size: var(--heading-size);
    font-family: var(--main-font);
}
```

---

# 9. Variables for a Design System

This is one of the biggest real-world benefits.

You can define:

```css
:root {
    --primary-color: #2563eb;
    --secondary-color: #64748b;

    --text-color: #222;
    --background-color: #fff;

    --spacing-small: 8px;
    --spacing-medium: 16px;
    --spacing-large: 24px;

    --radius-small: 5px;
    --radius-medium: 10px;
    --radius-large: 20px;
}
```

Then your website uses those values everywhere.

This creates a simple design system.

---

# 10. Local CSS Variables

Variables don't have to be global.

You can define one inside a specific element:

```css
.card {
    --card-color: blue;
}
```

Then use it inside that element:

```css
.card {
    --card-color: blue;
    border: 2px solid var(--card-color);
}
```

HTML:

```html
<div class="card">
    React Course
</div>
```

---

# 11. Variable Inheritance

CSS custom properties generally **inherit**.

Example:

```css
.parent {
    --main-color: blue;
}

.child {
    color: var(--main-color);
}
```

HTML:

```html
<div class="parent">
    <p class="child">Hello</p>
</div>
```

The child can use:

```text
--main-color
```

because the custom property is inherited from the parent.

This is a very important concept.

---

# 12. Global vs Local Variables

### Global

```css
:root {
    --primary-color: blue;
}
```

Available throughout the document unless overridden.

### Local

```css
.card {
    --primary-color: red;
}
```

The variable is scoped to that element and its descendants through inheritance.

Think:

```text
:root
→ global/default value

.component
→ local value
```

---

# 13. Overriding a CSS Variable

This is one of the most powerful features.

Start with:

```css
:root {
    --primary-color: blue;
}
```

Then:

```css
.card {
    --primary-color: red;
}
```

Inside `.card`:

```css
button {
    background-color: var(--primary-color);
}
```

The button inside the card can use:

```text
red
```

while buttons outside can still use:

```text
blue
```

---

# 14. Example of Variable Override

HTML:

```html
<div class="normal">
    <button>Normal Button</button>
</div>

<div class="special">
    <button>Special Button</button>
</div>
```

CSS:

```css
:root {
    --button-color: blue;
}

.special {
    --button-color: red;
}

button {
    background-color: var(--button-color);
}
```

Result:

```text
Normal Button  → blue

Special Button → red
```

This is very useful for component-based designs.

---

# 15. Fallback Values

What happens if a CSS variable isn't defined?

You can provide a fallback.

Syntax:

```css
var(--variable, fallback)
```

Example:

```css
button {
    background-color: var(--primary-color, blue);
}
```

Meaning:

```text
If --primary-color exists
        ↓
use it

Otherwise
        ↓
use blue
```

---

# 16. Fallback Example

```css
.card {
    color: var(--text-color, black);
}
```

If:

```css
--text-color
```

exists:

```text
use that value
```

Otherwise:

```text
use black
```

This is especially useful in reusable components.

---

# 17. Multiple Fallbacks

You can also create a fallback chain:

```css
color: var(--primary-color, var(--secondary-color, black));
```

Meaning:

```text
Try --primary-color
        ↓
if unavailable
Try --secondary-color
        ↓
if unavailable
Use black
```

You don't need to use this frequently, but understand how fallback works.

---

# 18. CSS Variables with `calc()`

CSS variables work very well with `calc()`.

For example:

```css
:root {
    --spacing: 20px;
}

.card {
    padding: calc(var(--spacing) * 2);
}
```

Result:

```text
20px × 2 = 40px
```

You will learn `calc()` in the next topic in your roadmap.

---

# 19. CSS Variables with Colors

Very common:

```css
:root {
    --primary-color: #2563eb;
    --danger-color: #dc2626;
    --success-color: #16a34a;
}
```

Then:

```css
.primary {
    background: var(--primary-color);
}

.danger {
    background: var(--danger-color);
}

.success {
    background: var(--success-color);
}
```

This makes color management much easier.

---

# 20. Dark Mode Using CSS Variables ⭐⭐⭐

This is one of the best real-world examples.

Define the default theme:

```css
:root {
    --background-color: white;
    --text-color: black;
    --card-color: #f5f5f5;
}
```

Then define dark theme:

```css
.dark-theme {
    --background-color: #121212;
    --text-color: white;
    --card-color: #222;
}
```

Use the variables:

```css
body {
    background-color: var(--background-color);
    color: var(--text-color);
}

.card {
    background-color: var(--card-color);
}
```

Now if an ancestor gets:

```html
<body class="dark-theme">
```

the variables change.

You don't have to rewrite every component's colors.

---

# 21. Why This is Useful in React

This becomes particularly useful in React applications.

Imagine:

```text
App
 ├── Navbar
 ├── Sidebar
 ├── CourseCard
 ├── StudentDashboard
 └── Footer
```

You could define:

```css
:root {
    --primary-color: #2563eb;
    --background-color: white;
    --text-color: #222;
}
```

Every component can use:

```css
color: var(--text-color);
background: var(--background-color);
```

If you change the theme variables, many components update automatically.

React can also add/remove a class such as:

```text
dark-theme
```

while CSS handles the visual theme.

This is a common combination of **React + CSS**.

---

# 22. CSS Variables vs SASS Variables

You may hear about:

```text
CSS variables
Sass variables
```

They are not exactly the same.

CSS variable:

```css
:root {
    --primary-color: blue;
}

button {
    color: var(--primary-color);
}
```

This exists in the browser and can be changed at runtime.

Sass variable:

```scss
$primary-color: blue;

button {
    color: $primary-color;
}
```

Sass variables are processed when Sass is compiled.

### Basic interview difference

```text
CSS custom property
→ browser/runtime
→ can be changed dynamically

Sass variable
→ preprocessor/compile time
```

For your current CSS roadmap, knowing this distinction is enough.

---

# 23. CSS Variables Can Change at Runtime

This is a major advantage.

For example:

```css
:root {
    --primary-color: blue;
}
```

JavaScript can change it:

```javascript
document.documentElement.style.setProperty(
    "--primary-color",
    "red"
);
```

Now:

```css
button {
    background: var(--primary-color);
}
```

will use red.

This is one reason CSS custom properties are useful for dynamic themes.

---

# 24. CSS Variable vs Normal CSS Property

Don't confuse:

```css
--primary-color: blue;
```

with:

```css
color: blue;
```

The first one **stores a custom value**.

The second one actually applies a CSS property.

Example:

```css
:root {
    --primary-color: blue;
}

button {
    color: var(--primary-color);
}
```

Here:

```text
--primary-color
→ stores blue

color
→ uses blue
```

---

# 25. CSS Variable With `font-size`

```css
:root {
    --heading-size: 36px;
}

h1 {
    font-size: var(--heading-size);
}
```

Later:

```css
:root {
    --heading-size: 40px;
}
```

All `h1` elements using that variable update.

---

# 26. CSS Variable With Border Radius

```css
:root {
    --radius: 12px;
}

.card {
    border-radius: var(--radius);
}

button {
    border-radius: var(--radius);
}

input {
    border-radius: var(--radius);
}
```

Now all components share the same radius.

---

# 27. CSS Variable With Spacing

```css
:root {
    --space: 20px;
}

.card {
    padding: var(--space);
}

.section {
    margin-bottom: var(--space);
}

button {
    padding: var(--space);
}
```

Again:

```text
change once
    ↓
multiple places update
```

---

# 28. A Real Website Example

Imagine your Inskill-style website has:

```text
Primary → Blue
Secondary → Red
Text → Dark Gray
Background → White
Card radius → 12px
```

You could write:

```css
:root {
    --primary-color: #2563eb;
    --secondary-color: #dc2626;
    --text-color: #333;
    --background-color: #fff;
    --card-radius: 12px;
}
```

Navbar:

```css
.navbar {
    background-color: var(--primary-color);
}
```

Buttons:

```css
.btn-primary {
    background-color: var(--primary-color);
}

.btn-danger {
    background-color: var(--secondary-color);
}
```

Cards:

```css
.card {
    background-color: var(--background-color);
    color: var(--text-color);
    border-radius: var(--card-radius);
}
```

If you later change:

```css
--primary-color: #dc2626;
```

the navbar and primary buttons automatically use the new color.

---

# 29. CSS Variables and Responsive Design

CSS variables can also change at different screen sizes.

Example:

```css
:root {
    --section-padding: 60px;
}

@media (max-width: 768px) {
    :root {
        --section-padding: 30px;
    }
}

.section {
    padding: var(--section-padding);
}
```

Desktop:

```text
60px
```

Mobile:

```text
30px
```

This keeps responsive styles organized.

---

# 30. Important Rule: Variable Names Are Case-Sensitive

These are different:

```css
--primary-color
--Primary-color
```

CSS custom property names are case-sensitive.

So be consistent with naming.

A common convention is:

```css
--primary-color
--secondary-color
--text-color
```

using lowercase and hyphens.

---

# 31. What Happens if a Variable Doesn't Exist?

Suppose:

```css
button {
    background: var(--button-color);
}
```

but:

```text
--button-color
```

has not been defined in the relevant scope.

The declaration may become invalid at computed-value time.

So use a fallback when appropriate:

```css
button {
    background: var(--button-color, blue);
}
```

Now you have a safe default.

---

# 32. CSS Variables Do Not Mean "Constants"

You may hear people casually call them constants, but technically CSS custom properties aren't immutable constants.

They can be:

* overridden
* inherited
* changed by media queries
* changed by JavaScript
* scoped to components

That's actually one of their biggest advantages.

---

# 33. CSS Variables + Hover

You can even change a variable during hover.

```css
button {
    --button-color: blue;
    background-color: var(--button-color);
}

button:hover {
    --button-color: red;
}
```

Now:

```text
normal → blue
hover  → red
```

This is a useful example of how custom properties participate in the cascade.

---

# 34. CSS Variables + Pseudo-elements

They also work with pseudo-elements.

```css
:root {
    --accent-color: red;
}

.title::after {
    content: "";
    display: block;
    width: 50px;
    height: 3px;
    background-color: var(--accent-color);
}
```

So the same variable can control your decorative elements too.

---

# 35. Best Practice for Variables

Instead of:

```css
:root {
    --blue: #2563eb;
    --red: #dc2626;
}
```

for many projects, it can be better to name values according to their **purpose**:

```css
:root {
    --primary-color: #2563eb;
    --danger-color: #dc2626;
    --text-color: #222;
}
```

Why?

Because later you may change the primary color from blue to purple.

Your components still say:

```css
background: var(--primary-color);
```

rather than depending on a literal color name.

---

# 36. Common Mistake

Don't do this:

```css
:root {
    --primary-color: blue;
}

button {
    background: --primary-color;
}
```

❌ Wrong.

You must use:

```css
button {
    background: var(--primary-color);
}
```

Remember:

```text
Create:
--name

Use:
var(--name)
```

---

# 37. Interview Questions ⭐⭐⭐

### 1. What are CSS variables?

> CSS variables, officially called custom properties, allow us to store reusable CSS values and use them throughout our stylesheets.

Example:

```css
:root {
    --primary-color: blue;
}

button {
    background: var(--primary-color);
}
```

---

### 2. How do you define a CSS variable?

Use two hyphens:

```css
--primary-color: blue;
```

---

### 3. How do you use a CSS variable?

Use:

```css
var(--primary-color)
```

---

### 4. Why use `:root`?

> `:root` is commonly used to define global custom properties that can be inherited and reused throughout the document.

---

### 5. Can CSS variables be overridden?

Yes.

```css
:root {
    --color: blue;
}

.card {
    --color: red;
}
```

The value can be different inside `.card`.

---

### 6. Can CSS variables have fallback values?

Yes.

```css
color: var(--text-color, black);
```

If `--text-color` isn't available, `black` is used.

---

### 7. Are CSS variables inherited?

Yes, custom properties generally inherit by default.

---

### 8. Can JavaScript change CSS variables?

Yes.

For example:

```javascript
document.documentElement.style.setProperty(
    "--primary-color",
    "red"
);
```

---

### 9. What is the difference between CSS variables and Sass variables?

```text
CSS custom properties
→ available at runtime
→ can be dynamically changed

Sass variables
→ processed during Sass compilation
```

---

# 38. CSS Variables Cheat Sheet ⭐

### Create

```css
:root {
    --primary-color: blue;
}
```

### Use

```css
button {
    background: var(--primary-color);
}
```

### Fallback

```css
button {
    background: var(--primary-color, blue);
}
```

### Local variable

```css
.card {
    --card-color: red;
}
```

### Use local variable

```css
.card {
    color: var(--card-color);
}
```

### Override

```css
.dark-theme {
    --background-color: #222;
}
```

### Responsive variable

```css
@media (max-width: 768px) {
    :root {
        --spacing: 20px;
    }
}
```

### JavaScript

```javascript
document.documentElement.style.setProperty(
    "--primary-color",
    "red"
);
```

---

# 39. Most Important Memory Trick

Remember these three things:

```text
1. Define
   --primary-color: blue;

2. Use
   var(--primary-color)

3. Global
   :root { ... }
```

And:

```text
CSS Variables
      ↓
Reusable values
      ↓
Colors
Spacing
Font sizes
Border radius
Themes
Responsive values
      ↓
Easy maintenance
```

---

# 40. What You Actually Need for Interviews

Don't try to memorize every advanced custom-property feature.

Focus strongly on:

```text
⭐⭐⭐

--variable-name
var(--variable-name)
:root
Inheritance
Overriding variables
Fallback values
Dark mode/theme
```

And understand this practical pattern:

```css
:root {
    --primary-color: #2563eb;
    --text-color: #222;
    --radius: 10px;
}

.card {
    color: var(--text-color);
    border-radius: var(--radius);
}

button {
    background: var(--primary-color);
    border-radius: var(--radius);
}
```

If an interviewer asks **"Why are CSS variables useful?"**, a strong answer is:

> **They allow us to define reusable CSS values, reduce repetition, make themes easier to manage, and allow values to be overridden or changed dynamically.**
