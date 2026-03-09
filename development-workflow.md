# GeoDat AI Development Workflow

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

# Guiding Principle

Code should be understandable, testable, and deployable.
