# 🟡 Level 5 — HTML Tables ⭐⭐

Tables are used to represent **tabular data** — information arranged into **rows and columns**.

Examples:

* Employee lists
* Product comparisons
* Student marks
* Invoices
* Sales reports
* Pricing tables
* Schedules
* Statistics

> **Important:** Tables are for **data**, not for creating the layout of a webpage. For layout, use CSS Flexbox/Grid.

---

# 64. `<table>`

The `<table>` element is the main container for a table.

Basic example:

```html
<table>
    ...
</table>
```

A complete simple table:

```html
<table>
    <tr>
        <th>Name</th>
        <th>Age</th>
    </tr>

    <tr>
        <td>John</td>
        <td>25</td>
    </tr>

    <tr>
        <td>Sarah</td>
        <td>28</td>
    </tr>
</table>
```

Conceptually:

```text
┌──────────┬─────┐
│ Name     │ Age │
├──────────┼─────┤
│ John     │ 25  │
│ Sarah    │ 28  │
└──────────┴─────┘
```

The `<table>` itself doesn't represent a particular cell.

It contains the table structure.

---

# 65. `<tr>`

`<tr>` means:

> **Table Row**

It creates one row.

Example:

```html
<tr>
    <td>John</td>
    <td>25</td>
</tr>
```

Conceptually:

```text
┌──────────┬─────┐
│ John     │ 25  │  ← one <tr>
└──────────┴─────┘
```

A table contains multiple `<tr>` elements.

```html
<table>

    <tr>
        ...
    </tr>

    <tr>
        ...
    </tr>

    <tr>
        ...
    </tr>

</table>
```

---

# 66. `<th>`

`<th>` means:

> **Table Header Cell**

It represents a header cell.

Example:

```html
<tr>
    <th>Name</th>
    <th>Age</th>
    <th>City</th>
</tr>
```

Conceptually:

```text
┌──────────┬─────┬──────────┐
│ Name     │ Age │ City     │  ← header
├──────────┼─────┼──────────┤
│ John     │ 25  │ Delhi    │
└──────────┴─────┴──────────┘
```

By default, browsers generally display `<th>` text bold and centered, but **don't depend on the default appearance**. CSS controls presentation.

---

## Why use `<th>` instead of `<td>` for headers?

Because `<th>` has **semantic meaning**.

Compare:

```html
<td>Name</td>
```

with:

```html
<th>Name</th>
```

The second tells browsers, assistive technologies, and developers:

> "This cell is a table header."

This is especially important for accessibility.

---

# 67. `<td>`

`<td>` means:

> **Table Data Cell**

It contains normal table data.

Example:

```html
<tr>
    <td>John</td>
    <td>25</td>
    <td>Delhi</td>
</tr>
```

Conceptually:

```text
┌──────────┬─────┬──────────┐
│ John     │ 25  │ Delhi    │
└──────────┴─────┴──────────┘
  ↑           ↑       ↑
 <td>        <td>    <td>
```

---

# ⭐ `<th>` vs `<td>`

This is a common interview question.

| `<th>`                   | `<td>`                       |
| ------------------------ | ---------------------------- |
| Header cell              | Data cell                    |
| Describes a row/column   | Contains normal data         |
| Semantic header          | Semantic data                |
| Useful for accessibility | Represents actual table data |

Example:

```html
<tr>
    <th>Name</th>
    <th>Salary</th>
</tr>

<tr>
    <td>John</td>
    <td>$5000</td>
</tr>
```

---

# 68. `<thead>`

`<thead>` groups the **header rows** of a table.

Example:

```html
<table>

    <thead>
        <tr>
            <th>Name</th>
            <th>Age</th>
            <th>City</th>
        </tr>
    </thead>

</table>
```

Think:

```text
<table>
   │
   └── <thead>
          │
          └── <tr>
                 ├── <th>
                 ├── <th>
                 └── <th>
```

---

## Why use `<thead>`?

It gives the table a clear semantic structure.

Instead of:

```html
<table>
    <tr>
        <th>Name</th>
        <th>Age</th>
    </tr>

    <tr>
        <td>John</td>
        <td>25</td>
    </tr>
</table>
```

you can write:

```html
<table>

    <thead>
        <tr>
            <th>Name</th>
            <th>Age</th>
        </tr>
    </thead>

    <tbody>
        ...
    </tbody>

</table>
```

This makes larger tables easier to understand and style.

---

# 69. `<tbody>`

`<tbody>` groups the **main body rows** of the table.

Example:

```html
<table>

    <thead>
        <tr>
            <th>Name</th>
            <th>Age</th>
        </tr>
    </thead>

    <tbody>

        <tr>
            <td>John</td>
            <td>25</td>
        </tr>

        <tr>
            <td>Sarah</td>
            <td>28</td>
        </tr>

    </tbody>

</table>
```

Think:

```text
┌──────────────────────────────┐
│            THEAD             │
│ Name          Age            │
├──────────────────────────────┤
│            TBODY             │
│ John          25             │
│ Sarah         28             │
└──────────────────────────────┘
```

---

# 70. `<tfoot>`

`<tfoot>` groups the **footer rows** of a table.

Common uses:

* Totals
* Summary
* Average
* Final calculations
* Notes

Example:

```html
<table>

    <thead>
        <tr>
            <th>Product</th>
            <th>Price</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <td>Laptop</td>
            <td>$1000</td>
        </tr>

        <tr>
            <td>Mouse</td>
            <td>$50</td>
        </tr>
    </tbody>

    <tfoot>
        <tr>
            <th>Total</th>
            <th>$1050</th>
        </tr>
    </tfoot>

</table>
```

Conceptually:

```text
┌──────────────┬─────────┐
│ Product      │ Price   │  ← THEAD
├──────────────┼─────────┤
│ Laptop       │ $1000   │  ← TBODY
│ Mouse        │ $50     │  ← TBODY
├──────────────┼─────────┤
│ Total        │ $1050   │  ← TFOOT
└──────────────┴─────────┘
```

---

# ⭐ Complete Table Structure

A professional table commonly looks like:

```html
<table>

    <thead>
        <tr>
            <th>Name</th>
            <th>Role</th>
            <th>Salary</th>
        </tr>
    </thead>

    <tbody>

        <tr>
            <td>John</td>
            <td>Developer</td>
            <td>$5000</td>
        </tr>

        <tr>
            <td>Sarah</td>
            <td>Designer</td>
            <td>$4500</td>
        </tr>

    </tbody>

    <tfoot>
        <tr>
            <th>Total</th>
            <th></th>
            <th>$9500</th>
        </tr>
    </tfoot>

</table>
```

The hierarchy is:

```text
<table>
│
├── <thead>
│     └── <tr>
│           ├── <th>
│           ├── <th>
│           └── <th>
│
├── <tbody>
│     ├── <tr>
│     │     ├── <td>
│     │     ├── <td>
│     │     └── <td>
│     │
│     └── <tr>
│           ├── <td>
│           ├── <td>
│           └── <td>
│
└── <tfoot>
      └── <tr>
            ├── <th>
            ├── <th>
            └── <th>
```

This structure is worth remembering.

---

# 71. `colspan`

`colspan` allows a cell to span **multiple columns**.

Example:

```html
<table border="1">

    <tr>
        <th colspan="2">Student Information</th>
    </tr>

    <tr>
        <th>Name</th>
        <th>Age</th>
    </tr>

    <tr>
        <td>John</td>
        <td>25</td>
    </tr>

</table>
```

The first header spans two columns:

```text
┌─────────────────────────────┐
│     Student Information     │
├──────────────┬──────────────┤
│ Name         │ Age          │
├──────────────┼──────────────┤
│ John         │ 25           │
└──────────────┴──────────────┘
```

This:

```html
<th colspan="2">
```

means:

> This cell occupies 2 columns.

---

## Another example

```html
<table>

    <tr>
        <th>Name</th>
        <th colspan="2">Contact</th>
    </tr>

    <tr>
        <td>John</td>
        <td>john@email.com</td>
        <td>9876543210</td>
    </tr>

</table>
```

Conceptually:

```text
┌──────────┬───────────────────────────┐
│ Name     │         Contact           │
│          ├─────────────┬─────────────┤
│ John     │ Email       │ Phone       │
└──────────┴─────────────┴─────────────┘
```

The `Contact` header spans two columns.

---

# 72. `rowspan`

`rowspan` allows a cell to span **multiple rows**.

Example:

```html
<table border="1">

    <tr>
        <th>Name</th>
        <th>Subject</th>
        <th>Marks</th>
    </tr>

    <tr>
        <td rowspan="2">John</td>
        <td>HTML</td>
        <td>90</td>
    </tr>

    <tr>
        <td>CSS</td>
        <td>85</td>
    </tr>

</table>
```

Conceptually:

```text
┌──────────┬──────────┬───────┐
│ Name     │ Subject  │ Marks │
├──────────┼──────────┼───────┤
│          │ HTML     │ 90    │
│ John     ├──────────┼───────┤
│          │ CSS      │ 85    │
└──────────┴──────────┴───────┘
```

This:

```html
<td rowspan="2">
```

means:

> This cell occupies 2 rows.

---

# ⭐ `colspan` vs `rowspan`

Very important to remember:

```text
colspan
   ↓
spans horizontally
spans columns

rowspan
   ↓
spans vertically
spans rows
```

| Attribute     | Meaning                 |
| ------------- | ----------------------- |
| `colspan="2"` | Cell occupies 2 columns |
| `rowspan="2"` | Cell occupies 2 rows    |

Easy memory trick:

```text
COLspan → COLumns
ROWspan → ROWs
```

---

# ⭐ Combining `rowspan` and `colspan`

You can use both.

Example:

```html
<table border="1">

    <tr>
        <th rowspan="2">Name</th>
        <th colspan="2">Scores</th>
    </tr>

    <tr>
        <th>HTML</th>
        <th>CSS</th>
    </tr>

    <tr>
        <td>John</td>
        <td>90</td>
        <td>85</td>
    </tr>

</table>
```

Conceptually:

```text
┌──────────┬───────────────┐
│          │    Scores     │
│   Name   ├───────┬───────┤
│          │ HTML  │ CSS   │
├──────────┼───────┼───────┤
│ John     │ 90    │ 85    │
└──────────┴───────┴───────┘
```

---

# ⭐ Table Headers and Accessibility

This is where tables become more important for frontend interviews.

Consider:

```html
<table>

    <thead>
        <tr>
            <th>Name</th>
            <th>Age</th>
            <th>City</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <td>John</td>
            <td>25</td>
            <td>Delhi</td>
        </tr>
    </tbody>

</table>
```

The browser understands that:

```text
Name → column heading
Age  → column heading
City → column heading
```

This semantic relationship helps assistive technologies understand the table.

---

# ⭐ `scope`

Although it's not in your required list, **you should learn this for interviews**.

`scope` tells the browser/assistive technologies what a header applies to.

### Column header

```html
<th scope="col">Name</th>
<th scope="col">Age</th>
<th scope="col">City</th>
```

Meaning:

```text
This header describes a column.
```

### Row header

Suppose each row represents a person:

```html
<tr>
    <th scope="row">John</th>
    <td>25</td>
    <td>Delhi</td>
</tr>
```

Here `John` acts as the header for that row.

---

# ⭐ Example with `scope`

```html
<table>

    <thead>
        <tr>
            <th scope="col">Student</th>
            <th scope="col">HTML</th>
            <th scope="col">CSS</th>
            <th scope="col">JavaScript</th>
        </tr>
    </thead>

    <tbody>

        <tr>
            <th scope="row">John</th>
            <td>90</td>
            <td>85</td>
            <td>88</td>
        </tr>

        <tr>
            <th scope="row">Sarah</th>
            <td>95</td>
            <td>92</td>
            <td>94</td>
        </tr>

    </tbody>

</table>
```

This is a much more semantically meaningful table.

---

# ⭐ `<caption>`

Another useful table element not explicitly in your list is `<caption>`.

It provides a title/description for the table.

```html
<table>

    <caption>Student Exam Results</caption>

    <thead>
        <tr>
            <th>Name</th>
            <th>Marks</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <td>John</td>
            <td>90</td>
        </tr>
    </tbody>

</table>
```

Think:

```text
Student Exam Results
────────────────────
Name       Marks
John       90
```

`<caption>` is useful for accessibility and makes the purpose of the table clear.

---

# ⭐ Real-World Example — Employee Table

Let's build something closer to what you'd see in an application.

```html
<table>

    <caption>Employee Information</caption>

    <thead>
        <tr>
            <th scope="col">Employee ID</th>
            <th scope="col">Name</th>
            <th scope="col">Department</th>
            <th scope="col">Salary</th>
        </tr>
    </thead>

    <tbody>

        <tr>
            <td>101</td>
            <td>John</td>
            <td>Engineering</td>
            <td>$5000</td>
        </tr>

        <tr>
            <td>102</td>
            <td>Sarah</td>
            <td>Design</td>
            <td>$4500</td>
        </tr>

        <tr>
            <td>103</td>
            <td>Mike</td>
            <td>Marketing</td>
            <td>$4000</td>
        </tr>

    </tbody>

    <tfoot>
        <tr>
            <th scope="row">Total</th>
            <td></td>
            <td></td>
            <td>$13,500</td>
        </tr>
    </tfoot>

</table>
```

Notice how semantic everything is:

```text
<table>
    ↓
<caption>
    ↓
<thead>
    ↓
<tbody>
    ↓
<tfoot>
```

---

# 🚨 Don't Use Tables for Page Layout

Old HTML websites sometimes used tables for layout:

```html
<table>
    <tr>
        <td>Header</td>
    </tr>

    <tr>
        <td>Sidebar</td>
        <td>Main content</td>
    </tr>
</table>
```

Don't do this for modern website layout.

Use:

```text
CSS Flexbox
CSS Grid
```

instead.

Tables should represent **relationships between tabular data**.

### Good use

```text
Product | Price | Quantity
Laptop  | $1000 | 2
Mouse   | $50   | 5
```

### Bad use

```text
┌─────────────────────────┐
│         HEADER          │
├──────────┬──────────────┤
│ SIDEBAR  │ MAIN CONTENT │
└──────────┴──────────────┘
```

That is webpage layout, not tabular data.

---

# ⭐ Common Table Mistakes

## Mistake 1 — Using `<td>` for headers

Bad:

```html
<tr>
    <td>Name</td>
    <td>Age</td>
</tr>
```

Better:

```html
<tr>
    <th>Name</th>
    <th>Age</th>
</tr>
```

---

## Mistake 2 — Using `<th>` for everything

Don't make every cell a `<th>`.

Use:

```text
<th> → headers
<td> → normal data
```

---

## Mistake 3 — Forgetting `<tr>`

This isn't the normal structure:

```html
<table>
    <td>John</td>
    <td>25</td>
</table>
```

Use:

```html
<table>
    <tr>
        <td>John</td>
        <td>25</td>
    </tr>
</table>
```

---

## Mistake 4 — Incorrect `colspan`

Suppose your table has three columns:

```html
<th colspan="3">Student</th>
```

This header occupies all three columns.

Don't accidentally use:

```html
<th colspan="2">Student</th>
```

if you intended to span three.

---

# 🧠 Table Mental Model

Memorize this structure:

```text
                    TABLE
                      │
          ┌───────────┼───────────┐
          │           │           │
        THEAD       TBODY       TFOOT
          │           │           │
         TR          TR          TR
          │           │           │
         TH       TH / TD       TH / TD
```

More accurately:

```text
<table>
│
├── <caption>
│
├── <thead>
│     └── <tr>
│           ├── <th>
│           ├── <th>
│           └── <th>
│
├── <tbody>
│     ├── <tr>
│     │     ├── <td>
│     │     ├── <td>
│     │     └── <td>
│     │
│     └── <tr>
│           ├── <td>
│           ├── <td>
│           └── <td>
│
└── <tfoot>
      └── <tr>
            ├── <th>
            ├── <td>
            └── <td>
```

And:

```text
colspan → multiple columns
rowspan → multiple rows
```

---

# 🎯 Interview Questions — Level 5

You should be able to answer these confidently.

### Basic

1. What is `<table>`?
2. What is `<tr>`?
3. What is `<th>`?
4. What is `<td>`?
5. Difference between `<th>` and `<td>`?
6. What is `<thead>`?
7. What is `<tbody>`?
8. What is `<tfoot>`?

### Intermediate

9. What is `colspan`?
10. What is `rowspan`?
11. Difference between `colspan` and `rowspan`?
12. Can `<th>` use `colspan`?
13. Can `<td>` use `rowspan`?
14. What is `<caption>`?
15. What is the purpose of `scope`?
16. How do you make a table accessible?
17. Should tables be used for website layout?
18. What should you use instead of tables for layout?

### ⭐ Common interview questions

**Q: Difference between `<th>` and `<td>`?**

> `<th>` represents a header cell, while `<td>` represents a normal data cell.

**Q: What does `colspan` do?**

> It makes a table cell span multiple columns.

**Q: What does `rowspan` do?**

> It makes a table cell span multiple rows.

**Q: Why use `<thead>`, `<tbody>`, and `<tfoot>`?**

> They semantically group the header, body, and footer portions of a table, making the structure clearer and easier to style/manage.

**Q: Should tables be used for page layout?**

> No. Tables should be used for tabular data. CSS Flexbox and Grid should be used for page layout.

**Q: How can you improve table accessibility?**

> Use proper `<th>` elements, appropriate `scope` values, meaningful table structure, and a `<caption>` where useful.

---

# 🏆 Level 5 — What You Must Know

For an interview, make sure these are automatic:

```text
<table>
   ↓
<tr>
   ↓
<th> / <td>
```

Then:

```text
<thead> → header
<tbody> → main data
<tfoot> → summary/footer
```

And:

```text
colspan → spans columns
rowspan → spans rows
```

Plus these two **bonus interview topics**:

```text
<caption> → table title/description
scope      → identifies what a header applies to
```

### Your Level 5 practice task

Build an **Employee Management Table** containing:

```text
Employee ID
Name
Department
Position
Salary
Joining Date
```

Requirements:

* Use `<caption>`
* Use `<thead>`
* Use `<tbody>`
* Use `<tfoot>`
* Use `<th>` for headers
* Use `scope`
* Create a total salary row
* Use `colspan` for the "Total" label

Once you can create that table without looking at notes, **Level 5 is done**.