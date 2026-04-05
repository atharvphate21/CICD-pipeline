Branch-based workflows are the way teams use Git branches to organize development, testing, and releases.

They define:

* where developers write code
* how changes are reviewed
* when code is merged
* how releases are managed

## Simple idea

Instead of everyone working directly on one branch, developers create separate branches for their work.

Example flow:

```text
main → feature/login-page → merge back to main
```

This helps teams work safely without breaking stable code.

---

## Common branch types

### 1. Main or master

This is usually the stable production branch.

It should contain:

* tested code
* deployable code
* approved changes

### 2. Develop

Used in some workflows as an integration branch.

Developers merge features here first, then later move to production branch.

### 3. Feature branches

Created for new work.

Examples:

* `feature/login`
* `feature/payment-api`
* `bugfix/header-issue`

A developer works on the feature branch, pushes code, creates a pull request, and merges after review.

### 4. Release branches

Used to prepare a release.

Examples:

* `release/1.2.0`
* `release/april-2026`

These branches allow final testing and fixes before production.

### 5. Hotfix branches

Used for urgent production fixes.

Example:

* `hotfix/payment-timeout`

These are created from production branch and merged back quickly.

---

## Common branch-based workflow models

## 1. Feature branch workflow

This is the simplest and most common one.

### Flow

1. create branch from `main`
2. make changes
3. commit and push
4. open pull request
5. review and test
6. merge back to `main`

Example:

```text
main
 └── feature/user-auth
```

### Benefits

* isolated development
* easier code review
* safer collaboration

---

## 2. Git Flow

This is a more structured workflow.

Common branches:

* `main`
* `develop`
* `feature/*`
* `release/*`
* `hotfix/*`

### Flow

* feature branches come from `develop`
* release branches come from `develop`
* hotfix branches come from `main`
* production code stays in `main`

### Good for

* teams with scheduled releases
* projects needing strong release control

### Drawback

It can feel heavy for small fast-moving teams.

---

## 3. Trunk-based development

In this model, developers integrate small changes frequently into one main branch, often called `main` or trunk.

Feature branches are:

* very short-lived
* small
* merged quickly

### Benefits

* fast integration
* fewer long-lived merge conflicts
* good for CI/CD

### Good for

* teams deploying often
* mature engineering teams

---

## 4. Release branch workflow

Some teams mainly use:

* `main`
* short-lived feature branches
* release branches when needed

This is common when code is continuously developed, but releases are packaged separately.

---

## Example of branch-based workflow in practice

Suppose a team uses feature branches.

### Steps

1. `main` has stable code
2. developer creates:

```bash
git checkout -b feature/login-page
```

3. developer commits code
4. pushes branch:

```bash
git push origin feature/login-page
```

5. opens pull request
6. CI runs tests
7. reviewers approve
8. branch merges into `main`
9. feature branch is deleted

---

## Why branch-based workflows are useful

They help with:

* parallel development
* code review
* CI/CD automation
* release management
* production stability

Without branch strategy, teams can easily overwrite each other’s work or break stable code.

---

## Common best practices

* keep `main` stable
* use pull requests for review
* keep feature branches small
* merge frequently to avoid conflicts
* protect important branches
* run CI on every PR
* delete merged branches
* use clear branch naming

Example branch names:

* `feature/add-search`
* `bugfix/login-error`
* `hotfix/prod-crash`
* `release/2.0.1`

---

## Interview-style answer

Branch-based workflows are Git development strategies where teams use separate branches to manage features, fixes, releases, and production code safely. Common branch types include main, develop, feature, release, and hotfix branches. These workflows help teams isolate changes, enable code review, support CI/CD, and maintain stable production code. Popular models include feature branch workflow, Git Flow, and trunk-based development.

## Very short summary

Branch-based workflow means:

* developers work on separate branches
* changes are reviewed and tested
* then merged into stable branch

Common models:

* feature branch workflow
* Git Flow
* trunk-based development

