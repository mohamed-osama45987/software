# Module 1 — Frontend Assessment

Mandatory module-level MCQ assessment. Try each question closed-book first; click **Show hint** for a nudge that points at the relevant lesson section without naming the answer.

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

---

1. Which CSS selector has the highest specificity?

- [ ] Tag Selector (p, h1, etc.)
- [ ] Class Selector (.)
- [ ] Universal Selector (*)
- [ ] ID Selector (#)

<details>
<summary>Show hint</summary>

- **Where:** CSS Selectors lesson — "Specificity" section.
- **Think:** Specificity is a ranking system. The four selector types each sit at a different level of that ranking — which one overrides all the others?

</details>

---

2. Which is not part of the CSS Box Model?

- [ ] Margin
- [ ] Padding
- [ ] Border
- [ ] Width

<details>
<summary>Show hint</summary>

- **Where:** CSS Box Model lesson — the diagram showing the four layers.
- **Think:** The Box Model describes the *spacing and border* layers around an element's content. Three of these options are named layers in that model — one is a property of the content area itself, not a layer of the box.

</details>

---

3. What operator can be used to get the remainder between two numbers?

- [ ] Division (/)
- [ ] Modulo (%)
- [ ] Subtraction (-)
- [ ] Multiplication (*)

<details>
<summary>Show hint</summary>

- **Where:** JavaScript Operators lesson — "Arithmetic Operators" table.
- **Think:** "Remainder" is the amount left over after dividing as many whole times as possible. Which operator in the table is described as returning the remainder?

</details>

---

4. Which represents the strict equality operator?

- [ ] !==
- [ ] !=
- [ ] ==
- [ ] ===

<details>
<summary>Show hint</summary>

- **Where:** JavaScript Operators lesson — "Comparison Operators" table.
- **Think:** "Strict" equality checks both value *and* type. The lesson contrasts `==` (loose) with the strict version — how many `=` signs does the strict version use, and what extra symbol is beside them?

</details>

---

5. What is the keyword to define the function's output value?

- [ ] result
- [ ] out
- [ ] return
- [ ] output

<details>
<summary>Show hint</summary>

- **Where:** JavaScript Functions lesson — "Return Values" section.
- **Think:** This is a reserved JavaScript keyword — one of the four options is an actual JS keyword you type inside a function body to send a value back to the caller.

</details>

---

6. Which is a correct syntax to call a function called "convertKmToMiles" that needs a number as an input?

- [ ] convertKmToMiles();
- [ ] convertKmToMiles(50);
- [ ] invoke convertKmToMiles(50);
- [ ] call convertKmToMiles(50);

<details>
<summary>Show hint</summary>

- **Where:** JavaScript Functions lesson — "Calling a Function" section.
- **Think:** To call a function with an argument, you write the function name followed by parentheses containing the value. No extra keywords like `invoke` or `call` are needed in standard JS syntax.

</details>

---

7. Given two statements, A and B, when will the AND operator have a true value?

- [ ] Statement B is true
- [ ] Both statements are true
- [ ] Neither of the statements are true
- [ ] Statement A is true

<details>
<summary>Show hint</summary>

- **Where:** JavaScript Operators lesson — "Logical Operators" section, AND (`&&`) truth table.
- **Think:** The AND operator is the strictest logical operator — it requires every condition it connects to be satisfied. What does that mean for statements A and B individually?

</details>

---

8. Which of the following is a correct way to write an if statement in JavaScript?

- [ ] `if (x > 10) -> { //statements }`
- [ ] `if x > 10 { //statements }`
- [ ] `if x > 10 -> { //statements }`
- [ ] `if (x > 10) { //statements }`

<details>
<summary>Show hint</summary>

- **Where:** JavaScript Control Flow lesson — "if statement" syntax example.
- **Think:** In JavaScript, the condition must be wrapped in parentheses, and the body must be wrapped in curly braces. There is no `->` arrow in an if statement — that belongs to arrow functions.

</details>

---

9. Which is a correct declaration of an array using JS?

- [ ] `array arr = [1, 2, 3, 4]`
- [ ] `const arr = [1, 2, 3, 4]`
- [ ] `const arr = (1, 2, 3, 4)`
- [ ] `const arr = {1, 2, 3, 4}`

<details>
<summary>Show hint</summary>

- **Where:** JavaScript Arrays lesson — "Declaring an Array" section.
- **Think:** Arrays use square brackets `[]`. The variable declaration keyword should be one of the modern JS keywords (`const`, `let`, `var`) — `array` is not a keyword in JavaScript.

</details>

---

10. Which is not a kind of loop?

- [ ] While
- [ ] Do-while
- [ ] For
- [ ] None of the above

<details>
<summary>Show hint</summary>

- **Where:** JavaScript Loops lesson — introduction listing the types of loops.
- **Think:** The lesson explicitly names the loop types available in JavaScript. Check whether all three named options (`while`, `do-while`, `for`) are listed there — then decide what "None of the above" would mean in that context.

</details>

---

11. What DOM manipulator takes in, as input, a search query and returns the first element in the DOM that matches?

- [ ] document.queryTarget()
- [ ] document.query()
- [ ] document.selector()
- [ ] document.querySelector()

<details>
<summary>Show hint</summary>

- **Where:** DOM Manipulation lesson — "Selecting Elements" section.
- **Think:** The method name describes exactly what it does: it *queries* (searches) for a *selector* (CSS selector string) and returns the first match. Which option combines those two words correctly?

</details>

---

12. Which is not a valid browser event?

- [ ] click
- [ ] keypress
- [ ] dblclick
- [ ] keyhold

<details>
<summary>Show hint</summary>

- **Where:** DOM Events lesson — list of common browser events.
- **Think:** Three of these are real, named browser events you can listen to with `addEventListener`. One is an invented name — there is no standard browser event for "holding" a key with that exact name.

</details>

---

13. Which is a correct way to call an attribute of an object?

- [ ] object["attribute"]
- [ ] object.attribute
- [ ] Both are correct
- [ ] None of the above

<details>
<summary>Show hint</summary>

- **Where:** JavaScript Objects lesson — "Accessing Properties" section.
- **Think:** The lesson shows two syntaxes for accessing object properties: dot notation and bracket notation. Both are valid JavaScript — one is more common for known property names, the other is useful when the property name is dynamic or contains special characters.

</details>

---

14. True or False. Objects can have objects nested in them?

- [ ] True
- [ ] False

<details>
<summary>Show hint</summary>

- **Where:** JavaScript Objects lesson — "Nested Objects" section.
- **Think:** The lesson gives a direct example of an object whose property value is itself another object. Consider whether JavaScript has any restriction preventing this.

</details>

---

15. Which statement is not true about props?

- [ ] Props are read-only.
- [ ] Props are used to pass data and event handlers to components.
- [ ] Props are used for component communication.
- [ ] Props can be modified within the component.

<details>
<summary>Show hint</summary>

- **Where:** React Props lesson — "Rules of Props" section.
- **Think:** The lesson is explicit that props flow in one direction and that the receiving component has a specific restriction on what it can do with them. Which option contradicts that restriction?

</details>

---

16. What symbols allow developers to write and execute JavaScript bound to the JSX?

- [ ] Parenthesis "()"
- [ ] Greater than and Less than symbols "<>"
- [ ] Curly Braces "{}"
- [ ] Square Brackets "[]"

<details>
<summary>Show hint</summary>

- **Where:** React JSX lesson — "Embedding Expressions" section.
- **Think:** JSX is HTML-like syntax inside JavaScript. To *escape back into* JavaScript within JSX, you wrap the expression in a specific pair of symbols — look at the lesson's examples of dynamic values inside JSX markup.

</details>

---

17. What is the syntax for a React state using the useState hook?

- [ ] `state, setState = useState(initialState);`
- [ ] `useState(state, setState);`
- [ ] `const state = useState(initialState);`
- [ ] `const [state, setState] = useState(initialState);`

<details>
<summary>Show hint</summary>

- **Where:** React Hooks lesson — "useState" section.
- **Think:** `useState` returns an *array* of two things: the current value and the setter function. The correct syntax uses array destructuring with `const` to capture both in one line.

</details>

---

18. What lifecycle method does useEffect replace?

- [ ] componentDidCatch
- [ ] shouldComponentUpdate
- [ ] componentWillUnmount
- [ ] componentDidMount, componentDidUpdate, and componentWillUnmount

<details>
<summary>Show hint</summary>

- **Where:** React Hooks lesson — "useEffect" section.
- **Think:** `useEffect` was introduced to unify *several* class component lifecycle methods into one hook. The lesson names which methods it replaces — it's more than one.

</details>

---

19. Which of the following are rules about using React Hooks?

- [ ] You can use Hooks inside of regular JavaScript functions.
- [ ] Hooks are primarily used for class components.
- [ ] Hooks can only be called at the top level of a React function component.
- [ ] Hooks can be called inside loops, conditions, and nested functions.

<details>
<summary>Show hint</summary>

- **Where:** React Hooks lesson — "Rules of Hooks" section.
- **Think:** The lesson lists two main rules of Hooks. One rule is about *where* in a component you can call them (top level only), and one is about *what kind* of function they can be called in (React function components, not regular JS functions or class components).

</details>

---

20. Which of these describe what the useEffect hook does?

- [ ] Provides type checking in React components
- [ ] Allows you to perform side effects in functional components
- [ ] Helps you to directly manipulate the DOM in React components
- [ ] Is used to optimize performance by memoizing component output

<details>
<summary>Show hint</summary>

- **Where:** React Hooks lesson — "useEffect" introduction.
- **Think:** "Side effects" is the key term the lesson uses to describe what `useEffect` handles — things like data fetching, subscriptions, and manually changing the DOM *after* render. Which option uses that exact term?

</details>
