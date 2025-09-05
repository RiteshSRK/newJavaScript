### 1. **API** stands for **Application Programming Interface**.

- An **API** is a **set of rules and protocols** that allows different **software** or **applications** to **communicate** with **each other**. 

- It defines the methods and data formats that applications can use to request and exchange information, enabling them to work together seamlessly.

### 2. Web API
- A **Web API** is a specific type of API that operates over the web, typically using HTTP/HTTPS protocols. Web APIs allow different systems to interact over the internet, often returning data in formats like JSON or XML. They are commonly used for web services, enabling developers to access functionality and data from remote servers.

- In summary, while all Web APIs are APIs, not all APIs are Web APIs. Web APIs are specifically designed for web-based communication.

### 3. What is REST API?

- **REST** (**Representational State Transfer**) is an **architectural** style for building APIs.

- It uses **HTTP methods** to perform operations on resources (data).

- Each resource is identified by a URL (Uniform Resource Locator).

- REST is stateless, meaning each request is independent and carries all necessary information.

👉 Think of it like:

- Resource = Data (e.g., user, product, order)

- HTTP Methods = Actions (CRUD operations)

---

## 📌 HTTP Methods in REST API
### 1. GET (Read data)

- Used to fetch data from the server.

- Data is usually returned in JSON format.

- HTTP Response Codes:

  - `200 OK` (Success)

  - `404 Not Found` (Resource doesn't exist)

  - `400 Bad Request` (e.g., invalid parameters)

✅ Example:
```http
GET /api/users
```

Response:
```json
[
  { "id": 1, "name": "Ritesh" },
  { "id": 2, "name": "Rahul" }
]
```

### 2. POST (Create data)

- Used to **create a new resource** on the server.

- Sends data in the **request body**.

- Server returns newly created resource (with `id`).

- HTTP Response Codes:

  - `201 Created` (Success, new resource created)

  - `400 Bad Request` (e.g., invalid data in request body)

✅ Example:
```http
POST /api/users
Content-Type: application/json

{
  "name": "Ritesh"
}
```

Response:
```json
{ "id": 3, "name": "Ritesh" }
```

### 3. PUT (Update data)

- Used to **update/replace an existing resource**.

- Requires the **full object** in the request body.

- Idempotent: Calling PUT multiple times with the same data gives the same result.

- HTTP Response Codes:

  - `200 OK` (Success)

  - `204 No Content` (Success, no content returned)

  - `201 Created` (If a new resource was created)

✅ Example:
```http
PUT /api/users/3
Content-Type: application/json

{
  "id": 3,
  "name": "Ritesh Kumar"
}
```

Response:
```json
{ "id": 3, "name": "Ritesh Kumar" }
```

### 4. PATCH (Partial Update) ⚡ (extra but important)

Used to **partially update** a resource (only specific fields).

✅ Example:
```http
PATCH /api/users/3
Content-Type: application/json

{
  "name": "Ritesh G."
}
```

Response:
```json
{ "id": 3, "name": "Ritesh G." }
```

### 5. DELETE (Remove data)

- Used to **delete a resource** from the server.

- HTTP Response Codes:

  - `200 OK` (Success, often with a confirmation message in the body)

  - `204 No Content` (Success, no body returned)

  - `202 Accepted` (Request accepted for processing, but not yet executed)

  - `404 Not Found` (Resource already doesn't exist)

✅ Example:
```http
DELETE /api/users/3
```

Response:
```http
204 No Content
```

## 🔑 Quick Interview Comparison

| Method | Purpose              | Idempotent? | Body Required?  |
| ------ | -------------------- | ----------- | --------------- |
| GET    | Retrieve resource    | ✅ Yes       | ❌ No            |
| POST   | Create new resource  | ❌ No        | ✅ Yes           |
| PUT    | Replace resource     | ✅ Yes       | ✅ Yes (full)    |
| PATCH  | Update part resource | ✅ Yes       | ✅ Yes (partial) |
| DELETE | Remove resource      | ✅ Yes       | ❌ Usually No    |

## 🎯 Example Use Case (Users API)

- `GET /users` → Get all users

- `GET /users/1` → Get user with id=1

- `POST /users` → Add a new user

- `PUT /users/1` → Update entire user details

- `PATCH /users/1` → Update only specific fields

- `DELETE /users/1` → Delete user with id=1

---

