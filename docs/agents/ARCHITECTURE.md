# Architecture — p29-code-review

<!-- graffino-agentic:begin v1 -->
> How this repo is built, generated from the code at backfill and kept current by
> whoever changes the structure. The code wins: when this page is wrong, fix it.
<!-- graffino-agentic:end -->

## Overview
No code yet. This page states only the shape the brief requires (`P29.md` §3–4).
Replace it with the real structure as parts are built.

```text
GitHub ──delivery──▶ web server ──job──▶ queue ──▶ worker ──▶ sandbox (repo code runs here only)
  ▲                      │                                        │
  └──── PR comment ──────┤◀──────────── results ──────────────────┘
                         ├─▶ database (history, trends, findings)
                         └─▶ badges · portfolio pages · professor view
```

## Parts
| Part | Path | Responsibility | Talks to |
|---|---|---|---|
| — | — | not built yet | — |

## Data flow
Analysis of a push (required by `P29.md` §3–4):
1. GitHub sends a delivery to the web server.
2. The server verifies the HMAC signature and drops a repeated delivery id.
3. The server enqueues a job and cancels stale jobs for the same repo/branch.
4. A worker clones the commit into a sandbox and runs the configured analysers.
5. Results go to the database; secret findings without their value.
6. If enabled for the repo, a PR comment is posted; badges and pages reflect the new results.

## State and storage
| What | Where | Owner | Notes |
|---|---|---|---|
| Analyses, history, findings | database (Q-002) | — | secret values never stored |

## Configuration
| Name | Where set | Used by | Notes |
|---|---|---|---|
<!-- names only, never values -->

## Build, deploy, runtime
Every server runs in Docker Compose (D-001). Commands: AGENTS.md section 2. Live
deploy target: Q-005.

## Boundaries
- Trust boundary: code from a connected repo is hostile. It runs only in the
  sandbox (Q-007), never in the web server (`P29.md` §4).
- Webhook boundary: unsigned or badly signed deliveries are rejected (`P29.md` §4).
- External contracts: `CONTRACTS.md`.
