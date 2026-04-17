# INV0

A locally-operated, Git-backed personal orchestration layer.

## What This Is

This repository is the **Invariant Core** ($\mathcal{I}$) of the `INV0` ecosystem.
It holds the axioms, identity, onboarding protocols, and state management
that remain constant across all users and projects.

Each user gets a **Covariant Brain** ($\mathcal{C}(u)$) — a profile + project
configuration generated from the invariant core via the Onboarding Wizard
(`onboarding/wizard-spec-v1.2.0.md`). The architecture is expressed as:

$$\text{Ecosystem} = \mathcal{I} \oplus \mathcal{C}(u)$$

The Onboarding Wizard is the **sole canonical authority** for $\mathcal{C}(u)$
topology (per A-5, `core/axioms-v1.4.0.md`).

## Constraints

| Constraint   | Axiom | Value                                      |
|--------------|-------|--------------------------------------------|
| Network      | A-1   | INTRANET — air-gapped, local-only          |
| Persistence  | A-3   | Git-backed — all state versioned via Git   |
| Agent Model  | A-2   | Identity Collapse — single AI agent        |
| Users        | —     | Vaheed (expert), Mehrsa (guided)           |

## Quickstart

1. Clone or init this repo locally.
2. Read `core/axioms-v1.4.0.md` for non-negotiable rules.
3. Read `core/identity-v1.0.0.md` for system identity and roles.
4. Run the Onboarding Wizard (`onboarding/wizard-spec-v1.0.0.md`)
   to generate your $\mathcal{C}(u)$ topology and user profile.

## Structure

### Invariant Layer ($\mathcal{I}$) — Director-authorized changes only

- `core/` — Axioms and identity.
- `onboarding/` — Wizard spec and onboarding protocols.
- `backlog/` — Deferred work, serialized and governed.

### Covariant Layer ($\mathcal{C}(u)$) — User-scoped, wizard-generated

Directory topology is defined per-user by the Onboarding Wizard.
No fixed directory structure is presumed; see `onboarding/wizard-spec-v1.0.0.md`
for the canonical generation schema.

### Optional

- `docs/` — Deep documentation (if needed).

## MANDATORY CHANGELOG

| Version   | Date       | State     | Description                                                                 |
|-----------|------------|-----------|-----------------------------------------------------------------------------|
| `v1.0.0`  | 2026-04-16 | `release` | Initial seed repository. Defined $\mathcal{I} \oplus \mathcal{C}(u)$ architecture, constraints, and structure. |
| `v1.1.0`  | 2026-04-17 | `draft`   | Aligned with axioms v1.4.0. Delegated $\mathcal{C}(u)$ topology to Onboarding Wizard (A-5). Replaced legacy Vector nomenclature with axiom IDs. Removed premature fixed-directory assumptions from Quickstart and Structure. |

