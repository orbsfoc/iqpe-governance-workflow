# ADR — Go Implementation Standards (Production Baseline)

Status: APPROVED (authoritative for Go implementation in this workflow pack)

## Context
Go services and tooling must remain maintainable as systems scale. Teams need concrete, reviewable implementation limits for file size, file focus, package boundaries, test structure, and production-grade operability.

## Decision
Adopt mandatory Go implementation standards for all production and tooling code generated or modified under this workflow.

## Standards

### 1) File size and focus targets
- One file, one primary responsibility.
- Target file size: 100–300 LOC.
- Warning threshold: >400 LOC requires refactor review note.
- Hard threshold: >600 LOC requires explicit ADR exception.
- Handler/controller files should primarily map input/output and delegate business logic.
- Domain/service files should contain business rules, not transport/database wiring.
- Repository/adapter files should contain persistence/integration mechanics, not domain policy.

### 2) Function and method limits
- Preferred function size: <=40 LOC.
- Warning threshold: >60 LOC.
- Hard threshold: >100 LOC requires decomposition or exception.
- Parameter count target: <=5 (prefer parameter objects/config structs beyond this).
- Cyclomatic complexity target: <=10 for non-trivial functions.

### 3) Package and dependency direction
- Keep package names short, stable, and intention-revealing.
- Avoid package-level globals for mutable runtime state.
- Dependency direction must be inward toward domain/use-case layers.
- Outer adapters (HTTP/DB/queue) depend on ports/interfaces, never the reverse.
- Prevent transport/persistence types from leaking into core domain models.

### 4) Error handling and observability
- Return explicit errors; do not silently swallow failures.
- Add context to errors at boundaries (`fmt.Errorf("...: %w", err)`).
- Translate infra errors at adapter boundaries to domain/use-case level semantics.
- Every external call path must have timeout, retry policy decision, and metrics/log hooks.

### 5) Testing expectations
- Table-driven tests for deterministic rule-heavy logic.
- Unit tests target domain and use-case behavior first.
- Contract/integration tests validate adapters and interfaces.
- Prefer fakes/mocks at port boundaries, not deep internal mocking.
- Coverage is not the only quality gate; critical path behavior evidence is mandatory.

### 6) Concurrency and performance safety
- Concurrency only where measurable benefit exists.
- Every goroutine must have lifecycle ownership and cancellation path.
- Use `context.Context` across request/workflow boundaries.
- Shared mutable state requires clear synchronization strategy and tests.

### 7) Configuration and runtime hygiene
- Config via env/files with typed validation at startup.
- No hard-coded credentials/secrets.
- Production defaults must be safe (timeouts, limits, backoff).
- Health/readiness endpoints and graceful shutdown are mandatory for services.

### 8) Documentation and review linkage
- Each significant component/package includes brief README or package doc.
- Every non-trivial change references `REQ/PLAN/DIAG/TEST` IDs.
- Review comments must cite violated standards when requesting changes.

## Hexagonal architecture alignment
- Core domain/use-case packages must remain framework-agnostic.
- Define inbound/outbound ports at application boundary.
- Implement adapters in separate packages/modules.
- Wiring/composition root instantiates adapters and injects ports into use cases.

## Consequences
- Improves change safety, readability, and onboarding.
- Reduces monolithic files and boundary leakage.
- Enforces production-capable implementation discipline by default.