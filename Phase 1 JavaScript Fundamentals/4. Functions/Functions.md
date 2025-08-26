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

👉 Agar function single line return hai, to return aur {} dono hata sakte ho:

```js
const add = (a, b) => a + b;
```