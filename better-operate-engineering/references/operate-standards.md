# Operate Engineering Reference

Use this reference for Better's `operate` repo.

## Stack

- Backend: Python 3.12, Flask 3, PyMongo, Pydantic, Celery.
- Frontend: React 18, TypeScript, Tailwind CSS, Axios.
- Infrastructure: MongoDB, Redis.
- Tests: Pytest and pytest-cov.
- Deployment: Docker and Kubernetes.

## Key Paths

- `src/apps/backend`: Flask app and modules.
- `src/apps/frontend`: React app.
- `tests`: backend tests.
- `docs`: architecture and operating docs.
- `config`: shared configuration.

## Commands

```bash
npm run serve
npm run serve:backend
npm run serve:worker
npm run serve:beat
npm run serve:frontend
npm run build
npm run lint:py
npm run lint:ts
npm run lint:md
docker compose -f docker-compose.test.yml up --build
```

Use the Docker test compose command for full backend tests.

## Backend Architecture

- Each domain module owns REST API, service, reader/writer, repository, types, and exceptions.
- Public module surface is `*_service.py`, `types.py`, and module exceptions.
- `internals/` is private.
- Repositories declare collection indexes.
- Mongo syntax stays in repositories, not service or view layers.

## High-Risk Areas

Always call out PR risk when touching:

- Authentication or sessions.
- Audit logging.
- Stored credentials or encryption.
- Provider integrations.
- Outbound HTTP calls.
- Subprocess execution.
- AI agent tool access.
- Mongo queries over growing collections.
- Celery workers and cron schedules.

## Security Baseline

- Never log PII or secrets.
- Validate request data at boundaries.
- Use allowlists for subprocess environments and outbound URLs.
- Do not turn failed reads into empty success states.
- State-changing routes need access checks and audit events.
- New collections need test cleanup fixtures.

## Frontend Baseline

- Pages use design-system components.
- No page-level raw DOM `className` or inline style.
- Use tokenized variants, sizes, gaps, and theme colors.
- Shared components live under `src/apps/frontend/components`.
- API calls flow through service modules.
