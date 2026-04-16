# CLAUDE.md

claude code config for this FastAPI project.
imports AGENTS.md.

import AGENTS.md

## python/fastapi specific rules

### before making changes

- read the existing models and schemas before adding new ones
- check for existing service functions before creating new ones
- follow the dependency injection pattern already in use

### fastapi conventions

- use `APIRouter` for all routes
- add `tags=[]` to every router for OpenAPI docs
- use `HTTPException` for error responses, not custom classes
- paginate list endpoints (offset/limit or cursor)

### pydantic

- use Pydantic v2 syntax (`model_config`, not `Config` class)
- separate request schemas (Create, Update) from response schemas (Read)
- use `Field()` for validation constraints
