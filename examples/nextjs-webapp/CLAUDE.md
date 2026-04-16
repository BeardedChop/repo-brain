# CLAUDE.md

claude code config for this Next.js project.
imports AGENTS.md — those rules apply here too.

import AGENTS.md

## next.js specific rules

### before making changes

- read `node_modules/next/dist/docs/` for the latest Next.js patterns — your training data is outdated
- always check if a feature is stable, experimental, or deprecated
- read existing route handlers in `app/` before creating new ones

### app router conventions

- server components are the default
- use `loading.tsx` for loading states
- use `error.tsx` for error boundaries
- use `not-found.tsx` for 404 pages
- server actions go in `actions/` — don't inline them in components

### data fetching

- use server components for data fetching — never fetch in client components
- cache strategy: use `revalidate` tags, not time-based revalidation
- for mutations: use server actions, not API routes

### styling

- Tailwind CSS only — no styled-components or CSS modules
- use `cn()` utility from `lib/utils` for conditional classes
- component variants use `cva` (class variance authority)
