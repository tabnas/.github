# tabnas/.github

Organization-wide defaults for [tabnas](https://github.com/tabnas). GitHub
treats this repository specially:

- **[`profile/README.md`](profile/README.md)** — the org's public Overview page.
- **Default community health files** — [`CONTRIBUTING.md`](CONTRIBUTING.md),
  [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md), [`SECURITY.md`](SECURITY.md),
  [`SUPPORT.md`](SUPPORT.md), [`GOVERNANCE.md`](GOVERNANCE.md),
  [`PULL_REQUEST_TEMPLATE.md`](PULL_REQUEST_TEMPLATE.md) and the
  [issue forms](.github/ISSUE_TEMPLATE/) apply to every tabnas repository
  that doesn't ship its own copy. Files are inherited, not copied — they
  never appear in individual clones or packages.
- **Reusable workflows** — [`.github/workflows/`](.github/workflows/) holds
  the shared CI called by each repo's thin caller workflow (see the header
  comment in [`polyglot-ci.yml`](.github/workflows/polyglot-ci.yml)).
- **[`renovate-config.json`](renovate-config.json)** — the org Renovate
  preset; repos extend it with
  `{ "extends": ["local>tabnas/.github:renovate-config"] }`.

Related infrastructure:

- [tabnas/status](https://github.com/tabnas/status) — public org health &
  compliance dashboard.
- `tabnas/admin` (private) — org administration: policy-as-code
  (Safe Settings), decisions/ADRs, operational tooling.
