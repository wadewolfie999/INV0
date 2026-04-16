# WERTHA Seed

A locally-operated, Git-backed personal orchestration layer.

## What This Is

This repository is the **Invariant Core** ($\mathcal{I}$) of the WERTHA ecosystem.
It holds the axioms, identity, onboarding protocols, and state management
that remain constant across all users and projects.

Each user gets a **Covariant Brain** ($\mathcal{C}(u)$) — a profile + project
configuration generated from the invariant core via onboarding. The architecture
is expressed as:

$$\text{Ecosystem} = \mathcal{I} \oplus \mathcal{C}(u)$$

## Constraints

| Constraint   | Value                                      |
|--------------|--------------------------------------------|
| Network      | INTRANET — air-gapped, local-only          |
| Persistence  | Git-backed (Vector 2)                      |
| Agent Model  | Identity Collapse (Vector 6) — single agent|
| Users        | Vaheed (expert), Mehrsa (guided)           |

## Quickstart

1. Clone or init this repo locally.
2. Read `core/axioms-v1.0.0.md` for non-negotiable rules.
3. Read `core/identity-v1.0.0.md` for system identity and roles.
4. To onboard a new user, copy `onboarding/templates/new-user.md` into `profiles/<name>.md` and fill it in.
5. Register a project under `projects/<project-name>/README.md`.
6. Checkpoints go in `state/checkpoints/` using CSM/VRL format.

## Structure

- `core/` — Axioms and identity (the $\mathcal{I}$ layer).
- `profiles/` — Per-user covariant brains ($\mathcal{C}(u)$).
- `projects/` — Active initiatives, one directory each.
- `state/` — Checkpoints (CSM/VRL) and thread log.
- `backlog/` — Deferred work, serialized and governed.
- `onboarding/` — Templates for generating new $\mathcal{C}(u)$ instances.
- `docs/` — Optional deep documentation.

## MANDATORY CHANGELOG

| Version   | Date       | State     | Description                                                                 |
|-----------|------------|-----------|-----------------------------------------------------------------------------|
| `v1.0.0`  | 2026-04-16 | `release` | Initial seed repository. Defined $\mathcal{I} \oplus \mathcal{C}(u)$ architecture, constraints, and structure. |

