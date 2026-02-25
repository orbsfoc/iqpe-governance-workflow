# ADR — General Design Principles Baseline

Status: APPROVED (authoritative baseline)

## Context
Architecture and implementation decisions need a shared quality baseline across languages, services, and teams.

## Decision
Adopt the following mandatory general design principles for planning, implementation, and review.

## Principles
- **SRP (Single Responsibility):** each module/component has one primary reason to change.
- **OCP (Open/Closed):** extend behavior through composition/polymorphism rather than risky invasive edits.
- **LSP (Liskov Substitution):** abstractions must be safely substitutable.
- **ISP (Interface Segregation):** prefer small focused interfaces over broad catch-all interfaces.
- **DIP (Dependency Inversion):** depend on abstractions/policies, not concrete infrastructure.
- **DRY:** avoid duplicated business rules and duplicated integration logic.
- **High Cohesion, Low Coupling:** keep related logic together and external dependencies minimal/explicit.
- **Explicit Boundaries:** define clear contracts between domains/components/teams.
- **Fail Fast and Transparent:** validate early, return explicit errors, preserve diagnosability.
- **Design for Change:** isolate volatility points and minimize blast radius of change.

## Application rules
- Every plan and implementation artifact should identify boundary ownership and dependencies.
- Violations must be documented with risk and mitigation, not silently accepted.
- Trade-offs are allowed only when recorded with rationale and expiry/remediation intent.

## Review rules
- Code/design reviews should map findings to one or more principles above.
- Repeated violations require architecture-level remediation tasking.

## Consequences
- Improves long-term maintainability and change velocity.
- Creates consistent review language across teams.
- Reduces regression risk from ad hoc design decisions.