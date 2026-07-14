# MERN Stack Interview Guide

A curated question bank and task list for interviewing (or preparing as) a MERN stack candidate — React implementation tasks + Node/Express/MongoDB theory and coding questions.

---

## Table of Contents

- [Part 1 — React Implementation Tasks](#part-1--react-implementation-tasks)
- [Part 2 — Backend Interview Questions](#part-2--backend-interview-questions)

---

## Part 1 — React Implementation Tasks

| # | Task | Tests |
|---|------|-------|
| 1 | Pagination | State management, slicing arrays, edge cases |
| 2 | Custom hook — debounce & throttle | Custom hooks, `useEffect`/`useRef`, timing control |
| 3 | Todo list with time filter | Derived state, date filtering |
| 4 | List virtualization | Performance, DOM math, scroll handling |
| 5 | React Query | Data fetching, caching, server state |
| 6 | Retry API calls | Async control flow, error handling |
| 7 | File Explorer (VS Code–style) | Recursion, tree data, controlled expand/collapse |
| 8 | Nested Comments (Reddit-style) | Recursion, arbitrarily deep tree data |

---

### 1. Pagination

**Task:** Build a component that paginates a list of items (e.g. 100 dummy items) into pages of `N` items each.

**Requirements:**
- Prev / Next buttons
- Direct page number navigation
- Handle edge cases: first page, last page, out-of-range page number

---

### 2. Custom Hook — Debounce & Throttle

**Task:** Write two custom hooks: `useDebounce(value, delay)` and `useThrottle(value, limit)`.

**Requirements:**
- Use `useDebounce` in a search input so the filter/API call only fires after the user stops typing
- Use `useThrottle` to limit how often a scroll or resize handler runs

```js
// Expected usage
const debouncedSearch = useDebounce(searchTerm, 500);
const throttledScrollY = useThrottle(scrollY, 200);
```

---

### 3. Todo List with Time Filter

**Task:** Build a Todo app where every todo stores a `createdAt` timestamp.

**Requirements:**
- Filter view: `Today`, `This Week`, `This Month`, `All`
- Filtering must be derived from `createdAt`, not stored separately

---

### 4. List Virtualization

**Task:** Render a list of 10,000+ items without freezing the browser or bloating the DOM.

**Requirements:**
- Only visible rows (+ a small buffer) exist in the DOM at any time
- May use `react-window` / `react-virtualized`, or implement manually using scroll position + item height

---

### 5. React Query

**Task:** Refactor a component that fetches data with `useEffect` + `fetch` into one that uses React Query (`useQuery`).

**Requirements:**
- Demonstrate caching and background refetching
- Handle loading and error states explicitly

---

### 6. Retry API Calls

**Task:** Write a function or hook that retries a failed API call up to `N` times with exponential backoff before giving up and surfacing an error.

---

### 7. File Explorer (VS Code–style Sidebar)

**Task:** Build a recursive file/folder tree component.

**Requirements:**
- Nested folders (folders can contain folders and files)
- Expand / collapse per folder
- Recursive rendering — one `<Node />` component renders itself for children
- Clicking a file/folder logs its full path

**Example data:**

```json
{
  "name": "src",
  "type": "folder",
  "children": [
    { "name": "index.js", "type": "file" },
    {
      "name": "components",
      "type": "folder",
      "children": [
        { "name": "Navbar.jsx", "type": "file" },
        { "name": "Footer.jsx", "type": "file" }
      ]
    }
  ]
}
```

**Structure:**

```mermaid
graph TD
    A[📁 src] --> B[📄 index.js]
    A --> C[📁 components]
    C --> D[📄 Navbar.jsx]
    C --> E[📄 Footer.jsx]
    A --> F[📁 utils]
    F --> G[📄 helpers.js]
```

---

### 8. Nested Comments (Reddit-style)

**Task:** Build a comments component where any comment can have any number of replies, and replies can have their own replies — unlimited depth.

**Requirements:**
- Add a reply to any comment at any depth
- Indent each level visually

**Example data:**

```json
{
  "id": 1,
  "text": "This is the top-level comment",
  "replies": [
    {
      "id": 2,
      "text": "This is a reply",
      "replies": [
        { "id": 3, "text": "This is a reply to a reply", "replies": [] }
      ]
    }
  ]
}
```

**Structure:**

```mermaid
graph TD
    A["💬 Comment 1"] --> B["↳ Reply 2"]
    B --> C["↳ Reply 3"]
    A --> D["↳ Reply 4"]
```

---

## Part 2 — Backend Interview Questions

Focused on what actually matters for a **fresher backend interview**: can the candidate build APIs, reason about requests, debug problems, and explain their choices — not obscure framework internals.

### 1. Node.js Fundamentals

- What is Node.js, and why use it instead of browser JS?
- Is Node single-threaded? What is the Event Loop?
- Blocking vs non-blocking operations
- `npm`, `package.json`, `dependencies` vs `devDependencies`, `npx`
- CommonJS vs ES Modules — `require()` vs `import`
- What happens when you run `node index.js`?
- Why can Node handle thousands of concurrent requests?

### 2. Express.js

- What is Express, and why use it over the raw `http` module?
- Request-response cycle
- Routing basics; GET vs POST vs PUT vs PATCH vs DELETE
- What is middleware? Why `express.json()`? What breaks without it?
- `app.use()` vs `app.get()`
- How do multiple middlewares execute in sequence?
- What is `next()`? When do you call it? Can middleware stop the chain?
- Route-level vs global middleware

### 3. REST APIs

- What makes an API "RESTful"? What's an endpoint? What is CRUD?
- Which HTTP method for create / update / delete?
- Why shouldn't GET modify data? What should a POST response return?

> **Scenario:** A user refreshes the page right after a POST request. What should happen, and why?

### 4. Request & Response Objects

- `req.body`, `req.params`, `req.query`, `req.headers`, `req.method`, `req.url`
- `res.send()` vs `res.json()` vs `res.status()` vs `res.end()`

> **Implementation:** What's the difference between `/users/5` and `/users?id=5`? When would you use each?

### 5. Middleware

- Why is middleware useful? Can multiple middlewares run per request?
- What happens if `next()` is never called?
- Authentication middleware vs logging middleware — how do they differ?

> **Implementation:** Write middleware that logs `METHOD /path` for every incoming request.

### 6. CORS

- What is CORS, and why does it exist?
- Why does a request work in Postman but fail in the browser?
- What is `Origin`? What breaks if CORS middleware isn't configured?

### 7. MongoDB

- MongoDB basics: collections, documents, BSON
- SQL vs MongoDB — when would you pick each?
- `insertOne`, `find`, `findOne`, `updateOne`, `deleteOne`
- `find()` vs `findOne()`; `updateOne()` vs `replaceOne()`

### 8. Mongoose

- Why use Mongoose over the native MongoDB driver?
- Schema vs Model — what's the difference?
- Why define validation at the schema level?

> **Code reading:**
> ```js
> const userSchema = new mongoose.Schema({
>   name: String,
>   age: Number
> });
> ```
> What is this doing, and what happens if you save a document that violates it?

### 9. Validation

- Why validate on the backend if the frontend already validates?
- Required fields, min/max length, custom validators

> **Scenario:** The frontend fails to validate a user's age. Should the backend trust it? Why or why not?

### 10. Authentication & Authorization

- Authentication vs Authorization — what's the difference?
- What is a JWT? Why use it? Where should a token be stored on the client?
- Describe a basic login flow end to end.

### 11. Password Security

- Why can't passwords be stored as plain text?
- Hashing vs encryption — why hash, not encrypt, passwords?
- What is bcrypt, and how does it help?

### 12. Environment Variables

- Why use `.env` files? What typically goes inside one?
- Why should API keys/secrets never be committed to GitHub?
- How do you access env variables in Node?

### 13. Error Handling

- How do you send error responses consistently?
- 400 vs 500 — who's at fault?
- Why wrap async code in try/catch (or use an async error wrapper)?

> **Scenario:** The database connection is down. What should the API return, and with what status code?

### 14. Async JavaScript

- Why `async/await` over raw callbacks?
- Promises vs callbacks
- Can `await` be used outside an `async` function?

### 15. HTTP Status Codes

Know the meaning of: `200, 201, 204, 400, 401, 403, 404, 409, 422, 500`

> **Scenarios:**
> - Wrong password → which status?
> - Missing auth token → which status?
> - Route doesn't exist → which status?

### 16. Project Structure

- How would you organize `controllers / routes / models / middleware / config / utils`?
- Why separate concerns this way instead of one big file?

### 17. Git

- `clone`, `pull`, `push`, `add`, `commit`, `branch`, `merge`

> **Scenario:** You committed to the wrong branch. Walk through how you'd fix it.

### 18. Debugging Questions

The candidate should *reason out loud*, not just recall an answer.

| Symptom | What should the candidate check? |
|---|---|
| `Cannot GET /users` | Route not registered, wrong method, typo in path |
| `req.body` is `undefined` | Missing `express.json()`, wrong `Content-Type` header |
| CORS error | Missing/misconfigured CORS middleware, origin mismatch |
| MongoDB connects but data isn't saving | Missing `await`, wrong collection/model, validation silently failing |
| Works in Postman, fails from frontend | CORS, different headers, missing credentials, base URL mismatch |
| Server hangs / loads forever | Response never sent, unresolved promise, missing `next()` |
| "Port already in use" | Previous process still running on that port |
| Unexpected 404 | Wrong route order, typo, missing route file import |

### 19. Project-Based Questions

- Walk me through your backend project.
- Why MongoDB (or SQL) for this project?
- Which API was hardest to build, and why?
- How did the frontend and backend communicate?
- Did you validate data? Where, and how?
- How did you structure your folders, and why?
- Did you deploy it? What would you improve now?

---

### Implementation / Coding Tasks

**Easy**

1. Build a Welcome API (`GET /` → welcome message)
2. Build a Calculator API (`add`, `subtract`, `multiply`, `divide` via query params)
3. Build an API returning the current date and time
4. `GET /users` returning a hardcoded list of dummy users
5. `POST /users` adding a user to an in-memory array
6. API to check if a number is even or odd
7. API to reverse a string
8. Palindrome-checker API
9. Factorial API
10. API returning a number's multiplication table

**Intermediate**

11. Full CRUD on an in-memory array
12. Full CRUD using MongoDB
13. Search users by name via query parameters
14. Filter products by category
15. Sort products by price
16. Paginate results
17. Validate incoming data before saving
18. Middleware that logs request method + URL
19. Auth middleware that checks for a dummy/static token
20. Return correct HTTP status codes for success/failure paths
21. Notes API (CRUD)
22. Student Management API
23. Todo API backed by MongoDB
24. Book Library API
25. Movie CRUD API
26. Login endpoint with hardcoded credentials that returns a JWT
27. Hash passwords before storing them (bcrypt)
28. Protect selected routes with JWT middleware
29. Upload a profile image using Multer
30. Centralized error-handling middleware for all routes

---

*Contributions welcome — open a PR to add more tasks or tighten existing ones.*
