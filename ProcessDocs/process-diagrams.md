# Process Diagrams

These diagrams visualize the workflow lifecycle and artifact production path.

## Diagrams

- `workflow-lifecycle.mmd`: end-to-end phase and gate flow
- `artifact-production-sequence.mmd`: setup and phase output sequence
- `mcp-skills-touchpoints.mmd`: sources of input and MCP server/skill/action touchpoints
- `workstream-review-loop.mmd`: implementation, testing, review, remediation, and gate loops

## Detailed stage diagrams

- `stage-00-initialization.mmd`: bootstrap, preflight, spec detection, planning behavior resolution, and initialization gates
- `stage-01-product-owner.mmd`: product intent/requirements/topology/contract planning and PO gate checks
- `stage-02-architect.mmd`: implementation planning, constraints/ADRs/diagrams, dependency modeling, and architect gates
- `stage-03-developer.mmd`: PLAN-driven implementation loops, review/remediation loops, integration loops, and developer gates
- `stage-04-release-review.mmd`: final readiness checks, severity/governance decisions, and GO/NO-GO/BLOCKED outcomes
