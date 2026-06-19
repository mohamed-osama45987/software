# Quiz: Promises and Async-Await

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

Try each question closed-book first. Click **Show hint** if you get stuck — hints point you at the relevant lesson section and how to think about the question, without naming the answer.

## Questions

1. What does `axios.get(url)` return?

- [ ] The response data directly
- [ ] A promise
- [ ] `undefined`
- [ ] An error object

<details>
<summary>Show hint</summary>

- **Where:** [Promises README](../README.md) — `.then` section.
- **Think:** We call `.then` on the return value of `axios.get`. What kind of object has a `.then` method?

</details>

2. When does the callback passed to `.then` run?

- [ ] Immediately, before the request is sent
- [ ] Synchronously, in the same line of code
- [ ] When the promise it was called on resolves
- [ ] Only if the request fails

<details>
<summary>Show hint</summary>

- **Where:** [Promises README](../README.md) — `.then` section.
- **Think:** `.then` exists specifically to defer logic until *after* something async finishes. What event triggers that deferred logic?

</details>

3. What does `.catch` do if none of the promises in the chain before it produce an error?

- [ ] It throws an error anyway
- [ ] Its callback is simply never called
- [ ] It still runs, but with `undefined` as the argument
- [ ] It cancels the rest of the chain

<details>
<summary>Show hint</summary>

- **Where:** [Promises README](../README.md) — `.catch` section.
- **Think:** `.catch` is for the error path only. What happens to a function whose triggering condition never occurs?

</details>

4. Without a `.catch`, what happens when a promise in the chain rejects?

- [ ] Nothing — the program continues as normal
- [ ] The program crashes
- [ ] The next `.then` runs with an error value
- [ ] JavaScript automatically retries the request

<details>
<summary>Show hint</summary>

- **Where:** [Promises README](../README.md) — `.catch` section.
- **Think:** The lesson explicitly states what `.catch` protects us from. What's the consequence of skipping that protection?

</details>

5. In the "Sequential Promises" example (change password → send email → log success), why is each step inside a `.then` rather than all three calls being written one after another at the top level?

- [ ] Because `axios` requires it for syntax reasons
- [ ] Because each step depends on the previous request having completed
- [ ] Because `.then` runs code faster than normal code
- [ ] It makes no difference — both approaches are equivalent

<details>
<summary>Show hint</summary>

- **Where:** [Promises README](../README.md) — "Sequential Promises".
- **Think:** What would happen if `send-email` fired before `change-password` had actually finished on the server?

</details>

6. What is the main benefit of `Promise.all` over chaining several `.then` calls one after another?

- [ ] It lets us skip writing `.catch`
- [ ] It runs the promises concurrently instead of waiting for each one sequentially
- [ ] It converts promises into synchronous code
- [ ] It automatically retries failed requests

<details>
<summary>Show hint</summary>

- **Where:** [Promises README](../README.md) — `Promise.all` section.
- **Think:** The lesson contrasts "concurrently" with "sequentially" — which is faster when the requests don't depend on each other?

</details>

7. In `Promise.all([p1, p2, p3]).then((results) => {...})`, what does `results` contain?

- [ ] Only the result of the first promise
- [ ] A single combined value
- [ ] An array of results, in the same order as `p1, p2, p3`
- [ ] A random ordering of the resolved values

<details>
<summary>Show hint</summary>

- **Where:** [Promises README](../README.md) — `Promise.all` section, `getData` example.
- **Think:** The lesson destructures `results` as `const [recipes, categories, users] = results`. What does that destructuring assume about ordering?

</details>

8. Compared to `.then` syntax, what does async-await syntax change about a function's *functionality*?

- [ ] It adds new functionality not possible with `.then`
- [ ] It makes the function run faster
- [ ] Nothing — it's the same functionality with different syntax
- [ ] It removes the need for promises entirely

<details>
<summary>Show hint</summary>

- **Where:** [Async Await](../0.4.6.1-async-await.md) — Introduction.
- **Think:** The lesson is explicit: "does not add new functionality". What *does* it change, if not functionality?

</details>

9. Which statement about `async` and `await` is correct?

- [ ] `await` can be used in any function, async or not
- [ ] `async` can be used without ever using `await` inside it
- [ ] `await` is only valid inside a function declared `async`
- [ ] `async` and `await` are interchangeable keywords

<details>
<summary>Show hint</summary>

- **Where:** [Async Await](../0.4.6.1-async-await.md) — Introduction.
- **Think:** The lesson says these two keywords "must be used together" — but the restriction is specifically about where `await` is *allowed*, not the reverse.

</details>

10. In the `getRecipes` example, `console.log("Before")` and `console.log("After")` both print *before* `console.log("Recipes")`, even though `getRecipes()` is called between them. Why?

- [ ] `console.log` inside a function is always delayed
- [ ] `getRecipes` is an async function, so it returns immediately while its internal `await` is still pending
- [ ] The order of `console.log` statements is randomised by the JS engine
- [ ] `getRecipes()` was called incorrectly

<details>
<summary>Show hint</summary>

- **Where:** [Async Await](../0.4.6.1-async-await.md) — "Async-await does not pause programs, only code in current function".
- **Think:** An `async` function call doesn't block the caller. What does `getRecipes()` return to its caller, and when does that returned thing actually settle?

</details>

11. To catch an error from `await client.query(...)`, what syntax does async-await use instead of `.catch`?

- [ ] `if/else`
- [ ] `try/catch`
- [ ] `switch/case`
- [ ] There is no way to catch errors with async-await

<details>
<summary>Show hint</summary>

- **Where:** [Async Await](../0.4.6.1-async-await.md) — "Catch errors with async-await".
- **Think:** The lesson directly maps one `.then`/`.catch` example to an equivalent block-based syntax used with `await`.

</details>

12. Which of the following correctly uses `Promise.all` with async-await syntax to fetch `recipes`, `categories`, and `users` concurrently?

- [ ] `const recipes = await pool.query("..."); const categories = await pool.query("...");` (one after another)
- [ ] `const results = await Promise.all([pool.query("..."), pool.query("..."), pool.query("...")]);`
- [ ] `const results = Promise.all(await [pool.query("..."), pool.query("..."), pool.query("...")]);`
- [ ] `Promise.all(...).await(results => {...})`

<details>
<summary>Show hint</summary>

- **Where:** [Async Await](../0.4.6.1-async-await.md) — "Async-await works with all promises, including the promise returned by `Promise.all`".
- **Think:** Only one option keeps `await` on the *outside*, applied to the whole `Promise.all(...)` expression — compare carefully against the `.then` version directly above it in the lesson.

</details>
