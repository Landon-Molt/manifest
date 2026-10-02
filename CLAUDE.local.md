# Archived Local Development Notes (Landon-Molt)

Local source checkout was created on 2026-04-16 and retired on 2026-10-02.
This document preserves reproducible setup notes, not a live service inventory.
Local credentials, generated secrets, databases, caches, and dependencies are intentionally excluded.

## Fork and remotes

- Personal fork: https://github.com/Landon-Molt/manifest
- Upstream: https://github.com/mnfst/manifest

## Historical database setup

The local development container was named `postgres_db` (PostgreSQL 16).
The development database was named `manifest_dev_507924`.
Before reusing or deleting a container, verify ownership and other consumers.
Generate fresh database credentials when restoring; do not reuse development defaults.
Configure `DATABASE_URL` in `packages/backend/.env` following `.env.example`.
The historical seed mode used `SEED_DATA=true` and generated demo agents and sample messages.
Seeded accounts and demo API keys are test fixtures, not production credentials.

## Restore source development environment

```bash
npm ci
npm run build
cd packages/backend
node -r dotenv/config dist/main.js
```

The historical single-server endpoint was http://127.0.0.1:3001.
For separate frontend development, Vite used port 3000 and proxied backend requests to port 3001.
OAuth callback configuration must match the chosen backend URL.

## Historical test commands

```bash
cd packages/backend && npx jest --coverage
cd packages/frontend && npx vitest run --coverage
cd packages/shared && npx jest --coverage
```

These are reproduction commands, not a claim that a fresh test run passed at retirement.
No raw database, model, cache, dependency environment, or test-data archive is part of this source snapshot.
