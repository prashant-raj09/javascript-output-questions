# 🤞 Promises & Async / Await – Output-Based JavaScript Questions

This section focuses on **Promise chaining**, **error handling**, and  
**async/await execution order**.

---

## 📌 Question 1: Basic Promise Resolution

```js
Promise.resolve("Success")
  .then(res => console.log(res));

console.log("End");
```

<details> <summary><b>✅ Output</b></summary>
End
Success
</details> <details> <summary><b>🧠 Explanation</b></summary>

- Synchronous code executes first

- `.then()` callback goes to the microtask queue

- Microtasks run after the call stack is empty

</details>

## 📌 Question 2: Promise Chaining
```js
Promise.resolve(1)
  .then(x => x + 1)
  .then(x => x + 1)
  .then(x => console.log(x));
```

<details> <summary><b>✅ Output</b></summary>
3
</details> <details> <summary><b>🧠 Explanation</b></summary>

- Each `.then()` returns a new Promise

- The resolved value is passed to the next .then()

</details>

## 📌 Question 3: Promise Rejection Flow
```js
Promise.resolve(10)
  .then(x => { throw x; })
  .then(x => console.log(x))
  .catch(err => console.log(err));

```
<details> <summary><b>✅ Output</b></summary>
10
</details> <details> <summary><b>🧠 Explanation</b></summary>

- Throwing inside `.then()` creates a rejected Promise

- `.catch()` handles the rejection

</details>

## 📌 Question 4: `async` Function Execution Order
```js
async function test() {
  console.log("A");
  return "B";
}

test().then(res => console.log(res));
console.log("C");
```
<details> <summary><b>✅ Output</b></summary>
A
C
B
</details> <details> <summary><b>🧠 Explanation</b></summary>

- async functions start synchronously

- Returned value is wrapped in a Promise

- `.then()` runs as a microtask

</details>

## 📌 Question 5: `await` vs `Promise.then`
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

- Code before await runs synchronously

- Code after await runs as a microtask

</details>

## 📌 Question 6: `try / catch` with Promise
```js
async function test() {
  try {
    return Promise.reject("Error");
  } catch (e) {
    console.log("Caught");
  }
}

test().catch(err => console.log(err));
```
<details> <summary><b>✅ Output</b></summary>
Error
</details> <details> <summary><b>🧠 Explanation</b></summary>

- `try/catch` does NOT catch un-awaited Promises

- The rejection propagates to `.catch()`

</details>

## ⭐ Interview Golden Rule

- await pauses execution, .then() schedules a microtask.