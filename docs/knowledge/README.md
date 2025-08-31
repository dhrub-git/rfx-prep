# Knowledge Packs

- Purpose: Curated, versioned sets of sources used by the RFP agentic workflows. Each pack contains a `manifest.json` and referenced artifacts.

- Packs:
  - `sydney_metro_cms_modernization/` — sample pack for a NSW use case

## Structure
- `manifest.json` — metadata, approvals, allowed models, source list
- `requirements.csv` — extracted requirements
- `compliance_matrix.csv` — owner, coverage, evidence, confidence
- `outline.md`, `technical_approach.md`, `architecture.md`, `project_plan.md`
- `nsw_standards.md`, `pricing_assumptions.md`, `research_notes.md`
- `resumes/` — short bios for key roles

## Usage
- Index the pack into search/vector stores with pack-level namespace.
- Enforce citation of file paths and section anchors from pack sources.
- After project retro, promote high-value content into base/domain packs.
