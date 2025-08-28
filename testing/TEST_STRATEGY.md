# [TEST STRATEGY] :: [Project Name]

**Date:** YYYY-MM-DD
**Owner:** QA & Test Engineer
**Status:** Accepted

## 1. Quality Principles
- **The Test Pyramid:** Our strategy is based on the test pyramid. We will have a broad base of fast, isolated **unit tests**, a smaller layer of **integration tests** to verify component interactions, and a highly focused set of **End-to-End (E2E) tests** for critical user journeys.
- **Shift-Left Testing:** We will integrate quality checks as early as possible in the development cycle. Automated tests will run on every commit, and security scanning will be part of the CI pipeline.
- **Automation First:** All repeatable test scenarios, especially regression tests, must be automated. Manual testing will be reserved for exploratory and usability testing.

## 2. Scope of Testing

| Test Type             | In Scope (Description)                                          | Out of Scope                               |
|-----------------------|-----------------------------------------------------------------|--------------------------------------------|
| **Unit Testing** | All business logic in individual functions/classes.             | Third-party library internals.             |
| **Integration Testing** | Interactions between our services (e.g., API to Database).      | Interactions with external, mocked APIs.   |
| **End-to-End (E2E)** | Critical user flows through the full application stack.         | Exhaustive testing of all edge cases.      |
| **Performance Testing** | Load and stress testing for key API endpoints.                  | Frontend rendering performance.            |
| **Security Testing** | Automated dependency scanning and static analysis (SAST).       | Manual penetration testing.                |

## 3. Tooling & Frameworks
- **Backend Unit/Integration:** `pytest`
- **Frontend E2E Testing:** `Cypress`
- **Performance/Load Testing:** `k6`
- **Security Scanning:** `trivy` (for container vulnerabilities), `semgrep` (for static code analysis)

## 4. Test Environments
- **Local:** Developers run unit and integration tests locally before committing.
- **CI/CD:** All tests are run automatically on every pull request.
- **Staging:** The `staging` environment is the primary target for running the full E2E and performance test suites against a deployed application.
- **Production:** A small suite of critical "smoke tests" will be run against the production environment after each deployment to verify core functionality.

## 5. Defect Management
- **Reporting:** Bugs are reported by creating a new task in `tasks.yml` with the `[BUG]` prefix.
- **Triage:** The Orchestrator, in consultation with the PM agent, will assign a severity (`Critical`, `High`, `Medium`, `Low`) to each bug.
- **Resolution:** Critical bugs must be addressed immediately. High-priority bugs will be scheduled into the next sprint.
