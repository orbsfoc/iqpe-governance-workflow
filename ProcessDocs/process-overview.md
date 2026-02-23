# Process Overview (How the workflow runs)

## Purpose

Describe the execution flow for the MCP-first product workflow pack and the expected lifecycle from bootstrap to release gate.

This document is now anchored to the current `IQPE-DocsStruct` repository layout and runnable `docflow` commands.

## Entry points

- Prompt pack: `prompts/productWorkflowPack`
- Orchestration start: `00-orchestrator.md`
- Supporting runbook: `MCP-ACTION-RUNBOOK.md`
- Runtime CLI root: `Tooling/docflow`
- Demo fixture root: `portfolio/iqpe-product-template/demo-project-v3`

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
8. Run scaling/library governance command set and persist reports under `demo-project-v3/artifacts/`:
   - `slice-graph-lint`
   - `library-search`
   - `library-decision-lint`
   - `tech-policy-eval`
   - `tech-radar-lint`
   - `architecture-ops-lint`
   - `topology-lint`
   - `data-boundary-lint`
   - `metadata-overview-lint`
   - `resource-variance-lint`

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

## Current project implementation status

- Feature 01 runtime command implemented: `slice-graph-lint`.
- Feature 02 runtime command implemented: `library-search`.
- Feature 03 runtime command implemented: `library-decision-lint`.
- Feature 04 runtime command implemented: `tech-policy-eval`.
- Feature 05 runtime command implemented: `tech-radar-lint`.
- Feature 06 runtime command implemented: `architecture-ops-lint`.
- Feature 07 runtime command implemented: `topology-lint`.
- Feature 08 runtime command implemented: `data-boundary-lint`.
- Feature 09 runtime command implemented: `metadata-overview-lint`.
- Feature 10 runtime command implemented: `resource-variance-lint`.
