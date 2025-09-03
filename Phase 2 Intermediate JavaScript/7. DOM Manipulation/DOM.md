# DOM Manipulation in JavaScript

## 🔹 What is DOM?

- **DOM (Document Object Model)** → A tree-like structure that represents an HTML document.

- Each element in HTML becomes a **node (object)** in this tree.

- Using DOM, we can **access**, **manipulate** (`read`, `update`, `add`, `delete`) HTML elements and their styles.

## 2. Selecting Elements

We need selectors to target HTML elements before manipulating them.

- `getElementById("id")` → returns single element by ID

- `getElementsByClassName("class")` → returns HTMLCollection

- `getElementsByTagName("tag")` → returns HTMLCollection

- `querySelector("selector")` → returns first matching element

- `querySelectorAll("selector")` → returns NodeList (all matches)



```js
document.querySelector('p');			//Selects first p element
document.querySelector('#myId'); 		//Selects first element with id = myId
document.querySelector('.myClass'); 	//Selects first element with class = myClass

document.querySelectorAll("p");		// Selects all p elements
```

<br>

| Method                            | Description                                  | Example                                   |
| --------------------------------- | -------------------------------------------- | ----------------------------------------- |
| `getElementById("id")`            | Selects element by ID                        | `document.getElementById("title")`        |
| `getElementsByClassName("class")` | Selects elements by class (HTMLCollection)   | `document.getElementsByClassName("item")` |
| `getElementsByTagName("tag")`     | Selects elements by tag name                 | `document.getElementsByTagName("p")`      |
| `querySelector("selector")`       | Selects **first** matching element           | `document.querySelector(".item")`         |
| `querySelectorAll("selector")`    | Selects **all** matching elements (NodeList) | `document.querySelectorAll(".item")`      |


⚡ Allows us **to use any CSS selector**

## 3. Changing Content

`element.textContent` → changes plain text (includes hidden text)

`element.innerText` → changes visible text only

`element.innerHTML` → changes text + allows HTML injection

## Manipulating Attributes:

```css
obj.getAttribute("attribute");  
obj.setAttribute("attribute","value");
```

```js
let link = document.querySelector("a");
link.getAttribute("href"); 
link.setAttribute("href", "https://google.com");
link.removeAttribute("target");
```

## Manipulating Style:

We can directly modify CSS properties:  `obj.style`

```js
let box = document.querySelector(".box");
box.style.backgroundColor = "blue";
box.style.fontSize = "20px";
```

## Working with Classes

- `classList.add("className")` → add a class

- `classList.remove("className")` → remove a class

- `classList.contains("className")` →	to check if class exists

- `classList.toggle("className")` → add if missing, remove if exists

```css
box.classList.add("active");
box.classList.toggle("hidden");
```

## Navigation:

- `parentElement`
- `children`
- `previousElementSibling` / `nextElementSibling`
- `childNodes` → Returns a NodeList of all child nodes 
- `firstElementChild` / `lastElementChild`

<br><br>

| Property                 | Description                | Example                     |
| ------------------------ | -------------------------- | --------------------------- |
| `parentNode`             | Access parent element      | `item.parentNode`           |
| `children`               | HTMLCollection of children | `ul.children`               |
| `firstElementChild`      | First child element        | `ul.firstElementChild`      |
| `lastElementChild`       | Last child element         | `ul.lastElementChild`       |
| `nextElementSibling`     | Next element               | `li.nextElementSibling`     |
| `previousElementSibling` | Previous element           | `li.previousElementSibling` |

<br>

---

## Creating and Adding Elements

### Create an element:
```js
const newEl = document.createElement('div');
```

- `appendChild(element)` → Only accepts **Node objects** (like `<p>`). Always adds at the **end** of parent.

- `append(element or text)` → Can accept **Node** + **text together**. Adds at the **end**.

- `prepend(element)` → Inserts the element at the **beginning** of the parent.

## `insertAdjacentElement(where, element)`

| Position          | Meaning                                              |
| ----------------- | ---------------------------------------------------- |
| **`beforebegin`** | Insert before the target element (as sibling).       |
| **`afterbegin`**  | Insert as the **first child** of the target element. |
| **`beforeend`**   | Insert as the **last child** of the target element.  |
| **`afterend`**    | Insert after the target element (as sibling).        |

## Removing Elements
- `remove( element )`		prefrance ise dena hai  
- `removeChild( element )`

```js
let item = document.querySelector(".list-item");
item.remove(); // modern way
```

---

## what is nodeList in javascript?
> A NodeList in JavaScript is a collection of DOM (Document Object Model) nodes, which can include elements, text nodes, comments, etc. It is often returned by DOM methods like `querySelectorAll()` or `childNodes`.

### Array-Like Structure:
> A NodeList is similar to an array, but it is not a true array. It has a length property and **allows access to its items using an index** (e.g., `nodeList[0]`).

### Iteration:
> You can iterate over a NodeList using:

- A for loop.

- The `forEach()` method (available in modern browsers).

- Converting it to an array using `Array.from()` or the spread operator (`[...nodeList]`).

```js
const classList
= document.getElementsByClassName('list—item')
```

```js
//  convert nodeList in to array
Array.from(classList)

const myConvertedArray = Array.from(classList)
```
---
### iterate childs nodes:
```html
    <ul>
        <li>one</li>
        <li>two</li>
        <li>three</li>
    </ul>
```

```js
    const ul = document.querySelector('ul');
        
    for(i=0; i<=ul.children.length; i++){
        console.log(ul.children[i].innerText)
    }
```

```js
    const app = ul.children[2].append(' Apple');
    //  three Apple
```

```js
    ul.children[2].append(' Apple');
    ul.children[2].append(' dacket');
    //  three Apple dacket
```

```js
    const app = ul.children[2].innerText;
    console.log(app)    //  three
```
---

> `createTextNode()` DOM API ka method hai jo sirf text node create karta hai (koi HTML tag nahi). Fir aap is text node ko kisi element ke andar append karte ho.

```html
<!DOCTYPE html>
<html>
<head>
    <title>createTextNode Example</title>
</head>
<body>
    <div id="container"></div>

    <script>
        // 1. Text Node create karna
        const textNode = document.createTextNode("Hello, this is a text created using createTextNode!");

        // 2. Target element select karna
        const container = document.getElementById("container");

        // 3. Text Node ko element ke andar append karna
        container.appendChild(textNode);
    </script>
</body>
</html>
```

```html
<body>
    <div id="root"></div>

    <script>
        // <p>Hello World</p> dynamically create karna hai

        // 1. p element create karo
        const para = document.createElement("p");

        // 2. Text node create karo
        const text = document.createTextNode("Hello World");

        // 3. Text node ko p ke andar append karo
        para.appendChild(text);

        // 4. p ko root div ke andar append karo
        document.getElementById("root").appendChild(para);
    </script>
</body>
```

---

### ⚡ Common Interview Questions

#### Q1. What is the difference between `innerText`, `textContent`, and `innerHTML`?

- `innerText` → visible text only.

- `textContent` → all text including hidden.

- `innerHTM`L → text + HTML tags.

#### Q2. What is the difference between `querySelector` and `getElementById`?

- `getElementById` → only works with IDs (faster).

- `querySelector` → works with CSS selectors (more flexible).

#### Q3. How can we add elements dynamically to the DOM?
👉 Using `document.createElement()` + `appendChild()`

#### Q4. What is the difference between `appendChild` and `innerHTML` for adding elements?

- `appendChild` → safer, prevents XSS, handles real nodes.

- `innerHTML` → faster but risky, can overwrite existing content.

#### Q5. How do you remove a DOM element?
👉 Using `element.remove()` or `parent.removeChild(element)`.
