# Storage Planning Behavior Template

Use this template to document how each data type maps to storage characteristics.

## Decision summary
- Primary system of record:
- Secondary storage systems used:
- Why this mapping is production-appropriate:

## Data category mapping
| Data type | Recommended storage | Access pattern | Latency target | Durability target | Scaling model | Structure/model |
|---|---|---|---|---|---|---|
| Transactional records | Relational database | OLTP, point reads/writes | Low ms | High (ACID + backups) | Vertical + read replicas + partitioning | Normalized relational schema |
| Session/cache data | In-memory cache | High QPS read-heavy | Sub-ms to low ms | Low-medium (rebuildable) | Horizontal sharding | Key/value |
| Blobs/files | Object storage | Large object read/write | Medium | Very high (multi-AZ/region options) | Elastic/object namespace | Object + metadata |
| Search/discovery | Search index | Full-text/filter queries | Low-medium | Rebuildable from source | Horizontal shards/replicas | Inverted index documents |
| Analytics/time-series | Columnar/time-series store | Aggregations/scans | Medium-high | Medium-high | Horizontal partitioning by time/key | Wide-column/time-series |

## Selection heuristics
- Prefer relational DB for critical business invariants and transactional consistency.
- Prefer cache for derived/hot data with explicit TTL and invalidation strategy.
- Prefer object storage for binary payloads, large files, and immutable artifacts.
- Prefer search index only for query acceleration, not as source-of-truth.
- Prefer append-friendly or columnar models for telemetry/analytics workloads.

## Non-functional requirements
- Expected throughput and peak concurrency:
- Read/write ratio:
- Retention policy and archival policy:
- Backup + restore RTO/RPO:
- Multi-AZ/region durability and failover design:

## Gate checks
- [ ] Every data category has a chosen storage type and rationale.
- [ ] Source-of-truth boundaries are explicit.
- [ ] Durability + backup/restore requirements are defined.
- [ ] Scaling plan exists for 10x expected load.
