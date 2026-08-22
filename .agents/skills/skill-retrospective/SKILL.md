---
name: skill-retrospective
description: Review the available conversation history when asked for a session retrospective on skill usage, agent friction, or evidence-backed improvements to invoked skills. Use for diagnosing how skills performed; use ordinary skill authoring for changes that are not grounded in a session.
---

# Skill Retrospective

Turn the visible session record into a traceable account of which skills ran, where
their guidance failed to produce a smooth result, and what narrow changes could
prevent the same failure.

## Build the invocation ledger

Scan the available conversation chronologically. Count a skill as **confirmed**
when the record shows at least one of these signals:

- the user explicitly invoked it;
- the agent announced that it was using it;
- its `SKILL.md` or a resource required by it was read;
- a skill-specific action in the record unambiguously demonstrates invocation.

Do not count a skill merely because it appeared in an available-skills catalog.
Label an invocation **inferred** when the behavior resembles a skill but no direct
signal survives in the visible record. Keep confirmed and inferred invocations
separate.

For each invocation, record the skill, the point in the conversation, the trigger,
the confirming evidence, and the work governed by the skill. Distinguish
**requested**, **loaded**, and **applied** when the record supports those states;
this exposes a named skill that the agent never actually consulted or followed.
Consolidate repeated reads belonging to one continuous use while preserving
distinct invocations.

The ledger is complete when every visible invocation signal is accounted for.

## Find friction

Treat **friction** as an observable mismatch between the task and the path the
agent took. Look for:

- **Invocation:** a relevant skill was missed, selected late, or selected for the
  wrong branch.
- **Retrieval:** required instructions or conditional references were skipped,
  loaded too late, or loaded without a usable trigger.
- **Execution:** the user corrected the agent, the agent backtracked, repeated a
  failed attempt, hesitated at an underspecified decision, or violated a skill
  requirement.
- **Completion:** the agent stopped before a checkable outcome, omitted required
  verification, or claimed more than the evidence supported.

For every friction point, cite the nearest visible turn or event, state what was
observed, identify the relevant skill instruction if available, and explain the
causal link. Assign confidence as high, medium, or low.

Long work, extensive tool use, a reasonable clarification, and a tool or
environment failure are not friction by themselves. Keep non-skill causes in a
separate section unless the skill could reasonably have anticipated or recovered
from them.

The friction pass is complete when each confirmed skill is either connected to at
least one supported finding or explicitly marked as having no observed friction.

## Propose narrow improvements

Map each proposal to one supported friction point. Prefer the smallest change that
would alter the failed decision on a future run:

- sharpen the description when invocation was missed or misrouted;
- add or tighten a step and its completion criterion when execution ended early;
- co-locate a rule with the decision it governs when it was overlooked;
- disclose branch-specific detail behind a precise pointer when unrelated detail
  obscured the active path;
- add a deterministic script only when repeated mechanical work caused the
  failure.

Give patch-ready replacement text when the evidence is strong enough. Mark a
single-session generalization as a hypothesis, and recommend observing another
run before adding broad rules. Reject changes that duplicate an existing rule,
encode a one-off environmental accident, restate default agent behavior, or weaken
the skill for other valid branches.

When the skill's source text is absent from the available record, describe the
needed behavioral change without inventing exact existing wording or file
locations.

Suggestions are the default deliverable. Edit skill files only when the user also
asks for implementation, and preserve the existing scope and invocation policy.

## Report

Present:

1. A brief outcome summary.
2. An invocation ledger with confirmed and inferred uses distinguished.
3. Friction findings, ordered by impact, including evidence, diagnosis, and
   confidence.
4. Proposed improvements mapped one-to-one to findings, with patch-ready wording
   where justified.
5. Non-skill causes and limitations.

State when the available history is incomplete, summarized, or lacks the hidden
reasoning needed to support a diagnosis. Do not reconstruct private reasoning from
the outcome. If no supported friction exists, say so instead of manufacturing an
improvement.

The retrospective is complete when every invoked skill has a disposition, every
finding has evidence, and every recommendation names the finding it addresses.
