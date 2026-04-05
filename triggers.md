In CI/CD, **triggers** are the events that start a pipeline automatically.

A trigger tells the system **when to run** the pipeline.

## Common CI/CD triggers

### 1. Code push

Pipeline starts when code is pushed to a branch.

Example:

* push to `main`
* push to `dev`

This is one of the most common triggers.

---

### 2. Pull request / Merge request

Pipeline starts when a PR or MR is created or updated.

Used to:

* run tests
* check build
* validate code before merge

Example:

* GitHub Pull Request
* GitLab Merge Request

---

### 3. Manual trigger

A user starts the pipeline manually.

Used when:

* deployment should happen only on demand
* production release needs approval
* special testing is needed

---

### 4. Scheduled trigger

Pipeline runs at a fixed time.

Examples:

* every night
* every hour
* every Sunday

Used for:

* nightly builds
* backups
* security scans
* cleanup jobs

---

### 5. Webhook trigger

An external system sends an event to start the pipeline.

Example:

* GitHub webhook triggers Jenkins
* Docker registry event triggers deployment

---

### 6. Tag trigger

Pipeline starts when a Git tag is created.

Used for:

* release builds
* production versioning

Example:

* tag `v1.0.0`
* tag `release-2026-04`

---

### 7. Upstream/Dependent pipeline trigger

One pipeline starts another after finishing.

Example:

* build pipeline finishes
* then deploy pipeline starts

This is common in multi-stage delivery workflows.

---

### 8. API trigger

Pipeline is started using API call.

Used for:

* automation
* external tools
* orchestrated workflows

---

## Real-world examples

* Developer pushes code → build and test pipeline starts
* PR opened → validation pipeline starts
* Tag created → release pipeline starts
* Nightly schedule → regression tests run
* Manual click → production deployment starts

---

## Interview-style answer

Triggers are the events or conditions that start a CI/CD pipeline. Common triggers include code pushes, pull requests, merge requests, manual execution, scheduled runs, tag creation, webhooks, and API calls. They help automate build, test, and deployment workflows whenever relevant changes or events occur.

## Very short summary

**Triggers = events that start pipeline**

Common triggers:

* push
* pull request
* manual
* schedule
* tag
* webhook
* API

