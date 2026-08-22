---
name: readability-refactor
description: Refactor existing code for faster maintainer understanding while preserving behavior. Use when readability is the requested outcome; route functionality and architecture changes separately.
---

# Readability Refactor

Minimize the time a typical maintainer needs to understand the code while preserving its behavior and the repository's conventions. Understanding has a high bar: the maintainer should be able to explain the purpose, trace the important paths, find the state and effects, spot likely bugs, and make a change confidently.

## Establish the contract

Inspect the code, its callers, tests, nearby conventions, and any governing specification. Describe the code's high-level goal in plain language and identify the observable behavior, interfaces, and constraints that must remain stable.

The contract is established when every behavior that the refactor could plausibly disturb is either covered by evidence or called out as uncertain.

## Simulate the reader

Read as a typical maintainer who does not have the author's unstated context. For each nontrivial block, list the tasks it performs; a task may be as small as validation or as broad as applying domain policy. Mark where the reader must pause to:

- switch between interleaved tasks;
- resolve an ambiguous name or interface expectation;
- hold a large expression, deep branch, or long-lived mutable value in mind;
- chase control flow or state outside the visible region;
- infer intent, invariants, or surprising behavior that the code does not disclose.

Tie each friction point to a concrete burden on tracing, changing, or verifying the code. The simulation is complete when every nontrivial block is accounted for and the most consequential burdens are identified.

## Refactor the burdens

Address the largest comprehension burden first. Make the code follow the plain-language account of its goal:

- defragment interleaved tasks into coherent sections or functions;
- separate supporting subproblems from the code's primary goal;
- make control flow linear where guards or direct sequencing clarify it;
- shorten the lifetime and mutation span of values the reader must track;
- choose names that resist plausible misinterpretations;
- record intent, invariants, and surprises where code alone cannot carry them.

Each extraction must repay its navigation cost through a coherent subproblem, a simpler caller, independent testability, or genuine reuse. Prefer the smallest behavior-preserving change that removes the identified burden, and keep local idioms unless they are themselves the source of confusion.

The refactor is shaped when every edit answers a recorded friction point and introduces no unsupported behavior or needless interface.

## Verify understanding and behavior

Run the repository's relevant formatting and tests, then inspect the diff for accidental behavior, interface, and scope changes. Walk through the result in plain language again and confirm that the code's structure now follows that account.

Stop when a typical maintainer can:

1. state the code's goal and important constraints;
2. trace its main paths without reconstructing interleaved tasks;
3. locate the state, effects, and likely change points;
4. see important intent and caveats without author-only knowledge.

Remaining cosmetic preferences do not justify more churn once those conditions hold. Report the comprehension burdens removed, the behavior-preservation evidence, validation performed, and any residual uncertainty.
