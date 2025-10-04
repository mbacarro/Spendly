# AI Money Tracker

A simple, TypeScript-first personal finance app that links your bank with Plaid and turns transactions into budgets, alerts, and basic AI insights.

> Web-first. API-powered. Side-project friendly.

## Tech Stack
- **Web:** Next.js (App Router), Tailwind, TanStack Query  
- **API:** NestJS, Prisma, PostgreSQL  
- **Jobs/Cache:** BullMQ + Redis  
- **Integrations:** Plaid (accounts & transactions), optional AI provider

## Monorepo Structure
```text
apps/
  web/      # Next.js app
  api/      # NestJS + Prisma API
  worker/   # (optional) background jobs
packages/
  types/    # shared Zod/TS types
  ui/       # shared UI primitives (web)
  utils/    # shared helpers
docs/
  PRD-Waypoint-Finance.md
```

## Quick Start
### 1) Install deps
pnpm install

### 2) Start local infra (Postgres + Redis)
docker compose up -d

### 3) Env vars
cp .env.example .env  # fill PLAID_*, DATABASE_URL, etc.

### 4) Migrate DB (API)
pnpm --filter api prisma:migrate

### 5) Run dev (web + api)
pnpm dev
#### web: http://localhost:3000
#### api: http://localhost:4000

## Plaid Sandbox (Fast Test)

1. Create a Plaid Sandbox app → add PLAID_CLIENT_ID and PLAID_SECRET to .env.

2. Open the Link flow in the web app using Plaid’s sandbox test credentials.

3. Confirm accounts/transactions appear in the dashboard.

## Documentation

PRD: docs/PRD-Waypoint-Finance.md
