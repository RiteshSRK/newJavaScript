## Conditional Statements in JavaScript

> Conditional statements allow code to **make decisions based on conditions** (`true`/`false`).

### 1. `if` Statement

- Runs a block of code **if condition is true**.

👉 Example:

```js
let age = 20;
if (age >= 18) {
  console.log("You can vote"); // ✅ runs
}
```

### 2. `if...else` Statement

> Executes one block of code if the condition is true; otherwise, it runs the `else` block.

👉 Example:

```js
let age = 16;
if (age >= 18) {
  console.log("You can vote");
} else {
  console.log("You cannot vote"); // ✅ runs
}
```

### Nested if:

```js
let username = "admin";
let password = "1234";

if (username === "admin") {
  if (password === "1234") {
    console.log("Login successful!");
  } else {
    console.log("Wrong password!");
  }
} else {
  console.log("User not found!");
}

```

### 3. `if...else if...else` Statement

- Checks multiple conditions in sequence.

- First true condition block executes, rest are skipped.

👉 Example:

```js
let marks = 72;

if (marks >= 90) {
  console.log("Grade A");
} else if (marks >= 75) {
  console.log("Grade B"); // ✅ runs
} else if (marks >= 50) {
  console.log("Grade C");
} else {
  console.log("Fail");
}
```

### 4. `switch` Statement

- Used to compare one value against multiple possible options (cases).

    - Compares value with `case` labels.

    - Uses `break` to stop execution, otherwise **fall-through** happens.

    - `default` runs if no case matches.

👉 Example:

```js
let day = 3;

switch (day) {
  case 1:
    console.log("Monday");
    break;
  case 2:
    console.log("Tuesday");
    break;
  case 3:
    console.log("Wednesday"); // ✅ runs
    break;
  default:
    console.log("Invalid day");
}
```

### Days of Week (switch)

```js
let day = 6;

switch (day) {
  case 1:
    console.log("Monday");
    break;
  case 2:
    console.log("Tuesday");
    break;
  case 3:
    console.log("Wednesday");
    break;
  case 4:
    console.log("Thursday");
    break;
  case 5:
    console.log("Friday");
    break;
  case 6:
    console.log("Saturday");    //  Saturday
    break;
  case 7:
    console.log("Sunday");
    break;
  default:
    console.log("Invalid day number");
}
```

### Traffic Light (switch)

```js
let signal = "yellow";

switch (signal) {
  case "red":
    console.log("Stop immediately!");
    break;
  case "yellow":
    console.log("Slow down, be ready!");    //  Slow down, be ready!
    break;
  case "green":
    console.log("Go ahead!");
    break;
  default:
    console.log("Invalid signal color");
}
```
