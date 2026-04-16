# repo-brain

a starter template for building repos that AI agents actually understand.

if you've ever felt like you're fighting your AI coding tool every session — giving it the same context over and over, watching it make the same mistakes, or getting output that ignores your project's patterns — this is why. you're not giving it a brain.

these files are the brain.

## what's in here

| file | what it does |
|------|-------------|
| `AGENTS.md` | the rulebook. how AI agents should behave in this repo |
| `CLAUDE.md` | claude code specific config — imports AGENTS.md so you don't duplicate |
| `SOUL.md` | your project's personality, voice, and design philosophy |
| `USER.md` | who you're building this for — keeps the AI focused on the actual user |
| `TOOLS.md` | tool-specific notes, API references, environment setup |
| `SECURITY.md` | pre-flight checklist for common AI-generated security mistakes |

## quick start

1. copy the files you need into your project root
2. edit each one to match your project
3. delete the ones you don't need (you probably don't need all six)
4. start coding — the AI will pick these up automatically

## which files do i actually need?

**minimum viable setup:**
- `AGENTS.md` — this one file does 80% of the work

**recommended setup:**
- `AGENTS.md` + `CLAUDE.md` — if you use claude code, cursor, or codex

**full setup:**
- all six files — for complex projects or when you want maximum control

## why this works

AI coding tools read files at the root of your repo before every task. they're looking for context. if you don't give them anything, they use their training data and guess. if you give them clear instructions, they follow them.

it's the difference between "write me an app" and "write me an app that follows these exact patterns, uses these tools, avoids these mistakes, and knows who it's for."

## structure

```
your-project/
├── AGENTS.md          # ← AI reads this first
├── CLAUDE.md          # ← specific to claude code (imports AGENTS.md)
├── SOUL.md            # ← project identity
├── USER.md            # ← who this is for
├── TOOLS.md           # ← tool-specific notes
├── SECURITY.md        # ← security checklist
├── src/               # ← your code
├── docs/              # ← detailed docs AI can reference when needed
└── ...
```

## how each AI tool picks these up

| tool | reads automatically | notes |
|------|-------------------|-------|
| claude code | `CLAUDE.md`, `AGENTS.md` | both are loaded by default |
| cursor | `.cursor/rules/`, `CLAUDE.md` | also reads AGENTS.md in recent versions |
| openai codex | `AGENTS.md` | looks for agent instructions at root |
| gemini cli | `AGENTS.md` | follows the same convention |

## what to put in each file

see the individual files in this repo for working examples. each one has comments explaining what goes where and why.

## examples

check `examples/` for pre-filled templates for different project types:
- a next.js web app
- a python api
- a mobile app

## pro tips

- **keep it short.** AI tools have context windows. every word in these files costs tokens. be specific, not verbose.
- **don't duplicate.** if something is in AGENTS.md, don't repeat it in CLAUDE.md. use imports/includes instead.
- **update as you go.** when you establish a pattern, document it. future-you and future-AI will thank you.
- **don't include obvious stuff.** "write clean code" wastes tokens. be specific: "use zod for all input validation" is useful.
- **put heavy docs in `docs/`.** link to them from AGENTS.md instead of pasting full documentation into the root files.

## security

see `SECURITY.md` for a checklist of things AI agents commonly miss — row-level security, auth bypasses, hardcoded secrets, etc.

## contributing

if you find a pattern that works well, open a PR. this template is built by people who actually use AI to build things.

---

## license

MIT. do whatever you want with these.

## about

made by [@BChopLXXXII](https://x.com/BChopLXXXII)

built for vibe coders who just want their AI to feel less... corporate.

ship it. 🚀

if this helped, ⭐ the repo — it helps others find it.
