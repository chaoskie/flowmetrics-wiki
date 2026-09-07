# Team meeting 2025-03-24

Present: Mara, Jonas, Priya, Tom, Sanne, Ruben

- INC-2025-03 post-mortem accepted. Findings F-013 recorded.
- Retry policy: agreed, five attempts everywhere, 500 ms base. Mara writes
  it up (became ADR-009). Nobody wants to discuss retry counts in review
  again.
- Tom: the usage client now uses `withRetry`. Payment client still has no
  retry at all; parked until the idempotency header is in (ADR-007).
- Sanne moves to the collector team in April.
