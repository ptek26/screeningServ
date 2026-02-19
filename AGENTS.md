# Agent Guidelines

This document provides guidelines for AI agents and developers working on this project.

## Before Committing

Always follow this sequence before committing and pushing changes:

### 1. Compile and Test Locally

```bash
./mvnw verify
```

This runs:
- Compile
- Unit tests
- SpotBugs static analysis

**Do not push if this fails.** Fix all issues first.

### 2. Update Relevant Documentation

When making changes, update the corresponding documentation:

| Change Type | Update This File |
|-------------|------------------|
| New feature or behavior | `CONTRIBUTING.md` |
| New CI/CD pipeline or check | `CONTRIBUTING.md` (CI Pipeline section) |
| New dependency | `pom.xml` + check if `README.md` needs update |
| Branch protection changes | `CONTRIBUTING.md` (Branch Protection section) |
| Release process changes | `CONTRIBUTING.md` (Release Process section) |

### 3. Commit with Meaningful Messages

Use conventional commit format:

```
<type>: <short description>

[optional body]
```

Types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`, `ci`

Examples:
- `feat: add candidate screening endpoint`
- `fix: resolve null pointer in validation`
- `docs: update API documentation`
- `ci: add SonarQube analysis`

## Quick Checklist Before Push

- [ ] `./mvnw verify` passes locally
- [ ] Documentation updated (if applicable)
- [ ] Commit message follows conventional format
- [ ] Changes are on a feature branch (not `develop` or `main`)

## Agent Constraints

**AI agents must NEVER:**
- Merge PRs (requires human approval)
- Approve PRs
- Force push to any branch
- Push directly to `develop` or `main`

**Agent workflow stops at:**
1. Create feature branch ✅
2. Make changes ✅
3. Push feature branch ✅
4. Create PR ✅
5. Report PR URL and status ✅
6. **STOP** — Wait for human to review, approve, and merge

All merges require human-in-the-loop (HITL) review.

## Before Making Changes

**CRITICAL:** Do not push changes without confidence they will work.

1. **Understand the problem fully** - Read logs, understand root cause
2. **Research the solution** - Check documentation, existing patterns, best practices
3. **Validate locally if possible** - Run tests, lint, build with `./mvnw verify`
4. **Consider edge cases** - What could go wrong? What dependencies exist?
5. **Plan before implementing** - Document the plan, identify all affected files
6. **One change at a time** - Don't batch unrelated fixes
7. **Verify CI passes** - All checks must pass before requesting merge

**Time and resources are valuable.** Avoid "try and see" approaches. Each failed CI run costs time and consumes resources.

### Planning Checklist

Before starting implementation:
- [ ] Problem is clearly understood and documented
- [ ] Solution approach is validated (documentation, similar implementations)
- [ ] All affected files identified
- [ ] Edge cases considered
- [ ] Documentation updates planned

## Branch Workflow

1. Create feature branch from `develop`
2. Make changes and test locally
3. Push feature branch
4. Create PR to `develop`
5. Wait for CI to pass
6. **STOP** — Report PR URL to user
7. User reviews, approves, and merges

See `CONTRIBUTING.md` for detailed workflow.
