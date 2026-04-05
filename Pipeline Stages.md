A CI/CD pipeline is usually divided into stages that move code from commit to production safely.

## Main stages

### 1. Source / Checkout

This is where the pipeline pulls the latest code from Git.

Typical actions:

* trigger on push, PR, or merge
* clone repository
* checkout branch or commit

---

### 2. Build

This stage converts source code into a runnable artifact.

Examples:

* compile Java code
* build binary
* create Docker image
* package application

Output can be:

* `.jar`
* `.war`
* binary
* Docker image
* zip package

---

### 3. Static checks / Lint / Code quality

This stage checks code quality before running it.

Examples:

* linting
* formatting checks
* static code analysis
* security scanning
* SonarQube checks

Goal:
catch issues early before build or deployment.

---

### 4. Unit testing

This stage runs small tests on individual functions or modules.

Purpose:

* validate code logic
* catch bugs early
* ensure new changes do not break existing logic

These tests are fast and usually run on every commit.

---

### 5. Integration testing

This stage checks whether multiple components work together.

Examples:

* app + database
* API + service
* service-to-service communication

This is broader than unit testing.

---

### 6. Artifact storage

Once build and tests pass, the pipeline stores the artifact in a repository.

Examples:

* JFrog Artifactory
* Nexus
* Docker Registry
* ECR / GCR / ACR

This ensures the same verified artifact is used later in deployment.

---

### 7. Deployment to lower environment

The application is deployed to environments like:

* dev
* test
* staging
* QA

Purpose:

* validate deployment logic
* test in environment closer to production
* allow QA or UAT

---

### 8. Acceptance / end-to-end testing

This stage validates the complete application flow.

Examples:

* UI tests
* API workflow tests
* business scenario tests

This checks whether the system works from end user perspective.

---

### 9. Approval / manual gate

In many pipelines, especially production ones, there is an approval step.

Examples:

* manager approval
* QA signoff
* change review
* CAB approval

This is common in enterprise environments.

---

### 10. Production deployment

The tested artifact is deployed to production.

Common deployment strategies:

* rolling deployment
* blue-green deployment
* canary deployment

Goal:
release safely with minimum downtime.

---

### 11. Post-deployment verification

After deployment, pipeline checks whether application is healthy.

Examples:

* health check endpoint
* smoke tests
* monitoring alerts
* log validation

This confirms deployment succeeded.

---

### 12. Rollback or recovery

If something fails, pipeline or team may:

* rollback to previous version
* scale down bad version
* restore known good release

This is an important part of mature CI/CD design.

---

## Simple pipeline flow

```text
Code Commit
→ Checkout
→ Build
→ Lint / Static Analysis
→ Unit Test
→ Integration Test
→ Package / Store Artifact
→ Deploy to Dev/Staging
→ Acceptance Test
→ Approval
→ Deploy to Production
→ Smoke Test / Monitor
```

---

## CI vs CD

### CI — Continuous Integration

Usually includes:

* code checkout
* build
* lint
* unit tests
* integration tests

Goal:
continuously validate code changes.

### CD — Continuous Delivery / Deployment

Usually includes:

* artifact packaging
* deployment
* environment promotion
* production release

Goal:
continuously deliver code safely.

---

## Real-world example

For a Java app:

1. developer pushes code
2. Jenkins/GitHub Actions checks out code
3. Maven builds `.jar`
4. SonarQube scans code
5. unit tests run
6. Docker image is built
7. image pushed to registry
8. deployed to staging on Kubernetes
9. smoke tests run
10. approval taken
11. deployed to production

---

## Interview-style answer

A CI/CD pipeline is typically divided into stages such as source checkout, build, code quality checks, unit testing, integration testing, artifact packaging, deployment to lower environments, acceptance testing, approval gates, production deployment, and post-deployment verification. CI focuses on integrating and validating code changes, while CD focuses on delivering and deploying tested artifacts safely across environments.

## Very short summary

Main CI/CD pipeline stages are:

* checkout
* build
* lint/static analysis
* unit test
* integration test
* package/store artifact
* deploy
* acceptance test
* production release
* monitor/rollback

