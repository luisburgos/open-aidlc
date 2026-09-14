---
status: accepted
date: 2026-09-14
tags: [candidate-standard]
---

# Structure the repository by concern

## Context and Problem Statement

This repository holds decisions, guidance, agent instructions and specs before it holds a single line of application code. Whatever gets built here will eventually be one surface among several, and the product's own definition belongs to none of them.

Organising by technology puts a reader in the position of knowing what something is written in before they can find it. Splitting per surface into separate repositories puts the product's definition in one of them, or in all of them.

How should the repository be laid out, and where does each kind of artifact live?

## Decision Drivers

* A reader who knows what they are looking for, and nothing about the stack, should know where to look.
* Artifacts with different lifetimes should not be neighbours: a vision statement changes yearly, a change proposal weekly.
* What is true of the product must sit above any surface that implements it.
* Directories should appear when something fills them, not in anticipation.

## Considered Options

* **By concern, one repository** — top-level directories named for what they hold, applications under `apps/`
* **By technology** — directories named for the stack, such as `swift/`, `web/`, `docs/`
* **Multiple repositories** — one per surface, product definition duplicated or arbitrarily housed
* **Flat** — everything at the root, conventional filenames

## Decision Outcome

Chosen option: "By concern, one repository", because

* Every artifact has one obvious home decided by what it is, not by how it is built.
* Product definition, specs and decisions sit at the root, above `apps/`, which is what stops them belonging to the first surface by accident when a second one arrives.
* Technology directories force a reader to know the stack before they can navigate, and the split is unstable: an application that adds a package in one language and a build tool in another lands in two places.
* Separate repositories fragment exactly what must be shared, and flat stops working at the first dozen files.

The layout:

| Path | Holds | Lifetime |
|---|---|---|
| `product/` | vision, principles, domain glossary | durable |
| `openspec/` | `specs/` current behaviour, `changes/` proposals | accumulating |
| `docs/adr/` | decisions and what they rejected | immutable |
| `docs/guides/` | repeatable procedures | revised with use |
| `apps/` | one directory per application | per surface |
| `packages/` | code shared between applications | appears with the second application |
| `tools/` | scripts | as needed |
| `.claude/skills/` | skills local to this repository | with the conventions they carry |

A directory is created when it has content. `apps/`, `packages/` and `tools/` are named here and do not exist yet, because nothing fills them until something is built.

### Consequences

* Good, because a second surface is added without moving anything that already exists.
* Bad, because the root carries more directories than a single-application repository needs, and the cost is paid from the first day while the benefit arrives with the second surface.
* Neutral, because a repository that never grows a second surface loses nothing by this layout beyond a `packages/` that stays empty.

### Confirmation

Validated when a second surface is added and nothing under `product/`, `openspec/` or `docs/` has to move.

Sunk if artifacts keep landing somewhere other than where this says, which would mean the categories match the writing less well than the layout claims.

**This is the one decision here that a project may not want.** A repository that will only ever hold one application pays for `apps/` and `packages/` without ever collecting on them, and a team with an established layout of its own has already answered this question. Declining it is not an exception to this record, it is a new record superseding it: write the ADR that states the layout actually chosen, and set this one's status to `superseded by ADR-NNNN`. The other decisions in this repository do not depend on the answer, so superseding this one costs nothing elsewhere.

## More Information

Execution lives in issues and milestones rather than a tracked directory. A backlog file is a worse issue tracker than the one already attached to the repository, and a second source of truth for what is in progress.
