# ADR-001: File Persistence Strategy

- **Status:** Accepted
- **Date:** 2025-12-31
- **Feature:** Storage & Persistence
- **Context:** Initially, the Constitution (v1.0.0) mandated "In-memory data ONLY" to enforce a minimal, controllable Phase-1 scope. However, aligning with hackathon reference requirements (which evaluate persistence and data management) and ensuring work is not lost between CLI invocations requires a persistent layer.

## Decision

We will implement file-based persistence using a flat JSON file (`tasks.json`).

- **Format**: JSON (human-readable, standard library support).
- **Location**: Project root or configurable via environment variable.
- **Strategy**:
  - Load all tasks into memory on CLI startup.
  - Save all tasks back to `tasks.json` atomically after any write operation (Add, Update, Delete, Complete).

## Consequences

### Positive

- **Survival**: Data persists across CLI sessions, matching user expectations for a todo app.
- **Interoperability**: JSON is easily readable by other tools and agents.
- **Simplicity**: No external database engines required; standard library `json` module is sufficient.
- **Alignment**: Matches hackathon Phase 1 reference architecture.

### Negative

- **Performance**: O(n) read/write of the entire file on every operation (acceptable for human-scale todo lists < 10,000 items).
- **Concurrency**: Possible race conditions if multiple CLI instances write simultaneously (out of scope for Phase-1 single-user requirement).
- **Corruption**: Risks file corruption if the process is killed during a write (can be mitigated by atomic write/replace patterns).

## Alternatives Considered

- **Strict In-Memory**: Rejected as it fails the "practicality" and "alignment" tests for a production-grade hackathon submission.
- **SQLite**: Rejected for Phase-1 to avoid even lightweight external dependencies and keep the data model transparently editable by humans/agents.

## References

- Constitution: v1.1.0 update (allowing `tasks.json`)
- Plan: [plan.md](../specs/001-add-task/plan.md)
