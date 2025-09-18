### 5. `LocalStorage`, and `SessionStorage`
#### Teach:
- **localStorage API**: `setItem`, `getItem`, `removeItem`, `clear()`
- **sessionStorage API**
- Storing/retrieving **strings** vs **JSON**

#### Confusion:
- Why only strings work in localStorage

#### Mindset:
- Use localStorage for state, cookies for cross-tab auth
#### Practice:
- Save theme preference in localStorage
- Login form that remembers user's name using storage

### 1. `LocalStorage`:

- localStorage object allows **store key–value pairs** in the **client’s browser**.

- Data persists **even after the browser is closed**.

- **Storage capacity:** around **5–10 MB** (varies by browser or origin).

- Data is stored per origin (domain + protocol).

- **Key-Value Pairs:** Data is stored as key-value pairs (**objects**/**arrays** need `JSON.stringify`).

#### 1. `localStorage.setItem(key, value)`:

- Stores a key-value pair. Both `key` and `value` must be **strings**.

- If the `key` already exists, its `value` will be updated.

```js
localStorage.setItem('username', 'Alice');
localStorage.setItem('theme', 'dark');
```

#### 2. `localStorage.getItem(key)`:

- Retrieves the value associated with the given `key`.

- Returns `null` if the `key` does not exist.

```js
const username = localStorage.getItem('username'); // "Alice"
const theme = localStorage.getItem('theme');     // "dark"
const nonexistentKey = localStorage.getItem('nonexistent'); // null
```

#### 3. `localStorage.removeItem(key)`:

- Removes the key-value pair associated with the given `key`.

```js
localStorage.removeItem('theme');
const themeAfterRemoval = localStorage.getItem('theme'); // null
```

#### 4. `localStorage.clear()`:

Removes all key-value pairs for the current origin. Use with caution!

```js
localStorage.clear();
const usernameAfterClear = localStorage.getItem('username'); // null
```

---

```js
// Save data
localStorage.setItem("username", "Ritesh");

// Get data
let user = localStorage.getItem("username"); 
console.log(user); // "Ritesh"

// Remove item
localStorage.removeItem("username");

// Clear all
localStorage.clear();

```


#### Storing Non-String Data (Objects and Arrays):
- Since `localStorage` only stores strings, you need to convert objects and arrays to JSON strings before storing them, and then parse them back when retrieving.

```js
// Storing an Arrays
localStorage.setItem("friends", JSON.stringify(["Rajan","Satyam","Gaurav"]));
const fr = JSON.parse(localStorage.getItem("friends"));
console.log(fr);
```

```js
// Storing an object
const userSettings = {
    fontSize: '16px',
    darkMode: true,
    notifications: ['email', 'sms']
};

localStorage.setItem('userSettings', JSON.stringify(userSettings));

// Retrieving and parsing the object
const storedSettingsString = localStorage.getItem('userSettings');
if (storedSettingsString) {
    const retrievedSettings = JSON.parse(storedSettingsString);
    console.log(retrievedSettings.darkMode); // true
    console.log(retrievedSettings.notifications[0]); // "email"
}
```

- ⚡`LocalStorage`: Saving JWT tokens, dark mode preference, cart items.

---

### `SessionStorage`:

- Same as localStorage
- **Data available only** for the **current tab or window**. If the user **closes the tab**, the `sessionStorage` data is **cleared**.

- Same storage capacity (~5 MB).

- Same origin restrictions.

👉 Example:

```js
// Save data
sessionStorage.setItem("theme", "dark");

// Get data
let theme = sessionStorage.getItem("theme");
console.log(theme); // "dark"

// Remove
sessionStorage.removeItem("theme");

// Clear all
sessionStorage.clear();
```

- `sessionStorage.key(index)`:

```js
console.log(sessionStorage.key(0));
```

- `sessionStorage.length`:

```js
console.log(sessionStorage.length);
```

⚡ Same localStorage wala hi feture hai bas ye tab/window closed hote hi data clear kar data hai.

---

