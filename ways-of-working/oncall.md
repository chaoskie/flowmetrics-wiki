# On-call

- Status: current
- Owner: Priya Nair (SRE)

Billing has a one-week rotation of two people (primary, secondary). Month
end (last two and first two days of the month) always has the tech lead as
secondary. Pages come from the `billing_runs_total{status="failed"}` rate
alert and from the provider's status webhook. Handover notes go in
`meeting-notes/` with the `oncall-` prefix.
