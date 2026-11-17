# Array Iteration Methods

**Short Definition:**  
Methods that loop over arrays in a cleaner way than classic `for` loops. Most important: `map`, `filter`, `reduce`.

---

## Why it matters
These appear in almost every interview and every real codebase.  
`map + filter + reduce` is the core of functional style in JS.

---

## 1. forEach
Runs a function for every element. **Returns undefined.**

```js
const nums = [1, 2, 3];
nums.forEach((n, index) => {
  console.log(index, n);
});
// Does not return a new array
```

---

## 2. map
Transforms every element → **returns a new array** of the same length.

```js
const nums = [1, 2, 3];
const doubled = nums.map(n => n * 2);
console.log(doubled); // [2, 4, 6]
console.log(nums);    // [1, 2, 3] (original unchanged)
```

**Memory view:**  
Creates a brand new array in memory. Original stays untouched.

---

## 3. filter
Keeps only elements that pass a test → **returns a new array** (usually shorter).

```js
const nums = [1, 2, 3, 4, 5, 6];
const evens = nums.filter(n => n % 2 === 0);
console.log(evens); // [2, 4, 6]
```

---

## 4. reduce
Boils the array down to a **single value**.

```js
const nums = [1, 2, 3, 4];
const sum = nums.reduce((acc, curr) => acc + curr, 0);
console.log(sum); // 10
```

```
Step by step:
acc = 0, curr = 1 → 1
acc = 1, curr = 2 → 3
acc = 3, curr = 3 → 6
acc = 6, curr = 4 → 10
```

---

## 5. find / findIndex / some / every

```js
const users = [
  { id: 1, name: "Alex" },
  { id: 2, name: "Sam" }
];

users.find(u => u.id === 2);       // { id: 2, name: "Sam" }
users.findIndex(u => u.id === 2);  // 1
users.some(u => u.name === "Alex"); // true
users.every(u => u.id > 0);         // true
```

---

## Quick Comparison

| Method | Returns | Changes original? | Use case |
|--------|---------|-------------------|----------|
| forEach | undefined | No | Just side effects |
| map | New array | No | Transform each item |
| filter | New array | No | Keep some items |
| reduce | Single value | No | Sum, object, anything |
| find | Single item | No | First match |

---

## Interview Expectation

| Question | Strong Answer |
|----------|---------------|
| Difference between map and forEach? | map returns new array, forEach returns undefined |
| Can reduce do everything map/filter can? | Yes, but readability suffers |
| Does map mutate? | No, it returns a new array |

---

## Practice
```js
const products = [
  { name: "Phone", price: 500 },
  { name: "Case", price: 20 },
  { name: "Charger", price: 30 }
];

// 1. Get array of prices
// 2. Get products cheaper than 100
// 3. Get total price
```
