# getting started with AI-operable repos

this guide walks you through setting up a project that AI coding tools actually understand.

## the problem

you open Claude Code, Cursor, or Codex. you say "add a login page." it builds something that doesn't match your project. you spend 20 minutes correcting it. next session, same thing happens.

this is because the AI has no idea:
- what your project does
- what patterns you use
- what you've already built
- what tools you're using
- who you're building for

## the fix

put context files at the root of your repo. the AI reads them automatically.

## step 1: start with AGENTS.md

this is the minimum. copy the template, fill in the blanks:

```markdown
# AGENTS.md

## project overview
[one sentence — what does this do?]

## tech stack
- framework:
- language:
- database:

## rules
### do
- [specific pattern or convention]

### don't
- [specific thing to avoid]
```

that's it. 20 minutes of work, infinite improvement to every AI session.

## step 2: add CLAUDE.md if you use Claude Code

if you use Claude Code, add `CLAUDE.md` with:

```markdown
import AGENTS.md

## claude-specific rules
[anything extra for Claude Code]
```

the `import AGENTS.md` line means you don't duplicate rules. Claude Code reads both files.

## step 3: add the rest as you need them

- `SOUL.md` → when you care about UX tone and design philosophy
- `USER.md` → when the AI keeps building for the wrong audience
- `TOOLS.md` → when you need to document environment setup or API references
- `SECURITY.md` → always, if your app handles user data

## what good looks like

bad AGENTS.md:
```
Write clean code. Follow best practices. Be helpful.
```
this is useless. every AI already tries to do this.

good AGENTS.md:
```
Use Zod for all input validation.
Put API routes in app/api/[resource]/route.ts.
Never use alert() — use the Toast component.
Server components only unless you need interactivity.
```
this is specific. the AI can actually follow it.

## the ROI

before: 20 minutes correcting AI output every session
after: AI gets it right the first time

that's 10-15 minutes saved per session. if you code 4 hours a day, that's 2+ sessions. that's 20-30 minutes a day. that's 10+ hours a month.

one file. infinite time savings.
