---
name: writing-pull-requests
description: >
  Use when writing or rewriting a pull request description in this repository.
  Also use when another skill needs the register a description here is written
  in.
---

The sections come from [`.github/pull_request_template.md`](../../../.github/pull_request_template.md), and every comment in it is an instruction to delete that comment. This skill is the **register** the template cannot enforce.

An agent-authored description fails the same way every time: it narrates the session that produced the change instead of stating what a reviewer must act on. The diff is one click away and says what changed. A description earns its place by carrying what the diff cannot — what was deliberately left alone, what went unverified, and where to push back.

## The register

**No session narration.** A sentence that begins "writing this still produced something three times longer" tells a story from the authoring session. Six months later nobody knows what it referred to. State the fact instead.

**No evolution of the pull request itself.** *Review focus* is the usual casualty, filling with what changed between drafts a reviewer never saw. Give the current fact and why it is contestable.

**Each description is read alone.** "First of three", "as decided in #2". The one exception is a base branch other than the default, which a reviewer needs in order to read the diff.

**Purpose, not provenance.** "Each rule is a mistake already made here" says where a rule came from instead of what it prevents.

**No defending your own edits.** "This is a genuine question, not a rhetorical one" argues with an imagined objection.

**Bullets, not bolded paragraphs.** Five bold openers followed by prose is the same verbosity with better formatting. *Why this way* and *Evidence* are lists.

**Nothing outside this repository is evidence.** See [`AGENTS.md`](../../../AGENTS.md#writing-for-readers-outside-this-repository).

## Gotchas

<!--
  This section is empty on purpose.

  It holds the failures caught in review in THIS repository, written down as they
  happen. A gotcha borrowed from another repository teaches nothing, because the
  reader cannot open the pull request it came from.

  Add one when a description gets sent back for something the register above did
  not prevent.

  Three that commonly belong here:

  - **Second person creeps in.** "Your call", "worth disagreeing with now".
    Reviewer-directed phrasing belongs in Review focus, and even there as a fact.

  - **`Not verified` gets omitted when the news is bad.** It is the most useful
    line in the description. Lead it with `**Not verified:**` so it is not buried.

  - **A cross-reference to another pull request is almost always narration.**
    Check it against the base-branch exception before keeping it.
-->

## Done when

Every template comment is deleted, no section restates the diff, *Evidence* names at least one thing that was not verified, and *Review focus* makes sense to someone who has read no other pull request here.
