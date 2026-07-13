# Better PRD And Planning Reference

Use this when drafting PRDs, tickets, sprint plans, or PM handoffs.

## PM Loop

1. Understand the customer problem.
2. Evangelize and validate the solution with design/customer.
3. Work with engineering to plan and execute.
4. Measure, learn, and improve after launch.

## PRD Template

```md
# Product Requirements Document

## 1. Introduction

Brief overview, purpose, importance, and scope.

## 2. Objectives

- Objective 1
- Objective 2
- Objective 3

## 3. Assumptions

- User behavior
- Technical infrastructure
- System dependencies
- Platform requirements
- User understanding
- Technical capabilities

## 4. Persona

- Persona:
- Goals:
- Challenges:
- Primary persona:

## 5. Use Cases

### Scenario

- Persona:
- Context:
- Steps:
- Expected outcome:

## 6. Functional Requirements

### FR1: Title

- Description:
- User flow:
- Options and sub-features:
- Acceptance criteria:
- Technical considerations:
```

## Sprint Execution

- Sprint planning: present intended work and get tech lead buy-in.
- Standup: track progress and adapt plan.
- Feature acceptance: review PRs and provide PM acceptance in GitHub.
- Sprint exit: demo completed tickets from business standpoint.
- Retro: capture what went well, what to improve, and concrete action items.

## Product Defects

When a stakeholder reports a defect:

- Validate against PRD or accepted behavior.
- Create or update a ticket.
- Assign priority: P0, P1, or P2.
- Work with lead to fix.
- Verify in production and notify reporter.
