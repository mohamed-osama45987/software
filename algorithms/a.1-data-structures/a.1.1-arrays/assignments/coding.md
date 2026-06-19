# Assignment: Binary Search Practice

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

## Setup

Create a single file `binarySearch.js`. You can run it with `node binarySearch.js`. No external packages needed.

## Tasks

1. Re-implement `binarySearch(arr, x)`

   Write your own version of the `binarySearch` function from the lesson (don't copy-paste — type it out yourself so the loop logic sinks in). It should return the index of `x` in sorted array `arr`, or `-1` if not found.

   Test it against:
   - `binarySearch([2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12], 6)` → should return `4`
   - `binarySearch([2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12], 2)` → first element
   - `binarySearch([2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12], 12)` → last element
   - `binarySearch([2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12], 1)` → not present, should return `-1`
   - `binarySearch([], 5)` → empty array, should return `-1`
   - `binarySearch([5], 5)` → single-element array, should return `0`

   Log the result of each test case with a label, e.g. `console.log("test 1:", binarySearch([...], 6));`

2. Count comparisons

   Modify your function (or write a second version `binarySearchCounted(arr, x)`) that also returns **how many times** it compared `arr[mid_index]` to `x`. Return `{ index, comparisons }`. Run it on a sorted array of 1000 elements (`Array.from({ length: 1000 }, (_, i) => i)`) searching for a value near the end (e.g. `999`). In a comment, note the comparison count and roughly compare it to `Math.log2(1000)`.

3. `searchInsertPosition(arr, x)`

   Write a function that, given a sorted array `arr` and a value `x` **not necessarily in the array**, returns the index where `x` *would* be inserted to keep `arr` sorted. For example, `searchInsertPosition([1, 3, 5, 6], 5)` → `2` (found exactly), and `searchInsertPosition([1, 3, 5, 6], 2)` → `1` (would go between `1` and `3`).

   This is a variant of binary search — when `x` isn't found, one of your bounds (`left_index` or `right_index`) ends up pointing at the correct insertion position when the loop ends. Figure out which one, and why.

## Deliverable

Submit `binarySearch.js` containing all three tasks with their test cases and `console.log` output, runnable via `node binarySearch.js`.

## Hints

<details>
<summary>Show hints</summary>

## Task 1 — re-implementing `binarySearch`
- **Where:** [Binary Search](../a.1.1.1-binary-search.md) — "Example Code".
- **Think:** Type the structure from memory first, then check against the lesson only if stuck: initialise `left_index`/`right_index`, `while (left_index <= right_index)`, compute `mid_index` with `Math.floor`, then three-way compare `arr[mid_index]` vs `x`.
- **Starter:** (structure only — fill in the comparison logic yourself)
  ```javascript
  const binarySearch = (arr, x) => {
    let left_index = 0;
    let right_index = arr.length - 1;
    while (left_index <= right_index) {
      const mid_index = Math.floor((left_index + right_index) / 2);
      // compare arr[mid_index] to x and update left_index/right_index, or return mid_index
    }
    return -1;
  };
  ```
  For the empty-array case: if `arr.length === 0`, then `right_index = -1` and `left_index = 0`, so `0 <= -1` is `false` — the loop body never runs, and you fall through to `return -1` automatically. Trace through this by hand to confirm.

## Task 2 — counting comparisons
- **Where:** [Binary Search](../a.1.1.1-binary-search.md) — "Example Code" (the `console.log("middle index", mid_index)` line hints that the lesson already tracks iterations for debugging — you're formalising that into a return value).
- **Think:** Add a `comparisons` counter, incremented once per loop iteration (each iteration does exactly one `arr[mid_index]` vs `x` comparison, even though it's written as up to three `if`/`else if`/`else` branches). Return `{ index: ..., comparisons }` from both the "found" and "not found" exit points.
- **Starter:**
  ```javascript
  const binarySearchCounted = (arr, x) => {
    let left_index = 0;
    let right_index = arr.length - 1;
    let comparisons = 0;
    while (left_index <= right_index) {
      comparisons += 1;
      const mid_index = Math.floor((left_index + right_index) / 2);
      // same comparison logic as Task 1, but return { index: mid_index, comparisons } on match
    }
    return { index: -1, comparisons };
  };
  ```
  `Math.log2(1000)` is roughly `9.97` — your comparison count for *any* target in a 1000-element array should be at most `Math.ceil(Math.log2(1000)) + 1` or so, regardless of where the target is. That's the whole point of `O(log n)`.

## Task 3 — `searchInsertPosition`
- **Where:** [Binary Search](../a.1.1.1-binary-search.md) — "Example Code", combined with reasoning about loop exit conditions.
- **Think:** Start from your Task 1 implementation. When `x` *is* found, return `mid_index` as before (that's also a valid insertion point — "the index where `x` would be inserted" when `x` is already there is just its own index). When the loop exits **without finding** `x`, `left_index` has crossed past `right_index` — at that exact moment, `left_index` points at the first element *greater than* `x` (or one-past-the-end of the array). That's your insertion position. Try tracing `searchInsertPosition([1, 3, 5, 6], 2)` by hand, step by step, watching what `left_index` and `right_index` equal at the moment the loop exits.
- **Starter:**
  ```javascript
  const searchInsertPosition = (arr, x) => {
    let left_index = 0;
    let right_index = arr.length - 1;
    while (left_index <= right_index) {
      const mid_index = Math.floor((left_index + right_index) / 2);
      if (arr[mid_index] === x) {
        return mid_index;
      } else if (arr[mid_index] < x) {
        left_index = mid_index + 1;
      } else {
        right_index = mid_index - 1;
      }
    }
    // one of left_index / right_index is your answer here — which one, and why?
  };
  ```

## Common pitfalls
- Off-by-one on `right_index = arr.length - 1` vs `arr.length` — using the wrong one breaks the empty-array case differently than expected.
- In Task 2, incrementing `comparisons` *inside* the `if`/`else if`/`else` (three separate increments possible per iteration) instead of once per loop — leads to over-counting.
- In Task 3, returning `right_index` when you meant `left_index` (or vice versa) — test against the worked example (`[1, 3, 5, 6]`, `x = 2` → `1`) to catch this quickly.

</details>
