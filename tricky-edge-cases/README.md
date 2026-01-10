# ⚠️ Tricky JavaScript Edge Cases – Output-Based Questions

This section covers **subtle JavaScript behaviors** that often surprise even
experienced developers.

---

## 📌 Question 1: `typeof null`

```js
console.log(typeof null);
```
<details> <summary><b>✅ Output</b></summary>
object
</details> <details> <summary><b>🧠 Explanation</b></summary>
- This is a historical bug in JavaScript

- `null` is a primitive, but typeof null returns "object"

</details>

## 📌 Question 2: `NaN` Comparisons
```js
console.log(NaN === NaN);
console.log(Object.is(NaN, NaN));
```
<details> <summary><b>✅ Output</b></summary>
false
true

</details> <details> <summary><b>🧠 Explanation</b></summary>

- `NaN` is not equal to itself

- `Object.is` correctly identifies NaN

</details>

## 📌 Question 3: Array Length Manipulation
```js
const arr = [1, 2, 3];
arr.length = 1;

console.log(arr);
```
<details> <summary><b>✅ Output</b></summary>

[1]

</details> <details> <summary><b>🧠 Explanation</b></summary>
- Reducing length truncates the array

- Elements beyond the new length are removed

</details>

## 📌 Question 4: delete vs undefined
```js
const obj = { a: 1 };
obj.a = undefined;

console.log("a" in obj, obj.hasOwnProperty("a"));
```
<details> <summary><b>✅ Output</b></summary>
true true

</details> <details> <summary><b>🧠 Explanation</b></summary>

- Property still exists on the object

- Only the value is set to undefined

</details>

## 📌 Question 5: `delete` on Array Element
```js
const arr = [1, 2, 3];
delete arr[1];

console.log(arr);
console.log(arr.length);
```
<details> <summary><b>✅ Output</b></summary>
[1, <empty>, 3]
3

</details> <details> <summary><b>🧠 Explanation</b></summary>

- `delete` removes the element but not the index

- Creates a sparse array

- `length` remains unchanged

</details>

## 📌 Question 6: Floating Point Precision
```js
console.log(0.1 + 0.2 === 0.3);
```
<details> <summary><b>✅ Output</b></summary>
false

</details> <details> <summary><b>🧠 Explanation</b></summary>

- JavaScript uses IEEE-754 floating-point arithmetic

- Some decimals cannot be represented precisely

</details>

## 📌 Question 7: Object Key Coercion

```js
const obj = {};
obj[1] = "one";
obj["1"] = "string one";

console.log(obj);
```
<details> <summary><b>✅ Output</b></summary>

{ "1": "string one" }

</details> <details> <summary><b>🧠 Explanation</b></summary>
- Object keys are coerced to strings

- Both keys become `"1"`

- Later assignment overrides earlier one

</details>

## 📌 Question 8: arguments vs Arrow Function
```js
const fn = () => {
  console.log(arguments);
};

fn(1, 2, 3);
```
<details> <summary><b>✅ Output</b></summary>
ReferenceError: arguments is not defined

</details> <details> <summary><b>🧠 Explanation</b></summary>

- Arrow functions do not have their own arguments

- They inherit from the enclosing scope

</details>

## ⭐ Interview Reality Check

- These questions test language mastery, not memorization.