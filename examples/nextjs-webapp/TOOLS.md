# TOOLS.md

## environment

- node 20+
- package manager: npm (or pnpm if you prefer)
- deploy: Vercel

## env vars

see `.env.example` for required variables. never commit `.env.local`.

```
DATABASE_URL=
NEXT_PUBLIC_API_URL=
AUTH_SECRET=
```

## common commands

```bash
npm run dev          # start dev server
npm run build        # production build
npm run lint         # ESLint
npm run typecheck    # tsc --noEmit
npx prisma generate  # regenerate prisma client
npx prisma migrate   # run migrations
```

## known issues

- Vercel deployment: make sure env vars are set in the Vercel dashboard
- Prisma: regenerate client after schema changes
- Hot reload: sometimes need to restart dev server after adding new route files
