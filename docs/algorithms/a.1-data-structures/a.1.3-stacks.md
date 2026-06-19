# A.1.3: Stacks

## Learning Objectives

1. Stacks are a last-in-first-out data structure, typically implemented with arrays
2. The stack concept is useful for tracking ordered data that we may need to reverse, e.g. text edits

## Introduction

{% include youtube.html id="F1F2imiOJfk" %}
Brief introduction to stack concepts, methods and applications


A stack (think stack of plates) is an array-like data structure that supports adding and removing only from the end, aka "top" of the stack. In practice we will use arrays to represent stacks, but what's important is the pattern of only adding and removing from the end of an array to model and solve certain types of problems.

The stack concept powers many features we use daily, including:

1. Undo and redo in text editors (adding new edits to top of stack and removing them on undo)
2. Parentheses-matching in code editors (adding new opening parens to top of stack, removing them on closing paren and highlighting the pair with the same colour)
3. Browser history (new pages get added to a stack, clicking back button pops them off the stack)

Because we only ever add or remove from the end of the stack, all stack operations run in `O(1)` time complexity.

## Exercises

Please use JavaScript arrays to perform stack operations.

After attempting each problem, find solutions in the Leaderboard tab (HackerRank, may be on left side of page) or Solution or Discuss tabs (LeetCode) on that problem's page. If you get stuck for more than 15 minutes, review and understand the solutions and move on. Come back and re-attempt the problem after a few days.

### Pre-Class

1. Remove All Adjacent Duplicates in String (<a href="https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/" target="_blank">LeetCode</a>)
   1. <a href="https://youtu.be/y---RCHCdD4?t=4613" target="_blank">Rocket strategy video</a> (Python)

### Part 1

1. Make The String Great (<a href="https://leetcode.com/problems/make-the-string-great/" target="_blank">LeetCode</a>)
   1. <a href="https://youtu.be/y---RCHCdD4?t=4457" target="_blank">Rocket strategy video</a> (Python)
2. Backspace String Compare (<a href="https://leetcode.com/problems/backspace-string-compare/" target="_blank">LeetCode</a>)

### Part 2

1. Crawler Log Folder (<a href="https://leetcode.com/problems/crawler-log-folder/" target="_blank">LeetCode</a>)
   1. <a href="https://youtu.be/y---RCHCdD4?t=2460" target="_blank">Rocket solution video</a> (Python)
2. Maximum Element (<a href="https://www.hackerrank.com/challenges/maximum-element/problem?isFullScreen=true" target="_blank">HackerRank</a>)

### Part 3

1. Valid Parentheses (<a href="https://leetcode.com/problems/valid-parentheses/" target="_blank">LeetCode</a>, <a href="https://www.hackerrank.com/challenges/balanced-brackets/problem?isFullScreen=true" target="_blank">HackerRank</a>)
   1. <a href="https://pastebin.com/qGbG1BAN" target="_blank">Rocket solution code</a> (Python)
2. Minimum Add To Make Parentheses Valid (<a href="https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/" target="_blank">LeetCode</a>)

### Part 4

1. Simple Text Editor (<a href="https://www.hackerrank.com/challenges/simple-text-editor/problem?isFullScreen=true" target="_blank">HackerRank</a>)
2. Validate Stack Sequences (<a href="https://leetcode.com/problems/validate-stack-sequences/" target="_blank">LeetCode</a>)

### More Comfortable

1. Score of Parentheses (<a href="https://leetcode.com/problems/score-of-parentheses/" target="_blank">LeetCode</a>)
   1. Hint: The depth of the stack can be the power of 2
2. Daily Temperatures (<a href="https://leetcode.com/problems/daily-temperatures/" target="_blank">LeetCode</a>)
   1. Hint: Store temperatures and their array indexes in a stack as we iterate through the input array, and pop those temperatures off the stack and populate "num days until warmer temperature" in answer array when we see a warmer temperature.

## Additional Resources

1. <a href="https://www.youtube.com/watch?v=F1F2imiOJfk" target="_blank">This video</a> is slightly more detailed introduction to stacks than the video above
2. <a href="https://youtu.be/y---RCHCdD4?t=559" target="_blank">FTBC3 class video </a>introducing stacks
