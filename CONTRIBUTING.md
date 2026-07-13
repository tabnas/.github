# Contributing to Tabnas

Thanks for your interest in contributing! These conventions apply to every
repository in the [tabnas](https://github.com/tabnas) organization. Individual
repositories may add specifics in their own docs.

## Repository layout

Almost every Tabnas repository is *polyglot*: it contains two parallel
implementations of the same package.

```
<repo>/
├── ts/        TypeScript implementation  → npm  @tabnas/<repo>
├── go/        Go implementation          → Go   github.com/tabnas/<repo>/go
├── Makefile   build/test both stacks
└── README.md
```

**`ts/` is canonical; `go/` tracks it.** A change to behavior normally needs
to land in both implementations, with tests in both.

## Development setup

Tabnas repositories resolve their unpublished `@tabnas/*` /
`github.com/tabnas/*` siblings from **side-by-side checkouts**, so clone the
repos you are working on (plus their Tabnas dependencies) into one parent
directory:

```bash
mkdir tabnas && cd tabnas
git clone https://github.com/tabnas/parser
git clone https://github.com/tabnas/json     # ...plus whatever you need
```

Common dependencies are `parser`, `debug`, `json`, `abnf` and `railroad`;
check the repo's CI workflow for its exact list.

Then, per repository:

```bash
make build   # builds ts/ and go/
make test    # tests ts/ and go/

# or per stack:
cd ts && npm install && npm run build && npm test
cd go && go build ./... && go test ./...
```

Go builds across siblings use a `go.work` workspace; CI sets this up
automatically and the same layout works locally.

## Commit messages

We use [Conventional Commits](https://www.conventionalcommits.org/). Release
automation derives versions and changelogs from them, so this is required:

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
3. Make sure `make test` passes for **both** implementations.
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
