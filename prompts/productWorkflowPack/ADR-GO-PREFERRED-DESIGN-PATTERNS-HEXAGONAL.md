# ADR — Preferred Go Design Patterns for Hexagonal Architecture

Status: APPROVED (authoritative best-practice catalog)

## Context
Teams need concrete pattern guidance for recurring implementation problems in Go while preserving hexagonal boundaries.

## Decision
Use the following preferred patterns by default; deviations require rationale in implementation notes or ADR exception.

## Preferred patterns by situation

### 1) Application service orchestration
- Pattern: **Use-case service + ports**
- Use when: coordinating domain logic with external systems.
- Why: keeps orchestration in core and infra at adapter edge.

### 2) External system integration
- Pattern: **Adapter + anti-corruption mapping**
- Use when: calling third-party APIs or legacy systems.
- Why: isolates vendor-specific types/protocols from core domain.

### 3) Persistence
- Pattern: **Repository adapter behind outbound port**
- Use when: storing/fetching aggregates or projections.
- Why: allows swap/test of persistence without changing use cases.

### 4) Cross-cutting concerns
- Pattern: **Decorator/middleware**
- Use when: adding logging, metrics, auth, retries.
- Why: composes behavior without contaminating business logic.

### 5) Construction/wiring
- Pattern: **Composition root + constructor injection**
- Use when: bootstrapping app/services/adapters.
- Why: explicit dependency graph and testable setup.

### 6) Strategy variability
- Pattern: **Strategy via interface + concrete implementations**
- Use when: runtime-selectable rules/policies.
- Why: localizes variation and avoids branching sprawl.

### 7) Event-driven workflows
- Pattern: **Outbox + idempotent consumer**
- Use when: reliable publish after state change.
- Why: reduces dual-write inconsistency and duplicate side effects.

### 8) Request handling
- Pattern: **Thin handler + mapper + use-case invoke**
- Use when: HTTP/gRPC endpoints.
- Why: transport logic stays thin; business logic remains in core.

## Go-specific anti-patterns to avoid
- Fat handlers/controllers containing business rules.
- Global mutable singletons for business state.
- Interface pollution (interfaces with many unrelated methods).
- Domain model leakage of transport/ORM types.
- Overuse of reflection-heavy frameworks where simple composition works.

## Pattern selection rules
- Start with simplest pattern meeting current requirements.
- Introduce complexity only with measured need (scale, variability, reliability).
- Keep patterns explicit in plan and review evidence for critical paths.

## Consequences
- Faster consistency in implementation decisions.
- Better testability and clearer ownership boundaries.
- Lower change risk as systems and teams scale.