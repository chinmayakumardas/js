# Arrow Functions

**Short Definition:**  
A shorter way to write functions introduced in ES6. They do **not** have their own `this`, `arguments`, or `prototype`.

---

## Why it matters
- Extremely common in modern code (React, array methods, callbacks)
- Biggest source of `this` bugs if you don’t understand lexical `this`

---

## Syntax

```js
// Full
const add = (a, b) => {
  return a + b;
};

// Implicit return (one expression)
const add2 = (a, b) => a + b;

// One parameter → parentheses optional
const square = n => n * n;

// No parameter
const hello = () => console.log("Hello");
```

---

## Key Differences vs Regular Functions

| Feature | Regular Function | Arrow Function |
|---------|------------------|----------------|
| `this` | Depends on how it is called | Lexical (taken from outer scope) |
| `arguments` object | Yes | No (use rest `...args`) |
| Can be used as constructor | Yes (`new`) | No |
| `prototype` property | Yes | No |

```js
const obj = {
  name: "Alex",
  regular: function() {
    console.log(this.name);   // "Alex"
  },
  arrow: () => {
    console.log(this.name);   // undefined (or global)
  }
};

obj.regular();
obj.arrow();
```

---

## When to use Arrow Functions
- Callbacks (`map`, `filter`, `forEach`)
- Short pure functions
- When you want to keep the outer `this`

## When NOT to use
- Object methods (usually)
- Event handlers when you need `this` as the element
- Constructors

---

## Interview Expectation
They will ask:  
“Does an arrow function have its own `this`?” → **No**.  
“Can you use `new` with arrow function?” → **No**.

---

## Practice
```js
const person = {
  age: 25,
  grow: () => {
    this.age++;
  }
};
person.grow();
console.log(person.age); // ?
```
