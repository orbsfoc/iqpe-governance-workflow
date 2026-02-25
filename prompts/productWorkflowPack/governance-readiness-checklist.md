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
- [ ] `docs/plans/index.md` exists and maps REQ -> PLAN -> plan-file-path -> target repo
- [ ] `docs/plans/planning-signoff.md` exists and contains `Approval Status: APPROVED` before phase-03 PASS
- [ ] Adaptor/service selections are mapped to approved corporate ADR/technology sources
- [ ] Repository topology decision ADR is present and approved
- [ ] Data architecture decision exists (`docs/data-architecture-decision.md`) and matches constraints/runtime evidence or has approved deviation
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
- [ ] `mcp.action.scaffold_service_workspace` executed and reported PASS
- [ ] `repos/` workspace exists with planned repositories and integration workspace artifacts aligned to topology decision
- [ ] No service/integration repositories were auto-created before planning signoff (`docs/plans/planning-signoff.md` approval)
- [ ] Naming convention ADR exists at `docs/adr/ADR-0001-repo-naming-conventions.md`
- [ ] Handoff routing matrix exists at `docs/handoffs/routing-matrix.md`
- [ ] Integration execution mode decision artifact exists for selected orchestration mode
- [ ] MCP usage evidence recorded in `docs/tooling/mcp-usage-evidence.md`
- [ ] Read-only ownership manifest exists at `docs/tooling/read-only-manifest.json`
- [ ] Workflow feedback docs are created under `docs/feedback/workflow/` (not `docs/tooling/`, unless approved exception)
- [ ] Non-owner draft deliverables are created under `docs/drafts/workflow/` (not under `docs/feedback/**`)
- [ ] `mcp.action.feedback_tree_policy_lint` returns PASS (no draft deliverables under `docs/feedback/**`)
- [ ] `mcp.action.phase_precondition_check` is PASS for current phase before phase authoring starts
- [ ] `mcp.action.materialize_repos_from_plan` executed before phase-03 PASS when topology is `multi-repo`
- [ ] `mcp.action.implementation_parity_check` returns PASS before phase-03 PASS
- [ ] `mcp.action.release_blocker_ownership_lint` returns PASS before final release GO
- [ ] `docs/known-blockers.md` exists and each open blocker has owner + ETA + evidence path
- [ ] Open planning-vs-skill gaps are tracked in `docs/tooling/skill-capability-gap.md` and resolved or exception-approved
- [ ] `mcp.action.context_promotion_publish` returns PASS with shared repo roots configured
- [ ] `docs/tooling/context-promotion-report.json` exists and lists published architecture/catalog targets

## Process gates
- [ ] Phase gates include PASS/FAIL/BLOCKED
- [ ] Evidence blocks attached per check
- [ ] Provenance metadata included in generated artifacts

## Decision
- Status: READY / BLOCKED
- Blocking issues:
- Owner:
- ETA:
