# Changelog

What each release of the template changed in the method, and what a repository that adopted an earlier release has to do about it. Releases are tagged `vX.Y.Z`.

Every change to a `candidate-standard` record says its **migration impact**, one of:

- **None:** wording only; nothing to do.
- **Clarified:** the decision stands, stated more precisely; reread it.
- **Reversed:** the decision changed; an adopter who followed it has something to undo, named in the entry.

## Unreleased

### Removed

- `openspec/`, its worked example, the OpenSpec section of `AGENTS.md` and the step that installed the CLI, following ADR-0002. ADR-0000, ADR-0004 and the ADR README point at PRDs and tests instead of `openspec/specs/`. **Migration impact: clarified** for those three records.

### Changed

- **ADR-0001** is now *Adopt a lifecycle from bet to learning*, and `docs/guides/lifecycle.md` describes its six steps: frame, decide, specify, build, ship, learn. The three nested cycles specified only the change, so a product could pass every review and still not be the one wanted; the unit is now a bet with a hypothesis and a metric fixed when a person decides to invest. **Migration impact: reversed.** Work in flight is framed as a brief before its next change; the brief's contents are in the guide, and a template follows once one has been carried through Learn.
- **ADR-0002** is now *Use living PRDs as the product contract*: one PRD per part of the product in `product/prds/`, edited before the code, instead of OpenSpec's specs and change proposals. A product specified one change at a time can satisfy every spec and still not be the one wanted. **Migration impact: reversed.** Describe what `openspec/specs/` holds as PRDs, then remove `openspec/` and the skills and commands `openspec init` generated.
- **ADR-0000:** records tagged `candidate-standard` are edited in place and recorded here, instead of being superseded by new records. Untagged records stay immutable. **Migration impact: reversed.** A repository that superseded one of the method's records can keep its own record; nothing forces the switch.

## [0.1.0] - 2026-09-14

The first release: the lifecycle, specs as the development contract, the repository layout, MADR records, and the product files a repository fills in.
