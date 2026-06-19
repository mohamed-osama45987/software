# Assignment: JWT Authentication (Sign Up, Log In, Protected Routes)

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

## Setup

1. Create a new Express project. `npm install express bcrypt jsonwebtoken cors dotenv`, add `"type": "module"` to `package.json`.
2. Create a `.env` file with `JWT_SECRET=<any long random string>` and `JWT_EXPIRES_IN=1h`. **Do not commit `.env`** — add it to `.gitignore`.
3. For this assignment, store users in an **in-memory array** (no database setup required) — focus is on the auth logic itself, not Sequelize.

## Tasks

1. `POST /signup`

   Accepts `{ email, password }` in `req.body`. Validate both fields are present (respond `400` if not). Check whether a user with that `email` already exists in your in-memory array (respond `400` if so). Hash the password with `bcrypt` before storing the user object `{ id, email, password: hashedPassword }`.

2. Sign a JWT on signup

   After creating the user, sign a JWT containing `{ id, email }` as the payload, using `JWT_SECRET` and `JWT_EXPIRES_IN` from `.env`. Respond with `{ success: true, data: { user: { id, email }, accessToken } }` — **never** include the hashed password in the response.

3. `POST /login`

   Accepts `{ email, password }`. Find the user by `email` (respond `401` with a generic message if not found — don't reveal whether the email exists). Use `bcrypt.compare` to check the password against the stored hash (respond `401` if it doesn't match). On success, sign and return a new JWT exactly as in Task 2.

4. JWT verification middleware

   Write a middleware function `jwtAuth` that reads the `Authorization` header, expects the format `Bearer <token>`, verifies it with `jwt.verify` and `JWT_SECRET`, and attaches the decoded payload to `req.user`. Respond `401` if the header is missing/malformed, and `403` if `jwt.verify` throws (invalid/expired token).

5. Protected route

   Add `GET /profile`, protected by `jwtAuth`, that responds with `{ id: req.user.id, email: req.user.email }`. Test it with Thunder Client: first call `/signup` or `/login` to get a token, then call `/profile` with `Authorization: Bearer <token>` — and without the header, to confirm you get `401`.

## Deliverable

Submit `index.js`, `middleware/jwtAuth.js`, `package.json`, and `.env.example` (a template `.env` with placeholder values — **not** your real secret). Include a short `notes.md` describing what happens (and what status code you get) when you call `/profile` with: no header, a malformed header, and a deliberately-edited (tampered) token.

## Hints

<details>
<summary>Show hints</summary>

## Task 1 — signup validation and hashing
- **Where:** [3.4.1 JWT App](../3.4.1-jwt-app.md) — "Backend Implementation", `signUp` example.
- **Think:** The lesson's `signUp` checks all required fields are present, then checks `findOne({ where: { email } })` — your in-memory equivalent is `users.find(u => u.email === email)`. `bcrypt.hash(password, saltRounds)` is `async` — `await` it. A reasonable `saltRounds` is `10`.
- **Starter:**
  ```javascript
  import bcrypt from "bcrypt";

  const SALT_ROUNDS = 10;
  let users = [];
  let nextId = 1;

  app.post("/signup", async (req, res) => {
    const { email, password } = req.body;
    if (!email || !password) {
      return res.status(400).json({ error: true, msg: "Email and password required" });
    }
    const existingUser = users.find((u) => u.email === email);
    if (existingUser) {
      return res.status(400).json({ error: true, msg: "Account already exists" });
    }
    const hashedPassword = await bcrypt.hash(password, SALT_ROUNDS);
    const newUser = { id: nextId++, email, password: hashedPassword };
    users.push(newUser);
    // continue in Task 2: sign token, respond
  });
  ```

## Task 2 — signing the JWT
- **Where:** [3.4.1 JWT App](../3.4.1-jwt-app.md) — `newAuthToken` example.
- **Think:** `jwt.sign(payload, secretKey, { expiresIn })`. The payload should be the **minimal** info you need to identify the user later (`id`, `email`) — never the password, hashed or not.
- **Starter:**
  ```javascript
  import jwt from "jsonwebtoken";

  const generateAuthToken = (payload) => {
    return jwt.sign(payload, process.env.JWT_SECRET, {
      expiresIn: process.env.JWT_EXPIRES_IN,
    });
  };

  // back in /signup, after creating newUser:
  const payload = { id: newUser.id, email: newUser.email };
  const accessToken = generateAuthToken(payload);
  return res.status(200).json({
    success: true,
    data: { user: { id: newUser.id, email: newUser.email }, accessToken },
  });
  ```

## Task 3 — login
- **Where:** [3.4.1 JWT App](../3.4.1-jwt-app.md) — Introduction ("when the user signs up and logs in they will be granted a JWT token").
- **Think:** `bcrypt.compare(plainPassword, hashedPassword)` returns a promise resolving to `true`/`false` — `await` it. For both "user not found" and "wrong password", return the **same** generic `401` message and shape, so an attacker can't distinguish "no such account" from "wrong password" (this is a standard security practice, though not explicitly spelled out in the lesson — think about *why* it matters).
- **Starter:**
  ```javascript
  app.post("/login", async (req, res) => {
    const { email, password } = req.body;
    const user = users.find((u) => u.email === email);
    if (!user) {
      return res.status(401).json({ error: true, msg: "Invalid email or password" });
    }
    const passwordMatches = await bcrypt.compare(password, user.password);
    if (!passwordMatches) {
      return res.status(401).json({ error: true, msg: "Invalid email or password" });
    }
    // same token-signing logic as Task 2
  });
  ```

## Task 4 — `jwtAuth` middleware
- **Where:** [3.4.1 JWT App](../3.4.1-jwt-app.md) — `jwtAuth` middleware example.
- **Think:** `req.headers.authorization` is the full string `"Bearer <token>"` — `.split(" ")[1]` gets just the token. The lesson's example has a subtle bug worth noticing: it accesses `.split(" ")[1]` *before* checking if `req.headers.authorization` exists at all — if the header is **completely missing**, `req.headers.authorization` is `undefined`, and calling `.split` on `undefined` throws a *different* error than the one the `if` block is trying to catch. Guard against the header being missing **first**.
- **Starter:**
  ```javascript
  const jwtAuth = (req, res, next) => {
    const authHeader = req.headers.authorization;
    if (!authHeader || !authHeader.startsWith("Bearer ")) {
      return res.status(401).json({ error: true, msg: "Missing or invalid access token" });
    }
    const accessToken = authHeader.split(" ")[1];
    try {
      const user = jwt.verify(accessToken, process.env.JWT_SECRET);
      req.user = user;
      next();
    } catch (error) {
      return res.status(403).json({ error: true, msg: "Unauthorised: invalid token" });
    }
  };

  export default jwtAuth;
  ```

## Task 5 — protected route
- **Where:** [3.4.1 JWT App](../3.4.1-jwt-app.md) — "Authorise access to protected routes" (concept), point 6.
- **Think:** Insert `jwtAuth` as a second argument to `app.get` — Express runs it as middleware *before* your route handler. Inside the handler, `req.user` is whatever you attached in Task 4 (the decoded JWT payload — `{ id, email, iat, exp }`).
- **Starter:**
  ```javascript
  app.get("/profile", jwtAuth, (req, res) => {
    res.json({ id: req.user.id, email: req.user.email });
  });
  ```

## Common pitfalls
- Storing the **plain** password instead of the bcrypt hash — or accidentally including the hash in API responses.
- `bcrypt.hash` and `bcrypt.compare` are async — forgetting `await` means you're comparing against a Promise object, not a boolean/string.
- Different error messages for "user not found" vs "wrong password" on `/login` — a minor info leak.
- In `jwtAuth`, accessing `.split(" ")` on a possibly-`undefined` header before checking it exists.
- Forgetting `app.use(express.json())`, so `req.body` is `undefined` on `/signup` and `/login`.

</details>
