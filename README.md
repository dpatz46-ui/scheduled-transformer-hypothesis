# The Scheduled Transformer

## A Hypothesis of Depth-Indexed State Regimes in Pre-RMSNorm Language Models

**Author / proposer:** Dustin Patzer  
**Affiliation:** Independent Researcher

**Status:** Public research statement / preliminary theory release  
**Version:** 0.1.0  
**Date:** 2026-09-22  
**License:** Substantive research content: [CC BY-NC 4.0](LICENSE.md); discovery/citation materials: [CC BY 4.0](LICENSE.md)

This repository publicly states the **Scheduled Transformer hypothesis** and records the planned empirical program for formal testing.

The narrow claim is that modern pre-normalized transformer language models appear to traverse a reproducible, ordered sequence of **depth-indexed state regimes**. In its most operational present form, the hypothesis concerns the geometry of the residual stream across layer depth.

Let \(x_{i,p,l}\) denote the residual-stream state for example \(i\), token position \(p\), and depth \(l\). Define

\[
r_{i,p,l}=\|x_{i,p,l}\|,
\]

and, where useful,

\[
y_{i,p,l}=\log r_{i,p,l}.
\]

The proposed object is **not merely residual-norm growth**. Prior work has already documented depth-dependent residual norms and growth. The Scheduled Transformer hypothesis instead treats the **ordered sequence of layer-conditioned state distributions and transition regimes itself** as the object of study: their centres, widths, shapes, overlaps, persistence, reorganization, contraction and expansion, and reproducible context-conditioned departures.

> **Core statement:** Transformer computation proceeds through a reproducible sequence of depth-indexed state regimes, with each successive transformation acting upon an inherited state shaped by the preceding trajectory.

Preliminary analysis of primary activation data **strongly indicates support** for this hypothesis. The formal confirmatory program is still in progress. This repository therefore separates:

1. the proposed theory;
2. preliminary supporting observations; and
3. the pre-specified experimental program intended to test, refine, or falsify the proposal.

## Repository map

- [`THEORY.md`](THEORY.md) — public-facing statement of the hypothesis.
- [`methods/EXPERIMENT_PLAN.md`](methods/EXPERIMENT_PLAN.md) — planned confirmatory experimental regime.
- [`methods/EXTRACTION_PROTOCOL.md`](methods/EXTRACTION_PROTOCOL.md) — residual-stream hook and data-acquisition plan.
- [`PRELIMINARY_STATUS.md`](PRELIMINARY_STATUS.md) — what is presently supported, what remains provisional, and what is not yet claimed.
- [`ROADMAP.md`](ROADMAP.md) — staged research program.
- [`CITATION.cff`](CITATION.cff) — citation metadata template.
- [`RELEASE_CHECKLIST.md`](RELEASE_CHECKLIST.md) — suggested public-release / archival workflow.
- [`LICENSE.md`](LICENSE.md) — split licensing: CC BY-NC 4.0 for substantive research content; CC BY 4.0 for discovery/citation materials.

## Scope

The hypothesis does **not** claim that residual radius alone represents meaning, that a model explicitly reads radius as a numerical depth coordinate, or that all contextual differentiation must appear radially. Direction, subspace structure, and other geometric properties remain available to carry differentiated relational content.

The narrow proposal is that residual states occupy structured, depth-dependent regimes and that transformer computation proceeds through their ordered traversal.

## Current empirical status

Preliminary work across multiple activation datasets shows structured depth dependence beyond simple monotonic norm growth, including candidate depth-specific radial bands, repeated changes in distributional width, radial contraction and expansion, persistence and reorganization of relative state positions, and candidate context-conditioned departures from a dominant trajectory.

These observations are treated here as **preliminary support**, not as completed confirmation. The primary confirmatory study is being formalized and executed separately.

## Suggested citation

Until archival metadata are finalized, preferred citation is: **Dustin Patzer, *The Scheduled Transformer: A Hypothesis of Depth-Indexed State Regimes in Pre-RMSNorm Language Models*, version 0.1.0 (2026)**, followed by the repository URL. A DOI-bearing archival release is recommended for public citation.
