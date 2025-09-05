## JSON (JavaScript Object Notation)

- **JSON** is a lightweight, text-based data format, used for **storing and exchanging data**.

- **Widely used:** Commonly used in **web APIs** to **exchange data between a server and a client**.

- **Data Storage:** Some NoSQL databases, like **MongoDB**, use a JSON-like format for storing data.

### 🔑 Key Features of JSON

- Based on **key-value pairs** (like JavaScript objects).

- Keys are always in **double quotes**.

- Supports values: `string`, `number`, `boolean`, `null`, `object`, `array`.

- Language-independent (used in **JavaScript**, **Python**, **Java**, etc.).

#### 👉 Example JSON:

```json
{
  "id": 1,
  "name": "Ritesh",
  "skills": ["JavaScript", "React", "Node.js"],
  "isActive": true
}
```

## 🛠 JSON Parsing in JavaScript

- When we work with APIs, data usually comes in JSON format (as a string).

- To use it in JavaScript, we need to parse it into an object.

### 1️⃣ `JSON.parse()` → String ➝ Object

- Used to convert **JSON string** into a **JavaScript object**.

#### ✅ Example:

```js
let jsonString = '{"id":1,"name":"Ritesh","isActive":true}';

let user = JSON.parse(jsonString);

console.log(user.id);      // 1
console.log(user.name);    // Ritesh
console.log(user.isActive);// true
```

### 2️⃣ `JSON.stringify()` → Object ➝ String

- Used to convert a **JavaScript object** into a **JSON string** (useful for sending data to APIs).

#### ✅ Example:

```js
let user = { id: 1, name: "Ritesh", isActive: true };

let jsonString = JSON.stringify(user);

console.log(jsonString);
// Output: {"id":1,"name":"Ritesh","isActive":true}
```

⚡ Interview Note: `JSON.stringify()` ignores `undefined`, `functions`, and `symbols`.

### 🎯 Real-World Example (API Call)

```js
// Fetch user data
fetch("https://jsonplaceholder.typicode.com/users/1")
  .then(res => res.json()) // JSON.parse() happens internally
  .then(data => console.log("User:", data));

// Send data (POST request)
let newUser = { name: "Ritesh", email: "ritesh@test.com" };

fetch("https://jsonplaceholder.typicode.com/users", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify(newUser) // convert object to JSON string
})
  .then(res => res.json())
  .then(data => console.log("Created:", data));
```