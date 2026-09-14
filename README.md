# open-aidlc

An open development lifecycle, AI driven and human gated.

## What this is

A template repository, carrying the structural decisions and the general steps that take an idea to a product, and then to what you learn from running it. It is a frame rather than a method: the gaps it leaves are meant to be filled with whatever processes you already use, and what it holds constant is where the judgement stays, so you get the speed of an agent without handing over the parts of the work that should stay yours.

## The lifecycle

Three cycles, nested. Each turns at its own rate.

| Cycle | Turns | Steps | Ends with |
|---|---|---|---|
| development | per change | intent → spec → review → task → review → archive | `openspec/specs/` updated |
| delivery | per release | integration → release → operation | something a person can run |
| learning | when evidence exists | signals → learning → next intent | a new intent |

An agent drafts the specification and writes the code. A person approves the specification before anything is implemented, and approves the code before it is kept. Those two gates are the lifecycle; everything else is arrangement.

Only development is specified. Delivery and learning are named so that archiving a change is not mistaken for shipping, and shipping is not mistaken for learning. Their steps stay undefined until there is a real release to describe, because writing the procedure before running it once is inventing it.

The full procedure is [`docs/guides/lifecycle.md`](docs/guides/lifecycle.md).

## What is already decided

| ADR | Decision |
|---|---|
| [0000](docs/adr/0000-use-madr-for-decision-records.md) | MADR 4.0.0 for decision records |
| [0001](docs/adr/0001-adopt-an-agentic-development-lifecycle.md) | Adopt an agentic development lifecycle |
| [0002](docs/adr/0002-use-specs-as-the-development-contract.md) | Use specs as the development contract |
| [0003](docs/adr/0003-write-documentation-in-markdown-and-mermaid.md) | Write documentation in Markdown and Mermaid |
| [0004](docs/adr/0004-structure-the-repository-by-concern.md) | Structure the repository by concern |

All five are tagged `candidate-standard`, which means they are meant to travel but have not been proven by long use. Each says in its *Confirmation* section what would validate it and what would sink it. You are adopting something in trial, and the records say so rather than hiding it.

ADR-0004 is the one you may not want. A repository that will only ever hold one application pays for `apps/` and `packages/` without collecting on them. Declining it means writing the ADR that supersedes it with the layout you chose instead, which is the mechanism these records already have. Nothing else here depends on the answer.

## Folder structure

```
product/       what this is, who it is for, what it is made of
openspec/      what the system does today, and what is about to change
docs/
  adr/         decisions and what they rejected
  guides/      repeatable procedures
.claude/       skills local to this repository

               not yet created:
apps/          one directory per application
packages/      code shared between applications
tools/         scripts
```

[ADR-0004](docs/adr/0004-structure-the-repository-by-concern.md) carries the full layout and the reasoning for arranging it this way.

## Getting started

**1. Install the OpenSpec CLI and initialise it.**

The lifecycle assumes it. Without it, the `spec` and `archive` steps describe something you cannot execute.

```bash
openspec init
```

This generates `openspec/`, the skills under `.claude/skills/openspec-*`, and the commands under `.claude/commands/opsx/`. Do not copy those from anywhere; let the CLI create them so they match the version you installed.

To see what the CLI eventually produces, [`openspec/changes/archive/_example-mark-an-item-done/`](openspec/changes/archive/_example-mark-an-item-done/) is a worked example of the four artifacts an archived change carries, written by hand for a toy product. Read it, then delete the directory.

**2. Fill in what is yours.**

| File | What to do |
|---|---|
| `product/domain.md` | Write your glossary. The heading explains the discipline; the entries are yours. [Matt Pocock's `domain-modeling` skill](https://github.com/mattpocock/skills/tree/main/skills/engineering/domain-modeling) does this well, with one divergence the file names. |
| `product/principles.md` | Write your principles. Each one must reject something tempting. |
| `product/vision.md` | What this is and who it is for. |
| `openspec/config.yaml` | Replace the `context` block with pointers to your own files. |
| `AGENTS.md` | Fill the sections marked as needing a pointer. |
| `LICENSE` | Your name, or your own licence. |

**3. Record your first decisions.**

`docs/adr/` already holds five, covering the method itself. Yours start at `0005`. Copy [`_template.md`](docs/adr/_template.md) rather than reconstructing the structure from another record.

## License

[MIT](LICENSE)
