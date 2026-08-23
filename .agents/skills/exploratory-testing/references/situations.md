# Situation-specific workflows

Use only the section matching the current task.

## Unfamiliar system: recon

Run a short recon session before risk-specific charters. Map what the system
does, its inputs and outputs, interfaces and dependencies, visible and hidden
control points, important variables, and obvious vulnerabilities. Establish one
simple input or action and its observed result, then see how configuration and
off-interface manipulation change it.

Recon is complete when there is a rough ecosystem map, an initial variable
inventory, candidate oracles, and a prioritized charter backlog—and these
questions can be answered without guessing:

- What does the target do and how can it be driven and observed?
- Where does data enter, move, persist, and emerge?
- Which environment or configuration factors affect behavior?
- How can likely error conditions be triggered safely?

Share the rough model early so maintainers and users can correct it. Interview
stakeholders with context, a concise account of current knowledge, and a
specific open question; capture capabilities, frustrations, risks, and questions
that change the charter backlog.

## Requirements or designs

Explore the idea before implementation. Establish the business or user value,
core capabilities, quality factors, and Always/Never invariants. Ask concrete
“What if?” questions about unexpected actions, unavailable resources, variable
inputs, interactions with existing features, and boundary conditions. Use the
answers to clarify scope and draft later charters; confirm whether stakeholders
would act on the risk information.

For a document, read actively and classify claims as Inputs, Processing,
Outputs, or Questions. Search for missing categories and for a defined response
to every stated boundary or assumption. Translate dense prose into a state,
data, or ecosystem model when another representation could reveal gaps or
conflicting interpretations.

Deliver ambiguities, competing interpretations, missing decisions, concrete
examples, Always/Never rules, and implementation charters. Treat a new
expectation discovered after implementation as unresolved scope until the team
agrees it was required.

## API, batch, library, or headless target

Find the actual interface and build the smallest harness that can vary inputs
and expose outputs and side effects. Respect constraints enforced by the type
system or protocol; an impossible call may test the compiler or client rather
than the target. Vary semantic content, length, encoding, structure, volume,
timing, call sequence, and downstream state. Monitor resource use and internal
effects as well as returned values.

First establish a simple known case, then steer toward boundaries and surprising
behavior. When output is complex or nondeterministic, use ranges,
characteristics, inverse operations, or simplified or extreme conditions as
oracles.

## Intermittent or hard-to-reproduce failure

Treat reproducibility as a variable-discovery problem. Gather traces from every
occurrence: timestamps, logs, screenshots, input data, configuration, machine,
user, load, and preceding actions. Look for correlations with time, activity,
platform, and sequence. Brainstorm multiple contributing variables; intermittent
failures often need a combination rather than a single cause. Model nearby
states and short-lived transitions to identify vulnerable timing windows.

Vary suspected factors to increase the occurrence rate and preserve all
evidence. Full on-demand reproduction is desirable but not required to report a
credible, bounded risk. Collaborate with people who bring complementary system,
domain, and implementation knowledge when available.

## After a valuable discovery

Generalize carefully. Ask whether the finding is an isolated defect, a family of
related vulnerabilities, a missing durable check, or evidence of a systemic gap.
Reuse discriminating data or conditions across relevant paths and propose a
regression check for an important fixed defect. Capture testability techniques
and environment knowledge that would otherwise be rediscovered.
