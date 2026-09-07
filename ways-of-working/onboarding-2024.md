# Onboarding (2024 edition)

- Status: stale. Kept because links to it exist in old tickets. Use `onboarding.md`.

Welcome to FlowMetrics billing. Clone the repo, run `npm install`, and read
ADR-001 to ADR-005. We use `axios` for outbound calls (see
`lib/http-client.ts`) and the config lives in `config/*.yaml` per
environment. Ask Mara for the staging `.env`.

Your first task is usually a small route change. Express 4 docs are at
expressjs.com.
