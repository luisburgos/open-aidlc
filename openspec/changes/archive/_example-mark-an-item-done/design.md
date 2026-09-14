# Design

## Done is a property of the item, not a separate thing

An item is done or it is not. There is no event, no history, and nothing to read
except the current state, because nothing in the proposal asks a question that
history would answer.

This is the glossary's `Item` gaining a property, not a new term. No change to
`product/domain.md` is needed.

## Marking is reversible by the same act

The proposal asks for marking done and unmarking. These are one behaviour with
two directions rather than two behaviours, so the specification treats them as
one requirement with two scenarios.

Making them separate would allow a state that can be entered and not left, which
nothing here wants.
