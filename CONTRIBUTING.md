# Contributing to InterviewForge AI

Thank you for your interest in contributing to InterviewForge AI! We welcome contributions from the community. Please take a moment to review this guide before submitting a contribution.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [Branch Naming Convention](#branch-naming-convention)
- [Commit Message Convention](#commit-message-convention)
- [Pull Request Process](#pull-request-process)
- [Code Style](#code-style)
- [Testing Requirements](#testing-requirements)
- [Issue Reporting](#issue-reporting)

## Code of Conduct

This project adheres to our [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you agree to uphold it.

## Getting Started

1. Fork the repository
2. Clone your fork: `git clone https://github.com/YOUR_USERNAME/interviewforge-ai.git`
3. Add upstream: `git remote add upstream https://github.com/interviewforge/interviewforge-ai.git`
4. Create a feature branch: `git checkout -b feat/your-feature-name`

## Development Setup

### Prerequisites
- Node.js 20+
- Docker Desktop
- npm 10+

### Steps

```bash
# Install dependencies
npm install

# Copy environment variables
cp .env.example .env
# Fill in required values in .env

# Start infrastructure
docker-compose up -d postgres redis

# Run database migrations
npm run db:migrate

# Seed the database (optional)
npm run db:seed

# Start development servers
npm run dev
```

API: http://localhost:4000  
Web: http://localhost:3000

## Branch Naming Convention

Use the following prefixes:

| Type | Pattern | Example |
|---|---|---|
| Feature | `feat/` | `feat/add-webcam-monitoring` |
| Bug Fix | `fix/` | `fix/jwt-refresh-token` |
| Documentation | `docs/` | `docs/update-api-reference` |
| Refactor | `refactor/` | `refactor/interview-service` |
| Test | `test/` | `test/auth-controller` |
| Chore | `chore/` | `chore/upgrade-dependencies` |
| Performance | `perf/` | `perf/optimize-leaderboard-query` |

## Commit Message Convention

We use [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <description>

[optional body]

[optional footer]
```

**Types:** `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`, `perf`, `ci`

**Examples:**
```
feat(auth): implement Google OAuth login
fix(interview): resolve timer reset on page refresh
docs(api): add Swagger annotations to payment endpoints
perf(leaderboard): add database index for ranking query
```

## Pull Request Process

1. **Update documentation** if you've changed any APIs or added features
2. **Add tests** for any new functionality (see Testing Requirements)
3. **Ensure all checks pass**: `npm run lint && npm run type-check && npm run test`
4. **Fill out the PR template** completely
5. **Link the related issue** using `Fixes #123`
6. Request review from at least one maintainer
7. Squash commits before merging (maintainers will do this)

### PR Template

When opening a PR, you will be prompted with a template. Please fill it in completely.

## Code Style

- **TypeScript**: Strict mode is enabled. All new code must be fully typed.
- **ESLint**: Run `npm run lint:fix` to auto-fix linting issues.
- **Prettier**: Run `npm run format` to auto-format code.
- **No `any` types**: Use proper types or `unknown` + type guards.
- **Comments**: Add JSDoc comments for all public functions and classes.
- **SOLID principles**: Keep functions small, single-purpose, and testable.

## Testing Requirements

| Contribution Type | Required Tests |
|---|---|
| New API endpoint | Unit test (controller) + Integration test (route) |
| New service | Unit test with mocks |
| New React component | Component rendering test |
| Bug fix | Regression test proving the bug is fixed |
| Database query | Test with test database |

**Minimum coverage thresholds:**
- Statements: 80%
- Branches: 70%
- Functions: 80%
- Lines: 80%

## Issue Reporting

### Bug Reports

Use the [Bug Report template](.github/ISSUE_TEMPLATE/bug_report.md).

Include:
- Clear title
- Steps to reproduce
- Expected vs actual behavior
- Environment details (OS, Node version, browser)
- Screenshots or logs

### Feature Requests

Use the [Feature Request template](.github/ISSUE_TEMPLATE/feature_request.md).

Include:
- Problem statement
- Proposed solution
- Alternatives considered
- Potential impact on existing features

---

Thank you for contributing! 🚀
