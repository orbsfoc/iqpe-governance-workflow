# Repository Portfolio Target Structure

## Objective

Define a maintainable, company-friendly repository model that separates workflow governance, MCP runtime, reusable skills, architecture standards, and product implementations.

## Recommended target repos

1. **iqpe-governance-workflow**
   - Owns workflow prompts, gates, templates, and process standards.
   - Primary contents:
     - product workflow pack
     - process docs
     - governance templates

2. **iqpe-mcp-runtime**
   - Owns MCP server runtime, action runners, and integration contracts.
  - Implementation language baseline: Go.
   - Primary contents:
     - MCP server modes
     - action registry and runner logic
     - runtime interfaces

3. **iqpe-skill-pack**
   - Owns reusable skills and versioned skill release process.
  - Any executable tooling helpers should be Go-based.
   - Primary contents:
     - skill definitions
     - skill version index
     - skill packaging notes

4. **iqpe-architecture-standards**
   - Owns ADR baselines, tech policy, and tech radar governance.
   - Primary contents:
     - ADR baselines
     - phase-aware technology policy
     - architecture-to-operations standards

5. **iqpe-library-catalog**
   - Owns reusable module/library catalog and topology indexes.
   - Primary contents:
     - module/library catalog
     - repo/service topology index
     - metadata schemas and quality checks

6. **iqpe-product-<domain>** (one per product/customer domain)
   - Owns product implementation, delivery artifacts, and product-specific docs.
   - Primary contents:
     - product source
     - product docs and handoffs
     - release outputs

## Cross-repo integration model

- Integration boundary is MCP plus documented contracts.
- Repos must not rely on implicit file-level coupling.
- All cross-repo dependencies should be versioned and traceable.

## Required standards in every repo

- `CHANGELOG.md` with key-doc references and change descriptions
- Ownership metadata and maintainers
- Build/test entrypoints documented and runnable in isolation
- Release gate checklist and evidence location

## Tooling portability policy

- Tooling/runtime repositories should standardize on Go implementations to maximize portability.
- Non-Go tooling is allowed only via approved exception with explicit replacement/migration plan.

## Why this structure scales

- Reduces monolithic coupling.
- Aligns ownership to team boundaries.
- Improves maintainability for long-lived maintenance phases.
- Simplifies enterprise review (security/compliance/platform) per repository purpose.
