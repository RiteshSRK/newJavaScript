### 🔹 1. What is Lexical Scoping?

**Definition:**
- Lexical scoping means that a function can access variables defined in its own scope, outer (parent) scopes, and global scope, but not in inner scopes.

- It depends on where the function is written (its position in code), not where it is called.

```js
function outer() {
  let name = "Ritesh";

  function inner() {
    console.log(name); // inner can access "name" from outer
  }

  inner();
}

outer(); // Output: Ritesh
```