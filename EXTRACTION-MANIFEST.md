# Extraction Manifest

## Scope

This package materializes the first actual extraction target: `iqpe-governance-workflow`.

## Source mapping

- Source: `prompts/productWorkflowPack`
  - Target: `prompts/productWorkflowPack`
- Source: `ProjectDocs/ProcessDocs`
  - Target: `ProcessDocs`

## Integrity rules

- Preserve file names and deterministic gate semantics (`PASS/FAIL/BLOCKED`).
- Keep process docs and prompts synchronized across related gate/policy changes.
- Record extracted updates in `CHANGELOG.md`.

## Next extraction increment

- Add automated parity check between source and extracted package before final repo split.
