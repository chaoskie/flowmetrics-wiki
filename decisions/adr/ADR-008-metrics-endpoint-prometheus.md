# ADR-008: Metrics are exposed on /metrics in Prometheus text format

- Status: accepted
- Date: 2025-05-06
- Owner: Priya Nair (SRE)
- Origin: F-015, teams invented three incompatible metrics formats

## Decision
Services expose `GET /metrics` in the Prometheus text exposition format.
Counters end in `_total`, durations are histograms in seconds, labels are
low-cardinality (never tenant ids). No metrics library is required for a
handful of counters; a plain text response is fine.

## Consequences
- The billing service should expose at least `billing_runs_total{status}`
  and `payment_retries_total`.
- Tenant ids as labels fail review (cardinality).
