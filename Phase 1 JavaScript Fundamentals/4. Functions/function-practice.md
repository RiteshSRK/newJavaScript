## Interview Example

### Q: What is the output?

```js
function Person() {
  this.age = 0;

  setInterval(() => {
    this.age++;
    console.log(this.age);
  }, 1000);
}

new Person();
```

Answer:     
👉 Yaha `this` arrow function ke wajah se parent scope (`Person` object) se bind hoga.
So age increment hoga:

```bash
1, 2, 3, 4...
```

---

Agar normal function use karte:

```js
setInterval(function() {
  this.age++;
  console.log(this.age);
}, 1000);
```

Toh `this` global ho jata, aur `NaN` aata.