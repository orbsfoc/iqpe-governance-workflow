# Repo Change Plan Template

Use this file as `docs/plans/repo-change-plan.md` to make repository create/update decisions explicit.

## Decision summary
- Topology: single-repo | multi-repo
- Decision owner:
- Date (UTC):

## Repo action matrix
| Service/Module ID | Capability | Repo Action (create/update) | Target Repo | Existing Repo Candidates Considered | Boundary/Ownership Rationale | Lifecycle Cost Impact | Approval |
|---|---|---|---|---|---|---|---|
| SVC-001 | Example capability | update | repos/go-application-service | repos/go-application-service | Existing boundary fits ownership and cadence | Lower maintenance overhead | Approved |

## Create-action justifications (mandatory)
For each `create` row above:
- Why existing repos are insufficient:
- Why new boundary is necessary:
- Ownership model:
- Maintenance/operational cost forecast:
- Sunset/deprecation conditions:

## Gate checks
- [ ] Every planned service/module has a repo action (`create` or `update`).
- [ ] Every `create` action has explicit necessity and boundary justification.
- [ ] Existing repo reuse was considered for each service/module.
- [ ] Lifecycle maintenance cost impact is documented for all actions.
