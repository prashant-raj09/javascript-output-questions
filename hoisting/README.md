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

- Variable declarations using var are hoisted

- Initialization is not hoisted

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

ReferenceError: Cannot access 'a' before initialization

</details> <details> <summary><b>🧠 Explanation</b></summary>

- let is hoisted but placed in the Temporal Dead Zone (TDZ)

- Accessing it before initialization throws an error

</details>

## 📌 Question 3: Function Declaration Hoisting
```js
foo();

function foo() {
  console.log("Hello");
}
```
<details> <summary><b>✅ Output</b></summary>
Hello
</details> <details> <summary><b>🧠 Explanation</b></summary>

- Function declarations are fully hoisted

- Both function name and body are available before execution

</details>

## 📌 Question 4: Function Expression Hoisting

```js
foo();

var foo = function () {
  console.log("Hello");
};
```
<details> <summary><b>✅ Output</b></summary>
TypeError: foo is not a function

</details> <details> <summary><b>🧠 Explanation</b></summary>

- var foo is hoisted as undefined

- Function assignment happens later

- Calling undefined() causes a TypeError

</details>

## 📌 Question 5: Arrow Function Hoisting
```js
bar();

const bar = () => {
  console.log("Hello");
};
```
<details> <summary><b>✅ Output</b></summary>
ReferenceError: Cannot access 'bar' before initialization

</details> <details> <summary><b>🧠 Explanation</b></summary>

- Arrow functions are treated like variables

- const is hoisted but in TDZ

</details>

## 📌 Question 6: Hoisting Inside Function Scope
```js
function test() {
  console.log(a);
  var a = 20;
}
test();
```
<details> <summary><b>✅ Output</b></summary>
undefined

</details> <details> <summary><b>🧠 Explanation</b></summary>

- Hoisting happens within function scope, not globally.
- Equivalent to:
```js
function test() {
  var a;
  console.log(a);
  a = 20;
}
```
</details>

## 📌 Question 7: Variable Shadowing + Hoisting
```js
var x = 10;

function foo() {
  console.log(x);
  var x = 20;
}

foo();
```
<details> <summary><b>✅ Output</b></summary>
undefined
<details>
<summary><b>🧠 Explanation</b></summary>

- Local `x` is hoisted inside `foo`
- It shadows the global `x`
- Value is `undefined` at log time

</details>


## ⭐ Interview Tip

Hoisting moves declarations, not initializations.
