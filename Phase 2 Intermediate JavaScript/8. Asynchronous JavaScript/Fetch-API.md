## Fetch API in JavaScript

### 1. What is Fetch API?

- The Fetch API provides a **modern**, **promise-based interface** for **making HTTP requests** in JavaScript.

- It’s **built in the browser** (no extra library needed).

### Basic `fetch()` Syntax

```js
fetch(url, options)
  .then(response => {
    // response object
  })
  .catch(error => {
    // error handling
  });
```

- **url** → The API endpoint you want to call.

- **options (optional)** → Method (`GET`, `POST`, etc.), headers, body, etc.

- **Returns a Promise** → which resolves to a **Response object**.

### 1. Making a Simple GET Request

```js
fetch("https://jsonplaceholder.typicode.com/users")
  .then(response => response.json()) // Convert response body to JSON
  .then(data => console.log("Users:", data))
  .catch(error => console.error("Error:", error));
```

✅ Output: An array of users from API.

```js
// Basic GET request
fetch('https://jsonplaceholder.typicode.com/posts/1')
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json(); // Parse JSON data
  })
  .then(data => {
    console.log('Data:', data);
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

### Understanding `response.json()`

- The **Response object** has methods to read the body:

  - `.json()` → **parse response as JSON** (returns a Promise)

  - `.text()` → parse response as text

  - `.blob()` → parse response as binary (files/images)

- You **must call one** of these to extract the data.

```js
fetch("https://jsonplaceholder.typicode.com/todos/1")
  .then(res => res.json())   // JSON parsing
  .then(data => console.log(data))
  .catch(err => console.error(err));
```

✅ Output:
```json
{ "userId": 1, "id": 1, "title": "delectus aut autem", "completed": false }
```

### Using fetch() with async/await

Cleaner syntax than `.then()` chaining.

```js
async function getPosts() {
  try {
    let response = await fetch("https://jsonplaceholder.typicode.com/posts");
    let data = await response.json();  // parse body
    console.log("Posts:", data);
  } catch (error) {
    console.error("❌ Fetch failed:", error);
  }
}

getPosts();
```

### Error Handling in Fetch

- ⚠️ Important: `fetch()` does not throw an error on HTTP errors like 404 or 500.
It only rejects on network errors.

- So, always check `response.ok`.

```js
async function getData() {
  try {
    let response = await fetch("https://jsonplaceholder.typicode.com/invalid-url");
    
    if (!response.ok) {
      throw new Error(`HTTP Error! Status: ${response.status}`);
    }

    let data = await response.json();
    console.log(data);
  } catch (error) {
    console.error("❌ Error:", error.message);
  }
}

getData();
```

```js
// Output
❌ Error: HTTP Error! Status: 404
```

### 2. POST Request with JSON Data

To send data, use options (`method`, `headers`, `body`).

```js
fetch("https://jsonplaceholder.typicode.com/posts", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
    title: "foo",
    body: "bar",
    userId: 1
  })
})
  .then(response => response.json())
  .then(data => console.log("Created:", data))
  .catch(error => console.error("Error:", error));
```

✅ Output:

```json
{ "id": 101, "title": "foo", "body": "bar", "userId": 1 }
```

```js
const newPost = {
  title: 'My New Post',
  body: 'This is the content of my post',
  userId: 1
};

fetch('https://jsonplaceholder.typicode.com/posts', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify(newPost)
})
  .then(response => response.json())
  .then(data => {
    console.log('Success:', data);
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

### 3. PUT and DELETE Requests

```js
// PUT (Update) request
fetch('https://jsonplaceholder.typicode.com/posts/1', {
  method: 'PUT',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    title: 'Updated Title',
    body: 'Updated content',
    userId: 1
  })
})
  .then(response => response.json())
  .then(data => console.log('Updated:', data));

// DELETE request
fetch('https://jsonplaceholder.typicode.com/posts/1', {
  method: 'DELETE'
})
  .then(response => {
    console.log('Delete successful, status:', response.status);
  });
```

### In short:

- `fetch()` → makes request, returns a `Response` object.

- `response.json()` → converts body into JSON.

- Always check `response.ok` for HTTP errors.

---

### Interview Notes

#### Q1: What does `fetch()` return?
A: A Promise that resolves to a `Response` object.

#### : Why do we use `response.json()`?
A: Because the response body is a **ReadableStream**, and `.json()` parses it into usable JSON.

#### Q3: Does fetch throw error on 404?
A: No, it resolves normally. You need to check `response.ok `manually.

#### Q4: Difference between `response.json()` and `response.text()`?
A: `.json()` parses as JSON, `.text()` parses as plain text string.