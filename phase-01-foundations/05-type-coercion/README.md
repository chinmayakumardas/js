# 05 — Type Conversion vs Type Coercion

**Level:** Beginner → Intermediate  
**Interview Weight:** Extremely High

---

## 1. Why this is critical

Most confusing interview questions and real bugs come from coercion.  
If you master this topic, you look senior even as a junior.

**Conversion** = you do it explicitly (`Number("5")`)  
**Coercion** = JavaScript does it automatically (`"5" + 2`)

---

## 2. Explicit Conversion

```js
Number("42")       // 42
Number("42px")     // NaN
Number(true)       // 1
Number(false)      // 0
Number(null)       // 0
Number(undefined)  // NaN

String(123)        // "123"
String(true)       // "true"
String(null)       // "null"

Boolean(0)         // false
Boolean("")        // false
Boolean(null)      // false
Boolean(undefined) // false
Boolean(NaN)       // false
Boolean("0")       // true   ← non-empty string is truthy
Boolean([])        // true   ← empty array is truthy
Boolean({})        // true
```

---

## 3. Implicit Coercion (the dangerous one)

### With `+` (string wins if any operand is string)

```js
"5" + 2          // "52"
2 + "5"          // "25"
"5" + 2 + 3      // "523"
2 + 3 + "5"      // "55"
true + 1         // 2
null + 1         // 1
undefined + 1    // NaN
```

### With `-`, `*`, `/` (number conversion)

```js
"5" - 2          // 3
"5" * "2"        // 10
"5" / 2          // 2.5
"5px" - 1        // NaN
```

### Loose equality `==` (coerces)

```js
0 == false       // true
"" == false      // true
null == undefined // true
[] == false      // true
[] == ![]        // true   (famous)
"0" == false     // true
```

### Strict equality `===` (no coercion)

```js
0 === false      // false
"" === false     // false
null === undefined // false
```

**Rule of thumb:** Always prefer `===` and `!==` unless you have a very good reason.

---

## 4. Falsy Values (memorize these)

Only these are falsy:
```
false, 0, -0, 0n, "", null, undefined, NaN
```

Everything else is truthy (including `[]`, `{}`, `"0"`, `"false"`).

---

## 5. Interview Questions

**Q1.** What is the difference between `==` and `===`?  
**Q2.** List all falsy values.  
**Q3.** What is the output of `[] == ![]` and why?  
**Q4.** Predict: `"5" + 3`, `"5" - 3`, `true + false`, `null + 1`  
**Q5.** Why is `Boolean([])` true but `[] == false` also true?  
**Q6.** How would you convert a string to number safely?

**Strong Answer Example:**  
“`==` does type coercion, `===` does not. I almost always use `===` because coercion rules are hard to remember and lead to bugs. Falsy values are: false, 0, -0, 0n, empty string, null, undefined, NaN.”

---

## 6. Practice (predict first)

```js
console.log("5" + 2);
console.log("5" - 2);
console.log([] + []);
console.log([] + {});
console.log({} + []);
console.log(true + false);
console.log(null + 1);
console.log(undefined + 1);
console.log([] == false);
console.log("" == false);
console.log(0 == "0");
console.log(0 === "0");
```
