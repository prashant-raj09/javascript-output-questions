# 🔒 Closures – Output-Based Questions

---

## Question 1: Basic Closure
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

## 📌 Question 2: Closure with var in Loop
```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 0);
}
```
<details> <summary><b>✅ Output</b></summary>
3
3
3
</details> <details> <summary><b>🧠 Explanation</b></summary>

var is function-scoped, not block-scoped.
All callbacks reference the same i, whose final value is 3.

</details>

## 📌 Question 3: Fixing Closure with IIFE
```js
for (var i = 0; i < 3; i++) {
  (function (i) {
    setTimeout(() => console.log(i), 0);
  })(i);
}
```

<details> <summary><b>✅ Output</b></summary>
0
1
2
</details> <details> <summary><b>🧠 Explanation</b></summary>

IIFE creates a new scope for each iteration, capturing the current value of i.

</details>