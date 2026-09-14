# Mark an item done

Closes #1.

## Why

A list that only grows is a worse notebook. The one thing a person does with an
item after writing it is finish it, and today there is no way to say so.

## What changes

An item carries a done state. A person marks an item done, and marks it not done
again if they were wrong.

## Out of scope

- Removing an item. Marking done is not deleting, and deletion is its own change.
- Ordering, filtering or hiding done items. The list shows everything in the order it was written; how it is presented is a later question.
- Any record of when an item was marked. A timestamp is a new term in the glossary and this change does not add one.
