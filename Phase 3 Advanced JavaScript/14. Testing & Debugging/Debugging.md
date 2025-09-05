# Debugging in JavaScript

## 1. What is Debugging?

- Debugging is the process of **finding and fixing errors** (**bugs**) in your code.

- JavaScript provides tools like `console.log`, `debugger`, and **browser DevTools** to make debugging easier.

### 2. Using console.log()

- Prints values in the console for inspection.

- Most common debugging method.

```js
let user = { name: "Ritesh", age: 25 };
console.log(user);             // Print object
console.log(user.name);        // Print property
console.log("Age:", user.age); // With message
```

#### 👉 Variants:

```js
console.error("Error message"); // Red error text
console.warn("Warning!");       // Yellow warning
console.table(user);            // Display object in table format
```

### 3. Using debugger Keyword

- Pauses code execution at that line (like a breakpoint).

- Opens DevTools automatically.

```JS
function add(a, b) {
  debugger; // Execution stops here
  return a + b;
}
console.log(add(5, 10));
```

### 4. Chrome DevTools Guide

- **Windows/Linux:** `F12` or `Ctrl+Shift+I`

- Right-click → Inspect → Console.

- **Mac:** `Cmd+Opt+I`

#### Key DevTools Panels

- **Console Tab** → Run JS, view logs.

- **Sources Tab** → Set breakpoints, step through code.

- **Network Tab** → Debug API calls.

- **Application Tab** → Inspect localStorage, cookies.