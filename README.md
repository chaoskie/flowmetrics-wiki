# FlowMetrics engineering wiki

FlowMetrics is a fictional 40-person dev shop that meters and bills API
usage. This repository is the billing team's institutional memory:
architecture decision records, security and coding standards, runbooks,
ways of working, meeting notes and `findings.json` with structured
post-mortem findings. It is kept separate from the code on purpose: the
code repository holds what the system does, this one holds why.

Everything here is made up. Nothing refers to a real company.

## How to read this wiki

Every document carries a status header. Read it first.

| Status | Meaning |
| --- | --- |
| `accepted`, `current`, `mandatory` | Binding. Reviewers hold changes against it. |
| `superseded by X` | Kept for history. Follow X, not this. |
| `stale` | Old and wrong in places. Kept because links to it exist. |
| `living document` | Updated in place; check the last-update line. |

Meeting notes are never revised after the meeting. When a note and an ADR
disagree, the ADR wins. When two ADRs disagree, the later one says which
part of the earlier one it replaces.

## Layout

| Folder | What lives there |
| --- | --- |
| `decisions/adr/` | ADR-001 to ADR-012, one decision per file, with owner, date, origin note and status |
| `decisions/decisions-in-flight.md` | What is agreed but not built, and what is proposed |
| `standards/` | SEC-001, SEC-002 (security), CONV-001 to CONV-005 (conventions), plus one superseded revision |
| `runbooks/` | Month-end billing run, incident response |
| `ways-of-working/` | Onboarding (current and the stale 2024 edition), review checklist, definition of done, on-call |
| `meeting-notes/` | Team, security and architecture meetings, on-call handovers, one post-mortem |
| `findings.json` | 30 post-mortem findings with `pattern` and `adr_ref` |

Every binding rule in here is a crystallised incident: the origin note names
the incident or finding that caused it. An engineering harness that can
read this wiki, and knows which documents are current, should stop an
assistant from repeating those incidents.
