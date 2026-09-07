# ADR-009: One retry policy for every upstream call: five attempts

- Status: superseded by ADR-012 (2026-06-15) for payment provider calls; still applies to the usage collector until CONV-004 is revised
- Date: 2025-03-24
- Owner: Mara Visser
- Origin: INC-2025-03 (finding F-013), the retry discussion in the 2025-03-24 team meeting

## Context
After the usage collector incident every client had its own idea of how
often to retry. Reviewers asked for one number.

## Decision
`withRetry` defaults to five attempts with a 500 ms base delay. Clients use
the default unless an ADR says otherwise.

## Consequences
- One number to remember. Reviewers stop arguing about it.
- (2026-06) The payment provider rate-limits retries. Five attempts at
  500 ms tripped their limiter. See ADR-012. This ADR stays for the usage
  collector only.
