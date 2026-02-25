# ADR — Data Separation and Usage Boundaries

Status: APPROVED (authoritative best-practice baseline)

## Context
Systems often degrade when transactional, analytical, cache, and integration concerns are mixed in a single data model or datastore without explicit boundaries.

## Decision
Adopt strict data separation and usage-boundary practices for planning and implementation.

## Best-practice rules
- Define a clear **system of record** per bounded context.
- Separate **transactional** data from **read-optimized/analytical** data stores.
- Use **cache** as a performance layer only, never as authoritative source-of-truth.
- Keep **integration/export** views separate from internal domain write models.
- Explicitly classify each dataset by sensitivity, retention, durability, and ownership.
- Define ownership for every schema/table/stream/index.

## Data usage categories (minimum)
- Transactional/OLTP (source-of-truth)
- Read/query projections
- Cache/session/ephemeral
- Search/index documents
- Analytics/time-series/observability
- File/object artifacts

## Planning requirements
- Every service/module plan must declare:
  - primary write store
  - read/query store(s)
  - cache usage and invalidation policy
  - retention and archival policy
  - backup/restore expectations (RTO/RPO)
- Cross-context data sharing must use explicit contracts (APIs/events), not direct schema coupling by default.

## Prohibited patterns
- Shared mutable schema across unrelated bounded contexts without explicit governance.
- Reporting queries directly on high-traffic transactional tables when read projection is required.
- Business-critical decisions based on cache-only state.

## Consequences
- Improves scalability and operational predictability.
- Reduces accidental coupling and migration risk.
- Increases clarity of ownership and change impact.