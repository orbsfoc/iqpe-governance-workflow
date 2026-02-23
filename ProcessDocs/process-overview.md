# Process Overview (How the workflow runs)

## Purpose

Describe the execution flow for the MCP-first product workflow pack and the expected lifecycle from bootstrap to release gate.

## Entry points

- Prompt pack: `prompts/productWorkflowPack`
- Orchestration start: `00-orchestrator.md`
- Supporting runbook: `MCP-ACTION-RUNBOOK.md`

## Mandatory runtime inputs

- `SPEC_DIR` (required): product specification directory for this run.
- Target repo root for bootstrap/preflight actions.

## End-to-end flow

1. Install/copy workflow pack and required skills.
2. Run local MCP install/configure actions.
3. Run bootstrap action and verify bootstrap report.
4. Run preflight action and require `PASS`.
5. Run spec technology detection and capture output.
6. Execute phases in order:
   - Product Owner
   - Architect
   - Developer
   - Release Reviewer
7. Enforce phase gates and evidence at each phase.

## Status model

Allowed statuses in all gates:

- `PASS`
- `FAIL`
- `BLOCKED`

If required artifacts or MCP evidence are missing, status must be `BLOCKED`.

## MCP policy summary

- MCP actions/tools are required (no manual bypass mode).
- If current client cannot invoke `run_action`, use another MCP-capable client against the same servers/skills.
- Every phase must append records to `docs/tooling/mcp-usage-evidence.md`.
