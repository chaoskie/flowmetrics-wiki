# CONV-004: Reuse the shared helpers, do not write a second one

- Status: current
- Owner: Mara Visser
- Date: 2025-03-18
- Origin: INC-2025-03 (finding F-013): the usage collector client had a hand-rolled retry loop without backoff and kept a recovering upstream down for 25 minutes

## Rule
Retries, timeouts, HTTP calls, logging and secrets have one implementation
each in `app/src/lib/`. In particular:

- Retry with backoff: `withRetry` in `lib/retry.ts`. It has exponential
  backoff, jitter, a retryable-error predicate and a hook for logging. Use
  it. Do not write a `for` loop with `setTimeout` in a client.
- HTTP: `httpJson` in `lib/http.ts` (ADR-003).
- Secrets: `getSecret` in `lib/secrets.ts` (SEC-001).

If the helper does not do what you need, extend it in place and add a test.

## Enforcement
Prose plus review checklist. `usage-client.ts` is the reference usage.
