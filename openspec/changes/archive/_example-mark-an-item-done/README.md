# This is an example. Delete it.

Not a real change. It exists so the four artifacts of an archived change can be
read before writing one, and it describes a toy product that has nothing to do
with whatever you are building.

**Delete this directory once you have read it.** Leaving it in place means every
later reader has to work out which changes are yours. The leading underscore in
the name is there to keep it sorted away from real changes, which are named for
the date they were archived, until you do.

## It was written by hand

A real change is produced by the OpenSpec CLI, not typed out. The CLI creates
the directory, generates each artifact from the change being proposed, and moves
it here when the change is archived:

```bash
openspec init                 # once per repository
```

Then propose, apply and archive through the commands the CLI installs for your
harness.

What follows is the shape those commands produce, so nothing here should be
copied as a starting point. Run the CLI and let it make the real one.

## What to look at

| File | What it carries |
|---|---|
| `proposal.md` | the intent, and what the change refuses to touch |
| `design.md` | the choices made before implementing, and the alternatives rejected |
| `specs/items/spec.md` | the behaviour as `WHEN`/`THEN` scenarios |
| `tasks.md` | the work, one session each, and how each was verified |

Three things are worth noticing, because they are what the rest of this
repository asserts and this example demonstrates.

**The fourth scenario earns its place.** Marking an item that is already done is
not an obvious case, and it is exactly the kind of question gate 1 exists to
settle. Without it, whoever implements the change decides alone whether that is
an error, a no-op, or something that updates a timestamp.

**`design.md` rejects things out loud.** It says why there is no history and why
marking and unmarking are one requirement rather than two. That is what stops an
implementation inventing an event log nobody asked for.

**No artifact names a technology.** No database, no language, no screen. The
specification describes behaviour, and what implements it is decided later.
