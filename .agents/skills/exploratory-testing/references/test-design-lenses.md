# Test-design lenses

Choose lenses from the charter's risk and observed behavior. This is a prompt
for analysis, not a checklist to exhaust.

## Variables

Inventory anything that can change directly or indirectly: values,
configuration, environment, prior history, and system-generated conditions.
Look past obvious fields toward hidden settings and variables within variables.

- Counts: Zero/One/Many, Too Few/Too Many.
- Sets: Some/None/All.
- Position: Beginning/Middle/End.
- Magnitude: too small/just right/too large; probe boundaries and powers of two.
- Shape: format, character set, symmetry, file contents, size, and nesting depth.
- Context: storage or geographic location, time zone, platform, configuration,
  resource availability, and production-like data.
- Time: speed, delay, frequency, duration, timeout boundaries, and repetition.
- Interaction: typing versus paste or import, mouse versus keyboard or API,
  direct versus indirect action.

Select values that distinguish plausible implementations. A symmetric input can
hide reversed processing. Pair a valid baseline with one meaningful variation
so the observation remains interpretable.

## Sequences and users

Vary order, path, and mechanism because real usage diverges from the designed
happy path. Try alternate ways to save, cancel, close, undo, retry, or reach the
same state; reverse a workflow; repeat actions; skip prerequisites; and revisit
earlier steps. For web flows, exercise browser Back/Forward/history and bookmark
an intermediate page.

When multiple actors matter, vary same-account and different-account sessions;
interleave or synchronize their actions; and watch for duplicate effects, lost
updates, stale authorization, and broken ownership.

When habit narrows the search, combine system nouns and verbs into unusual
actions or sequences. A realistic or extreme persona can supply a consistent
goal, knowledge level, pace, and interaction style instead of arbitrary abuse.

## Entities and data journeys

Identify visible and hidden entities, their attributes, ownership, dependencies,
and cardinalities. Apply Create/Read/Update/Delete through every materially
different route, including side effects, bulk operations, imports, and undo.
Combine CRUD with attribute variations and Zero/One/Many dependents. Try
clearing formerly populated optional fields and deleting or reassigning parents.

Follow consequential data through storage, search, reports, queues, audit
trails, integrations, caches, exports, and alternate views. Verify integrity and
authorization at every handoff; a value accepted at one interface may fail or
become unsafe downstream.

## States and interruptions

For timing, workflow, or intermittent risk, model a focused target as states and
events. Include user, external, system-generated, and time-based events. Choose
one perspective and an abstraction level that exposes the suspected window
without mapping the whole product.

- Find every materially different way to trigger a transition.
- Interrupt transitional and steady states with cancel, timeout, logout,
  process termination, lost connectivity, or another relevant event.
- Vary previous state, transition mechanism, time in state, event count, and
  loop count; then check recovery and data integrity.
- Convert the state diagram to a state/event table. Unknown or supposedly
  impossible cells are experiments.
- Zoom into a broad transition to reveal hidden substates; abstract details when
  the model becomes too large.

## Ecosystem and trust

Sketch only the useful ecosystem: human and programmatic interfaces, deployed
components, stores, files, networks, and external services. Treat every
controllable boundary—including databases and files—as untrusted. Follow data
across the map.

Ask what happens when a dependency is missing, slow, unavailable, malformed,
stale, duplicated, reordered, or partly successful. For files and stores,
consider empty/corrupt/huge content, locks, permissions, full capacity, custom
locations, and concurrent modification. Starve CPU, memory, disk, connections,
or bandwidth only in an authorized safe environment.

Also change topology: centralize data or load that is normally distributed, or
distribute what is normally centralized. These shapes expose assumptions that
ordinary volume tests may miss.

## Observation and testability

Direct attention to different surfaces to counter inattentional blindness. A
successful UI message is weak evidence if files, persisted data, permissions, or
downstream behavior are wrong. Watch consoles, logs, network traffic, storage,
background activity, CPU, memory, and timing; compare screenshots or recordings
when visual changes are subtle.

Improve visibility and control when important state is hidden: verbose logs,
diagnostic endpoints, controllable clocks or dependencies, seeded data, and
resource monitors. Keep production safety and removal requirements explicit for
temporary hooks.
