---
name: better-operate-engineering
description: "Operate engineering workflow. Use for implementing, reviewing, testing, or debugging Better's Flask/React/Mongo/Celery operate repo with layered backend, design-system frontend, security, audit, and test-container standards."
---

# Better Operate Engineering

Ship Operate changes with repo evidence and production risk in view.

## First Pass

1. Read the nearby module, tests, and docs before editing.
2. Check `AGENTS.md`, `CLAUDE.md`, and relevant files under `docs/`.
3. Inspect current git status and avoid touching unrelated changes.
4. Prefer existing module patterns over new abstractions.

Completion: the touched module pattern is understood, unrelated dirty files are ignored, and the validation plan is named.

## Backend Rules

- HTTP route -> view -> service -> reader/writer -> repository -> MongoDB.
- Import other modules through public service/type surfaces, never their `internals/`.
- Keep business rules in service-facing reader/writer layers, not Flask views.
- Use typed request/response/domain models.
- Add Mongo indexes for every new query or sort pattern.
- Avoid N+1 queries. Batch reads and assemble maps in memory.
- State-changing routes need access control and audit logging unless clearly exempt.
- New stored secrets, outbound calls, subprocesses, auth/session logic, or provider credentials need explicit security review in the PR.

## Frontend Rules

- Pages assemble design-system components from `src/apps/frontend/components`.
- Do not pass `className` to raw DOM elements in pages.
- Do not use inline `style` on pages.
- Use layout primitives and spacing/theme tokens.
- Add component variants instead of page-local styling hacks.
- Fetch through service modules and normalize responses into typed models.

## Testing

Run tests only in the dedicated test container when running the full backend suite:

```bash
docker compose -f docker-compose.test.yml up --build
```

Do not run destructive backend tests inside the dev container. It points at local development data.

For narrow validation, run the smallest relevant command first, then broader validation when risk warrants it. Record the exact command and result.

## PR Readiness

Before review:

- Diff is one logical concern.
- Self-review is complete line by line.
- Debug output and accidental files are removed.
- Related behavior and regression paths are checked.
- Product, security, audit, data, API, migration, and deployment impacts are explicit.

Read `references/operate-standards.md` for repo-specific commands, architecture, and high-risk areas.
