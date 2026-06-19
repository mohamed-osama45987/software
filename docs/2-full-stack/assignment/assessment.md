# Module 2 Assessment

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

**Mandatory** • 20 questions • Covers concepts for the Full Stack lessons.

Try each question closed-book first. Click **Show hint** if you get stuck — hints point you at the relevant lesson section and how to think about it, without naming the answer.

---

**Q1.** What is the purpose of an HTTP request?

- To establish a database connection
- To manage files on a server
- To receive data from a server
- To send data to a server

<details>
<summary>Show hint</summary>

- **Where:** [HTTP requests and responses](../2.1-internet-101/2.1.2-http-requests-and-responses.md) — request/response basics.
- **Think:** A request is the message your app sends out first; the response is what comes back afterward.

</details>

**Q2.** Which HTTP method is used to update an existing resource?

- GET
- POST
- DELETE
- PUT

<details>
<summary>Show hint</summary>

- **Where:** [HTTP requests and responses](../2.1-internet-101/2.1.2-http-requests-and-responses.md) — common HTTP methods.
- **Think:** Which method is the one specifically used when you want to change something that already exists?

</details>

**Q3.** What is a Promise in JavaScript?

- A method for creating classes
- A function that returns multiple values
- A way to handle synchronous operations
- An object representing the eventual completion or failure of an asynchronous operation

<details>
<summary>Show hint</summary>

- **Where:** [AJAX](../2.2-advanced-react/2.2.1-ajax.md) — asynchronous requests.
- **Think:** The key idea is that the result is not ready right away, so JavaScript uses a placeholder object to track what will happen later.

</details>

**Q4.** How do you handle errors in Promises?

- Using .catch() method
- Using .then() method
- Using .finally() method
- Errors can not be handled

<details>
<summary>Show hint</summary>

- **Where:** [AJAX](../2.2-advanced-react/2.2.1-ajax.md) — handling async responses.
- **Think:** When a request fails, which promise method is specifically designed to react to that failure?

</details>

**Q5.** What does useContext hook provide in React?

- Access to state management
- Styling components
- Routing capabilities
- Access to context values

<details>
<summary>Show hint</summary>

- **Where:** [useContext](../2.2-advanced-react/2.2.3-context.md) — reading shared values from context.
- **Think:** The hook lets a component read data that has been made available from somewhere higher up in the tree.

</details>

**Q6.** The "Link" attribute creates a clickable link that points to the resources using the \_\_\_ attribute?

- url
- to
- path
- target

<details>
<summary>Show hint</summary>

- **Where:** [React Router](../2.2-advanced-react/2.2.2-react-router.md) — `Link` and route paths.
- **Think:** The `Link` component uses a prop that tells React Router which route to go to.

</details>

**Q7.** What hook can be used to change the current URL on the browser and switch to the referenced page?

- useLocation
- useParams
- useResolvedPath
- useNavigate

<details>
<summary>Show hint</summary>

- **Where:** [React Router](../2.2-advanced-react/2.2.2-react-router.md) — navigation hooks.
- **Think:** The hook name suggests it is used to move the user to a different page programmatically.

</details>

**Q8.** What is the purpose of useReducer hook?

- To handle complex state logic
- To provide context values
- To manage local component state
- To perform side effects

<details>
<summary>Show hint</summary>

- **Where:** [useReducer](../2.2-advanced-react/2.2.4-usereducer.md) — reducer-based state management.
- **Think:** This hook is useful when state updates depend on multiple related actions and are harder to manage with simple `useState`.

</details>

**Q9.** What are environmental variables used for?

- Project styling
- Routing configurations
- Managing component state
- Storing sensitive information like API keys

<details>
<summary>Show hint</summary>

- **Where:** [Environmental variables](../2.2-advanced-react/2.2.5-environmental-variables.md) — `.env` usage.
- **Think:** These values are commonly used to hide private credentials and config details from the codebase.

</details>

**Q10.** True or False. Memoization is used to speed up computer programs by eliminating the repetitive computation of results?

- True
- False

<details>
<summary>Show hint</summary>

- **Where:** [useMemo and useCallback](../2.2-advanced-react/2.2.6-react-usememo-usecallback.md) — memoization.
- **Think:** The idea is to save previous results so expensive work does not need to be repeated.

</details>

**Q11.** What does useMemo do in React?

- Fetches data from APIs
- Handles side effects
- Manages state updates
- Caches a value based on dependencies

<details>
<summary>Show hint</summary>

- **Where:** [useMemo and useCallback](../2.2-advanced-react/2.2.6-react-usememo-usecallback.md) — `useMemo`.
- **Think:** The hook is about remembering a computed value until the inputs that affect it change.

</details>

**Q12.** What is the syntax to create a blank React Native app?

- npx create-expo-app -template=blank app_name
- npx create-expo-app -template blank app_name
- npx create-react-native-app app_name
- npx create-expo-rn-app --template app_name

<details>
<summary>Show hint</summary>

- **Where:** [React Native intro](../../react-native/1-intro-to-react-native/1-intro-to-react-native.md) — creating Expo apps.
- **Think:** The command starts with Expo tooling and uses the blank template option.

</details>

**Q13.** What React Native component allows for screen scrolling?

- ScrollBar
- Scroll
- View
- ScrollView

<details>
<summary>Show hint</summary>

- **Where:** [React Native components](../../react-native/2-react-native-components/1-rn-components.md) — layout and scrolling.
- **Think:** The component name itself points to the behavior: it gives the screen a scrollable area.

</details>

**Q14.** True or False. useContext and useReducer cannot be used together?

- True
- False

<details>
<summary>Show hint</summary>

- **Where:** [useContext](../2.2-advanced-react/2.2.3-context.md) and [useReducer](../2.2-advanced-react/2.2.4-usereducer.md) — state-sharing patterns.
- **Think:** These hooks solve different problems, so they are often used together rather than excluding each other.

</details>

**Q15.** True or False. The React Native Image tag need the dimensions specified for network images?

- True
- False

<details>
<summary>Show hint</summary>

- **Where:** [React Native components](../../react-native/2-react-native-components/1-rn-components.md) — images and sizing.
- **Think:** Remote images often need explicit size values so the layout knows how much space to reserve.

</details>

**Q16.** Which command is used to deploy an application to Firebase Hosting?

- firebase deploy
- firebase push
- firebase start
- firebase upload

<details>
<summary>Show hint</summary>

- **Where:** [Firebase hosting](../2.3-firebase/2.3.4-firebase-hosting.md) — deployment commands.
- **Think:** The command name should match the service you are trying to publish.

</details>

**Q17.** What type of database does Firebase use?

- NoSQL database
- SQL database
- Graph database
- Document database

<details>
<summary>Show hint</summary>

- **Where:** [Firebase realtime database](../2.3-firebase/2.3.1-firebase-realtime-database.md) — database model.
- **Think:** Firebase stores data in a JSON-like structure rather than in tables.

</details>

**Q18.** What does Firebase Realtime Database allow developers to do?

- Authenticate users
- Sync data in real-time across all clients connected to it
- Host web applications
- Store files securely

<details>
<summary>Show hint</summary>

- **Where:** [Firebase realtime database](../2.3-firebase/2.3.1-firebase-realtime-database.md) — real-time syncing.
- **Think:** The important phrase is that many connected clients can stay updated as changes happen.

</details>

**Q19.** What React Router element should be used in parent route elements to render their child route elements?

- Outlet
- Routes
- Route
- Link

<details>
<summary>Show hint</summary>

- **Where:** [React Router](../2.2-advanced-react/2.2.2-react-router.md) — nested routes and `Outlet`.
- **Think:** The element name is the one that acts like a placeholder where child routes are shown.

</details>

**Q20.** What will happen if you use `await` outside an `async` function?

- The code will run normally
- It will cause the system to wait indefinitely
- Syntax error
- It will create a new Promise

<details>
<summary>Show hint</summary>

- **Where:** [AJAX](../2.2-advanced-react/2.2.1-ajax.md) — async/await usage.
- **Think:** `await` only works correctly inside a function that is marked as asynchronous.

</details>
