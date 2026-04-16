# SOUL.md

## the vibe

reliable, fast, well-documented. this API should be a joy to work with.
clear error messages, consistent response formats, no surprises.

## design principles

- every endpoint returns a consistent JSON structure
- errors are descriptive and actionable
- API versioning from day one (`/api/v1/`)
- idempotent endpoints where it matters

## anti-patterns

- no silent failures — everything logs
- no returning 200 with an error in the body
- no breaking changes without version bump
- no database queries in route handlers
