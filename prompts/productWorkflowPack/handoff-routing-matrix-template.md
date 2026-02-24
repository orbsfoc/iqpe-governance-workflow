# Handoff Routing Matrix Template

Use this matrix to record producer/consumer routing, acceptance ownership, and acknowledgment evidence for each phase handoff.

## Matrix
| Handoff ID | From Phase | To Phase | Artifact Bundle Path | Receiver Role | Receiver Name | Ack Status | Ack Timestamp (UTC) | Ack Evidence Path |
|---|---|---|---|---|---|---|---|---|
| HO-001 | 01 | 02 | docs/handoffs/po/ | architect | <name> | PENDING |  |  |

## Rules
- Every phase transition must have an `ACKED` row before the next phase can be `PASS`.
- Missing receiver assignment or missing acknowledgment evidence is `BLOCKED`.
- Use deterministic paths for handoff bundles to keep traceability stable.
