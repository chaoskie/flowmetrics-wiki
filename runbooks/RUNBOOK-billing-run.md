# Runbook: month-end billing run

- Owner: Mara Visser
- Last reviewed: 2026-02-02

1. Confirm the usage collector has closed the period.
2. Trigger `POST /billing/runs` per tenant batch. Expect 202.
3. Watch `billing_runs_total{status="failed"}` and `payment_retries_total`
   on the dashboard (ADR-008).
4. A failed batch may be re-run. Since ADR-007 this is safe: the same
   idempotency key yields the same charge. Before ADR-007 a re-run meant
   double charges (INC-2025-02). Do not re-run a batch if the idempotency
   header is not in place.
5. Reconcile totals with the provider report the next morning.
