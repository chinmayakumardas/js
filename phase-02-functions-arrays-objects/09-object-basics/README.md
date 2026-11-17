# Objects — Basics

**Short Definition:**  
Objects store data as key-value pairs. They are the foundation of almost everything in JavaScript (even arrays and functions are objects under the hood).

---

## Why it matters
- Everything non-primitive is an object
- Props, state, API responses, configs → all objects
- Interviewers test dot vs bracket, reference behavior, and methods

---

## Creating & Accessing

```js
const user = {
  name: "Alex",
  age: 25,
  "home city": "Delhi"     // space in key → must use quotes
};

// Dot notation
console.log(user.name);          // "Alex"

// Bracket notation (required for dynamic keys or special characters)
console.log(user["home city"]);  // "Delhi"

const key = "age";
console.log(user[key]);          // 25
```

---

## Add / Update / Delete

```js
user.email = "alex@mail.com";    // add
user.age = 26;                   // update
delete user.email;               // delete
```

---

## Reference Behavior (Critical)

```js
const obj1 = { x: 10 };
const obj2 = obj1;        // both point to same memory

obj2.x = 99;
console.log(obj1.x);      // 99  ← original also changed
```

```
Memory:
obj1 ──┐
       ├──> { x: 99 }
obj2 ──┘
```

To copy (shallow):
```js
const copy = { ...obj1 };
const copy2 = Object.assign({}, obj1);
```

---

## Methods

```js
const calculator = {
  value: 0,
  add(n) {
    this.value += n;
  },
  getValue() {
    return this.value;
  }
};

calculator.add(5);
console.log(calculator.getValue()); // 5
```

---

## Interview Expectation
- Explain reference vs value
- When to use bracket notation
- How to clone an object (and that it’s shallow)

---

## Practice
```js
const person = { name: "Sam" };
const other = person;
other.name = "Alex";
console.log(person.name); // ?
```
