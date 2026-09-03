# AcmeCloud Docs Infrastructure

This repository is a progressive, hands-on project that demonstrates **how developer documentation can evolve from human-readable content into agent-consumable infrastructure.**

The goal is to demonstrate how documentation infrastructure should evolve:

***Starting from a structured, governed content foundation, and progressively exposing it to AI agents through MCP, without sacrificing accuracy, structure, or human trust.***

The project mirrors how modern developer platforms build and mature their documentation layer:

***One problem area at a time, each shipped independently, with architecture guiding every stage of growth.***

---

## What this repository demonstrates

This project focuses on:

- Designing documentation infrastructure around distinct, real-world problem areas rather than a single monolithic doc set
- Structuring content so it is reliable for both human developers and AI agents
- Exposing that content through MCP tools, one problem area at a time
- Understanding WHERE automation and AI genuinely help, and WHERE editorial judgment must stay in the loop
- Treating documentation as a system to be governed and measured, not just written

AcmeCloud (a fictional developer PaaS) is used as the example platform, but the patterns here are intended to generalize to any developer-facing documentation surface.

**NOTE:** This project focuses on documentation serving, diagnostics, and coverage, assuming content already exists. For a companion project on the generation and AI-enhancement pipeline itself, see [`End-to-End-Documentation-Pipeline`](https://github.com/PrineetKaur/End-to-End-Documentation-Pipeline).

---

## Problem areas (modules)

This project is organized around independent modules, each addressing a distinct documentation problem. Each module is designed to ship and be evaluated on its own, rather than requiring the whole system to be "finished" before any of it is useful.

### Module 1: Docs Search & Onboarding *(built)*

Getting developers to the right answer fast, without a support ticket. Exposes `search_docs` and `get_quickstart` over AcmeCloud's synthetic documentation set.

### Module 2: API Changelog & Migration *(in progress)*

Keeping documentation in sync with fast-moving API changes, and helping integrators migrate safely between versions. Exposes `get_breaking_changes` and `get_migration_guide`.

### Module 3: Error Diagnostics *(planned)*

Turning recurring support escalations into a structured, self-serve diagnostic reference: symptom, cause, and resolution, as data rather than prose. Will expose `get_troubleshooting_steps`.

### Module 4: Coverage Gap Finder *(planned)*

Automatically identifying where documentation is missing or stale, and drafting a starting point for a human to finish. Will expose `check_doc_coverage` and `draft_doc_stub`.

---

## Repository structure

```
acmecloud-docs-infrastructure/
│
├── content/                     # Synthetic AcmeCloud documentation
│   ├── docs/                       # Module 1: quickstarts, guides
│   ├── changelog/                   # Module 2: versioned API changes
│   └── diagnostics/                 # Module 3: symptom, cause, resolution data
│
├── server/                      # MCP server implementation
│   ├── main.py                     # Server entrypoint
│   └── tools/
│       ├── search_docs.py
│       ├── get_quickstart.py
│       ├── get_breaking_changes.py         # in progress
│       ├── get_migration_guide.py          # in progress
│       ├── get_troubleshooting_steps.py    # planned
│       ├── check_doc_coverage.py           # planned
│       └── draft_doc_stub.py               # planned
│
├── tests/
├── README.md
├── LICENSE
└── requirements.txt
```

Each folder has a clearly defined responsibility:

- **content/**: Synthetic AcmeCloud documentation, organized by module
- **server/**: MCP server and one tool file per capability
- **tests/**: Tests per module, added as each module ships

---

## The roadmap

This repository is developed in clear, incremental phases. Each module ships as its own unit, rather than all at once.

- [x] **Module 1**: Docs search & onboarding
- [ ] **Module 2**: API changelog & migration *(in progress)*
- [ ] **Module 3**: Error diagnostics
- [ ] **Module 4**: Coverage gap finder
- [ ] Swap keyword search for embedding-based retrieval
- [ ] Write up architecture decisions as a companion blog post

---

## How to run the server

From the repository root:

```
pip install -r requirements.txt
python server/main.py
```

Then connect it to Claude Desktop (or another MCP-compatible client) by adding it to your MCP config. See `docs/setup.md` *(coming soon)*.

---

## Why this project exists

This project grew out of real-world experience designing knowledge and documentation infrastructure, including controlled vocabularies, diagnostic references, and docs-as-code pipelines, for developer-facing products. This repository exists to explore:

- How a documentation platform's infrastructure can be broken into independent, shippable problem areas
- How structured content (not just well-written prose) becomes something an AI agent can reliably act on
- How the same governance principles that make docs trustworthy for humans extend to MCP tools for agents
- How to expose documentation as agent-callable tools without turning it into an ungoverned surface

The emphasis is on **architecture and reasoning**, not just the tools themselves.

---

## About the approach

- Each module builds and ships independently
- Complexity is introduced gradually, one problem area at a time
- Decisions are intentional and documented
- The project remains understandable at every stage

---

## Notes

AcmeCloud is a fictional developer platform. All documentation content, error codes, and changelog entries in this repository are invented for demonstration purposes and do not represent any real company, product, or employer, past or present. This repository demonstrates the architecture and reasoning behind agent-consumable documentation infrastructure, built at a scale suited for learning, experimentation, and portfolio review.

## License

MIT. This is a demo/portfolio project, feel free to fork and adapt.
