# AGENTS.md

this file tells AI coding agents how to behave in this repo.
every AI tool that supports agent instructions reads this file automatically.

keep it short. be specific. if you wouldn't say it to a human developer, don't write it here.

## project overview

one sentence. what does this project do?

## tech stack

list what you're actually using. the AI needs to know.

- **framework:**
- **language:**
- **database:**
- **auth:**
- **deployment:**

## rules

### do

- specific things the AI should always do
- example: use zod for all input validation
- example: write tests for new features

### don't

- specific things the AI should never do
- example: don't use alert() for errors
- example: don't commit API keys

## code style

- naming conventions
- file organization
- import order
- any patterns you want consistently applied

## architecture notes

brief description of how this project is structured.
what lives where. what talks to what.

## how to run

```bash
# install
npm install

# dev
npm run dev

# build
npm run build
```

## testing

what testing framework. how to run tests. any conventions.

## committing

- conventional commits? branch naming? PR requirements?
- any hooks or CI rules?

## documentation

- where docs live: `docs/`
- link to external docs if applicable
- "read relevant docs before making changes"

## security

- see `SECURITY.md` for the full checklist
- never hardcode secrets
- always validate input
