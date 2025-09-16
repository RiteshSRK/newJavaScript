## Functions 

- [Function declarations, expressions, and arrow functions](#1-function-declarations-expressions-and-arrow-functions)
- [Parameters vs arguments](#2-parameters-vs-arguments)
- [Default, rest, and spread parameters](#3-default-rest-and-spread-parameters)
- [Return values and early returns](#4-return-values-and-early-returns)
- [First-class functions (assign to variables, pass as arguments, return from other functions)](#5-first-class-functions-assign-to-variables-pass-as-arguments-return-from-other-functions)
- [Higher-order functions](#6-higher-order-functions)
- [Pure vs impure functions](#7-pure-vs-impure-functions)
- [Closures and lexical scoping](#8-closures-and-lexical-scoping)
- [IIFE (Immediately Invoked Function Expressions)](#9-iife-immediately-invoked-function-expression)
- [Hoisting differences between declaration and expression](#10-what-is-hoisting)

### Common Confusion:
- Arrow vs regular function: `this` context
- Function hoisting and TDZ
- Scope chains and closure traps

### Practice:
- Write a BMI calculator
- Create a reusable discount calculator (HOF)
- Build a counter using closur
- Create a pure function to transform a value
- Use IIFE to isolate variables

---
## 1. Function declarations, expressions, and arrow functions
### 1. Function Declaration

- A function declared **using the function keyword** with **a name directly in the code**.

```js
function greet() {
  return "Hello!";
}
```

### 2. Function Expression

- **Store** a **function inside a variable** and **treat the function like a value**.

- Function expressions are not hoisted.

```js
sayHello(); // ❌ Error: Cannot access 'sayHello' before initialization

const sayHello = function() {
  console.log("Hello World!");
};
sayHello(); // ✅ Works
```

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

👉 Agar function single line `return` hai, to `return` aur `{}` dono hata sakte ho:

---

## 2. Parameters vs arguments
### Function Parameters:

- A **paramete**r is a *variables inside function definition*.

### Function Arguments:

- **Arguments** are actual values passed to function, when calling.

```js
// Parameter - variable in the function definition
function greet(name) { // 'name' is a parameter
    console.log(`Hello, ${name}!`);
}

// Argument - actual value passed to the function
greet('Alice'); // 'Alice' is an argument
```

## 3. Default, rest, and spread parameters
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

### 3. Spread Operator

- **Spread Operator** (`...`) expands arrays or objects into individual elements.

- It's denoted by three dots (`...`)

Examples:

1. In Function Calls:
```js
function add(a, b, c) {
  return a + b + c;
}

const nums = [1, 2, 3];
console.log(add(...nums)); // 6
```

2. In Array Literals:
```js
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combinedArray = [...arr1, ...arr2, 7, 8];
console.log(combinedArray); // Output: [1, 2, 3, 4, 5, 6, 7, 8]
```

3. In Object Literals:
```js
// In objects
const obj1 = { a: 1 };
const obj2 = { b: 2 };
console.log({ ...obj1, ...obj2 }); // { a: 1, b: 2 }
```

```js
const user = {
  name: 'John Doe',
  age: 30
};

const userWithEmail = {
  ...user,
  email: 'john.doe@example.com'
};

console.log(userWithEmail);
// Output: { name: 'John Doe', age: 30, email: 'john.doe@example.com' }
```

## 4. Return values and early returns
### 1. Return Values in Functions

- The `return` statement **send a value back** to where the function was called.

- `return` statement used to stop a function.

```js
// Its return value is their sum.
function add(a, b) {
  const sum = a + b;
  return sum; // Returns the calculated value
}

let result = add(5, 3); // The value 8 is returned and stored in 'result'
console.log(result); // Output: 8
```

```js
function add(a, b) {
  return a + b;   // returns the sum
}

let result = add(5, 3);
console.log(result); // 8
```

### 2. Early Returns

- An **early return** is when we use `return` to **exit a function before the end**, usually for better readability and avoiding unnecessary computation.

Example 1: Validation
```js
function divide(a, b) {
  if (b === 0) {
    return "Error: Division by zero";  // early return
  }
  return a / b;
}
console.log(divide(10, 0)); // Error: Division by zero
console.log(divide(10, 2)); // 5
```

Example 2: Guard Clauses
```js
function greet(name) {
  if (!name) return "Name is required";  // early return
  return `Hello, ${name}`;
}
console.log(greet());       // Name is required
console.log(greet("Ritesh")); // Hello, Ritesh
```

### 5. `First-class` functions (`assign to variables`, `pass as arguments`, `return from other functions`)

- functions **treated like values** called **First-Class Functions**.
    - Assign to variables
    - Pass as arguments
    - Return from other functions

### 1. Assign to Variables
- You can store functions inside variables (just like numbers, strings, or objects).
```js
const greet = function(name) {
  return `Hello, ${name}!`;
};

console.log(greet("Ritesh")); // Hello, Ritesh!
```

### 2. Pass as Arguments
- You can pass functions into other functions.

```js
function sayHello() {
  return "Hello!";
}

function execute(fn) {
  console.log(fn());   // call the function passed
}

execute(sayHello); // Hello!
```

```js
function abcd(val){
    val()
}

abcd(function(){
    console.log("hello world");
})
```

✅ Example in Array methods:

```js
const numbers = [1, 2, 3];
const doubled = numbers.map(n => n * 2);
console.log(doubled); // [2, 4, 6]
```

### 3. Return from Other Functions

A function can return another function.

```js
function multiplier(factor) {
  return function(num) {
    return num * factor;
  };
}

const double = multiplier(2);
console.log(double(5)); // 10
```

```js
function createMultiplier(factor) {
  // This function returns another function
  return function(number) {
    return number * factor;
  };
}

// 'double' is now a function that multiplies by 2
const double = createMultiplier(2);
console.log(double(10)); // Output: 20

// 'triple' is now a function that multiplies by 3
const triple = createMultiplier(3);
console.log(triple(10)); // Output: 30
```

## 6. Higher-order functions

- A H**igher-Order Function (HOF)** is that function **Takes another function as an argument** (**callback**) OR **Return a function as result**.

- Built-in Higher-Order Functions( `map()`, `filter()`, `reduce()`)

### 1. HOF Taking Function as Argument
✅ Example: Callback

```js
function greet(name) {
  return `Hello, ${name}`;
}

function processUserInput(callback) {
  let name = "Ritesh";
  console.log(callback(name));
}

processUserInput(greet); // Hello, Ritesh
```

### 2. HOF Returning Function
✅ Example: Closure

```js
function multiplier(factor) {
  return function(num) {
    return num * factor;
  };
}

const double = multiplier(2);
console.log(double(5)); // 10
```

## 7. Pure vs impure functions

### 1. Pure Functions

- Pure Functions **returns the same output for the same input**.

- **Has no side effects** (does not modify external state, variables, or data).

```js
function add(a, b) {
  return a + b;  // depends only on input, no external changes
}

console.log(add(2, 3)); // 5
console.log(add(2, 3)); // 5 (always same result)
```

### 2. Impure Functions

- **Produces different output for the same input** (depends on external factors).

- **Has side effects** (changes external variables, state, or data).

```js
let counter = 0;

function increaseCounter(value) {
  counter += value;   // modifies external variable (side effect)
  return counter;
}

console.log(increaseCounter(5)); // 5
console.log(increaseCounter(5)); // 10 (different result for same input)
```

```js
function getRandomNumber(num) {
  return num;  // different result each time
}

console.log(getRandomNumber(Math.floor(Math.random() * 6) + 1));
```

## 8. Closures and lexical scoping

- A **closure** is a function that has **access to the parent scope**, after the parent function has closed.

- **closures** -> ek function jo return kare ek aur function aur return hone waala function humesha use karega parent function ka koi variable.

```js
function outer() {
  let count = 0;

  return function inner() {
    count++;             // inner function remembers 'count'
    return count;
  };
}

const counter = outer();
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3
```

```js
function createGreeter(greeting) {
  const greetingText = `${greeting}, `;

  return function(name) {
    console.log(greetingText + name);
  };
}

const sayHello = createGreeter('Hello');
sayHello('Alice');    // Output: Hello, Alice

const sayNamaste = createGreeter('Namaste');
sayNamaste('Rahul');  // Output: Namaste, Rahul
```

```js
function createGreeter(greeting) {
  // 'greeting' is part of the lexical scope that the inner function will "remember"
  const greetingText = `${greeting}, `;

  // This inner function is returned, creating a closure
  return function(name) {
    // It has access to 'greetingText' even after 'createGreeter' has finished
    console.log(greetingText + name);
  };
}

// Call the outer function. It returns the inner function.
// 'sayHello' is now a closure. It "remembers" that greetingText is "Hello, ".
const sayHello = createGreeter('Hello');

// 'sayNamaste' is another closure. It "remembers" that greetingText is "Namaste, ".
const sayNamaste = createGreeter('Namaste');

// Now, we execute the inner functions, which are living outside their original scope.
sayHello('Alice');    // Output: Hello, Alice
sayNamaste('Rahul');  // Output: Namaste, Rahul
```

#### Real-World Examples of Closures

```js
function createBankAccount() {
  let balance = 1000; // private variable

  return {
    deposit: function(amount) {
      balance += amount;
      return balance;
    },
    withdraw: function(amount) {
      balance -= amount;
      return balance;
    },
    getBalance: function() {
      return balance;
    }
  };
}

const account = createBankAccount();
console.log(account.deposit(500)); // 1500
console.log(account.getBalance()); // 1500
```

## 9. IIFE (Immediately Invoked Function Expression)

- defined and executed immediately

- Use for the Avoid Global Scope Pollution.

```js
(function() {
  console.log("IIFE Running!");
})();
```

 Arrow Function IIFE
```js
(() => {
  console.log("Arrow IIFE Running!");
})();
```

With Parameters
```js
( (name) => {
    console.log(`DataBase Connected ${name}`);
}) ("Ritesh");
```

⚠️ Ek file me 2 IIFE function likhna to `;` mat bhulna nhi to error aata hai.


## 10. What is Hoisting?

- **Hoisting** means that during the memory creation phase, JavaScript moves **function declarations** and **variable declarations** to the top of their scope (before code execution).

#### 1. Function Declaration Hoisting

- Function declarations are fully hoisted

```js
sayHello();  // ✅ Works, function is hoisted

function sayHello() {
  console.log("Hello!");
}
```

#### 2. Function Expression Hoisting

- Function expressions are not fully hoisted.

```js
sayHi();  // ❌ TypeError: sayHi is not a function

var sayHi = function() {
  console.log("Hi!");
};
```