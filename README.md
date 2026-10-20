# Repolex Knowledge Graph of klen/signalbus

RDF knowledge graph data for [klen/signalbus](https://github.com/klen/signalbus), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download klen/signalbus
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 6cf2c99c0703f6a8cc8b02c54bcd7de122c002e6
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 6cf2c99c0703f6a8cc8b02c54bcd7de122c002e6
│           └── chunk-001.nq.gz
├── blob
│   ├── 2a34a38389d5b0eac70d9ca6e06dbc4ab28d475e.nq.gz
│   ├── 502b398f50fcf28f9bc857a9140a8b022fd368cb.nq.gz
│   ├── 6032c7bdb5d2b4f13eb87ead5cf1bc1d7e7467ca.nq.gz
│   ├── 6314485fe40a26a1d76c500051e192d96817259e.nq.gz
│   ├── 9b1c8b133c966006ff025957aa43c7de7bc04be8.nq.gz
│   ├── 9db15d06f63aa387868e883ccc13592e4c4c3420.nq.gz
│   ├── c85fd2da562176be3d951862d74b81ccb849563f.nq.gz
│   ├── dccc506f15cdefe7836a3076d0330c74a1a4e2a2.nq.gz
│   ├── de925c5a377a6e9babb50c2554bf6bae933820b5.nq.gz
│   ├── e169889f5c3868ca7c76d6e0cfe9812ab60d345b.nq.gz
│   └── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 6cf2c99c0703f6a8cc8b02c54bcd7de122c002e6.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 17 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[klen/signalbus](https://github.com/klen/signalbus)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
