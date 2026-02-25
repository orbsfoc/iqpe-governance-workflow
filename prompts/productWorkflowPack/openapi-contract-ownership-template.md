# OpenAPI Contract Ownership Boundary

Use this file as `docs/openapi-contract-ownership.md` when both client and server depend on the same API contract.

- Contract Boundary Type: independent-contract-repository | equivalent-independent-boundary
- Source of Truth Artifact Path:
- Source of Truth Owner:
- Consumer Repositories:
  - client:
  - server:
- Change Approval Owner:
- Approval Status: APPROVED | PROPOSED | BLOCKED
- Compatibility Policy:
- Evidence Path:

Rules:
- Required when shared client/server dependency exists.
- Must not leave client or server implementation repo as implicit source of truth.
- Missing or unapproved ownership boundary keeps status `BLOCKED`.
