# Release Reviewer Prompt — Readiness and Maintainability Gate

Role: Release Reviewer

## Objective
Perform final readiness review against requirements, architecture plan, diagrams, implementation evidence, and maintenance/change controls.

## Runtime input (mandatory)
- `SPEC_DIR`: path to provided product specification directory for this run.
- Confirm delivered artifacts cite `SPEC_DIR` sources for requirement derivation.

## Severity policy
- `Sev-1` critical/demo-blocking: automatic `NO-GO`
- `Sev-2` major required-path failure: `NO-GO`
- `Sev-3` minor issue: `GO` allowed with notes

## Required checks
- Requirement coverage (`REQ-*`)
- Traceability completeness: `REQ -> PLAN -> DIAG -> TEST/DEF`
- Diagram alignment with implemented behavior
- Error-path verification evidence
- MCP/tooling validation evidence for fresh collaborator
- Reproducible run/test commands with expected vs actual outputs
- Change/maintenance artifacts present (`change-log`, deviations, updated traceability)
- Changelog/equivalent quality: clear change descriptions and key-doc references are present for implemented scope
- Technology radar is maintained with current adoption status and phase suitability
- Technology radar summary is produced for release decision (`adopt / trial / hold / retire`)
- Source integrity: requirements and plan decisions reference `SPEC_DIR` paths
- Corporate governance integrity: adaptor/service selections and technical decisions reference approved corporate ADR/technology sources
- Authority completeness: ADR/constraints artifacts include `Authoritative Source`, `Approval Owner`, and `Approval Status`

## Required outputs
- `docs/release-review.md`
- `docs/handoffs/release/phase-gate.md`
- `docs/handoffs/release/final-decision.md`
- `docs/tech-radar.md`
- `docs/handoffs/release/tech-radar-summary.md`

## MCP usage evidence (mandatory)
- Verify phase evidence exists in `docs/tooling/mcp-usage-evidence.md` and follows `prompts/productWorkflowPack/mcp-usage-evidence-template.md`.
- If required MCP evidence is missing for any phase, final release decision must be `BLOCKED`.

## Decision rules
- Missing required artifacts or unresolved `TC-*`: `BLOCKED`
- Any adaptor/service selection without corporate ADR backing: `BLOCKED`
- Missing authority fields or any non-`APPROVED` authority status for required technical/adaptor decisions: `BLOCKED`
- Open `Sev-1` or required-path `Sev-2`: `FAIL` and `NO-GO`
- Otherwise `PASS` with explicit GO/NO-GO rationale and remediation owners
