# ADR-005: Configuration from the environment, secrets through the secrets helper

- Status: accepted
- Date: 2024-07-15
- Owner: Priya Nair (SRE)
- Origin: findings F-002, F-005, F-009 (config drift between environments)

## Context
Seven of our first twelve post-mortems trace back to configuration that
differed between staging and production: a hardcoded URL here, a copied
`.env` there, a secret pasted into a YAML file.

## Decision
Non-secret configuration is read from environment variables in
`app/src/config.ts`, with defaults for local development only. Secrets are
never read from `process.env` directly and never live in config files: they
go through `app/src/lib/secrets.ts` (see SEC-001), which the production
build swaps for the Vault-backed implementation.

## Consequences
- One config module, one secrets module.
- `.env` files are gitignored; `.env.example` documents the keys.
