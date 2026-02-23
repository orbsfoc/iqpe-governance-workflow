# Local to Hosted Rollout Plan (GitHub + Actions)

## Objective

Provide a low-risk path from local-only testing to fully hosted repositories with automated pipelines.

## Phase 0: Local-first baseline (current)

- Validate workflow and MCP behavior locally.
- Keep process and feature docs evolving quickly.
- Ensure artifacts and gates are deterministic.

**Exit criteria**
- Local workflow runs repeatably.
- Required artifacts are consistently produced.
- Changelog and traceability discipline is stable.

## Phase 1: Hosted mirror with manual controls

- Host current repo in GitHub.
- Keep deployment manual while preserving local execution.
- Start issue templates and pull request template for governance.

**Minimum controls**
- Branch protection on main
- Required review for process/gate changes
- Manual release notes from changelog

## Phase 2: Foundational GitHub Actions

Add baseline workflows:

1. **docs-quality.yml**
   - Validate required process docs exist.
   - Validate changelog updates for relevant changes.

2. **workflow-governance.yml**
   - Validate gate artifacts/templates are present and current.
   - Validate required fields in governance artifacts.

3. **mcp-runtime-smoke.yml** (for runtime/tooling repos)
   - Build runtime components.
   - Run self-tests for supported server modes.

4. **feature-spec-validation.yml**
   - Validate feature-doc structure and required sections.

**Exit criteria**
- CI blocks merges on governance or structure violations.
- Team can diagnose failures from CI output without deep repo knowledge.

## Phase 3: Portfolio split + federated pipelines

As repos split:

- Move each domain into dedicated repo with scoped pipelines.
- Add cross-repo compatibility checks through versioned interfaces.
- Keep shared policy checks in reusable workflow templates.

## Phase 4: Advanced enterprise controls

- Signed releases and provenance attestations
- Security/license scanning at policy-defined thresholds
- Scheduled consistency checks for topology, metadata, and traceability

## Recommended GitHub Actions strategy

- Start with reusable workflow templates for consistency.
- Use repo-specific override only where justified.
- Keep quality gates deterministic and explainable.

## Suggested initial workflow set for this project

- docs-quality.yml
- process-gate-validation.yml
- changelog-enforcement.yml
- mcp-smoke-test.yml

## Operations note

During early phases, local testing remains primary; CI should confirm and enforce baseline quality, not replace local diagnosis.
