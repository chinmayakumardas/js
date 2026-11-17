# Loops

**Short Definition:**  
Repeat code until a condition is false. Main types: `for`, `while`, `do...while`, `for...of`, `for...in`.

---

## Classic for
```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

## while
```js
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```

## do...while
Runs at least once.
```js
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);
```

## for...of (values)
```js
const arr = ["a", "b", "c"];
for (const item of arr) {
  console.log(item);
}
```

## for...in (keys)
```js
const obj = { x: 1, y: 2 };
for (const key in obj) {
  console.log(key, obj[key]);
}
```

## break & continue
```js
for (let i = 0; i < 10; i++) {
  if (i === 3) continue;  // skip 3
  if (i === 7) break;     // stop
  console.log(i);
}
```

## Interview
- Prefer `for...of` for arrays
- Avoid `for...in` on arrays (it gives keys + inherited)
