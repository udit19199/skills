---
name: better-pr-review
description: "PR quality gate for Better. Use for PR prep, PR body, self-review, diff review, or review comment response."
---

# PR Review

Gold standard: [operate #482](https://github.com/jalantechnologies/operate/pull/482). Write so someone with zero context understands the problem, the design fit, and how to verify.

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

## Checklist

- PR does one thing.
- Title: `feat: …` or `feat(scope): …`.
- Description explains **why** and **how it fits**.
- Self-review complete line by line.
- Tests cover changed behavior and regression paths.
- UI: screenshots or N/A. Backend: automated tests unless docs/config only.
- API, DB, migration, security, audit, credential, privacy impacts called out.
- Loom linked for feature PRs.
- Prior review feedback addressed; threads resolved.

## References

`references/pr-guidelines.md` — handbook checklist, title/commit conventions, #482 breakdown.
