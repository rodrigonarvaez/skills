# Phase 5 — Test

**Goal:** Learn from real users reacting to the prototype. Look for patterns — not perfect data.

Five interviews is enough to spot the signals that matter.

---

## Exercise 1: Interview Structure

Each interview follows a consistent script (see @templates.md for the full template). The structure is:

1. **Friendly intro (5 min)** — Welcome the customer, explain the session is about learning (not testing them), ask permission to take notes.
2. **Context questions (10 min)** — Ask about their life, work, and habits related to the problem space. Don't mention the product yet. Goal: understand their world.
3. **Introduce the prototype (25–35 min)** — Show the prototype and ask the customer to think aloud as they use it. The Interviewer's job is to listen, not explain.
4. **Debrief questions (5–10 min)** — Ask about their overall impression, what surprised them, what they'd tell a friend about it.

**Key interviewer rules:**
- Never explain what the customer "should" do — let them get confused
- Ask "what were you thinking there?" not "did you like it?"
- Silence is data — resist filling it

---

## Exercise 2: Note-Taking Setup

Before interviews begin, set up a note-taking grid. Claude can help simulate this:

| | Customer 1 | Customer 2 | Customer 3 | Customer 4 | Customer 5 |
|---|---|---|---|---|---|
| Sprint Q1 | | | | | |
| Sprint Q2 | | | | | |
| Sprint Q3 | | | | | |
| General observations | | | | | |

After each interview, ask the user to fill in their observations. Claude helps identify which sprint questions each observation speaks to.

---

## Exercise 3: Pattern Review

After all 5 interviews, review the note grid together. Look for:

- **Strong positive signals** — 3+ customers reacted the same positive way
- **Strong negative signals** — 3+ customers hit the same friction or confusion
- **Surprising moments** — unexpected reactions that change the hypothesis
- **Noise** — one-off reactions that don't form a pattern

Prompt: *"What patterns stand out? What were you most wrong about going into this?"*

---

## Exercise 4: Compare to Monday's Goal

Return to the Phase 1 artifacts and evaluate:

- **Long-term goal** — Did the prototype move toward it?
- **Sprint questions** — Which ones got answered? Which are still open?
- **Target customer and moment** — Did real customers match your assumptions?

Ask the user: *"Based on what you learned, what's the single most important thing to do next?"*

---

## Exercise 5: Recommended Next Steps

Help the user choose a path:

| Signal | Recommended next step |
|---|---|
| Strong positive, clear path forward | Move to build — the concept is validated |
| Mixed signals, one strong failure point | Iterate on the prototype and run another test |
| Fundamental assumption was wrong | Return to Phase 1 and re-map with new insight |
| Two competing ideas tested (Rumble) | Pick the winner, or identify which elements to combine |

---

## Phase 5 Artifacts

Summarize the sprint outcome with the user:

1. **Interview findings grid** — observations per customer per sprint question
2. **Pattern summary** — top 3 signals (positive and negative)
3. **Sprint questions answered** — updated status for each
4. **Decision** — what happens next and why
