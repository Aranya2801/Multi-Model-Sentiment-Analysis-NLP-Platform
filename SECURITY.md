# Security Policy

## Supported Versions

| Version | Supported |
|---|---|
| 1.x | ✅ |

## Reporting a Vulnerability

If you discover a security vulnerability, please **do not open a public
issue**. Instead:

1. Email the maintainers (or use GitHub's private "Report a vulnerability"
   feature under the Security tab) with a description of the issue, steps
   to reproduce, and potential impact.
2. Allow a reasonable window for a fix before any public disclosure.
3. We'll acknowledge receipt within a few days and keep you updated as we
   work on a fix.

## Security Practices in This Project

- **Secrets**: never commit `.env` files. `SECRET_KEY` must be a long,
  random value in production — see `.env.example`.
- **Passwords**: hashed with bcrypt (`passlib`); never stored or logged in
  plaintext.
- **Auth**: short-lived JWT access tokens (default 30 min) with separate
  longer-lived refresh tokens.
- **Input validation**: all request bodies are validated via Pydantic
  schemas (length limits, type checking) before reaching business logic.
- **Rate limiting**: `slowapi` limits requests per IP to mitigate abuse
  and runaway inference costs.
- **Dependencies**: pinned versions in `requirements.txt`; review Dependabot
  / `pip-audit` alerts before merging dependency bumps.
- **CORS**: configured via `BACKEND_CORS_ORIGINS`; restrict this to known
  origins in production rather than `*`.

## Known Limitations (please account for these in production)

- The default `docker-compose.yml` uses hardcoded demo credentials for
  Postgres (`sentiment`/`sentiment`) — change these for any non-local
  deployment.
- `/sentiment/analyze` is intentionally public (no auth) in this scaffold
  to make the demo easy to try. Add `Depends(get_current_user)` to that
  route if you need to restrict access.
- Model inference runs in-process; a malicious actor submitting extremely
  long or adversarial text could increase resource consumption. The
  `max_length=8000` Pydantic constraint and rate limiting mitigate but do
  not eliminate this.
