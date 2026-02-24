# Process Overview (How the workflow runs now)

## Purpose

Describe the current MCP-first workflow lifecycle, including phase sequencing, feedback loops, review loops, and evidence production.

## Entry points

- Prompt pack: `prompts/productWorkflowPack`
- Orchestration start: `00-orchestrator.md`
- Supporting runbook: `MCP-ACTION-RUNBOOK.md`
- Runtime CLI root: `Tooling/docflow`
- Process diagrams index: `ProcessDocs/process-diagrams.md`

## Core inputs and sources of truth

- `SPEC_DIR` (required): product/domain specification source for this run.
- Architecture planning behavior profile (`planning-behavior-profile.yaml`) loaded via MCP.
- Corporate ADR/technology guidance used for adaptor/service approvals.
- Target workspace root for bootstrap/preflight and generated artifacts.

## MCP servers and skills used

From `.vscode/mcp.json`, the workflow uses these servers:

- `repo-read-local` (repo content lookup)
- `docflow-actions-local` (actions/templates/skill versions)
- `docs-graph-local` (documentation graph queries)
- `policy-local` (policy checks)

Skills/actions are installed into the target workspace and executed through MCP `run_action`.

## End-to-end processing flow

1. Install workflow pack and required skills in target workspace.
2. Execute setup actions:
   - `mcp.action.local_mcp_install`
   - `mcp.action.local_mcp_configure`
   - `mcp.action.bootstrap_workflow_pack`
   - `mcp.action.workflow_preflight_check`
   - `mcp.action.spec_tech_detect`
3. Validate setup artifacts under `docs/tooling/`.
4. Execute role phases in order:
   - Product Owner
   - Architect
   - Developer
   - Release Reviewer
5. At each phase, append MCP evidence and produce phase gate documents.
6. Enforce review/remediation loops before promoting workstream and before release decision.

## Looping and review behavior

- Workstream loop: implement -> test -> review feedback -> remediation -> re-test.
- Integration loop: contract/integration checks -> defect routing -> service remediation -> re-check.
- Gate loop: failed or missing prerequisites keep status `BLOCKED` until corrected evidence is produced.

## Status model

Allowed statuses in all gates:

- `PASS`
- `FAIL`
- `BLOCKED`

If required artifacts or MCP evidence are missing, status must be `BLOCKED`.

## Diagram map

- `workflow-lifecycle.mmd`: phase and gate lifecycle.
- `artifact-production-sequence.mmd`: setup + artifact sequence.
- `mcp-skills-touchpoints.mmd`: where servers, skills, actions, and inputs interact.
- `workstream-review-loop.mmd`: development/review/remediation loop and promotion logic.
