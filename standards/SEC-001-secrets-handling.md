# SEC-001: Secrets handling

- Status: current (mandatory)
- Date: 2024-07-15, tightened 2025-06-30
- Owner: Jonas Bakker (security champion)
- Origin: findings F-004 (API key committed in a config file), F-014 (key printed in a log line)

## Rules
1. No secret ever appears in a source file, config file, test fixture or
   commit. This includes "example" keys that are real.
2. Code obtains secrets only through `app/src/lib/secrets.ts` (`getSecret`).
   Direct `process.env.SOMETHING_KEY` reads outside that module fail review.
3. Secrets are never logged. Log the name of the secret if you must, never
   the value, never a prefix.
4. `.env` is gitignored. `.env.example` lists keys with placeholder values.
5. A new secret means: add it to `.env.example`, to the Vault path list in
   the deployment repo, and mention it in the pull request.

## Enforcement
Prose (this document), pull request checklist item, gitleaks in pre-commit
and CI. Level 3 of the ladder in CONV-005.
