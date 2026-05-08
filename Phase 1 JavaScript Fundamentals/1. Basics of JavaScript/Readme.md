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

- `var`: Function scoped, can be **redeclared** and **reassigned**.

- `let`: Block scoped, can be **reassigned** but **not redeclared**.

- `const`: Block scoped, **cannot be reassigned** or **redeclared**.

### 1. `var`

- **Introduced:** Old JavaScript (before ES6).

- **Scope:** Function-scoped OR globally scoped if declared outside a function.

- **Hoisting:** Hoisted to the top with `undefined` value.

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

#### Q1. What’s the difference between `var`, `let`, and `const`?

> 👉 `var` is function-scoped, allows re-declaration, and is hoisted with `undefined`.

> 👉 `let` and `const` are block-scoped, do not allow re-declaration, and are hoisted but remain in the Temporal Dead Zone until initialized.

> 👉 `let` allows reassignment, `const` doesn’t.

#### Q2. What is the Temporal Dead Zone (TDZ)?

---

> 👉 The period between hoisting and initialization when a variable exists but cannot be accessed.

```js
console.log(x); // ❌ ReferenceError
let x = 10; // TDZ until this line executes
```
---

#### Q3. Can we change properties of a const object?
>👉 Yes. const only prevents re-assignment of the variable reference, not mutation of the object/array.

### ⚡ Tip for Interviews:

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

### 🎯 Interview-style Q&A

#### Q1. What is the difference between null and undefined?
> 👉 **undefined** = variable declared but not assigned.    
> 👉 **null** = explicitly assigned empty value.

```js
let a;     // undefined
let b = null; // null
```

#### Q5. How many primitive data types does JavaScript have?
> 👉 7 primitive types: number, string, boolean, null, undefined, symbol, bigint.

### ⚡ Tip for Interviews:

- Always remember: **Primitives are immutable & stored by value**.

- Objects/arrays/functions are **non-primitive & stored by reference**.

---

## JavaScript Operators (Important for Interviews)

> Operators are symbols that perform operations on values/variables.

### 1. Arithmetic Operators

> Used for basic math.

| Operator | Meaning                | Example  | Output |
| -------- | ---------------------- | -------- | ------ |
| `+`      | Addition               | `5 + 3`  | `8`    |
| `-`      | Subtraction            | `5 - 3`  | `2`    |
| `*`      | Multiplication         | `5 * 3`  | `15`   |
| `/`      | Division               | `10 / 2` | `5`    |
| `%`      | Modulus (remainder)    | `10 % 3` | `1`    |
| `**`     | Exponentiation (power) | `2 ** 3` | `8`    |
| `++`     | Increment              |          |        |
| `--`     | Decrement              |          |        |

👉 Example:

```js
console.log(10 + 5);   // 15
console.log(10 - 5);   // 5
console.log(10 * 5);   // 50
console.log(10 / 2);   // 5
console.log(10 % 3);   // 1
console.log(2 ** 4);   // 16
```

### 2. Assignment Operators

> Assign values to variables.

```js
= // assigns value
+= // a += b => a = a + b
-= // a -= b
*=, /=, %=
```

👉 Example:

```js
let score = 5;
score += 2; // score = 7
```

### 3. Comparison Operators

> Used to compare two values.

| Operator | Meaning                     | Example     | Output  |
| -------- | --------------------------- | ----------- | ------- |
| `===`    | Strict equal (value + type) | `5 === "5"` | `false` |
| `!==`    | Strict not equal            | `5 !== "5"` | `true`  |
| `==`     | Loose equal (only value)    | `5 == "5"`  | `true`  |
| `!=`     | Loose not equal             | `5 != "5"`  | `false` |
| `>`      | Greater Than                |             |         |
| `<`      | Less Than                   |             |         |
| `>=`     | Greater or Equal            |             |         |
| `<=`     | Less or Equal               |             |         |

👉 Example:

```js
console.log(5 == "5");   // true (only value)
console.log(5 === "5");  // false (type check also)
console.log(5 !== "5");  // true
```

---

### 4. Logical Operators

>Used for boolean logic.

| Operator | Meaning                | Example           | Output                 |
| -------- | ---------------------- | ----------------- | ---------------------- |
| `&&`     | AND (all must be true) | `true && false`   | `false`                |
| `\|\|`   | OR (at least one true) | `true \|\| false` | `true`                 |
| `!`      | NOT (reverse)          | `!true`           | `false`                |

⚠️  OR( `||` ) ke sthan pr slash likha hai, kyuki markdown me ye table ke liye use hota hai.

👉 Example:

```js
console.log(true && true);   // true
console.log(true && false);  // false
console.log(true || false);  // true
console.log(!false);         // true
```


## 5. Ternary( conditional ) Operator (condition ? value1 : value2)

- Short form of `if...else`.

- Returns **one of two values** based on a **condition**.

👉 Example:

```js
let age = 18;
let canVote = (age >= 18) ? "Yes" : "No";
console.log(canVote); // "Yes"
```

## 🎯 Interview-style Q&A

### Q2. What is the ternary operator in JavaScript?
> 👉 A shorthand if...else that evaluates a condition and returns one of two values.

### Q3. Can we use multiple (nested) ternary operators?
> 👉 Yes, but avoid too many levels because it reduces readability. Use if...else for complex conditions.


## 6. Unary Operators
> Used on a single operand.

```js
+ // tries to convert to number
- // negates
++ // increment
-- // decrement
typeof // returns data type
```

```js
let x = "5";
console.log(+x); // 5 (converted to number)
```

---

### 7. Nullish Coalescing (`??`)

- Returns **right-hand value only if left-hand** is `null` or `undefined`.

- Unlike `||`, it doesn’t treat `0` or `""` as false.

👉 Example:

```js
let a = null;
let b = a ?? "Default";
console.log(b); // "Default"

let c = 0;
console.log(c || 100); // 100 (because 0 is falsy)
console.log(c ?? 100); // 0 (because 0 is not null/undefined)
```

### 8. Optional Chaining (`?.`)

- Safely access **deep properties** without error.

- Returns `undefined` if property doesn’t exist instead of throwing error.

👉 Example:

```js
let user = { name: "Ritesh", address: { city: "Delhi" } };

console.log(user.address?.city); // "Delhi"
console.log(user.contact?.phone); // undefined (no error)
```

---

### 🔥 Summary Table

| Operator | Category           | Example               | Output                 |
| -------- | ------------------ | --------------------- | ---------------------- |
| `+`      | Arithmetic         | `5 + 2`               | `7`                    |
| `-`      | Arithmetic         | `5 - 2`               | `3`                    |
| `*`      | Arithmetic         | `5 * 2`               | `10`                   |
| `/`      | Arithmetic         | `5 / 2`               | `2.5`                  |
| `%`      | Arithmetic         | `5 % 2`               | `1`                    |
| `**`     | Arithmetic         | `2 ** 3`              | `8`                    |
| `===`    | Comparison         | `5 === "5"`           | `false`                |
| `!==`    | Comparison         | `5 !== "5"`           | `true`                 |
| `&&`     | Logical AND        | `true && false`       | `false`                |
| `\|\|`   | Logical OR         | `true \|\| false`     | `true`                 |
| `??`     | Nullish Coalescing | `null ?? "Hi"`        | `"Hi"`                 |
| `?.`     | Optional Chaining  | `user?.address?.city` | `undefined` if missing |

---

## 🎯 Interview-style Q&A

### Q1. Difference between == and ===?
> 👉 **==** does type coercion (only checks value).   
> 👉 **===** checks both value and type.

```js
5 == "5"   // true
5 === "5"  // false
```

### Q2. Difference between `||` and `??`?
> 👉 `||` treats all falsy values (`0, "", false, null, undefined`) as false.   
> 👉 `??` only checks **null** and **undefined**.

### Q3. Why use optional chaining (?.)?
> 👉 To **avoid runtime errors** when **accessing deeply nested properties**.

### ⚡ Quick Tip for Interviews:

- Prefer `===` and `!==` instead of `==` and `!=`.

- Use `??` when you want default values but still allow `0` or `""`.

- Use `?.` for safe property access in APIs and objects.

---

## Assignment Operators in JavaScript

> Assignment operators are used to assign values to variables.  
>Besides =, we have shorthand operators.

| Operator | Meaning           | Example   | Equivalent To | Result     |
| -------- | ----------------- | --------- | ------------- | ---------- |
| `=`      | Assign            | `x = 10`  | –             | `x = 10`   |
| `+=`     | Add & assign      | `x += 5`  | `x = x + 5`   | `x = 15`   |
| `-=`     | Subtract & assign | `x -= 3`  | `x = x - 3`   | `x = 7`    |
| `*=`     | Multiply & assign | `x *= 2`  | `x = x * 2`   | `x = 20`   |
| `/=`     | Divide & assign   | `x /= 2`  | `x = x / 2`   | `x = 5`    |
| `%=`     | Modulus & assign  | `x %= 3`  | `x = x % 3`   | `x = 1`    |
| `**=`    | Power & assign    | `x **= 3` | `x = x ** 3`  | `x = 1000` |

👉 Example:

```js
let x = 10;

x += 5;   // 15
x -= 3;   // 12
x *= 2;   // 24
x /= 4;   // 6
x %= 4;   // 2
x **= 3;  // 8

console.log(x); // 8
```

---


## Type Conversion in JavaScript

> JavaScript is a **dynamically typed language**, so variables can change type at runtime. There are **two types of conversion**:

- **Implicit (Type Coercion)** → JS automatically converts types.

- **Explicit (Type Casting)** → Developer manually converts.

### 1. Implicit Conversion (Type Coercion)

JavaScript automatically converts one type to another when needed.

👉 Examples:

```js
// String + Number → String
console.log("5" + 2);  // "52"

// Number + Boolean
console.log(5 + true); // 6 (true → 1)

// Subtraction / Multiplication → Number
console.log("10" - 2); // 8
console.log("5" * "2"); // 10

// Boolean to Number
console.log(true + 1);  // 2
console.log(false + 10); // 10
```

#### String Concatenation:
```js
let result = '3' + 2;    // '32' (number converted to string)
let result2 = '3' + true; // '3true' (boolean converted to string)
```

#### Numeric Operations:
```js
let result = '4' - '2';   // 2 (strings converted to numbers)
let result2 = '4' * 2;    // 8 (string converted to number)
let result3 = '4' / '2';  // 2 (strings converted to numbers)
```

#### Boolean Context:
```js
if ('hello') { /* executes because non-empty string is truthy */ }
if (0) { /* doesn't execute because 0 is falsy */ }
```

#### Loose Equality (==):
```js
'1' == 1;    // true (string converted to number)
0 == false;  // true (boolean converted to number)
null == undefined; // true (special case)
```

⚠️ Problem: Can create unexpected results.

## 2. Explicit Conversion (Type Casting)

We manually convert types using built-in methods.

### (a) To Number

- `Number()`

- `parseInt()`, `parseFloat()`

- Unary `+`

👉 Example:

```js
console.log(Number("123"));   // 123
console.log(Number("123abc")); // NaN
console.log(parseInt("123abc")); // 123
console.log(parseFloat("3.14")); // 3.14
console.log(+ "42"); // 42
```

### (b) To String

- `String()`

- `toString()`

👉 Example:

```js
console.log(String(123));  // "123"
console.log((123).toString()); // "123"
```

### (c) To Boolean

- `Boolean()`

👉 Example:

```js
console.log(Boolean(1));  // true
console.log(Boolean(0));  // false
console.log(Boolean("")); // false
console.log(Boolean("hi")); // true
```

👉 Falsy Values in JS (convert to false):   
`0, "" (empty string), null, undefined, NaN, false`

Everything else → `true`.


---

### String Conversion:

```js
String(123);        // '123'
(123).toString();   // '123'
true.toString();    // 'true'
```

### Numeric Conversion:

```js
Number('123');      // 123
Number('123abc');   // NaN (Not a Number)
+'123';             // 123 (unary plus operator)
parseInt('123px');  // 123
parseFloat('12.3'); // 12.3
```

### Boolean Conversion:

```js
Boolean(1);         // true
Boolean(0);         // false
Boolean('hello');    // true
Boolean('');         // false
!!'hello';          // true (double NOT operator)
```

### Special Cases to Watch For:

```js
null + undefined;   // NaN
null + 5;           // 5 (null becomes 0)
undefined + 5;      // NaN
'5' - 3;            // 2
'5' + 3;            // '53' (not 8!)
true + true;        // 2
false + 10;         // 10
```
### 🔥 Key Differences Table

| Conversion  | Implicit (Coercion)      | Explicit (Casting)         |
| ----------- | ------------------------ | -------------------------- |
| Control     | Done automatically by JS | Done manually by developer |
| Readability | Sometimes confusing      | Clear and predictable      |
| Example     | `"5" + 2 → "52"`         | `Number("5") + 2 → 7`      |

## 🎯 Interview-style Q&A

#### Q1. Difference between Implicit & Explicit Conversion?
> 👉 Implicit is automatic conversion by JS (type coercion).  
> 👉 Explicit is manual using functions like `Number()`, `String()`, `Boolean()`.

#### Q2. What are falsy values in JavaScript?
> 👉 `0, "" (empty string), null, undefined, NaN, false`.

#### Q4. Difference between `parseInt("123abc")` and `Number("123abc")`?
> 👉 parseInt extracts valid numeric part (`123`).    
> 👉 `Number` returns `NaN` because full string isn’t a valid number.

---

## Comments in JavaScript

> Comments are **ignored by JavaScript engine** → used only for humans (`documentation`, `explanation`, `debugging`).

### 1. Single-line Comment (`//`)

- Starts with `//`

- Everything after `//` on the same line is ignored.

👉 Example:

```js
// This is a single-line comment
let x = 10; // Assigning value 10
```

### 2. Multi-line Comment (`/* ... */`)

- Starts with `/*` and ends with `*/`

- Used for multiple lines or large descriptions.

👉 Example:

```js
/*
 This is a multi-line comment
 It can span multiple lines
 Used for detailed explanations
*/
let y = 20;
```

### ⚡ Quick Tip for Interviews:

- `//` → small notes / debugging.

- `/* */` → documentation / large explanation.