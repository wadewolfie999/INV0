# INV0 Axioms — Unified Governance Constraint Matrix (v1.6.0)

<!-- E-DVCS: file: core/axioms-v1.6.0.md | version: 1.6.0 | layer: invariant | governed-by: self | supersedes: core/axioms-v1.5.0.md | status: draft -->

These are non-negotiable invariants governing the INV0 ecosystem.  
All lower-layer artifacts (identity, backlog, onboarding, execution state) MUST conform to this specification.

---

## §0 Preamble

This document defines the **system-wide invariants** governing all operations.  
All execution, state transitions, and artifacts MUST conform to these axioms without exception.

---

# §A-0 Dual-Mode Connectivity (REVISED)

The system operates under explicitly declared execution modes controlling external interaction.

### Mode Specification

```yaml
mode: strict-local | hybrid | external-enabled
````

| Mode             | Definition                                      |
| ---------------- | ----------------------------------------------- |
| strict-local     | No external interaction permitted               |
| hybrid           | External interaction allowed but fully logged   |
| external-enabled | External interaction unrestricted but monitored |

### Constraints

* Every operation MUST declare its mode
* Mode MUST be recorded in:

  * checkpoints
  * execution context
* strict-local mode MUST guarantee deterministic execution

---

## §A-1 Governance First

All system behavior MUST be derivable from governed artifacts.

(No change)

---

## §A-2 Documentation as Interface

(No change)

---

## §A-3 Git-Backed Persistence

All system state MUST be reconstructible from version-controlled artifacts.

### Extensions

* External dependencies MUST be captured via dependency ledger (§A-20)
* Checkpoints MUST include:

  * execution mode
  * dependency snapshot

---

## §A-4 Deterministic Execution (CONDITIONALLY EXTENDED)

Determinism is required in strict-local mode and approximated in other modes.

### Constraints

* strict-local → strict determinism
* hybrid / external-enabled → bounded determinism via replay mechanisms

---

## §A-5 Invariant / Covariant Separation

(No change)

---

## §A-6 Mandatory Changelog

(No change)

---

## §A-7 E-DVCS Compliance

All artifacts MUST include machine-parseable metadata headers.

### Extensions

Headers MUST include:

* execution mode (if applicable)
* dependency references (if applicable)

---

## §A-8 Layered Architecture

(No change)

---

## §A-9 Minimal Surface Area

(No change)

---

## §A-10 Explicitness Over Implicitness

(No change)

---

## §A-11 Git Discipline

All changes MUST be atomic, traceable, and reversible.

### Extensions

* External dependency commits MUST reference dependency IDs
* Mode changes MUST be explicitly committed

---

## §A-12 CLI-First Interface

(No change)

---

## §A-13 Validation Enforcement (NEW)

All invariant-layer artifacts MUST pass deterministic validation prior to commit.

### Requirements

Validation MUST verify:

* schema compliance
* E-DVCS headers
* mode declaration
* dependency linkage

---

## §A-14 Checkpoint Integrity (NEW)

All critical state transitions MUST produce a restorable checkpoint.

### Requirements

Checkpoints MUST include:

* execution mode
* dependency snapshot
* identity snapshot (§A-18)
* git reference

---

## §A-15 Lifecycle Formalization (NEW)

All tracked entities MUST define explicit state transitions.

### Applies To

* backlog items
* onboarding flows
* execution states

---

## §A-16 Connectivity Governance (NEW)

External interactions MUST be controlled, declared, and reproducible.

### Requirements

All external calls MUST:

* declare source
* be logged in dependency ledger
* include trust level (§A-19)

---

## §A-17 External Determinism Control (NEW)

External interactions MUST be replayable or bounded.

### Mechanisms

* dependency version pinning
* response snapshotting (if applicable)
* fallback or simulation strategy

---

## §A-18 Identity Instantiation (NEW)

A Director MUST be explicitly instantiated for every execution context.

### Requirements

Each session MUST declare:

* director (human operator)
* session_id
* timestamp

Director definition: the active human operator in the current runtime context.

---

## §A-19 Security Boundary Definition (NEW)

All external interactions MUST declare and respect trust boundaries.

### Trust Levels

```yaml
trust_level: local | verified | unverified
```

### Constraints

* strict-local → only local
* hybrid → verified preferred
* external-enabled → all allowed but logged

---

## §A-20 Dependency Traceability (NEW)

All non-local dependencies MUST be logged and referenceable.

### Requirements

Each dependency MUST include:

* unique ID
* source
* version or hash
* timestamp
* associated mode

---

## §A-21 Replayability Requirement (NEW)

System execution MUST be reproducible within defined bounds.

### Guarantees

* strict-local → exact replay
* hybrid / external-enabled → approximate replay

---

## §Final Clause

Violation of any axiom invalidates the affected artifact.

---

## MANDATORY CHANGELOG

| Version  | Date       | State     | Description                                                                 |   
|----------|------------|-----------|-----------------------------------------------------------------------------|
| `v1.0.0` | 2026-04-16 | `release` | Initial axiom set. A-0 through A-6 defined. Decision heuristic established. |
| `v1.1.0` | 2026-04-16 | `draft`   | Added Governance axioms: A-7 (E-DVCS Enforcement), A-8 (Contextual Economy $W_{ctx}$), A-9 (Canonical Output Topology), A-10 (Versioning Suffix Convention). Decision heuristic updated to span A-0 through A-10. | 
| `v1.2.0` | 2026-04-16 | `draft`   | Refactored A-4 to Dynamic Design (spectrum-based interaction modes). Refactored A-5 to reflect current invariant structure (`core/`, `onboarding/`, `backlog/`); covariant directories deferred to post-onboarding protocol. Removed references to legacy nomenclature and premature onboarding templates. || `v1.3.0` | 2026-04-16 | `draft`   | Added A-11 (Git-Assistant): AI Partner must guide Human Orchestrator through all Git operations. Decision heuristic updated to span A-0 through A-11. |
| `v1.4.0` | 2026-04-17 | `draft`   | A-5 refined: codified Onboarding Wizard (`onboarding/wizard-spec-v1.0.0.md`) as exclusive $\mathcal{C}(u)$ topology authority. |
| `v1.5.0` | 2026-04-17 | `draft`   | Added A-12 (Orchestrator-Routing Toggle): GUI/CLI $r/w/x$ permission model. Default state is Human Routing (GUI). Decision heuristic updated to span A-0 through A-12. |
| `v1.6.0`  | 2026-04-21 | `draft` | Dual-mode architecture added; determinism, identity, security, validation, and replayability layers introduced |

---
