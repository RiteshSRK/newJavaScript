## Promises in JavaScript

> A Promise in JavaScript is an object that represents the eventual **completion** (success) or **failure** of an asynchronous operation.

> Promises help us avoid **callback hell** and write cleaner asynchronous code.

### 🔹 Promise States

A Promise can be in 3 states:

- **Pending** → Initial state, operation not completed yet.

- **Fulfilled** → Operation completed successfully → returns a value.

- **Rejected** → Operation failed → returns an error.

### 🛠 Creating a Promise

```js
let promise = new Promise((resolve, reject) => {
  let success = true;

  if (success) {
    resolve("✅ Operation successful!");
  } else {
    reject("❌ Operation failed!");
  }
});

console.log(promise)
```

## Consuming a Promise
- `.then()` → Runs when promise is resolved (success).

- `.catch()` → Runs when promise is rejected (**Handles error**).

- `.finally()` → Runs always (success or failure).

```js
promise
  .then(result => {
    console.log("Then:", result); 
  })
  .catch(error => {
    console.log("Catch:", error);
  })
  .finally(() => {
    console.log("Finally: Always runs");
  });
```

#### 👉 Output (if `success = true`):

```bash
Then: ✅ Operation successful!
Finally: Always runs
```

#### 👉 Output (if `success = false`):

```bash
Catch: ❌ Operation failed!
Finally: Always runs
```

### Real Example (Fetching Data)

```js
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      let serverData = { user: "Ritesh", age: 25 };

      if (serverData) {
        resolve(serverData);
      } else {
        reject("No data found!");
      }
    }, 2000);
  });
}

fetchData()
  .then(data => console.log("Data received:", data))
  .catch(err => console.log("Error:", err))
  .finally(() => console.log("Fetch attempt complete."));
```

---

### Promises Example ( Case: 2 )

```js
function conectToDB(data){
    return new Promise((resolve, reject) => {
        let internetSpeed = Math.floor(Math.random() * 10) + 1;
        if(internetSpeed > 4){
            resolve("success : Data was saved");
        }else{
            reject("Failed : Weak Connection");
        }
    });
}

console.log(conectToDB("apna college"));
```

#### Promises ( `Then()` & `Catch()` )

```js
function conectToDB(data){
    return new Promise((resolve, reject) => {
        let internetSpeed = Math.floor(Math.random() * 10) + 1;
        if(internetSpeed > 4){
            resolve("success : Data was saved");
        }else{
            reject("Failed : Weak Connection");
        }
    });
}

//promise variable me save karke

let request = conectToDB("apna college"); //request : promise object
request.then(() => {
    console.log("Promise resolve");
    console.log(request);
    
})
.catch(() => {
    console.log("Promise Rejected");
    console.log(request);
});
```

---

## Promises chaining

- You can chain multiple `.then()` to avoid nested callbacks:

```js
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      let serverData = { user: "Ritesh", age: 25 };

      if (serverData) {
        resolve(serverData);
      } else {
        reject("No data found!");
      }
    }, 2000);
  });
}

fetchData()
  .then(data => {
    console.log("User:", data.user);
    return data.age;
  })
  .then(age => {
    console.log("Age:", age);
  })
  .catch(err => console.log(err))
  .finally(() => console.log("Done!"));
```

### Promises chaining ( Case: 2 )

```js
function conectToDB(data){
    return new Promise((resolve, reject) => {
        let internetSpeed = Math.floor(Math.random() * 10) + 1;
        if(internetSpeed > 4){
            resolve("success : Data was saved");
        }else{
            reject("Failed : Weak Connection");
        }
    });
}

// direct
conectToDB("apna college")
    .then((result) => {
        console.log("Data 1 : Saved\n", result);
        return conectToDB("hello world")
    })
    .then((result)=> {
        console.log("Data 2 : Saved\n", result);
        return conectToDB("Ritesh")
    })
    .then((result) => {
        console.log("Data 3 : Saved\n", result);
    })
    .catch((error) => {
        console.log("Promise was Rejected\n", error); 
    });
```

## ✅ Real Project Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Await Keyword Handling Rejections with Await
        </title>
</head>
<body>
    <h1>Apna college</h1>

    <script src="03_handllingRejection.js"></script>
</body>
</html>
```

```js
let h1 = document.querySelector('h1');

function changeColor(color,delay){
    return new Promise( (res,rej) => {
        setTimeout( () => {
            h1.style.color = color;
            res("color change");
        }, delay)
    });

}

changeColor("red", 1000)
.then( () => {
    console.log("red color was complete");
    return changeColor("green", 1000)
})
.then( () => {
    console.log("green color was complete");
    return changeColor("orange", 1000)
})
.then( () => {
    console.log("orange color was complete");
    return changeColor("blue", 1000)
})
.then( () => {
    console.log("blue color was complete");
})
```