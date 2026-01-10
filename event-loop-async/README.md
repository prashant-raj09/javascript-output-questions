# 🔁 Event Loop & Async – Output-Based JavaScript Questions

The Event Loop tests a developer’s understanding of **execution order**,  
**call stack**, **microtasks**, and **macrotasks**.

---

## 📌 Question 1: Basic Event Loop

```js
console.log("A");

setTimeout(() => console.log("B"), 0);

console.log("C");
```
<details> <summary><b>✅ Output</b></summary>
A
C
B
</details> <details> <summary><b>🧠 Explanation</b></summary>

- Synchronous code runs first

- setTimeout goes to the macrotask queue

- Macrotasks run after the call stack is empty

</details>

## 📌 Question 2: Promise vs setTimeout
```js
console.log("start");

setTimeout(() => console.log("timeout"), 0);

Promise.resolve().then(() => console.log("promise"));

console.log("end");
```

<details> <summary><b>✅ Output</b></summary>
start
end
promise
timeout
</details> <details> <summary><b>🧠 Explanation</b></summary>

- Promise callbacks go to the microtask queue

- Microtasks execute before macrotasks

- setTimeout is a macrotask

</details>

## 📌 Question 3: Multiple Promises
```js
Promise.resolve()
  .then(() => console.log("P1"))
  .then(() => console.log("P2"));

setTimeout(() => console.log("T1"), 0);
```

<details> <summary><b>✅ Output</b></summary>
P1
P2
T1
</details> <details> <summary><b>🧠 Explanation</b></summary>

- All microtasks complete before any macrotask

- Promise chaining stays in the microtask queue

</details>

## 📌 Question 4: Nested setTimeout
```js
setTimeout(() => {
  console.log("A");
  setTimeout(() => console.log("B"), 0);
}, 0);
```
<details> <summary><b>✅ Output</b></summary>
A
B
</details> <details> <summary><b>🧠 Explanation</b></summary>

- Inner setTimeout is scheduled after outer executes

- Each setTimeout creates a new macrotask

</details>

## 📌 Question 5: Async / Await Order
```js
async function test() {
  console.log("A");
  await Promise.resolve();
  console.log("B");
}

console.log("C");
test();
console.log("D");
```

<details> <summary><b>✅ Output</b></summary>
C
A
D
B
</details> <details> <summary><b>🧠 Explanation</b></summary>

- await pauses function execution

- Code after await runs as a microtask

- Async function starts synchronously

</details>

## 📌 Question 6: Promise inside setTimeout
```js
setTimeout(() => {
  console.log("timeout");
  Promise.resolve().then(() => console.log("promise"));
}, 0);

```

<details> <summary><b>✅ Output</b></summary>
timeout
promise

</details> <details> <summary><b>🧠 Explanation</b></summary>

- Macrotask executes first

- Microtasks created inside it run immediately after

</details>

## 📌 Question 7: Complex Ordering (Senior-Level)
```js
console.log("A");

setTimeout(() => console.log("B"), 0);

Promise.resolve().then(() => {
  console.log("C");
  setTimeout(() => console.log("D"), 0);
});

console.log("E");
```
<details> <summary><b>✅ Output</b></summary>
A
E
C
B
D
</details> <details> <summary><b>🧠 Explanation</b></summary>

- Synchronous code executes first

- Promise callback (microtask) runs next

- `B` is the first macrotask

- `D` is scheduled later from inside a microtask

</details>

## ⭐ Interview Golden Rule

- Microtasks always run before macrotasks.