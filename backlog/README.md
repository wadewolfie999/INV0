# Backlog Directory

This directory holds deferred work, archived projects, and serialized state
for initiatives that are not currently active.

## Structure

- `backlog-registry-v1.4.0.md` — The canonical registry. All deferred projects are logged here with last-known state, priority, and blocking dependencies.
- `archived/` — (Future) Retired project artifacts, legacy files, deprecated templates.
- `ideas/` — (Future) Raw, unstructured notes and brainstorming threads.

## Governance

- Adding a new backlog item requires a row in `backlog-registry-v1.4.0.md` with:
  - Unique ID (`BL-XXX`)
  - Project name
  - Domain
  - Last state
  - Priority (High/Medium/Low)
  - Blocking dependencies
  - Owner 
- Retiring a project moves it from "Active Backlog" to "Retired / Archived" with a reason and date.
- Backlog items do NOT get their own directories until they are promoted to `projects/`.

## MANDATORY CHANGELOG

| Version   | Date       | State     | Description                                                                 |
|-----------|------------|-----------|-----------------------------------------------------------------------------|
| `v1.0.0`  | 2026-04-16 | `release` | Initial backlog directory structure. Registry and governance rules defined. |

