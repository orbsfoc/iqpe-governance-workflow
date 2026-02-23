# Transfer Smoke Test (New Demo Repo)

## Purpose
Validate that the workflow pack runs in a fresh demo repo with MCP-first enforcement and deterministic evidence.

## Preconditions
- Workflow pack copied to target repo skill location.
- `.vscode/mcp.json` present in target repo.
- `SPEC_DIR` points to target demo specification directory.

## Required steps
1) Run `mcp.action.bootstrap_workflow_pack` with `target_root=<absolute target repo path>`.
2) Confirm `docs/tooling/bootstrap-report.md` exists.
3) Run `mcp.action.workflow_preflight_check` with `target_root=<absolute target repo path>` and `spec_dir=<spec path>`.
4) Confirm PASS in `docs/tooling/workflow-preflight.json`.
5) Create `docs/tooling/mcp-usage-evidence.md` from `mcp-usage-evidence-template.md`.
6) Run role flow from `00` through `04` (and `05` for change cycle).

## Pass criteria
- No manual fallback path used.
- If `run_action` is unavailable in-session, deterministic `agenttool` bridge from `MCP-ACTION-RUNBOOK.md` is used and evidenced.
- Each phase includes MCP action evidence.
- Phase gates only use `PASS`/`FAIL`/`BLOCKED` and block on missing MCP evidence.

## Block conditions
- Missing or invalid `.vscode/mcp.json`.
- `workflow_preflight_check` not PASS.
- Missing `SPEC_DIR` or unreadable spec files.
- Missing MCP evidence for any required phase.
