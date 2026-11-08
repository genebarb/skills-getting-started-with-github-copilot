# Agent Instructions

## Project Overview

This repository contains a small FastAPI exercise for signing students up for Mergington High School extracurricular activities. The browser UI is served by the same FastAPI process.

## Key Files

- `src/app.py`: API routes, FastAPI setup, static-file mount, and in-memory activity data.
- `src/static/`: Browser UI (`index.html`, `app.js`, and `styles.css`).
- `src/README.md`: Application usage and endpoint documentation.
- `requirements.txt`: Python dependencies.

## Local Commands

From the repository root:

```bash
python -m pip install -r requirements.txt
cd src && python -m uvicorn app:app --reload
pytest
```

The app is served at `http://localhost:8000`; API docs are available at `/docs`.

## Implementation Conventions

- Keep backend changes in `src/app.py` unless a larger structure is clearly justified.
- Activity names are the dictionary keys and route identifiers. URL-encode names in browser requests.
- Participant data is stored in the `activities` dictionaries in memory and resets on server restart.
- The browser UI calls the API with relative paths (`/activities` and `/activities/{name}/signup`).
- Preserve existing JSON response shapes and FastAPI HTTP error behavior unless the task explicitly changes them.
- Validate route changes against both the API and the static UI; update `src/README.md` when endpoint behavior changes.

## Testing

- Use `pytest` for Python tests. Add focused tests for route success cases and expected HTTP errors.
- There is currently no dedicated automated frontend test setup; manually exercise the relevant UI flow when changing `src/static/`.
