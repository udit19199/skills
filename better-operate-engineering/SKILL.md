---
name: better-operate-engineering
description: "Code quality standards for Better's operate repo (Flask/React/Mongo). Use when implementing, debugging, or reviewing operate code."
---

# Operate Engineering

Read the module, its tests, and nearby docs before editing. Check AGENTS.md and docs/ in the repo. Prefer existing patterns over new abstractions.

## Backend

- Route → view → service → reader/writer → repository → MongoDB.
- Import other modules through public service/type surfaces, never `internals/`.
- Business rules in service-facing reader/writer, not Flask views.
- Typed request/response/domain models.
- Mongo indexes for every new query or sort.
- No N+1 queries — batch reads, assemble maps in memory.
- State-changing routes need access control and audit logging.

## Frontend

- Pages assemble design-system components from `src/apps/frontend/components`.
- No `className` on raw DOM in pages. No inline `style` on pages.
- Layout primitives + spacing/theme tokens. Component variants over page-local hacks.
- Fetch through service modules, normalize into typed models.

## Security

New stored secrets, outbound calls, subprocesses, auth/session logic, or provider credentials → explicit security review in PR.

- Never log PII or secrets.
- Validate request data at boundaries.
- Allowlists for subprocess env and outbound URLs.
- No empty-success on failed reads.
- State-changing routes need access checks and audit events.
- New collections need test cleanup fixtures.

## Testing

Full backend suite in test container only:
```bash
docker compose -f docker-compose.test.yml up --build
```
Never run destructive tests in dev container (it hits dev data). Narrow validation first, broader when risk warrants. Record exact command and result.

## High-Risk Areas

Always flag PR risk when touching: auth, sessions, audit logging, stored credentials, provider integrations, outbound HTTP, subprocesses, AI agent tool access, Mongo over growing collections, Celery workers/cron.

## References

`references/operate-standards.md` — commands, architecture, high-risk areas.
