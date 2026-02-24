# Demo Provisioning Checklist (Review First)

## Goal
Provision a fresh demo project with tooling-first setup and minimal LLM overhead.

Policy:
- This workflow must run through MCP actions/tools.
- If MCP is unavailable, do not proceed with fallback/manual mode; mark run `BLOCKED`.

## 1) Install workflow pack
Copy `prompts/productWorkflowPack` to either project-scoped or personal skills location.

Install Copilot-native skills (copy one or more) from `.github/skills/`:
- Required for scaffolding:
	- `local-mcp-setup`
	- `project-bootstrap`
	- `workflow-preflight-check`
	- `spec-tech-detect`
- Install location options:
	- Project-scoped: `<PROJECT_ROOT>/.github/skills/`
	- Personal-scoped: `~/.copilot/skills/`

Before workflow execution in the target demo repo:
- Run local MCP setup actions:
	- `run_action` with `action_id: mcp.action.local_mcp_install`
	- `run_action` with `action_id: mcp.action.local_mcp_configure` and args:
		- `target_root` (mandatory; absolute path to target demo repo root)

Example command (Linux/macOS):
- `cp -R /home/norman/Code/IQPE-DocsStruct/prompts/productWorkflowPack <DESTINATION_PARENT_DIR>/`

Project-scoped:
- VS Code: `<PROJECT_ROOT>/.vscode/skills/productWorkflowPack/`
- Cursor: `<PROJECT_ROOT>/.cursor/skills/productWorkflowPack/`

Personal:
- VS Code: `<YOUR_VSCODE_SKILLS_DIR>/productWorkflowPack/`
- Cursor: `<YOUR_CURSOR_SKILLS_DIR>/productWorkflowPack/`

Verify copied files include prompts `00` through `05`.

## 2) Provide product spec directory
Set `SPEC_DIR` to the provided product spec folder for this run.

Before setting TC-003/TC-004 to unresolved:
- Run `mcp.action.spec_tech_detect` and review `docs/tooling/spec-tech-detect.json`.
- If specs indicate stack choices (for example `golang` backend, `react` frontend, `postgres` persistent engine, `flyway` migration tool), capture them into technology constraints and ADR artifacts.
- These stack examples are informational only; approved corporate baseline artifacts are authoritative when conflicts exist.

Validate using MCP/server-managed checks and evidence policy.

Template retrieval for phase artifacts:
- `list_templates`
- `get_template` (`name`, optional `version`; defaults to latest)
- `run_action` with `action_id: mcp.action.template_get` and args:
	- `template_name`
	- `template_version` (optional)

## 3) Run readiness checks
- `run_action` with `action_id: mcp.action.bootstrap_workflow_pack` and args:
	- `target_root` (mandatory; absolute path to target demo repo root)
	- `spec_dir` (optional)
- `run_action` with `action_id: mcp.action.workflow_preflight_check` and args:
	- `spec_dir` (mandatory)
	- `target_root` (mandatory; absolute path to target demo repo root)
- `run_action` with `action_id: mcp.action.spec_tech_detect` and args:
	- `spec_dir` (mandatory)
	- `target_root` (mandatory; absolute path to target demo repo root)
- `list_skill_versions`
- `check_skill_version` for required bootstrap and governance skills
- `run_action` for deterministic checks/actions
- `run_action` with `action_id: mcp.action.skill_version_check` and args:
	- `skill_id`
	- `expected_version` (optional)

If required artifacts are still missing after this step, execute `MCP-ACTION-RUNBOOK.md` and keep status `BLOCKED` until both artifacts exist.

If MCP client cannot call `run_action` in the current session, use:
- Another MCP-capable client connected to the same MCP servers/skills and execute bootstrap + preflight actions per `MCP-ACTION-RUNBOOK.md`.
- Or self-service from installed skill:
	- `go run ./.github/skills/local-mcp-setup/bootstrap_preflight.go --target-root <target_root_abs_path> --spec-dir <spec_dir_path>`
	- Confirm generated artifacts include `docs/tooling/spec-tech-detect.json` before architect phase.
	- The generated detection merges `SPEC_DIR` with `./.github/skills/local-mcp-setup/corporate-approved-tech.json`.

## 4) Execute role workflow
1. `00-orchestrator.md`
2. `01-product-owner-planning.md`
3. `02-product-owner-diagrams.md`
4. `03-developer-implementation.md`
5. `04-release-review.md`
6. `05-maintenance-change-cycle.md` (when specs/ADRs change)

## 5) Enforce gating
Every phase must end with:
- `PASS`, `FAIL`, or `BLOCKED`

Required MCP evidence:
- `docs/tooling/mcp-usage-evidence.md` with action IDs and outputs used in the phase

Required artifacts per phase:
- Phase gate template
- Evidence blocks
- Provenance metadata
- Traceability updates (`REQ/PLAN/DIAG/TEST/DEF/TC`)

## 6) For spec changes between versions
- Use deterministic MCP actions and server tools to generate change feed, linkage checks, and impact reports.
- Update change-impact and traceability artifacts.

## 7) Transfer smoke test in a new demo repo
- Copy this pack into the target demo repo skill location.
- Ensure target repo has `.vscode/mcp.json` configured for required MCP servers.
- Set `SPEC_DIR` to the target demo specs path.
- Run `mcp.action.bootstrap_workflow_pack` and confirm `docs/tooling/bootstrap-report.md`.
- Run `mcp.action.workflow_preflight_check`; require PASS.
- Run `mcp.action.spec_tech_detect` and confirm `docs/tooling/spec-tech-detect.json` exists.
- Initialize `docs/tooling/mcp-usage-evidence.md` from the template and record all phase MCP actions.
- Start with `00-orchestrator.md`; do not proceed if preflight/bootstrap evidence is missing.
