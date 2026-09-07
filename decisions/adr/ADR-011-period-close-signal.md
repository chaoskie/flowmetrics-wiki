# ADR-011: Billing waits for the collector's period-close signal

- Status: accepted
- Date: 2025-11-03
- Owner: Mara Visser
- Origin: INC-2024-03 (F-001) and a repeat in 2025-10 (F-026): billing priced a period the collector had not closed

## Decision
The billing run for a period starts only after the usage collector has
published `period.closed` for that period on the events topic. A manual run
without the signal requires the `force` flag and an incident-channel
message.

## Consequences
- Runbook step 1 is a hard gate, not advice.
- The billing worker (ADR-006) subscribes to the topic.
