# iqpe-governance-workflow

Workflow governance repository for role prompts, gates, templates, and process standards.

## Extracted package contents

- `prompts/productWorkflowPack` (authoritative role prompts and gate contracts)
- `ProcessDocs` (process behavior, expected outputs, rollout guidance)
- `docs/README.md` (governance docs index)

## Owns

- Workflow prompt packs
- Gate criteria and phase policies
- Process documentation and runbooks
- Evidence template standards

## Does not own

- MCP runtime binaries
- Product implementation code
- Customer-specific product repos

## Required standards

- Maintain CHANGELOG entries with key-doc references.
- Keep phase gate criteria deterministic (`PASS/FAIL/BLOCKED`).
- Keep docs index updated when new workflow modules are added.

## CI and hosting

- GitHub Actions is the active CI host for early testing.
- Keep checks provider-neutral by preserving command contracts when moving to other CI hosts.
- Follow `CI-HOSTING-PORTABILITY.md` in this repo after extraction.

## Extraction provenance

- See `EXTRACTION-MANIFEST.md` for source mapping from monorepo paths.
