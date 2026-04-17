> **E-DVCS** | `wizard-spec` | `v1.0.0` | `2026-04-17` | `draft` | `onboarding/wizard-spec-v1.0.0.md`

# Onboarding Wizard Specification

## 1. Authority & Scope

This specification defines the **Onboarding Wizard** — the sole canonical
authority for $\mathcal{C}(u)$ topology within the WERTHA ecosystem.

**Legal basis:** A-5 (`core/axioms-v1.4.0.md`)

> "$\mathcal{C}(u)$ (covariant): User-scoped directories whose canonical
> topology is defined exclusively by the Onboarding Wizard. The wizard
> is the sole authority for $\mathcal{C}(u)$ structure; no other process
> or artifact may define or override this topology without Director
> authorization."

**Scope:**

- Identifies and profiles the onboarding user.
- Detects interaction mode (A-4).
- Detects legacy state requiring migration (A-3).
- Computes and generates $\mathcal{C}(u)$ directory topology.
- Emits all artifacts with E-DVCS version blocks (A-7).
- Provides Git staging, commit, and tag guidance (A-11).

**Executor:** The AI Partner (single-agent, A-2) executes this protocol
on behalf of the Director(s) defined in `core/identity-v1.0.0.md`.

## 2. Preconditions

| #   | Condition                              | Verification                          |
|-----|----------------------------------------|---------------------------------------|
| P-1 | $\mathcal{I}$ layer initialized       | `core/axioms-v1.4.0.md` exists       |
| P-2 | Identity document present              | `core/identity-v1.0.0.md` exists     |
| P-3 | This spec is reachable                 | `onboarding/wizard-spec-v1.0.0.md` exists |
| P-4 | Git operational                        | `git status` returns clean or tracked |

If any precondition fails, halt and alert Director (Decision Heuristic).

## 3. Interaction Flow

The wizard consists of **three phases** and a maximum of **8 questions**.
Phase C is conditional. Questions Q1–Q3 are delivered in neutral tone;
the selected mode (Q3) governs tone and density for Q4–Q8 and all outputs.

### 3.1 Phase A — User Identification & Mode Selection

| Q#  | Prompt                                                                  | Variable         | Required |
|-----|-------------------------------------------------------------------------|------------------|----------|
| Q1  | What is your name?                                                      | `<username>`     | Yes      |
| Q2  | What is your role? (Director / Co-Director)                             | `<role>`         | Yes      |
| Q3  | Interaction mode? (Expert: terse, minimal / Guided: explanatory, paced) | `<mode>`         | Yes      |

**Validation:** `<username>` + `<role>` must match an entry in
`core/identity-v1.0.0.md`. If no match, halt and alert Director.
New users require an identity document update (A-0) before onboarding.

**Mode effect (A-4, A-8):**

- **Expert:** Subsequent prompts are terse. Outputs are raw.
  No inline explanations. Token expenditure minimized.
- **Guided:** Subsequent prompts include context and rationale.
  Outputs include inline annotations. Pacing is gentle.

### 3.2 Phase B — Project Scoping

| Q#  | Prompt                                  | Variable          | Required |
|-----|-----------------------------------------|-------------------|----------|
| Q4  | Primary project or initiative name?     | `<project>`       | Yes      |
| Q5  | One-line project description?           | `<description>`   | Yes      |
| Q6  | Immediate priority or goal?             | `<goal>`          | Yes      |

### 3.3 Phase C — Legacy Detection (Conditional)

| Q#  | Prompt                                                                       | Variable         | Required   |
|-----|------------------------------------------------------------------------------|------------------|------------|
| Q7  | Do you have existing files, archives, or prior work to ingest? (Y/N)        | `<has_legacy>`   | Yes        |
| Q8  | What file formats/types are present? (e.g., `.md`, `.pdf`, `.py`, mixed)    | `<legacy_types>` | If Q7 = Y  |

**Trigger:** Q7 is always asked. Q8 fires only if Q7 = Y.

## 4. Topology Generation Schema

The wizard computes $\mathcal{C}(u)$ topology from the collected answers.
This section is the **canonical definition** of that computation.

### 4.1 Base Topology (Always Generated)

| Directory                  | Derived From    | Purpose                                |
|----------------------------|-----------------|----------------------------------------|
| `profiles/<username>/`     | Q1              | User profile, preferences, per-user state |
| `projects/<project>/`      | Q4              | Primary project workspace              |
| `state/checkpoints/`       | Implicit (A-3)  | Git-backed session/state persistence   |

### 4.2 Conditional Topology

| Directory       | Condition | Purpose                              |
|-----------------|-----------|--------------------------------------|
| `migration/`    | Q7 = Y    | Legacy file ingestion staging area   |

### 4.3 Extensibility

Additional directories may be added in future wizard spec versions
(e.g., multi-project support, shared workspaces). Any topology change
requires a new version of this spec and Director authorization (A-0, A-5).

### 4.4 Topology Manifest

After computation, the wizard emits a **topology manifest** that records
the exact $\mathcal{C}(u)$ generated for this user. This manifest is the
canonical reference for all downstream processes.

**Output:** `profiles/<username>/topology-manifest-v1.0.0.md`

## 5. Output Artifacts

### 5.1 Artifact Registry

| #   | Artifact            | Path                                                        | Condition |
|-----|---------------------|-------------------------------------------------------------|-----------|
| O-1 | User profile        | `profiles/<username>/<username>-profile-v1.0.0.md`          | Always    |
| O-2 | Project README      | `projects/<project>/README-v1.0.0.md`                       | Always    |
| O-3 | Topology manifest   | `profiles/<username>/topology-manifest-v1.0.0.md`           | Always    |
| O-4 | Migration manifest  | `migration/migration-manifest-v1.0.0.md`                    | Q7 = Y    |

All artifacts comply with A-10 (versioning suffix convention).

### 5.2 E-DVCS Block Format (A-7)

Every generated artifact must begin with the following block:

```
> **E-DVCS** | `<artifact-id>` | `v<X.Y.Z>` | `<YYYY-MM-DD>` | `<state>` | `<path>`

**Fields:**

- `artifact-id`: Canonical name (e.g., `user-profile`, `topology-manifest`)
- `version`: Semantic version per A-10
- `date`: Generation date (Gregorian, per A-6)
- `state`: `draft` for initial generation
- `path`: Repository-relative file path
```

### 5.3 Artifact Content Specifications

#### O-1: User Profile


> **E-DVCS** | `user-profile` | `v1.0.0` | `<date>` | `draft` | `profiles/<username>/<username>-profile-v1.0.0.md`

# User Profile: <username>

## Identity
- **Name:** <Q1>
- **Role:** <Q2>
- **Mode:** <Q3>

## Primary Project
- **Name:** <Q4>
- **Description:** <Q5>
- **Goal:** <Q6>

## Legacy State
- **Has Legacy Files:** <Q7>
- **Legacy Types:** <Q8 or N/A>

## MANDATORY CHANGELOG
| Version | Date   | State   | Description                                    |
|---------|--------|---------|------------------------------------------------|
| `v1.0.0` | <date> | `draft` | Generated by Onboarding Wizard v1.0.0.        |

#### O-2: Project README


> **E-DVCS** | `project-readme` | `v1.0.0` | `<date>` | `draft` | `projects/<project>/README-v1.0.0.md`

# <project>

<Q5>

## Goal
<Q6>

## MANDATORY CHANGELOG
| Version | Date   | State   | Description                                    |
|---------|--------|---------|------------------------------------------------|
| `v1.0.0` | <date> | `draft` | Generated by Onboarding Wizard v1.0.0.        |

#### O-3: Topology Manifest


> **E-DVCS** | `topology-manifest` | `v1.0.0` | `<date>` | `draft` | `profiles/<username>/topology-manifest-v1.0.0.md`

# Topology Manifest — <username>

Generated by: `onboarding/wizard-spec-v1.0.0.md`
User: <username>
Date: <date>

## Covariant Layer $\mathcal{C}(u)$

| Directory                  | Purpose                            | Status  |
|----------------------------|------------------------------------|---------|
| `profiles/<username>/`     | User profile & topology manifest   | Created |
| `projects/<project>/`      | Primary project workspace          | Created |
| `state/checkpoints/`       | State persistence (A-3)            | Created |
| `migration/`               | Legacy ingestion staging           | Created / Skipped |

## MANDATORY CHANGELOG
| Version | Date   | State   | Description                                    |
|---------|--------|---------|------------------------------------------------|
| `v1.0.0` | <date> | `draft` | Initial topology generated by Onboarding Wizard v1.0.0. |

#### O-4: Migration Manifest (Conditional — Q7 = Y only)


> **E-DVCS** | `migration-manifest` | `v1.0.0` | `<date>` | `draft` | `migration/migration-manifest-v1.0.0.md`

# Migration Manifest

## Source
- **User:** <username>
- **Legacy Types:** <Q8>

## Migration Plan

| #  | Source File/Pattern | Target Path | Action                       | Status    |
|----|---------------------|-------------|------------------------------|-----------|
| 1  | *(populated during migration execution)* | | `copy` / `convert` / `archive` | `pending` |

## Instructions

1. Place legacy files in `migration/inbound/`.
2. AI Partner catalogs and maps files to $\mathcal{C}(u)$ topology.
3. Director reviews and approves mapping.
4. Files are moved to their canonical locations.
5. `migration/inbound/` is cleared post-migration.

## MANDATORY CHANGELOG
| Version | Date   | State   | Description                                    |
|---------|--------|---------|------------------------------------------------|
| `v1.0.0` | <date> | `draft` | Generated by Onboarding Wizard v1.0.0. Migration pending. |

## 6. Legacy Migration Protocol

**Trigger:** Q7 = Y

**Sequence:**

1. **Catalog.** AI Partner asks user to describe or list legacy files.
   In Guided mode, the AI Partner walks through file-by-file.
   In Expert mode, the AI Partner accepts a batch listing.

2. **Map.** Each legacy file is assigned a canonical location within
   $\mathcal{C}(u)$ based on the topology manifest (O-3).

3. **Stage.** Files are placed in `migration/inbound/` as a holding area.

4. **Review.** Director reviews the mapping in O-4 (`migration-manifest`).

5. **Execute.** Upon approval, files are moved to canonical paths.
   AI Partner provides Git commands for each move (A-11).

6. **Clean.** `migration/inbound/` is emptied. Migration manifest status
   updated to `complete`.

**Format Agnosticism:** The protocol handles any file type declared in Q8.
No format is rejected; all are mapped to appropriate locations within
$\mathcal{C}(u)$.

## 7. Post-Generation Git Protocol (A-11)

After all artifacts are generated, the AI Partner emits a complete
Git command sequence. In Guided mode, each command is preceded by a
one-line explanation. In Expert mode, commands only.

bash
# 1. Create directory structure
mkdir -p profiles/<username>
mkdir -p projects/<project>
mkdir -p state/checkpoints
# mkdir -p migration/inbound    ← only if Q7=Y

# 2. Place .gitkeep in initially empty directories
touch state/checkpoints/.gitkeep
# touch migration/inbound/.gitkeep    ← only if Q7=Y

# 3. Save each artifact to its canonical path
#    (user writes content to the paths listed in §5.1)

# 4. Stage all generated artifacts
git add profiles/<username>/<username>-profile-v1.0.0.md
git add profiles/<username>/topology-manifest-v1.0.0.md
git add projects/<project>/README-v1.0.0.md
git add state/checkpoints/.gitkeep
# git add migration/migration-manifest-v1.0.0.md    ← only if Q7=Y
# git add migration/inbound/.gitkeep                 ← only if Q7=Y

# 5. Commit
git commit -m "onboarding: <username> | C(u) topology generated by wizard-spec-v1.0.0"

# 6. Tag
git tag onboarding-<username>-v1.0.0

## 8. Axiom Compliance Matrix

| Axiom | Requirement                      | Satisfied By                                        |
|-------|----------------------------------|-----------------------------------------------------|
| A-0   | Director authority               | Q2 validation against identity; Director approval gates |
| A-1   | INTRANET / air-gapped            | No external dependencies in any artifact             |
| A-2   | Single agent                     | One AI Partner executes entire wizard                |
| A-3   | Git-backed persistence           | All outputs are files; Git protocol in §7            |
| A-4   | Dynamic design (spectrum)        | Mode detection at Q3; adaptive flow throughout       |
| A-5   | $\mathcal{C}(u)$ topology authority | §4 — this spec IS the authority                   |
| A-6   | Mandatory changelog              | All artifacts include changelog section              |
| A-7   | E-DVCS version blocks            | All artifacts begin with E-DVCS block (§5.2)        |
| A-8   | Contextual economy               | Expert mode minimizes tokens; no redundant output    |
| A-9   | Canonical output topology        | All outputs are `.md` (human-readable)               |
| A-10  | Versioning suffix                | All artifacts use `-vX.Y.Z.md` convention            |
| A-11  | Git-Assistant                    | §7 — full Git guidance post-generation               |

**Compliance score: 12/12**

## MANDATORY CHANGELOG

| Version   | Date       | State   | Description                                                                                                                                                                  |
|-----------|------------|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `v1.0.0`  | 2026-04-17 | `draft` | Initial wizard specification. Implements 5 CEO-approved fixes: legacy detection (A-3/A-11), spectrum-adaptive flow (A-4/A-8), covariant topology definition (A-5), E-DVCS version blocks (A-7), post-generation Git guidance (A-11). Full 12/12 axiom compliance. |


