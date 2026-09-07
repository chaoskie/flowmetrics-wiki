# ADR-004: Structured JSON logging, one line per event

- Status: accepted
- Date: 2024-06-03
- Owner: Priya Nair (SRE)
- Origin: INC-2024-05 (finding F-003), log lines could not be correlated across services

## Decision
All logs are single-line JSON with `ts`, `level`, `msg` and free fields.
Use `lib/logger.ts`. Never log secrets, tokens or full request bodies.

## Consequences
Loki queries work across services. CONV-002 carries the day-to-day rule.
