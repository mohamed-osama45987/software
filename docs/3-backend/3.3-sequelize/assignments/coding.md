# Assignment: Sequelize One-to-Many Relationships

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

## Setup

1. Create a new Node project, `npm install express sequelize pg pg-hstore sequelize-cli`, and add `"type": "module"` to `package.json`.
2. Initialise Sequelize with a `.sequelizerc` as covered in the Sequelize lessons, pointing config/models/migrations/seeders at sensible paths.
3. Create a database called `school` and configure `config/config.json` to connect to it.

## Tasks

Build a `Teacher` / `Course` 1-M relationship, where one teacher has many courses, and each course belongs to one teacher.

1. Generate models and migrations

   Use `sequelize model:generate` to create:

   - `Teacher` with fields `name` (string), `subject` (string)
   - `Course` with fields `title` (string), `credits` (integer), `teacherId` (integer)

   Run the migrations to create both tables.

2. Define associations

   In `models/teacher.js`, declare `this.hasMany(models.Course)` inside the `associate` static method. In `models/course.js`, declare `this.belongsTo(models.Teacher)`.

3. Seed data

   Write a seeder that creates 2 teachers and 4 courses, with courses split across the two teachers via `teacherId`.

4. Express routes using associations

   In a small Express app (`index.js`), implement:

   - `GET /teachers/:teacherId/courses` — returns all courses belonging to the given teacher, using the Sequelize association method (not a manual `where: { teacherId }` query)
   - `GET /teachers` — returns all teachers, each including their courses via **eager loading** (`include`)

5. Add a foreign key migration check

   In `notes.md`, explain (in your own words, 2–3 sentences) which table ended up with the `teacherId` foreign key column, and why — referencing what `hasMany` vs `belongsTo` each imply about where the foreign key lives.

## Deliverable

Submit your project folder (models, migrations, seeders, `index.js`, `notes.md`), or a GitHub repo link. Do not commit `node_modules`.

## Hints

<details>
<summary>Show hints</summary>

## Task 1 — generate models and migrations
- **Where:** [Sequelize README](../README.md) — "Migrations", "Model Basics".
- **Think:** `sequelize model:generate --name Teacher --attributes name:string,subject:string` creates both a model file and a migration. Run `--name Course --attributes title:string,credits:integer,teacherId:integer`. Then `npx sequelize db:migrate`.
- **Starter:**
  ```sh
  npx sequelize model:generate --name Teacher --attributes name:string,subject:string
  npx sequelize model:generate --name Course --attributes title:string,credits:integer,teacherId:integer
  npx sequelize db:migrate
  ```

## Task 2 — associations
- **Where:** [3.3.1 Sequelize 1-M Relationships](../3.3.1-sequelize-1-m-relationships.md) — "One-To-Many relationships (1-M)", point 2.
- **Think:** The lesson's exact pattern is `this.hasMany(models.Player)` from the "1" side's class, and `this.belongsTo(models.Team)` from the "M" side's class — both inside each model's `associate(models) { ... }` static method (generated automatically but usually empty by default).
- **Starter:**
  ```javascript
  // models/teacher.js, inside associate()
  static associate(models) {
    this.hasMany(models.Course);
  }

  // models/course.js, inside associate()
  static associate(models) {
    this.belongsTo(models.Teacher);
  }
  ```

## Task 3 — seeders
- **Where:** [Sequelize README](../README.md) — "Seeders", `bulkCreate`.
- **Think:** `npx sequelize seed:generate --name demo-teachers-courses` gives you a file with `up`/`down` functions. Use `queryInterface.bulkInsert` for raw rows (seeders work at the SQL level, not the model level) — include `created_at`/`updated_at` timestamps if your migration requires `allowNull: false` on them.
- **Starter:**
  ```javascript
  // in the seeder's up function
  await queryInterface.bulkInsert("Teachers", [
    { name: "Ms. Lee", subject: "Math", created_at: new Date(), updated_at: new Date() },
    { name: "Mr. Tan", subject: "Science", created_at: new Date(), updated_at: new Date() },
  ]);
  // then bulkInsert into "Courses", with teacherId 1 or 2 matching the rows above
  ```

## Task 4 — routes using associations
- **Where:** [3.3.1 Sequelize 1-M Relationships](../3.3.1-sequelize-1-m-relationships.md) — "Basics of queries involving associations" (mentions "special methods/mixins" like `getShip()`).
- **Think:** Because `Teacher.hasMany(Course)`, Sequelize auto-generates a `getCourses()` method on **instances** of `Teacher`. Find the teacher first with `findByPk`, then call `.getCourses()` on that instance. For eager loading, `Teacher.findAll({ include: Course })` joins and nests `Courses` inside each teacher object in one query.
- **Starter:**
  ```javascript
  app.get("/teachers/:teacherId/courses", async (req, res) => {
    const teacher = await Teacher.findByPk(req.params.teacherId);
    if (!teacher) return res.status(404).json({ error: true, msg: "Teacher not found" });
    const courses = await teacher.getCourses();
    res.json(courses);
  });

  app.get("/teachers", async (req, res) => {
    const teachers = await Teacher.findAll({ include: Course });
    res.json(teachers);
  });
  ```

## Task 5 — foreign key location
- **Where:** [3.3.1 Sequelize 1-M Relationships](../3.3.1-sequelize-1-m-relationships.md) — "Defining the Sequelize associations", point 4 ("Note in which table Sequelize expects the foreign key to be for each association").
- **Think:** You generated `Course` with `teacherId` as one of its own attributes in Task 1 — that's not a coincidence. Connect this to the lesson's statement about which side (`hasMany` vs `belongsTo`) "owns" the foreign key.

## Common pitfalls
- Forgetting to run `db:migrate` after generating models — the tables won't exist yet.
- Defining `hasMany`/`belongsTo` in only **one** of the two models — both calls are needed (the lesson states this explicitly) for the relationship methods to appear on both sides.
- Seeder `bulkInsert` table names are typically the **pluralised, capitalised** model name (`Teachers`, `Courses`) by Sequelize's default conventions — double-check against what your migration actually created.
- Calling `teacher.getCourses()` on the *class* `Teacher` instead of an *instance* (`findByPk` result) — the mixin methods are on instances.

</details>
