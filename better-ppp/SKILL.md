---
name: better-ppp
description: "Daily PPP (Plan/Problems/Progress) updates for Better. Use for morning updates, EOD replies, or status messages."
---

# PPP

Daily updates are part of the work culture. Not posting = not working.

## Shape

**Morning** (reply in project channel):
```
Plan:
- <deliverable>, <link>, <intended outcome>.

Problems:
- <blocker>, <what I tried>, <what you need>.
```

**EOD** (reply to same thread):
```
Progress:
- <completed outcome>, <link>, <verification>.
```

## Rules

- Outcomes only. "Ship auth tests in PR #234" > "Work on tests."
- Links to PRs, issues, docs, or artifacts. No bare text.
- Problems must include: what failed, what was tried, what decision/access is needed.
- Never "I'm stuck" alone. Include: goal, state, failure, files/logs/PR, attempts, specific ask.
- Reply to the morning thread at EOD — don't start a new one.

## Good

```
Plan:
- Add unit tests for AWS ECR cleanup logic (PR #234), ensuring edge cases are handled.
- Deploy cleanup code to staging and verify artifact removal (Issue #88).

Problems:
- Awaiting review on infra access request (ticket #567).
```
```
Progress (EOD):
- All tests passed and cleanup logic merged (PR #234).
- Verified artifact deletion in staging; no issues found.
```

## Bad

```
Plan:
- Read PPPs.
- Check emails.

Problems:
- Waiting for teammate's update.

Progress:
- Finished reading PPPs.
- No further updates.
```

## Handoff Shape

When switching context or wrapping a session:
- Current state of the work.
- What was completed (artifacts).
- What's blocked and why.
- What the next person/session should do first.
