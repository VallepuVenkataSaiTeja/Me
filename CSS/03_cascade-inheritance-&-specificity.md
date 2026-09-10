# 3. Cascade, Inheritance & Specificity ⭐⭐⭐

This is one of the **most important CSS topics for interviews** because in real projects, you will often have **multiple CSS rules trying to style the same element**.

For example:

```html
<p class="text" id="para">Hello</p>
```

And:

```css
p {
    color: red;
}

.text {
    color: blue;
}

#para {
    color: green;
}
```

Which color will the paragraph have?

**Green.**

Why?

Because CSS has rules that determine **which style wins**.

To understand this, you need to understand:

1. Cascade
2. Inheritance
3. Specificity
4. Source order
5. `!important`

Let's go one by one.

---

# 1. What is the Cascade?

The word **Cascading** in CSS means that when multiple CSS rules apply to the same element, the browser has a system for deciding **which rule should win**.

Consider:

```html
<p>Hello World</p>
```

CSS:

```css
p {
    color: red;
}

p {
    color: blue;
}
```

Both rules target the same `<p>`.

So which color wins?

```text
red ❌
blue ✅
```

The paragraph becomes **blue**.

Why?

Because the second rule comes later.

This is called **source order**, which is one part of the cascade.

---

# 2. Why Do We Need the Cascade?

Imagine a large website.

You might have:

```css
p {
    color: black;
}
```

Later, a specific section might need:

```css
p {
    color: white;
}
```

And perhaps one special paragraph needs:

```css
p {
    color: red;
}
```

CSS needs a way to determine which rule should apply.

The cascade considers things such as:

```text
Importance
   ↓
Origin
   ↓
Specificity
   ↓
Source order
```

For the level you need right now, the most important practical concepts are:

```text
Specificity
    ↓
Source order
```

and understanding `!important`.

---

# 3. Simple Example of Cascade

```css
p {
    color: red;
}

p {
    color: blue;
}
```

Both selectors have the same specificity.

Therefore, the later rule wins:

```css
p {
    color: blue;
}
```

Result:

```text
Paragraph → BLUE
```

---

# 4. What is Inheritance?

**Inheritance** means some CSS properties can be passed from a parent element to its child elements.

For example:

```html
<div>
    <p>Hello</p>
</div>
```

CSS:

```css
div {
    color: blue;
}
```

You didn't directly give the `<p>` a color.

But:

```text
div
 ↓
p
```

The `<p>` can inherit the `color` from its parent.

So:

```text
Hello → blue
```

---

# 5. Parent and Child

Consider:

```html
<div class="parent">

    <p>Hello</p>

</div>
```

If we write:

```css
.parent {
    color: red;
}
```

The `<p>` can inherit the red text color.

```text
.parent
   │
   └── p
       ↓
      red
```

This is **inheritance**.

---

# 6. Which Properties Are Commonly Inherited?

Some properties commonly inherit:

```css
color
font-family
font-size
font-weight
line-height
text-align
```

For example:

```css
body {
    font-family: Arial;
    color: black;
}
```

Many elements inside the `<body>` can inherit these values.

That's why developers often write:

```css
body {
    font-family: Arial, sans-serif;
}
```

instead of setting the font on every individual element.

---

# 7. Not Everything Is Inherited

This is very important.

Properties such as:

```css
margin
padding
border
width
height
background
```

generally **do not inherit automatically**.

For example:

```css
.parent {
    padding: 20px;
}
```

The child does **not automatically get `padding: 20px`**.

So:

```text
color       → commonly inherited
font-family → commonly inherited

margin      → not inherited
padding     → not inherited
border      → not inherited
width       → not inherited
```

Don't try to memorize every property right now. Just understand the concept.

---

# 8. The `inherit` Value

CSS also provides the `inherit` keyword.

Suppose:

```html
<div class="parent">
    <p>Hello</p>
</div>
```

CSS:

```css
.parent {
    color: red;
}

p {
    color: inherit;
}
```

Now you're explicitly telling the `<p>`:

> Take the `color` from my parent.

Result:

```text
Parent → red
   ↓
Child  → red
```

---

# 9. `initial`

CSS also has:

```css
initial
```

It resets a property to its **initial/default CSS value**.

Example:

```css
p {
    color: initial;
}
```

You don't need to use this frequently as a beginner, but you should know it exists.

---

# 10. `unset`

Another useful value is:

```css
unset
```

It essentially means:

> If the property normally inherits, inherit it. Otherwise, use its initial value.

For interviews, knowing that `inherit`, `initial`, and `unset` exist is enough initially.

---

# 11. What is Specificity? ⭐⭐⭐

**Specificity determines how specific a CSS selector is.**

Suppose:

```html
<p class="text" id="para">Hello</p>
```

CSS:

```css
p {
    color: red;
}

.text {
    color: blue;
}

#para {
    color: green;
}
```

All three rules target the same paragraph.

But:

```text
p          → less specific
.text      → more specific
#para      → even more specific
```

Therefore:

```text
#para wins
```

The text becomes:

**green**

---

# 12. Specificity Hierarchy

For the selectors you are learning, remember this order:

```text
ID
 ↓
Class / Attribute / Pseudo-class
 ↓
Element / Pseudo-element
```

In simple terms:

```text
#id       → strongest
.class    → medium
element   → weaker
```

For example:

```css
p {
    color: red;
}

.text {
    color: blue;
}

#para {
    color: green;
}
```

Result:

```text
#para → green ✅
```

---

# 13. Specificity Score

You will sometimes see specificity represented as:

```text
ID     Class     Element
 0       0          0
```

For example:

```css
p {
    color: red;
}
```

Specificity:

```text
0 - 0 - 1
```

Because there is:

```text
0 IDs
0 classes
1 element
```

---

### Class selector

```css
.text {
    color: blue;
}
```

Specificity:

```text
0 - 1 - 0
```

---

### ID selector

```css
#para {
    color: green;
}
```

Specificity:

```text
1 - 0 - 0
```

So:

```text
#para
1-0-0

.text
0-1-0

p
0-0-1
```

The ID wins.

---

# 14. Multiple Classes

Consider:

```css
.text {
    color: blue;
}

.text.large {
    color: red;
}
```

The second selector has:

```text
2 classes
```

So it is more specific.

```text
.text       → 0-1-0
.text.large → 0-2-0
```

Therefore:

```css
.text.large {
    color: red;
}
```

wins.

---

# 15. Combining Selectors

Consider:

```css
div p {
    color: red;
}
```

It has:

```text
1 element + 1 element
```

Specificity:

```text
0-0-2
```

Now:

```css
.text {
    color: blue;
}
```

Specificity:

```text
0-1-0
```

Which wins?

**`.text` wins.**

Why?

Because a class has greater specificity than an element selector.

So:

```text
div p    → 0-0-2
.text    → 0-1-0
```

Result:

```text
blue
```

---

# 16. Important Specificity Example ⭐

Consider:

```html
<div class="container">
    <p class="text">Hello</p>
</div>
```

CSS:

```css
p {
    color: red;
}

.container p {
    color: blue;
}

.container .text {
    color: green;
}
```

Let's calculate:

### `p`

```text
0-0-1
```

### `.container p`

```text
0-1-1
```

### `.container .text`

```text
0-2-0
```

Therefore:

```text
.container .text → wins
```

Result:

**green**

---

# 17. What is Source Order?

Source order means:

> If competing CSS rules have the same specificity, the rule that appears later generally wins.

Example:

```css
.text {
    color: red;
}

.text {
    color: blue;
}
```

Both have:

```text
0-1-0
```

Same specificity.

Therefore the later rule wins:

```text
blue ✅
```

---

# 18. Specificity vs Source Order ⭐⭐⭐

This is an important interview concept.

Consider:

```css
.text {
    color: blue;
}

#title {
    color: red;
}
```

HTML:

```html
<h1 id="title" class="text">Hello</h1>
```

Which one wins?

Even though `.text` appears first:

```text
.text  → 0-1-0
#title → 1-0-0
```

The ID is more specific.

Therefore:

**red wins.**

Now:

```css
#title {
    color: red;
}

#title {
    color: blue;
}
```

Both have:

```text
1-0-0
```

Same specificity.

Now source order matters.

The second rule wins:

**blue.**

### Remember:

```text
Different specificity
        ↓
More specific wins

Same specificity
        ↓
Later rule wins
```

---

# 19. What is `!important`? ⚠️

`!important` tells CSS that a declaration should receive **very high priority** within the cascade.

Example:

```css
p {
    color: red !important;
}

p {
    color: blue;
}
```

The paragraph becomes:

**red**

because:

```css
color: red !important;
```

has higher priority than the normal declaration.

---

# 20. Example of `!important`

```html
<p class="text">Hello</p>
```

```css
p {
    color: red;
}

.text {
    color: blue !important;
}
```

Even though `.text` is already more specific than `p`, `!important` makes the declaration explicitly important.

Result:

```text
blue
```

---

# 21. Should You Use `!important` Everywhere?

**No. ❌**

Avoid using it unless you have a good reason.

Bad:

```css
.button {
    color: white !important;
}

.title {
    font-size: 30px !important;
}

.card {
    padding: 20px !important;
}
```

This makes your CSS harder to maintain and harder to override later.

You can end up with:

```text
!important
   ↓
!important
   ↓
!important
   ↓
CSS becomes difficult to debug 😵
```

### Better approach

Use:

* Correct selectors
* Classes
* Appropriate specificity
* Proper CSS organization
* Source order

Use `!important` only when genuinely necessary.

---

# 22. `!important` Interview Point

Suppose:

```css
p {
    color: red !important;
}

#para {
    color: blue;
}
```

HTML:

```html
<p id="para">Hello</p>
```

What color?

**Red.**

Because the first declaration is `!important`.

This is a useful interview question.

---

# 23. Inline CSS and Specificity

Consider:

```html
<p id="para" class="text" style="color: orange;">
    Hello
</p>
```

And:

```css
#para {
    color: blue;
}
```

The inline style normally wins over the normal stylesheet rule.

So the result is:

**orange**

However, an important declaration can override a normal inline declaration:

```css
#para {
    color: blue !important;
}
```

Now:

**blue**

This is another reason not to casually use `!important`.

---

# 24. Universal Selector and Specificity

The universal selector:

```css
* {
    color: red;
}
```

has very low specificity.

It doesn't beat a class selector:

```css
* {
    color: red;
}

.text {
    color: blue;
}
```

Result:

**blue**

---

# 25. Attribute Selector Specificity

Remember from the previous topic:

```css
input[type="text"] {
    border: 1px solid blue;
}
```

An attribute selector has specificity similar to a class.

So:

```text
[type="text"] → 0-1-0
.class        → 0-1-0
```

---

# 26. Pseudo-class Specificity

Pseudo-classes such as:

```css
:hover
:focus
:nth-child()
:not()
```

also have class-level specificity.

For example:

```css
button:hover {
    background: blue;
}
```

Specificity:

```text
button → 0-0-1
:hover → 0-1-0

Total  → 0-1-1
```

You don't need to calculate every selector manually forever—the important thing is understanding the hierarchy.

---

# 27. Specificity Order You Should Remember

For the level you're currently learning:

```text
!important
    ↓
Inline style
    ↓
ID
    ↓
Class / Attribute / Pseudo-class
    ↓
Element / Pseudo-element
    ↓
Universal selector
```

**But one important clarification:** `!important` isn't simply another specificity level. It changes the cascade's priority, and competing `!important` declarations are then compared using origin/layer and specificity rules.

For normal interview questions, remember:

```text
!important → very high priority
inline      → very strong normal declaration
#id         → stronger selector
.class      → medium
element     → weaker
*           → very low
```

---

# 28. A Very Important Interview Example ⭐⭐⭐

HTML:

```html
<p id="message" class="text">Hello</p>
```

CSS:

```css
p {
    color: red;
}

.text {
    color: blue;
}

#message {
    color: green;
}

p {
    color: orange;
}
```

What is the final color?

### Step 1 — Find applicable rules

All four target the paragraph.

### Step 2 — Compare specificity

```text
p          → 0-0-1
.text      → 0-1-0
#message   → 1-0-0
p          → 0-0-1
```

The ID wins:

```css
#message {
    color: green;
}
```

### Final result:

🟢 **Green**

It doesn't matter that the last `p` rule says orange because the ID selector is more specific.

---

# 29. Another Interview Example

HTML:

```html
<p class="text">Hello</p>
```

CSS:

```css
.text {
    color: red;
}

.text {
    color: blue;
}
```

Both have the same specificity:

```text
0-1-0
```

So we use **source order**.

The second rule wins.

### Final:

🔵 **Blue**

---

# 30. Inheritance vs Cascade vs Specificity

These three terms are easy to confuse.

### Cascade

> Decides which competing CSS declarations win.

### Inheritance

> Allows certain properties to be passed from parent to child.

### Specificity

> Determines how strong a selector is when multiple rules target the same element.

Think:

```text
                 CSS
                  │
        ┌─────────┼─────────┐
        ↓         ↓         ↓
    Cascade   Inheritance  Specificity
        │                   │
   Which rule?          Which selector
    wins?               is stronger?
```

---

# 🎯 Interview Cheat Sheet

### What is CSS cascade?

> The cascade is the process CSS uses to determine which styles are applied when multiple declarations target the same element.

### What is inheritance?

> Inheritance allows certain CSS properties from a parent element to be passed down to its child elements.

### What is specificity?

> Specificity is the system used by CSS to determine which selector has higher priority when multiple selectors target the same element.

### What is source order?

> When competing rules have the same specificity, the rule that appears later in the CSS generally wins.

### What is `!important`?

> `!important` gives a declaration higher priority in the cascade. It should be used sparingly because excessive use makes CSS difficult to maintain.

---

# 🧠 Remember This

The most important things for you are:

```text
1. Cascade
   ↓
   Multiple rules can target the same element.

2. Inheritance
   ↓
   Some properties pass from parent → child.

3. Specificity
   ↓
   #id > .class > element

4. Source Order
   ↓
   Same specificity → later rule wins.

5. !important
   ↓
   Gives a declaration special high priority.
```

### One-line memory trick:

> **"Specificity decides the stronger selector; source order breaks a tie."**