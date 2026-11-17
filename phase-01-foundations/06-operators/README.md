# Operators

**Short Definition:**  
Symbols that perform operations on values (math, comparison, logic, assignment).

---

## Arithmetic
```js
+  -  *  /  %  **  ++  --
10 % 3    // 1
2 ** 3    // 8
```

## Assignment
```js
=  +=  -=  *=  /=
let x = 5;
x += 3;   // 8
```

## Comparison
```js
==   // loose (coerces)
===  // strict (no coercion) ← prefer this
!=   !==
>  <  >=  <=
```

## Logical
```js
&&  ||  !
true && false   // false
true || false   // true
!true           // false
```

## Ternary
```js
const result = age >= 18 ? "Adult" : "Minor";
```

## Interview
Always prefer `===` over `==`.  
Know short-circuit: `0 || "default"` → `"default"`.
