<!-- E-DVCS:
  file: onboarding/wizard-spec-v1.1.0.md
  version: 1.1.0
  layer: invariant (I)
  governed-by: core/axioms-v1.5.0.md
  status: draft
-->

# Onboarding Wizard — Specification

## §1 Purpose

This document defines the canonical Onboarding Wizard for the
`wertha-seed` ecosystem. The wizard is the **sole authority** for
generating the covariant layer $\mathcal{C}(u)$ topology (A-5).

It replaces all prior ad-hoc onboarding references and README-level
quickstart templates.

## §2 Scope & Governing Documents

| Document                        | Role                                      |
|---------------------------------|-------------------------------------------|
| `core/axioms-v1.5.0.md`        | Constraint matrix (A-0 through A-12)      |
| `core/identity-v1.0.0.md`      | Entity, Director, AI Partner, Values      |
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
```
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


<!-- E-DVCS:
  file: <relative-path>
  version: <semver>
  layer: covariant C(u)
  generated-by: onboarding/wizard-spec-v1.1.0.md
  status: draft
-->

No artifact may be emitted without this block.

### §5.4 Delivery Mode (A-12)

Artifact delivery is determined by the Orchestrator-Routing Toggle:

| State                     | Behavior                                                                 |
|---------------------------|--------------------------------------------------------------------------|
| **DEFAULT** (GUI/Browser) | All artifacts emitted as fenced Markdown code blocks. Orchestrator manually routes to `INVO-0`. |
| **OVERRIDE** (CLI/Agentic)| Artifacts written directly to filesystem by the AI Partner. Autonomous `INVO-0` manipulation. |

Current session state is **DEFAULT** unless the Director has issued an
explicit override command (A-12).

## §6 Git Guidance Protocol (A-11)

### §6.1 Post-Generation Commands

After all artifacts are emitted, the wizard provides a complete
Git staging and commit sequence:

bash
# Stage all generated C(u) artifacts
git add profiles/<username>/profile-v1.0.0.md
git add projects/<project>/README-v1.0.0.md
git add state/checkpoints/.gitkeep

# Conditional: migration path
git add migration/migration-manifest-v1.0.0.md   # only if Q7 = Y

# Commit
git commit -m "onboarding: initialize C(u) for <username> | profile, project <project>, state scaffold"

# Tag
git tag onboarding-<username>-v1.0.0

### §6.2 Delivery Mode Interaction (A-11 × A-12)

| A-12 State  | Git Guidance Behavior                                                    |
|-------------|--------------------------------------------------------------------------|
| **DEFAULT** | Commands emitted as code blocks with contextual commentary (per Q3 mode). Orchestrator executes manually. |
| **OVERRIDE**| Commands may be executed autonomously by the AI Partner.                  |

### §6.3 Migration-Specific Git Guidance

When Q7 = Y, additional commands are appended:

bash
# Stage legacy files per migration manifest
git add <target-paths-from-manifest>

# Commit migration
git commit -m "migration: ingest legacy artifacts for <username> per migration-manifest-v1.0.0"

## §7 Conditional Execution Matrix

Wizard behavior branches based on two state variables:

| Q7 (Legacy?) | A-12 State | Generated Topology                                | Delivery       | Git Guidance     |
|---------------|------------|---------------------------------------------------|----------------|------------------|
| N             | DEFAULT    | `profiles/`, `projects/`, `state/`                | Code blocks    | Manual guidance  |
| N             | OVERRIDE   | `profiles/`, `projects/`, `state/`                | Direct write   | Auto-executable  |
| Y             | DEFAULT    | `profiles/`, `projects/`, `state/`, `migration/`  | Code blocks    | Manual guidance  |
| Y             | OVERRIDE   | `profiles/`, `projects/`, `state/`, `migration/`  | Direct write   | Auto-executable  |

## §8 Axiom Compliance Matrix

| Axiom | Requirement                          | Wizard Compliance                                                    | Status |
|-------|--------------------------------------|----------------------------------------------------------------------|--------|
| A-0   | Sovereign Authority                  | Wizard executes only on Director initiation.                         | ✅      |
| A-1   | INTRANET Constraint                  | No external dependencies. All artifacts local.                       | ✅      |
| A-2   | Identity Collapse                    | Single-agent execution. No persona framing.                          | ✅      |
| A-3   | Git-Backed Persistence               | All outputs committed via §6. Legacy ingest via §3.2.               | ✅      |
| A-4   | Dynamic Design                       | Q3 spectrum-adaptive mode. §4 output rules.                         | ✅      |
| A-5   | Invariant/Covariant Separation       | Wizard is canonical $\mathcal{C}(u)$ topology authority. §5.1.      | ✅      |
| A-6   | Mandatory Changelog                  | All generated artifacts include changelog section.                   | ✅      |
| A-7   | E-DVCS Enforcement                   | All outputs carry E-DVCS header. §5.3.                              | ✅      |
| A-8   | Contextual Economy ($W_{ctx}$)       | Q3 mode governs verbosity. Expert mode minimizes tokens.             | ✅      |
| A-9   | Canonical Output Topology            | `.md` for docs (human-readable). Machine formats when applicable.    | ✅      |
| A-10  | Versioning Suffix Convention         | All filenames use `-vX.Y.Z.ext` pattern.                             | ✅      |
| A-11  | Git-Assistant                        | §6 provides full staging, commit, tag guidance.                      | ✅      |
| A-12  | Orchestrator-Routing Toggle          | §5.4 delivery mode. §6.2 Git interaction. §7 conditional matrix.    | ✅      |

**Compliance score: 13/13 (A-0 through A-12).**

## MANDATORY CHANGELOG

| Version | Date       | State   | Description                                                                                             |
|---------|------------|---------|---------------------------------------------------------------------------------------------------------|
| `v1.0.0` | 2026-04-17 | `draft` | Initial spec. 8-question flow, $\mathcal{C}(u)$ topology, 5 approved fixes (legacy, spectrum, topology, E-DVCS, Git guidance). 12/12 compliance. |
| `v1.1.0` | 2026-04-17 | `draft` | Integrated A-12 (Orchestrator-Routing Toggle): §5.4 delivery mode, §6.2 Git interaction, §7 conditional execution matrix, §8 compliance row. Governing axioms updated to v1.5.0. 13/13 compliance. |


