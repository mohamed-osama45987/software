# A.5: Dynamic Programming

## Learning Objectives

1. Dynamic programming (DP) problems are a subset of recursion problems that involve caching intermediate calculations to avoid repeated calculations
2. DP problems often involve "take or don't take" logic in each recursive call, which results in repeated calculations without caching
3. DP problems are not the most commonly seen interview problems (less common at most SWE jobs), and Rocket recommends being comfortable with prior algorithm topics before spending too much time on DP

## Introduction

Dynamic programming allows us to optimise recursive solutions by "caching" (i.e. storing) intermediate calculations to minimise repeated and redundant recursive calls.

The first 40 minutes of the below video visually explain the premise behind dynamic programming and why it is powerful. The remainder of the video walks through DP solutions to other problems, which we do not need to review right now.

{% include youtube.html id="oBt53YbR9Kk" %}
Introduction to dynamic programming

## Take or Don't Take

Many dynamic programming problems involve "take or don't take" logic, where we will need to choose an optimal set of values from a collection (e.g. array) with constraints such as no two adjacent values can be in the solution.

For example, given an input array, our objective might be to find the maximum sum of chosen values in the array where we cannot choose adjacent values.&#x20;

This problem is not the most straightforward because we cannot adopt a "greedy" solution by always choosing the largest numbers we see. Doing so may give us a suboptimal solution. For example, if the input array were `[2, 4, 3]`, the optimal solution would be to pick `2` and `3`, but if we had just chosen the largest of the first 2 numbers we looked at, we would have picked 4.

This is where recursion can help us, and dynamic programming can help optimise. Let's call this problem `maxSumNoAdjacent`. My code might look like the following.

```javascript
// We would use the cache to store intermediate calculations
const cache = {};
const maxSumNoAdjacent = (arr) => {
  // Base case: If array empty, return 0
  if (arr.length === 0) {
    return 0;
  }
  // Base case: If array length 1, return the only value in array
  if (arr.length === 1) {
    return arr[0];
  }
  // If calculation done before, return calculated value
  if (cache[arr]) {
    return cache[arr];
  }
  // Calculate max value if we choose the first element
  const resultIfChooseFirst = arr[0] + maxSumNoAdjacent(arr.slice(2));
  // Calculate max value if we do not choose the first element
  const resultIfChooseSecond = maxSumNoAdjacent(arr.slice(1));
  // Return the resulting value that is larger if we "take or don't take"
  return Math.max(resultIfChooseFirst, resultIfChooseSecond);
}
```

Notice in the final line of the code we return the maximum of values when we "take or don't take".

## Exercises

### Part 1

Please fork starter code Repl and attempt solutions there. Feel free to compare with reference solutions after attempting each problem. Conway and Catalan problems are optional. Have fun!

1. <a href="https://replit.com/@rocketkai/dp#index.js" target="_blank">Rocket DP intro problems</a> (<a href="https://replit.com/@rocketkai/dp-soln#index.js" target="_blank">solutions</a>)

### Part 2

1. Climbing Stairs (<a href="https://leetcode.com/problems/climbing-stairs/" target="_blank">LeetCode</a>)

### Part 3

1. Min Cost Climbing Stairs (<a href="https://leetcode.com/problems/min-cost-climbing-stairs/" target="_blank">LeetCode</a>)

### Part 4

1. House Robber (<a href="https://leetcode.com/problems/house-robber/" target="_blank">LeetCode</a>)

### More Comfortable

1. Maximum Points You Can Obtain From Cards (<a href="https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/" target="_blank">LeetCode</a>)
2. Minimum Operations to Reduce X to Zero (<a href="https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/" target="_blank">LeetCode</a>)
3. Coin Change (<a href="https://www.hackerrank.com/challenges/coin-change/problem?isFullScreen=true" target="_blank">HackerRank</a>, <a href="https://leetcode.com/problems/coin-change/" target="_blank">LeetCode</a>)

## Further Reading

1. <a href="https://youtu.be/ASoaQq66foQ" target="_blank">Video solution to Longest Common Subsequence</a>, a DP problem that involves storing intermediate calculations in a table with dimensions `m` by `n`, where `m` is the length of 1 input word and `n` is the length of the other.
