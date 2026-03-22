---
globs: ["**"]
---

# Git & Version Control Standards

## Commit Messages (Conventional Commits)
```
<type>(<scope>): <subject>

Types: feat, fix, docs, style, refactor, perf, test, chore, ci, build
Examples:
  feat(auth): add OAuth2 login with refresh token rotation
  fix(cart): handle zero-quantity edge case in total calculation
  refactor(api): decompose monolithic handler into service functions
```

## Branching
```
main → production-ready
develop → integration branch (if used)
feature/short-description → new features
bugfix/short-description → bug fixes
hotfix/short-description → urgent production fixes
```

## Before Every Commit
- [ ] Code compiles/builds without errors
- [ ] No untyped or loosely typed code introduced (e.g., `any`, `object`, `dynamic`, `void*`)
- [ ] All edge cases handled (null, 0, empty string, missing fields)
- [ ] Error handling is comprehensive (no silent swallows)
- [ ] No hardcoded secrets or credentials
- [ ] Database queries use parameterized values
- [ ] Functions are under 30 lines where possible
- [ ] Tests pass
