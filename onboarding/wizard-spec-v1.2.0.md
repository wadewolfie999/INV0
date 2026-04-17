<!-- E-DVCS:
  file: onboarding/wizard-spec-v1.2.0.md
  version: 1.2.0
  layer: invariant (I)
  governed-by: core/axioms-v1.5.0.md
  status: draft
-->

# Onboarding Wizard — Specification

## §1 Purpose

This document defines the canonical Onboarding Wizard for the
`INV0` ecosystem. The wizard is the **sole authority** for
generating the covariant layer $\mathcal{C}(u)$ topology (A-5).

It replaces all prior ad-hoc onboarding references and README-level
quickstart templates.

## §2 Scope & Governing Documents

| Document                        | Role                                      |
|---------------------------------|-------------------------------------------|
| `core/axioms-v1.5.0.md`        | Constraint matrix (A-0 through A-12)      |
| `core/identity-v1.1.0.md`      | Entity, Director, AI Partner, Values      |
| This spec                       | $\mathcal{C}(u)$ topology & onboarding flow |

**Invariant classification:** This file resides in `onboarding/`
($\mathcal{I}$). Modifications require Director authorization (A-5).

## §3 Question Flow

The wizard consists of **8 sequential questions**. All questions are
mandatory unless marked conditional.

| #  | Question                                                        | Maps To                        | Axiom   |
|----|-----------------------------------------------------------------|--------------------------------|---------|
| Q1 | What is your username or handle?                                | `profiles/<username>/`         | A-5     |
| Q2 | What is the project name? (skip if none yet)                    | `projects/<project>/`          | A-5     |
| Q3 | Where on the interaction spectrum do you prefer? (Expert ↔ Guided) | Session verbosity & pacing  | A-4     |
| Q4 | Describe the project's purpose in one sentence.                 | `profile-v1.0.0.md`, project README | A-8 |
| Q5 | Primary language or technology stack?                            | Scaffold templates             | A-9     |
| Q6 | Which initial artifact types are needed? (docs / code / config) | File generation plan           | A-9     |
| Q7 | Do you have existing/legacy files to ingest?  (Y/N)             | Migration path trigger         | A-3     |
| Q8 | *(Conditional: Q7 = Y)* List file types, formats, and locations. | `migration-manifest-v1.0.0.md` | A-3, A-11 |

### §3.1 Q3 Spectrum Behavior

The Q3 answer sets the **session interaction mode** per A-4:

| Response     | Behavior                                                              |
|--------------|-----------------------------------------------------------------------|
| Expert       | Terse output. No explanatory scaffolding. Raw artifact emission.      |
| Guided       | Step-by-step explanations. Contextual notes on every generated file.  |
| Mid-spectrum | Balanced: brief rationale per artifact, no hand-holding.              |

The mode persists for the duration of the onboarding session and
propagates as a metadata field in the user profile.

### §3.2 Q7–Q8 Legacy Detection & Migration Path

If Q7 = **Y**, the wizard:

1. Collects file metadata via Q8.
2. Generates `migration/migration-manifest-v1.0.0.md` — a structured
   inventory of legacy artifacts with target locations in $\mathcal{C}(u)$.
3. Emits Git guidance for staging the migration (A-11).

If Q7 = **N**, the `migration/` directory is omitted from the topology.

## §4 Spectrum-Adaptive Output Rules

All wizard outputs respect Q3 mode selection:

| Artifact                     | Expert Mode             | Guided Mode                          |
|------------------------------|-------------------------|--------------------------------------|
| Directory scaffold           | Tree only               | Tree + per-directory explanation      |
| `profile-v1.0.0.md`         | Template, no commentary | Template + field-by-field walkthrough |
| `migration-manifest-v1.0.0.md` | Raw manifest table   | Manifest + migration strategy notes   |
| Git commands                 | Commands only           | Commands + rationale per step         |

Mid-spectrum: tree + one-line descriptions; commands + inline comments.

## §5 Output Artifacts & $\mathcal{C}(u)$ Topology

### §5.1 Canonical Directory Structure

Upon wizard completion, the following $\mathcal{C}(u)$ topology is generated:

```
profiles/
  <username>/
    profile-v1.0.0.md

projects/
  <project>/
    README-v1.0.0.md

state/
  checkpoints/

migration/                          ← conditional (Q7 = Y only)
  migration-manifest-v1.0.0.md
All directory and file names comply with A-10 (versioning suffix convention).

### §5.2 Artifact Descriptions

| Artifact                          | Content                                                      |
|-----------------------------------|--------------------------------------------------------------|
| `profile-v1.0.0.md`              | Username, preferred mode (Q3), stack (Q5), values echo.      |
| `README-v1.0.0.md` (project)     | Project name (Q2), purpose (Q4), stack (Q5), artifact plan (Q6). |
| `state/checkpoints/`             | Empty directory. Reserved for future checkpoint commits.     |
| `migration-manifest-v1.0.0.md`   | Legacy file inventory: source path, format, target $\mathcal{C}(u)$ path, status. |

### §5.3 E-DVCS Version Blocks (A-7)

Every generated artifact begins with an E-DVCS header:

markdown
<!-- E-DVCS:
  file: <path/filename>
  version: 1.0.0
  layer: covariant (C(u))
  parent: onboarding/wizard-spec-v1.2.0.md
  status: draft
-->

This header:

- Binds the file to its generating spec (`wizard-spec-v1.2.0.md`).
- Declares its layer membership (`C(u)`).
- Establishes a traceable lineage for future diffs and audits.

## §6 Git-Backed Flow (A-3, A-11)

The wizard operates under strict Git-backed persistence:

1. **Pre-flight check:**

   - Verify that the working directory is a Git repo.
   - Verify that `core/axioms-v1.5.0.md` and `core/identity-v1.1.0.md`
     exist and are readable.
   - Confirm working tree status (clean/dirty).

2. **Staging guidance:**

   - After generating artifacts, the wizard proposes:

     ```bash
     git status
     git add <new/modified paths>
     ```

   - Expert mode: show commands only.
   - Guided mode: annotate each command with reasoning.

3. **Commit guidance:**

   - Provide a commit message template, e.g.:

     ```text
     onboarding: init C(u) for <username>/<project> via wizard-spec-v1.2.0
     ```

   - Optionally suggest tagging:

     ```bash
     git tag -a v1.0.0-onboarding-<username>-<project> -m "Initial C(u) scaffold"
     ```

4. **No auto-commit:**

   - The wizard must not execute Git commands autonomously.
   - All commands are suggestions for the human orchestrator to run.

## §7 Error Handling & Axiom Enforcement

The wizard must **halt and report** if:

- `core/axioms-v1.5.0.md` or `core/identity-v1.1.0.md` are missing.
- The repository is not a valid Git repo.
- The wizard is invoked from outside the repo root.
- Any planned write would violate A-5 (attempt to modify `core/`,
  `onboarding/`, or `backlog/`).

On such errors:

- Expert mode: report succinct error with a minimal reproduction hint.
- Guided mode: include remediation steps (e.g., "cd into repo root and retry").

## §8 Extensibility Notes

Future versions of the wizard may:

- Add richer project templates (e.g., language-specific directories).
- Introduce automated checks (linting, unit tests) post-onboarding.
- Expand Q3 spectrum to include additional modes.

Any such changes must:

- Remain governed by `core/axioms-v1.5.0.md`.
- Preserve backward compatibility with existing $\mathcal{C}(u)$ artifacts
  wherever feasible.
- Be reflected in this document's `## MANDATORY CHANGELOG`.

## MANDATORY CHANGELOG

| Version   | Date       | State     | Description                                                                 |
|-----------|------------|-----------|-----------------------------------------------------------------------------|
| `v1.0.0`  | 2026-04-16 | `draft`   | Initial wizard spec. Defined 8-question flow and baseline $\mathcal{C}(u)$ topology under axioms-v1.3.0. |
| `v1.1.0`  | 2026-04-16 | `draft`   | Updated to be governed by `core/axioms-v1.5.0.md`. Clarified Q7–Q8 migration path, added explicit Git-backed flow section (§6), and tightened error handling semantics to enforce A-5 and A-12. |
| `v1.2.0`  | 2026-04-17 | `draft`   | Ecosystem renaming: all `wertha-seed` references replaced with `INV0` per CEO directive. Updated §1, §2 (identity reference), §5.3 (E-DVCS parent), and §6 (pre-flight check). |


