# Numbers & Math

**Short Definition:**  
All numbers in JavaScript are 64-bit floating point. There is no separate integer type (except BigInt).

---

## Key Methods
```js
(3.14159).toFixed(2)    // "3.14" (returns string)
parseInt("42px")        // 42
parseFloat("3.14abc")   // 3.14
Number("42")            // 42
Number("42px")          // NaN
isNaN(NaN)              // true
Number.isNaN(NaN)       // true (better)
```

## Math Object
```js
Math.round(4.7)     // 5
Math.floor(4.7)     // 4
Math.ceil(4.1)      // 5
Math.max(1,5,3)     // 5
Math.min(1,5,3)     // 1
Math.random()       // 0–1
Math.pow(2,3)       // 8
Math.sqrt(16)       // 4
```

## Classic Gotcha
```js
0.1 + 0.2 === 0.3   // false (floating point)
```

## Interview
- `toFixed` returns string
- Prefer `Number.isNaN` over `isNaN`
