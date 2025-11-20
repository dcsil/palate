# ADR-030: Continuous Integration and Deployment (CI/CD) for Microservices

**Status**  
Accepted — 2025-11-19  

## Context

This is a part 2 of the microservice architecture testing. Refer to ADR-029. We are building multiple microservices and want a simple, consistent way to:

- Run tests on every change  
- Build Docker images  
- Deploy to our runtime platform in a repeatable, automated way  

Our current setup:

- Source control: Github
- Containerization: Docker
- Deployment target: Cloud Run

We want to avoid complex tooling and rely on managed, well-supported services.

## Decision

We will standardize on:

1. **CI/CD Tool**  
   - Use **GitHub Actions** as the primary CI/CD system because:
     - Our code is already on GitHub.
     - Good support for Docker and cloud providers.
     - Easy to version and share workflows per service.

2. **Build & Test Workflow (Per Service)**  
   On every **pull request** and **push to `main`**:

   1. Checkout repository.  
   2. Install dependencies for that service.  
   3. Run unit tests (and smoke tests where defined).  
   4. Build Docker image:
      - Tag format: `<service-name>:<git-sha>` and `<service-name>:latest` (for non-prod).

   If tests fail, the workflow fails and no deployment occurs.

3. **Deployment Workflow**  

   On **merge to `main`** (or on a tag like `v*` for releases):

   1. Build and push Docker image to our container registry:
      - GCR (Google Container Registry)
   2. Deploy the image to our runtime:
      - For Cloud Run: use `gcloud run deploy`.
   3. Use environment-specific configurations:
      - `dev` environment auto-deploys on every `main` merge.
      - `prod` environment deploys on tagged releases or a manual approval step.

4. **Secrets & Configuration**  
   - All credentials (cloud service accounts, registry tokens, etc.) will be stored as **GitHub Actions secrets**.  
   - No secrets in code or Docker images.  
   - Environment variables for services (DB URL, API keys, etc.) are managed at the runtime platform level, not hardcoded in CI.

## Consequences

**Positive**

- Single, consistent CI/CD pattern across all microservices.  
- Automated tests and builds on every change reduce regressions.  
- Deployments become repeatable and scriptable instead of manual.  
- GitHub Actions integrates tightly with our existing workflow.

**Negative**

- Initial time investment to set up workflows for each service.  
- CI/CD failures can block deployments if workflows are misconfigured.  
- We depend on GitHub Actions availability for our pipeline.

## Alternatives Considered

1. **Jenkins / self-hosted CI**  
   Rejected: more ops overhead; we prefer managed CI given our current size.

2. **CircleCI / GitLab CI**  
   Rejected for now: GitHub Actions is good enough and integrated with our repo.

3. **Manual deployment from local machines**  
   Rejected: inconsistent, error-prone, hard to audit.
