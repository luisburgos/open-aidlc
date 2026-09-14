---
status: accepted
date: 2026-09-14
tags: [candidate-standard]
---

# Use specs as the development contract

## Context and Problem Statement

The development cycle ([ADR-0001](0001-adopt-an-agentic-development-lifecycle.md)) names a spec between intent and implementation, but not what a spec is or where it lives. Handed an intent alone, an agent fills the gaps: which library, which error handling, how far the feature reaches. Those choices then arrive as code, which is the most expensive moment to reverse them.

Nothing yet holds what the system does today either, so each change would begin by reading the code to infer its own starting point.

What form does the contract between an intent and its implementation take?

## Decision Drivers

* Ambiguity has to be resolved before implementation, not discovered during review.
* What the system currently does must be readable without inferring it from code.
* A published format is recognised by an agent without being taught; a house format is re-explained every session.
* Proposed change and current truth must not be the same document, or a proposal quietly becomes a description.

## Considered Options

* **[OpenSpec](https://github.com/Fission-AI/OpenSpec)** — `specs/` for current truth, `changes/` for proposals, a propose/apply/archive state machine, slash commands for several agent harnesses
* **[GitHub Spec Kit](https://github.com/github/spec-kit)** — a fuller framework generating requirements, design and task files per change
* **A prompt template** — a house format for specs, no tooling
* **Issues as the contract** — GitHub issues carry the spec, code closes them

## Decision Outcome

Chosen option: "OpenSpec", because

* It separates `specs/` from `changes/`, which is the distinction the lifecycle needs and the only option that supplies it. Archiving merges a proposal into the record of current behaviour, so the record accumulates rather than resetting per change.
* Its requirement format is `WHEN`/`THEN` scenarios, which translate into tests directly rather than needing interpretation.
* It is published and installable, so no dialect has to be documented before an agent can follow it.
* Spec Kit generates files for phases this lifecycle does not run, and practitioners report it as heavier than the work it governs. A prompt template and issues both fail the same driver: neither leaves a readable account of current behaviour.

`openspec/` sits at the repository root rather than inside an application, so specs describe the product across every surface it grows.

User stories are not adopted alongside it. A story and a spec describe the same behaviour at different precision, and keeping both means writing each change twice.

### Confirmation

Validated when a change has run propose to archive and `openspec/specs/` describes behaviour that no one had to read code to discover.

Sunk if specs are written after the implementation to satisfy the process, or if `changes/` accumulates proposals that are never archived. Either means the contract is being narrated rather than used, and this is superseded by something lighter.

## More Information

The CLI is installed with `openspec init`, which generates `openspec/` along with the skills and commands its harness integration needs. Those generated files are refreshed by `openspec update` and are not edited by hand; a rule belonging to the repository goes in `openspec/config.yaml` or in `AGENTS.md`.
