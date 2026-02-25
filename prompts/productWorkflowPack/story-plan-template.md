# Story Plan Template

Use this template for each story/workstream plan file under `docs/plans/`.

## Identity
- PLAN ID: PLAN-XXX
- Story slug: <kebab-case-slug>
- File path: docs/plans/PLAN-XXX-<kebab-case-slug>.md
- Owner:
- Status: PLANNED | IN-PROGRESS | DONE | BLOCKED

## Source traceability
- Requirement IDs: REQ-XXX, REQ-YYY
- Spec sources (paths in `SPEC_DIR`):
- Related topology decision section:
- Related contract section:

## Scope
- In-scope:
- Out-of-scope:
- Dependencies (PLAN IDs / service prerequisites):

## Service/module value balance (mandatory)
- Customer/business value delivered:
- Existing module/service reuse considered:
- Service/module necessity evidence (why this must exist as separate module/service):
- Duplicate-capability check (which existing modules were assessed and why they are insufficient):
- Build-vs-buy/reuse decision and balanced rationale:
- Expected lifecycle maintenance cost (engineering + operational):
- Ownership and sunset/deprecation intent:

## Implementation approach
- Components/services affected:
- API/interface changes:
- Data model/storage changes:
- Error-path handling notes:

## Production readiness (mandatory)
- Scalability assumptions and target load:
- Performance SLO targets (p95/p99 latency, error budget):
- Maintainability controls (ownership, runbooks, testability):
- Upgrade strategy (expand/migrate/contract or equivalent):
- Zero-downtime upgrade plan (traffic shifting, backward compatibility, rollback):

## Verification plan
- Unit tests: TEST-UNIT-XXX
- API tests: TEST-API-XXX
- UI tests: TEST-UI-XXX
- Contract compatibility checks:

## Diagram and evidence linkage
- Diagram IDs: DIAG-XXX
- ADR references:
- MCP evidence blocks:

## Handoff notes
- Reviewer feedback loop notes:
- Remediation actions:
- Release risk notes:
