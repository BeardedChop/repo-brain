# AGENTS.md

this file tells AI coding agents how to behave in this Next.js project.

## project overview

a full-stack web app built with Next.js, using [auth provider] for auth and [database] for data.

## tech stack

- **framework:** Next.js 15 (app router)
- **language:** TypeScript
- **styling:** Tailwind CSS
- **database:** [Prisma/Supabase/Drizzle]
- **auth:** [Clerk/NextAuth/Supabase Auth]
- **deployment:** Vercel

### choosing your stack

pick one from each bracket above. here's a quick guide:

**database:**
- **Prisma** — best default. great DX, type-safe queries, easy migrations. use if you're on any SQL database.
- **Drizzle** — lighter than Prisma, closer to raw SQL. use if you want more control or smaller bundle.
- **Supabase** — managed Postgres with auth, storage, and realtime built in. use if you want a full backend-as-a-service.

**auth:**
- **Clerk** — drop-in auth with pre-built UI components. fastest to set up. use if you don't want to build auth screens.
- **NextAuth (Auth.js)** — flexible, self-hosted auth. use if you need custom providers or want full control.
- **Supabase Auth** — use if you already picked Supabase for your database. keeps everything in one place.

## rules

### do

- use server components by default — only use "use client" when you need interactivity
- validate all inputs with Zod on the server
- use TypeScript strict mode — no `any`
- write error boundaries for user-facing routes
- use the existing component patterns in `components/`

### don't

- don't pass secrets to client components
- don't use `alert()` — use the Toast component from `components/ui/toast`
- don't create new files in root — put code in the right directory
- don't skip error handling on database queries
- don't hardcode API URLs — use `process.env.NEXT_PUBLIC_API_URL`

## code style

- components: PascalCase (`UserProfile.tsx`)
- utils: camelCase (`formatDate.ts`)
- pages/routes: kebab-case (`app/user-profile/page.tsx`)
- group routes with `(group)` folders for layout-only directories
- barrel exports from `components/index.ts` — don't deep-import

## architecture

```
app/              ← routes (app router)
components/       ← reusable UI components
lib/              ← utilities, db client, auth helpers
prisma/           ← database schema
hooks/            ← custom React hooks
types/            ← shared TypeScript types
```

## how to run

```bash
npm install
npm run dev          # dev server on localhost:3000
npm run build        # production build
npm run lint         # ESLint
npm run typecheck    # TypeScript check
```

## testing

- vitest for unit tests, playwright for e2e tests
- tests live next to the code they test: `component.test.tsx`
- run `npm run test` for unit tests, `npm run test:e2e` for e2e

### what to test

- **always test:** API routes, server actions, utility functions, auth guards
- **usually test:** complex components with state, form validation, error boundaries
- **skip testing:** simple presentational components, layout files, static pages

### test patterns

```tsx
// unit test — lib/formatDate.test.ts
import { formatDate } from "./formatDate";
test("formats ISO date to readable string", () => {
  expect(formatDate("2025-01-15")).toBe("Jan 15, 2025");
});

// component test — components/UserCard.test.tsx
import { render, screen } from "@testing-library/react";
import { UserCard } from "./UserCard";
test("displays user name", () => {
  render(<UserCard name="Alice" />);
  expect(screen.getByText("Alice")).toBeInTheDocument();
});

// API route test — app/api/users/route.test.ts
test("GET /api/users returns 401 without auth", async () => {
  const res = await GET(new Request("http://localhost/api/users"));
  expect(res.status).toBe(401);
});
```

## security

- see `SECURITY.md`
- all auth checks happen on the server
- RLS enabled on database (if using Supabase)
- no secrets in client code
