## Loops in JavaScript

> Loops are used to repeat code multiple times until a condition is met.

### 1. `for` Loop

- Repeats a block of code a specified number of times.

👉 Syntax:

```js
for (initialization; condition; increment/decrement) {
   // code block
}
```

👉 Example:

```js
for (let i = 1; i <= 5; i++) {
  console.log("Number:", i);
}
// Output: 1 2 3 4 5
```

### 2. `while` Loop

- Executes while a condition is true.

```js
let i = 1;
while (i <= 5) {
  console.log("Count:", i);
  i++;
}
```

```js
let count = 0;
while (count < 5) {
  console.log(count); // 0, 1, 2, 3, 4
  count++;
}

// Infinite loop (be careful!)
// while (true) { console.log("This will run forever"); }
```

### 3. `do...while` Loop

- Similar to `while`, but it runs **at least once** even if condition is false.

👉 Example:

```js
let i = 6;
do {
  console.log("Value:", i);
  i++;
} while (i <= 5);

// Output: Value: 6 (runs once)
```

### 4. `for...of` Loop

- Iterates over values of an iterable (Array, String, Map, Set).

- Best for arrays and strings.

👉 Example:

```js
// Array iteration
const colors = ['red', 'green', 'blue'];
for (const color of colors) {
  console.log(color);
}


let arr = [10, 20, 30];
for (let value of arr) {
  console.log(value);
}
// Output: 10 20 30
```

```js
// String iteration
const str = 'hello';
for (const char of str) {
  console.log(char); // h, e, l, l, o
}
```

### 5. `for...in` Loop

- Iterates over keys (property names) of an object.

- Best for objects.

👉 Example:

```js
let user = { name: "Ritesh", age: 22, city: "Delhi" };

for (let key in user) {
  console.log(key, ":", user[key]);
}
// Output: name : Ritesh, age : 22, city : Delhi
```

```js
const person = {
  name: 'John',
  age: 30,
  job: 'developer'
};

for (const key in person) {
  console.log(`${key}: ${person[key]}`);
  // Output:
  // name: John
  // age: 30
  // job: developer
}
```

### ⚡ Quick Tip for Interviews:

- Use `for` when you know the iteration count.

- Use `while` when you don’t.

- Use `do...while` if you must run at least once.

- Use `for...of` for arrays/strings.

- Use `for...in` for objects.

### Q1. Difference between for...in and for...of?
- 👉 `for...in` iterates over **keys** (**indexes/properties**).
- 👉 `for...of` iterates over **values**.

---

## Break & Continue in JavaScript
### 1. break Statement

- Used to **exit the loop immediately**, even if the loop condition is still true.

- Control goes outside the loop.

👉 Example (stop when number = 5):

```js
for (let i = 1; i <= 10; i++) {
  if (i === 5) {
    break; // loop will stop here
  }
  console.log(i);
}
// Output: 1 2 3 4
```

### 👉 With `while`:

```js
let i = 1;
while (i <= 10) {
  if (i === 5) break;
  console.log(i);
  i++;
}
// Output: 1 2 3 4
```

### 2. continue Statement

- Used to **skip the current iteration** and move to the next iteration.

- Loop doesn’t stop; it just ignores that particular round.

👉 Example (skip number = 5):

```js
for (let i = 1; i <= 10; i++) {
  if (i === 5) {
    continue; // skip 5
  }
  console.log(i);
}
// Output: 1 2 3 4 6 7 8 9 10
```

👉 With `while`:

```js
let i = 0;
while (i < 7) {
  i++;
  if (i === 4) continue;
  console.log(i);
}
// Output: 1 2 3 5 6 7
```

## 🎯 Interview-style Q&A

### Q1. What is the difference between `break` and `continue`?
> 👉 `break` exits the loop completely, while `continue` skips the current iteration and moves to the next one.
