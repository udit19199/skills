---
name: better-pr-review
description: "Review workflow for Better pull requests. Use for PR prep, PR body writing, diff review, self-review, review comment response, testing evidence, or risk notes."
---

# Better PR Review

Run a review before asking others to review.

Gold-standard reference: [operate #482](https://github.com/jalantechnologies/operate/pull/482) — database monitoring toggle. Write so someone with zero context understands the problem, the design fit, what was rejected, and how to verify it.

## Review Stance

Lead with risks:

1. Bugs, regressions, security gaps, data issues, missing tests.
2. File and line references when reviewing code.
3. Open questions or assumptions.
4. Brief change summary only after findings.

If there are no findings, say that clearly and name remaining test gaps or residual risk.

## PR Preparation

Before writing the PR body:

1. Inspect the diff and classify the change.
2. Confirm it is one logical concern.
3. Remove unrelated edits, debug output, dead code, commented blocks, and accidental files.
4. Run the narrowest useful validation, then broader tests when risk warrants it.
5. Capture exact test commands and outcomes.

Completion: every modified file is accounted for, the PR concern is singular, and the testing evidence is explicit.

## Pick a Body Tier

Match depth to change size. Do not paste every section into a one-line fix.

| Tier | When | Sections to use |
| --- | --- | --- |
| **Narrative** | New feature, design choice, cross-cutting change | Full shape below |
| **Slice** | Stacked PR, one engine/check in a larger effort | Overview + slice boundaries + review path + tests + Loom |
| **Minimal** | Small fix, chore, docs | Overview + impact + test evidence |

## PR Body Shape (Narrative — use for features like #482)

Write in plain English. A reviewer with no prior context should understand the problem before opening the diff.

```md
## Overview

<How the system works today. What is different about this change. What this PR does and does not do. Link issue with Closes #N. Name follow-up PRs if any.>

## What this adds

- <Concrete operator/user-visible outcomes, not file names>

## How this stays consistent with existing behaviour

<Optional table or short paragraph: how this fits current patterns without special cases.>

## Approaches considered

**1. <Alternative>.** Rejected because <reason>.

**Chosen: <approach>.** <One sentence why.>

Skip this section when the change is obvious or there was no real design fork.

## What changed, at a high level

- <Architecture-level bullets — layers touched, new concepts, invariants preserved>

## Flow

```mermaid
sequenceDiagram
    ...
```

Use when an interaction path is non-obvious. Skip for backend-only plumbing with no actor flow.

## Notes for reviewers

- **SOC2 / security / audit:** <admin-only routes, credential handling, PII, etc. — or "None">
- **Scope boundary:** <what is deliberately out of this PR>

## Test evidence

- `<exact command>`: <pass count / result>
- Lint / typecheck: <what ran and outcome>
- Manual: <what you clicked or verified in the running app>

## Screenshots

<UI screenshots, or `N/A` for backend-only>

## Loom Video

- <link> — <what this video shows>
- <optional second link> — e.g. Network tab, edge case
```

## PR Body Shape (Slice — stacked work)

For part N of a larger effort (e.g. db-perf #581–#516):

```md
## Overview

<Business context for the whole effort, then what this slice adds. Closes / depends links.>

## Not in this slice

- <explicit exclusions>

## Depends on

- <parent PR or "None — bases main">

## How to review

1. <ordered steps — where to start in the diff>

## What changed, at a high level

- <3–6 bullets>

## Test evidence

- `<command>`: result
- Manual: <if any>

## API / DB impact

None | <describe>

## Screenshots

N/A | <links>

## Loom Video

<link> — <note if video covers full stack vs this slice only>
```

## After AI-Assisted Rebase or Hardening

If an agent rebased, resolved conflicts, or changed code on the author's branch (see jjalan on #482):

1. Post a **transparent summary comment**: what changed, why, what was verified statically, what was deliberately left as-is.
2. Ask the **author to re-review and verify in the running app** before merge. Do not treat AI work as approval.
3. Link any new Loom if behaviour changed materially.

## Better Checklist

- PR does one thing.
- Title follows the repo convention (`feat: …` or `feat(scope): …`).
- Description explains **why** and **how it fits**, not only what files changed.
- Self-review is complete line by line.
- Tests cover the changed behavior and related regression paths.
- Backend changes include automated tests unless the change is docs/config only.
- UI changes include screenshots or preview evidence; backend-only PRs say `N/A`.
- API, database, migration, security, audit, credential, and privacy impacts are called out.
- Loom linked when required (feature PRs) — label what each video shows.
- Feedback from earlier reviews is addressed directly; resolve review threads when fixed.

Read `references/pr-guidelines.md` for handbook checklist, title/commit conventions, and the #482 pattern breakdown.
