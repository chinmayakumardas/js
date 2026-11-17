# How Interviewers Think About JavaScript Questions

## What they are really testing

| They ask about... | They are testing... |
|-------------------|---------------------|
| `typeof null` | Did you actually study or just use JS casually? |
| `==` vs `===` | Do you understand coercion? |
| Closures | Can you think beyond syntax? |
| Event Loop | Do you understand how JS actually runs? |
| `this` | Do you know the binding rules? |
| Promises + async/await | Can you write real async code? |

## Answer Pattern That Scores High

1. **One clear definition** (10 seconds)
2. **Tiny code example**
3. **Common pitfall / edge case**
4. **Real-world use** (optional but strong)

### Example

**Q:** What is a closure?

**Weak answer:**  
"A function inside a function."

**Strong answer:**  
"A closure is when a function remembers the variables from the place where it was created, even after that outer function has finished running.  

```js
function counter() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}
const c = counter();
c(); // 1
c(); // 2
```

The inner function still has access to `count` because of the closure.  
Common use cases: data privacy, function factories, and React hooks under the hood."

---

## Topics Ranked by Interview Frequency (Junior → Mid)

1. Closures + Scope
2. Event Loop + Promises + async/await
3. `this` keyword + call/apply/bind
4. Type coercion + `==` vs `===`
5. Hoisting + TDZ
6. Prototypes / Classes
7. Array methods (`map`, `filter`, `reduce`)
8. `let` / `const` / `var`
