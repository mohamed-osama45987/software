# A.1.1.2: Sliding Windows

## Learning Objectives

1. Understand how to apply the sliding-window technique to solve relevant array problems

## Introduction

The sliding-window technique allow us to iteratively analyse subarrays ("windows") of varying sizes in an array by storing and independently incrementing a start and end index of the current subarray. Read <a href="https://stackoverflow.com/a/64111403" target="_blank">this Stack Overflow answer</a> for an intuitive explanation.

{% include youtube.html id="jM2dhDPYMQM" %}
Video introduction to sliding windows with examples


{% include youtube.html id="4i6-9IzQHwo" %}
Longest Substring Without Repeating Characters, sliding window solution explained


## Exercises

After attempting each problem, find solutions in the Leaderboard tab (HackerRank, may be on left side of page) or Solution or Discuss tabs (LeetCode) on that problem's page. If you get stuck for more than 15 minutes, review and understand the solutions and move on. Come back and re-attempt the problem after a few days.

### Pre-Class

1. Sum of All Odd-Length Subarrays (<a href="https://leetcode.com/problems/sum-of-all-odd-length-subarrays/" target="_blank">LeetCode</a>)
   1. Note: There is no need to attempt the `O(n)` solution for now. The `O(n)` solution requires math that may not be the most relevant to us while we are practising JavaScript.
   2. Hint: Would nested loops be helpful, an outer loop that determines the length of the subarray, and an inner loop that sums all subarrays of a given length?
   3. <a href="https://pastebin.com/apxLUSQh" target="_blank">Rocket solution code</a> (Python)

### Part 1

1. Maximum Number of Vowels in a Substring of Given Length (<a href="https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/" target="_blank">LeetCode</a>)
2. Longest Turbulent Subarray (<a href="https://leetcode.com/problems/longest-turbulent-subarray/" target="_blank">LeetCode</a>)

### Part 2

1. Longest Continuous Subarray with Absolute Difference Less Than or Equal to Limit (<a href="https://leetcode.com/problems/longest-continuous-subarray-with-absolute-diff-less-than-or-equal-to-limit/" target="_blank">LeetCode</a>)
2. Grumpy Bookstore Owner (<a href="https://leetcode.com/problems/grumpy-bookstore-owner/" target="_blank">LeetCode</a>)
   1. Hint: We may want to create a helper function that calculates the number of customers satisfied in a given day, given the specific days that the bookstore owner is not grumpy.

### More Comfortable

1. Max Consecutive Ones III (<a href="https://leetcode.com/problems/max-consecutive-ones-iii/" target="_blank">LeetCode</a>)
   1. Hint: What determines the start and end of the sliding window?
   2. Hint: Do we need to track the indexes of 0s in the array?
   3. <a href="https://pastebin.com/WFGdNszB" target="_blank">Rocket solution code</a> (Python)
   4. <a href="https://youtu.be/Kynk1Tny3yQ?t=3939" target="_blank">Rocket solution video</a> (Python)
2. Longest Repeating Character Replacement (<a href="https://leetcode.com/problems/longest-repeating-character-replacement/" target="_blank">LeetCode</a>)
