## Mutable kya hota hai?

**Mutable** ka matlab hai **original data ko change (modify) kiya ja sakta hai**.

JavaScript mein **Arrays** aur **Objects** mutable hote hain.

#### Example (Array)

```js
let arr = [1, 2, 3];

arr.push(4);

console.log(arr);   // Output:  [1, 2, 3, 4]
```

👉 `push()` ne original array ko hi change kar diya.

---

#### Example (Object)

```js
let user = {
  name: "Rahul"
};

user.name = "Aman";

console.log(user);  // Output:  { name: "Aman" }
```

👉 Original object modify ho gaya.

---

## Immutable kya hota hai?

**Immutable** ka matlab hai **original data change nahi hota**, balki ek **naya copy** create hota hai.

#### Example (Using Spread Operator)

```js
let arr = [1, 2, 3];

let newArr = [...arr, 4];

console.log(arr);   // [1, 2, 3]
console.log(newArr);    // [1, 2, 3, 4]
```

```js
let fruits = ["Apple", "Banana"];

let newFruits = [...fruits, "Mango"];

console.log(fruits);
// ["Apple", "Banana"]

console.log(newFruits);
// ["Apple", "Banana", "Mango"]
```

👉 Original array same raha.  
👉 Naya array create hua.

---

#### Immutable Object Example

```js
let user = {
  name: "Ritesh",
  age: 22
};

let updatedUser = {
  ...user,
  age: 23
};

console.log(user);
// { name: "Ritesh", age: 22 }

console.log(updatedUser);
// { name: "Ritesh", age: 23 }
```

```js
let user = { name: "John" };

function changeName(obj) {
  return {
    ...obj,
    name: "David"
  };
}

let updatedUser = changeName(user);

console.log(user.name);        // John
console.log(updatedUser.name); // David
```

## React ke Point of View Se

React reference (memory address) check karta hai.

❌ Wrong (Mutable)

```js
const [users, setUsers] = useState(["Ritesh"]);

users.push("Rahul");

setUsers(users);
```

✅ Correct (Immutable)

```js
const [users, setUsers] = useState(["Ritesh"]);

setUsers([...users, "Rahul"]);
```