# 04 — Data Types & `typeof`

**Level:** Beginner  
**Interview Weight:** Very High

---

## 1. Why this topic exists

JavaScript is dynamically typed. A variable does not have a type — the **value** has a type.  
If you don’t understand the 7 primitives + objects, you will keep getting surprised by `typeof`, equality, and coercion bugs.

---

## 2. The 7 Primitive Types

| Type | Example | Notes |
|------|---------|-------|
| `string` | `"hello"`, `'hi'`, `` `template` `` | Text is immutable |
| `number` | `42`, `3.14`, `NaN`, `Infinity` | All numbers are 64-bit floats |
| `boolean` | `true`, `false` | |
| `null` | `null` | Intentionally empty |
| `undefined` | `undefined` | Not assigned / missing |
| `symbol` | `Symbol("id")` | Unique identifier (ES6) |
| `bigint` | `10n`, `9007199254740993n` | For integers bigger than `Number.MAX_SAFE_INTEGER` |

Everything else is an **object** (including arrays, functions, dates, regex, etc.).

---

## 3. `typeof` Operator

```js
typeof "hello"        // "string"
typeof 42             // "number"
typeof true           // "boolean"
typeof undefined      // "undefined"
typeof Symbol()       // "symbol"
typeof 10n            // "bigint"
typeof {}             // "object"
typeof []             // "object"   ← arrays are objects
typeof function(){}   // "function" ← special case
typeof null           // "object"   ← famous legacy bug
```

### The `typeof null` bug

```js
typeof null === "object"   // true (this is a bug from 1995 that was never fixed)
```

**Interview answer:**  
“It’s a legacy bug from the original JavaScript implementation. `null` was represented as a null pointer (type tag 0), which was the same as the object type tag. The bug was never fixed because too much existing code depended on it.”

---

## 4. Primitive vs Non-Primitive (Reference)

```js
// Primitives are copied by value
let a = 10;
let b = a;
b = 20;
console.log(a); // 10  (a did not change)

// Objects are copied by reference
let obj1 = { name: "Alex" };
let obj2 = obj1;
obj2.name = "Sam";
console.log(obj1.name); // "Sam"  (both point to same object)
```

---

## 5. Common Mistakes

```js
// ❌ Thinking arrays are a separate type
typeof [] === "array"     // false

// ✅ Correct way to check array
Array.isArray([])         // true

// ❌ Using typeof to check for null
if (typeof value === "object") { ... }  // also catches null and arrays

// ✅ Better null check
if (value === null) { ... }
```

---

## 6. Interview Questions (This Topic)

**Q1.** What are the primitive types in JavaScript?  
**Q2.** What does `typeof null` return and why?  
**Q3.** What is the difference between `null` and `undefined`?  
**Q4.** How do you check if a value is an array?  
**Q5.** Are functions objects in JavaScript? Prove it.  
**Q6.** Predict: `typeof NaN`, `typeof []`, `typeof function(){}`

**Sample Answer Style (say this out loud):**  
“There are 7 primitives: string, number, boolean, null, undefined, symbol, bigint. Everything else is an object. `typeof null` returns `'object'` because of a legacy bug from 1995 that was never fixed for backward compatibility.”

---

## 7. Practice

```js
// Predict first, then run
console.log(typeof NaN);
console.log(typeof null);
console.log(typeof []);
console.log(typeof function(){});
console.log(typeof 10n);
console.log(typeof Symbol("x"));
```
