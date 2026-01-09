# ⬆️ Hoisting – Output-Based JavaScript Questions

Hoisting is a **core JavaScript concept** that is frequently tested in
**mid to senior-level interviews**.

---

## 📌 Question 1: `var` Hoisting

```js
console.log(a);
var a = 10;
```

<details> <summary><b>✅ Output</b></summary>
undefined
</details> <details> <summary><b>🧠 Explanation</b></summary>

Variable declarations using var are hoisted

Initialization is not hoisted

JavaScript treats it as:
```js
var a;
console.log(a);
a = 10;
```
</details>

## 📌 Question 2: let Hoisting (Temporal Dead Zone)

```js
console.log(a);
let a = 10;
```
<details> <summary><b>✅ Output</b></summary>
```
ReferenceError: Cannot access 'a' before initialization
```
</details> <details> <summary><b>🧠 Explanation</b></summary>

let is hoisted but placed in the Temporal Dead Zone (TDZ)

Accessing it before initialization throws an error

</details>
