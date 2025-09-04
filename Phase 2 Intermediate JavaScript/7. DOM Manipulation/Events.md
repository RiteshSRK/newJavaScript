# Event in Java Script
> Events are **actions** or **occurrences** that **happen in the browser**, which can be **detected** and **handled** using **event listeners**.

## Understanding Events
> Events can **occur** due to **user interactions** (like `clicks` and `key presses`), **browser actions** (like `loading a page`), or other **conditions** (like `timers`). Each event can **trigger** a **function**, known as an **event handler**.

## Event Handling

### 1. HTML Attribute Handlers (Inline Events)
```html
<button onclick="alert('Button clicked!')">Click Me</button>
```

### 2. DOM Property Method

```js
const btn = document.getElementById("myBtn");
btn.onclick = function() {
  alert("Button clicked!");
};
```
**⚠️ Limitation:** Only one handler can be assigned per event.

### 3. `addEventListener` (The modern, recommended approach)

```js
const btn = document.querySelector('button');

function handleClick() {
  console.log('Button clicked!');
}

btn.addEventListener('click', handleClick);
```

#### Advantages:

- Multiple listeners can be attached

- Supports removing event listeners (`removeEventListener`)

- More options available (capturing phase, passive events)

- Cleaner and modern approach

---

## Common Event Types
Here are some commonly used event types:

## Mouse Events:

#### ***click:*** Triggered when an element is clicked.

```js
let p = document.querySelector("p");

p.addEventListener("click", function() {
    console.log("para was clicked");
    
});
```

#### ***dblclick:***		Triggered on a double-click.

```js
let btnss = document.querySelectorAll("button");

for (btnn of btnss) {
    
    btnn.addEventListener("dblclick", luaph);
}

function luaph(){
    //alert("hello jii");
    console.log("hhaahah"); 
}
```

#### ***mouseover:***		Triggered when the mouse pointer is over an element.

```js
let box = document.querySelector(".box");
box.addEventListener("mouseover", function() {
    console.log("curser inside box");
    
});
```

#### ***mouseout:*** 		Triggered when the mouse pointer leaves an element.

```js
let box = document.querySelector(".box");
box.addEventListener("mouseout", function() {
    console.log("curser inside box");
    
});
```

## this in Event Listeners:
When `this` is used in a callback of event handler of something, it refers to that something.

## Redundancy :
iska matlab aisi chiz jisko humne baar baar likh rakha ho or as a programmer humko ek hi code ko baar2 likhane se bachna chahiye.

```js
let h1 = document.querySelector("h1");
let h3 = document.querySelector("h3");
let p = document.querySelector("p");
let btn = document.querySelector("button");

function msg(){
    console.dir(this.innerText);
    this.style.backgroundColor = "yellow";
}

h1.addEventListener("click", msg);
h3.addEventListener("click", msg);
p.addEventListener("click", msg);
btn.addEventListener("click", msg);
```
---

<br>

# 4. Event Object

📖 When an event occurs, the browser creates an event object containing details about the event:

## Common Event Object Properties & Methods

| Property / Method     | Description                                          |
| --------------------- | ---------------------------------------------------- |
| **type**              | The type of event.                                   |
| **target**            | The element that triggered the event.                |
| **preventDefault()**  | A method to prevent the default action of the event. |
| **stopPropagation()** | A method to stop the event from bubbling up the DOM. |

```js
let button = document.querySelector('button');

button.addEventListener('click', function(event) {
    
    console.log(event); // Event Object
    console.log(event.type); // "click"

    console.log(event.target); // The button element
    event.preventDefault(); // Prevents default action
});

```

### Keyboard Events

| Event        | Description                                  |
| ------------ | -------------------------------------------- |
| **keydown**  | When a key is pressed.                       |
| **keyup**    | When a key is released.                      |
| **keypress** | When a key is pressed down (**deprecated**). |

```js
let inp = document.querySelector('input');

inp.addEventListener('keyup', function(e){
    console.log("KeyCode =", e.code);
    console.log("Key =", e.key);
    
    console.log("KeyUp was pressed");
});
```

```js
let inp = document.querySelector('input');

inp.addEventListener('keyup', function(e){
    console.log("KeyCode =", e.code);
    if(e.code == 'ArrowUp'){
        console.log("Move to foreword");
    }else if(e.code == 'ArrowDown'){
        console.log("Move to backword");
    }else if(e.code == 'ArrowRight'){
        console.log("Move to Right");
    }else if(e.code == 'ArrowLeft'){
        console.log("Move to Left");
    }
});
```

## Form Events:
***submit:***		When a form is submitted.

## Preventing Default Actions
You can **prevent** the **default action** of an **event** (like form submission) using `event.preventDefault()`.

```js
let form = document.querySelector('form');

form.addEventListener('submit', function(e){
    e.preventDefault();
    console.log("Form was submited");
});
```

## Extracting Form Data
Extracting form data from the form

```js
let form = document.querySelector('form');

form.addEventListener('submit', function(e){
    e.preventDefault();

    //Case:1
    // let user = document.querySelector('#user');
    // let pass = document.querySelector('#pass');
    console.dir(this.elements)
    //Case:2
    let user = this.elements[0];
    let pass = this.elements[1];

    console.log(user.value);
    console.log(pass.value);

    alert(`Hi ${user.value} your password set to ${pass.value}`);
    
});
```

## More Events
### change event
> The **change** event **occurs** when the **value of** an **element** has **been changed** (***only works*** on `<input>`, `<textarea>`and `<select>` elements).

```js
let user = document.querySelector('#user');

    user.addEventListener('change', function(){
        console.log("input changed");
        console.log("fanal value:", user.value); 
});
```

### input event
The input event fires when the value of an `<input>` , `<select>` , or `<textarea>` element has been changed.

```js
let user = document.querySelector('#user');

user.addEventListener('input', function(){
  	console.log(user.value);
        
});
```

#### Input Text Area Task

```js
let user = document.querySelector('#user');

    user.addEventListener('input', function(){
        let p = document.querySelector('p');
        console.log(user.value);
        p.innerText = user.value;
        
});
```

### Event Bubbling
A method to stop the event from bubbling up the DOM.

```js
let div = document.querySelector('div');
let ul = document.querySelector('ul');
let lis = document.querySelectorAll('li');

div.addEventListener('click', function(){
    console.log("Hi I am div");
})

ul.addEventListener('click', function(e){
    e.stopPropagation();
    console.log("Hi I am ul");
})

for(li of lis){
    li.addEventListener('click', function(e){
        e.stopPropagation();
        console.log("Hi I am list");
    })  
}
```

---


## Propagation in JavaScript

> Event bubbling aur event capturing event propagation phases hain jo decide karte hain ki event DOM tree me kaise travel karega.

### ✅ Event Propagation in JavaScript

> Event propagate hone ke 3 phases hote hain:

- **Capturing Phase** (Top → Target)

- **Target Phase** (Actual element)

- **Bubbling Phase** (Target → Top)

## ✅ 1. Event Bubbling

- Event inner element se outer element tak propagate hota hai.

- Default behavior bubbling hota hai.

Example:

```html
<div id="parent" style="padding:20px; background:#ddd;">
  Parent
  <button id="child">Child Button</button>
</div>

<script>
document.getElementById("parent").addEventListener("click", () => {
    alert("Parent Clicked");
});

document.getElementById("child").addEventListener("click", () => {
    alert("Child Clicked");
});
</script>
```

#### Output:

- Agar child button click karte ho → pehle `"Child Clicked"` fir `"Parent Clicked"`.

- Kyunki event bubbling phase me parent tak gaya.

---

## ✅ 2. Event Capturing (Trickling)

Event outer element se inner element tak travel karta hai.

Isko enable karne ke liye `addEventListener` ka 3rd argument `true` set karte hain.

Example:

```html
<script>
document.getElementById("parent").addEventListener("click", () => {
    alert("Parent Capturing");
}, true); // capturing mode

document.getElementById("child").addEventListener("click", () => {
    alert("Child Clicked");
});
</script>
```

#### Output:

- Click on child → `"Parent Capturing"` pehle aayega, fir `"Child Clicked"`.

---

### ✅ How to stop propagation?

`event.stopPropagation()` → Event ko propagate hone se rokta hai.

Example:

```js
document.getElementById("child").addEventListener("click", (e) => {
    e.stopPropagation();
    alert("Child Only");
});
```

## ✅ 3. Capture vs Bubble in addEventListener

`addEventListener("click", handler, true)` → Capturing phase

`addEventListener("click", handler, false)` (default) → Bubbling phase.

<br>
<br>

---

# Forms Handling in JavaScript — Interview Notes

## Forms in JavaScript

- A form is used to collect user input (`<form>`, `<input>`, `<textarea>`, `<select>`, etc.).

- JavaScript allows us to **handle submissions**, **validate data**, and **send** it to **backend**.

👉 Interview Line: “Forms use to collect data from users, and helps control how this data is submitted and processed.

## Modern Way — `FormData`

`FormData` automatically collects key-value pairs from a form.

```js
form.addEventListener("submit", (e) => {
  e.preventDefault();

  const formData = new FormData(form);

  // Get values
  console.log(formData.get("name"));
  console.log(formData.get("email"));

  // Loop through all fields
  for (let [key, value] of formData.entries()) {
    console.log(key, ":", value);
  }
});
```

### 👉 Benefits of FormData:

- Easy handling of large forms.

- Works with file uploads.

- Directly usable with `fetch()` for **AJAX**.

## Sending Form Data with Fetch API

```js
form.addEventListener("submit", async (e) => {
  e.preventDefault();

  const formData = new FormData(form);

  let response = await fetch("/submit", {
    method: "POST",
    body: formData, // directly send FormData
  });

  let result = await response.json();
  console.log("Server Response:", result);
});
```

## Validating Form Data

```js
form.addEventListener("submit", (e) => {
  e.preventDefault();

  const name = form.querySelector("#name").value;
  const email = form.querySelector("#email").value;

  if (!name || !email) {
    alert("All fields are required!");
    return;
  }

  console.log("Form is valid!");
});
```

## Example: Full Form Handling

```js
<form id="myForm">
  <input type="text" name="name" placeholder="Enter name" required />
  <input type="email" name="email" placeholder="Enter email" required />
  <button type="submit">Submit</button>
</form>

<script>
  const form = document.querySelector("#myForm");

  form.addEventListener("submit", (e) => {
    e.preventDefault(); // stop refresh

    const formData = new FormData(form);

    // Validation
    if (!formData.get("name") || !formData.get("email")) {
      alert("Please fill all fields");
      return;
    }

    // Log all fields
    for (let [key, value] of formData.entries()) {
      console.log(key + ": " + value);
    }

    // Send data to server
    fetch("/submit", {
      method: "POST",
      body: formData,
    })
      .then((res) => res.json())
      .then((data) => console.log("Server says:", data));
  });
</script>
```