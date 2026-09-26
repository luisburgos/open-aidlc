---
status: accepted
date: 2026-09-14
tags: [candidate-standard]
---

# Use MADR for architecture decision records

## Context and Problem Statement

This repository will accumulate decisions that outlive the conversations that produced them, and some of those decisions will reject alternatives that were genuinely good. Both a human returning in six months and an agent starting a fresh session need that reasoning, or they reopen settled questions.

Which format and structure should these records follow?

## Decision Drivers

* A published standard needs no teaching. An agent recognises one; a house convention must be re-explained every session.
* Rejected alternatives must land in the record by construction, not by the author remembering.
* Readable on GitHub without tooling, greppable by an agent.
* A decision with a foreseeable expiry needs somewhere to name what would reopen it.

## Considered Options

* **[MADR](https://adr.github.io/madr/) 4.0.0** — Markdown Architectural Decision Records, versioned and actively maintained
* **[Michael Nygard's template](https://www.cognitect.com/blog/2011/11/15/documenting-architecture-decisions)** — the original 2011 format, about as small as an ADR gets
* **A house convention** — sections chosen for this repository
* **No ADRs** — decisions live in commit messages only

## Decision Outcome

Chosen option: "MADR 4.0.0, minimal variant", because

* It makes **Considered Options** a required section, which Nygard's *Context* permits but does not oblige.
* It is published and maintained, so onboarding a person or an agent is a link rather than an explanation.
* It is the maintained descendant of Nygard's format, not a competitor to it.
* A house convention fails the first driver outright, and *No ADRs* fails the agent audience: a decision recorded only in a commit message will not be found, and will be reopened.

### Confirmation

An ADR complies if it carries `status`, `date` and `tags`, the three required sections, and a filename matching `NNNN-title-with-dashes.md`. Review is the check; there is no tooling.

This ADR is tagged `candidate-standard`, so it must also be judged. MADR is validated once roughly half a dozen ADRs have been written at the moment of deciding without the template being fought. It is sunk if the sections push toward recording conventions as decisions, or if authors route around the template. Leaving it unjudged is the worst of the three outcomes.

## More Information

Two rules are adopted alongside the template. MADR supplies a `status` field but says nothing about either.

**A `candidate-standard` record is edited; any other is immutable once accepted.** A tagged record is part of the template, so a correction is made to it rather than stacked beside it: an adopter should read five records to learn what five say, not fifteen. Each edit is recorded in [`CHANGELOG.md`](../../CHANGELOG.md) with its migration impact. An untagged record is a decision about what is being built, and why it was made given what was known then: one that stops applying is superseded by a new one, never edited or deleted, and the old `status` becomes `superseded by ADR-NNNN`. What the product does now lives in its PRDs.

**Name the expiry condition.** Where a decision has a foreseeable end, say what would trigger reopening it. "Revisit later" is not a condition.

Writing guidance, including what to omit, is in [README.md](README.md). The blank is [_template.md](_template.md).
