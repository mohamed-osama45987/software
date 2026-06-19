# Assignment: Promises and Async-Await

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

## Setup

Create a new folder with a single file `index.js`. You can run it with `node index.js`. No external packages are required for Tasks 1–2; Task 3 uses `axios`, so run `npm init -y && npm install axios` first.

## Tasks

1. Sequential promises with `.then`

   Write a function `runSequential()` that returns a single chained promise (using `.then`, not `async`/`await`) which:

   - Resolves a first "fake request" promise `step1()` that returns the string `"step1 done"` after 500ms (use `setTimeout` wrapped in `new Promise`)
   - Logs the result of `step1`
   - Then calls `step2()`, another fake 500ms promise that returns `"step2 done"`
   - Logs the result of `step2`
   - Attaches a single `.catch` at the end that logs `"Error:"` followed by the error

2. The same logic with `async`/`await`

   Write an `async` function `runSequentialAsync()` that performs the **same two steps** as Task 1, but using `await` and a `try/catch` block instead of `.then`/`.catch`. Reuse `step1` and `step2` from Task 1 — do not duplicate their logic.

3. Concurrent requests with `Promise.all` and Axios

   Using `axios`, write an `async` function `getDogAndCatFacts()` that:

   - Sends two GET requests **concurrently** (not one after another) using `Promise.all`:
     - `https://dog.ceo/api/breeds/image/random` (returns a random dog image URL)
     - `https://catfact.ninja/fact` (returns a random cat fact)
   - Once both resolve, logs the dog image URL and the cat fact
   - Wraps the whole thing in `try/catch` and logs any error

4. Run all three

   At the bottom of `index.js`, call `runSequential()`, then `runSequentialAsync()`, then `getDogAndCatFacts()`. Add comments noting the *order* in which you'd expect their console output to interleave, given that some of these are firing requests concurrently.

## Deliverable

Submit `index.js` containing all functions from Tasks 1–4, runnable with `node index.js`.

## Hints

<details>
<summary>Show hints</summary>

## Task 1 — sequential `.then`
- **Where:** [Promises README](../README.md) — "Sequential Promises", `.then`, `.catch`.
- **Think:** `step1` and `step2` each need to be functions that *return a promise*. Wrap `setTimeout` in `new Promise((resolve) => { ... })` and call `resolve(value)` inside the timeout callback. Chain with `.then(result => { console.log(result); return step2(); }).then(...)`.
- **Starter:**
  ```javascript
  const step1 = () => new Promise((resolve) => {
    setTimeout(() => resolve("step1 done"), 500);
  });

  const step2 = () => new Promise((resolve) => {
    setTimeout(() => resolve("step2 done"), 500);
  });

  const runSequential = () => {
    return step1()
      .then((result) => {
        console.log(result);
        return step2();
      })
      // continue: log step2's result, then .catch
  };
  ```

## Task 2 — `async`/`await` version
- **Where:** [Async Await](../0.4.6.1-async-await.md) — "Catch errors with async-await".
- **Think:** The function signature changes to `const runSequentialAsync = async () => { try { ... } catch (error) { ... } }`. Each step becomes `const result1 = await step1();` followed by a `console.log`.
- **Starter:**
  ```javascript
  const runSequentialAsync = async () => {
    try {
      const result1 = await step1();
      console.log(result1);
      // your turn: await step2(), log it
    } catch (error) {
      console.error("Error:", error);
    }
  };
  ```

## Task 3 — `Promise.all` with Axios
- **Where:** [Promises README](../README.md) — `Promise.all` section.
- **Think:** `Promise.all([axios.get(url1), axios.get(url2)])` returns an array of two **Axios response objects**, not the raw data — you'll need `.data` on each. Destructure the array in the order you passed the requests in.
- **Starter:**
  ```javascript
  const axios = require("axios");

  const getDogAndCatFacts = async () => {
    try {
      const [dogRes, catRes] = await Promise.all([
        axios.get("https://dog.ceo/api/breeds/image/random"),
        axios.get("https://catfact.ninja/fact"),
      ]);
      // dogRes.data.message is the image URL
      // catRes.data.fact is the cat fact
    } catch (error) {
      console.error("Error:", error);
    }
  };
  ```

## Task 4 — ordering
- **Where:** [Async Await](../0.4.6.1-async-await.md) — "Async-await does not pause programs, only code in current function".
- **Think:** None of these three calls `await` *each other* at the top level, so they all start "at roughly the same time" from JS's perspective — but each one's *internal* `await`s mean their `console.log`s land at different real times. Reason about which 500ms timers vs. real network requests will finish first; there's no single "correct" exact ordering, but you should be able to argue for a plausible one.

## Common pitfalls
- Forgetting that `setTimeout`'s callback needs to call `resolve(...)`, not just run code — otherwise the promise never settles.
- In Task 3, using `axios.get(url).data` directly (`.data` is on the *resolved value*, not on the promise itself — you need `await` or `.then` first).
- Mixing `.then` and `await` in the same function for Task 2 — pick one style per function as the lesson does.

</details>
