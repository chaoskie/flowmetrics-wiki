# CONV-003: Validate at the edge

- Status: current
- Owner: Jonas Bakker
- Date: 2024-09-10
- Origin: F-006, a null tenant id reached the payment provider

Every route validates its inputs before calling a service and returns 400
with a plain error message. Services trust their callers. Do not validate
twice.
