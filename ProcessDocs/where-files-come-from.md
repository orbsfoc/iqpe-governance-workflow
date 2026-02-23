# Where Files Come From

## Prompt-owned outputs

The following paths are created/updated by role prompts in `prompts/productWorkflowPack`:

- Product Owner: intent/requirements/non-goals/risk docs
- Architect: planning/constraints/diagrams/traceability docs
- Developer: implementation evidence + change/deviation updates
- Release: release review + final decision docs

## MCP action-owned outputs

Actions generate setup/tooling artifacts:

- `bootstrap_workflow_pack` -> `docs/tooling/bootstrap-report.md`
- `workflow_preflight_check` -> `docs/tooling/workflow-preflight.json`
- `spec_tech_detect` -> `docs/tooling/spec-tech-detect.json`

## Evidence-owned outputs

Every phase must update:

- `docs/tooling/mcp-usage-evidence.md`

## Governance-owned outputs

Gate outputs are required per phase:

- `docs/handoffs/<role>/phase-gate.md`

Release phase also requires:

- `docs/handoffs/release/final-decision.md`

## Practical expectation

After a successful full run, you should have:

1. Setup artifacts under `docs/tooling/`
2. Phase outputs under `docs/` and `docs/diagrams/`
3. Handoff gate documents under `docs/handoffs/`
4. Final release decision documents
