# Contributing to Sentinel

Thanks for considering a contribution! This project welcomes issues and
pull requests of all sizes.

## Getting Started

1. Fork the repo and clone your fork.
2. Run `bash scripts/setup.sh` to get the stack running locally.
3. Create a branch: `git checkout -b feature/your-feature-name`.

## Development Workflow

### Backend

```bash
cd backend
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python -m spacy download en_core_web_sm

# Run tests (skip model-download tests for fast iteration)
pytest -m "not model"

# Run the full suite, including real model inference
pytest

# Run the dev server with hot reload
uvicorn app.main:app --reload
```

### Code Style

- Python: follow PEP 8; we run `ruff` in CI. Format with `black` if you
  have it available.
- Keep service modules (`app/services/`) free of FastAPI/HTTP concerns —
  they should be pure, testable functions that the API layer calls.
- Add type hints to new functions.

### Commit Messages

We loosely follow [Conventional Commits](https://www.conventionalcommits.org/):

```
feat: add Reddit connector for real-time ingestion
fix: correct entropy calculation in ensemble disagreement score
docs: clarify Kubernetes secret creation steps
test: add coverage for batch sentiment endpoint
```

## Pull Request Checklist

- [ ] Tests pass locally (`pytest -m "not model"` at minimum)
- [ ] New functionality has corresponding tests
- [ ] Updated relevant docs (`docs/`, `README.md`) if behavior changed
- [ ] No secrets or `.env` files committed

## Adding a New Model to the Ensemble

1. Add the HuggingFace model ID to `app/core/config.py`.
2. Write a `_normalize_<model>()` function in
   `app/services/sentiment_engine.py` that maps the model's native labels
   to the canonical `positive` / `negative` / `neutral` space.
3. Add it to `SENTIMENT_MODEL_FNS`.
4. Add a test case in `tests/test_sentiment.py` (mark with `@pytest.mark.model`).

## Reporting Bugs

Open an issue with: steps to reproduce, expected vs. actual behavior, and
relevant logs (`docker compose logs backend`).

## Code of Conduct

This project follows the [Code of Conduct](CODE_OF_CONDUCT.md). Please be
respectful and constructive.
