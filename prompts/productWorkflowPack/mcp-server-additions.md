# MCP Server Additions (Tooling-First Setup)

## Decision
Use additions to the existing `docflow-actions` server (via `mcp.action.*`) instead of creating a new MCP server.

## Rationale
- Lower operational complexity.
- Reuses existing deterministic action routing.
- Minimizes LLM setup burden by making bootstrap deterministic.

## New action
- `mcp.action.bootstrap_workflow_pack`
- Go skill command: `Tooling/docflow/cmd/agenttool workflow-bootstrap`

## What it does
1) Copies workflow pack to target project:
   - `.iqpe-workflow/productWorkflowPack`
2) Ensures MCP config exists:
   - `.vscode/mcp.json`
3) Writes bootstrap evidence report:
   - `docs/tooling/bootstrap-report.md`

## Runtime inputs
- `TARGET_ROOT` env var (optional)
- `SPEC_DIR` env var (optional at bootstrap; required by prompts at runtime)

## Skill mapping
- `AGENT-SKILL-PROJECT-BOOTSTRAP-001` ->
  - `mcp.action.bootstrap_workflow_pack`
  - `mcp.action.agent_skill_coverage_check`

## Expected usage pattern
1) Run bootstrap action.
2) Run spec-dir validation.
3) Start orchestrator prompt.

This pattern shifts project setup from LLM text generation to deterministic tooling execution.
