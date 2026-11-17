# Strings

**Short Definition:**  
Text data. Strings are primitive and immutable.

---

## Creating
```js
const a = "hello";
const b = 'world';
const c = `template ${a}`;  // template literal
```

## Common Methods
```js
str.length
str.toUpperCase()
str.toLowerCase()
str.slice(start, end)
str.substring(start, end)
str.indexOf("x")
str.includes("x")
str.split(" ")
str.trim()
str.replace("old", "new")
```

## Important
```js
"hello".length          // 5
"  hi  ".trim()         // "hi"
"a,b,c".split(",")      // ["a","b","c"]
```

## Interview
- Strings are immutable
- `slice` accepts negative indexes, `substring` does not
