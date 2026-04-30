# 📄 Execution Context Injection Specification (v1.0.0)

---

## §1 Purpose

This specification enforces **per-operation execution metadata binding**, ensuring that every runtime action is:

* explicitly typed by execution mode
* traceably linked to dependencies
* compatible with deterministic replay (A-17)
* bound to security constraints (A-19)

---

## §2 Required Execution Context Schema

Every operation MUST declare the following structure:

```yaml id="ctx-001"
execution:
  mode: strict-local | hybrid | external-enabled
  dependencies: [DEP-XXX]
```

---

## §3 Axiom Binding

### §3.1 A-0 (Dual-Mode Connectivity)

* `mode` is **mandatory**
* must match system-wide mode semantics exactly

---

### §3.2 A-17 (External Determinism Control)

* all external inputs MUST appear in `dependencies`
* missing dependencies invalidate execution trace

---

### §3.3 A-18 (Identity Instantiation)

Execution context is implicitly bound to:

```yaml id="ctx-identity"
identity:
  director: <human_operator>
  session_id: <uuid>
  timestamp: <iso8601>
```

(Injected at runtime, not redefined here, but required for completeness of execution state)

---

### §3.4 A-19 (Security Boundary Definition)

Each execution context inherits trust constraints via mode:

| Mode             | Trust Behavior           |
| ---------------- | ------------------------ |
| strict-local     | local only               |
| hybrid           | verified preferred       |
| external-enabled | fully allowed but logged |

---

## §4 Execution Rules

### §4.1 Mandatory Inclusion Rule

Every operation MUST include:

* execution.mode
* execution.dependencies

Failure to include either = **invalid execution unit**

---

### §4.2 Dependency Binding Rule

* All `DEP-XXX` references MUST exist in:

  ```
  state/dependency-ledger.md
  ```

---

### §4.3 Determinism Constraint

* strict-local → fully reproducible
* hybrid → reproducible via ledger replay
* external-enabled → best-effort reproducibility

---

### §4.4 No Orphan Execution Rule

No operation may execute without:

* declared mode
* declared dependency set (even if empty: `[]` explicitly required)

---

## §5 Example Usage

### Strict-local execution

```yaml id="ctx-ex-1"
execution:
  mode: strict-local
  dependencies: []
```

---

### Hybrid execution

```yaml id="ctx-ex-2"
execution:
  mode: hybrid
  dependencies: [DEP-001, DEP-002]
```

---

### External-enabled execution

```yaml id="ctx-ex-3"
execution:
  mode: external-enabled
  dependencies: [DEP-010]
```

---

## §6 System Effect

This layer enforces:

* full traceability of runtime behavior
* deterministic reconstruction of execution paths
* strict coupling between computation and provenance
* elimination of implicit execution state

---

## §7 Relationship to Step 1.1

This specification is **directly dependent on:**

* `state/dependency-ledger.md`

Without Step 1.1, this layer is non-operational.

---

## §8 Validity Condition

This specification is valid only if:

* dependency ledger exists and is immutable
* execution mode system (Step 0.2) is active
* all operations enforce schema inclusion

---

## §9 Status

ACTIVE — required for Phase 1 checkpoint system construction

