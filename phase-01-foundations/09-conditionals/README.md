# Conditionals

**Short Definition:**  
Control flow tools that run different code based on conditions (`if`, `else`, `switch`).

---

## if / else if / else
```js
if (score >= 90) {
  console.log("A");
} else if (score >= 75) {
  console.log("B");
} else {
  console.log("C");
}
```

## switch
```js
switch (day) {
  case "Mon":
    console.log("Start");
    break;
  case "Fri":
    console.log("Almost weekend");
    break;
  default:
    console.log("Normal day");
}
```

## Notes
- `switch` uses strict equality (`===`)
- Always use `break` unless you want fall-through
- Ternary is for simple cases: `condition ? a : b`
