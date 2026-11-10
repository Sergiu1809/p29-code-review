# Contracts — p29-code-review

<!-- graffino-agentic:begin v1 -->
> Promises across a boundary. **Provided:** this repo owns the contract; the text
> lives here only. **Consumed:** a link to the provider's entry plus the fields this
> repo relies on. **External:** what we rely on from a third-party service.
> Changing a provided contract is a PROPOSAL (AGENTS.md → The gate) and the plan
> lists the consumers' files too. Status: `approved` · `proposed` · `superseded-by`.
<!-- graffino-agentic:end -->

## Index

---

## Provided

None built yet. The brief requires these; each gets a C- entry when it is built:
the badge SVG URLs used in READMEs, the public portfolio page URL, the PR comment
format, and the professor view export (P29.md:38–41).

## Consumed

None.

## External

### GitHub · OAuth login, repo listing, webhooks, PR comments
- **Interface:** GitHub REST API and webhooks; App vs OAuth App is Q-006.
- **We rely on:** OAuth login; listing the user's repos; creating and deleting a repo webhook; posting a PR comment; push and pull request deliveries with an HMAC signature and a delivery id (P29.md:29–38, :46).
- **Known quirks:** GitHub redelivers deliveries with the same id; the brief requires one analysis per id (P29.md:46).
- **Evidence:** none in code yet (requirements only).

### Package registries · dependency audit
- **Interface:** `npm audit`, `composer audit`, `pip-audit` (P29.md:34).
- **We rely on:** their audit output, run inside the sandbox.
- **Known quirks:** they need network; the sandbox cuts network after dependency install (P29.md:47). Order of steps: Q-007.
- **Evidence:** none in code yet (requirements only).
