# Data Architecture Decision Template

Use this artifact to lock the canonical runtime data architecture and record approved deviations.

## Metadata
- Decision ID: `DA-XXXX`
- Status: Proposed | Approved | Superseded
- Date (UTC): `YYYY-MM-DD`
- Owner: `<owner-role-or-team>`

## Canonical runtime decision
- Primary database engine:
- Primary cache engine:
- Persistence boundary summary:
- Contract impact references (`TC-*`, ADR IDs):

## Required consistency checks
- Matches `docs/technology-constraints.md` (`TC-*`): yes/no
- Matches implementation evidence and deployment artifacts: yes/no
- If mismatch exists, release status must be `BLOCKED` until approved below.

## Approved deviations (if any)
| Deviation ID | Expected | Actual | Rationale | Approval Owner | Approval Status | Expiry/Review Date |
|---|---|---|---|---|---|---|
| DEV-DA-001 | Postgres + Redis | Local file state | MVP local-only bridge | architecture-owner | PROPOSED | YYYY-MM-DD |

## Evidence links
- Implementation evidence paths:
- Test evidence paths:
- Release review references:
