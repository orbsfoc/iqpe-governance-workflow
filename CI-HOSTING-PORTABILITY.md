# CI Hosting Portability (Governance Repo)

## Current host

GitHub Actions is used for early testing.

## Command contract (host-neutral)

Every CI host must preserve these checks:

1. Required baseline docs exist.
2. Required governance content exists:
   - `prompts/productWorkflowPack/README.md`
   - `prompts/productWorkflowPack/00-orchestrator.md`
   - `ProcessDocs/process-overview.md`
   - `ProcessDocs/phase-by-phase-checklist.md`
3. Pipeline fails when required files are missing.

## Migration rule

When moving away from GitHub, port checks with identical command semantics first, then optimize.
