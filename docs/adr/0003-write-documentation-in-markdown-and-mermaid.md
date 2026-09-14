---
status: accepted
date: 2026-09-14
tags: [candidate-standard]
---

# Write documentation in Markdown and Mermaid

## Context and Problem Statement

This repository's documentation has two audiences with one requirement in common. A person reads it on GitHub, in the browser, without checking anything out. An agent reads and edits it as text, and must be able to change a diagram without opening a drawing tool.

A format that neither renders on GitHub nor survives a text edit fails both at once, however good it is at describing the thing.

What formats do prose and diagrams use here?

## Decision Drivers

* Renders on GitHub with no tooling and no local checkout.
* Editable by an agent as text, diagrams included.
* One source, not a source plus a generated artifact that can drift from it.

## Considered Options

Prose:

* **Markdown** — rendered natively by GitHub
* **Self-contained HTML** — full control of layout and styling

Diagrams:

* **[Mermaid](https://mermaid.js.org/)** — fenced blocks, rendered natively by GitHub
* **[BPMN](https://www.bpmn.org/)** — a process notation with participants, gateways, message and timer events
* **Committed SVG** — drawn elsewhere, checked in
* **Exported PNG** — same, rasterised

## Decision Outcome

Chosen option: "Markdown and Mermaid", because

* Both render on GitHub natively, which no other option on either list does. BPMN needs a plugin, a preprocessor or a browser extension, none of which help a reader who follows a link.
* A Mermaid diagram is text in the file beside the prose, so changing a step is an edit rather than a regeneration. SVG and PNG both split one meaning across a source and an artifact, and nothing keeps the two aligned.
* Self-contained HTML is a defensible choice, and loses on the rendering constraint alone rather than on quality. It buys layout control this repository has no use for, at the cost of the one property both audiences need.
* GitHub sanitises embedded SVG, stripping elements, and the `<marker>` and `<defs>` a hand-drawn diagram relies on are among them.

### Consequences

* Bad, because Mermaid decides its own layout. A diagram that wants a specific arrangement cannot always have one.
* Neutral, because BPMN is the better notation for what the lifecycle actually is. It has participants, gateways, and message events for the waiting between a human and an agent, and this lifecycle has all three.

### Confirmation

Validated if diagrams stay legible in Mermaid as the lifecycle grows, and nobody reaches for a drawing tool.

BPMN is deferred, not rejected. It returns for reconsideration when a diagram here needs pools, message events, or gateways that Mermaid cannot express, and the cost of a generated artifact becomes worth paying. Reconsidering it means a new record superseding this one, not an exception.

## More Information

Operating rules live in [`AGENTS.md`](../../AGENTS.md): Mermaid in fenced blocks, no forced colours, no `.mmd` files.
