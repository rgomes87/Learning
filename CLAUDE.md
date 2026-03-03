# CLAUDE.md — AI Assistant Guide for rgomes87/Learning

This file provides guidance for AI assistants (Claude Code and similar tools) working in this repository. Keep it up to date as the project evolves.

---

## Repository Overview

| Field       | Value                                      |
|-------------|--------------------------------------------|
| Name        | Learning                                   |
| Owner       | rgomes87                                   |
| Remote      | `http://local_proxy@127.0.0.1:22770/git/rgomes87/Learning` |
| Status      | Freshly initialized — no source code yet   |

This is a new, empty repository. The conventions and workflows below are the starting baseline; update them as soon as a technology stack is chosen and source code is added.

---

## Git Workflow

### Branch Naming

All Claude Code sessions must develop on branches that follow this pattern:

```
claude/<short-description>-<SESSION_ID>
```

Example: `claude/add-claude-documentation-NW78U`

Never push directly to `main` or `master` without explicit permission.

### Making Changes

```bash
# 1. Ensure you are on the correct feature branch
git checkout claude/<description>-<SESSION_ID>

# 2. Stage specific files (avoid git add -A to prevent accidental sensitive-file inclusion)
git add <file1> <file2>

# 3. Commit with a clear, descriptive message
git commit -m "feat: describe what and why"

# 4. Push to the remote branch
git push -u origin claude/<description>-<SESSION_ID>
```

### Push Retry Policy

If a push fails due to a **network error**, retry with exponential backoff:

| Attempt | Wait before retry |
|---------|-------------------|
| 1st     | 2 s               |
| 2nd     | 4 s               |
| 3rd     | 8 s               |
| 4th     | 16 s              |

A **403** error means the branch name does not match the required `claude/...` pattern — fix the branch name rather than retrying.

### Commit Message Style

Use [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<optional scope>): <short summary>

<optional body — explain the "why", not the "what">
```

Common types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`, `ci`.

---

## Development Principles

### General

- Prefer editing existing files over creating new ones.
- Only make changes that are directly requested or clearly necessary — avoid over-engineering.
- Do not add docstrings, comments, or type annotations to code you did not change.
- Do not add error handling or validation for scenarios that cannot happen.
- Remove unused code completely rather than commenting it out or leaving backwards-compat shims.

### Security

- Never commit secrets, credentials, `.env` files, or API keys.
- Validate only at system boundaries (user input, external APIs); trust internal framework guarantees.
- Avoid introducing OWASP Top 10 vulnerabilities (SQLi, XSS, command injection, etc.).

### Code Review

Before committing, verify:
- [ ] No secrets or sensitive data staged.
- [ ] Logic is correct and changes are scoped to what was requested.
- [ ] Tests pass (when a test suite exists).
- [ ] Linters/formatters pass (when configured).

---

## Project Structure

> This section is a placeholder. Update it once source code exists.

```
Learning/
├── CLAUDE.md          # This file — AI assistant guide
└── (source code TBD)
```

When adding source code, document the structure here:
- List top-level directories and their purpose.
- Note where tests live.
- Note where configuration lives.

---

## Technology Stack

> Not yet determined. Update this section when a stack is chosen.

Common things to document here:
- Language(s) and runtime versions.
- Frameworks and key libraries.
- Package manager and how to install dependencies.
- How to run the project locally.
- How to run tests.
- Linting / formatting tools and commands.

---

## Testing

> No test suite configured yet. Update when tests are added.

Document here:
- Test runner command (e.g., `npm test`, `pytest`, `cargo test`).
- How to run a single test file or test case.
- Where mocks/fixtures live.
- Coverage expectations.

---

## CI/CD

> No CI/CD pipeline configured yet. Update when workflows are added.

Document here:
- Which CI system is used (GitHub Actions, GitLab CI, etc.).
- What the pipeline checks (lint, test, build, deploy).
- How to inspect pipeline results.

---

## Frequently Updated Sections Checklist

When the project grows, revisit and update:

- [ ] **Project Structure** — reflect current directory layout.
- [ ] **Technology Stack** — language, runtime, frameworks, package manager.
- [ ] **Testing** — commands, locations, coverage requirements.
- [ ] **CI/CD** — pipeline steps and how to read results.
- [ ] **Conventions** — coding style, naming conventions, API patterns.

---

*Last updated: 2026-03-03 by Claude Code (session NW78U)*
