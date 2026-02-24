# Product Owner Prompt — Product Intent and Requirement Baseline

Role: Product Owner

## Objective
Define product intent and requirement baseline for a fresh product domain, constrained to MVP scope and ready for architecture planning.

## Runtime input (mandatory)
- `SPEC_DIR`: path to provided product specification directory.
- Read product/domain requirements from `SPEC_DIR` first.
- If spec content is insufficient or conflicting, document explicit assumptions and mark `BLOCKED` when critical ambiguity remains.

## Required outputs
- `docs/product-intent.md`
- `docs/requirements.md` with `REQ-*` IDs
- `docs/non-goals.md`
- `docs/risks-assumptions.md`
- `docs/repo-topology-decision.md`
- `docs/openapi-contract-plan.md`
- `docs/data-architecture-decision.md`
- `docs/plans/index.md`
- `docs/plans/PLAN-*.md` (when per-story storage is configured)
- `docs/planning-behavior-resolution.md`
- `docs/handoffs/routing-matrix.md`
- `docs/handoffs/po/phase-gate.md`

## Planning behavior profile loading (mandatory)
- Load planning behavior profile via MCP tool access before topology/contract decisions.
- Allowed profile paths:
	- `docs/source/02-architecture/planning-behavior-profile.yaml`
	- `docs/source/DemoArchitectureDocs/planning-behavior-profile.yaml`
	- `.github/skills/local-mcp-setup/corporate-docs/planning-behavior-profile.yaml`
- `docs/planning-behavior-resolution.md` must capture:
	- profile source path
	- resolved behavior values used for this run
	- decision impacts (topology/contracts/plan-storage/dependencies/reviews/integration)

## Plan storage convention (mandatory)
- Plan storage rules are resolved from the planning behavior profile.
- Minimum controls to resolve and apply:
	- `plan_storage_mode`
	- `plan_directory`
	- `plan_index_file`
	- `plan_story_file_pattern`
	- `plan_traceability_required`
- If `plan_storage_mode=per-story-files`, planning must produce per-story plan files under the configured directory using configured naming pattern.
- `plan_index_file` must map each `REQ-*` to one or more `PLAN-*` IDs and corresponding plan file paths.
- For multi-repo/service decomposition, index rows must include a deterministic service/repo target in plan metadata and provenance.

## Repository topology decision (mandatory)
Planning must explicitly decide and record implementation topology in `docs/repo-topology-decision.md`.

Allowed topology values:
- `single-repo`
- `multi-repo`

Decision artifact must include:
- Chosen topology and rationale
- Expected profile direction vs selected topology (explicit comparison)
- Workstream/component boundaries
- Workspace/scaffolding plan
- Whether a separate integration/orchestrator workspace is required
- Governance impact and owner approval

Topology choice rule:
- Select the simplest topology that preserves independent delivery and testability of required workstreams.
- If dependency isolation, ownership, or release cadence requires separation, choose `multi-repo`; otherwise `single-repo` is acceptable.
- For service-oriented architectures, best-practice default is **one service per repository**.
- Any deviation from service-per-repo best-practice must be documented as an ADR exception with rationale and approval.
- If mandatory topology controls are unresolved in planning behavior profile, treat topology decision as `BLOCKED` unless owner-approved exception is recorded.

If topology is `multi-repo`, planning must also provide:
- repo list and ownership map
- workstream-to-repo mapping with primary language/runtime
- cross-repo integration strategy
- contract agreement path and contract ownership (OpenAPI when HTTP APIs are involved)
- pack generation/distribution plan (skills/prompts/bootstrap assets)
- per-repo test evidence mapping (`TEST-UNIT-*`, `TEST-API-*`, `TEST-UI-*`)
- concurrency plan for independent service streams
- dependency graph showing prerequisite gates between workstreams

## Contract-first planning (mandatory)
- Define contract baseline before dependent implementation starts.
- Use OpenAPI for HTTP API boundaries.
- `docs/openapi-contract-plan.md` must identify:
	- contract owner(s)
	- versioning and compatibility rules
	- workstream responsibilities and interface boundaries
	- review cadence for contract changes

If OpenAPI contract plan is missing, phase status must be `BLOCKED`.

If topology decision is missing, phase status must be `BLOCKED`.

If planning behavior profile is not loaded/resolved, phase status must be `BLOCKED`.

If required plan storage controls are missing or violated, phase status must be `BLOCKED`.

## Data architecture decision (mandatory)
- Capture canonical runtime data architecture in `docs/data-architecture-decision.md` using `data-architecture-decision-template.md`.
- This artifact must declare expected runtime database/cache engines and allowed deviations.
- If declared runtime data architecture conflicts with implementation intent and no approved deviation is present, status must be `BLOCKED`.

## Planning-vs-skill capability gate (mandatory)
- If planning intent requires capabilities not currently available in installed MCP skills/actions, create `docs/tooling/skill-capability-gap.md` using `skill-capability-gap-template.md`.
- Gap artifact must include owner, ETA, unblock criteria, and required closure evidence path.
- Open capability gaps keep phase status `BLOCKED` unless owner-approved exception is recorded.

## Requirement quality rules
- Each requirement must include acceptance criteria in Given/When/Then format.
- Each requirement must include at least one error-path criterion where applicable.
- Each requirement must cite source artifact paths used to derive it.

## Source-of-truth precedence
1) Product specs in `SPEC_DIR`
2) Governance/process docs
3) Explicitly documented assumptions

If conflicts exist, record a decision and rationale in risks/assumptions.

## Tooling responsibilities
- Validate MCP/agent-tooling connectivity only; do not restart servers.
- Record checks using evidence blocks.

## MCP usage evidence (mandatory)
- Append phase evidence to `docs/tooling/mcp-usage-evidence.md` using `.iqpe-workflow/productWorkflowPack/mcp-usage-evidence-template.md`.
- Include action/tool IDs invoked, input summaries, output summaries, and artifact paths.
- If MCP evidence is missing, phase status must be `BLOCKED`.

## Gate requirement
Use `templates/phase-gate-template.md`.
If intent/requirements are incomplete or uncited, mark `BLOCKED`.
