# CONV-005: The enforcement ladder

- Status: current
- Owner: Mara Visser
- Date: 2025-04-02

A rule that only lives in a document is an honor system. Every rule in this
wiki is at one of four levels, and we try to move rules up over time:

1. Prose: the ADR or standard states it.
2. Checklist: it is an item in the pull request template.
3. Template or helper: the right way is the easy way (a helper in `lib/`, a
   scaffold, a starter file).
4. Gate: CI or a pre-commit hook rejects the violation.

Current state: ADR-003 is at level 1 (a dependency check is planned).
SEC-001 is at level 4 (gitleaks). ADR-007 is at level 1 and has bitten us
once, so it is the next candidate for a test gate. CONV-004 is at level 3.
