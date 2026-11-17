# Objects — Advanced

**Short Definition:**  
Useful built-in methods for working with objects + destructuring + spread.

---

## Object Methods
```js
const user = { name: "Alex", age: 25 };

Object.keys(user)      // ["name", "age"]
Object.values(user)    // ["Alex", 25]
Object.entries(user)   // [["name","Alex"], ["age",25]]

Object.assign({}, user)
Object.freeze(user)    // cannot add/remove/change
Object.seal(user)      // cannot add/remove, can change existing
```

## Destructuring
```js
const { name, age } = user;
const { name: userName, age: userAge = 18 } = user; // rename + default
```

## Spread
```js
const copy = { ...user };
const extended = { ...user, city: "Delhi" };
```

## Loop
```js
for (const [key, value] of Object.entries(user)) {
  console.log(key, value);
}
```
