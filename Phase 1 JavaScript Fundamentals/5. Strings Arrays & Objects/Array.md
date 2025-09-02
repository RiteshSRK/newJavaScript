# Array in Java Script
> Array is a special type of object **used to store multiple values in a single variable.** Arrays can hold any type of data, including `numbers`, `strings`, `objects`, and even `other arrays`.

## Creating an Array
> Create an array using either the **array literal** syntax or the Array constructor.

```js
// Using array literal
let fruits = ['apple', 'banana', 'cherry'];
```

```js
// Using Array constructor
let numbers = new Array(1, 2, 3, 4);
```

## Accessing Elements
> **You can access** elements in an array **using their index** (starting from `0`):

```js
console.log(fruits[0]); // Output: 'apple'
console.log(numbers[2]); // Output: 3
```

## Modifying Arrays
> You can `add`, `modify`, or `remove` elements:

```js
// Adding an element
console.log(fruits.push('date')); // Adds 'date' to the end
console.log(fruits);
```

```js
// Modifying an element
console.log(fruits[1] = 'blueberry'); // Changes 'banana' to 'blueberry'
console.log(fruits);
```

```js
// Removing an element
console.log(fruits.pop()); // Removes the last element ('date')
console.log(fruits);
```

## Multidimensional Arrays/Nasted Array
> You can create arrays of arrays (multidimensional arrays):

```js
let matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

console.log(matrix[1][2]); // Output: 6
```

## Spread Operator
> The spread operator (`...`) allows you to expand an array into individual elements:

```js
let fruits = [ 'apple', 'blueberry', 'cherry'];

let moreFruits = ['kiwi', 'mango'];
let combinedFruits = [...fruits, ...moreFruits];

console.log(combinedFruits);
//Output: [ 'apple', 'blueberry', 'cherry', 'kiwi', 'mango' ]
```

---

# 🔥 JavaScript Array Methods

## Mutating Methods (Change original array)

### 1. push()

📖 **Adds one or more** elements to the **end** of an array, and returns the new length.

👉 Hindi Samajh: Array ke last me value add karta hai.

```js
let cars = ['audi','bmw','mahindra'];

let car = cars.push('tata','farari');

console.log(car);   //Output: 5
console.log(cars);  //Output: [ 'audi', 'bmw', 'mahindra', 'tata', 'farari' ]
```

### 2. pop()

📖 **Removes the last element** from an array, returns that element.

```js
let cars = ['audi','bmw','mahindra'];

let car = cars.pop();

console.log(car);   //Output: mahindra
console.log(cars);  //Output: [ 'audi', 'bmw' ]
```

### 3. shift()

📖 **Removes the first element** of an array.

```js
let cars = ['audi','bmw','mahindra','tata'];

let car = cars.shift();

console.log(car);   //Output: audi
console.log(cars);  //Output: [ 'bmw', 'mahindra', 'tata' ]
```

### 4. unshift()

📖 **Adds one or more** elements to the **beginning** of an array.

```js
let cars = ['audi','bmw','mahindra'];

let car = cars.unshift('tata');

console.log(car);   //Output: 4
console.log(cars);  //Output: [ 'tata', 'audi', 'bmw', 'mahindra' ]
```

### 5. splice(`start`, `deleteCount`, `item1`, `item2`, `...`)

📖 **Adds/Removes** elements at a specified index.

```js
let colors = ["red","yellow", "blue", "orange" ,"pink", "white"];

let remElem = colors.splice(1,2);
let addElem = colors.splice(0,0,"green","aqua");

console.log(remElem);   //Output: [ 'yellow', 'blue' ]
console.log(addElem);   //Output: []
console.log(colors);    //Output: [ 'green', 'aqua', 'red', 'orange', 'pink', 'white' ]
```

### 6. sort()
📖 **Sorts the elements** of the array in place.

```js
let days = ["monday","sunday","wednesdaay","tuesday"]

let sortElem = days.sort();

console.log(sortElem);  //Output: [ 'monday', 'sunday', 'tuesday', 'wednesdaay' ]

let numbers = [9,7,4,1,3,2,6,8]

let sortNum = numbers.sort();

console.log(sortNum);   //Output: [1, 2, 3, 4,6, 7, 8, 9]
```

### 7. reverse()

📖 **Reverses the elements** of the array in place.

```js
let cars = ['audi','bmw','mahindra','tata'];

let res = cars.reverse();

console.log(res);   //Output: [ 'tata', 'mahindra', 'bmw', 'audi' ]
```

### 8. fill(`value`, `start`, `end`):
**Fills** the array with a **static value** from **start to end**.

```js
const arr = [1, 2, 3, 4, 5];
console.log(arr.fill(0)); // [0, 0, 0, 0, 0]

const arr1 = [1, 2, 3, 4, 5];
console.log(arr1.fill(1, 2, 4)); // [1, 2, 1, 1, 5]

const arr2 = [1, 2, 3, 4, 5];
console.log(arr2.fill(0, 1)); // [1, 0, 0, 0, 0]

```

### 9. copyWithin(`target`, `start`, `end`)

> **Copies** part of the array to **another location** within the same array.

---

## Non-Mutating Methods (Do NOT change original array)
> These methods **return a new array** or **value** **without modifying** the **original array**.

### 10. concat()

📖 **Merges two** or **more arrays** and returns a **new array**.

```js
let primaryColor = ['red','green','yellow'];
let secondaryColor = ['blue','white','orange'];

let res = primaryColor.concat(secondaryColor);

console.log(res);   //Output: [ 'red', 'green', 'yellow', 'blue', 'white', 'orange' ]
```

### 11. slice(`start`, `end`)

📖 Returns a **shallow copy** of a portion of an array, without changing the original.

```js
let cars = ['audi','bmw','mahindra','tata'];

let res = cars.slice(1);
console.log(res);   //Output: [ 'bmw', 'mahindra', 'tata' ]

let res2 = cars.slice(1,3);
console.log(res2);  //Output: [ 'bmw', 'mahindra' ]

let res3 = cars.slice(-1);
console.log(res3);  //Output: [ 'tata' ]
```

### 12. join(`separator`)
📖 **Joins** all elements of the **array into a string**.

```js
const fruits = ['apple', 'banana', 'orange'];
const joinedFruits = fruits.join(' ');
console.log(joinedFruits);  // Output: apple banana orange

const numbers = [1, 2, 3, 4, 5];
const joinedNumbers = numbers.join("/");
console.log(joinedNumbers); // Output: 1/2/3/4/5
```

### 13. map()

📖 Creates a **new array** by **applying a function to each element**.

```js
const arr = [1,2,3,4,5,6];

const mul = arr.map( (el) =>{
    console.log(el * el);   //Output: 1 4 9 16 25 36
});
```

```js
const data = [
    {
        name : "Ritesh",
        marks : 90
    },
    {
        name : "satyam",
        marks : 95
    },
    {
        name : "rajan",
        marks : 80
    }
];

const student = data.map( (stu) =>{
    console.log(stu.name);
    return stu.name
    return stu.marks / 10;
});

console.log(student);   //Output: [ 9, 9.5, 8 ]
```

```js
//  Method chainning

let myNumber = [1,2,3,4,5,6,7,8,9,10];

let newNum = myNumber
.map( (num) => num + 1)
.map( (num) => num + 10)
.filter( (num) => num % 2 === 0)

console.log(newNum);    //Output: [ 12, 14, 16, 18, 20 ]
```

⚡ Interview Note: Returns new array, doesn’t modify original.

### 14. filter()

📖 Returns a new array with elements that pass the given condition.

```js
//Case:1
const num = [1,2,3,4,5,6,7,8,9,10,12,13,14,15];

const mul = num.filter( (el) =>{
    //console.log(el * el);
    //return (el % 2 == 0);
    //return (el % 2 != 0);
    //return (el > 10);
    return (el < 10);
});

console.log(mul);//Output: [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

```js
//Case:2
const products = [
    { id: 1, name: 'Product 1', price: 40 },
    { id: 2, name: 'Product 2', price: 60 },
    { id: 3, name: 'Product 3', price: 30 }
  ];
  
  const expensiveProducts = products.filter(product => product.price > 50);
  console.log(expensiveProducts); // [{ id: 2, name: 'Product 2', price: 60 }]
```

```js
let books = [
    { title: "book one", genre: "fiction", publish: 1981, edition:2004 },
    { title: "book two", genre: "non-fiction", publish: 1992, edition:2010},
    { title: "book three", genre: "history", publish: 1996, edition:2001 },
    { title: "book four", genre: "science", publish: 1999, edition:2008},
    { title: "book five", genre: "history", publish: 1997, edition:2003 },
    { title: "book six", genre: "fiction", publish: 2000, edition:2000 },
]

const userbook = books.filter( (bk) => bk.genre === 'history');

const userbook2 = books.filter( (bk) => { return bk.publish >= 2000});

const userbook3 = books.filter( (bk) => {
    return bk.publish >= 1995 && bk.genre === 'history'
});

console.log(userbook);
console.log(userbook2);
console.log(userbook3);
```

### 15. reduce(`callback`, `initialValue`)
📖 Reduces array to a single value (like sum, product).
> **Executes** a **reducer** function on **each element** of the array, **resulting** in a **single output** value.

```js
let num = [1,2,3,4,5,6];

//Sum
let sum = num.reduce( (res,el) => res+el);
console.log(sum);//Output: 21

//mul
let mul = num.reduce( (res,el) => res*el);
console.log(mul);//Output: 720

//Max
let max = num.reduce( (res,el) => (res > el)? res : el );
console.log(max);//Output: 6

//Min
let min = num.reduce( (res,el) => (res < el)? res : el );
console.log(min);//Output: 1

//concat array
const arrays = [[1, 2, 3], [4, 5], [6]];
const flattened = arrays.reduce((accumulator, currentValue) => {
  return accumulator.concat(currentValue);
}, );

console.log(flattened);//Output: [1, 2, 3, 4, 5, 6 ]
```

### 16. forEach()

📖 Executes a function for each array element.

```js
//Case:1
const arr = [1,2,3,4,5,6];
const print = function (el){
    console.log(el * 2);    //Output: 2, 4, 6, 8, 10, 12
    
};

arr.forEach(print);
```

```js
//Case:2
const arr2 = [1,2,3,4,5,6];
arr.forEach( (el) =>{
    console.log(`This is forEach ${el}`);   //Output: This is forEach1 * 6
    
});
```

```js
//forEach in array object
const data = [
    {
        name : "Ritesh",
        marks : 90
    },
    {
        name : "satyam",
        marks : 95
    },
    {
        name : "rajan",
        marks : 80
    }
];

data.forEach( (stu) =>{
    //console.log(stu.marks);   //Output: 90 95 80
    console.log(stu.name);  //Output: Ritesh satyam rajan
});
```

### 17. find()

📖 Returns the **first element** that matches the condition.

```js
const people = [
    { name: 'John', age: 25 },
    { name: 'Jane', age: 30 },
    { name: 'Alice', age: 20 },
    { name: 'Bob', age: 35 }
  ];
  
  const result = people.find(person => person.name.startsWith('J'));
  console.log(result);  // Output: { name: 'John', age: 25 }
```

### 18. includes(`element`, `fromIndex`)

📖 Checks if an array **contains a certain element**.

```js
// if found return true, else return false.
let cars = ['audi','bmw','mahindra','tata'];

let car = cars.includes('tata');

console.log(car);//Output: true
```

```js
let arr = [1, 2, 3];
console.log(arr.includes(2)); // true
console.log(arr.includes(5)); // false
```

### 19. indexOf()

📖 Returns the **first index** of an element (or -1 if not found).

```js
// if found return index number, else return -1.
let cars = ['audi','bmw','mahindra','tata'];

let car = cars.indexOf('tata');

console.log(car);//Output: 3
```

### 20. flat(`depth`)

📖 Creates a **new array** by **flattening nested arrays** up to a **specified depth**.

```js
let arr = [1, 2, [3, 4, [5, 6],],];
let flatArr = arr.flat();
console.log(flatArr);   // Output: [1, 2, 3, 4, [ 5, 6]] 

let numbers = [1, 2, [3, 4, [5, 6, [7, 8]]]];   //infinity
let res = numbers.flat(3);
console.log(res);   // Output: [1, 2, 3, 4, 5, 6, 7, 8]
```

### 21. flatMap(callback)

📖 Maps each element using a mapping function, then flattens the result into a new array.

### 22. some()

📖 Checks if **at least one element** satisfies the condition.

```js
let arr2 = [1,20,30,29,39,40];

let below2 = arr.some( (el) => {
     return el < 30;
});

console.log(below2);    //true
```

### 23. every()

📖 Checks if **all elements** satisfy the condition.

```js
//Case:1
let num = [2,4,6];

let checkNum = num.every( (el) =>{
    return el % 2 == 0;
});

console.log(checkNum);  //true
```

```js
//Case:2
let arr = [1,20,30,29,39,40];
let below = arr.every( (el) => {
    return el < 30;
});

console.log(below);     //false
```

### 24. entries()

Returns a **new Array Iterator object** that **contains** the **key/value pairs** for each index in the array.

```js
const obj = { a: 1, b: 2, c: 3 };
const entrie = Object.entries(obj);
console.log(entrie);    // Output: [[ 'a', 1 ], [ 'b', 2 ], [ 'c', 3 ]]

const arr = [1, 2, 3];
const entries = arr.entries();
console.log(entries.next().value); // Output: [0, 1]
console.log(entries.next().value); // Output: [1, 2]
console.log(entries.next().value); // Output: [2, 3]
```

### 25. keys()

Returns a **new Array Iterator object** that **contains** the **keys** for **each index** in the array.

### 27. values()

Returns a **new Array Iterator object** that **contains** the **values** for **each index** in the array.

### 28. toString()

Converts an array into a comma-separated string.

```js
const arr = ["Hello", 100, true];
console.log(arr.toString());  
// Output: "Hello,100,true"
```

---



## 🔧 Basic Manipulation Methods (15+)
- `push()`, `pop()`

- shift(), unshift()

- splice(), slice()

- concat()

- copyWithin()

- fill()

- flat(), flatMap()

## 🔍 Search and Find Methods (10+)
- indexOf(), lastIndexOf()

- find(), findIndex()

- findLast(), findLastIndex()

- includes()

- some(), every()

## 🔄 Iteration Methods (10+)
- forEach()

- map()

- filter()

- reduce(), reduceRight()

- entries(), keys(), values()

## 📊 Utility Methods (10+)
- join()

- reverse()

- sort()

- toString()

- toLocaleString()

- isArray()

- from(), of()

## 📏 Size and Structure Methods (5+)
- length (property)

- at()

- Array.isArray()

---

## 📌 JavaScript Array Methods List (Latest ES Spec ke hisaab se)
### 🔹 Adding / Removing Elements

- `push()` – Add at end

- `pop()` – Remove from end

- `shift()` – Remove from start

- `unshift()` – Add at start

- `splice()` – Add/Remove from specific index

- `fill()` – Fill array with static value

- `copyWithin()` – Copy part of array to another position

### 🔹 Searching / Finding

- `indexOf()` – First index of element

- `lastIndexOf()` – Last index of element

- `includes()` – Check if element exists

- `find()` – First element that matches condition

- `findIndex()` – Index of first element that matches

- `findLast()` (ES2023) – Last element that matches

- `findLastIndex()` (ES2023) – Index of last matching element

### 🔹 Iteration / Transformation

- `forEach()` – Run function for each element

- `map()` – Transform each element → new array

- `filter()` – Elements that pass condition

- `reduce()` – Reduce to single value

- `reduceRight()` – Reduce from right to left

- `flat()` – Flatten nested arrays

- `flatMap()` – Map + Flatten

### 🔹 Sorting

- `sort()` – Sort array

- `reverse()` – Reverse order

- `toSorted()` (ES2023, non-mutating sort)

- `toReversed()` (ES2023, non-mutating reverse)

### 🔹 Joining / Converting

- `join()` – Convert array to string

- `toString()` – Array → string

- `toLocaleString()` – Localized string

### 🔹 Slicing / Copying

- `slice()` – Extract part of array

- `concat()` – Merge arrays

### 🔹 New Immutable Methods (ES2023 / ES2024)

- `with()` – Replace element at index without mutating

- `toSpliced()` – Immutable version of splice