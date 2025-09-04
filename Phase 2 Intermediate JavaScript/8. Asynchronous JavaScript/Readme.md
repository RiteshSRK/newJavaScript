## Callback Functions in JavaScript

> A **callback function** is a function that is **passed as an argument** to another function and is **executed later**, usually ***after some operation is completed***.

```js
//  Basic Example
function greet(name, callback) {
  console.log("Hello, " + name);
  callback(); // call back later
}

function sayBye() {
  console.log("Goodbye!");
}

greet("Ritesh", sayBye);
```

```bash
Hello, Ritesh
Goodbye!
```

### Why Use Callbacks?

- To **control the order** of execution.

- To **handle asynchronous tasks** (e.g., fetching data, file loading, API calls).

### Async Example with setTimeout

```js
function fetchData(callback) {
  console.log("Fetching data...");

  setTimeout(() => {
    console.log("Data received!");
    callback(); // executed after data is ready
  }, 2000);
}

function processData() {
  console.log("Processing data...");
}

fetchData(processData);
```

```kotlin
Fetching data...
(2s delay)
Data received!
Processing data...
```

---

## Call Stack

#### Q. What is the `Call Stack` in JavaScript ?

The **call stack** is a **crucial concept** in **JavaScript’s runtime environment, representing** the **mechanism** by which the **JavaScript engine keeps track of function calls in a program**. It **operates** as a `Last In, First Out` (`LIFO`) **Data Structure**, meaning that the **last function called** is the **first one** to be **resolved**.

```js
// call stack: a function call another function

function hello(){
    console.log("and this is hello func");// 3rd call
    
    console.log("hello jii"); // 4th call
    
};

function demo(){
    console.log("inside demo function "); //2nd call
    
    hello();
};

console.log("calling demo func "); // 1st call

console.log(demo());

//Output:

//calling demo func 
//inside demo function 
//and this is hello func
//hello jii
```

### Visualizing Call Stack

```js
function one(){
    return 1;
};

function two(){
    return one() + one();
};

function three(){
    let ans = two() + one();
    console.log(ans);   //Output: 3
    
};

three()
```

```js
//Example of Asynchronous Behavior
console.log("Start");

setTimeout(() => {
    console.log("Timeout");
}, 1000);

console.log("End");

//Output:
//Start
//End
//Timeout
```

---

## Callback Hell

```js
let h1 = document.querySelector('h1');

function changeColor(color,delay,nextColorChange){
    setTimeout( () => {
        h1.style.color = color;
        if(nextColorChange) nextColorChange();
    },delay)

}

changeColor("red",1000, () => {
    changeColor("green",1000, () => {
        changeColor("yellow",1000, () => {
            changeColor("orange",1000, () => {
                changeColor("blue",1000, () => {
                })
            })
        })
    })
});
```

```js
function savetoDb(data,success,failure){
    let internetSpeed = Math.floor(Math.random() * 10) + 1;
    if(internetSpeed > 4){
        success();
        
    }else{
        failure();
        
    }
}

savetoDb("apnacollege",
    () => {
        console.log("success: your data was saved");
        savetoDb("hello word",
            () => {
                console.log("success2: data2 saved");
                savetoDb("Ritesh",
                    () => {
                        console.log("success3: data3 saved");
                        
                    },
                    () => {
                        console.log("failure3: data3 not save");
                        
                    }
                )
            },
            () => {
                console.log("failure2: data2 not save");
                
            }
        )

        
    },
    () => {
        console.log("failure: weak connection. data not saved");
    }
);
```