# Phase-by-Phase Checklist

## 0. Initialization gate

- [ ] MCP servers configured and reachable
- [ ] `bootstrap-report.md` exists
- [ ] `workflow-preflight.json` exists with `PASS`
- [ ] `spec-tech-detect.json` exists
- [ ] `mcp-usage-evidence.md` initialized
- [ ] `docs/data-architecture-decision.md` exists
- [ ] `docs/handoffs/routing-matrix.md` exists
- [ ] `docs/integration/compose-mode-decision.md` exists

If any item is missing: `BLOCKED`.

## 1. Product Owner gate

- [ ] Intent and requirements produced
- [ ] Requirements have acceptance criteria and source citations
- [ ] PO phase gate file exists
- [ ] MCP evidence appended

## 2. Architect gate

- [ ] Plan, backlog, and constraints produced
- [ ] Diagrams produced in Mermaid
- [ ] Traceability `REQ -> PLAN -> DIAG` complete
- [ ] Technical/adaptor decisions include authority fields and approved backing
- [ ] Data architecture decision matches constraints/plans or approved deviation is recorded
- [ ] Architect phase gate file exists
- [ ] MCP evidence appended
- [ ] New library proposals include machine-readable decisions with valid approval status
- [ ] Phase/environment technology policy evaluation produced for newly introduced technologies

## 3. Developer gate

- [ ] Implementation follows approved plan/constraints
- [ ] Tests and run commands captured
- [ ] `CHANGELOG.md` or `docs/change-log.md` updated with clear descriptions and key-doc references
- [ ] Change/deviation docs updated
- [ ] Traceability updated (`PLAN -> TEST`)
- [ ] Developer phase gate file exists
- [ ] MCP evidence appended
- [ ] Process docs under `ProcessDocs/` updated when workflow/runtime commands change
- [ ] Compose mode decision exists and has evidence for selected mode

## 4. Release gate

- [ ] Release review completed
- [ ] Severity policy applied (`Sev-1/2/3`)
- [ ] Final decision document produced
- [ ] Changelog/equivalent reviewed for completeness and key-doc linkage integrity
- [ ] `docs/tech-radar.md` updated with current technology adoption status
- [ ] `docs/handoffs/release/tech-radar-summary.md` produced for decision board
- [ ] Missing artifacts/evidence force `BLOCKED`
- [ ] Handoff routing matrix has required `ACKED` transitions with evidence paths
- [ ] Open planning-vs-skill capability gaps are resolved or exception-approved
- [ ] `v2-demo-readiness` report status is `pass`
- [ ] Slice graph, catalog search, library decision lint, tech policy eval, tech radar lint, architecture-ops lint, topology lint, data-boundary lint, metadata-overview lint, and resource-variance summary are present and current

## 5. Final decision criteria

- `PASS` only when required artifacts and evidence are complete.
- `FAIL` for unresolved critical/major readiness failures.
- `BLOCKED` for missing prerequisites, missing MCP evidence, or unresolved governance constraints.
