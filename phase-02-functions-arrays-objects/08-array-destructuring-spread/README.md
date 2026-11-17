# Array Destructuring & Spread

**Short Definition:**  
Destructuring pulls values out of arrays into variables. Spread (`...`) expands an array into individual elements.

---

## Destructuring
```js
const arr = [10, 20, 30];
const [a, b, c] = arr;
console.log(a, b, c); // 10 20 30

const [x, , z] = arr; // skip middle
const [first, ...rest] = arr;
```

## Spread
```js
const arr1 = [1, 2];
const arr2 = [3, 4];
const combined = [...arr1, ...arr2]; // [1,2,3,4]

const copy = [...arr1]; // shallow copy
Math.max(...[5, 1, 9]); // 9
```

## Interview
Spread creates shallow copy. Nested objects/arrays are still shared by reference.
