# Severity Classification Template

Use during release review for deterministic severity assignment.

## Classification rules
- Missing required evidence artifact -> Sev-2 (minimum)
- Missing mandatory traceability chain segment -> Sev-2
- Missing critical test proof for required path -> Sev-1
- Governance metadata incomplete (authority/approval fields) -> BLOCKED + Sev-2

## Findings
| Finding ID | Category | Severity | Rationale | Blocker ID |
|---|---|---|---|---|
| FIND-001 | evidence-missing | Sev-2 | Required artifact missing | BLK-001 |

## Blocker ownership
| blocker_id | owner_role | owner_name | eta_utc | unblock_criteria |
|---|---|---|---|---|
| BLK-001 | workflow-owner | <name> | <timestamp> | <criteria> |
