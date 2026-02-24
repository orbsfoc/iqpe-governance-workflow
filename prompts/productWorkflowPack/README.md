# Generic Agent Workflow Pack

This folder provides process + prompt + tooling assets for running fresh product delivery attempts using repository technical guidance.

## Required run input
- `SPEC_DIR`: path to the product specification directory provided for that run.
- Prompts must derive product requirements/plans from `SPEC_DIR`, not from prior demo outputs.
- If `SPEC_DIR` is missing, unreadable, or empty, workflow status is `BLOCKED`.
- Execute local MCP setup via skill actions before orchestrator execution:
	- `mcp.action.local_mcp_install`
	- `mcp.action.local_mcp_configure` (with `target_root`)

## Mandatory initialization step
- Copy this workflow pack directory before running the workflow.

## Skill installation model (Copilot-native)
- Install one or more skills from `.github/skills/` into project-scoped or personal-scoped skills.
- Minimum recommended set for scaffolding:
	- `local-mcp-setup`
	- `project-bootstrap`
	- `workflow-preflight-check`
	- `spec-tech-detect`
- Optional: copy all skills when running the full governance workflow.

Source directory to copy:
- `prompts/productWorkflowPack`

What to copy:
- Copy the entire `productWorkflowPack` directory (all files/subfolders).

Example command (Linux/macOS):
- `cp -R /home/norman/Code/IQPE-DocsStruct/prompts/productWorkflowPack <DESTINATION_PARENT_DIR>/`

Project-scoped install (recommended):
- VS Code: copy to `<PROJECT_ROOT>/.vscode/skills/productWorkflowPack/`
- Cursor: copy to `<PROJECT_ROOT>/.cursor/skills/productWorkflowPack/`

Personal install:
- VS Code: copy to `<YOUR_VSCODE_SKILLS_DIR>/productWorkflowPack/`
- Cursor: copy to `<YOUR_CURSOR_SKILLS_DIR>/productWorkflowPack/`

Minimum required files after copy:
- `00-orchestrator.md`
- `01-product-owner-planning.md`
- `02-product-owner-diagrams.md`
- `03-developer-implementation.md`
- `04-release-review.md`
- `05-maintenance-change-cycle.md`
- `templates/phase-gate-template.md`
- `templates/evidence-block-template.md`
- `templates/provenance-template.md`
- `templates/change-impact-template.md`

## Role flow
1) Product Owner: intent + requirements
2) Architect: technical planning + diagrams
3) Developer: implementation from plan
4) Release Reviewer: objective gate

## Prompt order
1. `00-orchestrator.md`
2. `01-product-owner-planning.md`
3. `02-product-owner-diagrams.md` (Architect phase)
4. `03-developer-implementation.md`
5. `04-release-review.md`
6. `05-maintenance-change-cycle.md` (future change management)

## Mandatory status values
- `PASS`
- `FAIL`
- `BLOCKED`

Use `BLOCKED` when prerequisites or technical decisions are missing.

## MCP execution policy (mandatory)
- Direct-access/manual fallback is not an approved execution mode for this pack.
- If MCP actions/tools are unavailable, status must remain `BLOCKED`.
- Each phase must include MCP usage evidence with action IDs and outputs.
- Local demo mode assumption: MCP server binary `iqpe-localmcp` is installed and available on user `PATH`.

Tooling language policy (mandatory):
- All project tooling/runtime utilities must be implemented in Go for portability.
- New tooling contributions in non-Go languages are `BLOCKED` unless an explicit approved exception exists.
- Existing non-Go helper scripts, if any remain, must be treated as transitional and scheduled for Go replacement.

Repository boundary policy (mandatory):
- Product, architecture, and tooling repositories operate independently.
- Integration boundary is MCP servers plus installed skills (project-scoped or personal-scoped).
- Do not use cross-repo bridge scripts/apps as a normal execution path.

Repository topology and dependency policy (mandatory):
- Topology (`single-repo` or `multi-repo`) must be explicitly decided in `docs/repo-topology-decision.md`.
- Execution must be split into workstreams with explicit dependency gates.
- Integration/orchestration steps can only execute after prerequisite workstream gates pass.
- If `multi-repo` is selected, developer phase must produce per-repo evidence plus central integration traceability.

Draft/feedback tree policy (mandatory):
- `docs/feedback/**` is feedback-only.
- Non-owner draft deliverables must be written under `docs/drafts/**`.
- Draft structures should mirror canonical relative paths to support deterministic owner promotion.

ADR best-practice rule:
- For service-oriented systems, individual services should be in individual repositories as the default best-practice.
- Any exception to service-per-repo must be documented as an ADR decision with rationale, risk, and approval.
- Code review feedback loops and coding principles (`SOLID`, `DRY`) are mandatory best-practice baseline; see `ADR-BEST-PRACTICE-CODE-QUALITY-AND-REVIEW.md`.

MCP-configurable planning behaviors:
- Load planning behavior profile via MCP from architecture guidance before planning decisions.
- Preferred sources:
	- `docs/source/02-architecture/planning-behavior-profile.yaml`
	- `docs/source/DemoArchitectureDocs/planning-behavior-profile.yaml`
- Record effective values in `docs/planning-behavior-resolution.md`.

Corporate architecture governance policy (mandatory):
- Adaptor/service selections and technical planning choices must be backed by approved corporate ADR/technology guidance.
- Local-only technical/adaptor decisions without corporate backing must remain `BLOCKED` until approved.
- Decision artifacts must include authority fields: `Authoritative Source`, `Approval Owner`, `Approval Status`.

Source precedence labeling:
- Label rules/examples as one of: `authoritative`, `example`, `informational`.
- If example text conflicts with approved baseline decisions, approved baseline (authoritative source) must win.

Approved execution when one client cannot invoke `run_action`:
- If MCP server is healthy but this client/session cannot invoke `run_action`, execute required actions from another MCP-capable client connected to the same servers/skills.
- Product teams may also use the installed `local-mcp-setup` skill self-service command to generate bootstrap/preflight artifacts directly.
- Strict gate policy is unchanged: required artifacts and evidence must still be produced, otherwise remain `BLOCKED`.
- Evidence must explicitly record that this client lacked `run_action` invocation and identify the MCP-capable client used.

## Required templates (MCP-retrieved)
Retrieve templates from MCP `docflow-actions` server:
- `list_templates`
- `get_template` with `name` and optional `version`

If `version` is omitted, the latest version is returned.

Action wrappers (for `run_action`) are also available:
- `mcp.action.template_list`
- `mcp.action.template_get` (set `template_name`, optional `template_version` args)

## Tooling checks (MCP skill/actions)
Use `docflow-actions` MCP tools:
- `list_actions` / `run_action`
- `list_skill_versions`
- `check_skill_version`

Required action baseline includes:
- `mcp.action.local_mcp_install`
- `mcp.action.local_mcp_configure`
- `mcp.action.bootstrap_workflow_pack`
- `mcp.action.scaffold_service_workspace`
- `mcp.action.context_promotion_publish`
- `mcp.action.workflow_preflight_check`
- `mcp.action.phase_precondition_check`
- `mcp.action.agent_skill_coverage_check`

AI usage reporting template:
- `ai-usage-report-template.md` (copy to `docs/tooling/ai-usage-report.md` and fill planned vs actual metrics)

Planning storage templates:
- `plans-index-template.md` (copy to `docs/plans/index.md`)
- `story-plan-template.md` (copy to `docs/plans/PLAN-<id>-<slug>.md`)

Draft/promotion and governance templates:
- `draft-promotion-checklist-template.md`
- `adr-approval-transition-template.md`
- `repo-naming-conventions-adr-template.md`
- `data-architecture-decision-template.md`
- `handoff-routing-matrix-template.md`
- `compose-mode-decision-template.md`
- `skill-capability-gap-template.md`
- `diagrams-drift-protocol-template.md`
- `test-execution-evidence-template.md`
- `severity-classification-template.md`

## AI design patterns
- Use planner-executor-verifier-governor pattern.
- Prefer deterministic tool actions over open-ended LLM generation.
- Keep outputs template-driven to minimize token use.
- Reuse artifact references instead of repeating large text.
- Read only the minimum required files from `SPEC_DIR` first, then expand scope if gaps remain.

## Skill version policy
- Skills are versioned in `Tooling/agent-skills/skill-versions.yaml`.
- Agents must verify required skills with `check_skill_version` before execution.
- Action wrappers are available:
	- `mcp.action.skill_version_list`
	- `mcp.action.skill_version_check` (set `skill_id`, optional `expected_version` args)

## Change and maintenance support
When technical docs or decisions change:
1) Update `TC-*` and change impact artifacts.
2) Recompute affected `REQ/PLAN/DIAG/TEST` links.
3) Regenerate impacted diagrams.
4) Re-run release gate with updated evidence.
5) Produce machine-readable change feed and impact-since report.

## Readiness checklist
- `governance-readiness-checklist.md`

## Transfer readiness (copy to new demo)
- Use `PROVISIONING-CHECKLIST.md` section "Transfer smoke test in a new demo repo".
- Run bootstrap first, then require `docs/tooling/workflow-preflight.json` (PASS) before phase execution.
- Require `docs/tooling/bootstrap-report.md` as proof that MCP config/materialization ran in the target repo.
- Initialize and maintain `docs/tooling/mcp-usage-evidence.md` for all phases.
- If orchestrator is BLOCKED for missing bootstrap/preflight artifacts, execute `MCP-ACTION-RUNBOOK.md`.
- If `run_action` is unavailable in-session, re-run required actions from an MCP-capable client as documented in `MCP-ACTION-RUNBOOK.md`.
