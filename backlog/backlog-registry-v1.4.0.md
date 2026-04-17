<!-- E-DVCS:
  file: backlog/backlog-registry-v1.4.0.md
  version: 1.4.0
  layer: invariant (I)
  governed-by: core/axioms-v1.5.0.md
  status: active
-->

# Backlog Registry

## §1 Invariant-Layer Deferrals

| ID     | Title                              | Priority | Status      | Spec Reference                          | Notes                                      |
|--------|------------------------------------|----------|-------------|-----------------------------------------|--------------------------------------------|
| BL-I02 | Axiom Compliance Linter            | medium   | deferred    | —                                       | Automated check that all files satisfy A-0–A-12. |
| BL-I03 | Checkpoint / Restore Mechanism     | medium   | deferred    | —                                       | Leverage `state/checkpoints/` (wizard-spec §5.1). |

## §2 Covariant-Layer Deferrals

| ID     | Title                              | Priority | Status      | Spec Reference                          | Notes                                      |
|--------|------------------------------------|----------|-------------|-----------------------------------------|--------------------------------------------|
| BL-C01 | Profile Schema Validation          | low      | deferred    | `onboarding/wizard-spec-v1.2.0.md` §5.2 | Formal schema for `profile-v1.0.0.md`.     |
| BL-C02 | Project Template Expansion         | low      | deferred    | `onboarding/wizard-spec-v1.2.0.md` §8   | Language-specific scaffolds.               |

## §3 Completed

| ID     | Title                              | Priority | Completed   | Spec Reference                          | Notes                                      |
|--------|------------------------------------|----------|-------------|-----------------------------------------|--------------------------------------------|
| BL-I01 | Onboarding Wizard POC              | high     | 2026-04-17  | `onboarding/wizard-spec-v1.2.0.md`      | Full spec (v1.2.0) authored & accepted. 8-question flow, $\mathcal{C}(u)$ topology, spectrum-adaptive output, Git-backed flow, error handling defined. |

## MANDATORY CHANGELOG

| Version | Date       | State    | Description                                                                                          |
|---------|------------|----------|------------------------------------------------------------------------------------------------------|
| `v1.0.0`| 2026-04-16 | `active` | Initial registry. Three invariant-layer items (BL-I01–BL-I03), two covariant-layer items (BL-C01–BL-C02). |
| `v1.1.0`| 2026-04-16 | `active` | Added spec references and priority fields; linked BL-I01 to wizard-spec-v1.0.0.                     |
| `v1.2.0`| 2026-04-16 | `active` | Updated BL-I01 status to `in-progress` after wizard-spec-v1.1.0 completion.                         |
| `v1.3.0`| 2026-04-17 | `active` | Ecosystem rename: `wertha-seed` → `INV0`. Updated all references. Linked BL-I01 to wizard-spec-v1.2.0. |
| `v1.4.0`| 2026-04-17 | `active` | Closed BL-I01 (Onboarding Wizard POC). Moved to new §3 Completed section with acceptance date 2026-04-17. |

