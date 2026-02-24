# Plans Index Template

Use this file as `docs/plans/index.md` when planning behavior profile resolves:
- `plan_storage_mode: per-story-files`
- `plan_directory: docs/plans`

## Profile alignment
- Plan storage mode:
- Plan directory:
- Plan index file:
- Plan story file pattern:
- Plan traceability required:

## Story plan mapping
| REQ ID | PLAN ID | Story/Workstream | Plan File Path | Target Repo Path | Target Service ID | Owner | Status | DIAG IDs | TEST IDs |
|---|---|---|---|---|---|---|---|---|---|
| REQ-001 | PLAN-001 | Example story | docs/plans/PLAN-001-example-story.md | repos/go-application-service | SVC-EXAMPLE-001 | team-a | PLANNED | DIAG-001 | TEST-UNIT-001 |

## Handoff routing linkage
| PLAN ID | Producer Phase | Consumer Phase | Handoff ID | Routing Matrix Path | Ack Evidence Path |
|---|---|---|---|---|---|
| PLAN-001 | 01 | 02 | HO-001 | docs/handoffs/routing-matrix.md | docs/handoffs/ack/HO-001.md |

## Notes
- Every `PLAN-*` must map to exactly one plan file path.
- Keep plan file paths stable over time; if renamed, update this index and traceability matrix in the same change.
- Status values should be deterministic (`PLANNED`, `IN-PROGRESS`, `DONE`, `BLOCKED`).
