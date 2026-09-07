# CONV-002: Logging

- Status: current
- Owner: Priya Nair
- Date: 2024-06-03
- Origin: ADR-004

Use `log(level, msg, fields)` from `lib/logger.ts`. No `console.log` in
`src/`. Messages are short lowercase phrases; details go in fields. Never
log secrets or request bodies.
