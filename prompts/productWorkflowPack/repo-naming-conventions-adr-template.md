# Repository Naming Conventions ADR Template

Use this ADR to define deterministic naming for service/UI/integration repositories in a multi-repo workspace.

## Metadata
- ADR ID: `ADR-XXXX`
- Status: Proposed | Approved | Superseded
- Date (UTC): `YYYY-MM-DD`
- Decision owner: `<owner-role-or-team>`
- Scope: `<product-or-portfolio>`

## Context
- Why deterministic repository naming is required for planning, traceability, and integration orchestration.

## Decision
- Service repo naming pattern: `<product>-svc-<bounded-context>-<runtime>`
- UI repo naming pattern: `<product>-web-<bounded-context>-ts-react`
- Integration repo naming pattern: `<product>-demo-compose`
- Workspace checkout directory convention: `repos/`

## Examples
- `<product>-svc-orders-go-app`
- `<product>-svc-catalog-go-module`
- `<product>-web-portal-ts-react`
- `<product>-demo-compose`

## Consequences
- Positive:
  - Deterministic automation for scaffolding, dependency planning, and CI wiring.
  - Easier traceability mapping (`REQ/PLAN/DIAG/TEST`) by repository identity.
- Trade-offs:
  - Renames require migration plan and redirect policy.

## Implementation Notes
- Reference scaffold action output and any exceptions approved by architecture governance.
