# Governance + Tooling Readiness Checklist

## Spec identity and deltas
- [ ] `spec-version.yaml` exists in `SPEC_DIR`
- [ ] `mcp.action.workflow_preflight_check` executed with PASS evidence in `docs/tooling/workflow-preflight.json`
- [ ] `mcp.action.spec_tech_detect` executed and captured in evidence
- [ ] TC log initialized with IDs `TC-001+`

## ADR linkage
- [ ] Deterministic action coverage check completed (`mcp.action.agent_skill_coverage_check`)
- [ ] ADR changes reflected in traceability and change-impact artifacts
- [ ] Planning behavior profile loaded via MCP and resolution recorded in `docs/planning-behavior-resolution.md`
- [ ] Plan storage controls resolved and applied (`plan_storage_mode`, `plan_directory`, `plan_index_file`, `plan_story_file_pattern`)
- [ ] Plan artifacts are stored in configured planning directory with per-story traceability mapping
- [ ] Adaptor/service selections are mapped to approved corporate ADR/technology sources
- [ ] Repository topology decision ADR is present and approved
- [ ] Dependency model between split workstreams is documented and gated
- [ ] Service-per-repo best-practice is applied for service-oriented scope, or approved ADR exceptions are recorded
- [ ] Code quality/review ADR is present and approved (SOLID/DRY + feedback loops)
- [ ] Code review findings and developer remediation responses are recorded for each implemented workstream
- [ ] Any unsupported adaptor/service choice is logged as blocked and not approved for implementation
- [ ] Authority fields present in decision artifacts: `Authoritative Source`, `Approval Owner`, `Approval Status`
- [ ] Required technical/adaptor decisions have `Approval Status: APPROVED`

## Workspace setup
- [ ] VS Code MCP config present at `.vscode/mcp.json`
- [ ] `mcp.action.bootstrap_workflow_pack` executed with evidence in `docs/tooling/bootstrap-report.md`
- [ ] MCP usage evidence recorded in `docs/tooling/mcp-usage-evidence.md`
- [ ] Read-only ownership manifest exists at `docs/tooling/read-only-manifest.json`
- [ ] Workflow feedback docs are created under `docs/feedback/workflow/` (not `docs/tooling/`, unless approved exception)

## Process gates
- [ ] Phase gates include PASS/FAIL/BLOCKED
- [ ] Evidence blocks attached per check
- [ ] Provenance metadata included in generated artifacts

## Decision
- Status: READY / BLOCKED
- Blocking issues:
- Owner:
- ETA:
