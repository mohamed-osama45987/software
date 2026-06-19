# Module 4 Assessment

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

**Mandatory** • 20 questions • Covers concepts for the DevOps lessons.

Try each question closed-book first. Click **Show hint** if you get stuck — hints point you at the relevant lesson section and how to think about it, without naming the answer.

---

**Q1.** Which comprises DevOps?

- Processes
- Tools
- Mindset
- All of the above

<details>
<summary>Show hint</summary>

- **Where:** [Intro to DevOps](../devops/intro-to-devops.md) — what DevOps includes.
- **Think:** DevOps is not just tools; it combines culture, process, and practices.

</details>

**Q2.** Which of the following is NOT a phase in DevOps?

- CICD
- Financial Reporting
- Planning
- Code and Build

<details>
<summary>Show hint</summary>

- **Where:** [Intro to DevOps](../devops/intro-to-devops.md) — DevOps phases.
- **Think:** The phases are about delivery and operations, not accounting work.

</details>

**Q3.** Which is NOT part of the Scrum Values?

- Focus
- Courage
- Openness
- Fortitude

<details>
<summary>Show hint</summary>

- **Where:** [Agile and Scrum](../devops/scrum.md) — Scrum values.
- **Think:** The official Scrum values are commitment, focus, openness, respect, and courage.

</details>

**Q4.** Which part of the Scrum team is responsible for maximizing the value of the product of the Scrum Team?

- Scrum Master
- Product Owner
- Development Team
- Stakeholders

<details>
<summary>Show hint</summary>

- **Where:** [Agile and Scrum](../devops/scrum.md) — Scrum roles.
- **Think:** This role is the one who owns the product vision and prioritization.

</details>

**Q5.** Which Sprint event deals with discussing what went well, what didn't go well, and how to improve the next Sprint?

- Sprint Review
- Sprint Retrospective
- Daily Scrum
- Sprint Planning

<details>
<summary>Show hint</summary>

- **Where:** [Agile and Scrum](../devops/scrum.md) — Sprint events.
- **Think:** The name of this meeting signals looking back and improving the process.

</details>

**Q6.** Which is NOT part of the branches in GitFlow?

- feature
- main
- develop
- None of the above

<details>
<summary>Show hint</summary>

- **Where:** [Branching strategies](../devops/branching-strategies.md) — GitFlow branches.
- **Think:** `feature`, `main`, and `develop` are all part of the common GitFlow model.

</details>

**Q7.** Which is not a benefit of branching strategies?

- Organize a series of planned, structured releases
- Map a clear path when making changes to code
- Incur costs per new branch
- Proper coordination among developers

<details>
<summary>Show hint</summary>

- **Where:** [Branching strategies](../devops/branching-strategies.md) — pros and cons.
- **Think:** This one is more of a tradeoff or downside than a benefit.

</details>

**Q8.** Which best describe a container?

- Packages of code with dependencies and libraries
- Set of dependencies needed to run an application
- Hosted web service
- Virtual machine

<details>
<summary>Show hint</summary>

- **Where:** [Containerization local](../containers/container-local.md) — container basics.
- **Think:** A container packages the app together with the dependencies it needs.

</details>

**Q9.** Which can be considered a benefit of containerization?

- Agility
- Portability
- Scalability
- All of the above

<details>
<summary>Show hint</summary>

- **Where:** [Containerization local](../containers/container-local.md) — benefits of containers.
- **Think:** Containers help teams move faster and run the same app in different environments.

</details>

**Q10.** What is the command to create a docker image?

- docker create image
- docker build image
- docker image
- docker build

<details>
<summary>Show hint</summary>

- **Where:** [Containerization local](../containers/container-local.md) — Docker build steps.
- **Think:** The command name is the one used to build an image from a Dockerfile.

</details>

**Q11.** Given the following version 2.9.10 in Semantic versioning, what does the 2 stand for?

- Major version
- Minor version
- Hotfixes
- None of the above

<details>
<summary>Show hint</summary>

- **Where:** [Containerization remote](../containers/container-remote.md) — semantic versioning.
- **Think:** In `MAJOR.MINOR.PATCH`, the first number is the major version.

</details>

**Q12.** True or False, CircleCI is the only usable CICD pipeline available?

- True
- False

<details>
<summary>Show hint</summary>

- **Where:** [CI pipeline](../cicd/ci.md) — CI tools.
- **Think:** There are several CI/CD platforms, not just one.

</details>

**Q13.** Which of the following is part of the CI pipeline?

- Build
- Deploy
- Plan
- Bug fix

<details>
<summary>Show hint</summary>

- **Where:** [CI pipeline](../cicd/ci.md) — CI process.
- **Think:** CI focuses on verifying code by building and testing it.

</details>

**Q14.** True or False, the CD pipeline should only run after the CI pipeline successfully completes.

- True
- False

<details>
<summary>Show hint</summary>

- **Where:** [CD pipeline](../cicd/cd.md) — deployment flow.
- **Think:** CD usually happens after CI succeeds, because deployment should be based on passing checks.

</details>

**Q15.** True or False, the steps in CICD pipelines can be configured to run in parallel.

- True
- False

<details>
<summary>Show hint</summary>

- **Where:** [CI pipeline](../cicd/ci.md) and [CD pipeline](../cicd/cd.md) — pipeline workflows.
- **Think:** Pipelines can be structured so some jobs run at the same time.

</details>

**Q16.** True or False, Docker images are not always immutable.

- True
- False

<details>
<summary>Show hint</summary>

- **Where:** [Containerization local](../containers/container-local.md) — images and containers.
- **Think:** Images are intended to be fixed artifacts, though you can replace them with new versions.

</details>

**Q17.** Which of the follow can be considered a secret anti-pattern?

- storing passwords in plain text
- updating passwords every few months
- encrypting secrets
- using long and complicated passwords

<details>
<summary>Show hint</summary>

- **Where:** [Web security](../security/web-security.md) — secret management.
- **Think:** Secrets should never be stored in a readable, unsecured format.

</details>

**Q18.** True or False, vulnerabilities should always be immediately fixed.

- True
- False

<details>
<summary>Show hint</summary>

- **Where:** [Web security](../security/web-security.md) — vulnerability scanning.
- **Think:** Teams often prioritize fixes based on severity, impact, and available resources.

</details>

**Q19.** Which type of monitoring is concerned with the performance and security of network components?

- Site Monitoring
- Application Monitoring
- Infrastructure Monitoring
- Network Monitoring

<details>
<summary>Show hint</summary>

- **Where:** [Monitoring](../security/monitoring.md) — types of monitoring.
- **Think:** This monitoring area focuses on the health and behavior of network resources.

</details>

**Q20.** True or False, DevOps is the same as Agile.

- True
- False

<details>
<summary>Show hint</summary>

- **Where:** [Intro to DevOps](../devops/intro-to-devops.md) — DevOps vs Agile.
- **Think:** Agile is about delivery approach, while DevOps is about combining development and operations practices.

</details>
