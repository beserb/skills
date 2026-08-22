---
name: codebase-reconnaissance
description: Build a verified working model of an unfamiliar repository before acting. Use when entering a new codebase, locating where a behavior lives, explaining its actual architecture, or finding a safe change seam. Use focused task skills directly when the relevant path and seam are already known.
---

# Codebase Reconnaissance

Plot a verified route through unfamiliar code. Learn enough to answer the user's question or begin the authorized work safely; a complete catalogue of the repository is unnecessary.

## Fix the destination

State the concrete behavior, subsystem, or change that the reconnaissance must illuminate. Determine from the request whether the work is read-only or includes implementation; learning the repository does not itself authorize edits.

Read the repository's governing instructions and relevant context documents. Preserve the current worktree and distinguish user changes from the baseline you are investigating.

The destination is fixed when the user goal, authorization boundary, governing documents, and evidence needed for the next action are explicit.

## Establish ground truth

Inspect the repository from the outside in:

- identify the source layout, toolchain, entry points, and dependency manifests;
- find the canonical build, test, lint, and run paths from executable configuration rather than copying commands from prose;
- inspect version-control status before drawing conclusions from local files;
- run the smallest safe command that establishes the relevant baseline when execution would sharpen the model.

Treat documentation as a lead and code as ground truth. Record discrepancies that could affect the task. A missing, manual, noisy, or machine-specific setup path is itself a finding.

When the task will rely on a test signal, verify that the selected test reaches the relevant behavior and can detect the failure of interest. If this requires a temporary intentional failure, do it only when edits are authorized, isolate it from user work, and remove only the temporary change you made.

Ground truth is established when the relevant commands either have observed outcomes or are explicitly unavailable, and every material documentation/code discrepancy is accounted for.

## Map the terrain

Build the smallest architecture map that explains the destination. Identify:

- modules and their interfaces;
- external entry points and adapters;
- state, persistence, and observable effects;
- dependencies that cross the relevant seams;
- tests and documents that reveal intended behavior;
- history or ownership clues only where present code cannot explain an important decision.

Prefer targeted searches and caller tracing over broad file-by-file reading. Separate the architecture the code implements from the architecture its names or diagrams suggest.

The terrain is mapped when every module relevant to the destination has a role in the model and unknown modules cannot plausibly change the answer without crossing an identified interface.

## Trace one route

Choose the representative behavior closest to the user's goal and trace it end to end: external input, dispatch, orchestration, domain decisions, state or outbound effects, and observable result. Follow actual callers and data transformations. Use tests as executable usage examples, but confirm that they exercise production code rather than a parallel test-only path.

Check the route with one or more falsifiable predictions. For example: a named input should enter through a specific adapter, cross a specific interface, mutate a specific state, and become visible through a specific result. Verify the decisive predictions by execution when practical and by converging static evidence otherwise.

The route is traced when you can explain why the behavior occurs, identify its safest change seam, and name the validation that would detect a wrong change.

## Hand off the map

If the user requested implementation, continue into that work once the route and validation seam are established. Otherwise report a compact orientation containing:

- the relevant architecture and end-to-end route;
- canonical commands and observed baseline health;
- the likely change seam or answer to the user's question;
- discrepancies, risks, and unresolved uncertainty.

Create lasting orientation documentation only when the user requested it or the implementation naturally requires it. Stop reconnaissance when the next action is supported by a verified route; unrelated areas of the repository may remain unexplored.
