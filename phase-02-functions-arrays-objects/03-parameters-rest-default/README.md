# Parameters, Default & Rest

**Short Definition:**  
How functions receive input. Default parameters give fallback values. Rest (`...args`) collects remaining arguments into an array.

---

## Parameters vs Arguments
- Parameters = names in function definition
- Arguments = actual values passed when calling

```js
function greet(name) {        // name is parameter
  console.log("Hi", name);
}
greet("Alex");                // "Alex" is argument
```

## Default Parameters
```js
function greet(name = "Guest") {
  console.log("Hi", name);
}
greet();          // Hi Guest
greet("Sam");     // Hi Sam
```

## Rest Parameters
```js
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}
sum(1, 2, 3, 4);   // 10
```

## Interview
- Rest must be the last parameter
- `arguments` object exists in regular functions but not in arrow functions
