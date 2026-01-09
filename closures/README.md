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

- Each call to createCounter() creates a new closure with its own count.
- c1 and c2 do not share state.

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
All callbacks reference the same `i`, whose final value is 3.

</details>

## 📌 Question 3: Fixing Closure with IIFE
```js
for (var i = 0; i < 3; i++) {
   // Immediately Invoked Function Expression (IIFE)
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

IIFE creates a new scope for each iteration, capturing the current value of `i`.

</details>

## 📌 Question 4: Closure with let
```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 0);
}
```
<details> <summary><b>✅ Output</b></summary>
0
1
2
</details> <details> <summary><b>🧠 Explanation</b></summary>

let is block-scoped, so each loop iteration gets its own `i`.

</details>

## 📌 Question 5: Closure with Function Parameter
```js
function outer(x) {
  return function inner(y) {
    console.log(x + y);
  };
}

const fn = outer(10);
fn(5);
fn(20);
```
<details> <summary><b>✅ Output</b></summary>
15
30
</details> <details> <summary><b>🧠 Explanation</b></summary>

inner retains access to `x` even after outer has finished execution.

</details>

## 📌 Question 6: Multiple Closures Sharing Same Scope
```js
function outer() {
  let count = 0;

  return {
    increment() {
      count++;
      console.log(count);
    },
    decrement() {
      count--;
      console.log(count);
    }
  };
}

const counter = outer();
counter.increment();
counter.increment();
counter.decrement();
```
<details> <summary><b>✅ Output</b></summary>
1
2
1
</details> <details> <summary><b>🧠 Explanation</b></summary>

Both functions share the same closure variable count.

</details>

## 📌 Question 7: Closure Trap with Reassignment
```js
let x = 10;

function foo() {
  console.log(x);
}

function bar() {
  let x = 20;
  foo();
}

bar();
```
<details> <summary><b>✅ Output</b></summary>
10
</details> <details> <summary><b>🧠 Explanation</b></summary>

- Closures are based on lexical scope, not call stack.
- foo captures `x` from the global scope.

</details>

## 📌 Question 8: Closure + setTimeout + Mutation

```js
function test() {
  let x = 1;
  setTimeout(() => {
    console.log(x);
  }, 1000);
  x = 5;
}

test();
```

<details> <summary><b>✅ Output</b></summary>
5
</details> <details> <summary><b>🧠 Explanation</b></summary>

- Closures capture variables, not values.
- The updated value of `x` is logged.

</details>

## 