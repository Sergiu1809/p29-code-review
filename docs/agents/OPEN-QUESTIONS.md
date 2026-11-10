# Open questions — p29-code-review

<!-- graffino-agentic:begin v1 -->
> Unknowns. Work that depends on an open question is out of scope until it is
> answered. Only the user answers; an agent never answers by guessing. An agent may
> write a `Proposed answer` the evidence supports; the question stays
> `investigating` until the user confirms it.
> Answered entries stay, with the answer and date, and usually become a D- or PATTERN-.
<!-- graffino-agentic:end -->

## Index
- Q-001 · Which backend stack (language, framework, test runner)?
- Q-002 · Which database?
- Q-003 · Which job queue?
- Q-004 · Which frontend?
- Q-005 · Where does the platform run live for the 2 weeks?
- Q-006 · GitHub App or OAuth App?
- Q-007 · Which sandbox mechanism, and with which limits?
- Q-008 · How does the local dev environment receive webhooks?
- Q-009 · Which risk signals does the professor see, in final form?
- Q-010 · Which analysers are on by default per repo, and which are optional?
- Q-011 · Which 5 real repos are connected, with which analysers?
- Q-012 · Design tokens and the screenshot command
- Q-013 · Is docs/agents/DECISIONS.md the DECISIONS.md the brief's Definition of Done names?

---

## Q-001 · Which backend stack (language, framework, test runner)?
- **Status:** open
- **Blocks:** all backend code; the install, run, test and lint commands in AGENTS.md section 2.
- **Who answers:** student
- **Answer:**
- **Recorded as:**

## Q-002 · Which database?
- **Status:** open
- **Blocks:** the data model for analyses, history, trends, users, classes.
- **Who answers:** student
- **Answer:**
- **Recorded as:**

## Q-003 · Which job queue?
- **Status:** open
- **Blocks:** limited concurrency, stale-job cancellation, retries, recovery of jobs left by a dead worker (P29.md:48, :56).
- **Who answers:** student
- **Answer:**
- **Recorded as:**

## Q-004 · Which frontend?
- **Status:** open
- **Blocks:** all UI: portfolio page, history and trend charts, professor view; design tokens (Q-012).
- **Who answers:** student
- **Answer:**
- **Recorded as:**

## Q-005 · Where does the platform run live for the 2 weeks?
- **Status:** open
- **Blocks:** deploy, the public webhook URL, release section of AGENTS.md (P29.md:61, :84).
- **Who answers:** student
- **Answer:**
- **Recorded as:**

## Q-006 · GitHub App or OAuth App?
- **Status:** open
- **Blocks:** login, webhook creation and deletion, PR comment identity (bot or user). Also whether GitLab is supported at all.
- **Who answers:** student, to confirm with the professor
- **Proposed answer:** The brief notes a GitHub App covers login and webhooks and comments on PRs as a bot (P29.md:88). Not confirmed.
- **Answer:**
- **Recorded as:**

## Q-007 · Which sandbox mechanism, and with which limits?
- **Status:** open
- **Blocks:** the analysis runner; the trap repo test. Limits needed: CPU, memory, time, disk, network (no network after dependency install, P29.md:47).
- **Who answers:** student
- **Answer:**
- **Recorded as:**

## Q-008 · How does the local dev environment receive webhooks?
- **Status:** open
- **Blocks:** local end-to-end testing of deliveries (options named in the brief: smee.io, Cloudflare tunnel).
- **Who answers:** student
- **Answer:**
- **Recorded as:**

## Q-009 · Which risk signals does the professor see, in final form?
- **Status:** open
- **Blocks:** the final professor view and its export. The brief's examples (secret found, no tests, activity in the last 48h) can be built; the final list needs validation with the industry developer (P29.md:91, :98).
- **Who answers:** student, after the industry interview
- **Answer:**
- **Recorded as:**

## Q-010 · Which analysers are on by default per repo, and which are optional?
- **Status:** open
- **Blocks:** default per-repo configuration (P29.md:92).
- **Who answers:** student
- **Answer:**
- **Recorded as:**

## Q-011 · Which 5 real repos are connected, with which analysers?
- **Status:** open
- **Blocks:** the Definition of Done (5 live repos for 2 weeks); `REPOS.md`, which only the student writes (P29.md:96, :102).
- **Who answers:** student
- **Answer:**
- **Recorded as:**

## Q-012 · Design tokens and the screenshot command
- **Status:** open
- **Blocks:** the token tables in `docs/design/DESIGN.md`; UI screenshots in the definition of done. Depends on Q-004.
- **Who answers:** student
- **Answer:**
- **Recorded as:**

## Q-013 · Is docs/agents/DECISIONS.md the DECISIONS.md the brief's Definition of Done names?
- **Status:** open
- **Blocks:** where the post-feedback changes are recorded (P29.md:65).
- **Who answers:** student, to confirm with the professor
- **Proposed answer:** Yes; this ledger is the project's decision record. A root `DECISIONS.md` could link to it if the professor expects one there.
- **Answer:**
- **Recorded as:**
