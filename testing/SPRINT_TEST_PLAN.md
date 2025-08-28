# [SPRINT TEST PLAN] :: [Sprint Name, e.g., Sprint 1 - User Registration]

**Date:** YYYY-MM-DD
**Owner:** QA & Test Engineer

## 1. Sprint Goal Alignment
This test plan supports the primary sprint goal as defined in the **[Sprint Plan](</path/to/sprint_plan.md>)**:
> *"A new user can successfully register an account, log in, and retrieve their user profile from a protected endpoint."*

## 2. Features Under Test
The following tasks from the `tasks.yml` are the primary focus for testing in this sprint:
- `TASK-002`: Implement the POST /register endpoint.
- `TASK-003`: Implement the POST /token endpoint.
- `TASK-004`: Implement the GET /users/me endpoint.

## 3. End-to-End (E2E) Test Scenarios
The following user journeys will be automated using Cypress and run against the `staging` environment.

### Scenario 1: Successful User Registration and Login
- **Given** a new user visits the application
- **When** they submit the registration form with valid credentials
- **Then** they should be successfully logged in
- **And** when they navigate to the profile page
- **Then** they should see their correct user information.

### Scenario 2: Attempted Access with Invalid Credentials
- **Given** a registered user
- **When** they attempt to log in with an incorrect password
- **Then** they should see a "Invalid credentials" error message
- **And** they should remain on the login page.

### Scenario 3: Unauthorized Access to Protected Route
- **Given** a user who is not logged in
- **When** they attempt to directly access the `/users/me` API endpoint
- **Then** the API should return a `401 Unauthorized` status code.

## 4. Performance Testing Scenarios
- **Target:** The `POST /token` endpoint.
- **Goal:** The endpoint must maintain an average response time of less than 200ms under a load of 50 virtual users for 1 minute.
- **Tool:** k6

## 5. Exploratory Testing Charter
- **Mission:** Attempt to break the user registration flow.
- **Areas to Explore:**
  - Submitting the form with invalid email formats.
  - Using special characters and scripts in the username and password fields.
  - Testing the flow on different screen sizes (mobile, tablet).

## 6. Success Criteria for This Sprint
- All automated E2E scenarios (Section 3) must pass in the `staging` environment.
- The performance test (Section 4) must meet its defined goal.
- No `Critical` or `High` severity bugs related to the "Features Under Test" are open at the end of the sprint.
