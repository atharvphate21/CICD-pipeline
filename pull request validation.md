Pull request validation is the set of automated and manual checks performed before a PR is merged.

Its purpose is to make sure the proposed change is safe, correct, and ready to integrate.

## What it usually includes

When a developer opens or updates a pull request, the CI system can automatically run validations such as:

* build check
* unit tests
* integration tests
* linting
* static code analysis
* security scanning
* formatting checks
* dependency checks

In addition to automation, there is usually code review by teammates.

## Simple flow

```text
Developer opens PR
→ CI pipeline runs validation
→ reviewers check code
→ issues are fixed if needed
→ PR is approved and merged
```

## Common pull request validation checks

### 1. Build validation

Confirms the code compiles or packages successfully.

Example:

* Maven build
* Gradle build
* npm build
* Docker build

### 2. Unit tests

Ensures core logic still works.

### 3. Linting / formatting

Checks code style and formatting rules.

Examples:

* flake8
* pylint
* eslint
* black
* prettier

### 4. Static analysis

Finds code quality issues, bad practices, bugs, or code smells.

Example:

* SonarQube

### 5. Security checks

Looks for vulnerabilities or secrets.

Examples:

* dependency scanning
* SAST
* secret scanning

### 6. Integration checks

Validates interaction with other components if required.

### 7. Branch policy checks

Examples:

* PR must be up to date with target branch
* minimum number of approvals required
* status checks must pass
* direct push to main not allowed

---

## Why PR validation is important

It helps:

* prevent broken code from reaching main branch
* catch bugs early
* enforce coding standards
* improve code quality
* reduce deployment failures
* make code review safer

---

## Real-world example

For a PR to `main`, validation might do this:

1. checkout PR code
2. install dependencies
3. run linting
4. run unit tests
5. run build
6. run SonarQube scan
7. report status back to GitHub/GitLab
8. allow merge only if all checks pass

---

## Interview-style answer

Pull request validation is the process of checking code changes before they are merged into the target branch. It typically includes automated checks such as build verification, linting, unit tests, integration tests, static code analysis, and security scanning, along with manual code review. The goal is to catch issues early, enforce quality standards, and ensure only stable and reviewed code is merged.

## Very short summary

PR validation means:

* run checks on pull request
* verify code quality and correctness
* block merge if checks fail

Common validations:

* build
* tests
* lint
* static analysis
* security scan
* code review

