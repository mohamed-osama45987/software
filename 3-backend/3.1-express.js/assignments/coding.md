# Assignment: Express CRUD API

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

## Setup

1. Create a new project folder, run `npm init -y`, then `npm install express cors`.
2. Add `"type": "module"` to your `package.json` so you can use `import` syntax.
3. Create an `index.js` file as your entry point.

## Tasks

Build an Express API for a simple in-memory `books` resource. Store books in an array of objects in memory (no database needed for this assignment), each with shape `{ id, title, author, year }`. Seed the array with 3 books on startup.

1. Basic server and CORS

   Set up an Express app that listens on port `3000`. Use `app.use(cors())` and `app.use(express.json())` (the latter lets you read JSON request bodies via `req.body`).

2. `GET /books` — list all

   Returns the full `books` array as JSON.

3. `GET /books/:bookId` — get one

   Returns the single book matching `:bookId`. If no book matches, respond with status `404` and `{ error: true, msg: "Book not found" }`.

4. `POST /books` — create

   Reads `title`, `author`, `year` from `req.body`, creates a new book with an auto-incrementing `id` (e.g. `Math.max(...books.map(b => b.id)) + 1`, or just track a counter), pushes it to `books`, and responds with the newly created book.

5. `PUT /books/:bookId` — update

   Finds the book matching `:bookId` and updates whichever of `title`, `author`, `year` are present in `req.body` (leave other fields unchanged). Responds with the updated book. If no book matches, respond `404` as in Task 3.

6. `DELETE /books/:bookId` — delete

   Removes the book matching `:bookId` from the array and responds with `{ success: true }`. If no book matches, respond `404`.

7. Logging middleware

   Add a custom middleware function (attached with `app.use`, **before** your routes) that logs the request method and URL for every incoming request, e.g. `GET /books`.

## Deliverable

Submit `index.js` (and `package.json`). Include a short `README.md` listing each route and an example `curl` or Thunder Client call for each.

## Hints

<details>
<summary>Show hints</summary>

## Task 1 — server setup
- **Where:** [Express.js README](../README.md) — "Basic Express App", "CORS".
- **Think:** The lesson's minimal example is `app.get("/", ...)` plus `app.listen(PORT, callback)`. `cors()` with no arguments is "the most open and least secure" config, which the lesson says is fine "to get our apps working" for now.
- **Starter:**
  ```javascript
  import express from "express";
  import cors from "cors";

  const PORT = 3000;
  const app = express();

  app.use(cors());
  app.use(express.json());

  let books = [
    { id: 1, title: "Book One", author: "Author A", year: 2001 },
    { id: 2, title: "Book Two", author: "Author B", year: 2010 },
    { id: 3, title: "Book Three", author: "Author C", year: 2020 },
  ];
  let nextId = 4;

  app.listen(PORT, () => console.log(`Listening on port ${PORT}`));
  ```

## Task 2 — `GET /books`
- **Where:** [Express.js README](../README.md) — "Routes".
- **Think:** This is the simplest possible route — no params, just send the whole array.
- **Starter:**
  ```javascript
  app.get("/books", (req, res) => {
    res.json(books);
  });
  ```

## Task 3 — `GET /books/:bookId`
- **Where:** [3.1.1 MVC](../3.1.1-mvc.md) — `getOne` method in `ProductsController`.
- **Think:** Route params arrive as strings on `req.params`. `find()` the matching book; if `find` returns `undefined`, that's your 404 case. Note: ids in your array are numbers, so compare with `==` or convert with `Number(req.params.bookId)`.
- **Starter:**
  ```javascript
  app.get("/books/:bookId", (req, res) => {
    const book = books.find((b) => b.id === Number(req.params.bookId));
    if (!book) {
      return res.status(404).json({ error: true, msg: "Book not found" });
    }
    res.json(book);
  });
  ```

## Task 4 — `POST /books`
- **Where:** [3.1.1 MVC](../3.1.1-mvc.md) — `insertOne` method in `ProductsController`.
- **Think:** `insertOne` destructures fields from `req.body` and builds a new object. You don't have a database `.create()` here — push to the array yourself, and remember `express.json()` from Task 1 is what makes `req.body` populated for POST requests.
- **Starter:**
  ```javascript
  app.post("/books", (req, res) => {
    const { title, author, year } = req.body;
    const newBook = { id: nextId, title, author, year };
    nextId += 1;
    books.push(newBook);
    res.json(newBook);
  });
  ```

## Task 5 — `PUT /books/:bookId`
- **Where:** [Express.js README](../README.md) — "Routes" (PUT = "Update data").
- **Think:** Find the book like in Task 3. Then for each of `title`, `author`, `year`, only overwrite if `req.body` actually contains that key — otherwise you'd wipe out existing fields with `undefined` when a partial update is sent. `Object.assign(book, req.body)` is one concise way, since `req.body` only contains the keys the client sent.
- **Starter:**
  ```javascript
  app.put("/books/:bookId", (req, res) => {
    const book = books.find((b) => b.id === Number(req.params.bookId));
    if (!book) {
      return res.status(404).json({ error: true, msg: "Book not found" });
    }
    Object.assign(book, req.body);
    res.json(book);
  });
  ```

## Task 6 — `DELETE /books/:bookId`
- **Where:** [Express.js README](../README.md) — "Routes" (DELETE = "Delete data").
- **Think:** `findIndex` instead of `find`, so you have a position to `splice` out. `-1` from `findIndex` is your "not found" signal here.
- **Starter:**
  ```javascript
  app.delete("/books/:bookId", (req, res) => {
    const index = books.findIndex((b) => b.id === Number(req.params.bookId));
    if (index === -1) {
      return res.status(404).json({ error: true, msg: "Book not found" });
    }
    books.splice(index, 1);
    res.json({ success: true });
  });
  ```

## Task 7 — logging middleware
- **Where:** [Express.js README](../README.md) — "Middleware", `myLogger` example.
- **Think:** The lesson's exact pattern — define a function `(req, res, next) => {...}`, call `console.log` using `req.method` and `req.url`, then call `next()`. It must be `app.use`'d **before** the routes, or it won't run for them.
- **Starter:**
  ```javascript
  app.use((req, res, next) => {
    console.log(`${req.method} ${req.url}`);
    next();
  });
  ```

## Common pitfalls
- Forgetting `next()` in the logging middleware — every request will hang forever.
- Forgetting `app.use(express.json())`, so `req.body` is `undefined` in POST/PUT.
- `req.params.bookId` is a **string** — comparing it to a numeric `id` with `===` without `Number(...)` will always be `false`.
- Registering the logging middleware *after* your routes — middleware order matters in Express.

</details>
