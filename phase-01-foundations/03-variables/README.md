# 03 — Variables (`var`, `let`, `const`)

**Interview Weight:** High

---

## Why this matters

Almost every interview asks the difference between `var`, `let`, and `const`.  
This is also the foundation for understanding scope and Temporal Dead Zone later.

---

## The three keywords

| Keyword | Scope | Hoisting | Can redeclare? | Can reassign? |
|---------|-------|----------|----------------|---------------|
| `var` | Function | Yes (initialized as `undefined`) | Yes | Yes |
| `let` | Block | Yes (TDZ) | No | Yes |
| `const` | Block | Yes (TDZ) | No | No |

```js
// var is function-scoped
function test() {
  if (true) {
    var x = 10;
  }
  console.log(x); // 10 (still accessible)
}

// let / const are block-scoped
function test2() {
  if (true) {
    let y = 20;
    const z = 30;
  }
  // console.log(y); // ReferenceError
}
```

---

## Temporal Dead Zone (TDZ)

```js
console.log(a); // undefined (var is hoisted and initialized)
var a = 5;

console.log(b); // ReferenceError (TDZ)
let b = 10;
```

---

## `const` does not make objects immutable

```js
const user = { name: "Alex" };
user.name = "Sam";     // allowed
// user = {}           // TypeError — cannot reassign the binding
```

---

## Best Practice (2024+)

- Use `const` by default.
- Use `let` only when you need to reassign.
- Avoid `var` in new code.

---

## Interview Questions

1. Difference between `var`, `let`, and `const`?
2. What is Temporal Dead Zone?
3. Is `const` immutable? Prove it.
4. Can you redeclare a `let` variable in the same scope?
5. What is the output of this hoisting example?
