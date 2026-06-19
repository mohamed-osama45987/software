# Module 2 Assessment

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

**Mandatory** • 20 questions • Covers Concepts For The Frontend lessons.

Try each question closed-book first. Click **Show hint** if you get stuck — hints point you at the relevant lesson section and how to think about it, without naming the answer.

---

**Q1.** Which CSS selector has the highest specificity?

- Tag Selector (p, h1, etc.)
- Class Selector (.)
- Universal Selector (*)
- ID Selector (#)

<details>
<summary>Show hint</summary>

- **Where:** [CSS intro](../html-css/css.md) — CSS specificity.
- **Think:** Remember the selector hierarchy: ID selectors are more specific than classes, and classes are more specific than tag selectors. The universal selector is the weakest match.

</details>

**Q2.** Which is not part of the CSS Box Model?

- Margin
- Padding
- Border
- Width

<details>
<summary>Show hint</summary>

- **Where:** [CSS layout](../html-css/layout.md) — CSS box model.
- **Think:** The box model describes the layers around content: margin, border, padding, and the content itself. Which option is not one of those layers?

</details>

**Q3.** What operator can be used to get the remainder between two numbers?

- `Division (/)`
- `Modulo (%)`
- `Subtraction (-)`
- `Multiplication (*)`

<details>
<summary>Show hint</summary>

- **Where:** [Arithmetic operators](../javascript-1/operators.md) — remainder/modulo.
- **Think:** The answer is the operator whose name literally points to the leftover piece after division. Ask yourself which one is used for “what remains.”

</details>

**Q4.** Which represents the strict equality operator?

- `!==`
- `!=`
- `==`
- `===`

<details>
<summary>Show hint</summary>

- **Where:** [Intro to logic](../javascript-1/conditional-logic.md) — equality operators.
- **Think:** “Strict” means the comparison checks both value and type. Which option is the one that does that exact job?

</details>

**Q5.** What is the keyword to define the function's output value?

- `result`
- `out`
- `return`
- `output`

<details>
<summary>Show hint</summary>

- **Where:** [Functions](../javascript-1/functions.md) — return values.
- **Think:** The keyword is the one that sends a value back from the function. It is the word you use when a function is finished computing its result.

</details>

**Q6.** Which is a correct syntax to call a function called "convertKmToMiles" that needs a number as an input?

- `convertKmToMiles();`
- `convertKmToMiles(50);`
- `invoke convertKmToMiles(50);`
- `call convertKmToMiles(50);`

<details>
<summary>Show hint</summary>

- **Where:** [Functions](../javascript-1/functions.md) — calling functions.
- **Think:** A function call uses the function name followed by parentheses. The value you want to pass goes inside those parentheses.

</details>

**Q7.** Given two statements, A and B, when will the AND operator have a true value?

- Statement B is true
- Both statements are true
- Neither of the statements are true
- Statement A is true

<details>
<summary>Show hint</summary>

- **Where:** [Intro to logic](../javascript-1/conditional-logic.md) — logical AND.
- **Think:** The AND operator is true only when every condition involved is true. Which option means “all of the conditions” rather than “one of them”?

</details>

**Q8.** Which of the following is a correct way to write an if statement in JavaScript?

- `if (x > 10) -> { //statements }`
- `if x > 10 { //statements }`
- `if x > 10 -> { //statements }`
- `if (x > 10) { //statements }`

<details>
<summary>Show hint</summary>

- **Where:** [Intro to logic](../javascript-1/conditional-logic.md) — `if` syntax.
- **Think:** The condition must be wrapped in parentheses, and the code block must use curly braces. The arrow syntax is not the correct JavaScript format here.

</details>

**Q9.** Which is a correct declaration of an array using JS?

- `array arr = [1, 2, 3, 4]`
- `const arr = [1, 2, 3, 4]`
- `const arr = (1, 2, 3, 4)`
- `const arr = {1, 2, 3, 4}`

<details>
<summary>Show hint</summary>

- **Where:** [Arrays](../javascript-1/arrays.md) — array syntax.
- **Think:** Arrays use square brackets to hold their values. Which option matches that syntax and still uses valid JavaScript declaration style?

</details>

**Q10.** Which is not a kind of loop?

- While
- Do-while
- For
- None of the above

<details>
<summary>Show hint</summary>

- **Where:** [Loops](../javascript-1/loops.md) — loop types.
- **Think:** All three named options are real loop structures in JavaScript. Pick the choice that is not actually a loop type.

</details>

**Q11.** What DOM manipulator takes in, as input, a search query and returns the first element in the DOM that matches?

- `document.queryTarget()`
- `document.query()`
- `document.selector()`
- `document.querySelector()`

<details>
<summary>Show hint</summary>

- **Where:** [DOM manipulation](../javascript-1/dom-manipulation.md) — selecting elements.
- **Think:** The method name suggests it looks for a selector and returns one matching element. Which option is the standard way to do that in the DOM?

</details>

**Q12.** Which is not a valid browser event?

- `click`
- `keypress`
- `dblclick`
- `keyhold`

<details>
<summary>Show hint</summary>

- **Where:** [DOM manipulation](../javascript-1/dom-manipulation.md) — event listeners.
- **Think:** Most browser events are common action names. Which option is not a standard event name you would normally use with `addEventListener`?

</details>

**Q13.** Which is a correct way to call an attribute of an object?

- `object["attribute"]`
- `object.attribute`
- Both are correct
- None of the above

<details>
<summary>Show hint</summary>

- **Where:** [Objects](../javascript-1/objects.md) — accessing object properties.
- **Think:** JavaScript allows both dot notation and bracket notation for object values. Which answer says that both forms are valid?

</details>

**Q14.** True or False. Objects can have objects nested in them?

- True
- False

<details>
<summary>Show hint</summary>

- **Where:** [Objects](../javascript-1/objects.md) — nested objects.
- **Think:** Objects in JavaScript can store values of many types, including other objects. That means the statement is true.

</details>

**Q15.** Which statement is not true about props?

- Props are read-only.
- Props are used to pass data and event handlers to components.
- Props are used for component communication.
- Props can be modified within the component.

<details>
<summary>Show hint</summary>

- **Where:** [React](../react/react.md) — components and props.
- **Think:** Props are intended to travel from parent to child and should not be changed directly by the child. Which option contradicts that idea?

</details>

**Q16.** What symbols allow developers to write and execute JavaScript bound to the JSX?

- `Parenthesis "()"`
- `Curly braces "{}"`
- `Greater than and Less than symbols "<>"`
- `Square Brackets "[]"`

<details>
<summary>Show hint</summary>

- **Where:** [React](../react/react.md) — JSX syntax.
- **Think:** JSX lets you insert JavaScript expressions directly into markup. The symbols used for that are the same ones used to wrap expressions inside JSX.

</details>

**Q17.** What is the syntax for a React state using the useState hook?

- `state, setState = useState(initialState);`
- `useState(state, setState);`
- `const state = useState(initialState);`
- `const [state, setState] = useState(initialState);`

<details>
<summary>Show hint</summary>

- **Where:** [useState](../react/useState.md) — hook syntax.
- **Think:** The hook returns two values, so the correct pattern is array destructuring. Which option assigns them as a pair correctly?

</details>

**Q18.** What lifecycle method does useEffect replace?

- `componentDidCatch`
- `shouldComponentUpdate`
- `componentWillUnmount`
- `componentDidMount, componentDidUpdate, and componentWillUnmount`

<details>
<summary>Show hint</summary>

- **Where:** [useEffect](../react/useEffect.md) — lifecycle behavior.
- **Think:** `useEffect` is commonly used to handle the setup and cleanup work that class components used separate lifecycle methods for. Which option lists those related lifecycle phases?

</details>

**Q19.** Which of the following are rules about using React Hooks?

- `You can use Hooks inside of regular JavaScript functions.`
- `Hooks are primarily used for class components.`
- `Hooks can only be called at the top level of a React function component.`
- `Hooks can be called inside loops, conditions, and nested functions.`

<details>
<summary>Show hint</summary>

- **Where:** [useState](../react/useState.md) — rules of hooks.
- **Think:** Hooks must be called in a predictable order, so they should not be placed inside loops or conditional branches. Which option describes that rule correctly?

</details>

**Q20.** Which of these describe what the useEffect hook does?

- `Provides type checking in React components`
- `Allows you to perform side effects in functional components`
- `Helps you to directly manipulate the DOM in React components`
- `Is used to optimize performance by memoizing component output`

<details>
<summary>Show hint</summary>

- **Where:** [useEffect](../react/useEffect.md) — purpose of the hook.
- **Think:** `useEffect` is meant for actions that happen after render, such as API calls, subscriptions, and cleanup. Which option best matches that purpose?

</details>
