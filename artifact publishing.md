Artifact publishing is the process of storing the build output of a pipeline in a repository so it can be reused later for testing, deployment, or rollback.

An artifact can be:

* a `.jar` or `.war`
* a binary
* a zip package
* a Docker image
* a Helm chart

## Why it is needed

After a build succeeds, we usually do not want to rebuild the same code again for every environment.

Instead, we:

1. build once
2. publish the artifact
3. deploy the same artifact to dev, test, staging, and production

This ensures consistency and traceability.

## Common artifact repositories

Examples:

* JFrog Artifactory
* Nexus Repository
* AWS ECR for Docker images
* Docker Hub
* GitHub Packages
* GitLab Package Registry

## Simple flow

```text
Code → Build → Test → Package → Publish Artifact → Deploy
```

## What gets published

Depending on the application, published artifacts may include:

* Java package from Maven or Gradle
* Python package
* Node package
* Docker image
* compiled executable
* Terraform module package
* release bundle

## Benefits

### 1. Reusability

The same artifact can be deployed to multiple environments.

### 2. Consistency

You avoid rebuilding the code differently each time.

### 3. Traceability

You can track which build produced which artifact.

### 4. Rollback support

Older artifact versions can be redeployed if needed.

### 5. Faster deployments

Deployment stage pulls an already built artifact instead of building again.

## Example

Suppose a Java application is built in CI.

Pipeline stages:

1. checkout code
2. run unit tests
3. build `app.jar`
4. publish `app.jar` to Artifactory or Nexus
5. deployment pipeline pulls that exact `app.jar`

For containers:

1. build Docker image
2. tag it with version or commit SHA
3. push image to Docker registry
4. deploy that exact image

## Good practices

* version artifacts properly
* tag them with build number, commit SHA, or release version
* publish only after build and test pass
* avoid rebuilding the same commit multiple times for different environments
* keep metadata for traceability

## Interview-style answer

Artifact publishing is the CI/CD step where the packaged build output, such as a binary, JAR, ZIP, or Docker image, is uploaded to an artifact repository or registry after a successful build. This allows the same tested artifact to be reused across environments, improves consistency, supports rollback, and provides versioning and traceability in the release process.

## Very short summary

Artifact publishing means:

* store build output in a repository
* reuse the same artifact later
* helps in deployment, rollback, and version tracking

