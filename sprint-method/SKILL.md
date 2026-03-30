---
name: sprint-method
version: 0.2.0
description: >
  Guide the user through the Design Sprint methodology — a structured five-phase process for going from a big problem or idea to a tested prototype. Covers: mapping the problem, sketching solutions, deciding what to build, prototyping, and testing with real users.
  Trigger when the user mentions SPRINT, design sprint, 5-day sprint, problem mapping, solution sketching, or the Sprint book by Jake Knapp. Also trigger on phrases like "start a sprint", "let's sprint on", "sprint method", "I want to run a sprint", or when the user wants a structured process for brainstorming, validating, or designing a new product, feature, service, or idea — especially if they want to move quickly from concept to tested prototype.
---

# Sprint Method

## Overview

The Design Sprint is a five-phase process created by Jake Knapp at Google, later refined at Google Ventures. The SPRINT's goal is to reduce debate, design, and testing into one focused process. In this skill, the "days" of the original sprint become **phases** — the user may complete them in one session or across multiple conversations.

This Skill adapts the SPRINT methodology into a 1-on-1 conversation with Claude. Claude plays multiple roles from the sprint team depending on the phase and context. The user is always the **Decider**.

## Roles

See @references/roles.md

## Phase Reference Files

Each phase has a dedicated reference file. Load only the file relevant to the active phase to keep context lean.

- Phase 1 — Map: @references/phase-1-map.md
- Phase 2 — Sketch: @references/phase-2-sketch.md
- Phase 3 — Decide: @references/phase-3-decide.md
- Phase 4 — Prototype: @references/phase-4-prototype.md
- Phase 5 — Test: @references/phase-5-test.md
- Reusable templates: @references/templates.md

## Instructions

### Pre-Phase — Sprint Brief & Role Defining

Before starting, gather the Sprint Brief by asking the user:

1. **Challenge** — What problem or opportunity are you sprinting on?
2. **Target customer** — Who is this for?
3. **Time horizon** — What's the goal in 6 months to 5 years?
4. **Starting phase** — Are you starting from Phase 1 or resuming at a specific phase?

Once you have the brief, research the topic and propose 3–5 sprint team roles relevant to the challenge (see @references/roles.md). Present them clearly and ask the user to confirm or adjust.

When confirmed, remind the user they can invoke a specific role at any time by naming it. Then proceed to the active phase.

---

### Phase 1 — Map

See @references/phase-1-map.md

**Output:** Long-term goal statement, sprint questions list, customer journey map, target customer and critical moment.

---

### Phase 2 — Sketch

See @references/phase-2-sketch.md

**Output:** Lightning demo insights, Crazy 8s variations, Solution Sketch (3-panel storyboard description).

---

### Phase 3 — Decide

See @references/phase-3-decide.md

**Output:** Chosen solution (or Rumble candidates), storyboard (10–15 frames).

---

### Phase 4 — Prototype

See @references/phase-4-prototype.md

**Output:** Prototype plan with assigned roles, content outline, and trial run notes.

---

### Phase 5 — Test

See @references/phase-5-test.md

**Output:** Interview findings organized by customer and sprint question, pattern summary, and recommended next steps.

---

## General Rules

- The user is always the **Decider**. Claude presents options, trade-offs, and recommendations — but never makes the final call.
- At the end of each phase, summarize the artifacts produced and ask the user to confirm before moving on.
- If the user resumes mid-sprint, ask them to share the artifacts from prior phases before continuing.
- Keep exercises concrete and adapted for a solo + AI context (no physical whiteboard or sticky notes assumed).
