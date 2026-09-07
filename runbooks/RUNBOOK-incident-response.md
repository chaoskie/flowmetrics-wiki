# Runbook: incident response

- Owner: Priya Nair (SRE)
- Last reviewed: 2026-01-12

1. Declare: post in `#incidents` with a one-line impact statement, take the
   incident commander role or name one.
2. Stabilise: roll back the last deploy first, investigate second. A rollback
   that was not needed costs ten minutes; a slow investigation costs hours.
3. Communicate: status page update within 15 minutes, then every 30.
4. Resolve and confirm with the on-call for the affected tenants.
5. Post-mortem within five working days. Blameless. Every finding gets a
   record in `findings.json` with a `pattern`, and every "we should never do
   this again" becomes or updates an ADR or standard with an origin note.

The last step is why this wiki exists.
