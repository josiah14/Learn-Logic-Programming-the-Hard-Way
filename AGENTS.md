# Learn Logic the Hard Way — agent guide

## Purpose

This repository teaches Josiah logic programming through project work, deliberate breakage, compiler feedback, repair, and reflection.

Build this curriculum **one stage at a time as Josiah learns**. Do not generate a complete book upfront or scaffold future stages speculatively. Each concept starts with a working program, bug hunt, comparison, or implementation; terminology comes afterward.

- Josiah writes substantive implementations. Agents may provide environment boilerplate, neutral examples, review, explanation, and diagnosis of actual compiler/test output.
- Do not provide a finished exercise implementation before a genuine attempt unless explicitly asked.
- Treat compiler output and tests as ground truth. A broken exercise must fail for its stated reason; a solution must be verified.
- A mature stage contains `README.md`, `starter/`, `solution/`, `broken/`, `tests/`, `reflection-prompts.md`, and `rubric.md`. Start with only the material needed for the current stage.

## Mercury is core: use Cinnabar

Mercury is the core language of this logic-programming track. For every Mercury stage, agents must use Cinnabar as the primary teaching substrate:

`/home/josiah/Development/personal/education/self/polyparadigm-project/cinnabar`

Do not recreate Cinnabar's katas, koans, bridges, or puzzles as competing exercises. Select relevant Cinnabar material, explain why it belongs at the current stage, have Josiah work it, and add only the course-specific comparison, reflection, or integration project needed here.

Cinnabar supplies Mercury fluency; this project supplies the cross-language logic-programming arc and the explainable-rule-engine destination. Use Cinnabar's foundations, mode-system, determinism, parsing, higher-order work, bridges, and advanced puzzles as each Mercury stage demands. Compile-check the specific lesson; reviewed material is not exempt from evidence-based correction.

## Mercury Nix environment

The initial Mercury toolchain comes from Cinnabar's host-prebuilt Nix flake. In FaradAI, `/nix/store` is read-only. Do not add packages, make it writable, or run `nix develop .` from a dirty checkout.

Use Cinnabar's commit-pinned shell:

```bash
nix develop 'git+file:///home/josiah/Development/personal/education/self/polyparadigm-project/cinnabar?rev=1a90a5e62aca85dfcb7af05c26ec45466031a73f'
```

For non-interactive commands:

```bash
nix develop 'git+file:///home/josiah/Development/personal/education/self/polyparadigm-project/cinnabar?rev=1a90a5e62aca85dfcb7af05c26ec45466031a73f' --command mmc --version
```

This shell includes Mercury 22.01.8 (`mmc`). If Cinnabar changes, replace `rev=` with `git rev-parse HEAD` only after the host has prebuilt that revision's flake closure. Otherwise request a prebuilt shell; do not work around the store restriction.

Prolog, Soufflé, Racket/miniKanren, and Python stages need separately verified tooling. Record the installed version and invocation in each stage README before adding the material.

## Language policy

| Stage | Main language |
| --- | --- |
| 0 | Prolog, Mercury, miniKanren, Soufflé Datalog |
| 1 | Prolog |
| 2–5 | Mercury |
| 6 | Soufflé Datalog |
| 7 | Mercury |
| 8–9 | miniKanren in Racket/Scheme |
| Practical interlude | Python 3.11+ with `kanren` 0.3.0 |
| 10–14 | Mercury |

Begin with Prolog's minimal relational surface. Move to Mercury when recursive relations need explicit direction, failure, and answer-count contracts. Use Datalog to experience finite fixpoint reasoning and its limits. Use miniKanren for visibly bidirectional relations, then return to Mercury for disciplined rule engines.

## Curriculum path

| Stage | Goal and deliverable |
| --- | --- |
| 0 — Logic-programming family | Run the same ancestor problem in Prolog, Mercury, miniKanren, and Soufflé; modify queries only. Deliver a two-page comparison of directionality, termination, syntax, answer generation, surprises, ease, and awkwardness. |
| 1 — Prolog facts, rules, queries | Build family facts plus `grandparent`, `sibling`, `ancestor`, and `descendant`; query multiple directions; repair broken recursion; hunt duplicate/overpermissive answers. Deliver a database and bug report. |
| 2 — Mercury modes and determinism | Port family relations; implement `my_append/3` in `(in,in,out) is det`, `(out,out,in) is multi`, and `(in,in,in) is semidet`; conduct mode-error and determinism-repair labs. |
| 3 — Recursion as relation | Implement list relations and graph `reachable`/`path`; expose a cyclic-graph looping query, explain it, and add visited tracking. |
| 4 — Search and generation | Generate paths and graph colorings; observe search explosion; prune with goal and constraint ordering. Deliver a solver and notes. |
| 5 — Negation and closed world | Contrast trusted-by-negation with explicit status over incomplete data; demonstrate unsafe negation before grounding. Deliver a report on absence, evidence, closed world, and groundness. |
| 6 — Datalog interlude | Build reachability and dependency closure in Soufflé; compare Mercury; attempt permutation-style generation and explain the boundary. |
| 7 — Higher-order Mercury | Implement `map`, semidet `filter`, and a fold; repair a higher-order mode error. |
| 8 — miniKanren relational lists | Implement `appendo`, splitting, prefix, and suffix; compare bidirectional `appendo` with Mercury append modes. |
| 9 — miniKanren relational arithmetic | Start with Peano naturals; implement order, addition, multiplication, and factorization; observe query-shape performance and termination. |
| Practical interlude — Python | Port a Stage 8 relation to `kanren`; diagnose a Python embedding bug; build a configuration validator plus one ordinary-Python integration; publish one explanatory public artifact. |
| 10 — Explanation and derivation trees | Return proof paths and missing-information reports for ancestry, reachability, and eligibility. |
| 11 — Rule engines I | Build forward- and backward-chaining Mercury engines over the same eligibility rules; compare eager and demand-driven reasoning. |
| 12 — Rule engines II | Represent rules as data, interpret them, preserve rule names, return derivation trees, and change rules without engine changes. |
| 13 — Committed choice and control | Add priorities and salience; compare all-applicable with first-match behavior; report considered, rejected, and winning rules. |
| 14 — Explainable rule-engine capstone | Build a tested rule engine with structured facts/rules, recursive reasoning, an explicit absence decision, validation, explanation trees, incomplete-data behavior, limitations, and data-only rule changes. |

## PPN95 companion capstone

Pineapple Paint Nightmare 95 (PPN95) fits this curriculum as a long-form Mercury
companion project and capstone variant:

`/home/josiah/Development/personal/education/self/polyparadigm-project/pineapple-paint-nightmare-95`

It should begin only after the learner has encountered the corresponding small logic
problems. PPN95 must **not** replace the family, list, graph, and rule-engine exercises:
its story engine has too many moving parts to be a good first encounter with modes,
cycles, negation, search, or explanations. Small exercises isolate each concept; PPN95
makes that concept matter in a coherent system.

| Learn Logic stage | PPN95 application | Why the connection matters |
| --- | --- | --- |
| 2–4: modes, recursion, search | Conditions as data and deterministic eligibility classification versus nondeterministic candidate generation | The project demonstrates why a useful engine may deliberately reject nondeterministic search: blocked candidates need retained reasons. |
| 5: negation and closed-world reasoning | `lacks_flag`, `not_seen`, and other absence semantics | Story content forces an explicit authored decision about what absence means. |
| 7: higher-order Mercury | Storylet-processing policies and later simulation-policy hooks | Higher-order control becomes a real extension mechanism rather than an abstract library exercise. |
| 10: explanations | `block_reason` values and `debug candidates` | Explanations become authoring/debugging infrastructure, not merely proof output. |
| 11–12: rule engines and rules as data | Storylets, conditions, and effects as data; later EDN loading | The learner sees a domain-specific interpreter and data-driven authoring without prematurely generalizing it into a rule engine. |
| 13: committed choice and control | Anchors, weights, selection policy, replayable PRNG | It distinguishes editorial/control policy from logical eligibility. |
| 14: explainable capstone | Validator, corpus reports, replay/debug tooling, and simulation harness | PPN95 can satisfy the serious-system part of a capstone while demonstrating a distinct, intentional engine architecture. |

The approximate sequencing is: PPN95 Stages 0–1 after Learn Logic Stages 2–3;
conditions and explanations alongside Stages 4–5 and 10; parsing and simulation after
higher-order Mercury; and validation, corpus reports, and replay tooling at capstone
level. When teaching the mapping, emphasize the productive contrast: a generic rule
engine may use forward or backward proof search, while PPN95 intentionally uses total,
deterministic classification with structured failures so authors can ask why a storylet
did not appear.

## Learning constraints

- Stages 1–4 make recursion bugs, modes, determinism, termination, cycles, search growth, and early pruning observable. Learners explain errors; they do not merely change code until it compiles.
- Stage 5 distinguishes absence of evidence from evidence of absence. Negation is not database truth without closed-world and groundness assumptions.
- Datalog teaches finite closure and its resistance to arbitrary constructive search. miniKanren relations run in multiple directions and are compared with Mercury's contracts and operational predictability.
- The Python interlude is integration, not a miniKanren replacement. Include a genuine host-language bug: Python boolean composition, iterator exhaustion, closure capture, or mutable defaults.
- Explanations in Stages 10–14 are structured values before rendered strings. Stages 11–12 share child-credit, caregiver-credit, and manual-review rules. Stage 13 distinguishes declarative all-solutions behavior from operational policy.
- Stage 14 tracks are tax eligibility, scholarship eligibility, access-control/permissions, or scheduling/rules hybrid. Require a recursive rule, explicit negation/absence choice, validation, explanations, incomplete data, tests, known limits, and rule changes without recompilation. Scheduling earns constraints.

## Optional extensions and progress

After the core path: finite-domain constraints; Soufflé static analysis; Prolog cuts; and inductive logic programming. Private dogfooding capstones may cover benefits, compliance, course prerequisites, or insurance pre-screening; they are not official student tracks unless explicitly promoted.

A stage is complete only when Josiah can run and alter its program, reproduce the intended failure or surprise, explain the cause plainly, repair or extend it independently, and connect the lesson to the next project. Correct code without an explanation of behavior is not completion.
