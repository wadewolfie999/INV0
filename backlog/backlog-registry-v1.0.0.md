# Backlog Registry — WERTHA-seed

> Canonical registry of all deferred work streams, serialized by architectural layer.
> This file is the single source of truth for quarantined scope outside the active POC.

---

## §1 — Invariant Layer Deferrals

Items that affect the core system ($\mathcal{I}$) and its scaling mechanisms.
These are blocked until the hardcoded POC ($\mathcal{C}(\text{V})$, $\mathcal{C}(\text{M})$) is validated.

| ID | Project | Last Known State | Priority | Blocked By |
|----|---------|-----------------|----------|------------|
| `BL-I01` | Arbitrary User Scaling (Conversational Wizard) | Designed but unbuilt. Intended as a dynamic onboarding protocol to auto-generate $\mathcal{C}(u)$ instances — the "GPT Builder" equivalent for WERTHA-seed. Tonight's POC strictly hardcodes two instances; this is deferred to a future context window. | High | Successful validation of hardcoded $\mathcal{C}(\text{V})$ and $\mathcal{C}(\text{M})$ instances. |

---

## §2 — Covariant Layer Deferrals

User-specific project implementations that belong inside a $\mathcal{C}(u)$ instance
but are not part of the current two-instance POC scope.

| ID | Project | Owner | Last Known State | Module Health | Priority | Blocked By |
|----|---------|-------|-----------------|---------------|----------|------------|
| `BL-C01` | Autonomous Trading Engine (C++/Python) | Vaheed | Post-Phase 17 complete. Snapshot: `SS-20260326-01`. Offline observability validated. Deterministic fault injection validated. Engine is functionally mature but not integrated into WERTHA-seed project structure. | N/A — monolithic | Medium | $\mathcal{C}(\text{V})$ stabilization, project template migration. |
| `BL-C02` | Self-Hosted Web App | Vaheed | Fragmented. No unified deployment. Module-level breakdown below. | Mixed (see below) | Low | $\mathcal{C}(\text{V})$ stabilization, stack decision, module triage. |
| `BL-C03` | Physics Research & Custom Instructions | Mehrsa / Vaheed | Scattered fragmented files (.md, .txt) across multiple devices. Domains: AdS/CFT, Black Hole Information Paradox, HEP-Phenom ML. Includes the highly valuable but unfinished "Research-Collaborator" persona instructions (legacy from `1-BOARDROOM/roster/` era, not yet migrated under Identity Collapse). | N/A — pre-structured | Medium | $\mathcal{C}(\text{M})$ onboarding, thesis context ingestion, file consolidation across devices. |

### BL-C02 Module Health Breakdown

| Module | Score | Notes |
|--------|-------|-------|
| Video-Chat | $6/10$ | Functional but unpolished. |
| Media-Streaming | $4/10$ | Films operational. Series playback broken. |
| Telegram Integration | $0/10$ | Unbuilt. No code exists. |

---

## §3 — Retired / Archived

| ID | Project | Reason | Date Retired |
|----|---------|--------|--------------|
| `BL-R01` | Multi-Agent Boardroom Simulation | Replaced by Identity Collapse (A-2). Persona framing retired. | 2026-04-16 |
| `BL-R02` | Manual File Attachment Persistence | Replaced by Git-Backed Persistence (A-3). | 2026-04-16 |

---

## §4 — ID Migration Reference

Old IDs from `v1.0.0` mapped to new layered scheme for traceability.

| Old ID | New ID | Notes |
|--------|--------|-------|
| `BL-001` | `BL-C01` | Trading Engine. State upgraded from "Concept phase" to "Post-Phase 17 complete." |
| `BL-002` | `BL-C02` | Web App. State upgraded from "Concept phase" to fragmented module health scores. |
| `BL-003` | `BL-C03` | Physics Research. Merged with old `BL-004` (Custom Instructions). |
| `BL-004` | `BL-C03` | Absorbed into BL-C03. "Research-Collaborator" persona instructions now tracked there. |
| (new)  | `BL-I01` | Arbitrary User Scaling. New invariant-layer entry. |

---

## MANDATORY CHANGELOG

| Version  | Date       | State      | Description |
|----------|------------|------------|-------------|
| `v1.0.0` | 2026-04-16 | `release`  | Initial backlog registry. Four active projects logged (BL-001 through BL-004). Two retired items archived. |
| `v1.1.0` | 2026-04-16 | `release`  | Structural overhaul per CEO directive. Registry split into Invariant Layer (§1) and Covariant Layer (§2) sections. All placeholder states overwritten with precise last-known technical realities. BL-003 and BL-004 merged into BL-C03. New entry BL-I01 (Arbitrary User Scaling) added. ID migration table (§4) added for traceability. Module health sub-table added for BL-C02. |