# Compose Mode Decision Template

Use this artifact to declare the active docker compose intent for the run.

## Decision
- Compose mode: `local-dev` | `integration-demo`
- Scope:
- Owner:
- Date (UTC):

## Mode contract
### local-dev
- Purpose: single-repo/local developer runtime.
- Evidence required: local service run evidence + minimal dependencies.

### integration-demo
- Purpose: cross-repo integration using checked-out service repos.
- Evidence required: checkout/update evidence, compose build evidence, cross-service verification.

## Selected mode evidence
- Checkout/update command output path:
- Compose build/up command output path:
- Integration verification path(s):

## Notes
- If selected mode evidence is missing, release status must be `BLOCKED`.
