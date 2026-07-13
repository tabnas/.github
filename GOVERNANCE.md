# Governance

This document describes how the [tabnas](https://github.com/tabnas)
organization is run. It applies to all repositories in the organization.

## Model

Tabnas currently uses a **single-maintainer (BDFL) model**: the project lead
has final say on design, scope, releases, and conduct enforcement. As the
contributor base grows, this document will evolve toward a maintainer-team
model.

**Project lead:** Richard Rodger ([richard@ricebridge.com](mailto:richard@ricebridge.com))

## Repository tiers

Repositories are classified into tiers, which determine how strictly policy
(reviews, branch protection, release cadence) is applied:

| Tier | Meaning | Repositories |
| --- | --- | --- |
| **core** | The engine and packages everything else depends on; versioned in lockstep | `parser`, `abnf`, `debug`, `json`, `railroad` |
| **supported** | Stable format parsers and tools; independent versioning | all other public repositories |
| **experimental** | Pre-stable APIs; may change without notice | tagged per repository |

The authoritative tier assignment lives in the organization's policy-as-code
configuration and is reported on the public
[status dashboard](https://github.com/tabnas/status).

## Decision making

- **Small changes** (bug fixes, docs, non-breaking improvements): decided in
  the pull request by the reviewing maintainer.
- **Larger changes** (new features, API changes): open an issue first;
  the project lead decides after discussion.
- **Breaking changes** to core packages require an issue, an explicit
  migration note, and a coordinated release.

## Becoming a maintainer

Consistent, high-quality contributions (code, review, triage, docs) are the
path to commit access. The project lead grants maintainer status per
repository. Maintainers are expected to follow this governance document, the
[Code of Conduct](CODE_OF_CONDUCT.md), and the org's policy-as-code
configuration.

## Changes to this document

Changes are proposed by pull request to
[tabnas/.github](https://github.com/tabnas/.github) and decided by the
project lead.
