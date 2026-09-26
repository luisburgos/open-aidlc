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

## Claims

A claim in a product document, whether a brief, a PRD or the journey, is one of four kinds:

- **FACT:** backed by something a reader can check: this repository, a test, or what was seen in use.
- **ASSUMPTION:** taken as true without evidence, on purpose, to make progress.
- **HYPOTHESIS:** a causal claim that can be tested and has not been.
- **RECOMMENDATION:** a judgement about what whoever owns the product should decide.

A claim with no label is a FACT, so every other kind is labelled where it is written, in capitals. A FACT is labelled only when its evidence is the point, and then names the evidence. A gap is not a claim: it is `TBD` with a one-line note.

Never write a hypothesis as a fact, and never invent evidence.

## Files and issues

What must outlast the work it came from is a file in this repository. What exists only while work is in flight is an issue.

- **Files:** the vision, principles, glossary and journey in `product/`; PRDs in `product/prds/`; each bet's brief and what it taught; decisions in `docs/adr/`.
- **Issues:** feedback on a build, efforts not yet built, and the tracking of work in flight. A tracking issue lists its pull requests as a checklist in its body, not as a sub-issue each.

An issue that holds something durable hands it to a file before it closes.

## Feedback

Feedback from using a build lives in one issue per build, labelled `feedback` and titled "Feedback on <version> (<build>)": what was seen, one section per day of use, and a checklist, "New from this feedback", of the fixes and backlog issues each point became. Only one is open at a time: the issue of the latest build shipped.

A quick fix is a pull request that references the feedback issue. An effort it raises is a sub-issue of its own, and gets a PRD when it is built.

When the next build ships, its feedback issue opens and the previous one closes, with every point in one of two states:

- **Shipped:** checked, with the pull request that did it. A checked point is always in the build that follows.
- **Deferred to backlog:** moved out of the checklist to a section of that name, linking its own issue. A point without one gets one before the close. A point decided against is deferred too, and its issue is closed as not planned.

From then on the backlog issue owns the point. A closed feedback issue is not edited again: it records what happened with that build, not where each point stands now. Bringing a deferred point into the open feedback issue is the product owner's decision, made by adding it to that issue's checklist.

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

A pull request is squash-merged: it lands on `main` as one commit titled with its Conventional Commit and its number, which is what a generated changelog reads, one line per pull request. Never merge with a merge commit, which puts every commit of the branch on `main`. How the entry of a release is generated is the `generating-changelogs` skill of the `contributing` plugin.

A pull request is atomic: it does one thing, and a description that needs "and also" is two pull requests.

- A change to a PRD, the glossary or another product document is its own pull request, merged before the code that builds it.
- A refactor changes no behaviour; a fix or a feature goes in a separate pull request.
- Removing what is no longer used comes before adding what replaces it.
- Two pull requests that change the same lines are not open at once: the second waits for the first to merge.

<!--
  Sections to add as this repository grows:

  ## Architecture     — once a stack is chosen, with a pointer to the ADR that chose it
  ## Environments     — once there is more than one build configuration
  ## Testing          — how a task verifies itself, and what counts as evidence
-->
