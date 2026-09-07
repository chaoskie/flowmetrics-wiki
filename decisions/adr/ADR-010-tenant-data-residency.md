# ADR-010: Tenant usage data stays in the EU region

- Status: accepted
- Date: 2025-09-08
- Owner: Jonas Bakker (platform), reviewed by legal (Anouk de Wit)
- Origin: customer contract review, Q3 2025; two enterprise tenants require EU residency

## Decision
Usage records, invoices and payment metadata for EU tenants are stored and
processed in `eu-west` only. The payment provider is called through its EU
endpoint. Cross-region replication is disabled for billing databases.

## Consequences
- Deployment manifests pin the region; a CI check rejects other regions.
- Log shipping stays inside the region (Loki `eu-west`).
- Any new data store needs a residency line in its ADR.
