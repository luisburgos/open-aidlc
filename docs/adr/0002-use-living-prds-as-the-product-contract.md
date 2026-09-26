---
status: accepted
date: 2026-09-25
tags: [candidate-standard]
---

# Use living PRDs as the product contract

## Context and Problem Statement

The lifecycle ([ADR-0001](0001-adopt-a-lifecycle-from-bet-to-learning.md)) needs, in its Specify step, something between a decided bet and its implementation that says what the product does. Handed an intent alone, an agent fills the gaps in code, where they are most expensive to reverse. But a contract written one change at a time can be precise about every change and still add up to a product nobody wanted, because nothing describes the product as a whole.

What form does the contract between the product and its implementation take?

## Decision Drivers

* What the product does now is readable without reading the code.
* A change is measured against the product as a whole, not appended to a record of changes.
* Ambiguity is resolved before implementation, not discovered in review.
* A behaviour is described once, not in a proposal and again in a record of current truth.

## Considered Options

* **Living PRDs**: one per part of the product, in `product/prds/`, edited before the code that changes it
* **[OpenSpec](https://github.com/Fission-AI/OpenSpec)**: `specs/` for current truth, accumulated from `changes/` proposals through propose, apply and archive
* **[GitHub Spec Kit](https://github.com/github/spec-kit)**: requirements, design and task files generated per change
* **Issues as the contract**: a GitHub issue carries the spec, and the code closes it

## Decision Outcome

Chosen option: "Living PRDs", because

* A PRD is written as the product, with its flows, edge cases and acceptance criteria, so a change is checked against what the product should be rather than against the code.
* It holds current behaviour, which is what OpenSpec's `specs/` was for, without a layer of proposals that repeats every edit a second time.
* Editing the PRD first, in its own pull request, is the review before implementation, and its acceptance criteria become the tests.
* OpenSpec's `specs/` accumulate from changes, so they record whatever the changes added; a product built that way can satisfy every spec and still not be the one wanted. Spec Kit generates phases this lifecycle does not run. Issues close, and leave no account of current behaviour.

### Consequences

* Good, because the product is described once, in the words of `product/domain.md`, and every change starts from that description.
* Bad, because a change of behaviour takes two pull requests, the PRD edit and then the code.

### Confirmation

Validated when a build is used and what it does is what its PRD says and what was wanted, without either being rewritten afterwards to match the other.

Sunk if PRDs are edited after the code to describe what was built, or if they fill with changes rather than with the product. Either means the contract is being narrated rather than used.

## More Information

A PRD follows [`product/prds/_template.md`](../../product/prds/_template.md), and how one is drafted is the `writing-prds` skill of the `contributing` plugin that `.claude/settings.json` declares.
