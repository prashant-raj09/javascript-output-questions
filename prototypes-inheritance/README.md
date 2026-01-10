# 🧬 Prototypes & Inheritance – Output-Based JavaScript Questions

This section focuses on **prototype chains**, **constructor functions**,  
and **inheritance-related edge cases** commonly asked in senior interviews.

---

## 📌 Question 1: Basic Prototype Lookup

```js
function A() {}
A.prototype.x = 10;

const a = new A();
console.log(a.x);
```
<details> <summary><b>✅ Output</b></summary>
10

</details> <details> <summary><b>🧠 Explanation</b></summary>

- Property x is not found on object a

- JavaScript looks up the prototype chain

- `x` is found on A.prototype

</details>

## 📌 Question 2: Prototype vs Own Property
```js
function A() {}
A.prototype.x = 10;

const a = new A();
a.x = 20;

console.log(a.x);
```
<details> <summary><b>✅ Output</b></summary>

20

</details> <details> <summary><b>🧠 Explanation</b></summary>

- Assigning `a.x` creates an own property

- Own properties take precedence over prototype properties

</details>

## 📌 Question 3: Changing Prototype After Object Creation
```js
function A() {}
A.prototype.x = 10;

const a = new A();
A.prototype = { x: 20 };

console.log(a.x);
```
<details> <summary><b>✅ Output</b></summary>
10

</details> <details> <summary><b>🧠 Explanation</b></summary>

- `a` keeps a reference to the original prototype

- Reassigning `A.prototype` does not affect existing instances

</details>

## 📌 Question 4: Prototype Mutation (Affects All Instances)
```js
function A() {}
A.prototype.x = 10;

const a1 = new A();
const a2 = new A();

A.prototype.x = 30;

console.log(a1.x);
console.log(a2.x);
```
<details> <summary><b>✅ Output</b></summary>
30
30

</details> <details> <summary><b>🧠 Explanation</b></summary>

- Both instances share the same prototype object

- Mutating the prototype affects all instances

</details>

## 📌 Question 5: Prototype Chain Resolution
```js
function A() {}
A.prototype.x = 10;

function B() {}
B.prototype = Object.create(A.prototype);

const b = new B();
console.log(b.x);
```
<details> <summary><b>✅ Output</b></summary>
10

</details> <details> <summary><b>🧠 Explanation</b></summary>

- `b → B.prototype → A.prototype`

- JavaScript resolves properties through the full prototype chain

</details>

## 📌 Question 6: Constructor Property Pitfall
```js
function A() {}
A.prototype = { x: 10 };

const a = new A();
console.log(a.constructor === A);
```
<details> <summary><b>✅ Output</b></summary>
false

</details> <details> <summary><b>🧠 Explanation</b></summary>

- Replacing prototype removes the default constructor reference

- constructor now points to Object

</details>

## 📌 Question 7: `__proto__` vs `prototype`
```js
function A() {}
const a = new A();

console.log(a.__proto__ === A.prototype);
```
<details> <summary><b>✅ Output</b></summary>
true

</details> <details> <summary><b>🧠 Explanation</b></summary>

- `__proto__` points to an object's internal prototype

- It references the constructor’s prototype

</details>

## ⭐ Interview Golden Rule

- Objects delegate property access through the prototype chain.