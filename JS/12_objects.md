# 12. Objects ⭐⭐⭐⭐⭐

Objects are **one of the most important JavaScript topics for React interviews**.

In real React applications, you will constantly work with objects:

* API responses
* User information
* Product information
* Props
* State
* Form data
* Configuration
* Nested data
* Arrays of objects

So let's learn Objects from **basic → intermediate → React → interview level**.

---

# 1. What is an Object?

An **object** is a collection of data stored in **key-value pairs**.

### Example

```javascript
const student = {
    name: "Sai",
    age: 22,
    course: "React",
    city: "Kadapa"
};
```

Here:

```text
name   → "Sai"
age    → 22
course → "React"
city   → "Kadapa"
```

Each pair is called a **property**.

### Structure

```javascript
const objectName = {
    key: value,
    key: value,
    key: value
};
```

---

# 2. Why Do We Need Objects?

Suppose you store student information separately:

```javascript
const name = "Sai";
const age = 22;
const course = "React";
const city = "Kadapa";
```

This works, but related information is scattered.

Instead:

```javascript
const student = {
    name: "Sai",
    age: 22,
    course: "React",
    city: "Kadapa"
};
```

Now all student information is grouped together.

This is much easier to manage.

---

# 3. Creating an Object

The most common way is using an **object literal**.

```javascript
const person = {
    name: "Rahul",
    age: 25,
    city: "Hyderabad"
};
```

You can also create an empty object:

```javascript
const person = {};
```

Then add properties later:

```javascript
person.name = "Rahul";
person.age = 25;
```

---

# 4. Object Properties

Consider:

```javascript
const student = {
    name: "Sai",
    age: 22,
    course: "React"
};
```

Here:

```text
name   → property
age    → property
course → property
```

And their values are:

```text
"Sai"   → value
22      → value
"React" → value
```

A property can contain different data types.

```javascript
const student = {
    name: "Sai",           // string
    age: 22,               // number
    passed: true,          // boolean
    skills: ["HTML", "CSS", "JS"], // array
    address: {
        city: "Kadapa"
    }                      // object
};
```

Objects can therefore contain:

* strings
* numbers
* booleans
* arrays
* other objects
* functions

---

# 5. Accessing Object Properties

There are two main ways.

## Method 1: Dot notation ⭐⭐⭐⭐⭐

```javascript
const student = {
    name: "Sai",
    age: 22
};

console.log(student.name);
console.log(student.age);
```

Output:

```text
Sai
22
```

This is the most commonly used syntax.

---

# 6. Bracket Notation ⭐⭐⭐⭐⭐

You can also use:

```javascript
const student = {
    name: "Sai",
    age: 22
};

console.log(student["name"]);
console.log(student["age"]);
```

Output:

```text
Sai
22
```

So:

```javascript
student.name
```

and

```javascript
student["name"]
```

access the same property.

---

# 7. Dot Notation vs Bracket Notation

### Dot notation

```javascript
student.name
```

### Bracket notation

```javascript
student["name"]
```

Usually use dot notation when you know the property name.

Use bracket notation when the property name is stored in a variable.

### Example

```javascript
const student = {
    name: "Sai",
    age: 22
};

const property = "name";

console.log(student[property]);
```

Output:

```text
Sai
```

This is extremely important.

---

# 8. Why Doesn't This Work?

Consider:

```javascript
const property = "name";

console.log(student.property);
```

JavaScript looks for:

```text
student → property
```

It searches for a property literally called `"property"`.

It does **not** use the value of the variable.

Instead:

```javascript
student[property]
```

means:

```javascript
student["name"]
```

because:

```javascript
property = "name"
```

---

# 9. Adding Properties

You can add a property after creating an object.

```javascript
const student = {
    name: "Sai"
};

student.age = 22;

console.log(student);
```

Output:

```javascript
{
    name: "Sai",
    age: 22
}
```

You can also use bracket notation:

```javascript
student["city"] = "Kadapa";
```

Now:

```javascript
console.log(student);
```

```text
{
    name: "Sai",
    age: 22,
    city: "Kadapa"
}
```

---

# 10. Updating Properties

Suppose:

```javascript
const student = {
    name: "Sai",
    age: 22
};
```

Change the age:

```javascript
student.age = 23;
```

Now:

```javascript
console.log(student.age);
```

Output:

```text
23
```

You can also update using brackets:

```javascript
student["age"] = 24;
```

---

# 11. Deleting Properties

Use the `delete` operator.

```javascript
const student = {
    name: "Sai",
    age: 22,
    city: "Kadapa"
};

delete student.city;

console.log(student);
```

Output:

```text
{
    name: "Sai",
    age: 22
}
```

### Interview point

```javascript
delete object.property;
```

removes the property.

---

# 12. Checking if a Property Exists

You can use:

```javascript
"name" in student
```

Example:

```javascript
const student = {
    name: "Sai",
    age: 22
};

console.log("name" in student);
console.log("city" in student);
```

Output:

```text
true
false
```

---

# 13. `hasOwnProperty()`

Another common way:

```javascript
console.log(student.hasOwnProperty("name"));
```

Output:

```text
true
```

And:

```javascript
console.log(student.hasOwnProperty("city"));
```

Output:

```text
false
```

Modern JavaScript also provides:

```javascript
Object.hasOwn(student, "name");
```

For interviews, know both.

---

# 14. Nested Objects ⭐⭐⭐⭐⭐

An object can contain another object.

```javascript
const student = {
    name: "Sai",
    age: 22,

    address: {
        city: "Kadapa",
        state: "Andhra Pradesh",
        pincode: 516001
    }
};
```

Now:

```javascript
console.log(student.name);
```

Output:

```text
Sai
```

To access the nested city:

```javascript
console.log(student.address.city);
```

Output:

```text
Kadapa
```

Or:

```javascript
console.log(student.address.pincode);
```

Output:

```text
516001
```

---

# 15. Deeply Nested Objects

Objects can have multiple levels.

```javascript
const company = {
    name: "ABC",
    employee: {
        name: "Sai",
        address: {
            city: "Kadapa",
            country: {
                name: "India"
            }
        }
    }
};
```

Access:

```javascript
console.log(company.employee.address.city);
```

Output:

```text
Kadapa
```

And:

```javascript
console.log(company.employee.address.country.name);
```

Output:

```text
India
```

---

# 16. Optional Chaining `?.` ⭐⭐⭐⭐⭐

This is very important in modern JavaScript and React.

Suppose:

```javascript
const student = {
    name: "Sai"
};
```

If you do:

```javascript
console.log(student.address.city);
```

you get an error because `address` doesn't exist.

Instead:

```javascript
console.log(student.address?.city);
```

Output:

```text
undefined
```

You can also write:

```javascript
console.log(student?.address?.city);
```

This safely checks each level.

---

# 17. Objects Can Contain Arrays

Very common in API data.

```javascript
const student = {
    name: "Sai",
    skills: ["HTML", "CSS", "JavaScript", "React"]
};
```

Access:

```javascript
console.log(student.skills);
```

Output:

```text
["HTML", "CSS", "JavaScript", "React"]
```

Access one item:

```javascript
console.log(student.skills[0]);
```

Output:

```text
HTML
```

---

# 18. Arrays Can Contain Objects ⭐⭐⭐⭐⭐

This is **extremely important for React**.

```javascript
const students = [
    {
        id: 1,
        name: "Sai",
        age: 22
    },
    {
        id: 2,
        name: "Rahul",
        age: 23
    },
    {
        id: 3,
        name: "Anil",
        age: 21
    }
];
```

This is an:

> **Array of Objects**

You will see this structure everywhere in React.

For example, API response:

```javascript
[
    {
        id: 1,
        name: "Sai"
    },
    {
        id: 2,
        name: "Rahul"
    }
]
```

---

# 19. Accessing Objects Inside an Array

```javascript
console.log(students[0]);
```

Output:

```javascript
{
    id: 1,
    name: "Sai",
    age: 22
}
```

Get the name:

```javascript
console.log(students[0].name);
```

Output:

```text
Sai
```

Second student's name:

```javascript
console.log(students[1].name);
```

Output:

```text
Rahul
```

---

# 20. Looping Through an Array of Objects

You can use `for...of`:

```javascript
for (const student of students) {
    console.log(student.name);
}
```

Output:

```text
Sai
Rahul
Anil
```

Or the most common React approach:

```javascript
students.map(student => {
    console.log(student.name);
});
```

---

# 21. Object Methods ⭐⭐⭐⭐⭐

An object can contain functions.

```javascript
const person = {
    name: "Sai",

    greet: function() {
        console.log("Hello");
    }
};
```

Call the method:

```javascript
person.greet();
```

Output:

```text
Hello
```

A function stored inside an object is commonly called a **method**.

---

# 22. Short Method Syntax

Instead of:

```javascript
const person = {
    greet: function() {
        console.log("Hello");
    }
};
```

You can write:

```javascript
const person = {
    greet() {
        console.log("Hello");
    }
};
```

This is modern JavaScript syntax.

---

# 23. Object Method Using `this` ⭐⭐⭐⭐⭐

This connects Objects with the `this` topic you'll study later.

```javascript
const person = {
    name: "Sai",

    greet() {
        console.log("Hello " + this.name);
    }
};

person.greet();
```

Output:

```text
Hello Sai
```

Here:

```javascript
this.name
```

refers to:

```javascript
person.name
```

So:

```text
this → person
this.name → "Sai"
```

We'll study `this` deeply later.

---

# 24. Object Property Shorthand ⭐⭐⭐⭐⭐

Suppose:

```javascript
const name = "Sai";
const age = 22;
```

Instead of:

```javascript
const student = {
    name: name,
    age: age
};
```

Modern JavaScript allows:

```javascript
const student = {
    name,
    age
};
```

JavaScript understands:

```javascript
name: name
age: age
```

automatically.

---

# 25. Example

```javascript
const name = "Sai";
const course = "React";

const student = {
    name,
    course
};

console.log(student);
```

Output:

```text
{
    name: "Sai",
    course: "React"
}
```

This is very common in React.

---

# 26. Computed Property Names ⭐⭐⭐⭐

You can create a property name dynamically.

```javascript
const key = "name";

const student = {
    [key]: "Sai"
};

console.log(student);
```

Output:

```text
{
    name: "Sai"
}
```

Why?

```javascript
[key]
```

evaluates the variable.

Since:

```javascript
key = "name"
```

the property becomes:

```javascript
name: "Sai"
```

---

# 27. Object Destructuring ⭐⭐⭐⭐⭐

This is one of the **most important JavaScript concepts for React**.

Suppose:

```javascript
const student = {
    name: "Sai",
    age: 22,
    course: "React"
};
```

Normally:

```javascript
console.log(student.name);
console.log(student.age);
```

With destructuring:

```javascript
const { name, age } = student;

console.log(name);
console.log(age);
```

Output:

```text
Sai
22
```

You are extracting properties from the object.

---

# 28. Destructuring With Different Variable Name

Suppose:

```javascript
const student = {
    name: "Sai"
};
```

You can rename it:

```javascript
const { name: studentName } = student;

console.log(studentName);
```

Output:

```text
Sai
```

Here:

```javascript
name: studentName
```

means:

```text
Take property "name"
and store it in variable "studentName"
```

---

# 29. Default Values in Destructuring

```javascript
const student = {
    name: "Sai"
};

const { name, age = 22 } = student;

console.log(name);
console.log(age);
```

Output:

```text
Sai
22
```

Since `age` didn't exist, JavaScript uses the default value `22`.

---

# 30. Nested Destructuring

Example:

```javascript
const student = {
    name: "Sai",
    address: {
        city: "Kadapa",
        state: "Andhra Pradesh"
    }
};
```

You can write:

```javascript
const {
    address: { city, state }
} = student;

console.log(city);
console.log(state);
```

Output:

```text
Kadapa
Andhra Pradesh
```

---

# 31. Object Spread Operator ⭐⭐⭐⭐⭐

This is **very important in React**.

Suppose:

```javascript
const student = {
    name: "Sai",
    age: 22
};
```

Create a copy:

```javascript
const newStudent = {
    ...student
};
```

Now:

```javascript
console.log(newStudent);
```

Output:

```text
{
    name: "Sai",
    age: 22
}
```

---

# 32. Adding Properties With Spread

```javascript
const student = {
    name: "Sai",
    age: 22
};

const newStudent = {
    ...student,
    course: "React"
};
```

Result:

```javascript
{
    name: "Sai",
    age: 22,
    course: "React"
}
```

---

# 33. Updating an Object With Spread ⭐⭐⭐⭐⭐

Suppose:

```javascript
const student = {
    name: "Sai",
    age: 22
};
```

You want a new object with age `23`.

```javascript
const updatedStudent = {
    ...student,
    age: 23
};
```

Result:

```javascript
{
    name: "Sai",
    age: 23
}
```

Notice:

```javascript
...student
```

copies the existing properties.

Then:

```javascript
age: 23
```

overwrites the old age.

---

# 34. Property Order Matters With Spread

Look carefully:

```javascript
const student = {
    age: 22
};

const result = {
    age: 23,
    ...student
};

console.log(result.age);
```

Output:

```text
22
```

Why?

Because the later property wins.

Compare:

```javascript
{
    ...student,
    age: 23
}
```

Result:

```text
age: 23
```

But:

```javascript
{
    age: 23,
    ...student
}
```

Result:

```text
age: 22
```

### Interview rule

> When object properties have the same key, the **later value overwrites the earlier value**.

---

# 35. Object Destructuring vs Spread

This is commonly confusing.

### Destructuring

```javascript
const { name } = student;
```

Means:

> Take data **out** of the object.

### Spread

```javascript
const newStudent = {
    ...student
};
```

Means:

> Copy/expand the object's properties **into another object**.

Think:

```text
Destructuring → take out
Spread        → spread/copy in
```

---

# 36. `Object.keys()` ⭐⭐⭐⭐⭐

Returns an array containing the object's keys.

```javascript
const student = {
    name: "Sai",
    age: 22,
    city: "Kadapa"
};

console.log(Object.keys(student));
```

Output:

```javascript
["name", "age", "city"]
```

---

# 37. `Object.values()` ⭐⭐⭐⭐⭐

Returns the values.

```javascript
console.log(Object.values(student));
```

Output:

```javascript
["Sai", 22, "Kadapa"]
```

---

# 38. `Object.entries()` ⭐⭐⭐⭐⭐

Returns key-value pairs.

```javascript
console.log(Object.entries(student));
```

Output:

```javascript
[
    ["name", "Sai"],
    ["age", 22],
    ["city", "Kadapa"]
]
```

Each entry is:

```javascript
[key, value]
```

---

# 39. Looping Through Object Properties

Using `Object.keys()`:

```javascript
Object.keys(student).forEach(key => {
    console.log(key);
});
```

Output:

```text
name
age
city
```

Using `Object.entries()`:

```javascript
Object.entries(student).forEach(([key, value]) => {
    console.log(key, value);
});
```

Output:

```text
name Sai
age 22
city Kadapa
```

This combines:

* `Object.entries()`
* array `forEach()`
* destructuring

Very useful for interviews.

---

# 40. `for...in` With Objects

You can also use:

```javascript
for (const key in student) {
    console.log(key);
}
```

Output:

```text
name
age
city
```

To get values:

```javascript
for (const key in student) {
    console.log(student[key]);
}
```

Output:

```text
Sai
22
Kadapa
```

### Important

For objects:

```javascript
for...in
```

is commonly used to iterate over keys.

For arrays:

```javascript
for...of
```

is generally preferred for values.

---

# 41. Object Reference ⭐⭐⭐⭐⭐

This is a **very important interview concept**.

Consider:

```javascript
const student1 = {
    name: "Sai"
};

const student2 = student1;

student2.name = "Rahul";

console.log(student1.name);
```

What is the output?

```text
Rahul
```

Why?

Because:

```javascript
student2 = student1;
```

doesn't create a new independent object.

Both variables refer to the same object.

Conceptually:

```text
student1 ──┐
           ↓
        { name: "Rahul" }
           ↑
student2 ──┘
```

---

# 42. Objects Are Reference Values

This is different from primitive values.

### Primitive

```javascript
let a = 10;
let b = a;

b = 20;

console.log(a);
```

Output:

```text
10
```

Because `b` gets its own primitive value.

### Object

```javascript
const a = {
    value: 10
};

const b = a;

b.value = 20;

console.log(a.value);
```

Output:

```text
20
```

Both refer to the same object.

---

# 43. Copying an Object With Spread

To create a new outer object:

```javascript
const student1 = {
    name: "Sai",
    age: 22
};

const student2 = {
    ...student1
};

student2.name = "Rahul";

console.log(student1.name);
console.log(student2.name);
```

Output:

```text
Sai
Rahul
```

Now they are different outer objects.

---

# 44. But Spread Creates a Shallow Copy ⭐⭐⭐⭐⭐

This is an important interview question.

Consider:

```javascript
const student1 = {
    name: "Sai",
    address: {
        city: "Kadapa"
    }
};

const student2 = {
    ...student1
};
```

The outer object is copied.

But:

```javascript
address
```

is still referencing the same nested object.

So:

```javascript
student2.address.city = "Hyderabad";
```

Then:

```javascript
console.log(student1.address.city);
```

Output:

```text
Hyderabad
```

Why?

Because the nested object was not deeply copied.

---

# 45. Shallow Copy vs Deep Copy

### Shallow copy

Copies only the first level.

```javascript
const copy = {
    ...original
};
```

### Deep copy

Creates independent nested structures.

One modern approach:

```javascript
const copy = structuredClone(original);
```

Example:

```javascript
const student1 = {
    name: "Sai",
    address: {
        city: "Kadapa"
    }
};

const student2 = structuredClone(student1);

student2.address.city = "Hyderabad";

console.log(student1.address.city);
```

Output:

```text
Kadapa
```

For React interviews, understand the concept:

```text
Spread → shallow copy
structuredClone → deep clone for supported data
```

---

# 46. Comparing Objects ⭐⭐⭐⭐⭐

This is a classic interview question.

```javascript
const obj1 = {
    name: "Sai"
};

const obj2 = {
    name: "Sai"
};

console.log(obj1 === obj2);
```

Output:

```text
false
```

Even though their contents are identical.

Why?

Because they are two different object references.

---

# 47. Same Reference Comparison

```javascript
const obj1 = {
    name: "Sai"
};

const obj2 = obj1;

console.log(obj1 === obj2);
```

Output:

```text
true
```

Because both variables point to the same object.

### Important rule

```text
Objects are compared by reference, not by their contents.
```

---

# 48. Object With Function

Objects can contain data and behavior.

```javascript
const calculator = {
    add(a, b) {
        return a + b;
    },

    subtract(a, b) {
        return a - b;
    }
};

console.log(calculator.add(10, 5));
console.log(calculator.subtract(10, 5));
```

Output:

```text
15
5
```

---

# 49. React Connection: Objects as State ⭐⭐⭐⭐⭐

Objects are extremely important in React state.

Example:

```javascript
const [user, setUser] = useState({
    name: "Sai",
    age: 22,
    city: "Kadapa"
});
```

To update the age:

```javascript
setUser({
    ...user,
    age: 23
});
```

Why use spread?

Because we want to create a new object instead of directly mutating the existing state object.

Avoid:

```javascript
user.age = 23;
```

and then expecting React to detect the change automatically.

---

# 50. React Object State Example

```javascript
function App() {
    const [user, setUser] = useState({
        name: "Sai",
        age: 22
    });

    const updateAge = () => {
        setUser({
            ...user,
            age: 23
        });
    };

    return (
        <div>
            <h2>{user.name}</h2>
            <p>{user.age}</p>

            <button onClick={updateAge}>
                Update Age
            </button>
        </div>
    );
}
```

The important JavaScript concept is:

```javascript
{
    ...user,
    age: 23
}
```

---

# 51. React Connection: Props Are Objects ⭐⭐⭐⭐⭐

Suppose:

```jsx
<Student name="Sai" age={22} />
```

Inside the component:

```javascript
function Student(props) {
    console.log(props);
}
```

`props` is an object.

Conceptually:

```javascript
{
    name: "Sai",
    age: 22
}
```

You can destructure it:

```javascript
function Student({ name, age }) {
    return (
        <h2>
            {name} - {age}
        </h2>
    );
}
```

So understanding object destructuring is essential for React.

---

# 52. React Connection: API Data

Imagine an API returns:

```javascript
const user = {
    id: 101,
    name: "Sai",
    email: "sai@example.com",
    address: {
        city: "Kadapa"
    }
};
```

You might write:

```javascript
<p>{user.name}</p>
<p>{user.email}</p>
<p>{user.address.city}</p>
```

Or destructure:

```javascript
const {
    name,
    email,
    address
} = user;
```

Then:

```jsx
<p>{name}</p>
<p>{email}</p>
<p>{address.city}</p>
```

---

# 53. React Connection: Updating Objects Inside Arrays ⭐⭐⭐⭐⭐

Suppose:

```javascript
const users = [
    { id: 1, name: "Sai" },
    { id: 2, name: "Rahul" }
];
```

You want to update Rahul.

Use:

```javascript
const updatedUsers = users.map(user =>
    user.id === 2
        ? { ...user, name: "Anil" }
        : user
);
```

Result:

```javascript
[
    { id: 1, name: "Sai" },
    { id: 2, name: "Anil" }
]
```

This pattern is **very important in React interviews**.

---

# 54. Common Object Interview Question

### Question:

What is the difference between:

```javascript
const obj1 = obj2;
```

and:

```javascript
const obj1 = { ...obj2 };
```

### Answer

```javascript
const obj1 = obj2;
```

Both variables reference the **same object**.

Whereas:

```javascript
const obj1 = { ...obj2 };
```

creates a **new shallow copy** of the object.

---

# 55. Common Interview Question

### What is the difference between dot and bracket notation?

```javascript
student.name
```

uses dot notation.

```javascript
student["name"]
```

uses bracket notation.

Bracket notation is especially useful for dynamic property names:

```javascript
const key = "name";

student[key];
```

---

# 56. Common Interview Question

### What is object destructuring?

Object destructuring allows us to extract properties into variables.

```javascript
const user = {
    name: "Sai",
    age: 22
};

const { name, age } = user;
```

Now:

```javascript
name
```

contains:

```text
Sai
```

and:

```javascript
age
```

contains:

```text
22
```

---

# 57. Common Interview Question

### What is the difference between `Object.keys()`, `Object.values()`, and `Object.entries()`?

| Method                | Returns         |
| --------------------- | --------------- |
| `Object.keys(obj)`    | Keys            |
| `Object.values(obj)`  | Values          |
| `Object.entries(obj)` | Key-value pairs |

Example:

```javascript
const user = {
    name: "Sai",
    age: 22
};
```

### `Object.keys()`

```javascript
["name", "age"]
```

### `Object.values()`

```javascript
["Sai", 22]
```

### `Object.entries()`

```javascript
[
    ["name", "Sai"],
    ["age", 22]
]
```

---

# 58. Common Interview Question

What is the output?

```javascript
const user = {
    name: "Sai"
};

const copy = user;

copy.name = "Rahul";

console.log(user.name);
```

Answer:

```text
Rahul
```

Because both variables reference the same object.

---

# 59. Common Interview Question

What is the output?

```javascript
const user = {
    name: "Sai"
};

const copy = {
    ...user
};

copy.name = "Rahul";

console.log(user.name);
```

Answer:

```text
Sai
```

Because spread created a new outer object.

---

# 60. Important Object Methods Cheat Sheet

| Method / Syntax       | Purpose             |
| --------------------- | ------------------- |
| `obj.name`            | Access property     |
| `obj["name"]`         | Access property     |
| `obj.name = value`    | Add/update          |
| `delete obj.name`     | Delete              |
| `"name" in obj`       | Check property      |
| `Object.keys(obj)`    | Get keys            |
| `Object.values(obj)`  | Get values          |
| `Object.entries(obj)` | Get key-value pairs |
| `{...obj}`            | Shallow copy        |
| `{...obj, age: 25}`   | Copy + update       |
| `obj?.address?.city`  | Safe nested access  |
| `const {name} = obj`  | Destructure         |

---

# 61. Object vs Array

This is important because both are commonly used together.

| Object                        | Array                           |
| ----------------------------- | ------------------------------- |
| Stores key-value pairs        | Stores ordered values           |
| `{}`                          | `[]`                            |
| Access using keys             | Access using indexes            |
| `user.name`                   | `users[0]`                      |
| Usually represents one entity | Usually represents a collection |
| `user = {name: "Sai"}`        | `users = ["Sai", "Rahul"]`      |

In real React applications, you frequently get:

```javascript
[
    {
        id: 1,
        name: "Sai"
    },
    {
        id: 2,
        name: "Rahul"
    }
]
```

That's an **array of objects**.

---

# 62. Most Important Concepts for React Interviews ⭐⭐⭐⭐⭐

From this entire topic, prioritize these:

### Must know

1. Object creation
2. Properties and values
3. Dot notation
4. Bracket notation
5. Add/update/delete properties
6. Nested objects
7. Arrays of objects
8. Object destructuring
9. Object spread
10. Object reference
11. Shallow copy
12. `Object.keys()`
13. `Object.values()`
14. `Object.entries()`
15. Optional chaining
16. Objects as React state
17. Objects as props
18. Updating objects immutably
19. Updating objects inside arrays
20. Object methods and `this`

---

# 63. Common Mistakes

### Mistake 1: Confusing dot and bracket notation

Wrong for dynamic key:

```javascript
const key = "name";

user.key;
```

Correct:

```javascript
user[key];
```

---

### Mistake 2: Mutating React state

Avoid:

```javascript
user.age = 23;
```

Prefer:

```javascript
setUser({
    ...user,
    age: 23
});
```

---

### Mistake 3: Thinking spread is deep copy

```javascript
const copy = {
    ...original
};
```

This is a **shallow copy**.

---

### Mistake 4: Comparing objects by content

```javascript
{} === {}
```

returns:

```text
false
```

because they are different references.

---

### Mistake 5: Forgetting optional chaining

Potentially unsafe:

```javascript
user.address.city
```

Safer when data may be missing:

```javascript
user?.address?.city
```

---

# 64. Mini Practice Questions 🧠

Try answering these without running the code.

### Question 1

```javascript
const user = {
    name: "Sai",
    age: 22
};

console.log(user.name);
```

What is the output?

---

### Question 2

```javascript
const user = {
    name: "Sai"
};

user.age = 22;

console.log(user);
```

What does the object contain?

---

### Question 3

```javascript
const user = {
    name: "Sai",
    age: 22
};

const { name } = user;

console.log(name);
```

---

### Question 4

```javascript
const user = {
    name: "Sai",
    age: 22
};

const copy = {
    ...user,
    age: 25
};

console.log(copy);
```

---

### Question 5 ⭐

```javascript
const user1 = {
    name: "Sai"
};

const user2 = user1;

user2.name = "Rahul";

console.log(user1.name);
```

---

### Question 6 ⭐⭐⭐⭐⭐

```javascript
const user = {
    name: "Sai",
    address: {
        city: "Kadapa"
    }
};

const copy = {
    ...user
};

copy.address.city = "Hyderabad";

console.log(user.address.city);
```

This tests **shallow copy**.

---

# 65. Final Mental Model 🧠

Remember Objects like this:

```text
OBJECT
  │
  ├── key/value
  │
  ├── access
  │     ├── obj.name
  │     └── obj["name"]
  │
  ├── modify
  │     ├── add
  │     ├── update
  │     └── delete
  │
  ├── nested objects
  │
  ├── arrays of objects
  │
  ├── methods
  │
  ├── destructuring
  │
  ├── spread
  │
  ├── Object.keys()
  ├── Object.values()
  ├── Object.entries()
  │
  ├── references
  │
  ├── shallow copy
  │
  └── React
        ├── Props
        ├── State
        ├── API data
        └── Immutable updates
```

## ⭐ Interview priority

If you're preparing specifically for **React interviews**, make sure you can comfortably write and explain:

```javascript
const user = {
    name: "Sai",
    age: 22,
    address: {
        city: "Kadapa"
    }
};
```

```javascript
const { name, age } = user;
```

```javascript
const updatedUser = {
    ...user,
    age: 23
};
```

```javascript
console.log(Object.keys(user));
console.log(Object.values(user));
console.log(Object.entries(user));
```

```javascript
console.log(user?.address?.city);
```

And especially:

```javascript
const updatedUsers = users.map(user =>
    user.id === 2
        ? { ...user, name: "Updated Name" }
        : user
);
```

That last pattern combines **objects + arrays + `map()` + spread + immutability**, which is extremely common in React.