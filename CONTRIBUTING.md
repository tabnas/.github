# Contributing to Tabnas

Thanks for your interest in contributing! These conventions apply to every
repository in the [tabnas](https://github.com/tabnas) organization. Individual
repositories may add specifics in their own docs.

## Repository layout

Almost every Tabnas repository is *polyglot*: it contains three parallel
implementations of the same package.

```
<repo>/
├── ts/        TypeScript implementation  → npm        @tabnas/<repo>
├── go/        Go implementation          → Go         github.com/tabnas/<repo>/go
├── rs/        Rust implementation        → crates.io  tabnas-<repo>
├── Makefile   build/test all three stacks
└── README.md
```

**`ts/` is canonical; `go/` and `rs/` track it.** A change to behavior
normally needs to land in all three implementations, with tests in all
three.

## Development setup

The TypeScript and Go sides install published packages, `@tabnas/*` from the
npm registry and `github.com/tabnas/*/go` from the Go module proxy, so a
clone of the one repository builds and tests them. The Rust side is the
exception: each `rs/Cargo.toml` takes its Tabnas crates as path dependencies
(`path = "../../<repo>/rs"`), so the Rust build needs those repositories
checked out beside the repository even for a plain build. The crates are all
on crates.io, but the committed manifests stay path-only; the release
workflow swaps in crates.io versions only when it publishes. So clone the
repos you are working on, plus the Tabnas dependencies their `rs/Cargo.toml`
names, into one parent directory:

```bash
mkdir tabnas && cd tabnas
git clone https://github.com/tabnas/parser
git clone https://github.com/tabnas/json     # ...plus whatever you need
```

For TypeScript and Go, sibling checkouts are optional: they matter only when
you work against unreleased changes in a dependency. Then link each one over
`ts/node_modules/@tabnas/<name>` and list the Go modules in a `go.work` in
the parent directory (the maintainers' `scripts/link.sh`, in the private
`tabnas/admin` repository, does both). Never commit that wiring. A repo's
`.github/workflows/ci.yml` names, in `deps`, the siblings its CI builds.

Then, per repository:

```bash
make build   # builds ts/, go/ and rs/
make test    # tests the same

# or per stack:
cd ts && npm install && npm run build && npm test
cd go && go build ./... && go test ./...
cd rs && cargo build --all-targets && cargo test --all-targets
```

CI (the shared `polyglot-ci.yml`) clones the siblings named in `deps`, links
them over the registry copies, and builds Go through a `go.work` over them.
It then builds the Go module again with `GOWORK=off`, against the versions
`go.mod` requires, which is what a consumer gets.

## Commit messages

We use [Conventional Commits](https://www.conventionalcommits.org/), for
commit messages and PR titles alike, and they are required. PRs are
squash-merged, so a PR's title is its commit message, and the GitHub Release
each release creates lists those titles in its generated notes. They do not
set the version: a release is its own version-bump pull request, then a
dispatch of the repository's `release.yml` on `main`. For example:

```
feat: add lax mode for trailing commas
fix: handle CRLF inside block scalars
docs: clarify plugin ordering
chore: update dev dependencies
```

Use `feat!:` / `fix!:` (or a `BREAKING CHANGE:` footer) for breaking changes.

## Pull requests

1. Open an issue first for anything larger than a small fix, so the approach
   can be agreed before you invest time.
2. Branch from `main`; keep PRs focused on one change.
3. Make sure `make test` passes for **all three** implementations.
4. PR titles follow Conventional Commits (PRs are squash-merged, so the title
   becomes the commit message).
5. CI must be green and one maintainer review is required before merge.

## Reporting bugs

Use the issue forms — they ask for the package version, which implementation
(TypeScript or Go), and a minimal reproduction. A failing test case is the
most useful reproduction of all.

## Security issues

Never open a public issue for a vulnerability — see [SECURITY.md](SECURITY.md).

## Code of conduct

Participation in the Tabnas community is covered by our
[Code of Conduct](CODE_OF_CONDUCT.md).
