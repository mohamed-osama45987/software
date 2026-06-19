# Assignment: HTTP Requests with Thunder Client and Axios

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

## Setup

1. Open VS Code and install the **Thunder Client** extension if you haven't already.
2. Create a new React app (Vite is fine: `npm create vite@latest http-basics -- --template react`), then `npm install axios`.

## Tasks

1. Inspect a real API with Thunder Client

   Open Thunder Client and send a GET request to:

   ```
   https://jsonplaceholder.typicode.com/users/3
   ```

   In a new file `notes.md` in your project root, write down:

   - The HTTP **method** and **status code** of the response
   - The `name`, `email`, and `city` (inside `address`) fields from the response body
   - One header from the response (any header — pick one and note its name and value)

2. Send the same request from React

   In `App.jsx`, use `useEffect` and `axios` to GET the same URL (`https://jsonplaceholder.typicode.com/users/3`) when the component mounts. Store the result in state with `useState`, and render the user's `name`, `email`, and city.

3. Handle a request that fails

   Add a second `useEffect`-driven request to a URL that **doesn't exist**, e.g. `https://jsonplaceholder.typicode.com/users/99999999`. Use `.catch` (or `try/catch` with `async`/`await`) to catch the error, and render a message like `"Could not load second user"` instead of crashing the page.

   In `notes.md`, note what status code this failing request returns, and how you found out (Network panel or Thunder Client).

4. POST request

   Add a button labelled "Create Post". When clicked, send a POST request to `https://jsonplaceholder.typicode.com/posts` with a JSON body `{ title: "My Post", body: "Hello world", userId: 3 }`. Log the response to the console, and render the returned `id` on the page (this is a fake API — it always echoes back a new `id`, but doesn't actually persist data).

## Deliverable

Submit your project folder (or a zipped version / GitHub link) containing `App.jsx` and `notes.md`.

## Hints

<details>
<summary>Show hints</summary>

## Task 1 — Thunder Client
- **Where:** [HTTP Requests and Responses](../2.1.2-http-requests-and-responses.md) — "Thunder Client".
- **Think:** Thunder Client's response view splits into Headers and Response (body) tabs — the body tab is JSON, the headers tab is a list of key-value pairs.

## Task 2 — fetching on mount
- **Where:** [AJAX](../2.2-advanced-react/2.2.1-ajax.md) — "AJAX in React".
- **Think:** The lesson explicitly warns: fetch in `useEffect`, not directly in the component body, "to avoid fetching data every time the component re-renders". Use an empty dependency array `[]` so it only runs once.
- **Starter:**
  ```jsx
  import { useState, useEffect } from "react";
  import axios from "axios";

  function App() {
    const [user, setUser] = useState(null);

    useEffect(() => {
      axios.get("https://jsonplaceholder.typicode.com/users/3")
        .then((response) => setUser(response.data))
        .catch((error) => console.error(error));
    }, []);

    // render user?.name, user?.email, user?.address?.city
  }
  ```

## Task 3 — handling failure
- **Where:** [AJAX](../2.2-advanced-react/2.2.1-ajax.md) — point 3 ("`res.json()` extracts the JSON...").
- **Think:** A second piece of state (e.g. `secondUserError`) can track whether this *specific* request failed, independently of the first. In `.catch`, set that error state instead of (or in addition to) logging.
- **Starter:**
  ```jsx
  const [secondUserError, setSecondUserError] = useState(false);

  useEffect(() => {
    axios.get("https://jsonplaceholder.typicode.com/users/99999999")
      .then((response) => { /* won't be hit for a 404 */ })
      .catch((error) => setSecondUserError(true));
  }, []);
  ```
  Check the Network panel (Chrome DevTools) for the actual status code — `jsonplaceholder` returns `404` for a missing resource, matching the status-code table from [HTTP Requests and Responses](../2.1.2-http-requests-and-responses.md).

## Task 4 — POST
- **Where:** [HTTP Requests and Responses](../2.1.2-http-requests-and-responses.md) — "Request Method" table (POST = "Create data").
- **Think:** `axios.post(url, bodyObject)` — the second argument is the request body, sent as JSON automatically. Define `handleCreatePost` as an `async` function attached to the button's `onClick`, separate from the `useEffect`s (since it should only run on click, not on mount).
- **Starter:**
  ```jsx
  const [newPostId, setNewPostId] = useState(null);

  const handleCreatePost = async () => {
    try {
      const response = await axios.post("https://jsonplaceholder.typicode.com/posts", {
        title: "My Post",
        body: "Hello world",
        userId: 3,
      });
      console.log(response.data);
      setNewPostId(response.data.id);
    } catch (error) {
      console.error(error);
    }
  };
  ```

## Common pitfalls
- Forgetting the empty `[]` dependency array on `useEffect`, causing infinite re-fetch loops.
- Accessing `user.name` before `user` is loaded (it starts as `null`) — use `user?.name` or check `if (!user) return <p>Loading...</p>` first.
- Mixing up `axios.get(url, data)` vs `axios.post(url, data)` — GET requests don't take a body as the second argument the same way.

</details>
