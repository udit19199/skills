---
name: better-product-planning
description: "Product planning for Better. Use for PRDs, acceptance criteria, tickets, sprint plans, KPIs, feature decisions, or defect triage."
---

# Product Planning

Start with the problem, not the requested solution. Own the outcome end-to-end — a checkbox on a ticket is not the same as a real user result.

## 5 Whys

When the ask is ambiguous:
1. What is happening?
2. Why does it matter to the user or business?
3. Why is the current system insufficient?
4. Why is this the right time?
5. Why is this scope enough?

## PM Loop

1. Understand the customer problem.
2. Validate solution with design/customer before big builds.
3. Engineering designs + breaks into small tasks. Sprints are 2 weeks.
4. PM Acceptance on GitHub PRs before merge when the feature needs it.
5. After ship: watch KPI / usage.

## PRD Shape

- **Introduction**: product/feature summary.
- **Objectives**: 2-4 concrete goals.
- **Assumptions**: user, technical, dependency, platform.
- **Personas**: primary user, secondary stakeholders.
- **Use cases**: scenario, context, steps, expected outcome.
- **Functional requirements**: behavior, flow, acceptance criteria, technical notes.
- **KPIs**: usage, quality, operational, or commercial signal.
- **Non-goals**: intentionally excluded.
- **Risks**: product, engineering, data, security, rollout.

## Ticket Breakdown

Each ticket: single deliverable, acceptance criteria, test evidence expected, explicit dependencies. Architecture/data-flow changes get their own ticket.

## Defect Triage

1. Validate against PRD or accepted behavior.
2. Classify: bug, expected behavior, or missing requirement.
3. Priority: P0 (stop everything), P1 (fix soon), P2 (backlog).
4. Create/update ticket.
5. After deploy: verify in prod once, notify reporter.

## References

`references/prd-template.md` — full template and sprint execution notes.
