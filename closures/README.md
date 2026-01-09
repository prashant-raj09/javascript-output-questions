# 🔒 Closures – Output-Based Questions

---

## Question 1
```js
function createCounter() {
  let count = 0;
  return function () {
    return ++count;
  };
}

const c1 = createCounter();
const c2 = createCounter();

console.log(c1());
console.log(c1());
console.log(c2());
console.log(c1());
