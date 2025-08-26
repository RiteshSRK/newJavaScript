## 1. What is Math Object?

- `Math` ek **built-in object** hai JavaScript me.

- Ye mathematical constants (π, e, etc.) aur functions (rounding, random, trigonometry, etc.) provide karta hai.

- ❌ Math ek constructor nahi hai → matlab new `Math()` nahi likh sakte.

- ✅ Methods aur properties hamesha static hote hain → `Math.methodName()` use karna padta hai.

## 2. Math Properties (Constants)

| Property       | Meaning            | Example      |
| -------------- | ------------------ | ------------ |
| `Math.PI`      | Value of π (pi)    | `3.14159...` |
| `Math.E`       | Euler’s number     | `2.718...`   |
| `Math.SQRT2`   | Square root of 2   | `1.414...`   |
| `Math.SQRT1_2` | Square root of 1/2 | `0.707...`   |
| `Math.LN2`     | Natural log of 2   | `0.693...`   |
| `Math.LN10`    | Natural log of 10  | `2.302...`   |

👉 Example:

```js
console.log(Math.PI);  // 3.141592653589793
console.log(Math.E);   // 2.718281828459045
```

## 3. Math Methods

### (A) Rounding Numbers

- `Math.round(x)` → nearest integer

- `Math.floor(x)` → always down

- `Math.ceil(x)` → always up

- `Math.trunc(x)` → removes decimal part

```js
console.log(Math.round(4.6)); // 5 (nearest integer)
console.log(Math.floor(4.9)); // 4 (always down)
console.log(Math.ceil(4.1));  // 5 (always up)
console.log(Math.trunc(4.9)); // 4 (remove decimals)
```

### (B) Power & Roots

- `Math.pow(a, b)` → a raised to b

- `a ** b` → ES6 alternative

- `Math.sqrt(x)` → square root

```js
console.log(Math.pow(2, 3)); // 8 (2³)
console.log(2 ** 3);         // 8 (same as above ES6)
console.log(Math.sqrt(16));  // 4
```

### (C) Absolute & Sign

- `Math.abs(x)` → absolute value (distance from 0)

- `Math.sign(x)` → returns:

  - `-1` if negative

  - `0` if zero

  - `1` if positive

```js
console.log(Math.abs(-10));   // 10 (absolute value)
console.log(Math.sign(-5));   // -1
console.log(Math.sign(0));    // 0
console.log(Math.sign(7));    // 1
```

### (D) Min & Max

`Math.min(...values)` → smallest value

`Math.max(...values)` → largest value

```js
console.log(Math.min(10, 20, 5));  // 5
console.log(Math.max(10, 20, 5));  // 20
```

### (E) Random Numbers

- `Math.random()` → 0 (inclusive) se 1 (exclusive) ke beech random decimal deta hai

- `Math.floor(Math.random() * n)` → 0 to (n-1) random integer

- `Math.floor(Math.random() * n) + 1` → 1 to n random integer

```js
console.log(Math.random());         // 0 to 1 (decimal)
console.log(Math.floor(Math.random() * 10)); // 0-9
console.log(Math.floor(Math.random() * 100) + 1); // 1-100
```

**👉 Use case:** Lottery games, OTP generator, dice roll.

### (F) Logarithmic & Exponential

- `Math.log(x)` → natural log (base e)

- `Math.log2(x)` → log base 2

- `Math.log10(x)` → log base 10

- `Math.exp(x)` → e^x

```js
console.log(Math.log(10));     // Natural log (base e)
console.log(Math.log2(8));     // 3 (base 2 log)
console.log(Math.log10(100));  // 2 (base 10 log)
console.log(Math.exp(1));      // e^1 = 2.718
```

### (G) Trigonometry (in radians)

- `Math.sin(x)` → sine

- `Math.cos(x)` → cosine

- `Math.tan(x)` → tangent

👉 **Important:** JavaScript me trigonometric functions **radians** me hote hain, degrees me nahi.

👉 Formula:
`radians = degrees * (Math.PI / 180)`

```js
console.log(Math.sin(Math.PI/2)); // 1 (90°)
console.log(Math.cos(Math.PI));   // -1 (180°)
console.log(Math.tan(0));         // 0
```

---

## 🎯 Interview Quick Notes

- `Math` is not a constructor, can’t do `new Math()`.

- `Math.random()` gives value in `(0, 1)`.

- For rounding decimals → use `Math.round`, `Math.floor`, `Math.ceil`.

- For absolute values → `Math.abs()`.

- **Trigonometric functions work in radians**, not degrees.

---

## 4. Real Life Examples with Math

### Dice Roll (1–6)

```js
let dice = Math.floor(Math.random() * 6) + 1;
console.log("🎲 Dice:", dice);
```

### OTP Generator (6 Digits)

```js
let otp = Math.floor(100000 + Math.random() * 900000);
console.log("🔐 OTP:", otp);
```

### Area of Circle

```js
let radius = 7;
let area = Math.PI * Math.pow(radius, 2);
console.log("⚪ Area of Circle:", area.toFixed(2));
```

### Random Password Generator

```js
function generatePassword(length) {
  let chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
  let password = "";
  for (let i = 0; i < length; i++) {
    let randomIndex = Math.floor(Math.random() * chars.length);
    password += chars[randomIndex];
  }
  return password;
}
console.log("🔑 Password:", generatePassword(8));
```


---

```js
console.log(Math);
```

```js
//  (-) value ko positive value me badal deta hai
console.log(Math.abs(-4));  //  4
```

```js
//  rounded to the nearest integer.
console.log(Math.round(4.6));   //  5
console.log(Math.round(4.4));   //  4
```

```js
//  round up to the nearest integer.
console.log(Math.ceil(4.4));
```

```js
//  rounds down to the nearest integer
console.log(Math.floor(4.6));
```

```js
const arr = [2,6,8,9];

console.log(Math.max(...arr));  //  9
console.log(Math.max(10, 20, 30));  //  30

console.log(Math.min(...arr));  //  2
console.log(Math.min(10, 20, 30));  //  10

console.log(Math.random()); //  0.1040003328580783
console.log((Math.random() * 10) + 1);  //  10.570477026761175
```

```js
//  specially yaad kardo
console.log(Math.floor(Math.random() * 10) + 1);  //  Random number between 1 to 10
```

```js
const min = 10;
const max = 20;

console.log(Math.floor(Math.random() * (max - min + 1)) + min);
console.log(Math.floor(Math.random() * (max - min + 1)) + max);
```

```js
//  Math.pow(base, exponent): Calculates base raised to the power of exponent.
console.log(Math.pow(2, 3)); // 8
```

```js
//  Math.sqrt(): Finds the square root.
console.log(Math.sqrt(16)); // 4
```

```js
//  Math.cbrt(): Finds the cube root
console.log(Math.cbrt(27)); // 3
```