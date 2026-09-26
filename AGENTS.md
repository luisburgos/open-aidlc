# Agent instructions

Operating rules for agents working in this repository. Harness-agnostic; a harness-specific file such as `CLAUDE.md` points here rather than repeating it.

## Decision records

ADRs follow [`docs/adr/README.md`](docs/adr/README.md). **Read it before writing one**, and copy [`docs/adr/_template.md`](docs/adr/_template.md) rather than reconstructing the structure from memory or from another ADR.

The README settles which sections a record uses and how long it runs. How it should read is the `writing-adrs` skill, which exists because structure alone does not prevent the usual failure: writing three times as much as the decision needs.

The `writing-adrs` skill carries that procedure. It comes from the `contributing` plugin, which [`.claude/settings.json`](.claude/settings.json) declares; if it is not available, say so rather than writing the record without it. Use it rather than working from the README alone. A mistake caught in review here that it did not prevent is written down in this section.

## Domain model

The vocabulary of the product is [`product/domain.md`](product/domain.md). It is a glossary and nothing else: one entry per term, one or two sentences saying what the thing is, and an `_Avoid_` line naming the words not to use for it. No fields, types, storage, behaviour, or screens. Behaviour goes to PRDs, decisions to `docs/adr/`.

Read it before drafting a PRD or starting a change. A change that needs a new term, or an existing one to mean something else, edits the glossary as its own act and says so.

A change also names the term it builds: which entry it makes real or extends, and why that one before any other still unbuilt. A change that can name none is not ready. Reading the glossary is not the same as building toward it, and only the second is visible from outside the change.

Root [`CONTEXT.md`](CONTEXT.md) only points there, for tooling that looks for a glossary at the root. Do not add terms to it.

## Product requirements

What the product does is its PRDs, in [`product/prds/`](product/prds/), one per part of the product, numbered in order: who it serves, its flows, edge cases, acceptance criteria, and what it leaves for later. [ADR-0002](docs/adr/0002-use-living-prds-as-the-product-contract.md) says why. A PRD builds on [`product/vision.md`](product/vision.md) rather than restating it, and [`product/principles.md`](product/principles.md) filters every decision in it.

Read the PRD a change belongs to before starting it. A change the PRD does not describe edits the PRD first, as its own pull request, merged before the code. A new part of the product starts a new PRD, copied from [`product/prds/_template.md`](product/prds/_template.md) rather than from another PRD.

The `writing-prds` skill carries how a PRD is drafted and when it is done. It comes from the `contributing` plugin, which [`.claude/settings.json`](.claude/settings.json) declares; if it is not available, say so rather than drafting without it.

## Writing for review

The `writing-pull-requests` skill carries the procedure for a pull request description. It comes from the `contributing` plugin, which [`.claude/settings.json`](.claude/settings.json) declares; if it is not available, say so rather than writing the description without it. It guards against the register failures an agent-authored description falls into: narrating the authoring session, explaining how the change evolved, and restating what the diff already shows. A failure caught in review here that it did not prevent is written down in this section.

## Diagrams

Mermaid, in fenced blocks inside Markdown, so GitHub renders them. No forced colours: the default theme adapts to light and dark, and hard-coded hex values break one of the two.

Do not write `.mmd` files, and do not commit rendered SVG or PNG for diagrams that Mermaid can express.

## Writing for readers outside this repository

Everything committed here is written for someone who can see only this repository. Private files, other repositories, and this conversation are not available to them.

So: **nothing outside this repository can be cited as evidence, context, or justification.**

- No appeals to preferences, rules or conventions held elsewhere. A reader cannot follow them, cannot verify them, and learns only that unseen rules govern decisions here.
- No "the author's other projects", no "as we discussed", no "per the usual convention". Where such a source genuinely shaped a decision, state the substance of it and let that stand on its own.
- A decision that needs an invisible authority to justify it is not yet justified. Make the argument from what is in the repository, or reconsider the decision.

This holds whether the repository is private or public. Privacy is a setting, and it changes.

## Writing

No em dashes in prose. Rewrite the sentence rather than substituting punctuation.

Do not hard-wrap prose in anything a renderer reflows: pull request bodies, issue bodies, release notes. One continuous line per paragraph. Commit messages are the exception and keep their ~72-character wrap.

## Commits and pull requests

Conventional Commits. Subjects and bodies in English, always, regardless of the language of the conversation.

No attribution lines: no generated-with trailers, no co-author trailers naming the agent.

Pull requests use [`.github/pull_request_template.md`](.github/pull_request_template.md). Delete every comment as you fill it in, and delete any section that has nothing to say rather than padding it.

<!--
  Sections to add as this repository grows:

  ## Architecture     — once a stack is chosen, with a pointer to the ADR that chose it
  ## Environments     — once there is more than one build configuration
  ## Testing          — how a task verifies itself, and what counts as evidence
-->
