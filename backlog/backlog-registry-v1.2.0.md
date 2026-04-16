# Backlog Registry — WERTHA-seed
> Canonical registry of all deferred work streams, serialized by architectural layer. 
> Single source of truth for quarantined scope outside the active POC.

---

### §1 — Invariant Layer Deferrals
> Items that affect the core system ($\mathcal{I}$) and its scaling mechanisms. 
> *Note: While this section generally tracks deferred items, `BL-I01` has been promoted to an active POC.*

| ID | Project | Current State & Blueprint | Priority | Blocked By |
|----|---------|---------------------------|----------|------------|
| `BL-I01` | Arbitrary **Project** Scaling (`onboarding-wizard`) | **ACTIVE POC.** Blueprint design and full integration currently underway. Acts as the "GPT Builder" equivalent to auto-generate the Covariant Layer ($\mathcal{C}(u)$) based on project context when the user clones the Invariant Core.<br><br>**Design Constraints:**<br>• **Orchestrator Sovereignty:** Human leads; AI asks, never assumes.<br>• **Single-Agent Executor:** Operates as a behavioral mode of the same AI, not a separate service.<br>• **Deterministic Structure:** No ad-hoc structures; outputs must map strictly to the ecosystem topology.<br>• **Git-Native Output:** Canonical formats only; files must slot cleanly into the repo.<br><br>**Acceptance Criteria:** CEO simulated run (clone repo $\rightarrow$ run wizard $\rightarrow$ verify $\mathcal{C}(u)$ setup). | Critical (Active) | None (Previous blocker re-assigned to post-completion testing phase). |

---

### §2 — Covariant Layer Deferrals
> User-specific project implementations that belong inside a $\mathcal{C}(u)$ instance but are not part of current POC scope.

| ID | Project | Owner | Last Known State | Module Health | Priority | Blocked By |
|----|---------|-------|------------------|---------------|----------|------------|
| `BL-C01` | Autonomous Trading Engine (C++/Python) | Vaheed | Post-Phase 17 complete. Snapshot: `SS-20260326-01`. Offline observability validated. Deterministic fault injection validated. Functionally mature but not integrated into WERTHA-seed project structure. | N/A — monolithic | Medium | $\mathcal{C}(\text{V})$ stabilization, project template migration. |
| `BL-C02` | Self-Hosted Web App | Vaheed | Fragmented. No unified deployment. Module-level breakdown below. | Mixed (see below) | Low | $\mathcal{C}(\text{V})$ stabilization, stack decision, module triage. |
| `BL-C03` | Physics Research & Custom Instructions | Mehrsa / Vaheed | Scattered fragmented files (`.md`, `.txt`) across multiple devices. Domains: AdS/CFT, Black Hole Information Paradox, HEP-Phenom ML. Includes highly valuable but unfinished 'Research-Collaborator' persona instructions from `1-BOARDROOM/roster/`, not yet migrated under Identity Collapse. | N/A — pre-structured | Medium | $\mathcal{C}(\text{M})$ onboarding, thesis context ingestion, file consolidation across devices. |

#### BL-C02 Module Health Breakdown
| Module | Score | Notes |
|--------|-------|-------|
| Video-Chat | 6/10 | Functional but unpolished. Requires refactoring for standard deployment. |
| Media-Streaming | 4/10 | Films OK, series indexing broken. Database schema needs rewrite. |
| Telegram Integration | 0/10 | Unbuilt. Purely conceptual at this stage; no code exists. |

---

### §3 — Retired / Archived
> Scope permanently removed from the ecosystem.

| ID | Project | Reason | Date Retired |
|----|---------|--------|--------------|
| `BL-R01` | Legacy Web UI | Replaced by single-agent executor workflow constraint. | 2026-04-14 |
| `BL-R02` | Multi-Agent Orchestrator | Architectural pivot to "Identity Collapse" (Single AI, multiple personas). | 2026-04-15 |

---

### §4 — ID Migration Reference
> Mapping of `v1.0.0` flat IDs to layered semantic IDs (`v1.1.0+`).

| Old ID | New ID | Notes |
|--------|--------|-------|
| `BL-001` | `BL-C01` | State upgraded from "Concept phase" to reflect true post-Phase 17 completion. |
| `BL-002` | `BL-C02` | Split into sub-modules to reflect fragmented health states accurately. |
| `BL-003` | `BL-C03` | Merged with `BL-004` under a unified Covariant project profile. |
| `BL-004` | `BL-C03` | Absorbed into Physics Research; persona instructions are inherently covariant. |
| *(new)*  | `BL-I01` | Arbitrary Project Scaling (`onboarding-wizard`) added as a foundational invariant block. |

---

## MANDATORY CHANGELOG

| Version  | Date       | State      | Description |
|----------|------------|------------|-------------|
| `v1.0.0` | 2026-04-16 | `release`  | Initial backlog registry. Four active projects logged (BL-001 through BL-004). Two retired items archived. |
| `v1.1.0` | 2026-04-16 | `release`  | Structural overhaul per CEO directive. Registry split into Invariant Layer (§1) and Covariant Layer (§2) sections. All placeholder states overwritten with precise last-known technical realities. BL-003 and BL-004 merged into BL-C03. New entry BL-I01 (Arbitrary User Scaling) added. ID migration table (§4) added for traceability. Module health sub-table added for BL-C02. |
| `v1.2.0` | 2026-04-16 | `release`  | Promoted `BL-I01` to an active POC status and removed previous blockers. Renamed `BL-I01` to "Arbitrary **Project** Scaling (`onboarding-wizard`)". Integrated stringent architectural design constraints (Orchestrator Sovereignty, Single-Agent Executor, Deterministic Structure, Git-Native Output) and defined acceptance criteria via CEO simulation run. |
