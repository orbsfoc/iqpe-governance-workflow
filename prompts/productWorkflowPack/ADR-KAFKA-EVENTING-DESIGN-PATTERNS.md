# ADR — Kafka Eventing Design Patterns and Reliability Controls

Status: APPROVED (authoritative when Kafka is selected)

## Context
Kafka-based eventing provides scalable asynchronous integration, but reliability and traceability depend on disciplined producer/consumer patterns.

## Decision
When Kafka is used, apply the following mandatory patterns and controls.

## Producer patterns
- Use Transactional Outbox for business state + event publication consistency.
- Prefer idempotent producers and stable event keys.
- Partition by aggregate/entity key when ordering is required.
- Use explicit event envelope fields:
  - `event_id`
  - `event_type`
  - `schema_version`
  - `aggregate_id`
  - `correlation_id`
  - `causation_id`
  - `occurred_at`
  - `producer_service`
  - `traceparent`

## Consumer patterns
- Use idempotent consumer handling (dedupe by `event_id` or Inbox pattern).
- Treat processing as at-least-once by default.
- Define retry tiers and DLQ routing for poison events.
- Make ordering assumptions explicit by partition key.
- Document replay/backfill procedures and divergence recovery.

## Schema and compatibility
- Use schema registry or equivalent contract governance.
- Enforce compatibility mode per topic (backward/forward/full as required).
- Version event schemas explicitly; no silent breaking changes.

## Operability and SLOs
- Monitor lag, throughput, redelivery, DLQ rate, and schema rejection rate.
- Define alert thresholds and owner escalation paths.
- Define retention/compaction policy per topic.

## Security and governance
- Define topic ownership and ACL boundaries by producer/consumer group.
- Classify event payload sensitivity and apply masking/encryption requirements.
- Avoid PII leakage in events unless explicitly approved and controlled.

## Consequences
- Improves event reliability and incident diagnosability.
- Adds required operational and schema-governance discipline.
- Reduces hidden coupling and replay risk.
