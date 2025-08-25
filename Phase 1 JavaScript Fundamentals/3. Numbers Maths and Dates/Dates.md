## JavaScript Date Object

✅ JavaScript me Date() object hota hai jo date aur time ke liye use hota hai.

- By default → system ki current date/time deta hai.

- Internally → **milliseconds since Jan 1, 1970 UTC (Unix Epoch)** ke form me store hota hai.

👉 Example:

```js
let date = new Date();
console.log(date); // current date & time
```

### Ways to Create Date Objects

```js
new Date()                  // current date & time
new Date("2025-08-25")      // specific date (YYYY-MM-DD)
new Date(2025, 7, 25, 10, 30) // year, month(0-11), day, hr, min
new Date(0)                 // Jan 1, 1970 UTC
```

## Important Date Methods
### 1. Get Methods:

```js
let d = new Date();

console.log(d.getFullYear()); // 2025
console.log(d.getMonth());    // 7 (August → 0-based)
console.log(d.getDate());     // 25 (day of month)
console.log(d.getDay());      // 1 (0=Sunday, 1=Monday,...)
console.log(d.getHours());    // 10
console.log(d.getMinutes());  // 30
console.log(d.getSeconds());  // 45
console.log(d.getMilliseconds()); // 123
console.log(d.getTime());     // milliseconds since 1970
```

### 2. Set Methods:

```js
let d = new Date();
d.setFullYear(2030);
d.setMonth(0);     // January
d.setDate(1);
d.setHours(12);
d.setMinutes(0);
d.setSeconds(0);

console.log(d);
```

### 3. Conversion Methods:

```js
let d = new Date();

console.log(d.toString());     // Full date as string
console.log(d.toDateString()); // Only date
console.log(d.toTimeString()); // Only time
console.log(d.toISOString());  // ISO format (2025-08-25T09:30:00.000Z)
console.log(d.toUTCString());  // UTC format
console.log(d.toLocaleDateString()); // Local format (e.g. 8/25/2025)
console.log(d.toLocaleTimeString()); // Local time
console.log(d.toLocaleString());     // Local date & time
```

```js
let d = new Date();

console.log(d.toString());     // Mon Aug 25 2025 12:05:49 GMT+0000 (Coordinated Universal Time)
console.log(d.toDateString()); // Mon Aug 25 2025
console.log(d.toTimeString()); // 12:05:49 GMT+0000 (Coordinated Universal Time)
console.log(d.toISOString());  // 2025-08-25T12:05:49.504Z
console.log(d.toUTCString());  // Mon, 25 Aug 2025 12:05:49 GMT
console.log(d.toLocaleDateString()); // 8/25/2025
console.log(d.toLocaleTimeString()); // 12:05:49 PM
console.log(d.toLocaleString());     // 8/25/2025, 12:05:49 PM
```

### Shortcut Table:

| Method                 | Description             | Example Output               |
| ---------------------- | ----------------------- | ---------------------------- |
| `getFullYear()`        | Get year                | `2025`                       |
| `getMonth()`           | Get month (0-11)        | `7`                          |
| `getDate()`            | Day of month (1-31)     | `25`                         |
| `getDay()`             | Day of week (0=Sun)     | `1`                          |
| `getHours()`           | Hour (0-23)             | `10`                         |
| `getMinutes()`         | Minute (0-59)           | `30`                         |
| `getSeconds()`         | Seconds (0-59)          | `45`                         |
| `getMilliseconds()`    | Milliseconds (0-999)    | `123`                        |
| `getTime()`            | Milliseconds since 1970 | `1692950400000`              |
| `setFullYear(y)`       | Set year                | `2030`                       |
| `setMonth(m)`          | Set month (0=Jan)       | `0`                          |
| `toDateString()`       | Date only               | `"Mon Aug 25 2025"`          |
| `toTimeString()`       | Time only               | `"10:30:45 GMT+0530"`        |
| `toISOString()`        | ISO format              | `"2025-08-25T09:30:00.000Z"` |
| `toLocaleDateString()` | Local date              | `"8/25/2025"`                |
| `toLocaleTimeString()` | Local time              | `"10:30:45 AM"`              |

---

### Date Formatting Methods

| Method                 | Example Output         |
| ---------------------- | ---------------------- |
| `toDateString()`       | `Mon Aug 25 2025`      |
| `toTimeString()`       | `14:30:45 GMT+0530`    |
| `toISOString()`        | `2025-08-25T09:00:00Z` |
| `toLocaleDateString()` | `8/25/2025` (US)       |
| `toLocaleTimeString()` | `2:30:45 PM`           |
| `toUTCString()`        | `Mon, 25 Aug 2025...`  |



---

## 🎯 Interview-style Q&A

#### Q1. Difference between `getDate()` and `getDay()`?
👉 `getDate()` → day of month (1–31)  
👉 `getDay()` → day of week (0–6, Sunday=0)

#### Q2. How does JavaScript store Date internally?
👉 As milliseconds since Jan 1, 1970 UTC (Unix Epoch).

#### Q3. How to get current timestamp?
👉 `Date.now()` → milliseconds    
👉 `Math.floor(Date.now() / 1000)` → seconds

#### Q4. How to format date in user’s local timezone?
👉 `date.toLocaleString()` / `toLocaleDateString()` / `toLocaleTimeString()`.

### ⚡ Quick Tip for Projects:

- For formatting → always use toLocaleDateString() (handles country format).

- For APIs → use toISOString() (standard format).

---

## Date & Time in Indian Time Zone (IST)

### ✅ Example 1: Current Date & Time in IST

```js
let now = new Date();
let indianTime = now.toLocaleString("en-IN", { timeZone: "Asia/Kolkata" });

console.log("🇮🇳 Indian Time:", indianTime);
```

👉 Output:  
`🇮🇳 Indian Time: 25/8/2025, 10:45:30 am`

---

### ✅ Example 2: Only Time in IST

```js
let now = new Date();
let indianTime = now.toLocaleTimeString("en-IN", { timeZone: "Asia/Kolkata" });

console.log("⏰ IST Time:", indianTime);
```

👉 Output:  
`⏰ IST Time: 10:50:45 am`

---

### ✅ Example 3: Only Date in IST

```js
let now = new Date();
let indianDate = now.toLocaleDateString("en-IN", { timeZone: "Asia/Kolkata" });

console.log("📅 IST Date:", indianDate);
```

👉 Output:  
`📅 IST Date: 25/8/2025`

---

### ✅ Example 5: Digital Clock (Always in IST)

```js
function showISTClock() {
  let now = new Date();
  let time = now.toLocaleTimeString("en-IN", { timeZone: "Asia/Kolkata" });
  let date = now.toLocaleDateString("en-IN", { timeZone: "Asia/Kolkata" });

  console.log(`⏰ ${time} | 📅 ${date}`);
}

setInterval(showISTClock, 1000);
```

👉 Output (updates every second):   
`⏰ 10:53:01 am | 📅 25/8/2025`

---

### ⚡ Pro Tip (Interview Point)

- By default, `new Date()` system ke timezone me hota hai.

- Agar **fixed timezone (like IST)** chahiye → `toLocaleString("en-IN", { timeZone: "Asia/Kolkata" })` use karna chahiye.

---

## Real-Life Examples with Date & Time in JavaScript

### Example 1: Show Current Date & Time on Website (Digital Clock)

```js
function showClock() {
  let now = new Date();
  let time = now.toLocaleTimeString();
  let date = now.toLocaleDateString();

  console.log("⏰ Time:", time, "| 📅 Date:", date);
}

setInterval(showClock, 1000); // update every second
```

👉 Output (updates every second):   
`⏰ Time: 10:45:30 AM | 📅 Date: 8/25/2025`

---

### Example 2: Countdown Timer (e.g. Sale Ending Soon ⚡)

```js
let endDate = new Date("2025-12-31 23:59:59");

function countdown() {
  let now = new Date();
  let diff = endDate - now; // milliseconds

  if (diff <= 0) {
    console.log("🎉 Sale Ended!");
    return;
  }

  let days = Math.floor(diff / (1000 * 60 * 60 * 24));
  let hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
  let mins = Math.floor((diff / (1000 * 60)) % 60);
  let secs = Math.floor((diff / 1000) % 60);

  console.log(`⏳ ${days}d ${hours}h ${mins}m ${secs}s left`);
}

setInterval(countdown, 1000);
```

👉 Useful for E-commerce countdown timers (Flipkart, Amazon, etc.).

---

### Example 3: Days Passed Since Registration

```js
let registerDate = new Date("2025-01-01");
let today = new Date();

let diff = today - registerDate;
let daysPassed = Math.floor(diff / (1000 * 60 * 60 * 24));

console.log(`🧑 You registered ${daysPassed} days ago.`);
```

👉 Common in user profiles → “You joined 237 days ago”.

---

### Example 4: Last Login Time

```js
let lastLogin = new Date("2025-08-20T14:30:00");

console.log("👤 Last Login:", lastLogin.toLocaleString());
```

👉 Output: `👤 Last Login: 8/20/2025, 2:30:00 PM`

---

### Example 5: Check Expiry Date (Subscription / Token)

```js
let expiryDate = new Date("2025-09-01");
let now = new Date();

if (now > expiryDate) {
  console.log("⚠️ Subscription expired!");
} else {
  console.log("✅ Subscription is active.");
}
```

👉 Very useful in subscriptions, JWT tokens, free-trial apps.

---

### Example 6: Format Date as DD/MM/YYYY

```js
let d = new Date();

let day = String(d.getDate()).padStart(2, '0');
let month = String(d.getMonth() + 1).padStart(2, '0'); // +1 because 0=Jan
let year = d.getFullYear();

console.log(`${day}/${month}/${year}`);
```

👉 Output: `25/08/2025`

---

### Example 7: Greeting Based on Time (Good Morning/Afternoon/Night)

```js
let now = new Date();
let hour = now.getHours();

if (hour < 12) {
  console.log("🌞 Good Morning!");
} else if (hour < 18) {
  console.log("🌤️ Good Afternoon!");
} else {
  console.log("🌙 Good Evening!");
}
```

👉 Common in **chat apps**, **dashboards**, **landing pages**.

---

### ⚡ Ye real-world examples tumhe practical + interview ready bana denge.

Bhai, kya mai tumhe iska mini-project idea (Digital Clock + Greeting + Date Formatting) ek saath bana ke code du jo tum apne portfolio website me use kar sako?