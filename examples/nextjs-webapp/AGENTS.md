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

- vitest for unit tests
- playwright for e2e tests
- tests live next to the code they test: `component.test.tsx`

## security

- see `SECURITY.md`
- all auth checks happen on the server
- RLS enabled on database (if using Supabase)
- no secrets in client code
