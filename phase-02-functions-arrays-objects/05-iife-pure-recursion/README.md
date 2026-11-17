# IIFE, Pure Functions & Recursion

**Short Definition:**  
IIFE = function that runs immediately. Pure function = same input always gives same output, no side effects. Recursion = function calling itself.

---

## IIFE
```js
(function() {
  console.log("I run immediately");
})();

(() => {
  console.log("Arrow IIFE");
})();
```
Used historically to avoid polluting global scope.

## Pure vs Impure
```js
// Pure
function add(a, b) {
  return a + b;
}

// Impure (depends on external state / has side effect)
let total = 0;
function addToTotal(n) {
  total += n;
}
```

## Recursion Basics
```js
function factorial(n) {
  if (n === 0) return 1;
  return n * factorial(n - 1);
}
factorial(5); // 120
```
Always need a base case to avoid infinite recursion (stack overflow).
