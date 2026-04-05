Environment promotion is the process of moving the **same tested build artifact** through multiple environments in a controlled order.

Typical order is:

```text
Dev → Test / QA → Staging → Production
```

## What it means

A build is created once, then promoted step by step after validation.

So instead of rebuilding the code separately for every environment, we:

1. build once
2. test it in a lower environment
3. promote the same artifact to the next environment
4. finally release it to production

This improves consistency and reduces risk.

## Why it is important

Environment promotion helps ensure that:

* the exact same artifact is used across environments
* testing is done before production
* releases are controlled and traceable
* rollback and auditing are easier

If you rebuild separately in each environment, the binary or image may differ, which can create unpredictable issues.

## Example

Suppose a pipeline builds Docker image:

```text
myapp:1.2.0
```

Flow:

1. image is built once
2. deployed to dev
3. after tests pass, promoted to QA
4. after approval, promoted to staging
5. finally promoted to production

The artifact stays the same. Only the target environment changes.

## Common environments

### Dev

Used by developers for early testing.

### QA / Test

Used for formal testing and validation.

### Staging

Production-like environment for final checks.

### Production

Live environment used by real users.

## Promotion criteria

An artifact is usually promoted only if certain checks pass, such as:

* build success
* unit tests pass
* integration tests pass
* security scans pass
* approval gate completed
* smoke tests pass

## Manual vs automatic promotion

### Automatic promotion

Artifact moves automatically when checks pass.

Used in fast CI/CD setups.

### Manual promotion

A person approves before moving to the next environment.

Used for:

* production releases
* regulated environments
* higher-risk deployments

## Interview-style answer

Environment promotion is the CI/CD practice of moving the same built and tested artifact through successive environments such as development, QA, staging, and production, instead of rebuilding it separately for each stage. This ensures consistency, improves traceability, reduces release risk, and helps validate the artifact progressively before it reaches production.

## Very short summary

Environment promotion means:

* build once
* test in lower environments
* move same artifact to higher environments
* finally release to production

