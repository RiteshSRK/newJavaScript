- **Case-sensitive:** JavaScript is case-sensitive, so `myVariable` is different from `myvariable`.

- **Semicolons:** Semicolons are optional in JavaScript, but it is a good practice to use them.

- **Data types:** JavaScript has 7 primitive data types: `number` , `string` , `boolean` , `null` , `undefined` , `bigint` , and `symbol` .

- **Variables:** Variables are used to store data. To declare a variable, use the keywords `var` , `let` , or `const`.

- **Arithmetic operators:** JavaScript has the following arithmetic operators: `+` , `-` , `*` , `/` , `%`, and `**`.

- **Logical operators:** JavaScript has the following logical operators: `&&` , `||` , and `!`.

- **Conditional statements:** JavaScript has the following conditional statements: `if` , `else` , `else if` , and `switch` .

- **Loops:** JavaScript has the following loops: `for` , `while` , and `do...while`.

- **Functions:** Functions are used to group code together and reuse it.

---

## Variables in JavaScript (`var`, `let`, `const`)

- `var`: Function scoped, can be **redeclared** and **updated**.

- `let`: Block scoped, can be **updated** but **not redeclared**.

- `const`: Block scoped, **cannot be updated** or **redeclared**.

### 1. `var`

- **Introduced:** Old JavaScript (before ES6).

- **Scope:** Function-scoped OR globally scoped if declared outside a function.

- **Hoisting:** Hoisted to the top but initialized with `undefined`.

- **Re-declaration:** Allowed.

- **Re-assignment:** Allowed.

- **Problem:** Causes issues because it ignores block scope.

👉 Example:

```js
function testVar() {
  if (true) {
    var x = 10;
  }
  console.log(x); // ✅ Works (10), because var is function-scoped
}
testVar();

console.log(x);     //  ReferenceError: x is not defined

var a = 5;
var a = 20; // ✅ No error (re-declaration allowed)
```

### 2. `let`

- Introduced in ES6 (2015).

- **Scope:** Block-scoped `{}`.

- **Hoisting:** Yes, but in the ***Temporal Dead Zone*** (cannot use before declaration).

- **Re-declaration:** ❌ Not allowed in the same scope.

- **Re-assignment:** ✅ Allowed.

👉 Example:

```js
function testLet() {
  if (true) {
    let y = 20;
    console.log(y); // ✅ Works (20)
  }
  // console.log(y); ❌ Error (block-scoped)
}

let b = 10;
// let b = 30; ❌ Error (re-declaration not allowed in same scope)
b = 40; // ✅ Works (re-assignment)
```

### 3. `const`

- Introduced in ES6.

- **Scope:** Block-scoped `{}`.

- **Hoisting:** Yes, but in the Temporal Dead Zone.

- **Re-declaration:** ❌ Not allowed.

- **Re-assignment:** ❌ Not allowed.

- **Const with objects/arrays:** The reference is constant, but properties/elements can be changed.

👉 Example:

```js
const c = 50;
// c = 100; ❌ Error (cannot re-assign)

const obj = { name: "Ritesh" };
obj.name = "Kumar"; // ✅ Allowed (modifying property)
console.log(obj); // { name: "Kumar" }

const arr = [1, 2, 3];
arr.push(4); // ✅ Allowed
console.log(arr); // [1, 2, 3, 4]
```

### 🔥 Key Differences Table

| Feature        | `var`             | `let`                | `const`               |
| -------------- | ----------------- | -------------------- | --------------------- |
| Scope          | Function / Global | Block                | Block                 |
| Hoisting       | ✅ Yes (undefined) | ✅ Yes (TDZ)          | ✅ Yes (TDZ)           |
| Re-declaration | ✅ Yes             | ❌ No                 | ❌ No                  |
| Re-assignment  | ✅ Yes             | ✅ Yes                | ❌ No                  |
| Best to Use    | ❌ Avoid           | ✅ When value changes | ✅ When value is fixed |

## 🎯 Interview-style Q&A

### Q1. What’s the difference between `var`, `let`, and `const`?

> 👉 `var` is function-scoped, allows re-declaration, and is hoisted with `undefined`.

> 👉 `let` and `const` are block-scoped, do not allow re-declaration, and are hoisted but remain in the Temporal Dead Zone until initialized.

> 👉 `let` allows reassignment, `const` doesn’t.

### Q2. What is the Temporal Dead Zone (TDZ)?

---

> 👉 The period between hoisting and initialization when a variable exists but cannot be accessed.

```js
console.log(x); // ❌ ReferenceError
let x = 10; // TDZ until this line executes
```
---

### Q3. Can we change properties of a const object?
>👉 Yes. const only prevents re-assignment of the variable reference, not mutation of the object/array.

## ⚡ Tip for Interviews:

- Prefer `const` by default.

- Use `let` only when reassignment is needed.

- Avoid `var` completely.

---

## JavaScript Data Types

> JavaScript has ***two categories of data types***:

1. **Primitive Types** (immutable, stored directly in memory)

2. **Non-Primitive / Reference Types** (objects, arrays, functions)

Here we’ll cover **all primitive types**:   
👉 `number`, `string`, `boolean`, `null`, `undefined`, `symbol`, `bigint`

---

### 1. Number

- Represents `integers` and `floating-point` numbers.

- Special values: `Infinity`, `-Infinity`, `NaN` (Not a Number).

- Internally stored as **64-bit floating point**.

👉 Example:

```js
let num1 = 42;        // integer
let num2 = 3.14;      // float
console.log(1 / 0);   // Infinity
console.log("a" * 2); // NaN
```

### 2. String

- Sequence of characters enclosed in `''`, `""`, or backticks `${``}`.

- Strings are immutable.

- Template literals (`Hello ${name}`) allow interpolation.

👉 Example:

```js
let name = "Ritesh";
let greet = `Hello, ${name}!`; // template literal
console.log(greet); // Hello, Ritesh!
```

### 3. Boolean

- Represents only `true` or `false`.

- Commonly used in conditions and logical operations.

👉 Example:

```js
let isLoggedIn = true;
let isAdmin = false;
console.log(5 > 3); // true
```

### 4. Null

- Represents an **intentional absence of value**.

- Type is **object** (historical JS bug).

👉 Example:

```js
let user = null; // explicitly no value
console.log(user); // null
```

### 5. Undefined

- A variable that is **declared but not initialized**.

- Default value assigned by JS.

👉 Example:

```js
let x;
console.log(x); // undefined
```

### 6. Symbol (ES6)

- Represents a **unique identifier**.

- Useful as **object keys** to avoid conflicts.

- Always unique, even if description is same.

👉 Example:

```js
let id1 = Symbol("id");
let id2 = Symbol("id");
console.log(id1 === id2); // false
```

### 7. BigInt (ES11 / ES2020)

- Used for numbers larger than 2^53 - 1 (Number limit).

- Declared by appending n at the end.

👉 Example:

```js
let big = 1234567890123456789012345678901234567890n;
let small = 20n;
console.log(big + small); // works with other BigInts
```

### 🔥 Key Differences Table

| Data Type | Example                          | Description               |
| --------- | -------------------------------- | ------------------------- |
| Number    | `42`, `3.14`, `NaN`, `Infinity`  | All numbers (int + float) |
| String    | `"hello"`, `'world'`, `` `Hi` `` | Text data                 |
| Boolean   | `true`, `false`                  | Logical values            |
| Null      | `null`                           | Intentional empty value   |
| Undefined | `undefined`                      | Declared but not assigned |
| Symbol    | `Symbol("id")`                   | Unique identifiers        |
| BigInt    | `9007199254740991n`              | Very large integers       |

## 🎯 Interview-style Q&A

### Q1. What is the difference between null and undefined?
> 👉 **undefined** = variable declared but not assigned.    
> 👉 **null** = explicitly assigned empty value.

```js
let a;     // undefined
let b = null; // null
```

### Q5. How many primitive data types does JavaScript have?
> 👉 7 primitive types: number, string, boolean, null, undefined, symbol, bigint.

## ⚡ Tip for Interviews:

- Always remember: **Primitives are immutable & stored by value**.

- Objects/arrays/functions are **non-primitive & stored by reference**.

---

