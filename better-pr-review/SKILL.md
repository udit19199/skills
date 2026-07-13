---
name: better-pr-review
description: "PR quality gate for Better. Use for PR prep, PR body, self-review, diff review, or review comment response."
---

# PR Review

Gold standard: [operate #482](https://github.com/jalantechnologies/operate/pull/482). Write so someone with zero context understands the problem, the design fit, and how to verify.

**Incomplete descriptions = rejected PRs.** Poor documentation leads to production issues.

## Branch & Commits

- Branch: `author/type/description` (e.g. `udit/fix/login-timeout`).
- Commits: `type: description` (≤50 chars), imperative mood.
- Types: `feat` · `fix` · `chore` · `refactor` · `docs` · `test` · `perf` · `ci`.
- Raise / update PRs daily when possible.

## Stance

Lead with risks, not summaries:
1. Bugs, regressions, security gaps, data issues, missing tests.
2. File and line references.
3. Open questions or assumptions.
4. Change summary only after findings.

No findings → say so, name remaining test gaps or residual risk.

## PR Prep

1. Inspect diff, classify the change. One logical concern only.
2. Remove unrelated edits, debug output, dead code, commented blocks, accidental files.
3. Run narrowest useful validation, then broader tests when risk warrants.
4. Capture exact test commands and outcomes.

Completion: every file accounted for, concern is singular, testing evidence is explicit.

## Pick a Tier

| Tier | When | Sections |
|------|------|----------|
| **Narrative** | Feature, design choice, cross-cutting | Full shape below |
| **Slice** | Stacked PR, one piece of larger effort | Overview + slice boundaries + review path + tests |
| **Minimal** | Fix, chore, docs | Overview + impact + test evidence |

## PR Body — Narrative

```md
## Overview
<How the system works today. What changes. What this PR does and does not do. Closes #N. Name follow-up PRs.>

## What this adds
- <Concrete operator/user-visible outcomes, not file names>

## How this stays consistent with existing behaviour
<How this fits current patterns without special cases.>

## Approaches considered
**1. <Alternative>.** Rejected because <reason>.
**Chosen: <approach>.** <Why.>
Skip when the change is obvious or no real design fork.

## What changed, at a high level
- <Architecture bullets — layers touched, invariants preserved>

## Flow
<Mermaid sequence diagram if interaction path is non-obvious. Skip for backend-only plumbing.>

## Notes for reviewers
- **SOC2 / security / audit:** <or "None">
- **Scope boundary:** <what is deliberately out>

## Test evidence
- `<exact command>`: <result>
- Lint / typecheck: <outcome>
- Manual: <what you verified>

## Screenshots / Loom
<UI proof or N/A. Loom link with what it shows.>
```

## PR Body — Slice

```md
## Overview
<Business context for whole effort. What this slice adds. Closes / depends links.>

## Not in this slice
- <exclusions>

## How to review
1. <where to start in the diff>

## What changed
- <3–6 bullets>

## Test evidence
- `<command>`: result

## API / DB impact
None | <describe>
```

## Before Requesting Review (handbook checklist)

- [ ] Line-by-line self-review
- [ ] Tests pass; related behavior not broken
- [ ] Template complete
- [ ] Loom when it saves reviewer time
- [ ] Automated tests for backend behavior
- [ ] No debug noise / dead comments
- [ ] Prior feedback addressed

## Meta

- Assignee = you. Labels set.
- Give reviewers ~24h before nudging.

## After Review

- Eng review + **PM Acceptance** on the PR when required.
- Sprint exit: demo on staging, business standpoint.

## References

`references/pr-guidelines.md` — handbook checklist, title/commit conventions, #482 breakdown.
