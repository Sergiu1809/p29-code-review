# Decisions — p29-code-review

<!-- graffino-agentic:begin v1 -->
> Constraints the code must obey. Status: `approved` (obey) · `proposed` (do not
> build on it) · `superseded-by <ID>` (kept to explain old code).
> Adding or changing an entry needs the user's OK (AGENTS.md → The gate).
<!-- graffino-agentic:end -->

## Index
- D-001 · Every server runs in Docker (Docker Compose)

---

## D-001 · Every server runs in Docker (Docker Compose)
- **Status:** approved
- **Date:** 2026-11-10
- **Rule:** Every server process (web, workers, database, queue) runs as a Docker Compose service. No server runs directly on the host.
- **Why:** A requirement of the lab (the student's decision in the brief).
- **Rejected:** none recorded.
- **Evidence:** P29.md:79
- **Source:** docs · confidence high
- **Owner note:** The analysis sandbox mechanism is still open (Q-007); this rule covers the servers, not the sandbox.
