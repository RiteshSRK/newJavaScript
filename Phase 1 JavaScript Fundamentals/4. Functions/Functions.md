## 1. Function Declaration

> A function declared using the function keyword with a name directly in the code.

✅ Syntax:

```js
function greet() {
  return "Hello!";
}
```

### ✅ Characteristics:

- **Hoisting hota hai** → Means function ko define karne se pehle bhi call kar sakte ho.

- Named function hota hai.

- Code readability ke liye achha hota hai.

- Mostly jab function baar-baar use karna ho, tab best.

### ✅ Example:

```js
sayHello(); // ✅ Works even before definition

function sayHello() {
  console.log("Hello World!");
}
```

## 2. Function Expression

A function ko variable ya constant me store kar dete hain.  
Matlab function ko ek value ki tarah treat karte hain.

✅ Syntax:

```js
const greet = function () {
  return "Hello!";
};
```

### ✅ Characteristics:

- Hoisting nahi hoti → Matlab function ko declare karne se pehle call karoge to error aayega.

- Anonymous ya Named dono ho sakta hai.

- Useful when function ko as a value pass karna ho (callbacks, higher-order functions, etc.).

- Flexible hota hai.

### ✅ Example:

```js
sayHello(); // ❌ Error: Cannot access 'sayHello' before initialization

const sayHello = function() {
  console.log("Hello World!");
};
sayHello(); // ✅ Works
```

---

## 🔥 Arrow Functions in JavaScript

> Arrow functions were introduced in ES6 (2015). They are a shorter syntax for function expressions.

## Syntax
### Normal Function Expression:

```js
const add = function(a, b) {
  return a + b;
};
```

### Arrow Function:

```js
const add = (a, b) => {
  return a + b;
};
```

👉 Agar function single line `return` hai, to `return` aur `{}` dono hata sakte ho:

```js
const add = (a, b) => a + b;
```

## 🔹 Characteristics of Arrow Functions

- Shorter syntax – Compact aur readable.

- No `this` binding – Arrow function apna khud ka `this` nahi banata,
balki **parent scope ka `this` use karta hai**.

- Not hoisted – Ye function expression jaisa hi behave karta hai.
Matlab, declaration se pehle use nahi kar sakte.

- No `arguments` object – Normal function ke paas `arguments` object hota hai, arrow ke paas nahi.

- Best use – Callbacks, array methods, short utility functions.

## All Types of Arrow Functions in JavaScript

| Type                            | Syntax                         | Example                                                                                      | Output                  |
| ------------------------------- | ------------------------------ | -------------------------------------------------------------------------------------------- | ----------------------- |
| **No Parameter**                | `() => expression`             | `js const greet = () => "Hello!"; console.log(greet()); `                                    | `Hello!`                |
| **Single Parameter**            | `param => expression`          | `js const square = x => x * x; console.log(square(4)); `                                     | `16`                    |
| **Multiple Parameters**         | `(a, b) => expression`         | `js const add = (a, b) => a + b; console.log(add(2, 3)); `                                   | `5`                     |
| **Block Body (with return)**    | `(a, b) => { return a * b; }`  | `js const mul = (a, b) => { return a * b; }; console.log(mul(2, 3)); `                       | `6`                     |
| **No Return (void)**            | `() => { statement }`          | `js const log = () => { console.log("Hi!"); }; log(); `                                      | `Hi!`                   |
| **Returning Object**            | `() => ({ key: value })`       | `js const getObj = () => ({ name: "Ritesh" }); console.log(getObj()); `                      | `{ name: "Ritesh" }`    |
| **Default Parameters**          | `(a=1, b=2) => a + b`          | `js const sum = (a=1, b=2) => a + b; console.log(sum()); `                                   | `3`                     |
| **Rest Parameters**             | `(...args) => {}`              | `js const total = (...nums) => nums.reduce((a, b) => a + b, 0); console.log(total(1,2,3)); ` | `6`                     |
| **Nested Arrow Function**       | `() => () => value`            | `js const outer = () => () => "Nested!"; console.log(outer()()); `                           | `Nested!`               |
| **With `this` (lexical scope)** | `() => { console.log(this); }` | `js const obj = { name:"RK", show: () => console.log(this) }; obj.show(); `                  | Global `this` (not obj) |

---

| Type                              | Syntax Example                              | Description                                            |
| --------------------------------- | ------------------------------------------- | ------------------------------------------------------ |
| **No Parameter**                  | `const greet = () => console.log("Hello");` | Used when there are no parameters.                     |
| **Single Parameter**              | `const square = x => x * x;`                | For one parameter, parentheses are optional.           |
| **Multiple Parameters**           | `const add = (a, b) => a + b;`              | For two or more parameters, parentheses are required.  |
| **Single-line (Implicit return)** | `const sum = (a, b) => a + b;`              | No need to write `{}` and `return` (automatic return). |
| **Multi-line (Explicit return)**  | `const calc = (a, b) => { return a + b; };` | Use `{}` and `return` for multi-line logic.            |
| **Returning Object**              | `const obj = () => ({ name: "Ritesh" });`   | Wrap the object in parentheses to return it correctly. |
| **As a Callback**                 | `arr.forEach(n => console.log(n));`         | Common in array methods or event listeners.            |
