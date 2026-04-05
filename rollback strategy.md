A rollback strategy is the plan to return an application or deployment to the last known good version if the new release causes problems.

Its purpose is to reduce downtime and restore service quickly.

## Why it is needed

Even if testing is done, a new release can still cause:

* application errors
* failed deployments
* performance issues
* broken integrations
* database problems

A rollback strategy makes recovery fast and controlled.

## Basic idea

Instead of trying to fix production immediately, we:

1. detect the issue
2. stop or limit impact
3. restore the previous stable version
4. verify service health

## Common rollback strategies

### 1. Re-deploy previous version

This is the simplest method.

If version `v2` fails, deploy `v1` again.

Used when:

* artifacts are versioned
* deployment system can quickly redeploy older version

Example:

* previous Docker image tag
* previous `.jar`
* previous Helm release

---

### 2. Blue-green deployment rollback

In blue-green deployment, two environments exist:

* **blue** = current live version
* **green** = new version

Traffic is switched to the new environment only after validation.

If the new version fails, traffic is switched back to the old environment.

This is one of the safest rollback methods because the old version is still available.

---

### 3. Canary rollback

In canary deployment, the new version is released to a small percentage of users first.

If errors appear:

* stop rollout
* send traffic back to stable version
* remove canary version

This limits blast radius.

---

### 4. Rolling deployment rollback

In rolling deployment, instances are updated gradually.

If failure happens mid-rollout:

* stop further rollout
* replace updated bad instances with previous version

This is common in Kubernetes and VM-based deployments.

---

### 5. Feature flag rollback

Sometimes the issue is caused by a feature, not the entire deployment.

In that case:

* keep deployment
* disable the feature flag
* restore stable behavior without redeploying

This is very fast if the system supports feature toggles.

---

## Important parts of a good rollback strategy

### Versioned artifacts

You must have clearly versioned build outputs so you can go back to an exact release.

### Deployment history

You should know:

* what version is currently running
* what version ran previously
* what changed

### Fast recovery steps

Rollback should be documented and ideally automated.

### Health checks

After rollback, verify:

* app is up
* APIs respond correctly
* errors return to normal
* metrics stabilize

### Database considerations

Application rollback is easy compared to database rollback.

If schema changes are not backward compatible, rollback becomes risky.
So database migrations should be:

* backward compatible when possible
* planned carefully
* reversible if feasible

---

## Real-world example

Suppose version `v2.3` is deployed and starts giving 500 errors.

Rollback approach:

1. detect issue from monitoring and alerts
2. pause rollout
3. redeploy version `v2.2`
4. verify health endpoint, logs, and metrics
5. investigate `v2.3` separately

---

## Kubernetes example

In Kubernetes, rollback can be done with:

```bash
kubectl rollout undo deployment/my-app
```

This rolls the deployment back to the previous revision.

You can check rollout history with:

```bash
kubectl rollout history deployment/my-app
```

---

## Interview-style answer

A rollback strategy is a planned method to restore the last stable version of an application when a new deployment causes issues. Common rollback strategies include redeploying the previous version, switching traffic back in blue-green deployments, stopping and reversing canary rollouts, undoing rolling updates, or disabling features through feature flags. A good rollback strategy depends on versioned artifacts, deployment history, health checks, automation, and careful handling of database changes.

## Very short summary

Rollback strategy means:

* go back to last working version if release fails

Common methods:

* redeploy previous version
* blue-green switchback
* canary stop and revert
* rolling update undo
* disable feature flag
