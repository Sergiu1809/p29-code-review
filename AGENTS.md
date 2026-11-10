# AGENTS.md — p29-code-review

<!-- graffino-agentic:begin v1 -->
## How we work here

**Before any work:** `git fetch --all --prune`, then `git pull --ff-only`. Stop on a
non-fast-forward or on uncommitted changes you did not make.

**Always load** (indexes; open the entry, or its topic file, before you rely on it):
`docs/agents/DECISIONS.md`, `docs/agents/PATTERNS.md`,
`docs/agents/CONTRACTS.md`, `docs/agents/OPEN-QUESTIONS.md`, `CONTEXT.md`.

**Load on demand:**

| When | Load |
|---|---|
| You rely on an entry | the entry, or its topic file under `docs/agents/<kind>/` |
| Structural work | `docs/agents/ARCHITECTURE.md` |
| Old code or a past decision needs explaining | `docs/agents/DECISIONS-SUPERSEDED.md`, `PATTERNS-SUPERSEDED.md` (never obeyed) |
| UI work | `docs/design/DESIGN.md`, `docs/design/registry.yaml` |
| Any feature work, a scope or acceptance question | `P29.md` (the project brief; sections 1–6 are fixed requirements) |

**Flow:** a change to more than a few lines, or one with a design choice, starts with
`/plan`. The approved plan runs with `/build`. Small fixes go straight to build, with
tests first where tests exist.

### The gate
Ask yourself: **does this change something already approved?**
- **Do, then report:** add a `candidate` pattern; add or answer an open question
  (only with an answer the user gave); write a `Proposed answer` the evidence
  supports (the question stays `investigating` until the user confirms it); fix a
  typo, link or moved path; code that follows the approved entries.
- **Propose and wait:** change, supersede or delete an `approved` pattern or
  decision; promote `candidate → approved`; add a decision; code that contradicts an
  entry. Use this shape, then stop:

```text
PROPOSAL: <add-decision | change | supersede | promote | delete>
- Existing: <ID and what it says, or "none">
- Proposed: <the new rule>
- Why now: <what changed>
- Impact: <files that follow the old rule>
- If approved: <old ID> → superseded-by <new ID> (kept, not deleted)
```
Before you propose, check `docs/agents/REJECTED.md`: never re-propose a rejected item
without new evidence. A rejected proposal is added there with the reason.

### Hard rules
- Build only from `approved` entries. Unanswered means out of scope: record a Q-,
  never invent a value, a requirement or a behaviour.
- Add nothing nobody asked for. Note it as a suggestion instead.
- Build the smallest change that meets the approved criteria, reusing existing code.
  A new abstraction, dependency, configuration option, extension point or broad
  refactor needs a concrete reason today. Never at the cost of tests or error handling.
- Tests first where the repo has tests. Never change what an existing test asserts
  to make code pass; an assertion you think is wrong goes to the user.
- Never write a secret, token, password or personal data into a file, commit or log.
- Never push, tag, release, or deploy without the user's go for that action.
- When you cite past work, label the intent: **replicate** (only for an `approved`
  pattern) or **for awareness only**. History is not a template.
- The code wins over any document. When they disagree, say so and fix the document.
- Report honestly: a failed check is reported with its output; a skipped step is
  named with its reason.

### Ledger rules
- IDs are one sequence per kind in this repo: `D-`, `PATTERN-`, `C-`, `Q-`. Never renumber.
- A provided contract (C-) lives here only; consumers link to it. Changing one is a
  PROPOSAL, and the plan names the consumer files too.
- Superseded entries stay (`status: superseded-by <ID>`) so old code stays explainable.
  Their index lines live in `DECISIONS-SUPERSEDED.md` / `PATTERNS-SUPERSEDED.md`, not
  in the always-loaded indexes; the lint (`--fix`) moves them.
- After any ledger change: `python3 docs/agents/tools/ledger-lint.py --fix` (next free
  ID: `--next D`). It must pass.
- **Confirmed:** when the user confirms an entry in a plan, set `- **Confirmed:** <date>`
  on it. Any edit to an entry removes its Confirmed line.
- A new reusable practice becomes a `candidate` pattern in the same session.
- A settled constraint becomes a decision PROPOSAL in the same session.
<!-- graffino-agentic:end -->

## 1. What this repo is
P29, an individual student project (Tehnologii Web II, Round 1). It is an automated
code review platform. It connects to real GitHub repos via OAuth and webhooks. On
every push or PR, it analyses the code in an isolated sandbox. It keeps a history,
comments on PRs, serves SVG badges and builds a public portfolio page per developer.
Professors get a class view with risk signals. Where it runs live: Q-005.

## 2. Stack and commands
Not chosen yet: backend Q-001, database Q-002, job queue Q-003, frontend Q-004.
Every server runs in Docker Compose (D-001).

```bash
# No code yet. Add the exact commands here once the stack is chosen:
# install · build · run (docker compose …) · test · lint/type-check
# screenshot: Q-012
```

## 3. Layout
- `P29.md` — the project brief (Romanian). Source of all requirements.
- `docs/agents/` — the ledger: decisions, patterns, contracts, open questions, architecture.
- `docs/design/` — design guardrails, registry, mocks and screenshots.
- `.claude/` — the `/plan` and `/build` skills and the planner/builder agents.

## 4. Rules for this repo
- `P29.md` sections 1–6 are fixed catalog requirements. Never renegotiate or reinterpret them.
- Only `P29.md` section 7 (the student's decisions) can become approved D- entries.
- Anything the brief does not state becomes a Q- entry. Never pick a stack item for the student.
- `P29.md` section 10 tasks belong to the student. Never write repo lists, interview
  notes or feedback into `REPOS.md` or `INTERVIEW.md`.
- Non-negotiable technical requirements (`P29.md` §4), check every plan against them:
  - the web server never runs code from an analysed repo;
  - webhooks: HMAC signature verified; the same delivery id twice = one analysis;
  - queue: limited concurrency, stale jobs cancelled, retry on infrastructure errors only;
  - found secrets are stored without the value (type, file, line, partial hash only).
- Write project docs in English. `P29.md` stays as the student wrote it.

## 5. Release
No remote, no tags, no release flow yet. Branch from `main`. Deploy target: Q-005.
Never push, tag or deploy without the student's go.

## 6. Definition of done
- The test command passes (not defined yet: depends on Q-001).
- The build / type-check command passes (not defined yet).
- The stack starts with Docker Compose (D-001).
- UI changes: screenshots of every changed screen, light and dark, compared with
  `docs/design/DESIGN.md` (screenshot command: Q-012).
- New practices recorded as candidate patterns; open points recorded as Q- entries.
- Project-level done: `P29.md` section 5.
