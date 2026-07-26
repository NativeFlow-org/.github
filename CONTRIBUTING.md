# Contributing to NativeFlow

Thank you for your interest in contributing to NativeFlow! This document outlines the process for contributing to any repository in the NativeFlow organization.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Repository Structure](#repository-structure)
- [Development Workflow](#development-workflow)
- [Pull Request Guidelines](#pull-request-guidelines)
- [Commit Conventions](#commit-conventions)
- [Testing](#testing)
- [Security](#security)

## Code of Conduct

All contributors must adhere to our [Code of Conduct](CODE_OF_CONDUCT.md). Please read it before proceeding.

## Getting Started

1. Fork the repository you wish to contribute to.
2. Clone your fork locally.
3. Set up the development environment as described in the repository's README.
4. Create a new branch for your work: `git checkout -b feat/your-feature-name`.

## Repository Structure

NativeFlow is organized as a multi-repo project:

| Repository | Purpose |
|---|---|
| `.github` | Organization-level documentation, templates, and shared workflows |
| `nativeflow-contract` | Soroban smart contracts (Rust) |
| `nativeflow-frontend` | Web dashboard and SDK (TypeScript) |
| `nativeflow-keeper` | Off-chain automation daemon (Rust) |

Work on each repository independently. Cross-repo changes requiring coordinated releases should be discussed in an issue first.

## Development Workflow

1. **Discuss first** -- Open an issue to discuss significant changes before implementing.
2. **Keep changes focused** -- Each pull request should address a single concern.
3. **Write tests** -- Add or update tests to cover your changes.
4. **Run the test suite** -- Ensure all existing tests pass.
5. **Update documentation** -- Update README, API references, or inline docs as needed.

## Pull Request Guidelines

- PR titles should follow conventional commit format (see below).
- Reference the related issue: `Closes #123`.
- Provide a clear description of what the PR does and why.
- Keep PRs small and reviewable. Split large changes into multiple PRs.
- Ensure CI checks pass before requesting review.

## Commit Conventions

We use conventional commit messages:

```
<type>: <short description>

[optional body]
```

Types:
- `feat` -- New feature
- `fix` -- Bug fix
- `docs` -- Documentation changes
- `refactor` -- Code restructuring
- `test` -- Adding or updating tests
- `chore` -- Build, CI, or tooling changes
- `style` -- Formatting, linting (no production code change)

Examples:
- `feat: add multi-token support to subscribe`
- `fix: handle edge case when interval is zero`
- `docs: update deployment instructions`

## Testing

- **Rust repos** (contract, keeper): Run `cargo test` and `cargo clippy`.
- **Frontend repo**: Run `npm run lint` and `npm run build`.
- Ensure all new code has adequate test coverage.

## Security

If you discover a security vulnerability, do not open a public issue. Please report it privately to security@nativeflow.io.

---

Thank you for helping make NativeFlow better!
