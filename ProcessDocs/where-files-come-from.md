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

## `docflow` command-owned outputs (current project)

Generated in `portfolio/iqpe-product-template/demo-project-v3/artifacts/`:

- `slice-graph-lint` -> `slice-graph-lint-report.yaml`
- `library-search` -> `library-search-report.yaml`
- `library-decision-lint` -> `library-decision-lint-report.yaml`
- `tech-policy-eval` -> `tech-policy-eval-report.yaml`
- `tech-radar-lint` -> `tech-radar-lint-report.yaml`
- `architecture-ops-lint` -> `architecture-ops-lint-report.yaml`
- `topology-lint` -> `topology-lint-report.yaml`
- `data-boundary-lint` -> `data-boundary-lint-report.yaml`
- `metadata-overview-lint` -> `metadata-overview-lint-report.yaml`
- `resource-variance-lint` -> `resource-variance-summary.yaml`
- `v2-demo-readiness` -> `v2-demo-readiness-report.yaml`

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
5. Demo governance artifacts and generated reports under `portfolio/iqpe-product-template/demo-project-v3/artifacts/`

## Process documentation ownership

When execution flow, commands, required artifacts, or gating semantics change, update:

- `ProcessDocs/process-overview.md`
- `ProcessDocs/tools-and-actions-reference.md`
- `ProcessDocs/expected-documents-catalog.md`
- `ProcessDocs/phase-by-phase-checklist.md`
- `ProcessDocs/where-files-come-from.md`
