# CONV-004 (v1, March 2025): Reuse the shared helpers

- Status: superseded by the current CONV-004 (same id, 2025-03-18 revision). Kept for history.
- Owner: Mara Visser
- Date: 2025-03-11

Retries go through `withRetry`. Use five attempts everywhere so reviewers do
not have to think about it. Do not write your own loop.

HTTP goes through `httpJson`. Secrets go through `getSecret`.
