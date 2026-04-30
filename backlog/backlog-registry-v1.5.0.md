<!-- E-DVCS:
  file: backlog/backlog-registry-v1.5.0.md
  version: 1.5.0
  layer: invariant (I)
  governed-by: core/axioms-v1.6.0.md
  status: active
-->

# Backlog Registry

---

## §1 Invariant-Layer Deferrals

| ID     | Title                          | Priority | Status   | Spec Reference | Notes |
|--------|--------------------------------|----------|----------|----------------|------|
| ~~BL-I02~~ | ~~Axiom Compliance Linter~~ | medium   | ~~done~~ | — | superseded by validation engine (Phase 1.4) |
| BL-I03 | Checkpoint / Restore Mechanism | medium   | deferred | — | integrates with checkpoint + replay system |

---

## §2 Covariant-Layer Deferrals

| ID     | Title                     | Priority | Status   | Spec Reference | Notes |
|--------|---------------------------|----------|----------|----------------|------|
| BL-C01 | Profile Schema Validation | low      | deferred | onboarding/wizard-spec-v1.2.0.md §5.2 | unchanged |
| BL-C02 | Project Template Expansion | low     | deferred | onboarding/wizard-spec-v1.2.0.md §8 | unchanged |

---

## §3 Active Phase 1 Items

| ID     | Title                          | Priority | Status   | Spec Reference | Notes |
|--------|--------------------------------|----------|----------|----------------|------|
| BL-I09 | Dependency Ledger System       | high     | complete | execution-plan-v1.0.0 §1.1 | traceability foundation |
| BL-I10 | Execution Context Injection    | high     | complete | execution-plan-v1.0.0 §1.2 | runtime binding layer |
| BL-I11 | Checkpoint Enrichment          | high     | active   | execution-plan-v1.0.0 §1.3 | state snapshot + persistence |
| BL-I12 | Deterministic Replay Protocol  | high     | pending  | execution-plan-v1.0.0 §1.4 | execution reconstruction layer |

---

## §4 Completed

| ID     | Title                     | Completed   | Notes |
|--------|--------------------------|-------------|------|
| ~~BL-I01~~ | ~~Onboarding Wizard POC~~ | ~~2026-04-17~~ | retained for traceability |

---

## §5 Transition Notes

- Phase 0 → COMPLETE
- Phase 1 → ACTIVE (determinism recovery in progress)
- Phase 1 now forms a full deterministic pipeline:
  dependency → execution context → checkpoint → replay

No orphan or misaligned Phase 1 identifiers remain.

---

## MANDATORY CHANGELOG

| Version | Date       | State  | Description |
|---------|------------|--------|------------|
| `v1.0.0`| 2026-04-16 | `active` | Initial registry. Three invariant-layer items (BL-I01–BL-I03), two covariant-layer items (BL-C01–BL-C02). |
| `v1.1.0`| 2026-04-16 | `active` | Added spec references and priority fields; linked BL-I01 to wizard-spec-v1.0.0.                     |       
| `v1.2.0`| 2026-04-16 | `active` | Updated BL-I01 status to `in-progress` after wizard-spec-v1.1.0 completion.                         |       
| `v1.3.0`| 2026-04-17 | `active` | Ecosystem rename: `wertha-seed` → `INV0`. Updated all references. Linked BL-I01 to wizard-spec-v1.2.0. |
| `v1.4.0`| 2026-04-17 | `active` | Closed BL-I01 (Onboarding Wizard POC). Moved to new §3 Completed section with acceptance date 2026-04-17. |
| `v1.5.0` | 2026-04-30 | active | Re-indexed Phase 1 identifiers for causal consistency. Mapped BL-I11 → Checkpoint Enrichment and BL-I12 → Deterministic Replay Protocol. Removed identity misplacement drift from Phase 1 registry. |
