## Numbers in JavaScript

> ✅ In JavaScript, all numbers are stored as floating-point (64-bit IEEE 754 format).

- Means `5`, `5.5`, `-3`, `1000000000000` sab ek hi type ke hote hain → `number`

- Special values:

  - `Infinity` → result of dividing by 0 (`1 / 0`)

  - `Infinity` → result of negative division (`-1 / 0`)

  - `NaN (Not a Number)` → invalid mathematical operation (`"abc" * 2`)

👉 Example:
```js
    console.log(10 / 0);     // Infinity
    console.log(-10 / 0);    // -Infinity
    console.log("abc" * 2);  // NaN
```
---

### Creating Numbers:

```js
// Different ways to create numbers
let num1 = 42;         // Number literal
let num2 = Number(42); // Number constructor
let num3 = new Number(42); // Number object (avoid - creates object wrapper)
let floatNum = 3.14159;
let scientific = 5e3;  // 5000
```

## Number Methods
### 1. `toString()` → Convert number to string

```js
let num = 123;
console.log(num.toString());    // "123"
console.log((100 + 23).toString()); // "123"
```

### 2. `toFixed(n)` → Round number to n decimal places (string output)

```js
let num = 12.3456;
console.log(num.toFixed(2)); // "12.35"
console.log(num.toFixed(0)); // "12"
```

```js
let num = 1234;

console.log(num.toFixed(2));    //  1234.00
console.log(num.toFixed(3));    //  1234.000
```

### 3. `toPrecision(n)` → Return number with total digits = `n`

```js
let num = 12.3456;
console.log(num.toPrecision(4)); // "12.35"
console.log(num.toPrecision(2)); // "12"
```

### 4. `Number()` → Convert value to number

```js
console.log(Number("123"));    // 123
console.log(Number("12.34"));  // 12.34
console.log(Number("abc"));    // NaN
```

### 5. `parseInt()` → Convert string to integer

```js
console.log(parseInt("123.45")); // 123
console.log(parseInt("100px"));  // 100
console.log(parseInt("abc"));    // NaN
```

### 6. `parseFloat()` → Convert string to floating-point number

```js
console.log(parseFloat("123.45")); // 123.45
console.log(parseFloat("100.50px")); // 100.5
```

### 7. `isNaN()` → Check if value is NaN

```js
console.log(isNaN("abc"));  // true
console.log(isNaN(123));    // false
```

### 8. `isFinite()` → Check if value is finite number

```js
console.log(isFinite(100));   // true
console.log(isFinite(Infinity)); // false
console.log(isFinite("abc")); // false
```

### 9. `Number.isInteger()` → Check if value is integer

```js
console.log(Number.isInteger(10));    // true
console.log(Number.isInteger(10.5));  // false
```

### 10. `Number.isNaN()` → Strict check for NaN

```js
console.log(Number.isNaN(NaN));   // true
console.log(Number.isNaN("abc")); // false (string is not NaN directly)
```
---

## Quick Table of Number Methods

| Method                  | Description            | Example                   | Output    |
| ----------------------- | ---------------------- | ------------------------- | --------- |
| `toString()`            | Number → String        | `(123).toString()`        | `"123"`   |
| `toFixed(n)`            | Rounds to `n` decimals | `(12.345).toFixed(2)`     | `"12.35"` |
| `toPrecision(n)`        | Total length = `n`     | `(12.345).toPrecision(3)` | `"12.3"`  |
| `Number(val)`           | Convert to number      | `Number("12.5")`          | `12.5`    |
| `parseInt(val)`         | String → Integer       | `parseInt("12.7px")`      | `12`      |
| `parseFloat(val)`       | String → Float         | `parseFloat("12.7px")`    | `12.7`    |
| `isNaN(val)`            | Check NaN (loose)      | `isNaN("abc")`            | `true`    |
| `Number.isNaN(val)`     | Strict NaN check       | `Number.isNaN(NaN)`       | `true`    |
| `isFinite(val)`         | Check finite number    | `isFinite(10)`            | `true`    |
| `Number.isInteger(val)` | Check integer          | `Number.isInteger(5.5)`   | `false`   |


#### Q2. Difference between `parseInt()` and `Number()`?
👉 `parseInt("100px")` → 100 (reads until non-digit)  
👉 `Number("100px")` → NaN (whole string must be valid number).

#### Q3. What’s the difference between `toFixed()` and `toPrecision()`?
👉 `toFixed(n)` → fix decimal places  
👉 `toPrecision(n)` → fix total digits

---

### ⚡ Shortcut to remember:

- `Fixed = decimal fixed`

- `Precision = total digits`

- `parseInt → Integer only`

- `parseFloat → Decimal bhi le lega`

---

#### 1. Conversion Methods

```js
let num = 123.456;

console.log(num.toString());    // "123.456"
console.log(num.toString(2));   // "1111011.01110100101111001" (binary)
console.log(num.toString(8));   // "173.35165705027" (octal)
console.log(num.toString(16));  // "7b.74bc6a7ef9" (hexadecimal)
```