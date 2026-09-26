---
status: accepted
date: 2026-09-14
tags: [candidate-standard]
---

# Adopt an agentic development lifecycle

## Context and Problem Statement

Conventional lifecycles assume each phase is performed and signed off by the team that owns it. When agents do the work, that assumption breaks: authoring stops being the constraint, review becomes it, and a decision left unreserved is taken by whoever is executing rather than by whoever should.

What is wanted is a lifecycle that agents can execute and a person can follow, concrete enough to name where each turn starts and ends, and shaped so that adding people later extends it rather than replaces it.

How should work be organised, from intent through to something a person can run?

## Decision Drivers

* **Legible to both.** An agent must be able to execute a turn without interpretation, and a person must be able to follow one without reading the code.
* **Review is the bottleneck.** A lifecycle that raises output per review makes throughput worse, not better.
* **Decisions are reserved explicitly.** Anything not named as a human gate is taken by whoever is executing.
* **Concrete turns.** Each cycle names what starts it and what ends it, so "done" has one meaning rather than three.
* **Built to scale out.** Work is organised so that a second person, or a second agent, joins without the model changing shape.
* **No invented phases.** What cannot yet be described honestly is named and left unspecified.

## Considered Options

* **[AI-DLC](https://www.ibm.com/think/topics/ai-dlc)** — Inception, Construction, Operation, with mob rituals per phase
* **An agentic product engineering handbook** — vision through to learnings, an initiative as the unit of work
* **[GitHub Spec Kit](https://github.com/github/spec-kit) or Kiro** — requirements, design and task phases, generated as files
* **A conventional SDLC** — plan, build, test, release, with AI applied inside the build phase
* **Three nested cycles** — development, delivery and learning, composed from the above

## Decision Outcome

Chosen option: "Three nested cycles", because

* Nesting is what the alternatives lack. Archiving a change is not a release, and a release is not a learning; collapsing them is what gives "done" three meanings.
* Each cycle is a turn with a named start and end, so a turn can be handed to an agent, to a person, or to several at once without renegotiating what it covers.
* Applying AI inside a conventional build phase is the failure the [measured 20% slowdown](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/) describes: one phase gets faster and the surrounding ones absorb the gain.
* The published options each fix a shape. AI-DLC binds phases to four staffed roles; the handbook's unit is a bet carrying a hypothesis and a metric; Spec Kit and Kiro generate files for phases not being run. Composing leaves the shape free to change as the project does.

The cycles, innermost first:

| Cycle | Turns | Steps | Ends with |
|---|---|---|---|
| development | per change | intent → spec → review → task → review → archive | `openspec/specs/` updated |
| delivery | per release | integration → release → operation | something a person can run |
| learning | when evidence exists | signals → learning → next intent | a new intent |

How each turn runs is in [docs/guides/lifecycle.md](../guides/lifecycle.md).

### Confirmation

Only the development cycle is specified. Delivery and learning are named so that archiving is not mistaken for shipping, but their steps stay undefined until there is a real release to describe and signals to read. Writing them now would be inventing procedure.

The learning cycle needs users, which is the condition, not a date.

This decision is tagged `candidate-standard`. It is validated if a change can be traced from intent to archive without a step being skipped or improvised. It is sunk if the gates get bypassed under time pressure, which would mean the cycle describes an intention rather than a practice.

## More Information

The mechanism of the development cycle — how a spec is written, and in what format — is a separate decision, settled in [ADR-0002](0002-use-living-prds-as-the-product-contract.md).

Sources: [AI-DLC phases and artefacts](https://www.ibm.com/think/topics/ai-dlc), and the argument that redesigning the lifecycle beats accelerating one phase of it.
