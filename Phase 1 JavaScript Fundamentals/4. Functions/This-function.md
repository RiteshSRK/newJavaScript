## Arrow vs regular function: `this` context

### 1. `this` Keyword

- `this` is a keyword that **refers to the current object or execution context**. Its value depends on **how a function is invoked** (runtime binding), not how it is defined.

```js
let stu = {
    firstName: "Ritesh",
    lastName: "Gupta",
    eng: 99,
    hin: 85,
    math: 100,
    getAvg: function(){
        let avg = (this.eng + this.hin + this.math) / 3;
        console.log(avg);
    }
}

console.log(stu.getAvg());  //Output: 94.66666666666667
console.log(stu.eng);       //Output: 99
```

### 1. Regular Functions (`function`)

- It depends on **how** the function is called (runtime binding).

- the object that invokes the function.

#### Example 1: As an object method

```js
const user = {
  name: "Ritesh",
  greet: function() {
    console.log("Hello, " + this.name);
  }
};
user.greet(); // Hello, Ritesh
```
👉 Here, `this` refers to the object `user`.

#### Example 2: As a standalone function

```js
function show() {
  console.log(this);
}
show(); 
// In strict mode: undefined
// In non-strict mode: window (global object in browser)
```
👉 In regular functions, `this` changes depending on the **caller**.

### 2. Arrow Functions (`=>`)

- Arrow functions **do not have their own** `this`.

- Instead, they **inherit `this` from the parent call / Lexical scope** (the place where they are defined).

#### Example 2: Lexical `this` in practice

```js
const user = {
  name: "Ritesh",
  greet: function() {
    const inner = () => {
      console.log("Hello, " + this.name);
    };
    inner();
  }
};
user.greet(); // Hello, Ritesh
```

---

```js
const student = {
    name : "aman",
    marks : 95,
    prop : this,    // global scope
    
    getName : function(){
        console.log(this);  // student object
        return this.name;
    },

    
    getMarks : () => {
        console.log(this);  // parent scope -> window
        return this.marks;
    },

    getInfo1 : function() {
        setTimeout( () => {
        console.log(this);  // student
        },2000);
    },

    getInfo2 : function() {
        setTimeout(function() {
        console.log(this);  // window
        },2000);
    },
};

//console.log(student);
//console.log(student.getName());   // Ritesh
//console.log(student.getMarks());  // undefined (G.S)
//console.log(student.getInfo1());  // student object
//console.log(student.getInfo2());
```

---

### 1. Global Scope me (`this`)
✅ Browser

```js
console.log(this); 
// 👉 Window object
```
👉 Browser me global scope ka this hamesha window hota hai.


✅ Node.js

```js
console.log(this); 
// 👉 {}
```

👉 Node.js me global scope ka this ek empty object {} hota hai, na ki global.