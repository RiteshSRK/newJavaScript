## What is `async/await`?

`async` → Declares a function with `async` keyword. It **always returns a Promise**, even if you don’t explicitly return one.

`await` → `await` keyword used inside an `async` function. It **pauses execution** until the **Promise settles** ( ***fulfilled*** or ***rejected*** ), and then returns the resolved value.

### Basic Syntax
Declaring an Async Function

```js
// Function declaration
async function fetchData() {
    // Async operations here
}
```

```js
// Function expression
const fetchData = async function() {
    // Async operations here
};
```

```js
// Arrow function
const fetchData = async () => {
    // Async operations here
};
```

```js
// Method in object/class
const api = {
    async getData() {
        // Async operations here
    }
};
```

## 1. `async` function

- If you declare a function with the `async` keyword:

  - It **always returns a Promise**.

  - If you return a value, it is wrapped inside a resolved Promise.

  - If you throw an error, it is wrapped inside a rejected Promise.

```js
async function greet() {
  return "Hello World";
}

greet().then(msg => console.log(msg)); 
// Output: Hello World
```

⚡ Even though we just returned a string, it becomes `Promise.resolve("Hello World")`.

## `await` keyword

- Can only be used inside an `async` function.

- `await` pauses the execution of the function until the Promise is settled (resolved or rejected).

- Makes async code look synchronous.

```js
function fetchData() {
  return new Promise(resolve => {
    setTimeout(() => resolve("Data fetched"), 2000);
  });
}

async function getData() {
  console.log("Fetching...");
  let result = await fetchData();   // waits for 2 sec
  console.log(result);
  console.log("Done!");
}

getData();
```

```bash
Fetching...
Data fetched
Done!
```

## Error Handling with `async/await`

We use `try...catch` block for **error handling**.

```js
function fetchWithError() {
  return new Promise((_, reject) => {
    setTimeout(() => reject("Something went wrong!"), 2000);
  });
}

async function handleData() {
  try {
    let result = await fetchWithError();
    console.log(result);
  } catch (error) {
    console.error("Error:", error);
  }
}

handleData();
```

```js
Error: Something went wrong!
```

### Real Example – Fetching API

```js
async function getUsers() {
  try {
    let response = await fetch("https://jsonplaceholder.typicode.com/users");
    let data = await response.json();
    console.log(data);
  } catch (error) {
    console.error("Error fetching users:", error);
  }
}

getUsers();
```

---

```js
function getNum() {
    return new Promise( (resolve, reject) => {
        setTimeout( () => {
            let num = Math.floor(Math.random() * 10) + 1;
            console.log(num);
            resolve()
        }, 1000)
    });
    
}

async function demo(){
    await getNum();
    await getNum();
    await getNum();
}

demo()
```