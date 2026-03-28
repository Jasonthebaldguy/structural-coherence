# SC-FCALC v0.7.0 — Release Notes

**Document ID:** SC-FCALC-000001  
**Canonical Name:** Structural Coherence Formal Operational Calculus — Formal Theory  
**Version:** 0.7.0-DRAFT  
**Issuance ID:** v04  
**Release Date:** 2026-03-28  
**Release Status:** Published for review and comment  
**DOI:** 10.5281/zenodo.19289657  
**Issuing Authority:** Coherence Research  

---

## Status

This version is published for **review and comment**. It has passed internal validation gates and RCC verification, but carries a DRAFT version designation reflecting active development. Feedback and formal comment are welcome.

---

## What This Document Is

SC-FCALC-000001 is the formal operational theory derived from the SC-AS canonical set. It establishes the algebraic, order-theoretic, and convergence properties of the σ-step calculus — the iterative reduction system that implements SC-AS admissibility constraints operationally. It provides the mathematical foundation for SC-CALC-000001 (the computational implementation) and for formal verification of convergence, closure correspondence, and emergence transitions.

This document is derived from SC-AS. It introduces no new primitives, no new admissibility predicates, and claims no canonical authority equal to SC-AS.

---

## Scope

Formal operational theory over SC-AS primitives; proves convergence, closure correspondence, emergence transitions, composition, and ordering-representability conditions; includes abstract reduction system correspondence; derived, non-extending, non-overriding.

---

## Basis / Dependencies

| Document | Version | DOI |
|----------|---------|-----|
| SC-CORE-000001 | v39c | [10.5281/zenodo.18039635](https://doi.org/10.5281/zenodo.18039635) |
| SC-AXIOM-000001 | v11k | [10.5281/zenodo.18043770](https://doi.org/10.5281/zenodo.18043770) |
| SC-HDR-000001 | v12 | — |
| SC-SCOPE-000001 | v04 | — |

All basis documents are publicly available. SC-HDR and SC-SCOPE DOIs pending individual Zenodo deposits.

---

## Validation Status

| Check | Status | Notes |
|-------|--------|-------|
| Document class conformance | PASS | FWK class, all required fields present |
| RCC | PASS | rcc__SC-FCALC-000001__v03__v01.md — 7/7 checks PASS |
| SHA-256 integrity | PASS | `ec5e75583f8f382f13ad97...` |
| Zenodo DOI | Assigned | 10.5281/zenodo.19289657 |
| SC-AS basis verified | PASS | All constructs trace to SC-AS per §12 Derivation Map |

---

## Open Questions

The following open questions remain from this version (documented in §14.2 of the spec):

- **OQ-3:** Archimedean condition for ratio-scale representability at non-discrete regimes
- **OQ-4:** General selection optimality under overlapping driver scopes
- **OQ-5:** Per-step structural equivalence of VFeas candidates
- **OQ-6:** Completeness of the Axiom chain as constraint type coverage for emergence

None of these block the core operational results (convergence, closure correspondence, bounded regime descent).

---

## What Changed

**v04 (this release) from v03:**
- §9 ratio-scale representability: removed Krantz et al. external import (RQ-8 resolved). Representation now derived constructively from §10 integer spectrum and §10.0.1 pathway index arithmetic.
- §10.0.1: Arithmetic on pathway indices derived from D1.9/D1.10 structure via meta-structural apparatus.
- FWK::Author field added (SC-HDR v12 schema).
- Header Schema updated to SC-HDR-000001 v12.

**v03 from prior:**
- Full formal theory: §§1–12 complete.
- RCC verified.

---

## Changelog

| Issuance ID | Date | Summary |
|-------------|------|---------|
| v04 | 2026-03-28 | RQ-8 resolved: §9 ratio-scale derivation closed within SC-AS primitives; Author field added |
| v03 | 2026-03-15 | First full formal theory release; RCC v01 PASS |

---

*Coherence Research — https://coherenceresearch.com*
