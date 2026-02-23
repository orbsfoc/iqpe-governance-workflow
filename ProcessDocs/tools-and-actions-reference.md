# Tools and Actions Reference

## Tooling language baseline

- Project tooling components are expected to be implemented in Go for portability.
- Non-Go tooling additions require explicit approval/exception and migration plan.
- Runtime evidence should capture tooling implementation/runtime where relevant.

## MCP servers used in this process

Configured in `.vscode/mcp.json`:

- `repo-read-local`
- `docflow-actions-local`
- `docs-graph-local`
- `policy-local`

## Core MCP actions used during setup

- `mcp.action.local_mcp_install`
- `mcp.action.local_mcp_configure`
- `mcp.action.bootstrap_workflow_pack`
- `mcp.action.workflow_preflight_check`
- `mcp.action.spec_tech_detect`

## Supporting MCP actions/checks

- `mcp.action.agent_skill_coverage_check`
- `mcp.action.skill_version_check`
- `mcp.action.template_list`
- `mcp.action.template_get`

## When each action is expected

- Before phase execution:
  - `local_mcp_install`, `local_mcp_configure`, `bootstrap_workflow_pack`, `workflow_preflight_check`, `spec_tech_detect`
- Before/within governance checks:
  - `agent_skill_coverage_check`, `skill_version_check`
- During artifact creation:
  - `template_list`, `template_get`

## Required evidence logging

For each action/tool call, append to:

- `docs/tooling/mcp-usage-evidence.md`

Include:

- action/tool ID
- input summary
- output summary
- artifact path
