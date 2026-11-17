# Phase 5 — Asynchronous JavaScript (Full Visualization)

**Goal:** Master async code. Understand the Event Loop completely.  
Stop being afraid of `async`/`await`.

**Interview Weight:** Extremely High

---

## 1. Why Async Exists

JavaScript has **one call stack**. If a long task (network, timer, file) blocked it, the browser would freeze.

```mermaid
flowchart LR
    A[Long running task] --> B[Blocks Call Stack]
    B --> C[Page freezes]
    C --> D[Bad UX]
```

Solution → Hand the long task to the browser/Web API and continue.

---

## 2. The Big Picture — How Async Really Works

```mermaid
flowchart TD
    A[Call Stack] --> B{Stack empty?}
    B -->|No| A
    B -->|Yes| C[Check Microtask Queue]
    C --> D{Microtasks left?}
    D -->|Yes| E[Run all Microtasks]
    E --> C
    D -->|No| F[Check Macrotask Queue]
    F --> G{Macrotask left?}
    G -->|Yes| H[Run ONE Macrotask]
    H --> A
    G -->|No| I[Wait for next task]
```

### Components

| Component | What it holds | Examples |
|-----------|---------------|----------|
| **Call Stack** | Currently running code | Functions, global code |
| **Web APIs** | Browser features | `setTimeout`, `fetch`, DOM events |
| **Microtask Queue** | High priority async | Promises, `queueMicrotask`, `MutationObserver` |
| **Macrotask Queue** | Lower priority async | `setTimeout`, `setInterval`, I/O, UI rendering |

**Golden Rule:**  
After every task, the engine empties the **entire Microtask queue** before taking the next Macrotask.

---

## 3. setTimeout is NOT a precise timer

```js
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

console.log("End");
```

```mermaid
sequenceDiagram
    participant Stack as Call Stack
    participant WebAPI as Web APIs
    participant Macro as Macrotask Queue

    Stack->>Stack: console.log("Start")
    Stack->>WebAPI: setTimeout(..., 0)
    WebAPI->>Macro: after 0ms put callback
    Stack->>Stack: console.log("End")
    Stack->>Stack: Stack becomes empty
    Macro->>Stack: run timeout callback
    Stack->>Stack: console.log("Timeout")
```

Output:
```
Start
End
Timeout
```

---

## 4. Promises & Microtasks

```js
console.log("A");

setTimeout(() => console.log("B"), 0);

Promise.resolve().then(() => console.log("C"));

console.log("D");
```

```mermaid
sequenceDiagram
    participant Stack as Call Stack
    participant Micro as Microtask Queue
    participant Macro as Macrotask Queue

    Stack->>Stack: console.log("A")
    Stack->>Macro: setTimeout callback
    Stack->>Micro: Promise.then callback
    Stack->>Stack: console.log("D")
    Note over Stack: Stack empty
    Micro->>Stack: run Promise callback → "C"
    Note over Stack: Microtask queue empty
    Macro->>Stack: run setTimeout → "B"
```

**Output: A D C B**

---

## 5. Promise Lifecycle

```mermaid
stateDiagram-v2
    [*] --> Pending
    Pending --> Fulfilled: resolve(value)
    Pending --> Rejected: reject(error)
    Fulfilled --> [*]
    Rejected --> [*]
```

```js
const p = new Promise((resolve, reject) => {
  // executor runs immediately
  resolve("Success");
});

p.then(result => console.log(result))
 .catch(err => console.error(err))
 .finally(() => console.log("Done"));
```

---

## 6. async / await (Under the Hood)

`async/await` is **syntactic sugar** over Promises.

```js
async function load() {
  try {
    const res = await fetch("/api/data");
    const data = await res.json();
    return data;
  } catch (err) {
    console.error(err);
  }
}
```

What actually happens:

```mermaid
flowchart TD
    A[async function called] --> B[Returns a Promise immediately]
    B --> C[await pauses the function]
    C --> D[Rest of the function becomes .then]
    D --> E[If error → goes to catch]
```

---

## 7. Promise Combinators

```js
// Runs in parallel, fails fast
Promise.all([p1, p2, p3]);

// Waits for all, never rejects
Promise.allSettled([p1, p2, p3]);

// First one to settle (resolve or reject)
Promise.race([p1, p2, p3]);

// First one to resolve (ignores rejects until all reject)
Promise.any([p1, p2, p3]);
```

```mermaid
flowchart LR
    A[Promise.all] --> B[All must fulfill]
    C[Promise.race] --> D[First settled wins]
    E[Promise.any] --> F[First fulfilled wins]
    G[Promise.allSettled] --> H[Always waits for all]
```

---

## 8. Classic Event Loop Output Questions

### Question 1
```js
console.log(1);

setTimeout(() => console.log(2), 0);

Promise.resolve().then(() => console.log(3));

console.log(4);
```
**Answer:** 1 4 3 2

### Question 2
```js
async function foo() {
  console.log(1);
  await Promise.resolve();
  console.log(2);
}

console.log(3);
foo();
console.log(4);
```
**Answer:** 3 1 4 2

### Question 3
```js
setTimeout(() => console.log("A"), 0);

Promise.resolve()
  .then(() => {
    console.log("B");
    return Promise.resolve("C");
  })
  .then(console.log);

console.log("D");
```
**Answer:** D B C A

---

## 9. Fetch + JSON

```js
async function getUser(id) {
  try {
    const res = await fetch(`https://api.example.com/users/${id}`);
    if (!res.ok) throw new Error("Network response was not ok");
    const data = await res.json();
    return data;
  } catch (err) {
    console.error("Failed:", err.message);
  }
}
```

---

## 10. Interview Questions You Must Own

1. Explain the Event Loop with a diagram.
2. Difference between Microtask queue and Macrotask queue.
3. What is the output of mixed `setTimeout` + Promise questions?
4. States of a Promise.
5. `Promise.all` vs `Promise.allSettled` vs `Promise.race` vs `Promise.any`.
6. What happens if you forget `await`?
7. How does `async/await` work under the hood?
8. How would you run async tasks in parallel?
9. How would you run them sequentially?
10. Write a retry function for a failed fetch.

---

## Mental Model Summary

```mermaid
flowchart TD
    A[JS Code] --> B[Call Stack]
    B --> C[Web APIs for async work]
    C --> D[Callback / Promise goes to Queue]
    D --> E{Microtask or Macrotask?}
    E -->|Promise| F[Microtask Queue]
    E -->|setTimeout etc| G[Macrotask Queue]
    F --> H[Event Loop checks when Stack is empty]
    G --> H
    H --> B
```
