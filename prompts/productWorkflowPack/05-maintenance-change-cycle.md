# Maintenance Prompt — Change and Impact Cycle

Role: Architect + Developer Maintenance Workflow

## Objective
Process future changes in technical docs/specs/ADRs with controlled impact analysis, traceability updates, and selective implementation updates.

## Runtime input (mandatory)
- `SPEC_DIR`: path to provided product specification directory.
- Use `SPEC_DIR` as the primary source for product-scope deltas.

## Triggers
Run this workflow when any of the following change:
- Technical specification version
- ADR decision
- Technology constraint (`TC-*`)
- Required behavior (`REQ-*`)

## Required outputs
- `docs/change-impact.md` using `templates/change-impact-template.md`
- Updated `docs/technology-constraints.md` if decisions changed
- Updated `docs/traceability-matrix.md`
- Updated affected diagrams
- Updated tests for impacted paths
- `docs/handoffs/maintenance/phase-gate.md`

## Required process
1) Identify impacted IDs (`REQ/PLAN/DIAG/TEST/DEF/TC`).
2) Mark unaffected areas explicitly to reduce rework.
3) Apply minimal required updates only.
4) Re-run tooling checks and release gate criteria for impacted scope.

## Token minimization rules
- Analyze only changed IDs and directly linked artifacts.
- Avoid full-system re-planning unless impact analysis requires it.
- Use deterministic checks and concise templates.

## MCP usage evidence (mandatory)
- Append cycle evidence to `docs/tooling/mcp-usage-evidence.md` using `.iqpe-workflow/productWorkflowPack/mcp-usage-evidence-template.md`.
- Include action/tool IDs executed for impacted scope and output artifacts.
- If MCP evidence is missing, cycle status must be `BLOCKED`.

## Gate requirement
Use `templates/phase-gate-template.md`.
If impact cannot be traced to IDs, mark `BLOCKED`.
