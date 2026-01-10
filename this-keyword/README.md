# 🎯 `this` Keyword – Output-Based JavaScript Questions

The `this` keyword is one of the **most confusing and frequently asked**
topics in **senior JavaScript interviews**.

---

## 📌 Question 1: Global Context

```js
console.log(this);
```

<details> <summary><b>✅ Output</b></summary>
Window (browser) / global (Node.js)
</details> <details> <summary><b>🧠 Explanation</b></summary>

- In non-strict mode, this refers to the global object

- In browsers → window

- In Node.js → global

</details>

## 📌 Question 2: this Inside Object Method

```js
const obj = {
  name: "JavaScript",
  getName() {
    console.log(this.name);
  }
};

obj.getName();
```
<details> <summary><b>✅ Output</b></summary>
JavaScript
</details> <details> <summary><b>🧠 Explanation</b></summary>

- this refers to the object before the dot

- Here, this === obj

</details>

## 📌 Question 3: Method Detached from Object
```js
const obj = {
  name: "JS",
  getName() {
    console.log(this.name);
  }
};

const fn = obj.getName;
fn();
```
<details> <summary><b>✅ Output</b></summary>
undefined

</details> <details> <summary><b>🧠 Explanation</b></summary>

- this depends on how the function is called

- Detached function loses its object context

- this falls back to global object (or undefined in strict mode)

</details>

## 📌 Question 4: this with Arrow Function
```js
const obj = {
  name: "JS",
  getName: () => {
    console.log(this.name);
  }
};

obj.getName();
```
<details> <summary><b>✅ Output</b></summary>
undefined
</details> <details> <summary><b>🧠 Explanation</b></summary>

- Arrow functions do not have their own this

- They capture this from lexical scope

- Here, lexical this is global

</details>

## 📌 Question 5: Arrow Function Inside Method
```js
const obj = {
  name: "JS",
  getName() {
    return () => {
      console.log(this.name);
    };
  }
};

obj.getName()();
```
<details> <summary><b>✅ Output</b></summary>
JS
</details> <details> <summary><b>🧠 Explanation</b></summary>

- Arrow function captures this from enclosing function

- Enclosing this refers to obj

</details>

## 📌 Question 6: this with call
```js
function greet() {
  console.log(this.name);
}

const user = { name: "Prashant" };

greet.call(user);
```
<details> <summary><b>✅ Output</b></summary>
Prashant
</details> <details> <summary><b>🧠 Explanation</b></summary>

- call explicitly sets this

- First argument becomes the context

</details>

## 📌 Question 7: this in Constructor Function
```js
function Person(name) {
  this.name = name;
}

const p = new Person("Alex");
console.log(p.name);
```
<details> <summary><b>✅ Output</b></summary>
Alex
</details> <details> <summary><b>🧠 Explanation</b></summary>

- new creates a new object

- this points to the newly created object

</details>



## ⭐ Interview Rule (Golden)
- `this` is determined at call time, not at declaration time.
