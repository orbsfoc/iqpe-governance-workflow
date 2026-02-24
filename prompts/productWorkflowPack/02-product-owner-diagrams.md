# Architect Prompt — Technical Planning and Diagrams

Role: Architect

## Objective
Use technical docs/specs to produce an implementation plan, technology constraints, and architecture diagrams with full traceability.

## Runtime input (mandatory)
- `SPEC_DIR`: path to provided product specification directory.
- Architecture planning must be grounded in `SPEC_DIR` plus project technical guidance.

## Required outputs
- `docs/implementation-plan.md` with `PLAN-*` IDs linked to `REQ-*`
- `docs/plans/index.md` with `REQ-*` to `PLAN-*` to plan-file mapping
- `docs/plans/PLAN-*.md` plan files (when per-story storage is configured)
- `docs/backlog.md` prioritized by dependency and risk
- `docs/technology-constraints.md` with `TC-*` decisions
- ADR artifacts for technical/adaptor decisions using `adr-decision-template` authority fields
- ADR artifacts for:
	- API contract governance (OpenAPI-first)
	- service repository topology
	- orchestration dependency and integration sequencing
	- service/orchestration testing feedback loops
	- code quality and review policy (SOLID/DRY + mandatory feedback loop)
- `docs/traceability-matrix.md` covering `REQ -> PLAN -> DIAG`
- `docs/diagrams/system-context.mmd`
- `docs/diagrams/sequence-flow.mmd`
- `docs/diagrams/components.mmd`
- `docs/diagrams/error-flow.mmd`
- `docs/diagrams/mapping-table.md`
- `docs/handoffs/architect/phase-gate.md`

## Planning rules
- Plan must be derived from `SPEC_DIR` specs and technical docs/guidance with source citations.
- Plan must align to `docs/planning-behavior-resolution.md` values derived from MCP-loaded profile.
- Plan storage layout and naming must align to resolved profile controls (`plan_storage_mode`, `plan_directory`, `plan_index_file`, `plan_story_file_pattern`).
- Any unresolved core technology decision must be marked as `TC-*` and block implementation.
- Mermaid is required for all diagrams.
- Plan must define concurrent service workstreams and their independent review gates.
- Plan must define integration/orchestration steps with explicit dependency gates on prerequisite workstreams.
- OpenAPI contract must be approved before implementation workstreams begin.
- Code quality and review ADR baseline must be approved before implementation workstreams begin.
- If `docs/tooling/spec-tech-detect.json` contains stack decisions, materialize them into `docs/technology-constraints.md` and corresponding ADR entries before declaring unresolved TC constraints.
- Adaptor/service selections must be backed by approved corporate ADR/technology guidance; local-only choices are not allowed.
- If corporate backing is missing for an adaptor/service choice, record as blocked decision and set phase status to `BLOCKED`.
- For each technical/adaptor decision, include explicit fields in ADR/constraints artifacts:
	- `Authoritative Source`
	- `Approval Owner`
	- `Approval Status`
- Auto-approval rule: if a decision is directly backed by approved corporate ADR/technology sources, set `Approval Status: APPROVED` and continue.
- If backing is absent or ambiguous, set `Approval Status: PROPOSED` and keep dependent work `BLOCKED`.

## Diagram rules
- Include stable `DIAG-*` IDs in diagrams or mapping table.
- Ensure 1:1 coverage from plan tasks to diagram elements.
- Define diagram drift protocol for future changes.
- Include orchestration dependency view showing service completion prerequisites.
- Include test-loop view showing per-workstream test cycle and integration feedback cycle.

## MCP usage evidence (mandatory)
- Append phase evidence to `docs/tooling/mcp-usage-evidence.md` using `.iqpe-workflow/productWorkflowPack/mcp-usage-evidence-template.md`.
- Include `mcp.action.spec_tech_detect` evidence before marking any core `TC-*` as unresolved.
- If MCP evidence is missing, phase status must be `BLOCKED`.

## Gate requirement
Use `templates/phase-gate-template.md`.
If planning behavior resolution is missing or violated, mark `BLOCKED`.
If any mandatory `TC-*` decision is unresolved, mark `BLOCKED`.
If adaptor/service choices lack corporate ADR backing, mark `BLOCKED`.
If authority fields are missing or `Approval Status` is not `APPROVED`, mark `BLOCKED`.
