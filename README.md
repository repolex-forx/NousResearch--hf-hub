# Repolex Knowledge Graph of NousResearch/hf-hub

RDF knowledge graph data for [NousResearch/hf-hub](https://github.com/NousResearch/hf-hub), parsed by [repolex](https://repolex.ai).

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
rlex download NousResearch/hf-hub
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── a66bdcf2f2664a55ab3a1415184c7aebd8ac4ed5
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── a66bdcf2f2664a55ab3a1415184c7aebd8ac4ed5
│           └── chunk-001.nq.gz
├── blob
│   ├── 1c3b18fec5fae00e8f4dfbac76e979d34ef13e24.nq.gz
│   ├── 2ef5f7b54cf9f0000dd4e26c9f9192a4087d48d1.nq.gz
│   ├── 3172115b500079c1fec82991800f26367cba86c9.nq.gz
│   ├── 5f13df66ddcb6cd821f1883719d96225dea9c84a.nq.gz
│   ├── 71aefc371d5b1a971afafaa0294417b871252d13.nq.gz
│   ├── 7aea0c689b614c9a30708a0f986ec264bb6e9166.nq.gz
│   ├── 83e3e688e30f7ed5a1b5cd76c999c7adb3f79183.nq.gz
│   ├── 8f5a03d4ce1c89a71750d2b73eea9d4aac13f195.nq.gz
│   ├── 96ef6c0b944e24fc22f51f18136cd62ffd5b0b8f.nq.gz
│   ├── b616fa06ab9e643921dadb374d8f22522f941609.nq.gz
│   ├── dfa0cbb28d632d44be4b3f00e0aee23819eaa3f6.nq.gz
│   └── ef738ca7ce29467ffe0bfbda14a9504b375bf13a.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── a66bdcf2f2664a55ab3a1415184c7aebd8ac4ed5.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 19 files
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

[NousResearch/hf-hub](https://github.com/NousResearch/hf-hub)

---
*Parsed on 2026-10-09 by [repolex](https://repolex.ai)*
