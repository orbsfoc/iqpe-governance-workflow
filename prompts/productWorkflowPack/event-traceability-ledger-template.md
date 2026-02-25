# Event Traceability Ledger Template

Use this file as `docs/handoffs/event-traceability-ledger.md` when eventing/Kafka is in scope.

## Event inventory
| Event ID | Event Type | Topic/Stream | Producer | Consumers | Schema Version | Key Strategy | Ordering Scope |
|---|---|---|---|---|---|---|---|
| EVT-001 | <type> | <topic> | <service> | <service-a,service-b> | v1 | aggregate_id | per-aggregate |

## Traceability mapping
| REQ ID | PLAN ID | DIAG ID | Event ID | TEST IDs | DEF IDs | TC IDs |
|---|---|---|---|---|---|---|
| REQ-001 | PLAN-001 | DIAG-001 | EVT-001 | TEST-API-001 | DEF-001 | TC-001 |

## Producer/consumer reliability controls
- Producer pattern used (outbox/direct):
- Consumer idempotency strategy:
- Retry policy:
- DLQ policy:
- Replay/backfill procedure:

## Observability and SLOs
- Lag SLO:
- End-to-end latency SLO:
- Alert thresholds:
- Ownership/escalation:

## ADR and planning references
- ADR IDs applied:
- Planning behavior profile id/source/version:
- Workflow decisions influencing event design:
