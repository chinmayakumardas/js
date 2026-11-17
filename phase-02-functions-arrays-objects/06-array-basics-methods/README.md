# Array Basics & Common Methods

**Short Definition:**  
Arrays are ordered lists. They are objects under the hood. Many methods either mutate the original array or return a new one.

---

## Creating
```js
const arr = [1, 2, 3];
const arr2 = new Array(5);     // empty slots
const arr3 = Array.of(1, 2);   // [1,2]
```

## Mutating Methods
```js
arr.push(4)        // add at end
arr.pop()          // remove from end
arr.unshift(0)     // add at start
arr.shift()        // remove from start
arr.splice(1, 1)   // remove/replace at index
arr.reverse()
arr.sort()
```

## Non-mutating
```js
arr.slice(1, 3)    // new piece
arr.concat([4,5])  // new combined array
arr.join("-")      // string
arr.indexOf(2)
arr.includes(2)
```

## Interview
Know which methods mutate and which don’t.  
`sort` without compare function converts to string first.
