# Onboarding: your first week on FlowMetrics billing

- Status: current (revised 2026-07). The 2024 edition is stale, do not follow it.

Welcome. Read in this order:

1. the wiki `README.md` and this file.
2. ADR-001, ADR-002, ADR-003, ADR-005, ADR-007, ADR-012. They explain most
   of the shape of `app/`. Read the status header of every ADR first;
   superseded ones are kept on purpose.
3. SEC-001, SEC-002 and CONV-001 to CONV-005 (the current CONV-004, not the v1 file).
4. `findings.json`. Skim the `pattern` field. You will notice one pattern
   dominates. That is why ADR-005 exists.

Your first pull request will be reviewed against the checklist in
`review-process.md`. The most common review comments for newcomers, in
order: wrote a helper that already exists in `lib/` (CONV-004), added a
dependency without checking ADR-003, read `process.env` directly (SEC-001),
touched the payment client without reading ADR-007 and ADR-012, touched a
route without reading SEC-002.
