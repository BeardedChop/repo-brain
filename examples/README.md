# examples/

pre-filled templates for common project types.
copy the folder you need, edit the placeholders, drop into your project root.

## available templates

- `nextjs-webapp/` — a next.js app with auth, database, and deployment
- `python-api/` — a python REST API with fastapi
- `mobile-app/` — a react native / expo mobile app

each template includes:
- AGENTS.md (filled in with realistic defaults)
- CLAUDE.md
- SOUL.md
- USER.md
- TOOLS.md
- SECURITY.md (adapted for that stack)

## how to use

```bash
# copy the template you need
cp -r examples/nextjs-webapp/* ../my-new-project/

# edit the files to match your project
# (replace bracketed placeholders like [your-app-name])

# done — the AI will pick these up automatically
```
