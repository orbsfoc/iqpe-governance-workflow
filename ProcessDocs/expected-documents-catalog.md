# Expected Documents Catalog

## A) Setup artifacts (must exist before phase work)

- `docs/tooling/bootstrap-report.md`
- `docs/tooling/workflow-preflight.json` (must contain `status: PASS`)
- `docs/tooling/spec-tech-detect.json`
- `docs/tooling/mcp-usage-evidence.md`

## B) Product Owner outputs

- `docs/product-intent.md`
- `docs/requirements.md` (with `REQ-*` IDs)
- `docs/non-goals.md`
- `docs/risks-assumptions.md`
- `docs/handoffs/po/phase-gate.md`

## C) Architect outputs

- `docs/implementation-plan.md` (with `PLAN-*`)
- `docs/backlog.md`
- `docs/technology-constraints.md` (with `TC-*`)
- ADR decision artifacts (authority fields required)
- `docs/traceability-matrix.md` (`REQ -> PLAN -> DIAG`)
- `docs/diagrams/system-context.mmd`
- `docs/diagrams/sequence-flow.mmd`
- `docs/diagrams/components.mmd`
- `docs/diagrams/error-flow.mmd`
- `docs/diagrams/mapping-table.md`
- `docs/handoffs/architect/phase-gate.md`

## D) Developer outputs

- Implementation changes linked to `PLAN-*`
- Test evidence (`TEST-UNIT-*`, `TEST-API-*`, `TEST-UI-*`)
- `CHANGELOG.md` or `docs/change-log.md` (must reference key updated docs and include change descriptions)
- `docs/deviations.md`
- Updated `docs/traceability-matrix.md` (`PLAN -> TEST` linkage)
- `docs/handoffs/dev/phase-gate.md`

## E) Release Reviewer outputs

- `docs/release-review.md`
- `docs/handoffs/release/phase-gate.md`
- `docs/handoffs/release/final-decision.md`
- `docs/tech-radar.md`
- `docs/handoffs/release/tech-radar-summary.md`

## F) Gate/evidence templates expected in use

- phase gate template
- evidence block template
- provenance template

(Templates are retrieved through MCP template actions/tools.)

## G) IQPE-DocsStruct demo governance artifacts

Required fixture artifacts under `portfolio/iqpe-product-template/demo-project-v3/artifacts/`:

- `session-plan-orchestration.yaml`
- `library-catalog.yaml`
- `new-library-decisions.yaml`
- `phase-tech-policy.yaml`
- `tech-radar-summary.yaml`
- `architecture-operations-boundary.yaml`
- `portfolio-topology.yaml`
- `data-boundary-evidence.yaml`
- `code-unit-metadata.yaml`
- `human-readable-overviews.yaml`
- `plan-resource-estimation.yaml`
- `developer-agent-usage-report.yaml`

Generated validation/evaluation reports currently expected:

- `slice-graph-lint-report.yaml`
- `library-search-report.yaml`
- `library-decision-lint-report.yaml`
- `tech-policy-eval-report.yaml`
- `tech-radar-lint-report.yaml`
- `architecture-ops-lint-report.yaml`
- `topology-lint-report.yaml`
- `data-boundary-lint-report.yaml`
- `metadata-overview-lint-report.yaml`
- `resource-variance-summary.yaml`
- `v2-demo-readiness-report.yaml`
