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

Stage-to-capability reference:

- `ProcessDocs/mcp-capability-matrix.md`

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

## `docflow` commands used in this repository

Run from `Tooling/docflow`:

- `go run ./cmd/docflow v2-demo-readiness --demo-root ../../portfolio/iqpe-product-template/demo-project-v3 --report ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/v2-demo-readiness-report.yaml`
- `go run ./cmd/docflow slice-graph-lint --graph ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/session-plan-orchestration.yaml --report ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/slice-graph-lint-report.yaml`
- `go run ./cmd/docflow library-search --catalog ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/library-catalog.yaml --query shared --report ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/library-search-report.yaml`
- `go run ./cmd/docflow library-decision-lint --register ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/new-library-decisions.yaml --report ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/library-decision-lint-report.yaml`
- `go run ./cmd/docflow tech-policy-eval --policy ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/phase-tech-policy.yaml --project-phase MVP --environment DEMO --decision-type ORCHESTRATION --technology docker-compose --approval-status APPROVED --report ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/tech-policy-eval-report.yaml`
- `go run ./cmd/docflow tech-radar-lint --radar ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/tech-radar-summary.yaml --report ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/tech-radar-lint-report.yaml`
- `go run ./cmd/docflow architecture-ops-lint --boundary ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/architecture-operations-boundary.yaml --report ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/architecture-ops-lint-report.yaml`
- `go run ./cmd/docflow topology-lint --topology ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/portfolio-topology.yaml --report ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/topology-lint-report.yaml`
- `go run ./cmd/docflow data-boundary-lint --evidence ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/data-boundary-evidence.yaml --report ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/data-boundary-lint-report.yaml`
- `go run ./cmd/docflow metadata-overview-lint --metadata ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/code-unit-metadata.yaml --overview ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/human-readable-overviews.yaml --report ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/metadata-overview-lint-report.yaml`
- `go run ./cmd/docflow resource-variance-lint --estimation ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/plan-resource-estimation.yaml --usage ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/developer-agent-usage-report.yaml --report ../../portfolio/iqpe-product-template/demo-project-v3/artifacts/resource-variance-summary.yaml`

Expected generated reports:

- `demo-project-v3/artifacts/v2-demo-readiness-report.yaml`
- `demo-project-v3/artifacts/slice-graph-lint-report.yaml`
- `demo-project-v3/artifacts/library-search-report.yaml`
- `demo-project-v3/artifacts/library-decision-lint-report.yaml`
- `demo-project-v3/artifacts/tech-policy-eval-report.yaml`
- `demo-project-v3/artifacts/tech-radar-lint-report.yaml`
- `demo-project-v3/artifacts/architecture-ops-lint-report.yaml`
- `demo-project-v3/artifacts/topology-lint-report.yaml`
- `demo-project-v3/artifacts/data-boundary-lint-report.yaml`
- `demo-project-v3/artifacts/metadata-overview-lint-report.yaml`
- `demo-project-v3/artifacts/resource-variance-summary.yaml`
