# Taking User Input

**Short Definition:**  
In the browser you can use `prompt()`, `alert()`, and `confirm()` for quick input/output.

---

```js
const name = prompt("What is your name?");
alert("Hello, " + name);

const yes = confirm("Are you sure?");
if (yes) {
  console.log("User said yes");
}
```

## Notes
- `prompt` always returns a string (or null if cancelled)
- Convert with `Number(prompt("Age?"))`
- These are blocking and mainly for learning / quick demos
