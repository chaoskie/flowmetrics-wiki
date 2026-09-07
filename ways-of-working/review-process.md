# Review process and pull request checklist

Every pull request has one reviewer from the billing team. The author fills
in the checklist; the reviewer verifies it.

- [ ] I searched `app/src/lib/` before adding a helper (CONV-004).
- [ ] No new dependency, or the PR explains why and it is not an HTTP client (ADR-003).
- [ ] No secret in code, config, tests or logs (SEC-001).
- [ ] Payment provider calls carry a deterministic idempotency key (ADR-007).
- [ ] Payment retries: at most three attempts, two second base delay (ADR-012).
- [ ] Change touches `routes/` or `app.ts`: framework major upgraded or exception recorded (SEC-002).
- [ ] Inputs validated at the route (CONV-003).
- [ ] Logs are structured and secret-free (CONV-002).
- [ ] New metrics follow ADR-008 naming and cardinality rules.
- [ ] Tests added or updated, `npm test` green.
