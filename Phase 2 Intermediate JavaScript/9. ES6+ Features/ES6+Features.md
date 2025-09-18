### Variables in JavaScript (`var`, `let`, `const`)

- `var`: Function scoped, can be **redeclared** and **updated**.

- `let`: Block scoped, can be **updated** but **not redeclared**.

- `const`: Block scoped, **cannot be updated** or **redeclared**.


### 3. Arrow Functions (ES6)

- A shorter syntax for writing functions, introduced in ES6.

- They not have its own `this` → inherits from lexical scope.

```js
const add = (a, b) => {
  return a + b;
};
```

```js
const add = (a, b) => a + b;
```

| Type                              | Syntax Example                              | Description                                            |
| --------------------------------- | ------------------------------------------- | ------------------------------------------------------ |
| **No Parameter**                  | `const greet = () => console.log("Hello");` | Used when there are no parameters.                     |
| **Single Parameter**              | `const square = x => x * x;`                | For one parameter, parentheses are optional.           |
| **Multiple Parameters**           | `const add = (a, b) => a + b;`              | For two or more parameters, parentheses are required.  |
| **Single-line (Implicit return)** | `const sum = (a, b) => a + b;`              | No need to write `{}` and `return` (automatic return). |
| **Multi-line (Explicit return)**  | `const calc = (a, b) => { return a + b; };` | Use `{}` and `return` for multi-line logic.            |
| **Returning Object**              | `const obj = () => ({ name: "Ritesh" });`   | Wrap the object in parentheses to return it correctly. |
| **As a Callback**                 | `arr.forEach(n => console.log(n));`         | Common in array methods or event listeners.            |

👉 Agar function single line `return` hai, to `return` aur `{}` dono hata sakte ho:

### 2. Arrow Functions (`=>`)

- Arrow functions **do not have their own** `this`.

- Instead, they **inherit `this` from the parent call / Lexical scope** (the place where they are defined).

#### Example 2: Lexical `this` in practice

```js
const user = {
  name: "Ritesh",
  greet: function() {
    const inner = () => {
      console.log("Hello, " + this.name);
    };
    inner();
  }
};
user.greet(); // Hello, Ritesh
```

---

### 1. Default Parameters in JavaScript

- Default parameters allow user to **set a default value** for a function parameter.

- if no argument (or undefined) is passed.

```js
function multiply(a, b = 2) {  // b has default value
  return a * b;
}

console.log(multiply(5));    // Argument only for a → Output: 10
console.log(multiply(5, 3)); // Both arguments → Output: 15
```

```js
function greet(name = "Guest") {
  console.log("Hello " + name);
}

greet("Ritesh"); // Hello Ritesh
greet();         // Hello Guest  (default value used)
```

---


### 2. Rest Parameters:

- It collects multiple arguments into a single array.

- It's denoted by three dots (`...`)

```js
function showNames(...names) {
  console.log(names);
}

showNames("Ritesh", "Aman", "Pooja");
// Output: ["Ritesh", "Aman", "Pooja"]
```

```js
function sumAll(...numbers) {
  return numbers.reduce((total, n) => total + n, 0);
}

console.log(sumAll(1, 2, 3, 4, 5)); // 15
```

```js
function collectRest(a,b,...val){
    console.log(a,b,val);   // 1 2 [ 3, 4, 5, 6, 7, 8 ]
}

collectRest(1,2,3,4,5,6,7,8);
```

---

### Spread Operator (`...`)

📖 It expands arrays or objects into individual elements.

#### 1. Spread with Arrays

```js
//  Copying an array
let arr1 = [1, 2, 3];
let arr2 = [...arr1]; // shallow copy

console.log(arr2); // [1, 2, 3]
console.log(arr1 === arr2); // false (different references)
```

#### 2. Spread with Objects

```js
//  Copying an object
let user = { name: "Ritesh", city: "Delhi" };
let copyUser = { ...user };

console.log(copyUser); // { name: "Ritesh", city: "Delhi" }
```

```js
//  Adding new properties while copying
let user = { name: "Ritesh" };
let newUser = { ...user, age: 25, city: "Delhi" };

console.log(newUser);
// { name: "Ritesh", age: 25, city: "Delhi" }
```

```js
let arr1 = [1, 2];
let arr2 = [3, 4];
let combinedArr = [...arr1, ...arr2];  
// [1,2,3,4]

let user = { name: "Ritesh", city: "Delhi" };
let updatedUser = { ...user, city: "Mumbai", age: 25 };  
// { name:"Ritesh", city:"Mumbai", age:25 }

let str = "JS";
console.log([...str]); // ["J", "S"]
```

---

### 2. What are Modules?

- A **module** is a **separate JavaScript file** that **exports** and **Import** some code between **different files**.

- Helps in code **Organization**, **Reusability**, **Maintenance**, and clean structure.

- There are **two** primary ways to use **modules** in JavaScript.

#### 1. ES6 (ECMA Script 2015) Module

#### `import`, `export` keywords

#### (a) Named Export and Import

```js
//  math.js

export const add = (a,b) => a + b;
export const subtract = (a,b) => a - b;
```

```js
//  main.js

import { add, subtract } from './math.js'
console.log(add(2,3));  //  5
console.log(subtract(5,2)); //  3
```

#### (b) Default Export and Import

```js
//  math.js

const multiply = (a,b) => a * b;
export default multiply;
```

```js
//  main.js

import multiply from './math.js';
console.log(multiply(2,3)); //  6
```

### 2. CommonJS Modules (used in NodeJS)

```js
//  math.js

const age = 25;
const userName = "Ritesh Gupta";

module.export = {
    age,
    userName
}
```

```js
//  main.js

const math = require('./math.js');

console.log(math.age);
console.log(math.usernName);
```

---

```js
//  math.js

const add = (a,b) => {
    return a + b;
}

module.export = add;
```

```js
//  main.js

const add = require('./math.js');

console.log(add(2,5));  //  7
```

---

