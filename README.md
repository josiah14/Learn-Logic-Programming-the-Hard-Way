# Learn Logic Programming the Hard Way

A project-based curriculum for learning logic programming by building programs, breaking them deliberately, reading the behavior, repairing them, and reflecting on the underlying model.

This is not a book generated all at once. It is being built one stage at a time as its learner works through it. Concepts land better after a concrete encounter: a surprising query, a loop, a compiler error, a failed proof, or a small system improved by one precise change.

## What the path covers

The curriculum begins with the same relational problem in Prolog, Mercury, miniKanren, and Soufflé Datalog. It then moves through Prolog relations, Mercury modes and determinism, recursion, search, negation, Datalog, miniKanren, and a small Python `kanren` interlude.

The second half returns to Mercury for explanation trees, forward and backward chaining, rules as data, committed choice, salience, and an explainable rule-engine capstone.

## Mercury is the core language

Mercury is the main language of the track. Its types, modes, determinism declarations, and compiler feedback make the operational consequences of relational code explicit.

The Mercury work uses [Cinnabar](../cinnabar/) as its primary exercise library. Cinnabar provides focused katas, koans, bridges, and puzzles; this project provides the cross-language progression and a coherent destination in explainable rule engines.

## Companion project: PPN95

[Pineapple Paint Nightmare 95](../pineapple-paint-nightmare-95/) is the long-form Mercury companion capstone. Its storylet engine applies the curriculum's ideas to a real system: conditions as data, deterministic eligibility classification, structured block reasons, authoring/debugging tools, replayable selection, validation, and simulation.

It complements rather than replaces smaller exercises. A family relation or graph search problem isolates one idea; PPN95 demonstrates why that idea matters when a system has users, content, debugging needs, and operational policy.

## Status

The repository currently contains the curriculum contract and teaching path in [AGENTS.md](AGENTS.md). Stage material will be added only when it is actively being learned and can be tested against real tools.

## License

This work is licensed under [CC BY-SA 4.0](LICENSE).
