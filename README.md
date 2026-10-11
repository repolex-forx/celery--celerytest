# Repolex Knowledge Graph of celery/celerytest

RDF knowledge graph data for [celery/celerytest](https://github.com/celery/celerytest), parsed by [repolex](https://repolex.ai).

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
rlex download celery/celerytest
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 39c71758240c598f56dcde900fe607364c4ddffe
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 39c71758240c598f56dcde900fe607364c4ddffe
│           └── chunk-001.nq.gz
├── blob
│   ├── 006dc16d67e9dca13dd459e0688b4ded1289509e.nq.gz
│   ├── 0384aed26f1ede6c28f4b472ef12d3c752b4ffd5.nq.gz
│   ├── 3373b280cf8ca7b3e586126e9b4481b9090c3377.nq.gz
│   ├── 3c66c6f90021ce5cad959dfed1fd86ac5cfe2126.nq.gz
│   ├── 665db51506cb3392e691d958d3128c52a8849780.nq.gz
│   ├── 67bb7498d598549ce66f30173d3c6ac739037aa3.nq.gz
│   ├── 7fc4e22c1e67cc625dd7017daa5ef244f2922674.nq.gz
│   ├── 8152910a2cf7ffe785995c0c21e9171fc49f31ce.nq.gz
│   ├── 90001186118cb7e719196e9a4b63d73801d79be1.nq.gz
│   ├── 9b11eec3ac01e69af460b64a63485756d6b9fecf.nq.gz
│   ├── ad04fe3cd44ac8f3227eae2a7ef47f0bc25c3ee1.nq.gz
│   ├── b9b8de2a0bc70cb335e8cef195aadb4e10c3d099.nq.gz
│   ├── eb78715e8e8ee16c84b3c315eb20ba32de6430d9.nq.gz
│   └── fadeb6f618ea9bdde04675a9e64215f73f149ad2.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 39c71758240c598f56dcde900fe607364c4ddffe.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 22 files
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

[celery/celerytest](https://github.com/celery/celerytest)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
