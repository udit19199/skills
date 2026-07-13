# Better PR Guidelines

Use this reference when preparing or reviewing a PR.

## Gold Standard

**[operate #482](https://github.com/jalantechnologies/operate/pull/482)** — `feat: turn database monitoring on or off, per connection`

Why it works for reviewers with no context:

| Section | What it does |
| --- | --- |
| **Overview** | Explains how proactive monitoring works today, why databases are different, what this PR covers vs #458 follow-up |
| **What this adds** | Operator-visible outcomes in bullets |
| **How this stays consistent** | Table comparing whole-integration vs per-connection scope — shows no special-case branching |
| **Approaches considered** | Rejected alternatives with reasons; names the chosen design |
| **What changed, at a high level** | Architecture bullets, not a file list |
| **Flow** | Mermaid sequence diagram for the toggle path |
| **Notes for reviewers** | SOC2/audit callout + explicit scope boundary |
| **Test evidence** | Suite count, specific scenarios, lint/mypy, manual app verification |
| **Loom** | Two links — UI walkthrough + Network tab for API proof |

Adapt the pattern; do not copy every section into small PRs.

## Principles

- Code quality matters for production stability.
- Clean code reduces maintenance cost.
- Type safety catches issues before production.
- Small broken windows should be fixed before they become normal.
- PRs are permanent documentation — write for the engineer debugging at 2 AM in six months.

## Before Coding

- Keep PRs small: one logical change.
- Use a proper branch name if creating one: `author/type/description`.
- Understand the business and user context before implementation.

## Commits And Titles

Use the repo's convention when it exists. Common Better convention:

```text
<type>(<scope>): <subject>
```

or shorter handbook form:

```text
type: description
```

Use imperative mood. Keep the subject short and specific.

Common types:

- `feat`
- `fix`
- `chore`
- `refactor`
- `docs`
- `test`
- `perf`
- `ci`

Handbook: https://handbook.btr.group/engineering/pr-etiquette

## PR Description — Required Elements

Always include:

- **Why** — business/operator problem first.
- **What** — outcomes and high-level design, not a raw diff summary.
- **Impact** — API/DB/deployment (write `None` when true).
- **Test evidence** — exact commands and results.
- **Screenshots** — UI proof, or explicit `N/A` for backend-only.

Add when the change warrants it:

- **Consistency** — how this fits existing patterns.
- **Approaches considered** — for non-trivial design forks only.
- **Flow diagram** — when the interaction path is hard to follow from code alone.
- **Notes for reviewers** — security, audit, SOC2, scope boundaries.
- **Loom** — feature PRs; label what each video demonstrates.

## Stacked / Slice PRs

When one issue is split across PRs:

- State **part N of M** and link the parent issue.
- **Not in this slice** — stop scope creep questions early.
- **Depends on** — name the base PR/branch.
- **How to review** — ordered steps into the diff.
- **Loom** — say whether the video covers the full stack or only this slice.

## AI-Assisted Changes (founder expectation — jjalan on #482)

When an agent rebases, resolves conflicts, or hardens a branch:

1. Post a comment summarizing what the agent changed and why.
2. List what was verified statically vs what needs human runtime check.
3. Call out design choices **deliberately left as-is**.
4. Author must **re-review and verify in the app** — do not merge on the agent's say-so alone.

## Self-Review

Before requesting review:

- Review the diff line by line.
- Test the change and nearby behavior.
- Complete the PR template (or narrative/slice shape from the skill).
- Add automated tests for backend behavior.
- Remove debug code, console logs, dead code, and stale comments.
- Address previous feedback directly.
- Resolve review threads when fixes land.

Give reviewers time. Follow up when review is blocking other work.
