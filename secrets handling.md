Secrets handling is the practice of storing, accessing, and using sensitive information securely in applications and pipelines.

Examples of secrets:

* passwords
* API keys
* database credentials
* SSH keys
* access tokens
* cloud credentials
* TLS private keys

## Why it matters

If secrets are exposed, attackers may get access to:

* production systems
* databases
* cloud accounts
* CI/CD pipelines
* internal APIs

So secrets should never be treated like normal config values.

## Good practices for secrets handling

### 1. Never hardcode secrets in code

Secrets should not be written directly in:

* source code
* Git repositories
* scripts
* Dockerfiles

Bad example:

```python
password = "admin123"
```

This is risky because it can be leaked through version control or logs.

---

### 2. Use a secret manager

Store secrets in dedicated systems such as:

* AWS Secrets Manager
* HashiCorp Vault
* Azure Key Vault
* GCP Secret Manager
* Kubernetes Secrets with proper controls

This is much safer than storing them in plain text files.

---

### 3. Inject secrets at runtime

Applications should receive secrets through:

* environment variables
* mounted secret files
* secret manager API calls
* CI/CD secret injection

This keeps them out of source code.

---

### 4. Restrict access using least privilege

Only the required users, services, or pipelines should have access to a secret.

For example:

* app A should not access app B’s database password
* dev environment should not have production secrets
* only specific CI jobs should read deployment keys

---

### 5. Rotate secrets regularly

Secrets should be changed periodically or immediately after suspected exposure.

Examples:

* rotate API keys
* rotate DB passwords
* rotate SSH keys
* rotate cloud access credentials

---

### 6. Avoid logging secrets

Secrets should never appear in:

* build logs
* app logs
* debug output
* exception traces

Always mask or redact them.

---

### 7. Use short-lived credentials when possible

Temporary credentials are safer than long-lived static ones.

Examples:

* IAM roles
* STS tokens
* workload identity
* temporary session tokens

These reduce risk if credentials are leaked.

---

### 8. Protect secrets in CI/CD

In pipelines:

* store secrets in CI secret store
* do not echo them in logs
* restrict them to required branches/environments
* separate dev and prod secrets
* use masked variables

---

### 9. Encrypt secrets at rest and in transit

Secrets should be:

* encrypted when stored
* encrypted when transmitted

That means:

* use TLS for transmission
* use encrypted secret storage

---

### 10. Scan for accidental secret leaks

Use tools to detect secrets in code repositories and pipelines.

Examples:

* GitHub secret scanning
* Gitleaks
* TruffleHog

This helps catch accidental commits.

---

## Real-world examples

### Application

Instead of hardcoding DB password:

* store it in Vault or Secrets Manager
* inject it as env var at runtime

### Kubernetes

Store secret securely and mount it into pods or expose as env vars, while controlling RBAC access carefully.

### CI/CD

Store deployment token in Jenkins credentials, GitHub Actions secrets, or GitLab CI variables instead of plain pipeline code.

---

## Common mistakes

* committing `.env` files to Git
* hardcoding credentials in scripts
* sharing secrets in chat or email
* printing tokens in logs
* using the same secret across all environments
* never rotating old credentials

---

## Interview-style answer

Secrets handling is the secure management of sensitive data such as passwords, API keys, access tokens, and private keys used by applications and pipelines. Best practices include never hardcoding secrets in source code, storing them in dedicated secret management systems, injecting them securely at runtime, restricting access with least privilege, rotating them regularly, masking them in logs, and using short-lived credentials whenever possible.

## Very short summary

Secrets handling means:

* store secrets securely
* never hardcode them
* inject them safely at runtime
* restrict access
* rotate regularly
* never expose them in logs
