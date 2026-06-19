# Assignment: SQL Fundamentals and One-to-Many Relationships

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

## Setup

1. Ensure PostgreSQL is running and you can connect via `psql` or DBeaver.
2. Create a new database called `library`:
   ```sql
   CREATE DATABASE library;
   ```
3. Connect to it (`\c library` in psql, or open it in DBeaver) before running the queries below.

## Tasks

1. Create tables

   Create two tables:

   - `authors`: `id` (serial primary key), `name` (varchar), `country` (varchar)
   - `books`: `id` (serial primary key), `title` (varchar), `year` (int), `author_id` (int, foreign key referencing `authors(id)`)

2. Insert data

   Insert at least 3 authors and at least 6 books, with books distributed across authors (some authors should have more than one book).

3. Basic queries and filtering

   Write queries to:

   - List all books published after the year 2000
   - List all books with "the" (case-insensitive) anywhere in the title
   - List all authors from a specific country of your choice

4. Joins

   Write a query that returns each book's `title`, `year`, and its author's `name`, using a `JOIN` between `books` and `authors`.

5. Aggregation

   Write a query that returns each author's `name` alongside the **count** of books they've written, ordered from most books to fewest. Include authors with zero books (think about which join type this requires).

6. Update and delete

   - Write an `UPDATE` query that changes one book's `year`.
   - Write a `DELETE` query that removes one book by `id`.
   - Note: order matters here if you're testing against live data — make sure your `UPDATE` runs before your `DELETE` removes the row you're updating, or pick different rows.

## Deliverable

Submit a single `.sql` file containing all queries from Tasks 1–6, in order, with comments above each query explaining what it does.

## Hints

<details>
<summary>Show hints</summary>

## Task 1 — table creation
- **Where:** [SQL README](../README.md) — "Creating a table", "SQL relationships".
- **Think:** `authors` has no dependencies, so create it first. `books.author_id` needs a `FOREIGN KEY` constraint referencing `authors(id)` — the lesson's `student_addresses` example shows the exact `CONSTRAINT ... FOREIGN KEY ... REFERENCES` syntax.
- **Starter:**
  ```sql
  CREATE TABLE authors (
      id SERIAL PRIMARY KEY,
      name VARCHAR(255),
      country VARCHAR(255)
  );

  CREATE TABLE books (
      id SERIAL PRIMARY KEY,
      title VARCHAR(255),
      year INT,
      author_id INT,
      CONSTRAINT fk_author_id
      FOREIGN KEY (author_id)
      REFERENCES authors(id)
  );
  ```

## Task 2 — inserting data
- **Where:** [SQL README](../README.md) — "Data Insertion".
- **Think:** Insert into `authors` **first** and note their generated `id`s (or query `SELECT * FROM authors` after inserting) — `books.author_id` must reference real `authors.id` values, since the foreign key constraint will reject anything else. The lesson shows the multi-row `INSERT ... VALUES (...), (...), (...)` syntax.
- **Starter:**
  ```sql
  INSERT INTO authors (name, country) VALUES
    ('Author One', 'UK'),
    ('Author Two', 'USA'),
    ('Author Three', 'Japan');

  -- check generated ids
  SELECT * FROM authors;

  -- then insert books with matching author_id values
  ```

## Task 3 — filtering
- **Where:** [SQL README](../README.md) — "Data Querying" (the `SELECT ... WHERE` examples).
- **Think:**
  - **After 2000:** `WHERE year > 2000`.
  - **"the" in title, case-insensitive:** Postgres's `ILIKE` is case-insensitive `LIKE` — `WHERE title ILIKE '%the%'`.
  - **Authors from a country:** `WHERE country = 'Japan'` (or whichever country you used).

## Task 4 — joins
- **Where:** [SQL README](../README.md) — "SQL relationships", final `JOIN` example.
- **Think:** The lesson's example joins `students` and `student_addresses` `ON students.id = student_addresses.student_id`. Your join condition is the same shape: `books.author_id = authors.id`. Select `books.title, books.year, authors.name`.
- **Starter:**
  ```sql
  SELECT books.title, books.year, authors.name
  FROM books
  JOIN authors ON books.author_id = authors.id;
  ```

## Task 5 — aggregation with zero-book authors
- **Where:** [1-M Relationships](../3.2.1-sql-1-m-relationships.md) — "Querying related data using SQL".
- **Think:** A plain `JOIN` (inner join) drops authors with no matching books entirely. To **keep** authors with zero books, you need a `LEFT JOIN` from `authors` to `books` — then `COUNT(books.id)` (not `COUNT(*)`) so that a `NULL` book row counts as `0`. `GROUP BY authors.id, authors.name` and `ORDER BY` the count descending.
- **Starter:**
  ```sql
  SELECT authors.name, COUNT(books.id) AS book_count
  FROM authors
  LEFT JOIN books ON books.author_id = authors.id
  GROUP BY authors.id, authors.name
  ORDER BY book_count DESC;
  ```

## Task 6 — update/delete
- **Where:** [SQL README](../README.md) — "To alter existing data within the tables you can use the UPDATE or DELETE commands".
- **Think:** Both follow the pattern `UPDATE table SET col = value WHERE id = ...` and `DELETE FROM table WHERE id = ...`. Always include a `WHERE` clause with a specific `id` — an `UPDATE`/`DELETE` without `WHERE` affects **every row**.

## Common pitfalls
- Inserting books before authors exist — the foreign key constraint will reject the `INSERT`.
- Using `COUNT(*)` instead of `COUNT(books.id)` in Task 5 — with a `LEFT JOIN`, `COUNT(*)` counts the joined row itself (always ≥1) even when `books.*` is all `NULL`, giving every author a count of at least 1.
- `LIKE` vs `ILIKE` — `LIKE` is case-sensitive in Postgres (unlike SQLite's default), so `'%The%'` with `LIKE` would miss `"the"`.
- Forgetting `WHERE` on `UPDATE`/`DELETE`, accidentally affecting all rows.

</details>
