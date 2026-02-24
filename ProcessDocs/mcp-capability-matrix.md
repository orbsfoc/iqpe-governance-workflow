# MCP Capability Matrix (By Workflow Stage)

This matrix maps each workflow stage to the MCP servers, tools/actions, skills, and required evidence artifacts used in current process execution.

## Stage mapping

| Stage | Primary objective | MCP servers | MCP tools/actions | Skills in use | Required evidence/artifacts |
|---|---|---|---|---|---|
| Stage 00 — Initialization | Prepare target repo for governed execution | `docflow-actions-local`, `repo-read-local`, `docs-graph-local`, `policy-local` | `run_action`: `mcp.action.local_mcp_install`, `mcp.action.local_mcp_configure`, `mcp.action.bootstrap_workflow_pack`, `mcp.action.workflow_preflight_check`, `mcp.action.spec_tech_detect`, `mcp.action.planning_behavior_resolve` | `local-mcp-setup`, `workflow-preflight-check`, `spec-tech-detect` | `docs/tooling/bootstrap-report.md`, `docs/tooling/workflow-preflight.json`, `docs/tooling/spec-tech-detect.json`, `docs/planning-behavior-resolution.md`, `docs/tooling/mcp-usage-evidence.md` |
| Stage 01 — Product Owner | Build requirement baseline and topology/contract intent | `docflow-actions-local`, `repo-read-local`, `docs-graph-local`, `policy-local` | `run_action`: `mcp.action.planning_behavior_resolve`; tools: `template_list`, `template_get`, repo/docs lookup | `local-mcp-setup`, `project-bootstrap` | `docs/product-intent.md`, `docs/requirements.md`, `docs/repo-topology-decision.md`, `docs/openapi-contract-plan.md`, `docs/plans/index.md`, `docs/plans/PLAN-*.md`, `docs/handoffs/po/phase-gate.md`, `docs/tooling/mcp-usage-evidence.md` |
| Stage 02 — Architect | Produce technical plan, ADRs, diagrams, dependency model | `docflow-actions-local`, `repo-read-local`, `docs-graph-local`, `policy-local` | `run_action`: `mcp.action.spec_tech_detect`, `mcp.action.planning_behavior_resolve`, template retrieval; docs/policy checks | `spec-tech-detect`, `workflow-preflight-check` | `docs/implementation-plan.md`, `docs/backlog.md`, `docs/technology-constraints.md`, ADR docs, `docs/traceability-matrix.md`, `docs/diagrams/*.mmd`, `docs/handoffs/architect/phase-gate.md`, `docs/tooling/mcp-usage-evidence.md` |
| Stage 03 — Developer | Execute PLAN-linked implementation and remediation loops | `docflow-actions-local`, `repo-read-local`, `docs-graph-local`, `policy-local` | `run_action`: `mcp.action.skill_version_check`, template retrieval; repo/docs/policy checks for traceability and governance | `project-bootstrap`, `workflow-preflight-check` | code/test outputs, `docs/change-log.md` or `CHANGELOG.md`, `docs/deviations.md`, handoff docs, `docs/tooling/ai-usage-report.md`, `docs/handoffs/dev/phase-gate.md`, `docs/tooling/mcp-usage-evidence.md` |
| Stage 04 — Release Review | Final governance/readiness decision | `docflow-actions-local`, `repo-read-local`, `docs-graph-local`, `policy-local` | `run_action`: `mcp.action.skill_version_check`, template retrieval; policy and traceability verification checks | `workflow-preflight-check` | `docs/release-review.md`, `docs/handoffs/release/phase-gate.md`, `docs/handoffs/release/final-decision.md`, complete evidence chain `REQ -> PLAN -> DIAG -> TEST/DEF` |

## Notes

- All stages require updates to `docs/tooling/mcp-usage-evidence.md`.
- If required MCP evidence or stage artifacts are missing, stage status must be `BLOCKED`.
- Server names are those configured in `.vscode/mcp.json` for local workflow execution.
