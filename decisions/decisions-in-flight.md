# Decisions in flight

- Status: living document, updated in the fortnightly architecture meeting
- Last update: 2026-08-24

| Topic | State | Owner | Notes |
| --- | --- | --- | --- |
| Express 5 upgrade | agreed, not scheduled | Jonas | SEC-002 makes it mandatory when routes are touched. Nobody has touched routes since March. |
| Idempotency header in `PaymentClient` | agreed since ADR-007, still open | Mara | Embarrassing. First item of the payment backlog for eighteen months. Whoever adds retry does this first. |
| Retry gate in CI for payment calls | proposed | Priya | Test that fails if `PaymentClient` retries without the header, or with more than three attempts (ADR-012). |
| Dependency check for ADR-003 | proposed | Jonas | Fail CI when `axios`, `got`, `node-fetch` or `superagent` appear in the lockfile. |
| Metrics endpoint | decided (ADR-008), not built | Priya | Runbook already refers to the counters. |
| Worker for billing runs | decided (ADR-006), in progress | Mara | Behind the events topic (ADR-011). |
