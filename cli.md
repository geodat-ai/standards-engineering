# Geodat AI Command Line Interface

The Geodat CLI (will eventually) provide a unified interface for interacting with the platform.

It allows developers and operators to access platform functionality without directly interacting with individual services or infrastructure components.

The CLI may expose capabilities such as:

- running analysis workflows
- interacting with APIs
- managing local development environments
- deploying services
- triggering data processing pipelines
- accessing AI services

---

# Role in the Platform

The CLI acts as an operational interface to the Geodat AI platform.

It provides a consistent interface across:

- infrastructure
- services
- data systems
- analysis pipelines

Where possible, the CLI wraps existing APIs and services rather than duplicating functionality.

---

# Design Principles

The CLI should:

- use platform APIs rather than bypassing services
- support scripting and automation
- provide consistent command patterns
- remain lightweight and composable

---

## Implementation: Go and Cobra

The Geodat CLI is implemented in **Go** using the **Cobra** CLI framework.

Go is well suited for platform tooling because it produces a **single compiled binary**, is fast, portable, and widely used for infrastructure and developer tools. Cobra provides a structured way to build command-line applications with **nested commands, flags, help output, and consistent command patterns**.

Using Go and Cobra allows the CLI to support commands such as:

- `geodat analysis run`
- `geodat data ingest`
- `geodat services deploy`

Cobra handles command parsing, argument validation, help generation, and command hierarchy, allowing the CLI code to remain small while delegating real work to platform APIs or internal services.

In practice, CLI commands act as **thin wrappers** that translate user commands into calls to platform APIs or service functions, keeping the CLI lightweight and maintainable while ensuring it remains aligned with the platform architecture.

---

# Guiding Principle

The CLI should simplify access to platform capabilities without becoming a tightly coupled monolithic tool.
