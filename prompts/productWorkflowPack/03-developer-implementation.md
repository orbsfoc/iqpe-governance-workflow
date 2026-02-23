# Developer Prompt — Implement from Architect Plan

Role: Developer

## Objective
Implement code from approved architect plan and diagrams, preserving traceability and future maintenance readiness.

## Runtime input (mandatory)
- `SPEC_DIR`: path to provided product specification directory used by Product Owner and Architect phases.
- Use only approved artifacts that trace back to `SPEC_DIR`.

## Mandatory preconditions
- Approved `docs/implementation-plan.md`
- Approved `docs/technology-constraints.md` (`TC-*` resolved)
- Approved diagram set and mapping table
- Completed architect phase gate
- Evidence that requirements were sourced from `SPEC_DIR`

If any are missing, set status `BLOCKED`.

## Implementation requirements
- Implement against `PLAN-*` items; reference IDs in implementation notes.
- Preserve architecture layers: UI, API/controller, service/domain, persistence.
- Enforce canonical error response schema for non-2xx paths:
   - `code`, `message`, `details`, `correlationId`
- Add tests with IDs:
   - `TEST-UNIT-*`, `TEST-API-*`, `TEST-UI-*`

## Maintenance/change readiness requirements
- Maintain a repository change log (`CHANGELOG.md` or `docs/change-log.md`) for every implementation update.
- Each change-log entry must include:
   - a concise change description
   - impacted IDs (`REQ/PLAN/TC/DIAG/TEST` as applicable)
   - links/paths to key updated docs (for example requirements, plan, constraints, diagrams, traceability)
- Add `docs/deviations.md` for any plan/diagram divergence with impacted IDs.
- Update traceability matrix for new/changed requirements.

## MCP usage evidence (mandatory)
- Append phase evidence to `docs/tooling/mcp-usage-evidence.md` using `prompts/productWorkflowPack/mcp-usage-evidence-template.md`.
- Include action/tool IDs used for deterministic checks and their outputs.
- If MCP evidence is missing, phase status must be `BLOCKED`.

## Required outputs
- Implementation artifacts
- Run/build/test instructions
- Test evidence and command outputs
- Updated repository change log (`CHANGELOG.md` or `docs/change-log.md`) with key-doc references
- Updated traceability links (`PLAN -> TEST`)
- `docs/handoffs/dev/phase-gate.md`

## Gate requirement
Use `templates/phase-gate-template.md`.
Status cannot be `PASS` unless required tests, error-path evidence, and change-log updates are present.
