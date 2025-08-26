### Q1. What is `JavaScript`? What is the `role` of JavaScript engine?
> JavaScript is a programming language that is used for converting static web pages to interactive and dynamic web pages.

> A JavaScript engine is a program present in web browsers that executes JavaScript code. Like V8 engine in chrome.

### Q2. What are `client side` and `server side`?
> A client is a device, application, or software component that requests and consumes services or resources from a server.

> A server is a device, computer, or software application that provides services, resources, or functions to clients.

### Q3. What are `variables`? What is the difference between `var`, `let`, and `const`?

> Variables are used to store data. 	var count = 10;

- `var`: Function scoped, can be redeclared and updated.
- `let`: Block scoped, can be updated but not redeclared.
- `const`: Block scoped, cannot be updated or redeclared.

### Q5. What is `DOM`? What is the difference between `HTML` and `DOM`?
> HTML (Hypertext Markup Language) is the standard markup language used to create web pages. It's a static representation of the document's structure and content, written in a series of tags and attributes.

> The DOM(Document Object Model) represents the web page as a tree-like structure that allows JavaScript to dynamically access and manipulate the content and structure of a web page.

### Q6. What are selectors in JS?
> Selectors in JS help to get specific elements from DOM based on IDs, class names, tag names.

- DOM Selector methods:-  
  - `getElementByld()`
  - `getElementsByClassName()`
  - `getElementsByTagName()`
  - `querySelector()`
  - `querySelectorAll()`

### Q8. What are data types in JS?
> A data type determines the type of variable. Its two types.

### Q. What is the difference between `primitive` and `non-primitive` data types?

| **Primitive Data Types** | **Non-primitive Data Types** |
| ------------------------- | ----------------------------- |
| 1. Number, String, Boolean, Undefined, Null are primitive data types. | Object, Array, Function, Date, RegExp are non-primitive data types. |
| 2. Primitive data types can hold only a single value. | Non-primitive data types can hold multiple values and methods. |
| 3. Primitive data types are immutable and their values cannot be changed. | Non-primitive data types are mutable and their values can be changed. |
| 4. Primitive data types are simple data types. | Non-primitive data types are complex data types. |


### Q9. What are `operators`? What are the types of operators in JS?
> Operators are symbols or keywords used to perform operations on operands ( Value ).

### 1.	Arithmetic Operators:

| **Operator** | **Meaning**        | **Example**   | **Output** |
|-------------|--------------------|--------------|-----------|
| `+`        | Addition           | `5 + 3`     | `8`       |
| `-`        | Subtraction        | `5 - 3`     | `2`       |
| `*`        | Multiplication     | `5 * 3`     | `15`      |
| `/`        | Division           | `6 / 3`     | `2`       |
| `%`        | Modulus (Remainder)| `5 % 2`     | `1`       |
| `**`       | Exponentiation     | `2 ** 3`    | `8`       |

### 2.	Assignment Operators:

| **Operator** | **Meaning**                | **Example**      | **Equivalent To** |
|-------------|---------------------------|-----------------|--------------------|
| `=`        | Simple Assignment         | `x = 5`        | `x = 5`           |
| `+=`       | Addition Assignment       | `x += 3`       | `x = x + 3`       |
| `-=`       | Subtraction Assignment    | `x -= 3`       | `x = x - 3`       |
| `*=`       | Multiplication Assignment | `x *= 3`       | `x = x * 3`       |
| `/=`       | Division Assignment       | `x /= 3`       | `x = x / 3`       |
| `%=`       | Modulus Assignment        | `x %= 3`       | `x = x % 3`       |
| `**=`      | Exponentiation Assignment | `x **= 3`      | `x = x ** 3`      |

### 3.	Comparison Operators:

| **Operator** | **Meaning**                     | **Example**     | **Output** |
|-------------|---------------------------------|---------------|-----------|
| `==`        | Loose Equality (compares values, ignores type) | `5 == '5'`     | `true`    |
| `===`       | Strict Equality (compares value & type)       | `5 === '5'`    | `false`   |
| `!=`        | Loose Inequality (compares values, ignores type) | `5 != '5'`  | `false`   |
| `!==`       | Strict Inequality (compares value & type)     | `5 !== '5'`    | `true`    |
| `>`         | Greater Than                                  | `7 > 5`        | `true`    |
| `<`         | Less Than                                     | `3 < 5`        | `true`    |
| `>=`        | Greater Than or Equal To                     | `5 >= 5`       | `true`    |
| `<=`        | Less Than or Equal To                        | `3 <= 5`       | `true`    |

### 4.	Logical Operators:

| **Operator**| **Meaning**        | **Example**               | **Output**|
|-------------|--------------------|---------------------------|-----------|
| `&&`        | Logical AND        | `(true && false)`         | `false`   |
| `\|\|`      | Logical OR         | `(true \|\| false)`       | `true`    |
| `!`         | Logical NOT        | `!(true)`                 | `false`   |

### Conditional (Ternary) Operator:

```js
//  It is a short form of if...else.

let age = 18;
let beverage = age >= 21 ? "Beer" : "Juice";
console.log(beverage); // Output: "Juice"
```

---

### What are the types of `conditions statements` in JS?

### 1. `if...else` Statement
> The `if...else` statement allows you to check multiple conditions in sequence.

```js
let grade = 85;

if (grade >= 90) {
    console.log("A");
} else if (grade >= 80) {
    console.log("B");       //  Output: B
} else if (grade >= 70) {
    console.log("C");
} else {
    console.log("D");
}
```

### `switch` statement
> The switch statement evaluates an expression and executes code blocks based on matching case values. It’s useful for handling multiple conditions that depend on the same expression.

```js
let day = 3;

switch (day) {
    case 1:
        console.log("Monday");
        break;
    case 2:
        console.log("Tuesday");
        break;
    case 3:
        console.log("Wednesday");   //  Output: Wednesday
        break;
    default:
        console.log("Invalid day");
}
```

### Conditional (Ternary) Operator
> The conditional (ternary) operator is a shorthand for `if...else` statements, allowing you to choose between two values based on a condition.

```js
let age = 18;
let beverage = age >= 21 ? "Beer" : "Juice";
console.log(beverage); // Output: "Juice
```

---

### Q11.	What is a `loop`? What are the `types of loops` in JS?

> A loop is a programming way to run a piece of code repeatedly until a certain condition is met.

### 1. for Loop

> Used when we know how many times we want to run the loop.

```js
for (initialization; condition; update) {
   // code block
}
```

```js
for (let i = 1; i <= 5; i++) {
  console.log("Number:", i);
}
// Output: 1 2 3 4 5
```

### 2. while Loop

- Runs as long as condition is `true`.

- Used when number of iterations is not fixed.

```js
let i = 1;
while (i <= 5) {
  console.log("Count:", i);
  i++;
}
```

### 3. do...while Loop

>Similar to while, but it runs at least once even if condition is false.

```js
let i = 6;
do {
  console.log("Value:", i);
  i++;
} while (i <= 5);

// Output: Value: 6 (runs once)
```

### 4. for...of Loop

- Iterates over values of an iterable (Array, String, Map, Set).

- Best for arrays and strings.

```js
let arr = [10, 20, 30];
for (let value of arr) {
  console.log(value);
}
// Output: 10 20 30
```

```js
for (let ch of "JS") {
  console.log(ch);
}
// Output: J S
```

### 5. for...in Loop

- Iterates over keys (property names) of an object.

- Best for objects.

```js
let user = { name: "Ritesh", age: 22, city: "Delhi" };

for (let key in user) {
  console.log(key, ":", user[key]);
}
// Output: name : Ritesh, age : 22, city : Delhi
```

---

### Q12.	What are `Functions` in JS? What are the `types of function`?

> A function is a reusable block of code that performs a specific task.

### Q13.	What are Arrow Functions in JS? What is it use?

> Arrow functions, also known as fat arrow functions, is a simpler and shorter way for defining functions in JavaScript.

```js
const add = (a, b) => a + b;
console.log(add(2, 3)); // Output: 5
```

### Key Features
1.	**Concise Syntax:** Shorter and cleaner than regular functions.

2.	**Implicit Return:** Single expression returns value automatically.

3.	**Lexical this:** Inherits this from the surrounding context, useful in callbacks.

4.	**No arguments Object:** Cannot access arguments directly.

### Use Cases
- **Callbacks:** Simplifies code for functions like `map`, `filter`, etc.
- **Event Handlers:** Maintains the correct this context.
- **Functional Programming:** Enhances readability and expressiveness.

---

### What are Arrays in JavaScript?

- **Definition:** An Array in JavaScript is a **special type of object** that is used to store multiple values in a single variable.

- Arrays are ordered collections of elements (indexed from 0).

```js
let fruits = ["Apple", "Mango", "Banana"];
```

#### How to Get Elements from an Array?

- Using index:

```js
let fruits = ["Apple", "Mango", "Banana"];
console.log(fruits[0]); // Output: Apple
console.log(fruits[2]); // Output: Banana
```

- Get array length:

```js
console.log(fruits.length); // Output: 3
```

### How to Add Elements to an Array?

| Method      | Description                          | Example                        |
| ----------- | ------------------------------------ | ------------------------------ |
| `push()`    | Add element at the **end**           | `fruits.push("Orange");`       |
| `unshift()` | Add element at the **beginning**     | `fruits.unshift("Grapes");`    |
| `splice()`  | Insert element at **specific index** | `fruits.splice(1, 0, "Kiwi");` |

```js
let fruits = ["Apple", "Mango"];
fruits.push("Banana");   // ["Apple", "Mango", "Banana"]
fruits.unshift("Orange"); // ["Orange", "Apple", "Mango", "Banana"]
fruits.splice(2, 0, "Kiwi"); // ["Orange", "Apple", "Kiwi", "Mango", "Banana"]
```

### How to Remove Elements from an Array?

| Method     | Description                          | Example                |
| ---------- | ------------------------------------ | ---------------------- |
| `pop()`    | Remove element from the **end**      | `fruits.pop();`        |
| `shift()`  | Remove element from the **start**    | `fruits.shift();`      |
| `splice()` | Remove element at **specific index** | `fruits.splice(1, 1);` |

```js
let fruits = ["Orange", "Apple", "Kiwi", "Mango", "Banana"];
fruits.pop();      // ["Orange", "Apple", "Kiwi", "Mango"]
fruits.shift();    // ["Apple", "Kiwi", "Mango"]
fruits.splice(1,1);// ["Apple", "Mango"]
```

---

### Q15.	What are `Objects` in JS?

> Object in JavaScript is a collection of key-value pairs.

### Q16.	What is Scope in JavaScript?
> Scope determines where variables are defined and where they can be accessed.
- Global Scope
- Functional Scope
- Block Scope

