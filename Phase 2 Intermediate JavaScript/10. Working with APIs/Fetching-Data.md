## 🌐 Fetching Data in JavaScript

- When working with APIs (REST APIs, GraphQL, etc.), we need to **send HTTP requests** and handle **responses**.

- The two most common ways in JavaScript are:

  1. **fetch API** (built-in, modern browsers)

  2. **axios** (popular third-party library)

### 1️⃣ fetch API

- A **built-in JavaScript function** (no installation needed).

- Returns a **Promise**.

- Works with `async/await` or `.then()`.

#### ✅ Example (GET request)

```js
fetch("https://jsonplaceholder.typicode.com/users")
  .then(response => response.json()) // convert to JSON
  .then(data => console.log(data))
  .catch(error => console.error("Error:", error));
```

#### ✅ Example (POST request)

```js
fetch("https://jsonplaceholder.typicode.com/users", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ name: "Ritesh", email: "ritesh@test.com" })
})
  .then(response => response.json())
  .then(data => console.log("Created:", data))
  .catch(error => console.error("Error:", error));
```

#### ⚡ Interview Notes:

- `fetch` **does not throw error** on HTTP errors (like 404, 500), only on network errors.

- You must check `response.ok` manually:

```js
if (!response.ok) throw new Error("Request failed");
```

#### using `fetch` with `async/await`:

```js
let url = "https://catfact.ninja/fact";

async function getFact(){
    
 try{
    let res1 = await fetch(url);
    let data1 = await res1.json();
    console.log(data1.fact);

    let res2 = await fetch(url);
    let data2 = await res2.json();
    console.log(data2.fact);
    } catch(e){
        console.log(e);
        
    }
}

getFact();
```

---

### 2️⃣ axios

- A **popular library** for HTTP requests.

- Returns a **Promise**.

- Automatically **parses JSON** (no need for `response.json()`).

- Better error handling than `fetch`.

- Supports request cancellation, interceptors, and older browsers.

#### 👉 Install:

```bash
npm install axios
```

#### ✅ Example (GET request)

```js
import axios from "axios";

axios.get("https://jsonplaceholder.typicode.com/users")
  .then(response => console.log(response.data))
  .catch(error => console.error("Error:", error));
```

#### ✅ Example (POST request)

```js
axios.post("https://jsonplaceholder.typicode.com/users", {
  name: "Ritesh",
  email: "ritesh@test.com"
})
  .then(response => console.log("Created:", response.data))
  .catch(error => console.error("Error:", error));
```

#### Interview Notes:

- Axios automatically transforms JSON response.

- Handles HTTP error status codes directly.

- Supports `async/await`:

```js
try {
  const res = await axios.get("/api/data");
  console.log(res.data);
} catch (err) {
  console.error(err);
}
```

---

### 🎯 Interview Q&A Quickies

#### Q1: Which is better: fetch or axios?
👉 `fetch` is lightweight and built-in, `axios` has more features (better error handling, interceptors). Use `axios` in big projects, `fetch` in small/simple apps.

#### Q2: Why does `fetch` not throw error on 404?
👉 Because `fetch` only rejects on network errors, not HTTP status errors. You must check `response.ok`.

---

### 🌐 What is AJAX?

**AJAX (Asynchronous JavaScript and XML)** is a technique used in web development to send and receive data from a server **asynchronously** (without reloading the entire page).

👉 In simple words:     
AJAX allows web pages to **update parts of content dynamically** without a full page refresh.

👉 Bhai, AJAX ka matlab hai dynamic content loading without page reload. Ye ek concept hai, na ki ek alag library.

#### ✅ How AJAX Works (Step by Step)

1. User triggers an event (e.g., click a button).

2. JavaScript sends an HTTP request to the server.

3. Server processes the request and sends a response (usually JSON).

4. JavaScript updates the page dynamically (without reload).