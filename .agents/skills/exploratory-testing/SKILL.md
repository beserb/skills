---
name: exploratory-testing
description: Support human-led live testing or, when explicitly requested, autonomously explore software, APIs, requirements, or existing systems through adaptive experiments. Use for exploratory test sessions, test charters, risk-focused investigation, or characterizing surprising behavior; use scripted checks when the task is only to verify known expectations.
---

# Exploratory Testing

Turn a risk or open question into empirical evidence. Exploration complements
preplanned checks: use checks to confirm known expectations and exploration to
discover risks the plan did not anticipate.

## Choose the collaboration mode

Default to **live copilot** mode. The user operates the target while you sharpen
the charter, propose one experiment at a time, explain its purpose, interpret
the user's observations, maintain session notes, and steer toward the next most
informative experiment. Wait for the user's observation before advancing. Keep
the user in control of pace, scope, and whether to pursue a tangent.

Use **autonomous** mode only when the user explicitly asks you to operate the
target or execute the exploration. In live copilot mode, interact with the
target, run tests, or mutate state only when the user delegates that specific
action. A request for ideas, guidance, or a testing session keeps the user as
driver.

If the user asks only for a charter or idea backlog, produce that planning
artifact without implying that a session ran. Begin the one-experiment cadence
only when live execution starts.

The mode is established when it is clear who operates the target. If the user
has not delegated operation, proceed as live copilot without asking.

## Establish the mission

Determine with the user the target, the stakeholder decision the work supports,
the available time, and the test environment. Prefer a disposable environment
and recoverable data. Keep disruptive experiments within the user's authority.
Obtain approval or use a safe simulation when an experiment could damage shared
data, interrupt a service, incur cost, or affect other users. Use synthetic or
minimized data where possible. Before recording or sharing evidence, redact
credentials, session tokens, payment data, personal data, and other secrets.

For an unfamiliar system, a requirement or design, or an API, batch, library, or
headless target, read [references/situations.md](references/situations.md) and
apply only the matching branch before continuing. Otherwise identify:

- the core capability or user value at stake;
- important **Always/Never** invariants and quality concerns;
- interfaces, dependencies, data, states, and observability available;
- known checks and the risks they leave unexplored.

Write a charter naming the **target**, useful **resources**, and the
**information** to discover. Keep it narrow enough for one focused session and
open enough to permit steering: a mission, not a scripted test case. When
stakeholders are available, confirm that they would act on the information.

The mission is established when its question, boundary, oracle candidates,
safety limits, and stopping point are explicit.

## Select lenses

Read [references/test-design-lenses.md](references/test-design-lenses.md) and
select the few lenses most likely to expose the charter's risk. Combine lenses
when interactions matter—for example CRUD × Zero/One/Many dependents or a state
interruption × a slow network. Prefer plausible, discriminating variations over
exhaustive combinations.

## Run an adaptive session

Start with the smallest representative success path when the baseline is not
known.

In live copilot mode, offer a single experiment containing:

- the question or risk it investigates;
- the setup and action for the user to perform;
- the signals to observe and the applicable oracle;
- any safety boundary or cleanup.

Wait for the result. Record the user's observation separately from your
interpretation, update the session notes, and offer the next experiment that
best discriminates between the remaining explanations. Ask a focused question
instead when missing context would materially change that choice. Provide a
checkpoint summary whenever the user asks or changes direction.

In autonomous mode, work in a tight loop:

1. Form a question or risk hypothesis.
2. Design and execute the smallest informative experiment immediately.
3. Observe visible output and relevant hidden effects: logs, requests, stored
   data, resource use, background work, and downstream views.
4. Compare the observation with an oracle and record the evidence.
5. Let the result choose the next experiment: vary, zoom in, change the model,
   reproduce, or abandon the weak lead.

In either mode, keep lightweight notes with the setup or data, action,
observation, oracle, and next question. Record surprises even when they are not
yet bugs. Change one factor at a time when attribution matters; combine factors
when the suspected failure is an interaction. Put valuable tangents in a
follow-up-charter list. After a valuable discovery, use the post-discovery
branch in [references/situations.md](references/situations.md) to generalize the
evidence without overextending it.

When a bad surprise appears, characterize its conditions, scope, severity,
recovery, and evidence. Before classifying it as target behavior, check for an
observer effect from the harness, test data, environment, cache, or temporary
instrumentation. Corroborate through an independent route when practical. Seek
the smallest reliable reproduction while retaining credible intermittent risks.
Use the intermittent-failure branch in
[references/situations.md](references/situations.md) when needed.

## Evaluate observations

Use the strongest applicable oracle:

1. explicit requirement, worked example, or stakeholder expectation;
2. core-value and Always/Never invariant;
3. internal consistency across equivalent paths, views, or interfaces;
4. an applicable standard or agreed comparable product;
5. a useful approximation: plausible range, statistical characteristic,
   inverse operation, or deliberately simplified or extreme input.

Distinguish observed fact from inference. Classify useful results as capability,
limitation, risk, bug, or open question. If an oracle is disputed, report the
behavior and competing expectations instead of silently inventing scope.

## Stop and debrief

End a session at its timebox or earlier when the charter is answered, new
experiments stop producing information, further findings would not change a
decision, or another charter has higher value. Running out of ideas alone does
not demonstrate coverage.

Report a decision-ready summary:

- charter and depth: what was explored and with which lenses;
- evidence: important capabilities, limitations, risks, and bugs;
- unknowns: what remains untested or weakly observed;
- next move: highest-value follow-up charters, testability improvements, or
  durable checks for important discoveries.

Charters and sessions are not pass/fail units. Report externally verifiable
evidence and confidence boundaries. The work is complete when the stakeholder
can tell what is known, what remains uncertain, and what decision the evidence
supports.
