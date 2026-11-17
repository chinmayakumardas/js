# First-class Functions, Callbacks & Higher-Order Functions

**Short Definition:**  
In JavaScript, functions are values. You can store them in variables, pass them as arguments, and return them from other functions.

---

## First-class Citizens
```js
const fn = function() { return 1; };
const arr = [fn];
const obj = { f: fn };
```

## Callback
A function passed into another function to be called later.
```js
function process(name, callback) {
  callback(name);
}
process("Alex", function(n) {
  console.log("Hello", n);
});
```

## Higher-Order Function (HOF)
A function that takes another function as argument **or** returns a function.
```js
// takes function
[1,2,3].map(n => n * 2);

// returns function
function multiplier(factor) {
  return function(n) {
    return n * factor;
  };
}
const double = multiplier(2);
double(5); // 10
```

## Interview
map, filter, reduce, forEach, setTimeout → all use callbacks / are HOFs.
