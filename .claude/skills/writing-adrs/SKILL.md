---
name: writing-adrs
description: >
  Use when writing or reviewing an architecture decision record in this
  repository, or before creating any file under docs/adr/. Also use when another
  skill needs the register an ADR here is written in.
---

Structure comes from [`docs/adr/_template.md`](../../../docs/adr/_template.md); which sections to use and how long the record runs come from [`docs/adr/README.md`](../../../docs/adr/README.md). Both are read as part of writing one.

This skill is the **register** neither can enforce: a record can satisfy every structural rule and still fail its reader.

Write to be read by someone who has forgotten why, not by someone checking that a process was followed.

## The register

**A reason appears once.** Context says what is wrong. Drivers say what would make an option good. Decision Outcome says why this one won. The same argument in two of them is the most common defect, and the hardest to see while writing.

**Options are what someone might actually choose.** Weighing a published standard against two undocumented in-house conventions is not a comparison: those are prior art, not candidates, and comparing against local history reads as justifying a choice already made.

**Nothing outside this repository is evidence.** See [`AGENTS.md`](../../../AGENTS.md#writing-for-readers-outside-this-repository).

**A criterion that needs judgement says so.** "A reviewer will accept this" is not checkable. Mark it rather than dressing it as a condition.

**An expiry names its trigger.** "Revisit later" is not a condition. Where a decision has a foreseeable end, *Confirmation* says what would reopen it.

**A decision the glossary or a principle already made is not an ADR.** Before copying the template, ask whether any option survives `product/domain.md` and `product/principles.md`. If none does, the decision was spent when those were written, and the record would restate a definition with a "because" attached. The README's test, did you reject an alternative, is answered before drafting, not by drafting.

## Gotchas

<!--
  This section is empty on purpose.

  It holds the mistakes made in THIS repository, written down after they happen,
  with enough specificity that the next author recognises the shape. A gotcha
  borrowed from somewhere else teaches nothing, because the reader cannot check
  it against a record they can open.

  Add one when a review catches something the register above did not prevent.
  Name the record, say what went wrong, and say what it cost.

  One that will almost certainly belong here eventually:

  - **The index row is forgotten.** It goes in `docs/adr/README.md` in the same commit.
-->

## Done when

No reason is stated in two places, every optional section present carries something the reader could not infer, and the record arrives by pull request rather than a direct commit.
