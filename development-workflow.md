# GeoDat AI Development Workflow

This document defines the standard development workflow for repositories in the GeoDat AI GitHub organisation.

---

## Branching Strategy

The default branch is:

- `main`

This branch should always represent stable, usable work.

All new development should normally happen in short-lived branches.

Examples:

- `feature/add-otp-endpoint`
- `feature/create-postgis-schema`
- `fix/shiny-login-bug`
- `docs/update-readme`

---

## Standard Workflow

1. Create or update a branch from `main`.
2. Make small, logical changes.
3. Commit regularly with clear messages.
4. Push changes to GitHub.
5. Open a pull request for significant work.
6. Review changes before merging to `main`.

---

## Pull Requests

Pull requests should normally be used for:

- infrastructure changes
- schema changes
- production API changes
- important client deliverables
- major refactoring

Even for solo work, pull requests are encouraged because they provide a change history and review point.

---

## Commit Message Style

Commit messages should be short and clear.

Examples:

- `Add initial PostGIS schema`
- `Create Docker Compose for Shiny service`
- `Fix OTP request timeout handling`
- `Update client project README`

Avoid vague messages such as:

- `stuff`
- `changes`
- `update files`

---

## Main Branch Rules

The `main` branch should be treated as protected for important repositories.

Direct commits to `main` are acceptable during early setup for low-risk documentation repos, but production, infrastructure, and critical client repositories should move towards pull-request-based changes.

---

## Repository Setup Expectations

Each repository should normally include:

- a clear `README.md`
- a sensible folder structure
- configuration examples where relevant
- documentation for running or deploying the project
- a `.gitignore` appropriate to the technology

---

## Guiding Principle

Work should be easy to understand, easy to review, and easy to deploy.
