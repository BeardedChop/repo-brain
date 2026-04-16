# AGENTS.md

this file tells AI coding agents how to behave in this FastAPI project.

## project overview

a REST API built with FastAPI, using SQLAlchemy for the ORM and [database] for storage.

## tech stack

- **framework:** FastAPI
- **language:** Python 3.12+
- **ORM:** SQLAlchemy 2.0
- **database:** PostgreSQL
- **auth:** JWT tokens
- **deployment:** Docker + [railway/fly.io/render]

## rules

### do

- use Pydantic v2 models for all request/response schemas
- add type hints to every function
- use dependency injection for DB sessions and auth
- put routes in `routers/`, not in main.py
- add docstrings to every endpoint

### don't

- don't use `SELECT *` — always specify columns
- don't return raw SQLAlchemy models — use Pydantic schemas
- don't put business logic in route handlers — use services
- don't skip error handling on database operations
- don't hardcode database URLs — use environment variables

## code style

- snake_case for everything (files, functions, variables)
- one route per file in `routers/`
- services go in `services/`
- schemas go in `schemas/`
- models go in `models/`

## architecture

```
app/
├── main.py           ← FastAPI app entry point
├── routers/          ← API routes
├── services/         ← business logic
├── models/           ← SQLAlchemy models
├── schemas/          ← Pydantic schemas
├── core/             ← config, security, middleware
└── database.py       ← DB connection
```

## how to run

```bash
python -m venv venv
source venv/bin/activate    # or venv\Scripts\activate on Windows
pip install -r requirements.txt
uvicorn app.main:app --reload
```

## testing

- pytest in `tests/`, run with `pytest`
- use TestClient for endpoint tests
- use factory_boy or faker for test data
- mirror `app/` structure in `tests/`: `tests/routers/`, `tests/services/`

### what to test

- **always test:** every endpoint (happy path + error cases), service functions, auth/permission guards
- **usually test:** schema validation, database queries with edge cases, middleware behavior
- **skip testing:** config loading, simple CRUD wrappers with no logic

### test patterns

```python
# tests/routers/test_users.py
from fastapi.testclient import TestClient
from app.main import app

client = TestClient(app)

def test_get_users_requires_auth():
    response = client.get("/api/v1/users")
    assert response.status_code == 401

def test_create_user(auth_headers, db_session):
    response = client.post(
        "/api/v1/users",
        json={"email": "new@example.com", "name": "New User"},
        headers=auth_headers,
    )
    assert response.status_code == 201
    assert response.json()["email"] == "new@example.com"

# tests/services/test_user_service.py
def test_get_user_by_email_not_found(db_session):
    user = user_service.get_by_email(db_session, "nope@example.com")
    assert user is None
```

## security

- see `SECURITY.md`
- all endpoints require auth unless explicitly public
- CORS configured for specific origins only
- rate limiting on public endpoints
