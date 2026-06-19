# Quiz: Continuous Integration & Continuous Deployment

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

Try each question closed-book first. Click **Show hint** if you get stuck — hints point you at the relevant lesson section and how to think about the question, without naming the answer.

## Questions

1. What does Continuous Integration (CI) mean?

- [ ] Automatically deploying code to production whenever it's pushed
- [ ] Automatically running tests whenever there are changes to code, and notifying engineers of failures
- [ ] Manually reviewing every pull request before merging
- [ ] Writing code comments automatically

<details>
<summary>Show hint</summary>

- **Where:** [Continuous Integration README](../README.md) — Learning Objectives / Introduction.
- **Think:** CI is about a *trigger* (a code change) and an *automatic reaction* (running something, then telling someone the result).

</details>

2. According to the lesson, what's the cost of skipping tests early in a product's life?

- [ ] There is no cost — skipping tests is always fine
- [ ] It may speed up development short-term but slow it down later as undetected bugs accumulate
- [ ] It immediately causes the app to crash
- [ ] It only affects the frontend, never the backend

<details>
<summary>Show hint</summary>

- **Where:** [Continuous Integration README](../README.md) — Introduction.
- **Think:** The lesson contrasts two timeframes — what happens "in the short term" vs "in the longer term"?

</details>

3. What does "CI/CD" refer to as a combined term?

- [ ] Two unrelated tools that are never used together
- [ ] Continuous Integration and Continuous Deployment, often using the same underlying tooling
- [ ] A single command that runs both tests and a database migration
- [ ] Continuous Improvement and Continuous Documentation

<details>
<summary>Show hint</summary>

- **Where:** [Continuous Integration README](../README.md) — Introduction.
- **Think:** The lesson explains *why* the two are "often referred to together" — what do they share?

</details>

4. In a GitHub Actions workflow YAML file, what does the `on:` key configure?

- [ ] The name of the Docker image to use
- [ ] The triggers (e.g. push or pull request to specific branches) that start the workflow
- [ ] The list of npm packages to install
- [ ] The final deployment URL

<details>
<summary>Show hint</summary>

- **Where:** [Continuous Integration README](../README.md) — "GitHub Actions", sample CI workflow YAML.
- **Think:** Read the sample workflow's `on:` block — it lists `push` and `pull_request` with `branches: [main]`. What category of configuration is that?

</details>

5. In the sample CI workflow, which command actually runs the project's test suite?

- [ ] `npm ci`
- [ ] `npm test`
- [ ] `npm install`
- [ ] `actions/checkout@v3`

<details>
<summary>Show hint</summary>

- **Where:** [Continuous Integration README](../README.md) — sample CI workflow YAML, `steps:`.
- **Think:** `npm ci` installs dependencies from the lockfile. Which *other* npm script in the steps list is the one that runs tests?

</details>

6. Where must a new GitHub Actions workflow file be placed in a repo for GitHub to recognise it?

- [ ] Anywhere in the repo root
- [ ] In a `.github/workflows` folder
- [ ] In a `ci/` folder
- [ ] Inside `node_modules`

<details>
<summary>Show hint</summary>

- **Where:** [Continuous Integration README](../README.md) — "GitHub Actions" section.
- **Think:** The lesson names this folder explicitly when describing how to create a new "workflow".

</details>

7. In the Fly.io continuous deployment setup, why is the `FLY_API_TOKEN` stored as a GitHub Actions secret rather than written directly into `fly.yml`?

- [ ] Secrets make the workflow run faster
- [ ] So the token isn't exposed in the repo's code, since `fly.yml` is committed to GitHub
- [ ] GitHub Actions doesn't support plain environment variables
- [ ] `fly.yml` doesn't support any variables at all

<details>
<summary>Show hint</summary>

- **Where:** [4.2.1 Continuous Deployment (Fly.io)](../4.2.1-continuous-deployment-fly.io.md) — "Setting up Continuous Deployment".
- **Think:** Anything committed to a (potentially public) GitHub repo is visible to anyone with access. What category of value should never go in a committed file?

</details>

8. Why does the Fly.io lesson say to remove the `[env]` block from `fly.toml` once secrets are set via `fly secrets set`?

- [ ] `fly.toml` doesn't support an `[env]` block
- [ ] Because `fly.toml` is pushed to GitHub, so secret values shouldn't live there in plain text
- [ ] Because `[env]` variables are slower to load
- [ ] It's purely a stylistic preference with no security implication

<details>
<summary>Show hint</summary>

- **Where:** [4.2.1 Continuous Deployment (Fly.io)](../4.2.1-continuous-deployment-fly.io.md) — "Pre-requisites → Setting up proper env variables".
- **Think:** Same underlying principle as the GitHub Actions secret question above — where is `fly.toml` going to end up, and what shouldn't be visible there?

</details>

9. In the CircleCI + Netlify setup described in the lesson, what role does the dedicated branch (e.g. `netlify-ignored-deployment`) play?

- [ ] It's the branch where all feature development happens
- [ ] It lets Netlify track a branch separate from `main` so two deployment processes don't run simultaneously
- [ ] It's required by CircleCI to store secrets
- [ ] It automatically deletes itself after each deploy

<details>
<summary>Show hint</summary>

- **Where:** [4.2.2 CircleCI](../4.2.2-circle-ci.md) — "Netlify Deployment".
- **Think:** The lesson explains this is to avoid running "two deployment processes simultaneously" — Netlify tracks one branch, CircleCI (eventually) tracks another (`main`).

</details>

10. In the CircleCI `config.yml` shown in the lesson, what is the purpose of the `restore_cache` / `save_cache` steps around `npm install`?

- [ ] To delete `node_modules` before every build
- [ ] To cache dependencies so future builds can reuse them instead of reinstalling from scratch
- [ ] To cache the deployed website's HTML
- [ ] To store test results permanently

<details>
<summary>Show hint</summary>

- **Where:** [4.2.2 CircleCI](../4.2.2-circle-ci.md) — `config.yml` listing.
- **Think:** The cache key includes a checksum of `package-lock.json`, and the cached path is `./node_modules`. What does caching *that specific folder, keyed on that specific file* let you skip on a future build where the lockfile hasn't changed?

</details>

11. After CircleCI builds and deploys via Netlify, what triggers a *new* deployment in this workflow?

- [ ] Manually clicking "Deploy" in the Netlify dashboard every time
- [ ] A push to the `main` branch, which CircleCI picks up and redeploys via Netlify
- [ ] Restarting the CircleCI account
- [ ] Editing the `README.md`

<details>
<summary>Show hint</summary>

- **Where:** [4.2.2 CircleCI](../4.2.2-circle-ci.md) — final paragraphs (the `Landing.js` / "Added with CircleCi" example).
- **Think:** The lesson walks through making a small code change and pushing it — what branch does it push to, and what happens "automatically" as a result?

</details>
