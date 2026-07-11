# Onboarding exercise: fix a broken repo *through* the agent

A ~45-minute hands-on exercise I use to ramp engineers on Claude Code.
The design goal: hit the major agentic-coding failure modes on purpose,
in a sandbox, so people recognize them before they meet them in production
code. Adapt the sample repo to whatever small codebase fits your team.

## Setup (before the session)

- A small, runnable repo (~10–15 files) with a test suite — any language.
- Plant four deliberate problems:
  1. A failing test caused by a bug **two layers away** from where it surfaces
  2. A misleading function name that invites a wrong "fix"
  3. A module with **no** conventions/CLAUDE.md coverage
  4. One TODO that's genuinely ambiguous without asking a human
- Learners need Claude Code installed and the repo cloned. That's it.

## The exercise

**Part 1 — Orient (10 min).**
Prompt: have the agent map the repo. *Do not let learners open files manually.*
Ask them to get the agent to produce: what the project does, the module map,
how to run the tests.
Debrief question: what did the agent get wrong or overstate? (It usually
overstates confidence about the module with no documentation — failure mode:
confident wrong architecture.)

**Part 2 — Plan before code (10 min).**
Task: fix the failing test — but the rule is **plan first**. Learners must get
the agent to propose an approach and a file list *before* allowing any edit.
The planted bug is two layers from the symptom, so first plans are usually
wrong. Learners practice correcting a plan instead of reviewing a bad diff.

**Part 3 — The trap (10 min).**
Task: implement the ambiguous TODO. The right move is to notice it's
ambiguous and ask a human — but the agent will happily invent requirements.
Debrief: who shipped invented requirements? (Failure mode: silent scope
creep + "it compiles so it's done.")

**Part 4 — Tests are the contract (10 min).**
Task: have the agent write tests for the misleading-named function.
Learners must read the assertions and reject at least one weak test.
Debrief: what did the generated tests *not* check? (Failure mode: test
theater.)

**Wrap (5 min).**
Each learner writes one line they'd add to this repo's CLAUDE.md based on
what the agent got wrong. Collect them — that's the start of the team's
real conventions file.

## What this teaches, explicitly

| Part | Habit built |
|---|---|
| 1 | Verify the agent's map before trusting it |
| 2 | Plan-then-execute on multi-file work |
| 3 | Ambiguity goes to a human, not the model |
| 4 | Read assertions, not pass counts |
| Wrap | Conventions are failure-derived |
