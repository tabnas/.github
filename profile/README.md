# Tabnas

**One parsing engine, many formats — in TypeScript and Go.**

Tabnas is a grammar-driven parsing ecosystem. A single engine
([`parser`](https://github.com/tabnas/parser)) powers a family of format
parsers, each shipped as a matched pair of implementations: an npm package
(`@tabnas/*`) and a Go module (`github.com/tabnas/<repo>/go`).

## Ecosystem

### Engine & tooling

| Repo | What it is |
| --- | --- |
| [parser](https://github.com/tabnas/parser) | The Tabnas parsing engine |
| [abnf](https://github.com/tabnas/abnf) | BNF compiler for the Tabnas parser |
| [debug](https://github.com/tabnas/debug) | Debug plugin for the Tabnas parser |
| [railroad](https://github.com/tabnas/railroad) | Railroad diagrams |
| [jsonic-cli](https://github.com/tabnas/jsonic-cli) | Command-line interface for `@tabnas/jsonic` |

### Format parsers

| Repo | Format |
| --- | --- |
| [json](https://github.com/tabnas/json) | JSON |
| [jsonc](https://github.com/tabnas/jsonc) | JSON with Comments |
| [json5](https://github.com/tabnas/json5) | JSON5 |
| [jsonic](https://github.com/tabnas/jsonic) | JSONIC (relaxed JSON dialect) |
| [yaml](https://github.com/tabnas/yaml) | YAML |
| [toml](https://github.com/tabnas/toml) | TOML |
| [ini](https://github.com/tabnas/ini) | INI |
| [csv](https://github.com/tabnas/csv) | CSV |
| [xml](https://github.com/tabnas/xml) | XML |
| [markdown](https://github.com/tabnas/markdown) | Markdown |
| [css](https://github.com/tabnas/css) | CSS |
| [c](https://github.com/tabnas/c) | C (concrete syntax) |
| [proto](https://github.com/tabnas/proto) | Protocol Buffers IDL (all versions) |
| [zon](https://github.com/tabnas/zon) | ZON (Zig Object Notation) |
| [feed](https://github.com/tabnas/feed) | Web feeds |

### Supporting libraries

[expr](https://github.com/tabnas/expr) ·
[path](https://github.com/tabnas/path) ·
[directive](https://github.com/tabnas/directive) ·
[hoover](https://github.com/tabnas/hoover) ·
[multisource](https://github.com/tabnas/multisource)

## Install

```bash
# TypeScript / JavaScript
npm install @tabnas/json

# Go
go get github.com/tabnas/json/go
```

## Project health

Org-wide status and compliance reporting lives at
[tabnas/status](https://github.com/tabnas/status).

## Contributing

All repositories share the same conventions — see the org-wide
[CONTRIBUTING guide](https://github.com/tabnas/.github/blob/main/CONTRIBUTING.md).
Security issues: see [SECURITY](https://github.com/tabnas/.github/blob/main/SECURITY.md).

All code is [MIT licensed](https://opensource.org/licenses/MIT).
