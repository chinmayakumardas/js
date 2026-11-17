# Function Declaration vs Function Expression

**Short Definition:**  
Two ways to create functions in JavaScript. They look similar but behave differently because of hoisting.

---

## Why it matters
Interviewers love asking this. It also affects when you can call a function.

---

## 1. Function Declaration

```js
function greet(name) {
  return "Hello, " + name;
}

console.log(greet("Alex")); // "Hello, Alex"
```

- Fully hoisted (you can call it before the line where it is written)
- Has a name (good for stack traces and recursion)

```js
// This works because of hoisting
sayHi(); // "Hi"

function sayHi() {
  console.log("Hi");
}
```

---

## 2. Function Expression

```js
const greet = function(name) {
  return "Hello, " + name;
};
```

- Not fully hoisted (only the variable is hoisted as `undefined`)
- Can be anonymous or named

```js
// This fails
sayHi(); // TypeError: sayHi is not a function

var sayHi = function() {
  console.log("Hi");
};
```

---

## Memory / Creation View

```
Creation Phase:
  - function greet → entire function is stored in memory
  - var sayHi → undefined

Execution Phase:
  - greet is already available
  - sayHi gets the function value only when that line runs
```

---

## Interview Expectation

| Level | What they expect |
|-------|------------------|
| Junior | Know the syntax difference and that declarations are hoisted |
| Mid | Explain TDZ + why expression cannot be called early |
| Strong | Mention named function expressions and stack trace benefits |

**Sample Answer:**  
“Function declarations are fully hoisted, so I can call them before their line. Function expressions are not — only the variable is hoisted as undefined. That’s why calling an expression early throws a TypeError.”

---

## Practice

```js
// Predict output
console.log(a);
console.log(b);

function a() { return 1; }
var b = function() { return 2; };
```
