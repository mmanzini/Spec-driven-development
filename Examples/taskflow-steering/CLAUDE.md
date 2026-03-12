# TaskFlow

## Project Overview

TaskFlow is a SaaS task management application for small teams (2-20 people). It provides boards, lists, and cards for organizing work, with real-time collaboration, due dates, and basic reporting. Currently in active development with 3 developers and ~2,000 active users.

## Tech Stack

- **Language:** TypeScript 5.4 (strict mode)
- **Frontend:** Next.js 14 with App Router, React 18
- **Styling:** Tailwind CSS 3.4
- **Backend:** Next.js API routes + tRPC for type-safe API calls
- **Database:** PostgreSQL 16 via Prisma ORM (schema at `prisma/schema.prisma`)
- **Auth:** NextAuth.js v5 with email + Google OAuth
- **Real-time:** Pusher for WebSocket connections
- **Testing:** Vitest for unit/integration, Playwright for e2e
- **Hosting:** Vercel (frontend), Railway (database)

## Commands

```bash
# Install dependencies
pnpm install

# Development server
pnpm dev

# Run all tests
pnpm test

# Run e2e tests
pnpm test:e2e

# Lint and type check
pnpm lint && pnpm typecheck

# Database migrations
pnpm prisma migrate dev

# Generate Prisma client
pnpm prisma generate
```

## Project Structure

```
src/
  app/                   # Next.js App Router pages
    (auth)/              # Auth pages (login, register)
    (dashboard)/         # Authenticated pages
    api/                 # API routes
  components/
    ui/                  # Shared UI components (Button, Input, Modal, etc.)
    layout/              # Layout components (Sidebar, Header)
  features/
    boards/              # Board management
    cards/               # Card CRUD and detail views
    lists/               # List management within boards
    users/               # User profiles and team management
    notifications/       # Notification system
  lib/
    database.ts          # Prisma client singleton
    auth.ts              # NextAuth configuration
    pusher.ts            # Pusher client/server setup
    email.ts             # Email sending utility (Resend)
  server/
    trpc/                # tRPC router definitions
specs/                   # SDD spec folders
standards/               # Project-wide coding standards
prisma/
  schema.prisma          # Database schema
  migrations/            # Migration files
tests/
  e2e/                   # Playwright e2e tests
```

## Code Conventions

- **Naming:** camelCase for variables/functions, PascalCase for components/types, SCREAMING_SNAKE for constants
- **Files:** Feature code lives in `src/features/[feature-name]/`. Shared UI in `src/components/ui/`.
- **Components:** One component per file. Co-locate component-specific types in the same file. Shared types go in `src/types/`.
- **API responses:** All API responses use `{ data, error, meta }` shape via tRPC
- **Database:** All queries go through Prisma. No raw SQL unless explicitly approved. Use transactions for multi-table operations.
- **Testing:** Every new feature needs unit tests for business logic and at least one e2e test for the primary user flow.
- **Imports:** Use `@/` path alias for `src/` directory. Group imports: external → internal → relative.

## Boundaries

### Always

- Run `pnpm test` before marking any task complete
- Follow existing file and folder structure in `src/features/`
- Use existing UI components from `src/components/ui/` before creating new ones
- Use Prisma for all database operations
- Use tRPC for all API endpoints (no raw API routes for new features)
- Handle loading and error states in all UI components
- Use TypeScript strict mode — no `any` types, no `@ts-ignore`

### Ask

- Before adding any new `pnpm` dependency
- Before creating a new top-level directory under `src/`
- Before modifying `prisma/schema.prisma` (requires migration planning)
- Before changing any authentication or authorization logic
- Before modifying shared UI components in `src/components/ui/`
- Before changing the tRPC router structure

### Never

- Never commit `.env` files or expose API keys/secrets
- Never push directly to `main` — all changes go through PRs
- Never skip or disable tests
- Never modify Vercel or Railway configuration files
- Never use `!important` in Tailwind/CSS
- Never bypass NextAuth for authentication checks
- Never use `console.log` in production code — use the logger from `src/lib/logger.ts`
