# Industrial data harmonization and contextualization home lab

This repository (`aadehamid/industrial-context-engineering`, renamed from
`scada_harmonization` on 2026-11-26) simulates Lagos Specialty Chemicals, a
manufacturer whose sites represent similar equipment and process data with
different tags, units, and identities. It turns those differences into a
governed Sparkplug B Unified Namespace, then connects operational, business,
and engineering context in a knowledge graph. The Python package name
(`src/scada_harmonizer/`), the live R2 prefix (`lagos-chem-l0/`), and the
Eraser workspace (`scada_harmonization`) stay unchanged.

The lab is a learning environment and architecture prototype. Only the physical
Level 0 data is synthetic. The software above it exercises real protocols,
services, and data contracts.

## Start here

1. Read [HANDOFF.md](HANDOFF.md) sections 2 and 3 for current status and what to build next.
2. Read [the project charter](docs/LSC-001_Problem_Statement_and_Project_Charter.md) for the problem, scope, architecture, decisions, and phase exit criteria.
3. Use [the master index](docs/LSC-000_Master_Index.md) to choose a subject or learning path.
4. Read [working conventions](docs/WORKING_CONVENTIONS.md) and [the development guide](docs/DEVELOPMENT.md) before making changes.

## What the lab explores

| Plane | Responsibility | Charter |
| --- | --- | --- |
| Harmonize | Conform site-specific OT representations into reusable telemetry | Section 3, Plane 1 |
| Record | Turn curated operational events into enterprise records | Section 3, Plane 2 |
| Contextualize | Reconcile IT, OT, and engineering identities into connected context | Section 3, Plane 3 |
| Apply | Use the governed context for ML and graph-based reasoning | Section 3, Plane 4 |

The three-stage mapping connects a Level 0 variable to a site PLC tag and a
Sparkplug metric. The Unit 100 engineering record links the 59-name tag schedule
to that work. See [the engineering record](docs/LSC-007_Unit_100_Engineering_Record.md)
and [the Level 0 contract](docs/LSC-004_Level_0_Contract.md).

The drawing-to-graph learning path is defined in charter section 8, Phase 5b.1.
The related private project `aadehamid/engineering-drawing-intelligence`
(formerly `aadehamid/Engineering_Drawing_to_Graph`) adds an authoring-system
backend route; it is a separate project, not a dependency.

## Relationship to Pearland Petroleum Corporation (PPC)

Lagos Specialty Chemicals (LSC) and its R2 bucket (`lagos-chem-l0/`) remain this
repository's standalone home-lab scenario through Phase 7. Across the broader
five-repository downstream ecosystem (`enterprise-performance-model`,
`enterprise-context-engineering`, `industrial-context-engineering`,
`engineering-drawing-intelligence`, and `pearland-petroleum-corporation`),
`aadehamid/pearland-petroleum-corporation` owns the single canonical enterprise
world model (Refinery A v1, `ADR-0040`, `ADR-0041`, and `ADR-0053`, reconciled
at `ebc226f`). PPC integrates this repository's L0 contracts through a
commit-pinned provisional adapter (`ADR-0042`), isolates hidden world truth
under `evaluation/hidden/`, and plans to publish Refinery A's coherent
`observable/` OT L0 streams and native tag schedule via `WorldExportBundle` in
`WP-8B` (`ADR-0053`). From PPC's perspective, pre-world-model R2 prefixes
(`lagos-chem-l0/`) are classified as `LEGACY_PRE_WORLD_MODEL` and are never
moved or deleted by PPC. See
[LSC-REF-001](docs/LSC-REF-001_Technology_Roles_and_Reuse_Assessment.md#2026-11-26-ppc-baseline-update).

## Repository layout

| Path | Responsibility |
| --- | --- |
| `docs/` | Numbered project documents, learning guides, and document index |
| `docs/archive/` | Superseded design alternatives |
| `docs/history/` | Dated session records |
| `src/scada_harmonizer/` | Python package and finalized component code |
| `config/` | Site configuration and mapping bindings |
| `docker/` | Infrastructure configuration |
| `notebooks/` | Marimo learning notebooks |
| `tests/` | Tests and small deterministic fixtures |
| `scripts/` | Shared verification and facts tools |
| `data/` | Ignored local scratch data |
| `reference/` | Local-only reference material; its README is tracked |

The charter governs project definitions. `HANDOFF.md` section 2 owns current
status. Document history does not change either authority.

## Development

Use `uv` for Python project management. Run `scripts/check.sh` for the repository
gates; CI and the pre-push hook call the same script. Figures and searches come
from `scripts/facts.py`. See [the development guide](docs/DEVELOPMENT.md).

## License

[MIT](LICENSE)
