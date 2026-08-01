# Objects in JavaScript

An object is a collection of **key-value pairs** in JavaScript.

- **Keys** → called properties (always `string` or `symbol`).

- **Values** → can be anything (`string`, `number`, `boolean`, `array`, `function`, `another object`).

## Object literals

```js
const person = {
    name: "Ritesh",
    age: 24,
    isStudent: True
};
```

```js
//  Constructor notation: Object using new keyword
const person = new Object();
person.name = "Alice";
person.age = 30;
person.isStudent = false;
```

## Accessing Object Properties

📖 You can access properties using **dot notation** or **bracket notation**.

```js
//  Dot notation:
console.log(person.name); // Alice
```

```js
//  Bracket notation:
console.log(person['age']); // 30
```

## Adding and Modifying Properties
You can **add** or **modify** properties easily:

```js
person.email = "alice@example.com";     // Adding a new property
person.age = 31;    // Modifying an existing property
```

## Deleting Properties
You can **delete** properties with the `delete` operator:

```js
delete person.isStudent;
```

## Nested Objects
Objects can contain other objects:

```js
const student = {
    name: "Bob",

    details: {
        age: 25,
        major: "Computer Science"
    }
};

console.log(student.details.major);     // Computer Science
```

## Methods in Objects

📖 Objects can also have methods (**functions stored as properties**):

```js
const calculator = {
    add: function(a, b) {
        return a + b;
    },
    subtract: function(a, b) {
        return a - b;
    }
};

console.log(calculator.add(5, 3));  // 8
console.log(calculator.subtract(5, 3)); // 2
```
```js
let user = {
  name: "Ritesh",
  greet: function() {
    return "Hello, " + this.name;
  }
};

console.log(user.greet()); // Hello, Ritesh

```
**⚡ Interview Note:** `this` keyword inside method refers to the ***current object***.

## Array of Objects
Storing information of multiple students

```js
const bioInfo = [
    {
        name: "aman",
        grade: "A+",
        city: "Delhi"
    },
    {
        name: "shradha",
        grade: "A",
        city:"Pune"
    },
    {
        name: "karan",
        grade: "c",
        city: "Mumbai"
    }
];

console.log(bioInfo[0].name);   //Output: aman
console.log(bioInfo[0].name = "Ritesh");    //Output: Ritesh
console.log(bioInfo[0]);    //Output: { name: 'Ritesh', grade: 'A+', city: 'Delhi' }
```

## Iterating Objects

```js
let student = { id: 1, name: "Ritesh", course: "JS" };

for (let key in student) {
  console.log(key, student[key]);
}
```

```js
// Modern way
Object.keys(student).forEach(k => console.log(k, student[k]));
```

## `Object.keys()`, `Object.values()`, `Object.entries()`

```js
let person = { name: "Ritesh", age: 25 };

console.log(Object.keys(person));   // ["name", "age"]
console.log(Object.values(person)); // ["Ritesh", 25]
console.log(Object.entries(person)); // [["name", "Ritesh"], ["age", 25]]
```

```js
const person = {
  name: "Rahul",
  age: 30,
  city: "Mumbai"
};

const keysArray = Object.keys(person);
console.log(keysArray); // Output: ['name', 'age', 'city']
```

```js
const person = {
  name: "Rahul",
  age: 30,
  city: "Mumbai"
};

const valuesArray = Object.values(person);
console.log(valuesArray); // Output: ['Rahul', 30, 'Mumbai']
```

```js
const person = {
  name: "Rahul",
  age: 30,
  city: "Mumbai"
};

const entriesArray = Object.entries(person);
console.log(entriesArray);
// Output:
// [ ['name', 'Rahul'], ['age', 30], ['city', 'Mumbai'] ]
```

```js
const person = {
  name: "Rahul",
  age: 30,
  city: "Mumbai"
};

// Method 1: Using for...in (The older way)
for (let key in person) {
  console.log(key, person[key]);
}

// Method 2: Using Object.entries() with for...of (Modern & readable)
for (let [key, value] of Object.entries(person)) {
  console.log(key, value);
}

// Method 3: Using forEach (Functional programming style)
Object.entries(person).forEach(([key, value]) => {
  console.log(key, value);
});
```

## Spread Operator (`...`)

📖 It expands arrays or objects into individual elements.

### 1. Spread with Arrays

```js
//  Copying an array
let arr1 = [1, 2, 3];
let arr2 = [...arr1]; // shallow copy

console.log(arr2); // [1, 2, 3]
console.log(arr1 === arr2); // false (different references)
```

### 2. Spread with Objects

```js
//  Copying an object
let user = { name: "Ritesh", city: "Delhi" };
let copyUser = { ...user };

console.log(copyUser); // { name: "Ritesh", city: "Delhi" }
```

```js
//  Adding new properties while copying
let user = { name: "Ritesh" };
let newUser = { ...user, age: 25, city: "Delhi" };

console.log(newUser);
// { name: "Ritesh", age: 25, city: "Delhi" }
```

```js
let arr1 = [1, 2];
let arr2 = [3, 4];
let combinedArr = [...arr1, ...arr2];  
// [1,2,3,4]

let user = { name: "Ritesh", city: "Delhi" };
let updatedUser = { ...user, city: "Mumbai", age: 25 };  
// { name:"Ritesh", city:"Mumbai", age:25 }

let str = "JS";
console.log([...str]); // ["J", "S"]
```

### ⚡ Interview Notes

#### Q: Difference between spread and rest operator (...)?

- **Spread** → expands (`[...arr]`, `{...obj}`)

- **Rest** → collects (`function sum(...args) {}`)

## 🔥 Destructuring in JavaScript

📖 Destructuring allows you to **extract values** from **arrays** or **objects** into **variables**.

### 1. Object Destructuring

```js
const person = { name: "Ritesh", age: 25, city: "Delhi" };

const { name, age } = person;
console.log(name); // Ritesh
console.log(age);  // 25
```

```js
//  Assigning to new variable names
const { name: fullName, age: years } = person;
console.log(fullName); // Ritesh
console.log(years);    // 25
```

```js
//  Default values
const { country = "India" } = person;
console.log(country); // India (default applied)
```

Nested destructuring
```js
const employee = {
  id: 101,
  profile: { firstName: "Ritesh", lastName: "Gupta" }
};

const { profile: { firstName, lastName } } = employee;
console.log(firstName, lastName); // Ritesh Gupta
```

### 2. Array Destructuring

```js
const numbers = [10, 20, 30];

const [x, y] = numbers;
console.log(x); // 10
console.log(y); // 20
```

```js
//  Skipping items
const [first, , third] = numbers;
console.log(first, third); // 10 30
```

```js
const user = { id: 1, name: "Ritesh", city: "Delhi" };
const { name, city = "Mumbai" } = user;
console.log(name, city); // Ritesh Delhi

const arr = [100, 200, 300];
const [first, , third, fourth = 400] = arr;
console.log(first, third, fourth); // 100 300 400

let a = 5, b = 10;
[a, b] = [b, a];
console.log(a, b); // 10 5
```

---

## Shallow Copy vs Deep Copy (JavaScript)

### Shallow Copy 

📖 **Shallow copy copies only the first-level properties**.  
If the **object contains nested objects or arrays**, it copies their **references**, not the actual data.

```js
const user1 = {
  name: "Rahul",
  address: {
    city: "Delhi"
  }
};

const user2 = { ...user1 };

user2.name = "Amit";

console.log(user1.name);    //Output: Rahul
console.log(user2.name);    //Output: Amit

user2.address.city = "Mumbai";

// Because address is still shared.
console.log(user1.address.city);    //Output: Mumbai
console.log(user2.address.city);    //Output: Mumbai
```

### Deep Copy

A deep copy duplicates **everything**, including nested objects and arrays.

```js
const user1 = {
  name: "Rahul",
  address: {
    city: "Delhi"
  }
};

// 1. structuredClone (modern, built-in, recommended)
const deep1 = structuredClone(user1);

console.log(deep1);

deep1.address.city = "Prayagraj";

console.log(deep1);
```

```js
const user1 = {
  name: "Rahul",
  address: {
    city: "Delhi"
  }
};

// 2. JSON methods (older, has limitations)
const deep2 = JSON.parse(JSON.stringify(user1));

console.log(deep2);

deep2.address.city = "Varanasi";

console.log(deep2);
```

⚡ Main Limitations of `JSON.parse(JSON.stringify())`?

It removes **functions**.  
It removes `undefined` values.  
It converts `Date` **objects into strings**.  
It doesn't correctly copy `Map` and `Set`.  
It fails with **circular references**.  
It doesn't support `BigInt`.

---

