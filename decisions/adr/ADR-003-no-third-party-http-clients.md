# ADR-003: No third-party HTTP client libraries, use lib/http.ts over fetch

- Status: accepted
- Date: 2024-11-28
- Owner: Jonas Bakker (platform)
- Origin: INC-2024-11 (finding F-007)

## Context
On 2024-11-19 a transitive dependency of the HTTP client library we used
(`axios` at the time) shipped a version that changed default redirect
handling. Our payment calls followed a redirect to a staging host, dropped
the authorization header on the way and failed silently for four hours.
Root cause analysis (F-007) showed we had three different HTTP clients in
the codebase with three different timeout and header behaviours.

## Decision
Third-party HTTP client libraries (axios, got, node-fetch, superagent,
undici-request wrappers and similar) are banned in this repository. All
outbound HTTP goes through `app/src/lib/http.ts`, which wraps the built-in
`fetch` with one timeout policy, one header policy and one error type
(`UpstreamError`).

## Consequences
- One place to fix header, timeout and redirect behaviour.
- Adding `axios` or `got` to `package.json` fails review. A CI dependency
  check is planned (see CONV-005 enforcement ladder).
- Pull requests that touch outbound calls must reference this ADR.
