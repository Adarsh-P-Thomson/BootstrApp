# Python Library Integration Notes

Consult these notes when a user requests specific libraries to avoid common configuration pitfalls and outdated practices.

## FastAPI
- **Server**: Always install `uvicorn` alongside FastAPI (`pip install fastapi uvicorn`).
- **Structure**: Create a basic `main.py` and run using `uvicorn main:app --reload`.

## SQLAlchemy
- **Async**: If using FastAPI, recommend `async` drivers (like `asyncpg` for PostgreSQL or `aiosqlite` for SQLite).

## Pytest
- Configuration: Set up a `pytest.ini` file at the root to declare the `testpaths` and `pythonpath` nicely to avoid module discovery errors. 
