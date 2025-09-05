## 1. What are Template Literals?

> Template literals ( **introduced in ES6** ) are a way to define strings using **backticks** (`) instead of single or double quotes, allowing for enhanced string formatting, **multi-line strings**, and **embedded variables & expressions**.

### Basic Example

```js
let name = "Ritesh";
let message = `Hello ${name}, welcome!`;
console.log(message);
```

✅ Output:

```bash
Hello Ritesh, welcome!
```

### String Interpolation

You can **embed variables** or even **expressions** inside `${}`.

```js
// Variables in strings
const name = 'Alice';
const age = 30;

// Old way (concatenation)
const oldWay = 'Hello, my name is ' + name + ' and I am ' + age + ' years old.';

// Template literal way
const newWay = `Hello, my name is ${name} and I am ${age} years old.`;

console.log(newWay); // "Hello, my name is Alice and I am 30 years old."
```

### Expressions in Template Literals

```js
// Mathematical expressions
const a = 5;
const b = 10;
console.log(`The sum is ${a + b}`); // "The sum is 15"

// Function calls
function getGreeting() {
    return 'Hello there!';
}
console.log(`${getGreeting()} How are you?`); // "Hello there! How are you?"

// Ternary operators
const isLoggedIn = true;
console.log(`User status: ${isLoggedIn ? 'Online' : 'Offline'}`); // "User status: Online"
```

### Multi-line Strings

Without template literals, multi-line strings were messy (`\n`).

```js
// Old way (using \n or concatenation)
const oldMultiline = 'Line 1\n' +
                     'Line 2\n' +
                     'Line 3';

// Template literal way
const newMultiline = `Line 1
Line 2
Line 3`;

console.log(newMultiline);
// Output:
// Line 1
// Line 2
// Line 3
```

### ⚡ In short:

- Use backticks `(`)`.

- `${}` → interpolate variables & expressions.

- Supports multi-line strings.

- Tagged templates → advanced custom formatting.

## 2. What are Modules?

- A **module** is a **separate JavaScript file** that **exports** and **Import** some code between **different files**.

- Helps in code **Organization**, **Reusability**, **Maintenance**, and clean structure.

- There are **two** primary ways to use **modules** in JavaScript.

### 1. ES6 (ECMA Script 2015) Module

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

## 3. Optional Chaining (`?.`) in JavaScript

**Optional chaining** (`?.`) is a **safe** way to **access nested object properties**, **methods**, or **array** without throwing errors if a property doesn’t exist.

### Basic Syntax

```js
// Instead of: ( Old way )
const value = obj && obj.property && obj.property.nested;

// With optional chaining:
const value = obj?.property?.nested;
```

### Accessing Object Properties

```js
const user = {
    name: 'John',
    address: {
        street: '123 Main St',
        city: 'New York'
    }
};

// Safe property access
console.log(user?.address?.city); // 'New York'
console.log(user?.contact?.phone); // undefined (no error)

// Without optional chaining (old way)
const city = user && user.address && user.address.city;
```

### Accessing Array Elements

```js
const users = [
    { name: 'John', age: 30 },
    { name: 'Jane', age: 25 }
];

// Safe array access
console.log(users[0]?.name); // 'John'
console.log(users[5]?.name); // undefined (no error)

// With dynamic indices
const index = 1;
console.log(users?.[index]?.age); // 25
```

### Optional Chaining with Methods

```js
let user = {
  sayHi: function() {
    return "Hello!";
  }
};

console.log(user.sayHi?.());  // "Hello!"
console.log(user.sayBye?.()); // undefined (method doesn’t exist)
```

---

## 4. Nullish Coalescing (`??`)

- The `??` operator provides right-hand side **default value** if the left-hand side is `null` or `undefined`.

#### Basic Example

```js
let username = null;
let displayName = username ?? "Guest";
console.log(displayName); // "Guest"
```

#### Comparison with Logical OR (`||`)

```js
// Logical OR (||) returns right operand for any falsy value
console.log('' || 'default'); // 'default'
console.log(0 || 'default'); // 'default'
console.log(false || 'default'); // 'default'
console.log(null || 'default'); // 'default'
console.log(undefined || 'default'); // 'default'

// Nullish coalescing (??) returns right operand only for null/undefined
console.log('' ?? 'default'); // ''
console.log(0 ?? 'default'); // 0
console.log(false ?? 'default'); // false
console.log(null ?? 'default'); // 'default'
console.log(undefined ?? 'default'); // 'default'
```

#### Combining with Nullish Coalescing

```js
const config = {
    // timeout might be undefined
};

// Set default value if null/undefined
const timeout = config?.timeout ?? 5000;
console.log(timeout); // 5000

const user = {
    settings: {
        theme: 'dark'
    }
};

const theme = user?.settings?.theme ?? 'light';
console.log(theme); // 'dark'
```

### Practical Examples
#### 1. API Response Handling

```js
// Safe access to API responses
async function fetchUserData() {
    try {
        const response = await fetch('/api/user');
        const data = await response.json();
        
        // Safe property access
        const email = data?.user?.profile?.email;
        const posts = data?.user?.posts?.[0]?.title;
        
        console.log('Email:', email ?? 'Not provided');
        console.log('Latest post:', posts ?? 'No posts');
        
    } catch (error) {
        console.error('Fetch failed:', error);
    }
}
```