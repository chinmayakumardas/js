# Top 100 JavaScript Interview Questions + Answers

**How to practice:** Cover answer → speak out loud in 30–60 sec → check.

**Answer format that scores high:**
1. One-line definition
2. Small example
3. Common pitfall
4. Real use / why it matters

---

## PHASE 1 — Foundations (1–25)

**1. What are the primitive types in JavaScript?**  
string, number, boolean, null, undefined, symbol, bigint.

**2. What does `typeof null` return and why?**  
`"object"`. Legacy bug from 1995. Null was represented as a null pointer (type tag 0), same as objects. Never fixed for backward compatibility.

**3. Difference between `null` and `undefined`?**  
`undefined` = declared but not assigned (or missing).  
`null` = intentional empty value set by developer.

**4. List all falsy values.**  
`false`, `0`, `-0`, `0n`, `""`, `null`, `undefined`, `NaN`.

**5. Difference between `==` and `===`?**  
`==` performs type coercion. `===` does not. Always prefer `===`.

**6. What is type coercion?**  
Automatic conversion of one type to another by the JS engine (e.g. `"5" + 2` → `"52"`).

**7. Predict: `"5" + 2` and `"5" - 2`**  
`"52"` and `3`.

**8. Why is `[] == ![]` true?**  
`![]` becomes `false`. `[]` coerced to primitive becomes `""`. `"" == false` is true.

**9. Difference between `var`, `let` and `const`?**  
- `var`: function-scoped, hoisted as `undefined`, can redeclare  
- `let`: block-scoped, TDZ, cannot redeclare  
- `const`: block-scoped, TDZ, cannot reassign the binding

**10. What is Temporal Dead Zone (TDZ)?**  
Period from entering scope until the `let`/`const` declaration is executed. Accessing the variable in TDZ throws ReferenceError.

**11. Is `const` immutable?**  
No. The binding cannot be reassigned, but object properties can still be changed.

**12. How do you correctly check if a value is an array?**  
`Array.isArray(value)`

**13. Why is `0.1 + 0.2 !== 0.3`?**  
Floating-point precision issue (IEEE-754). Numbers are 64-bit floats.

**14. Difference between `for...of` and `for...in`?**  
`for...of` iterates values of iterables.  
`for...in` iterates keys of objects (including inherited).

**15. What does `toFixed` return?**  
A string.

**16. Difference between `parseInt` and `Number`?**  
`parseInt` parses until non-numeric character. `Number` is stricter and returns `NaN` on invalid input.

**17. What is short-circuit evaluation?**  
`&&` and `||` stop evaluating as soon as the result is determined.  
Example: `0 || "default"` → `"default"`.

**18. What is the ternary operator?**  
`condition ? valueIfTrue : valueIfFalse`

**19. Difference between `null` and empty object `{}`?**  
`null` is primitive empty. `{}` is a valid object with no properties.

**20. How do you reverse a string?**  
`str.split("").reverse().join("")`

**21. How do you check if a string is a palindrome?**  
Compare string with its reverse (ignore case/spaces if required).

**22. What is FizzBuzz?**  
Print 1–100: multiple of 3 → Fizz, 5 → Buzz, both → FizzBuzz.

**23. What does `typeof NaN` return?**  
`"number"`

**24. What does `typeof []` return?**  
`"object"` (use `Array.isArray` instead)

**25. What does `typeof function(){}` return?**  
`"function"` (special case of object)

---

## PHASE 2 — Functions, Arrays, Objects (26–50)

**26. Function declaration vs function expression?**  
Declaration is fully hoisted. Expression is not (variable is hoisted as `undefined`).

**27. Does an arrow function have its own `this`?**  
No. It lexically inherits `this` from the outer scope.

**28. Can you use `new` with an arrow function?**  
No. Arrow functions do not have a `prototype` and cannot be used as constructors.

**29. What is a callback function?**  
A function passed as an argument to another function that is called later.

**30. What is a higher-order function?**  
A function that takes another function as argument or returns a function.

**31. Difference between `map` and `forEach`?**  
`map` returns a new array. `forEach` returns `undefined`.

**32. What does `reduce` do?**  
Reduces an array to a single value using an accumulator function.

**33. Does `map` mutate the original array?**  
No. It returns a new array.

**34. Difference between `push`/`pop` and `shift`/`unshift`?**  
`push`/`pop` work at the end. `shift`/`unshift` work at the beginning (slower).

**35. How does `sort` work without a compare function?**  
Converts elements to strings and sorts lexicographically.

**36. What is array destructuring?**  
Extracting values from an array into variables cleanly.  
`const [a, b] = [1, 2]`

**37. What is object destructuring?**  
Extracting properties into variables.  
`const { name, age } = user`

**38. Dot notation vs bracket notation?**  
Bracket is required for dynamic keys or keys with spaces/special characters.

**39. How do you shallow clone an object?**  
`{ ...obj }` or `Object.assign({}, obj)`

**40. What does `Object.freeze` do?**  
Prevents adding, removing, or changing properties.

**41. What does `Object.keys / values / entries` return?**  
Arrays of keys, values, or [key, value] pairs.

**42. What is the `arguments` object?**  
Array-like object available inside regular functions containing all passed arguments. Not available in arrow functions.

**43. What are rest parameters?**  
`...args` collects remaining arguments into a real array. Must be last parameter.

**44. What are default parameters?**  
Fallback values used when argument is `undefined`.  
`function f(x = 10) {}`

**45. What is an IIFE?**  
Immediately Invoked Function Expression. Runs as soon as it is defined. Used to create private scope.

**46. Pure function vs impure function?**  
Pure: same input → same output, no side effects.  
Impure: depends on or modifies external state.

**47. What is recursion?**  
A function calling itself until a base condition is met.

**48. How do you flatten a nested array (basic)?**  
`arr.flat()` or `arr.flat(Infinity)` or reduce + concat.

**49. Difference between `slice` and `splice`?**  
`slice` (non-mutating) returns a piece.  
`splice` (mutating) can add/remove elements.

**50. How do you check if an object is empty?**  
`Object.keys(obj).length === 0`

---

## PHASE 3 — Execution Context, Scope, Closures (51–70)

**51. What is an Execution Context?**  
The environment in which JS code is evaluated. Contains variable environment, scope chain, and `this`.

**52. What are the two phases of Execution Context?**  
1. Creation phase (memory allocation / hoisting)  
2. Execution phase (code runs line by line)

**53. What is the Call Stack?**  
A LIFO data structure that tracks which function is currently being executed.

**54. What causes a Stack Overflow?**  
Too many nested function calls (usually infinite recursion).

**55. What is Hoisting?**  
JS moves declarations to the top of their scope during the Creation phase.

**56. How does hoisting differ for `var`, `let`, `const`?**  
`var` → hoisted and initialized as `undefined`.  
`let`/`const` → hoisted but stay in Temporal Dead Zone.

**57. What is Scope?**  
The region of code where a variable is accessible.

**58. What is Lexical Scope?**  
Scope is determined by the location where the code is written (not where it is called).

**59. What is the Scope Chain?**  
When a variable is not found in current scope, JS looks outward into parent scopes until global.

**60. What is a Closure?**  
A function that remembers the variables from the outer environment where it was created, even after that outer function has finished executing.

**61. Give a practical use of closures.**  
Data privacy / private variables, function factories, currying, module pattern, React hooks internals.

**62. Explain the classic loop + closure problem.**  
With `var`, all timeouts share the same `i`. With `let`, each iteration gets its own block-scoped `i`.

**63. What is a function factory?**  
A function that returns another function (often customized by parameters), usually using closures.

**64. What is currying?**  
Transforming a function with multiple arguments into a sequence of functions each taking a single argument.

**65. Difference between scope and context?**  
Scope → variable visibility.  
Context (`this`) → value of `this` inside the function.

**66. Can you create private variables in JavaScript?**  
Yes, using closures.

**67. What happens when a function returns another function?**  
The returned function keeps a reference to the outer variables (closure is created).

**68. What is Global Execution Context?**  
The base context created when the script first runs. Only one exists.

**69. What is Function Execution Context?**  
Created every time a function is invoked. Pushed onto the Call Stack.

**70. Why do we need closures?**  
They enable powerful patterns: encapsulation, callbacks that remember state, partial application, modules.

---

## PHASE 4 — `this`, Prototypes, Classes (71–85)

**71. How is `this` determined?**  
By how the function is called (method call, `new`, `call`/`apply`/`bind`, arrow, or default).

**72. Difference between regular function and arrow function regarding `this`?**  
Regular → `this` depends on call site.  
Arrow → `this` is lexical (from outer scope).

**73. What do `call`, `apply` and `bind` do?**  
They let you set `this` explicitly.  
`call`/`apply` invoke immediately (`apply` takes array of args).  
`bind` returns a new function with `this` permanently bound.

**74. Difference between `call` and `apply`?**  
`call(thisArg, a, b, c)`  
`apply(thisArg, [a, b, c])`

**75. What is a prototype?**  
An object from which other objects inherit properties and methods.

**76. Difference between `__proto__` and `prototype`?**  
`obj.__proto__` → the actual prototype of that instance.  
`Func.prototype` → the object that becomes `__proto__` of instances created by `new Func()`.

**77. What is the Prototype Chain?**  
The chain of links (`__proto__`) that JS follows when looking up a property.

**78. How does inheritance work via prototypes?**  
Objects inherit from other objects through the prototype chain.

**79. What is `Object.create`?**  
Creates a new object with the specified object as its prototype.

**80. Are ES6 classes syntactic sugar?**  
Yes. They are cleaner syntax over constructor functions + prototypes.

**81. What is the difference between static and instance methods?**  
Static methods are called on the class itself. Instance methods are called on instances.

**82. What are getters and setters?**  
Special methods that run when a property is read or written.

**83. What are private fields (`#`)?**  
True private properties that cannot be accessed outside the class body.

**84. How does the `new` keyword work?**  
1. Create empty object  
2. Set its `__proto__` to constructor’s `prototype`  
3. Bind `this` to the new object  
4. Return the object (unless constructor returns another object)

**85. What is the value of `this` in the global scope?**  
Browser → `window`. Node → `global` (or `undefined` in strict mode / ES modules).

---

## PHASE 5 — Asynchronous JavaScript (86–100)

**86. Difference between synchronous and asynchronous code?**  
Sync → blocks until finished.  
Async → doesn’t block; continues and handles result later.

**87. What is the Event Loop?**  
Mechanism that decides what runs next when the Call Stack is empty. Prioritizes Microtasks over Macrotasks.

**88. Microtask Queue vs Macrotask Queue?**  
Microtasks (Promises, `queueMicrotask`) run completely before the next Macrotask.  
Macrotasks (`setTimeout`, I/O, UI) run one at a time.

**89. What is a Promise and its states?**  
Object representing a future value. States: `pending` → `fulfilled` or `rejected`.

**90. Difference between `.then` chaining and `async/await`?**  
`async/await` is syntactic sugar over Promises. Makes async code look synchronous and easier to read/handle errors.

**91. How do you handle errors with Promises vs async/await?**  
Promises → `.catch()`  
async/await → `try/catch`

**92. What does `Promise.all` do? When does it reject?**  
Runs promises in parallel. Rejects immediately if any promise rejects.

**93. Difference between `Promise.all`, `allSettled`, `race`, `any`?**  
- `all` → fails fast  
- `allSettled` → waits for all  
- `race` → first settled  
- `any` → first fulfilled

**94. What happens if you forget `await`?**  
You get a Promise object instead of the resolved value. Execution continues without waiting.

**95. What is callback hell?**  
Deeply nested callbacks that make code hard to read and maintain. Solved by Promises / async-await.

**96. Predict output: `console.log(1); setTimeout(() => console.log(2), 0); Promise.resolve().then(() => console.log(3)); console.log(4);`**  
1 4 3 2

**97. What does `fetch` return?**  
A Promise that resolves to a Response object.

**98. How do you parse and stringify JSON?**  
`JSON.parse(string)` and `JSON.stringify(object)`

**99. How do you run async tasks in parallel vs sequential?**  
Parallel → `Promise.all([p1, p2, p3])`  
Sequential → `await p1; await p2; await p3`

**100. Write a simple retry idea for a failed fetch.**  
Use a loop (or recursion) with try/catch, wait a bit, and retry limited times.

---

## Quick Depth Guide

| Level | What interviewer expects |
|-------|--------------------------|
| Junior | Correct definition + simple example |
| Mid | + Common pitfall + when to use |
| Strong | + Under-the-hood behavior + related concepts |

Always speak in this order: **Definition → Example → Pitfall → Use case**.
