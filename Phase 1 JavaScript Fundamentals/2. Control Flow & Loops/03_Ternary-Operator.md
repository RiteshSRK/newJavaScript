## Ternary Operator in JavaScript
## ✅ Definition

> The ternary operator is a short form of `if...else`.

- It has 3 parts → `condition ? expression1 : expression2`

- If condition is true → `expression1` runs.

- If condition is false → `expression2` runs.

👉 Example:

```js
let age = 20;
let result = (age >= 18) ? "Adult" : "Minor";
console.log(result); 
// Output: Adult
```

👉 With function return:

```js
function checkVote(age) {
  return (age >= 18) ? "You can vote" : "You cannot vote";
}
console.log(checkVote(16)); // Output: You cannot vote
```

👉 Using inside template literals:

```js
let isLoggedIn = true;
console.log(`User is ${isLoggedIn ? "online" : "offline"}`);
// Output: User is online
```

## 🎯 Interview-style Q&A

### Q1. What is the ternary operator in JavaScript?
- 👉 It’s a shorthand for `if...else`, syntax → `condition ? expr1 : expr2`.

### Q4. Where is the ternary operator mostly used?
- 👉 In short decisions like **UI rendering**, **inline conditions**, **JSX (React)**.