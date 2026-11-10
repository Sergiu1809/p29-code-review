# CONTEXT — p29-code-review vocabulary

<!-- graffino-agentic:begin v1 -->
> The approved terms for this project. Use each term exactly as defined, in the part
> of speech given. Never swap in a synonym; never use a word on an _Avoid_ line.
<!-- graffino-agentic:end -->

**Connected repo** (noun) — a developer's repo whose webhook this platform created; disconnecting deletes the webhook.
_Avoid_: linked repo, tracked project

**Delivery** (noun) — one webhook call from GitHub, identified by its delivery id; a redelivery repeats the same id.
_Avoid_: event, hook call

**Analysis** (noun) — one run of the configured analysers over one commit of a connected repo.
_Avoid_: scan (except for the secret scan), check, build

**Analyser** (noun) — one configurable step of an analysis: lint, tests, complexity, dependency audit, secret scan, diff size.
_Avoid_: plugin, tool, check

**Job** (noun) — a queued unit of work that runs one analysis.
_Avoid_: task, worker run

**Stale job** (noun) — a job for a repo/branch that a newer push has replaced; it is cancelled, even while running.
_Avoid_: outdated job, old job

**Sandbox** (noun) — the isolated environment where repo code runs, with CPU, memory, time, disk and network limits.
_Avoid_: container (unless the mechanism is meant), runner, VM

**Infrastructure error** (noun) — a failure of the platform (sandbox, clone, queue); the job is retried.
_Avoid_: system error

**Code error** (noun) — a failure caused by the analysed repo (lint fails, tests fail, timeout in its tests); never retried.
_Avoid_: user error, build error

**Trap repo** (noun) — the student's hostile test repo ("repo capcană") that tries to escape the sandbox or block the queue.
_Avoid_: evil repo, malicious fixture

**Secret finding** (noun) — a detected secret, stored only as type, file, line and partial hash, never the value.
_Avoid_: leak, exposed key

**Partial hash** (noun) — a truncated hash of a secret's value, enough to match repeats, not enough to recover it.
_Avoid_: fingerprint, masked value

**Badge** (noun) — a dynamic, cached SVG image (tests, vulnerabilities, last scan) for a README.
_Avoid_: shield, icon

**PR comment** (noun) — the automatic summary comment posted on a pull request; configurable and switchable per repo.
_Avoid_: review, bot message

**Portfolio page** (noun) — a developer's public page: projects, detected stack, weekly commit activity, insignia; can be switched off.
_Avoid_: profile, CV page

**Class** (noun) — a professor's group of developers and their connected repos.
_Avoid_: group, course

**Risk signal** (noun) — a flag in the professor view, e.g. a secret found, no tests, activity concentrated in the last 48h.
_Avoid_: alert, warning

**Developer** (noun) — the role that connects repos and owns a portfolio page.
_Avoid_: student (as a role name), user

**Professor** (noun) — the role that manages classes and sees the class view and risk signals.
_Avoid_: teacher, instructor

**Admin** (noun) — the role that manages the platform.
_Avoid_: superuser
