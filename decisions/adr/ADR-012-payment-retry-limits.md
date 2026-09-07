# ADR-012: Payment provider calls retry at most three times, two second base delay

- Status: accepted, supersedes ADR-009 for payment calls
- Date: 2026-06-15
- Owner: Mara Visser, with Priya Nair (SRE)
- Origin: INC-2026-05 (finding F-027): the provider rate-limited our account for eleven minutes after a burst of retries

## Context
On 2026-05-29 a partially failing month-end batch retried each charge five
times with a 500 ms base delay (ADR-009 default). The provider's limiter
counts retries per account, not per tenant. After roughly two hundred
retries in a minute it returned 429 for everything and locked the account
for eleven minutes. The batch failed for every remaining tenant.

The provider's integration guide, which we had not read since 2024, states:
at most three attempts per charge, exponential backoff starting at two
seconds, honour `Retry-After`.

## Decision
Calls to the payment provider use `withRetry` with `attempts: 3` and
`baseDelayMs: 2000`. `Retry-After` is honoured when present. This overrides
the ADR-009 default for the payment client only. The usage collector keeps
its own setting.

## Consequences
- `PaymentClient` passes these options explicitly; the defaults in
  `lib/retry.ts` are not the payment policy.
- A charge that fails three times is left to the next run (safe because of
  ADR-007).
- Reviewers: a payment retry with more than three attempts or a base delay
  below two seconds fails review. Older notes that say "five attempts
  everywhere" are stale.
