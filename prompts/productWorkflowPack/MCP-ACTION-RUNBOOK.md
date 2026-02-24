# MCP Action Runbook (Bootstrap + Preflight)

Use this runbook when orchestrator is BLOCKED due to missing `bootstrap-report.md` or `workflow-preflight.json`.

## Required arguments
- `target_root`: absolute path to the target demo repo root
- `spec_dir`: path to the spec directory for this run

## Required MCP action calls
0) `run_action`
- `action_id`: `mcp.action.local_mcp_install`

1) `run_action`
- `action_id`: `mcp.action.local_mcp_configure`
- args:
  - `target_root`

2) `run_action`
- `action_id`: `mcp.action.bootstrap_workflow_pack`
- args:
  - `target_root`
  - `spec_dir` (optional)

Expected artifact:
- `docs/tooling/bootstrap-report.md`

3) `run_action`
- `action_id`: `mcp.action.workflow_preflight_check`
- args:
  - `target_root`
  - `spec_dir`

Expected artifact:
- `docs/tooling/workflow-preflight.json` with `status: PASS`

## If `run_action` client interface is unavailable in-session
Preferred: use another MCP-capable client connected to the same MCP servers/skills and run the required actions.

Self-service option (product team can execute directly from installed skill, from any current directory):

`TARGET_ROOT=<target_root_abs_path> SPEC_DIR=<spec_dir_path> GO_BIN="$(command -v go)" && "$GO_BIN" run "$TARGET_ROOT/.github/skills/local-mcp-setup/bootstrap_preflight.go" --target-root "$TARGET_ROOT" --spec-dir "$SPEC_DIR"`

This command merges `SPEC_DIR` detection with the installed corporate approved baseline file:
- `./.github/skills/local-mcp-setup/corporate-approved-tech.json`

This option is approved for client-integration gaps and does not require tools-team intervention.

If using MCP-capable client path, run:

1) `mcp.action.bootstrap_workflow_pack`
2) `mcp.action.workflow_preflight_check`

Required produced artifacts remain:
- `<target_root_abs_path>/docs/tooling/bootstrap-report.md`
- `<target_root_abs_path>/docs/tooling/workflow-preflight.json` with `status: PASS`
- `<target_root_abs_path>/docs/tooling/spec-tech-detect.json`

Classification:
- This path is an approved MCP-client substitution for integration gaps.
- It is not a manual fallback bypass.

Status policy remains unchanged:
- If artifacts are missing or preflight is not PASS, remain `BLOCKED`.

## Evidence recording (mandatory)
- Append both calls and outputs to `docs/tooling/mcp-usage-evidence.md`.
- Record which MCP-capable client executed the actions when this session cannot invoke `run_action`.
- If either artifact is missing, remain `BLOCKED` and do not proceed to phase 01.
