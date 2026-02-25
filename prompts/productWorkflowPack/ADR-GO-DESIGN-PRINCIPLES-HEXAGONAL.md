# ADR — Go Design Principles under Hexagonal Architecture

Status: APPROVED (authoritative for Go service/application design)

## Context
This workflow prefers hexagonal architecture. Go implementation choices must apply core design principles in a way that fits Go idioms and operational production requirements.

## Decision
Apply general design principles to Go through explicit hexagonal layering and package conventions.

## Go + Hexagonal application model

### Core layers
- **Domain layer:** entities, value objects, invariants, domain services.
- **Use-case layer:** application workflows, orchestration of domain + ports.
- **Port layer:** interfaces that define inbound and outbound boundaries.
- **Adapter layer:** concrete implementations (HTTP, DB, queue, cache, external APIs).
- **Composition root:** dependency wiring/bootstrap only.

### Principle mapping in Go
- SRP: keep packages and files narrowly focused; avoid "utility dump" packages.
- DIP: use-case/domain depend on interfaces defined at the boundary they own.
- ISP: prefer small interfaces near consumers ("accept interfaces, return structs").
- DRY: share reusable domain logic in domain/use-case layers, not copy across handlers.
- Cohesion/coupling: separate adapter concerns (`internal/adapters/...`) from core (`internal/core/...`).

### Go-specific guidance
- Prefer explicit constructors for dependencies; avoid hidden globals/singletons in core logic.
- Keep `context.Context` at boundaries and long-running operations; do not store it in structs.
- Keep interfaces minimal and colocated with use sites.
- Keep DTO/transport structs separate from domain models.
- Use composition over inheritance-like embedding for behavior reuse.

### Package structure reference
- `internal/core/domain`
- `internal/core/usecase`
- `internal/core/ports`
- `internal/adapters/in/http`
- `internal/adapters/out/postgres`
- `internal/adapters/out/kafka`
- `cmd/<service>/main.go` (composition root)

## Gate criteria
- If adapters import core-internal adapter details, status is `BLOCKED`.
- If domain/use-case depends on concrete transport/persistence packages, status is `BLOCKED`.
- If core behavior cannot be tested without live infrastructure, status is `BLOCKED` unless exception-approved.

## Consequences
- Preserves architecture boundaries as systems grow.
- Improves independent testability of business logic.
- Enables safer upgrades and adapter replacement with lower risk.