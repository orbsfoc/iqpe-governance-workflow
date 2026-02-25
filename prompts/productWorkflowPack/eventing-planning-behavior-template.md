# Eventing Planning Behavior Template

Use this template to define event-driven boundaries and guarantees.

## Decision summary
- Eventing required for these flows:
- Broker/transport selected:
- Why synchronous-only is insufficient (if applicable):

## Event contract policy
- Delivery semantics (default): at-least-once
- Ordering scope: per aggregate/entity key
- Schema versioning strategy:
- Compatibility policy (forward/backward):
- Dead-letter and retry policy:
- Idempotency strategy for consumers:

## Kafka producer/consumer patterns (mandatory when Kafka is used)
- Producer generation pattern (transactional outbox/direct):
- Producer idempotency strategy:
- Consumer dedupe/idempotency strategy:
- Partition key strategy and ordering assumptions:
- Replay/backfill procedure:

Required event envelope fields:
- `event_id`, `event_type`, `schema_version`, `aggregate_id`, `correlation_id`, `causation_id`, `occurred_at`, `producer_service`, `traceparent`

## Topic/stream design
| Topic/stream | Producer | Consumers | Key | Ordering needed | Retention | Replay required |
|---|---|---|---|---|---|---|

## Operational controls
- Lag/throughput SLOs:
- Poison message handling:
- Backpressure strategy:
- Reprocessing/replay runbook:
- Observability (trace IDs, correlation IDs, metrics):

## Gate checks
- [ ] Event schemas are versioned and ownership is assigned.
- [ ] Consumers are idempotent.
- [ ] Retry + DLQ behavior is defined.
- [ ] Ordering assumptions are explicit and testable.
- [ ] Replay and recovery procedure is documented.
- [ ] Event traceability ledger exists (`docs/handoffs/event-traceability-ledger.md`) with REQ/PLAN/DIAG/TEST/DEF/TC mappings.
