---
status: accepted
date: 2026-09-25
tags: [candidate-standard]
---

# Adopt a lifecycle from bet to learning

## Context and Problem Statement

When agents do the work, authoring stops being the constraint and review becomes it, and a decision left unreserved is taken by whoever is executing. A lifecycle built around the change, where an intent becomes a spec and then code, reserves the right decisions about each change and none about which changes are worth making: a release can pass every review and still not be the product that was wanted.

How should work be organised, from the decision to build something through to what using it taught?

## Decision Drivers

* **Legible to both.** An agent executes a step without interpretation, and a person follows one without reading the code.
* **Decisions are reserved explicitly.** Anything not named as a person's decision is taken by whoever is executing, and the largest one is what to build at all.
* **A bet is judged, not assumed.** What a piece of work is expected to change is written down before it is built, so its use can say whether it did.
* **Concrete steps.** Each step names what starts it and what ends it, so "done" has one meaning.
* **No invented procedure.** What has not been done yet is named and left thin.

## Considered Options

* **From bet to learning**: an initiative frames a bet with a hypothesis and a metric, a person decides, PRDs and code follow, and a shipped build is judged against the bet
* **Three nested cycles**: development per change, delivery per release, learning when evidence exists
* **[AI-DLC](https://www.ibm.com/think/topics/ai-dlc)**: Inception, Construction, Operation, with mob rituals per phase
* **[GitHub Spec Kit](https://github.com/github/spec-kit)**: requirements, design and task phases, generated as files
* **A conventional SDLC**: plan, build, test, release, with AI applied inside the build phase

## Decision Outcome

Chosen option: "From bet to learning", because

* It reserves the decision the others leave to momentum: whether a piece of work is worth doing, taken by a person, with the hypothesis and the metric fixed from then on.
* Shipping and learning are steps with an output, a build in use and a written learning, rather than names for later, so a release is judged instead of assumed.
* The three nested cycles specified only the change, and a product built one reviewed change at a time can be exactly what every review approved and still not be wanted. AI-DLC binds phases to staffed roles, Spec Kit generates phases not being run, and a conventional SDLC speeds up one phase while the rest absorb the gain.

The six steps:

| Step | Who | Produces |
|---|---|---|
| Frame | agent drafts, person owns | a brief: the problem, the outcome it serves, a hypothesis and a primary metric |
| Decide | **person** | invest or not; the hypothesis and the metric are fixed |
| Specify | agent drafts, **person approves** | the PRD changes, each its own pull request, merged before code |
| Build | agent writes, **person reviews** | the code the PRDs describe |
| Ship | **person** | a build in use, and one issue for what its use shows |
| Learn | agent drafts, person owns | the evidence read against the hypothesis, written down |

How each step runs is [docs/guides/lifecycle.md](../guides/lifecycle.md). A fix that brings the product back to what its PRD says skips all of them.

### Confirmation

Validated when a bet is carried from Frame to Learn and its learning says whether the hypothesis held, without the hypothesis or the metric having moved after the decision.

Sunk if work reaches Build without a decision, or if Learn is skipped once a build ships, which would mean the lifecycle describes an intention rather than a practice.

## More Information

The contract used in Specify is [ADR-0002](0002-use-living-prds-as-the-product-contract.md). The shape of a brief is fixed in the guide by its contents; a template for it waits until one has been carried through Learn.
