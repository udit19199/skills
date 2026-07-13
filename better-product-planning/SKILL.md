---
name: better-product-planning
description: "Problem workflow for Better product planning. Use for PRDs, acceptance criteria, tickets, sprint plans, KPIs, feature decisions, customer problems, or product defect triage."
---

# Better Product Planning

Convert a vague request into a clear problem, plan, and ticket shape.

## Problem First

Start with the problem, not the requested solution.

Use 5 Whys when the ask is ambiguous:

1. What is happening?
2. Why does it matter to the user or business?
3. Why is the current system insufficient?
4. Why is this the right time to solve it?
5. Why is the proposed scope enough?

## PRD Shape

Produce concise sections:

- Introduction: product or feature summary.
- Objectives: 2-4 concrete goals.
- Assumptions: user, technical, dependency, and platform assumptions.
- Personas: primary user and secondary stakeholders.
- Use cases: scenario, context, steps, expected outcome.
- Functional requirements: behavior, flow, options, acceptance criteria, technical notes.
- KPIs: usage, quality, operational, or commercial signal.
- Non-goals: what is intentionally excluded.
- Risks: product, engineering, data, security, and rollout risk.

## Ticket Breakdown

Break work into reviewable tickets:

- Each ticket has a single deliverable.
- Each ticket has acceptance criteria.
- Each ticket has test evidence expected.
- Dependencies are explicit.
- Technical design work is a ticket when it changes architecture or data flow.

Completion: the plan states the problem, acceptance criteria, risks, validation signal, and ticket boundaries.

## Defect Triage

When a defect is reported:

1. Validate expected behavior against PRD or accepted product behavior.
2. Decide if it is a bug, expected behavior, or missing requirement.
3. Assign priority:
   - P0: stop everything.
   - P1: fix soon, current sprint if possible.
   - P2: backlog.
4. Create/update the ticket.
5. After production deploy, verify once and notify the reporter.

Read `references/prd-template.md` when producing a PRD or ticket plan.
