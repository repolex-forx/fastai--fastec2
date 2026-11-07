# Repolex Knowledge Graph of fastai/fastec2

RDF knowledge graph data for [fastai/fastec2](https://github.com/fastai/fastec2), parsed by [repolex](https://repolex.ai).

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
rlex download fastai/fastec2
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 6b47aa02351983f60d7797420791ac18e70a7f08
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 6b47aa02351983f60d7797420791ac18e70a7f08
│           └── chunk-001.nq.gz
├── blob
│   ├── 12e807dc37e20494f0a446e8c19c505ea2e25cf8.nq.gz
│   ├── 2864eaf5a5babb7b458932523bd05492fb261acb.nq.gz
│   ├── 3ab676c21342c31e263642cecbd920f5a0a3f8ba.nq.gz
│   ├── 6d2c93117f12b9666347daf5f3055bf65e85774b.nq.gz
│   ├── 7fb91908d004d8182ad595937244cb374354a667.nq.gz
│   ├── 8eddff4edefb896fe0fee61db1539917720b0106.nq.gz
│   ├── a1bab3072ec367f08950ec0ef16496852cdccf15.nq.gz
│   ├── c3c12be5ef53606e3b6957ced592192e65e1cb0a.nq.gz
│   ├── d7abb4383151d2d66b9606e3fa893c894e5c6999.nq.gz
│   └── f8212bf6555d5d1beddccdee493553f376c69cd5.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 6b47aa02351983f60d7797420791ac18e70a7f08.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 18 files
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

[fastai/fastec2](https://github.com/fastai/fastec2)

---
*Parsed on 2026-11-07 by [repolex](https://repolex.ai)*
