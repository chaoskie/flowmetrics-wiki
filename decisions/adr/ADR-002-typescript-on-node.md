# ADR-002: TypeScript on Node, run directly, minimal dependencies

- Status: accepted
- Date: 2024-02-20
- Owner: Mara Visser
- Origin: kickoff workshop; revisited 2025-09 when Node started running .ts files natively

## Decision
The service is written in TypeScript and runs on Node without a build step.
Express is the only runtime dependency. Every new dependency needs a one-line
justification in the pull request and a check against ADR-003.

## Consequences
- Fast onboarding, small supply-chain surface.
- Type-only syntax only (no enums, no parameter properties), so the files
  stay runnable by Node's type stripping.
