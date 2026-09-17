# Muze-X Lab Search & Dev

**Open exploratory research preprints from Muze-X Lab — versioned scientific notes, falsifiable models, reproducible methods, provenance records, and disclosed human–AI collaborative contributions.**

This repository is the public publication surface for selected research snapshots developed in private governed laboratories. It is intentionally **not** a mirror of the private repositories.

Each publication is exported as a versioned **Exploratory Research Preprint (ERP)** with:

- an explicit research status;
- a traceable private-source snapshot;
- a research chronology;
- a falsification or limitation section;
- machine-readable metadata;
- disclosed human–AI collaborative contribution;
- no automatic promotion of a hypothesis merely because it is public.

## Published collection

| ID | Research line | Preprint | Research genealogy | Status |
| --- | --- | --- | --- | --- |
| `ERP-0001` | Finite prime-log operator / Riemann-related exploration | [**O_X: A Finite Mirrored Prime-Log Operator**](preprints/ERP-0001-OX/) | research record from 2026-08-06; first auditable Git record 2026-08-24 | Exploratory |
| `ERP-0002` | Adaptive inference resource allocation | [**Adaptive Inference Resource Regulator (AIRR): A Multi-Resource Closed-Loop Controller for Experimental AI Inference Allocation**](preprints/ERP-0002-AIRR/) | Git-grounded from 2026-08-24 | Experimental / hypothesis-driven |
| `ERP-0003` | Pre-inference admission regulation | [**The Silence-First Framework (SSF) v0.2: An Experimental Pre-Inference Admission Regulator**](preprints/ERP-0003-SSF/) | repository genealogy from 2026-02-02; scientific reconstruction 2026-08-24 | Experimental / reconstructed / falsifiable |

**Initial public release:** 17 September 2026.  
**Peer review:** none claimed for the initial ERP releases.  
**DOI:** not assigned at the initial release.

## Repository structure

```text
Muze-X-Lab-Search-Dev/
├── README.md
├── LICENSE
├── LICENSING.md
├── CITATION.cff
├── CONTRIBUTING.md
├── PREPRINT_INDEX.json
├── PUBLICATION_MANIFEST.json
└── preprints/
    ├── ERP-0001-OX/
    │   ├── README.md
    │   ├── METADATA.json
    │   └── PUBLICATION-MANIFEST.json
    ├── ERP-0002-AIRR/
    │   ├── README.md
    │   ├── METADATA.json
    │   └── PUBLICATION-MANIFEST.json
    └── ERP-0003-SSF/
        ├── README.md
        ├── METADATA.json
        ├── PUBLICATION-MANIFEST.json
        └── source/
            ├── ssf_preprint.tex
            └── references.bib
```

## Scientific status discipline

The collection separates public availability from scientific validation.

Typical status vocabulary across the source projects includes:

- `OPEN` — unresolved question or proof obligation;
- `HYP` / `HYPOTHESIS` — explicit candidate statement with a falsification route;
- `PRED` — falsifiable expected outcome;
- `NUMERICAL` — reproducible computational result under declared conditions;
- `SAT` — a declared test passed under declared conditions;
- `DEMONSTRATED` — complete checkable proof within the stated model;
- `CERTIFIED` — independent review of an exact demonstrated version;
- `UNKNOWN` — not established;
- `REFUTED` — falsified under a declared test.

The exact vocabulary varies by research line, but the governing rule is stable:

```text
public != peer reviewed
implementation != validation
formalization != evidence
SAT != proof
analogy != identity
```

## Collaborative attribution

Research direction and final scientific accountability are retained by **Muze-X · Muse-IRS**.

**ChatGPT (OpenAI)** is disclosed as an AI-assisted collaborative contributor where applicable, including contributions to formalization, counter-analysis, research structuring, experimental design, code/test planning, documentation and manuscript development.

AI collaboration is not presented as independent scientific certification.

## Provenance model

Each ERP records at least:

1. the earliest defensible research-start or genealogy date;
2. the first auditable Git record where available;
3. the private source repository;
4. the exact private source commit used to construct the public snapshot;
5. the public initial publication commit and release date;
6. a later DOI or archival identifier if assigned.

The private laboratories remain authoritative for ongoing work. This public repository contains selected, frozen publication snapshots. See [`PUBLICATION_MANIFEST.json`](PUBLICATION_MANIFEST.json) for the collection-level provenance record.

## Licensing

Unless a preprint explicitly states otherwise, the **public manuscript text and publication metadata** in this repository are licensed under **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Source code or other material reproduced from originating projects remains governed by its stated source license. See [`LICENSING.md`](LICENSING.md).

## Citation

Use the metadata shipped with the exact ERP version cited. The repository-level [`CITATION.cff`](CITATION.cff) identifies the collection; individual ERP metadata identifies the specific research snapshot.

## Scope boundary

This repository exists to expose research in a form that is inspectable, citable and historically traceable. It is not a publication venue claiming peer review, institutional endorsement, patent priority, or proof beyond the status explicitly attached to each result.
