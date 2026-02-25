# Production Capability Planning Behavior Template

Use this template to force production-capable planning choices early.

## Scalability plan
- Baseline load assumptions:
- 10x growth target and scaling path:
- Horizontal/vertical scaling strategy by component:
- Capacity bottlenecks + mitigation:

## Performance plan
- SLO targets (p50/p95/p99 latency, throughput, error budget):
- Critical path budgets by subsystem:
- Performance test strategy and acceptance thresholds:

## Maintainability plan
- Ownership model (team/service):
- Required runbooks and operational docs:
- Test strategy coverage (unit/integration/contract/e2e):
- Dependency/version management policy:

## Upgrade and rollout plan (mandatory)
- Upgrade model (expand/migrate/contract, blue/green, canary):
- Backward compatibility requirements:
- Rollback criteria and rollback automation:
- Zero-downtime strategy (mandatory):
  - traffic shifting method:
  - database/schema compatibility during rolling deployment:
  - multi-version coexistence window:
  - no planned user-facing downtime declaration:

## Operability plan
- Alerting + dashboards:
- SLO/SLA reporting method:
- Incident response + on-call model:
- Disaster recovery tests and cadence:

## Gate checks
- [ ] Scalability and performance budgets are documented and measurable.
- [ ] Maintainability controls are explicit and owned.
- [ ] Upgrade plan includes rollback and compatibility strategy.
- [ ] Zero-downtime approach is documented and testable.
- [ ] Operability/SLO ownership is assigned.
