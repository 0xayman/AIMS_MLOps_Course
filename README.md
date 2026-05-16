# AIMS SA MLOps Course

This repository contains course materials and project scaffolding for building end-to-end machine learning applications with MLOps practices.

## Repository layout

- `src/students/<github-username>/`: each student’s working area
- `src/students/example/`: reference implementation used by course maintainers
- `tests/`: shared test suite
- `utils/`: shared utility functions
- `.github/workflows/`: CI checks and deployment workflows

## Getting started

### 1) Create your branch

- Branch from `development`
- Use the naming convention: `feature-branch-{your-name}`

### 2) Open in GitHub Codespaces

- Open your branch in Codespaces
- Select the weakest compute specification unless your task requires more resources

### 3) Set up the environment

The devcontainer is configured to install dependencies automatically with `uv sync`.

Useful environment commands:

- `source .venv/bin/activate` — activate the project virtual environment
- `deactivate` — leave the virtual environment
- `which python` — confirm the active Python interpreter
- `uv python find` — show the current uv-managed Python
- `uv pip list` — list installed packages

## Development workflow

Run checks before opening a pull request:

- `uv run ruff check` — linting
- `uv run pyright` — type checks
- `uv run pytest` — unit tests

These checks are also run in GitHub Actions for pull requests targeting `development`.

## Running services

- API (default example app):  
  `uv run uvicorn "api.main:app" --host 0.0.0.0 --port 8080`
- Dagster + MLflow helper script:  
  `./run_dagster.sh`

For container-based runs, the project uses `Dockerfile` + `entrypoint.sh` to select and start the correct student or example API based on environment variables.
