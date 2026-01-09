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
```

<details> <summary><b>✅ Output</b></summary>
1
2
1
3
</details> <details> <summary><b>🧠 Explanation</b></summary>

Each call to createCounter() creates a new closure with its own count.
c1 and c2 do not share state.

</details>