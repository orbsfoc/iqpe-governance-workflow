# ADR Best Practice — Code Quality and Review Policy

Status: APPROVED (best-practice baseline)

## Context
Implementation quality must be consistently reviewable, maintainable, and improvable across all workstreams and repositories.

## Decision
All code changes must pass a structured review loop and comply with core coding principles.

### Mandatory review loop
For every code change:
1. Developer submits implementation with linked `REQ/PLAN/TC/DIAG/TEST` IDs.
2. Reviewer provides explicit feedback (issues, risks, and improvement actions).
3. Developer applies fixes/improvements and records response to feedback.
4. Reviewer re-checks and approves or returns for another loop.

No change is considered complete without documented reviewer feedback and developer response.

### Mandatory coding principles
- `SOLID` design principles
- `DRY` (avoid duplicated logic)
- Clear naming and cohesion
- Explicit error handling and testability
- Small focused units/functions/modules where practical

### Evidence requirements
- Review log per workstream/repo with:
  - reviewer name/role
  - findings and severity
  - developer remediation notes
  - approval decision and timestamp
- Test evidence linked to reviewed changes (`TEST-UNIT-*`, `TEST-API-*`, `TEST-UI-*` as applicable)

### Exception handling
Any temporary deviation must be documented as an ADR exception with:
- rationale
- risk and mitigation
- owner
- expiry/remediation date

## Consequences
- Improves maintainability and defect prevention.
- Adds mandatory feedback cycles before release.
- Release gate remains `BLOCKED` if review/quality evidence is missing.
