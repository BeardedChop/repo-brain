# TOOLS.md

## environment

- python 3.12+
- virtual environment: venv
- database: PostgreSQL

## env vars

```
DATABASE_URL=postgresql://user:pass@localhost:5432/dbname
SECRET_KEY=
CORS_ORIGINS=http://localhost:3000,http://localhost:5173
```

## common commands

```bash
uvicorn app.main:app --reload    # dev server
pytest                           # run tests
alembic upgrade head             # run migrations
alembic revision -m "message"    # create migration
```
