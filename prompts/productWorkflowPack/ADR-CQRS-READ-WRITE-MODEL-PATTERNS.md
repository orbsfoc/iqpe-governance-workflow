# ADR — CQRS and Read/Write Model Patterns

Status: APPROVED (conditional baseline)

## Context
Some domains require independent optimization of command-side consistency and query-side performance. Applying CQRS indiscriminately adds complexity.

## Decision
Use CQRS selectively when complexity is justified; otherwise use a simpler unified model.

## When CQRS is recommended
- Read and write workloads have significantly different access patterns.
- Query model requires denormalized projections for latency/scale targets.
- Domain write-side invariants are complex and must remain protected from query concerns.
- Event-driven integration naturally supports projection updates.

## When CQRS is not recommended
- Small/simple domains with low read/write asymmetry.
- Teams without operational capacity for projection lag/replay management.
- No measurable performance/scalability pressure requiring model split.

## Mandatory controls when CQRS is used
- Define command model ownership and invariants.
- Define read model ownership and projection update strategy.
- Define consistency expectations (eventual consistency window/SLO).
- Define replay/backfill procedures for projections.
- Define idempotency and ordering assumptions for projection consumers.
- Define monitoring for projection lag and data divergence.

## Traceability requirements
- Link each CQRS decision to `REQ/PLAN/DIAG/TEST/TC` artifacts.
- Record ADR ledger entries for read/write split rationale.
- Include diagrams showing command flow, event flow, and query flow.

## Consequences
- Positive: better scalability and query performance under the right conditions.
- Trade-off: higher operational complexity and stronger observability requirements.