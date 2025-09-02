# JavaScript String Methods

### 1. trim()

📖 Removes whitespace from both ends.

```js
let msg = "     hello    ";
let msg2 = msg.trim();
console.log(msg2);
//Output: hello

// Doesn’t remove middle spaces.
let str = "he    llo";
let str2 = str.trim();
console.log(str2);
//Output: he    llo
```

### trimStart() / trimEnd()

📖 Removes whitespace only from start/end.

```js
console.log("  hello".trimStart()); // "hello"
console.log("hello  ".trimEnd());   // "hello"
```

### 3. toLowerCase()

📖 Converts string to lowercase.

```js
let str = "Ritesh Gupta";

let str2 = str.toLowerCase();
console.log(str2);
//Output: ritesh gupta
```

### 4. toUpperCase()

📖 Converts string to uppercase.

```js
let str = "Ritesh Gupta";

let str2 = str.toUpperCase();
console.log(str2);
//Output: RITESH GUPTA
```

## Method Chaining
Using one method after another. Order of execution will be left to right.

`str.toUpperCase( ).trim( )`

### 5. slice(`start`, `end`)

📖 Extracts substring (non-mutating).

```js
let arr = ["apple","ball","cat"];

let arr2 = arr.slice(1);
console.log(arr2); //Output: ["ball","cat"]
```

```js
let string = "IloveProgrammingLanguage";

let string2 = string.slice(5,16);
console.log(string2);//Output: Programming
```

```js
let name ="apnaCollege";

let res = name.slice(4,9);
console.log(res);//Output: Colle
```

### 6. repeat(`n`)

📖 Repeats string `n` times.

```js
//repeat    Returns a string with the number of copies of a string

let str = "I love coding";

let res = str.repeat(3);
console.log(res); //Output: I love codingI love codingI love coding
```

### 7. replace(`search`, `replaceWith`)

📖 Replaces first occurrence of substring.

```js
let str = "I love coding";

let res = str.replace("love","do");
console.log(res);//Output: I do coding
```

### 7. replaceAll(search, replaceWith)

📖 Replaces all occurrences.

```js
let str = "a a a";
console.log(str.replaceAll("a", "b")); // b b b
```

### 8. charAt(index)

📖 Returns character at given index.

```js
// yah method string ka character return karta hai

let str = "Ritesh Gupta";
let res = str.charAt(1);

console.log(res);//Output: i
```

```js
let str = "JavaScript";
console.log(str.charAt(4)); // S
```

### 9. concat()

📖 Joins multiple strings.

```js
let firstName = "Ritesh";
let lastName = "Gupta";

let fullName = firstName.concat(" ",lastName);

console.log(fullName);//Output: Ritesh Gupta
```

### 10. split(separator)

📖 Splits string into array.

```js
// Split String ko array bana deta hai
let geeks = 'stands-for-GeeksforGeeks';

// Split string on '-'. 
console.log(geeks.split('-'))
//Output: [ 'stands', 'for', 'GeeksforGeeks' ]
```

```js
let str = "I hello how are you";
let res = str.split(" ");

console.log(res);
//Output: [ 'I', 'hello', 'how', 'are', 'you' ]
```

### 11. charCodeAt(index)

📖 Returns UTF-16 code of character.

```js
console.log("A".charCodeAt(0)); // 65
```
⚡ Interview Note: Useful in ASCII/Unicode operations.

### 12. includes(substring)

📖 Checks if string contains given substring.

```js
let str = "JavaScript";
console.log(str.includes("Script")); // true
```
⚡ Interview Note: Case-sensitive. Cleaner than indexOf().

### 13. indexOf(substring)

📖 Returns first index of substring.

```js
let str = "Hello World";
console.log(str.indexOf("o")); // 4
```
⚡ Interview Note: Returns -1 if not found.

### 14. startsWith(substring) / endsWith(substring)

```js
//  Checks if string starts with given substring.
console.log("JavaScript".startsWith("Java")); // true
```

```js
//  Checks if string ends with given substring.
console.log("JavaScript".endsWith("Script")); // true
```
⚡ Interview Note: Case-sensitive.

### 15. padStart(length, padString)

📖 Pads string from start until length.

```js
console.log("5".padStart(3, "0")); // 005
```

### 16. padEnd(length, padString)

📖 Pads string from end until length.

```js
console.log("5".padEnd(3, "0")); // 500
```


---


## 📌 JavaScript String Methods
### 🔹 Character Access

- `charAt(index)` → Returns character at given index
`"Hello".charAt(1) → "e"`

- `charCodeAt(index)` → Unicode of char
`"A".charCodeAt(0) → 65`

- `at(index)` (ES2022) → Modern way to access character (supports negative index)
`"Hello".at(-1) → "o"`

### 🔹 Searching

- `indexOf(substring)` → First occurrence index

- `lastIndexOf(substring)` → Last occurrence index

- `includes(substring)` → Boolean check

- `startsWith(substring)` → True if string starts with substring

- `endsWith(substring)` → True if string ends with substring

### 🔹 Extracting

- `slice(start, end)` → Extract substring

- `substring(start, end)` → Similar to slice but no negative index

- `substr(start, length)` (deprecated, avoid in new code)

### 🔹 Modifying / Transforming

- `toUpperCase()` → Convert to UPPERCASE

- `toLowerCase()` → Convert to lowercase

- `trim()` → Remove spaces from both ends

- `trimStart()` / `trimLeft()` → Remove leading spaces

- `trimEnd()` / `trimRight()` → Remove trailing spaces

- `repeat(count)` → Repeat string

- `padStart(length, padString)` → Add padding at start

- `padEnd(length, padString)` → Add padding at end

- `replace(search, new)` → Replace first match

- `replaceAll(search, new)` (ES2021) → Replace all matches

### 🔹 Splitting / Joining

- `split(separator)` → Convert string into array

- `concat(str1, str2, …)` → Join strings

### 🔹 Pattern Matching (Regex support)

- `match(regex)` → Array of matches

- `matchAll(regex)` → Iterator of matches

- `search(regex)` → Index of match

- `replace(regex, new)` → Replace with regex

- `replaceAll(regex, new)` → Replace all regex matches

### 🔹 String Conversion

- `toString()` → Returns string itself

- `valueOf()` → Primitive value of string