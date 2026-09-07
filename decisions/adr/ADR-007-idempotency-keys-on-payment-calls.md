# ADR-007: Every payment provider call carries an idempotency key

- Status: accepted
- Date: 2025-02-10
- Owner: Mara Visser, reviewed by Jonas Bakker
- Origin: INC-2025-02 (finding F-012): a retried month-end run charged 212 tenants twice

## Context
After ADR-006 the billing worker retried a batch that had partially
succeeded. The payment provider treated each retry as a new charge. We
refunded 212 tenants by hand over two days.

The provider supports an `Idempotency-Key` header: identical key, identical
result, no second charge. We were not sending it.

## Decision
Every call that creates or mutates money at the payment provider MUST send
an `Idempotency-Key` header. The key is deterministic from the business
identity of the operation, not random: for a period charge it is
`charge:<tenantId>:<periodId>`. Retrying with the same key is therefore safe
by construction, and any retry logic added to `PaymentClient` must be built
on top of this key, never without it.

## Consequences
- `PaymentClient.charge` must set the header before any retry wrapper is
  added around it. Retry without idempotency is the exact failure of
  INC-2025-02 and fails review.
- Tests assert the header is present and deterministic.
- Status: header not yet implemented in the billing service. Tracked as the
  first item of the payment client backlog.
