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

## docker

```bash
docker compose up                # start API + Postgres
docker compose up -d             # start in background
docker compose down              # stop everything
docker compose build             # rebuild after dependency changes
```

## pre-commit hooks

```bash
pip install pre-commit
pre-commit install               # set up hooks
pre-commit run --all-files       # run on everything once
```
