# CLAUDE.md

this file tells claude code how to work on this project.
it imports AGENTS.md so you don't have to duplicate rules.

<!-- imports AGENTS.md -- these rules apply too -->
import AGENTS.md

## claude-specific rules

these override or add to AGENTS.md. things that are specific to how claude code operates.

### before making changes

- read the relevant file(s) first — don't guess what's there
- read docs in `docs/` for framework-specific guidance
- check existing patterns before introducing new ones

### when working on files

- make focused changes — don't touch unrelated code
- preserve existing code style and conventions
- if you rename or move something, update all references
- don't delete code without explaining why

### when unsure

- ask. one or two questions max, then start working
- if a change might break something, flag it
- if there are multiple approaches, pick the simplest one

### output format

- explain what you changed and why (1-2 sentences)
- don't dump the full file if only a few lines changed
- use code blocks with filenames for partial edits
