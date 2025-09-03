# try, catch, finally in JavaScript

📖 `try...catch...finally` is used for **error handling** in JavaScript.

- **try** → block of code that may throw an error.

- **catch** → block that handles the error.

- **finally** → block that always runs, whether an error occurred or not.

### Syntax

```js
try {
    // Code that might throw an error
} catch (error) {
    // Code to handle the error
} finally {
    // Code that always runs
}
```

```js
try {
  JSON.parse("{ invalid json }"); // ❌
} catch (err) {
  console.log("Parsing error:", err.message);
}
```

```js
function getData() {
  try {
    console.log("Fetching data...");
    let response = JSON.parse("{ invalid json }"); // ❌ error
    console.log(response);
  } catch (error) {
    console.log("Error:", error.message);
  } finally {
    console.log("Cleanup completed!");
  }
}

getData();
```

## Throwing Errors (`throw new Error()`)

📖 We can **manually create and throw errors** using the `throw` statement.

```js
try {
  throw new Error("Something went wrong!");
} catch (err) {
  console.log("Caught:", err.message);
}
```

```js
try {
  throw new TypeError("Invalid type provided");
} catch (err) {
  console.log(err.name);    // TypeError
  console.log(err.message); // Invalid type provided
}
```
