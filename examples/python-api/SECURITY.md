# SECURITY.md

pre-flight security checklist for AI-generated code.

80% of AI-generated code has security flaws. this checklist catches the common ones.
run through this before deploying anything.

## critical checks

### authentication & authorization

- [ ] all routes that need auth are protected
- [ ] role-based access control is enforced at the API level, not just the UI
- [ ] no admin functions accessible without admin role
- [ ] session tokens expire and rotate properly
- [ ] no tokens or API keys in client-side code

### database security

- [ ] row-level security (RLS) enabled if using Supabase
- [ ] no raw SQL queries — use parameterized queries or ORM
- [ ] database credentials not hardcoded in source
- [ ] public API keys have minimal permissions
- [ ] no database dumps or backups in the repo

### input validation

- [ ] all user input validated server-side (not just client-side)
- [ ] file uploads have type and size limits
- [ ] no eval(), Function(), or dangerouslySetInnerHTML without sanitization
- [ ] URL parameters validated
- [ ] form submissions rate-limited

### secrets & environment

- [ ] no API keys, tokens, or secrets in source code
- [ ] .env files in .gitignore
- [ ] secrets loaded from environment variables only
- [ ] no secrets in error messages or logs
- [ ] use a secret manager for production (Vercel env vars, etc.)

### common AI mistakes

- [ ] AI didn't generate hard-coded data instead of real database calls
- [ ] AI didn't skip error handling on async operations
- [ ] AI didn't expose internal IDs that could enumerate users
- [ ] AI didn't create default admin accounts with known credentials
- [ ] AI didn't leave debug endpoints accessible in production

## testing security

run these tests before deploying:

1. **unauthenticated access:** try to access protected routes without logging in
2. **role escalation:** try to access admin features as a regular user
3. **injection:** try SQL injection and XSS on all user inputs
4. **token replay:** try using an expired or revoked token
5. **data enumeration:** try accessing other users' data by guessing IDs

## tools

- [supabase RLS checker](https://supabase.com/docs/guides/auth/row-level-security)
- [OWASP top 10](https://owasp.org/www-project-top-ten/)
- [dependency audit](https://docs.npmjs.com/cli/commands/npm-audit)

## logging & monitoring

### do

- [ ] log authentication events (login, logout, failed attempts)
- [ ] log authorization failures (access denied)
- [ ] log unexpected errors with stack traces (server-side only)
- [ ] use structured logging (JSON format) — use `structlog` or `python-json-logger`
- [ ] include request IDs for tracing (use middleware to inject)

### don't

- [ ] no secrets, tokens, or API keys in log output
- [ ] no passwords (even hashed ones) in logs
- [ ] no PII in production logs unless required and encrypted
- [ ] no full request/response bodies — log summaries instead
- [ ] no stack traces in user-facing error responses
- [ ] no debug-level logging enabled in production

## when to escalate

if you find any of these, stop and get human review:
- any data exposure to unauthenticated users
- broken authentication
- any way to access another user's data
