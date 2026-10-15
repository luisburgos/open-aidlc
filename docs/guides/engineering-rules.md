# Engineering rules

The laws the code, its design and the documents that describe it are held to, whatever the stack. Each names a well-known law of software engineering; what binds here is its operational rule, not the law's wider reading. A repository's decision records add the rules of its stack on top of these.

They are applied in review at Build and in every audit. A change or a design that breaks one is reverted, whatever it improves elsewhere.

## Rules

| # | Law | Operational rule | How it is verified |
|---|---|---|---|
| E1 | Goodhart's law: when a measure becomes a target, it ceases to be a good measure | A score, a rubric or a check is a mirror, not the target. Every change names its real driver: a behaviour a PRD asks for, a defect, or a decision record. A change whose only driver is a better score is rejected. | The pull request names its driver |
| E2 | YAGNI: do not add what is not needed yet | Every abstraction (interface, module, layer, registry) has at least two real uses today, or sits on a boundary with I/O or nondeterminism (storage, network, clock, ids, preferences), where the test double counts as the second use. | Review and audit |
| E3 | KISS | Of two designs with the same behaviour, the one with fewer pieces wins. A size limit is an alarm that asks for a reason, not a gate that forces a split. | Review |
| E4 | Gall's law: a complex system that works evolved from a simple system that worked | A change lands as an incremental pull request on code that works. Nothing needs a rewrite before it can be released. | Pull request size; every merge releasable |
| E5 | The second-system effect | A rebuilt or second implementation reproduces what the first proved before it adds mechanisms of its own. | Review |
| E6 | Premature optimisation (Knuth) | No tool, check or rule for a risk that has not been observed. Once a risk is observed with a consequence in data, money, security or a decision record broken in the code, a check for it is the answer, and existing tools are extended first. | The check cites the observation that justified it |
| E7 | Pareto | An audit stops at the findings that change a decision. The last fraction of any score costs more than the rest and is mostly noise. | The audit's stopping point is stated |
| E8 | Sunk cost | Reverting is cheap. A change that breaks these rules is discarded whatever it cost, keeping only its factual corrections. | History |
| E9 | The map is not the territory | An audit is checked against the code as it runs, not only against the documents that describe it. | Each audit names the code it read |
| E10 | DRY | Each fact lives in one place: a rule in one decision record or guide, a derivation in one function. Everything else refers to it. | Contradictions found in audit |
| E11 | Tesler's law: complexity cannot be removed, only moved | The domain's own complexity is neither hidden nor simplified away. Only the complexity the process added is removed. | Review |
| E12 | SOLID (Martin) | A type or module has one reason to change; behaviour is extended by adding code, not by editing what callers rely on; a substitute keeps its contract; callers depend on the narrow interface they use; policy depends on abstractions it owns, not on details. Read under E2: no interface exists only to satisfy a letter of SOLID. | Audit |
| E13 | The Law of Demeter | A unit talks to its immediate collaborators. A view receives the state it shows, not the state of the whole application. | Audit |
| E14 | Broken windows (Hunt and Thomas) | A change follows the decision records, never the code around it where the two disagree. Code that breaks a decision record is left as it is, outside the change, and reported as a finding; it is not a pattern to copy. | Review; the repository's checks run on the lines a change touches |

## Why E14 is here

The other thirteen are laws of design. E14 is a law of drift. An agent, and a person in a hurry, writes the next change to look like the code around it. When that code already breaks a decision, every change that matches it breaks it again, and the decision record stays accepted while the code stops honouring it. Nothing in a single review shows it, because each change is consistent with its neighbours.

So a decision record states what it requires in terms a check or an audit can hold, and the checks run on what a change touches. A repository adopts a stack's rules once, in its decision records; it does not let them be inferred, file by file, from whatever was written first.
