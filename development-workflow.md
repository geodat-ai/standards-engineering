# Geodat AI Development Workflow

This document defines the development workflow used across GeoDat AI repositories.

---

# Branching Strategy

The default branch is:

main

The main branch should always represent stable code.

New work should occur in short-lived branches.

Examples:

feature/add-routing-api  
feature/create-postgis-schema  
fix/api-timeout  
docs/update-readme

---

# Standard Workflow

1. Create a branch from main
2. Implement the change
3. Commit frequently
4. Push to GitHub
5. Open a pull request
6. Review changes
7. Merge to main

---

# Pull Requests

Pull requests should normally be used for:

infrastructure changes  
database schema updates  
API modifications  
container configuration updates  
client deliverables  
major refactoring

Even for solo work, pull requests provide useful history.

---

# Commit Messages

Commit messages should be concise and descriptive.

Examples:

Add PostGIS schema for routing service  
Create container build for Go API  
Fix OTP request timeout handling  
Update Shiny dashboard layout

Avoid vague messages.

---

# Container Development Workflow

Most GeoDat AI services run as containers.

Typical workflow:

1. Develop application code
2. Build container using Dockerfile
3. Test locally using Docker
4. Push code to GitHub
5. CI builds container image
6. Deploy container to runtime platform

---

# CI/CD with GitHub Actions

Every repository with a deployable container must have a GitHub Actions workflow that automates build and deploy on push to main.

Standard setup:

1. Create `.github/workflows/deploy.yml` (or per-component e.g. `deploy-frontend.yml`, `deploy-api.yml`)
2. Add `AZURE_CREDENTIALS` repository secret (service principal JSON from `az ad sp create-for-rbac --sdk-auth`)
3. Each project should have its own service principal scoped to `geodat-rg`

Standard workflow steps:

1. Checkout code
2. Azure login (`azure/login@v2` with `AZURE_CREDENTIALS` secret)
3. ACR login (`az acr login`)
4. Docker build and push (tag with commit SHA + latest)
5. Deploy to Container Apps (`az containerapp update`)

Path filtering:

Workflows should use `paths:` to only trigger on relevant file changes. For example a frontend workflow triggers on `frontend/**` changes only.

Reference implementations:

- GD001 (Farm Buildings): `.github/workflows/deploy.yml`
- GD004 (TreeMap Wales): `.github/workflows/deploy-frontend.yml`

Manual deploys (`az acr build` from a developer machine) are acceptable for emergencies only. Normal deployments must go through CI/CD.

Containers must always be built from version-controlled code.

---

# Repository Expectations

Each repository should normally contain:

README.md  
documentation  
environment configuration examples  
deployment instructions  
container configuration if applicable

---

Each repository should document:

- its purpose
- its primary access pattern
- how it is run locally
- how it is deployed
- any authentication or configuration requirements

---

# Guiding Principle

Code should be understandable, testable, and deployable.
