# ADR-006: Billing runs are asynchronous jobs, the HTTP call only enqueues

- Status: accepted
- Date: 2025-01-20
- Owner: Mara Visser
- Origin: INC-2024-12 (finding F-008): a month-end run held an HTTP connection for 40 seconds and the load balancer cut it

## Decision
`POST /billing/runs` accepts the request and returns 202 with a run id. The
actual pricing and charging happens in a worker. (The service still
runs inline; the worker is on the roadmap. The 202 status is already in
place so clients do not depend on a synchronous result.)

## Consequences
- Clients poll or subscribe for the result.
- Retries of the worker step must be safe to repeat, which is why ADR-007
  exists.
