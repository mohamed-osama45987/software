# Quiz: Binary Search

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

Try each question closed-book first. Click **Show hint** if you get stuck — hints point you at the relevant lesson section and how to think about the question, without naming the answer.

## Questions

1. What precondition must an array satisfy before binary search can be used on it?

- [ ] It must contain only positive numbers
- [ ] It must be sorted
- [ ] It must have an even number of elements
- [ ] It must contain no duplicates

<details>
<summary>Show hint</summary>

- **Where:** [Binary Search](../a.1.1.1-binary-search.md) — Introduction.
- **Think:** The lesson's opening sentence says binary search lets us search "a ___ array" in `O(log n)` time.

</details>

2. What is the time complexity of binary search on an array of size `n`?

- [ ] `O(n)`
- [ ] `O(n^2)`
- [ ] `O(log n)`
- [ ] `O(1)`

<details>
<summary>Show hint</summary>

- **Where:** [Binary Search](../a.1.1.1-binary-search.md) — Introduction.
- **Think:** This is stated directly in the first sentence of the lesson.

</details>

3. In the example `binarySearch` implementation, what are `left_index` and `right_index` initialised to?

- [ ] Both to `0`
- [ ] `left_index = 0`, `right_index = arr.length - 1`
- [ ] `left_index = arr.length - 1`, `right_index = 0`
- [ ] Both to `arr.length`

<details>
<summary>Show hint</summary>

- **Where:** [Binary Search](../a.1.1.1-binary-search.md) — "Example Code".
- **Think:** These two variables represent the bounds of the *current search range*, which initially should cover the *whole array*.

</details>

4. What is the loop condition for the `while` loop in the example implementation?

- [ ] `while (left_index < right_index)`
- [ ] `while (left_index <= right_index)`
- [ ] `while (mid_index !== x)`
- [ ] `while (true)`

<details>
<summary>Show hint</summary>

- **Where:** [Binary Search](../a.1.1.1-binary-search.md) — "Example Code".
- **Think:** The comment above the loop says it runs "While `left_index` and `right_index` have **yet to overlap**". Overlapping means they've crossed *or become equal* — so when should the loop *stop*?

</details>

5. How is `mid_index` calculated in each iteration?

- [ ] `Math.ceil((left_index + right_index) / 2)`
- [ ] `Math.floor((left_index + right_index) / 2)`
- [ ] `(left_index + right_index) * 2`
- [ ] `left_index - right_index`

<details>
<summary>Show hint</summary>

- **Where:** [Binary Search](../a.1.1.1-binary-search.md) — "Example Code".
- **Think:** The lesson explicitly says `Math.floor` is used "to ensure that the index position is an integer not a decimal". Which rounding function does that?

</details>

6. If `arr[mid_index] < x`, what update is made to the search bounds?

- [ ] `right_index = mid_index - 1`
- [ ] `left_index = mid_index + 1`
- [ ] `left_index = mid_index`
- [ ] No update — the loop exits

<details>
<summary>Show hint</summary>

- **Where:** [Binary Search](../a.1.1.1-binary-search.md) — "Example Code".
- **Think:** If the middle element is *too small*, the target `x` must be somewhere to the *right* of `mid_index` — so which bound moves, and in which direction?

</details>

7. If `arr[mid_index] > x` (i.e. `x` is less than the middle element), what update is made?

- [ ] `left_index = mid_index + 1`
- [ ] `right_index = mid_index - 1`
- [ ] `right_index = mid_index + 1`
- [ ] `left_index = mid_index - 1`

<details>
<summary>Show hint</summary>

- **Where:** [Binary Search](../a.1.1.1-binary-search.md) — "Example Code", the `else` branch.
- **Think:** This is the mirror image of the previous question — `x` must be to the *left* of `mid_index`, so the *right* bound shrinks. By how much, and in which direction?

</details>

8. What does the function return if the `while` loop completes without finding `x`?

- [ ] `0`
- [ ] `null`
- [ ] `-1`
- [ ] `undefined`

<details>
<summary>Show hint</summary>

- **Where:** [Binary Search](../a.1.1.1-binary-search.md) — "Example Code", final line of the function.
- **Think:** This is a common sentinel value meaning "not found, and definitely not a valid array index" — look at the line right after the closing `}` of the `while` loop.

</details>

9. Given `myList = [2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]` and `binarySearch(myList, 6)`, what value does the function return?

- [ ] `6`
- [ ] `5`
- [ ] `4`
- [ ] `-1`

<details>
<summary>Show hint</summary>

- **Where:** [Binary Search](../a.1.1.1-binary-search.md) — "Example Code", usage example with `// 4` comment.
- **Think:** The lesson's own usage example tells you the answer directly via an inline comment. Confirm it by counting indices from `0`.

</details>

10. Why is binary search generally faster than scanning every element one-by-one (linear search) for large sorted arrays?

- [ ] Binary search checks every element too, but in a different order
- [ ] Binary search eliminates roughly half of the remaining search space with each comparison
- [ ] Binary search uses extra memory to pre-sort the array each time
- [ ] It isn't faster — they're equivalent in practice

<details>
<summary>Show hint</summary>

- **Where:** [Binary Search](../a.1.1.1-binary-search.md) — Introduction and "Example Code" walkthrough.
- **Think:** Each comparison moves either `left_index` or `right_index` to roughly the midpoint of the *current* range — what fraction of the remaining range does that discard each time? This is the intuitive reason behind `O(log n)`.

</details>
