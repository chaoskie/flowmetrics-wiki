# ADR-001: FlowMetrics billing is one service, not a platform

- Status: accepted
- Date: 2024-02-12
- Owner: Mara Visser (tech lead, billing)
- Origin: kickoff workshop, February 2024

## Context
FlowMetrics meters API usage for tenants and charges them per period. The
team is small (six engineers on billing) and the first customers wanted
invoices, not a marketplace.

## Decision
One service, `flowmetrics`, owns usage pricing and payment initiation. Usage
collection is an upstream dependency (the collector), payment execution is a
downstream provider. We do not build a plugin platform.

## Consequences
- Clear seams: `clients/usage-client` in, `clients/payment-client` out.
- Feature requests that need a marketplace go to a separate ADR.
