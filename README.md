# Repolex Knowledge Graph of scrapy/scrapely

RDF knowledge graph data for [scrapy/scrapely](https://github.com/scrapy/scrapely), parsed by [repolex](https://repolex.ai).

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
rlex download scrapy/scrapely
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 31b5881bed01a99be2b65b30b9c81ad65a517eaf
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 31b5881bed01a99be2b65b30b9c81ad65a517eaf
│           └── chunk-001.nq.gz
├── blob
│   ├── 0b4a93c4fecaa2f1fbf17be5e755a7f45e05ebdf.nq.gz
│   ├── 12a32933be6700ad52c499e04aaf711132fcdf61.nq.gz
│   ├── 136c2f6666ce4a31b8701f6372ed9bf668304855.nq.gz
│   ├── 1749078632f9305142556ea62c7d4ab15a9eefe9.nq.gz
│   ├── 1a2f1ebe6c6e43343a1f426a796dbaefc1fac2e9.nq.gz
│   ├── 1bea6e82a25ce74c517c6cea81b5888ef8155bd8.nq.gz
│   ├── 1e32c5e357e82837de8d49de4f5836a392e79bbd.nq.gz
│   ├── 24e8879d18ddb462401495cf5128174c399d1ee2.nq.gz
│   ├── 3246b0a933414fc6bffb7acd74e91c322cd4a0a8.nq.gz
│   ├── 3e4324779b575c1d0830d91a88a9c8e91bc1a818.nq.gz
│   ├── 42185b2b8327db6a16fffb83e5d9538f27ca5d29.nq.gz
│   ├── 421e39c2493251e94056887dfa464048463ab52c.nq.gz
│   ├── 489ea40b692d706f0443c26f3f18aa199b83b319.nq.gz
│   ├── 4cb993fb7e2a822506a158dc0e45f62413d277a3.nq.gz
│   ├── 54845736ab9065db4bde00b281d799726f8ff5d3.nq.gz
│   ├── 5ce8c480b937ceccc2ce0a0d29cb88a1f2bf1ec9.nq.gz
│   ├── 615a5544203077f41e4f52897a72db552911429f.nq.gz
│   ├── 6472e8c1e53390999b263968ea350715805bbc1c.nq.gz
│   ├── 69f062ac946b9fcdd54eac4045b8b7f88a40cfeb.nq.gz
│   ├── 74a469e7a1cc1dce89992813b223bb79a3d8ed31.nq.gz
│   ├── 7de1bec354cd3eee7b70e0e1e0129b74f256b984.nq.gz
│   ├── 8469ce9dea44d68ef78c34412078f02bdbefbfaf.nq.gz
│   ├── 8cc36e6db750ae77a2c32d748c1111ae79096987.nq.gz
│   ├── 8d35720b055c186ed1988d3edfacde541e5420ed.nq.gz
│   ├── 968c870693a7eebf367cbeab2bc770bd886b2eff.nq.gz
│   ├── 98a697e964c80f85ea0743f1ae3dcd9cb6f65283.nq.gz
│   ├── a1a5b8c6f57142a9ef76e1ff35fa5469bf1ce53d.nq.gz
│   ├── a93cb0cc389894db19aa9a1c004f737e8fc17780.nq.gz
│   ├── abd1c1201d9530c5de9f69652bd08ea276e1b412.nq.gz
│   ├── ac640b578f8ace9fe710977b841826088ef0c0e6.nq.gz
│   ├── b59bcf1b86b17c0f27420e424e874fa70a11d904.nq.gz
│   ├── b94b12fafdaaed7f00e0a35987124d3443d34f76.nq.gz
│   ├── c6dc0b838018ff2eb3cecaceee6b251226ab6a38.nq.gz
│   ├── ca308524fced762c3726011e0ee8552ec4036273.nq.gz
│   ├── d7977cb0a6e20564f06d3000c5f93f27adf1e865.nq.gz
│   ├── e5ab414f7b5f6a7ac860b6a5e9c48e562e36454b.nq.gz
│   ├── ee910e77df5d911b6ea1a070ec06ee3c7aa719a2.nq.gz
│   ├── ef561787b7bae335019a1da845aaeb34cc318162.nq.gz
│   └── fb01d303f1c905037b082d651e7469ef11a4d770.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 31b5881bed01a99be2b65b30b9c81ad65a517eaf.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 47 files
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

[scrapy/scrapely](https://github.com/scrapy/scrapely)

---
*Parsed on 2026-10-12 by [repolex](https://repolex.ai)*
