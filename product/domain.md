# Domain

The words this product is made of, and the one name each thing goes by. Every PRD is written in this vocabulary; a change that needs a term this document lacks, or means differently, changes this document first and says so.

A glossary and nothing else. What each thing is, not how it behaves, how it is stored, or how it is shown. Behaviour belongs in PRDs, decisions in `docs/adr/`.

## How an entry is written

One or two sentences saying what the thing is. Then an `_Avoid_` line naming the words that must not be used for it, which is the half that does the work: a glossary without it records a preference, and a glossary with it settles an argument before it happens.

Group entries under headings when there are enough to need them. The example below is the shape, not a suggestion; delete it.

```
### Grouping heading

**Term**:
What the thing is, in one or two sentences.
_Avoid_: the near-synonyms someone would otherwise reach for
```

## Building this out

Writing a glossary is easier as a discipline than as a document. [Matt Pocock's `domain-modeling` skill](https://github.com/mattpocock/skills/tree/main/skills/engineering/domain-modeling) (MIT) is that discipline: it challenges a term the moment it conflicts with one already written, sharpens vague words into a single canonical one, stress-tests relationships with concrete scenarios, and captures each term as it is resolved rather than in a batch afterwards.

Its entry format is the one above, so what it writes fits here unchanged.

**One divergence to hold it to.** The skill writes the glossary to a root `CONTEXT.md`. Here that file is a pointer and nothing else, and the glossary is this one. Tell it to write to `product/domain.md`, or it will put terms where `AGENTS.md` says they must not go.

## Language

<!--
  Your terms go here. Start with the things a person using the product would
  name out loud, not the things the code will need.

  A term earns a place when two people could reasonably call it two different
  things. If there is only one obvious word for it, the glossary does not need
  the entry.
-->
