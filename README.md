# Repolex Knowledge Graph of vercel/arg

RDF knowledge graph data for [vercel/arg](https://github.com/vercel/arg), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [lexq](https://github.com/repolex-ai/lexq) query tool using [uv](https://docs.astral.sh/uv/getting-started/installation/).

If you have uv installed, just copy/paste this into your terminal:

```bash
uv tool install git+https://github.com/repolex-ai/lexq
```

This installs lexq onto your system, in your user context. Verify the install:

```bash
lexq --help
```

**lexq is designed to be used primarily by LLMs in a terminal.** Start up your favorite LLM and ask it to use the lexq tool. It's that easy!

To load this repo's data:

```bash
lexq download vercel/arg
```

This will automatically download essential data files from the last parsed commit. Consult `lexq --moreinfo` for other options, including downloading multiple commits, blobs, etc.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 20e630a8a581dfe7ac9a47290b9be66d2ac5c752
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 20e630a8a581dfe7ac9a47290b9be66d2ac5c752.nq.gz
│   └── repolex
│       └── 20e630a8a581dfe7ac9a47290b9be66d2ac5c752
│           └── chunk-001.nq.gz
├── blob
│   ├── 100e340b76dd50e16604eacc0c66a6ccddfb8fd0.nq.gz
│   ├── 2e5320bca288312b897db71084b5b7af84e315bb.nq.gz
│   ├── 3f60f4cadc95780cfbb37bf27e972a864c69cbff.nq.gz
│   ├── 44f9f354ba3354257f701bbcf669dc5fae45792a.nq.gz
│   ├── 47368d76d2b916bb003ec35e0ff6162d3f23768f.nq.gz
│   ├── 49e638f1d4f6fb4be023dc1298419a5e81859d34.nq.gz
│   ├── 5bc071f4804e4f848409e818313fdfe8f63c447d.nq.gz
│   ├── 6501df5980d25fb1dc4f3f569ae36192cdb8f5cb.nq.gz
│   ├── 7170cff093742da9665b7226ba7ebf40b1e060f3.nq.gz
│   └── b708f872cb51eb69058c6f83864300a5ce4b0658.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── 20e630a8a581dfe7ac9a47290b9be66d2ac5c752.nq.gz
├── filetree
│   └── 20e630a8a581dfe7ac9a47290b9be66d2ac5c752.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 20 files
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

## Source repository

[vercel/arg](https://github.com/vercel/arg)

---
*Parsed on 2026-04-25 by [repolex](https://repolex.ai)*
