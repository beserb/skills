# Test heuristics catalog

Use this catalog to widen a charter, recover when experiments stop producing
information, or check whether a test design has ignored a relevant class of
risk. It is an idea generator, not a coverage checklist. Start from a valid
baseline, choose variations that could distinguish plausible implementations,
and combine heuristics when the suspected failure depends on an interaction.

The catalog is adapted from the *Test Heuristics Cheat Sheet*, Ministry of
Testing (2022), credited there to Elisabeth Hendrickson, James Lyndsay, Dale
Emery, and additional contributors.

## Data-type attacks

Choose attacks from the value's actual representation and domain. Fixed sizes
such as 255 or powers of two are probes, not universal boundaries. Apply hostile
payloads only within the charter's authorization and safety limits.

### Paths and files

- Names: very long names and names containing spaces, punctuation, delimiters,
  separators, wildcards, quotes, or shell-significant characters.
- Existence: missing targets and targets that already exist.
- Capacity: no free space and barely enough free space.
- Access and location: write-protected, unavailable, locked, or remote targets.
- Integrity: corrupt files or storage.

### Time and dates

- Timeouts; clocks that disagree between machines; time-zone crossings.
- Leap days, invalid calendar dates, and February 29 in non-leap years.
- Ambiguous, shortened, localized, or mixed date formats.
- Twelve-hour versus twenty-four-hour time.
- Daylight-saving transitions and clocks moved backward or forward.

### Numbers

- Zero and negative values.
- Values immediately below, at, and above likely binary limits, including
  powers around 2^15, 2^16, 2^31, and 2^32.
- Very small decimals, floating-point values, and scientific notation.
- Thousands and decimal separators in different locales.
- Repeat the relevant probes inside calculations, not only at input.

### Strings and domain values

- Lengths immediately around likely limits and substantially beyond them.
- Accented text, non-Latin scripts, emoji, mixed encodings, and normalization.
- Quotes, backticks, slashes, pipes, markup, delimiters, tabs, and line endings.
- Empty input, one or many spaces, and leading or trailing whitespace.
- The same value through create, search, update, import, and other available
  actions or interfaces.
- Markup, script, query, or command-like input when authorized.
- Values that violate semantic rules or uniqueness constraints.

## Web

### Navigation and input

- Use Back, Forward, refresh, direct URLs, bookmarks, intermediate URLs, and
  bookmarks after logout; watch for stale pages and repeated transactions.
- Run multiple browser instances and use touch gestures where supported.
- Change, remove, or forge URL parameters within the safety boundary.
- Exercise data-type attacks through inputs; inspect length handling, large
  text areas, and authorized markup or script injection.

### Rendering and preferences

- Validate HTML and CSS syntax when malformed output is plausible.
- Disable JavaScript or cookies, increase browser security, resize the window,
  and change font size.

### Accessibility

- Keyboard: reach all functionality; check order, skip links, visible focus,
  traps, and focus management for pop-ups.
- Context: descriptive links and alternatives, associated form labels, one
  meaningful main region, declared language, plain language, and explained
  acronyms.
- Presentation: zoom to 200%, avoid meaning carried only by color, and examine
  contrast, capitalization, justification, and gendered assumptions.
- Modality equivalence: visible information should be available to screen-reader
  users, and audible information should have an equivalent such as captions,
  transcripts, or audio description.

## APIs

Use the named mnemonics as alternative prompts, not as three mandatory passes:

- **BINMEN:** boundaries, invalid entries, null, methods, empty, negative.
- **POISED:** parameters, output, interoperability, security, errors, data.
- **VADER:** verbs, authentication and authorization, data, errors,
  responsiveness.

Also distinguish testing an interface itself from testing through that interface
to reach deeper behavior. The same distinction applies to UI tests.

## Mobile and device contexts

Vary device, orientation, browser, visual presentation, platform conventions,
network, inputs, time, personas, interruptions, performance, energy consumption,
ergonomics, security, privacy or tracking, and automation approach. Use only
dimensions that can alter the behavior or stakeholder outcome.

## General lenses

- **Variables:** inventory obvious, subtle, and hidden values that can change.
- **Touchpoints:** find public and private interfaces that offer control or
  visibility; use them to provoke, monitor, and verify.
- **Boundaries:** approach, reach, and cross a meaningful boundary.
- **Goldilocks:** too small, just right, and too large.
- **CRUD:** create, read, update, and delete.
- **Follow the data:** move a value through entry, search, reports, exports,
  imports, updates, and views; verify integrity at every handoff.
- **Configurations:** vary resolution, network behavior, resources, environment,
  and the count of attached peripherals.
- **Interruptions:** log out, shut down, reboot, terminate a process, disconnect,
  hibernate, time out, or cancel.
- **Starvation:** constrain CPU, memory, network, disk, or another finite resource
  in an authorized environment.

- **Position:** beginning, middle, and end.
- **Selection:** some, none, and all.
- **Count:** zero, one, and many.
- **Multi-user:** concurrent creation, update, or deletion from distinct users or
  sessions, including two sessions for one account.
- **Flood:** simultaneous or repeated requests, including repeated submission.
- **Dependencies:** identify "has-a" relationships, then combine CRUD, count,
  position, and selection across parent and child entities.
- **Constraints:** violate required fields, dependent-field combinations,
  uniqueness, and other invariants.
- **Input method:** compare typing, paste, import, drag-and-drop, GUI, and API.
- **Sequences:** reorder, reverse, combine, invert, repeat, undo or redo, and run
  actions simultaneously.
- **Sorting:** compare alphabetic with numeric behavior and cross-page ordering.
- **State analysis:** identify states and events, then represent them in a table
  or diagram and combine them with sequences and interruptions.
- **Map making:** establish a base state, take one transition, return to base,
  and repeat in other directions; record failures to restore state.
- **Users and scenarios:** use cases, soap-opera scenarios, personas, and extreme
  personalities to supply coherent goals and behavior.

## Risk, requirements, and reporting

### Regression routing: RCRCRC

Classify and prioritize regression risks as:

- **Recent:** new or newly changed areas.
- **Core:** essential capabilities that must continue working.
- **Risky:** intrinsically hazardous or high-impact behavior.
- **Configuration-sensitive:** behavior dependent on environment settings.
- **Repaired:** defect fixes and nearby behavior they may disturb.
- **Chronic:** areas with a history of breaking.

### Failure and context prompts

- **FAILURE:** functional behavior, appropriateness, impact, logs, UI, recovery,
  and emotional effect.
- **WWWWWHKE:** who, what, when, where, why, how, and what the tester's knowledge
  and experience suggest asking next.
- **TORCH:** timer, oracles, risks, questions to consider, and heuristics.
- **MCOASTER:** mission, coverage, obstacles, audience, status, techniques,
  environment, and risk. Use it to debrief omissions as well as findings.

### Specifications and designs

Scan for ambiguity; modal or evasive words; deferred decisions without an owner
or date; inconsistent terminology; jargon and unexplained acronyms; and both
over-simplification and over-complication. Turn each hit into competing
interpretations, a discriminating example, or a stakeholder question.

### Diversity and affect

Ask whether the product works for the tester, for known people unlike the
tester, and for people or circumstances the team has not considered. Vary
personas and emotional states when they plausibly change behavior, comprehension,
or harm. The **Seven Dwarfs** prompt—Grumpy, Happy, Sleepy, Bashful, Sneezy,
Dopey, and Doc—is one mnemonic for generating contrasting affective or ability
conditions. Treat these prompts as hypothesis generators; validate important
claims with affected users or stronger domain guidance.

## Automation and observation

- **SACRED:** state management, actions, a codified oracle, reporting, execution,
  and determinism.
- **TRIMS:** targeted, reliable, informative, maintainable, and speedy.
  Use these as quality questions for automated checks, with tradeoffs disclosed
  rather than assuming every attribute can be maximized.

- **Judgement:** look for inconsistencies, absences, and extras relative to
  internal expectations, a specific external reference, or broader cultural
  expectations. Report disputed references as competing oracles.
- **Observations:** attend separately to input, output, and their linkage.
- **Flow:** trace input, processing, and output.
- **Requirements:** inventory users, functions, attributes, and constraints.
- **Nouns and verbs:** combine system entities with actions; use adjectives and
  adverbs to vary attributes and manner, producing unusual but interpretable
  scenarios.
- **Deming cycle:** plan, do, check, and act.

## Working principles

Use these principles to steer selection and interpretation:

- A test is an experiment intended to reveal information or answer a question.
- Stakeholder questions give the experiment its value.
- Speed is not the same as progress.
- Contrary perspectives and direct observation widen discovery.
- A narrow viewpoint leaves wider ignorance; the tester is not representative
  of every person.
- Defects may cluster, and important discoveries may initially appear by chance.
- Vary sequences, configurations, and data because interactions among variables
  often expose the failure.
