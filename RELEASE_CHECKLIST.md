# Public release checklist

## Recommended publication structure

A Git repository is useful for version control and transparency, but a repository URL alone is not the strongest archival flag plant.

Recommended stack:

1. **GitHub (or another public Git host)** for living version history, issues, and later code/data updates.
2. **A DOI-bearing archival snapshot** of the first public release through a research archive such as Zenodo or OSF.
3. **Optional preprint** on arXiv or another suitable preprint server once the research statement has been formatted as a conventional manuscript.

The key principle is: **living repository + immutable dated archival release**.

## Before first public release

- [x] Author metadata entered in `CITATION.cff` (Dustin Patzer, Independent Researcher).
- [ ] Add repository URL.
- [ ] Add ORCID if desired.
- [ ] Confirm title and version.
- [ ] Confirm that preliminary empirical statements accurately reflect retained source data.
- [ ] Add references / bibliography, especially prior work on residual norm growth and layerwise residual distributions.
- [x] Confirm split-license approach in `LICENSE.md`.
- [ ] Create Git tag `v0.1.0`.
- [ ] Create a public release from that tag.
- [ ] Archive the exact release in a DOI-bearing repository.
- [ ] Add the DOI back to the README and citation metadata.

## Suggested release note

> **v0.1.0 — Initial public statement of the Scheduled Transformer hypothesis.** This release defines the proposed depth-indexed state-regime framework, records preliminary empirical support, and pre-specifies the planned residual-state extraction and confirmatory analysis regime. Comprehensive confirmatory results are not yet claimed in this release.


## License verification

- Confirm the split-license scope in `LICENSE.md` before release: CC BY-NC 4.0 for substantive research content; CC BY 4.0 for discovery/citation materials.
