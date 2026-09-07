# SEC-002: Dependency currency

- Status: current (mandatory)
- Date: 2026-03-02
- Owner: Jonas Bakker (security champion)
- Origin: F-028 (audit finding, Q1 2026): the billing service ran a framework major that had reached end of life; two advisories had no fix on that line

## Rules
1. Runtime dependencies on a major version past its vendor end-of-life are
   a security finding, not a preference.
2. Express 4 reached end of life on 2026-01-31. The billing service is still
   on 4.x. Any change that touches `app/src/routes/` or `app/src/app.ts`
   must either upgrade to the supported major (Express 5) with tests green,
   or record an explicit, dated exception in the pull request description
   with the reason and an owner for the follow-up.
3. Adding a new dependency on an end-of-life line is not allowed.
4. `npm audit` runs in CI at level high. Findings without a fix on the
   current line are exactly the case rule 2 is for.

## Notes for the Express 5 upgrade
Express 5 changed path matching (no more bare `*`), `req.query` is a getter,
and rejected promises from async handlers are forwarded to the error
handler. Our routes are small; the upgrade is expected to be under an hour.

## Enforcement
Prose plus pull request checklist item. A CI gate on the framework major is
planned (CONV-005 level 4).
