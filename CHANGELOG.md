# Changelog

What each release of the template changed in the method, and what a repository that adopted an earlier release has to do about it. Releases are tagged `vX.Y.Z`.

Every change to a `candidate-standard` record says its **migration impact**, one of:

- **None:** wording only; nothing to do.
- **Clarified:** the decision stands, stated more precisely; reread it.
- **Reversed:** the decision changed; an adopter who followed it has something to undo, named in the entry.

## Unreleased

### Changed

- **ADR-0000:** records tagged `candidate-standard` are edited in place and recorded here, instead of being superseded by new records. Untagged records stay immutable. **Migration impact: reversed.** A repository that superseded one of the method's records can keep its own record; nothing forces the switch.

## [0.1.0] - 2026-09-14

The first release: the lifecycle, specs as the development contract, the repository layout, MADR records, and the product files a repository fills in.
