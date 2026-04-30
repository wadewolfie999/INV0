<!-- E-DVCS:
  file: state/dependency-ledger.md
  version: 1.0.0
  layer: state-traceability
  governed-by: core/axioms-v1.6.0.md
  status: active
-->

# INV0 Dependency Ledger — Traceability Layer (v1.0.0)

---

## §1 Purpose

This ledger is the **canonical registry of all external and non-local dependencies** used across the INV0 system.

It enables:

- deterministic replay (A-17)
- traceability enforcement (A-20)
- security boundary auditing (A-19)

---

## §2 Ledger Schema

Each dependency entry MUST conform to the following structure:

```yaml id="ldg-schema-01"
- id: DEP-XXX
  source: <url | tool | system>
  version: <semantic_version | hash | snapshot_id>
  timestamp: <iso8601>
  artifact: <description_of_what_was_used>
  hash: <optional_content_hash>
  mode: strict-local | hybrid | external-enabled
  trust_level: local | verified | unverified
```

---

## §3 Invariants (A-20 Enforcement)

### §3.1 Mandatory Registration

All external dependencies MUST be recorded before or immediately after use.

---

### §3.2 Immutability Rule

Once recorded, dependency entries:

* MUST NOT be modified
* MUST NOT be deleted
* MAY be appended with corrective entries

---

### §3.3 Mode Binding

Each dependency MUST declare execution context:

| Mode             | Requirement                                  |
| ---------------- | -------------------------------------------- |
| strict-local     | MUST NOT contain external dependency entries |
| hybrid           | MUST log all external interactions           |
| external-enabled | MUST log all interactions with trust level   |

---

### §3.4 Traceability Requirement

Each DEP entry MUST be:

* uniquely identifiable
* globally referencable across checkpoints
* reproducible in audit context

---

## §4 Example Entries

```yaml id="ldg-example-01"
- id: DEP-001
  source: https://api.example.com/data
  version: v3.2.1
  timestamp: 2026-04-30T10:15:00Z
  artifact: fetched dataset for model calibration
  hash: 9f2c1a7b...
  mode: hybrid
  trust_level: verified
```

```yaml id="ldg-example-02"
- id: DEP-002
  source: local-cache
  version: commit:ab12cd34
  timestamp: 2026-04-30T10:17:00Z
  artifact: cached inference snapshot
  mode: strict-local
  trust_level: local
```

---

## §5 System Integration Points

This ledger integrates with:

* §A-17 External Determinism Control → replay uses DEP version pinning
* §A-18 Identity Instantiation → dependency tied to session context
* §A-19 Security Boundary → trust_level governs risk classification
* Checkpoints (Phase 1.3) → snapshot references DEP list

---

## §6 Deterministic Replay Contract

To replay any execution:

1. Resolve all DEP entries
2. Reconstruct versions or snapshots
3. Simulate missing external responses if needed
4. Bind to checkpoint state

---

## §7 Validity Condition

This ledger is valid only if:

* all external interactions are recorded
* all DEP IDs are unique and immutable
* all entries include mode + trust level

---

## §8 Status

ACTIVE — Required for Phase 1 execution flow
