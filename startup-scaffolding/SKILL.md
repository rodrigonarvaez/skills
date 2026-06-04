---
name: startup-scaffolding
version: 0.3.0
description: >
  Generates complete foundational documentation for a new business or startup idea.
  Trigger this skill immediately whenever the user says "Let's scaffold a startup",
  "Let's scaffold my business plan", "Let's create a business", "help me start a
  company", "I have a business idea", "I want to build a product", or any similar
  phrase expressing intent to launch, plan, or document a new venture — even if
  they haven't fully defined the idea yet. This skill produces a full structured
  artifact set: Vision Document, Validation Document, PRD, AI Instructions Document,
  and Project Description. Do NOT wait for the user to list requirements; start the
  intake interview immediately.
---

# Startup Scaffolding Skill

Produces a complete, investor-grade documentation suite for a new business or
product idea. Uses whatever AI tool the user is currently working with as the primary
AI for development support. Never assume a specific AI product — infer it from context
or ask during intake if unclear.

---

## Phase 1 — Intake Interview

Before writing anything, run a focused intake interview. Ask ALL of the following in
a single conversational message (not a wall of bullets — make it feel like a
co-founder conversation):

1. **Project name** — What are you calling this, even tentatively?
2. **The problem** — What frustrating thing exists in the world that you want to fix?
3. **Target audience** — Who suffers from this problem most acutely?
4. **Your angle** — Why are _you_ the right person to tackle this?
5. **Validation signal** — Have you talked to anyone who has this problem? If so, how many people, and what did you learn?
6. **Success horizon** — What does winning look like in 3 years?
7. **Primary platform** — Web app, mobile, API, marketplace, SaaS, physical product?
8. **Team & resources** — Solo founder, co-founder, team? Budget constraints?

If the user has already provided any of these in the conversation, extract them and
only ask about the gaps.

> **Default behavior — ask, don't assume**: Never fill in missing information with
> inferences or guesses. If something is unclear or unanswered, ask before writing.
> The goal is shared context, not a fast first draft. Every detail in the documents
> should come from the founder's own words.
>
> **Exception — user-directed placeholders**: If the founder explicitly says something
> like "assume X for now", "just use Y as a placeholder", or "we can decide that
> later", honor it. Record that item as `[placeholder — to be confirmed]` in the
> relevant document section so it's easy to find and revisit.

### Phase 1b — User Story Elicitation

After the main intake, run a dedicated story session _before_ writing the PRD.
Introduce it like this:

> "Now let's capture your user stories. I'll ask three questions per story — who,
> what, and why. Just answer naturally and I'll shape them into the right format.
> How many stories do you want to start with? (3–5 for MVP is a good starting
> point.)"

For each story, ask in sequence:

1. **Role** — "Who is doing this?" (Map to a persona name when possible.)
2. **Want** — "What do they want to _do_ — the specific action, not the outcome?"
3. **So that** — "Why does it matter to them? What changes when this works?"

Validate each answer before moving on:

- If the Want describes a feature or solution → redirect: _"What would they use
  that to actually do?"_
- If the So That is vague → probe: _"Can you be more specific — saves time, avoids
  an error, unblocks something?"_
- If one story contains multiple actions → split: _"Let's make that two stories."_

Once all stories are confirmed, flag any story where the founder was uncertain as
`[needs validation]`, then ask:

> "Great — I have everything I need to generate your full document suite: Vision,
> Validation, PRD, AI Instructions, Project Description, and a set of starter stubs
> for the rest of your repo. Ready for me to go ahead?"

Only proceed to Phase 2 after the founder confirms.

---

## Project Folder Structure

All generated documents map to this standard directory layout. When delivering,
label each output with its target file path so the user can drop it directly into
their repo.

```
/startup
    /business
        vision.md          ← Output 2 (Vision Document)
        validation.md      ← Output 3 (Validation Document)
        business-model.md  ← stub: mark as "to be completed"

    /product
        prd.md             ← Output 4 (PRD — problem, NFRs, features, phases)
        user-personas.md   ← extracted from PRD; standalone persona file
        roadmap.md         ← stub: seeded from Phased Plan in PRD

    /engineering
        architecture.md    ← stub: mark as "to be completed"
        decisions.md       ← stub: mark as "to be completed"
        coding-standards.md← stub: mark as "to be completed"

    /ai
        ai_context.md      ← Output 5 (AI Instructions Document)
        prompt-library.md  ← stub: mark as "to be completed"

    /metrics
        success-metrics.md ← stub: seeded from "Success in 3 Years" in Vision doc
```

For stub files, generate a minimal markdown file with:

- A one-line description of what belongs there
- A `## Status` section: `🔲 Not started — scaffold only`
- A `## Next Steps` prompt to guide the founder when they return to it

---

## Phase 2 — Generate the Document Suite

After intake, produce all 6 outputs in a single response. Structure them as clearly
separated sections with H2 headers. Prefix each section header with its target file
path, e.g. `### /startup/business/vision.md`. Each document is self-contained and
ready to copy into a repo, Notion, or Google Docs.

Use this exact output order:

### Output 1 — Project Name & Tagline `/startup/README.md` (header)

```
# [Project Name]
> [One-sentence tagline: what it does and who it's for]
```

---

### Output 2 — Vision Document

```markdown
## Vision Document — [Project Name]

### Problem

[2–3 sentences: the pain, the gap, the cost of inaction]

### Who Has This Problem

[Specific persona sketch: job title or life context, frequency of the problem,
emotional stakes]

### Why It Matters

[Market size signal or cultural/systemic reason this problem persists]

### Why You're the Right Person

[Founder-market fit: relevant experience, personal connection, unfair advantage]

### What Success Looks Like in 3 Years

- [Metric 1 — e.g., 10,000 paying users]
- [Metric 2 — e.g., $X ARR]
- [Milestone 3 — e.g., product in X industry/region]
- [Qualitative outcome — e.g., "users describe it as indispensable"]
```

---

### Output 3 — Validation Document

```markdown
## Validation Document — [Project Name]

### Who Has This Problem (Confirmed)

[Refine from Vision based on any interview data]

### Interviews Conducted

| #   | Role / Context             | Key Insight      |
| --- | -------------------------- | ---------------- |
| 1   | [e.g., Freelance designer] | [What they said] |
| …   | …                          | …                |

> If no interviews yet: note this as a gap and recommend 5–10 discovery conversations
> with the target persona before building. Provide 3 suggested interview questions.

### Current Solutions They Use

[List tools, workarounds, or behaviors people use today]

### Why Current Solutions Fall Short

[Gaps, friction, cost, missing features, or wrong job-to-be-done]

### Validation Gaps to Close

- [ ] [e.g., Interview 5 more users in the [X] segment]
- [ ] [e.g., Run a landing page smoke test]
- [ ] [e.g., Confirm willingness to pay]
```

---

### Output 4 — Product Requirements Document (PRD)

```markdown
## PRD — [Project Name]

**Version**: 0.1 — Pre-seed draft  
**Last updated**: [date]

### Problem Statement

[One crisp paragraph: the specific problem this product solves]

### Target Users

[2–3 sentence description of primary user segment]

---

### User Personas

#### Persona 1 — [Name]

- **Role / Context**: [e.g., Freelance UX designer, 3–7 years exp]
- **Goal**: [What they're trying to accomplish]
- **Pain point**: [The specific friction this product removes]
- **Tech comfort**: [Low / Medium / High]
- **Quote**: "[Fictional but realistic quote capturing their frustration]"

#### Persona 2 — [Name]

[Same structure]

---

### User Stories

**Must-have (MVP)**

- As a [role], I want to [action] so that [outcome].
- As a [role], I want to [action] so that [outcome].
- [3–5 total — elicited, not invented]

**Nice-to-have (V2+)**

- As a [role], I want to [action] so that [outcome].
- [2–3 total — elicited, not invented]

---

### Features

#### MVP (Ship to first 10 users)

| #   | Feature | Description    | Priority |
| --- | ------- | -------------- | -------- |
| 1   | [Name]  | [What it does] | P0       |
| 2   | [Name]  | [What it does] | P0       |
| …   | …       | …              | …        |

#### Future Features (Post-PMF)

| #   | Feature | Rationale   |
| --- | ------- | ----------- |
| 1   | [Name]  | [Why later] |

#### Phased Plan

| Phase                | Milestone                             | Target        |
| -------------------- | ------------------------------------- | ------------- |
| Phase 1 — Foundation | Core loop working, 10 beta users      | [Month range] |
| Phase 2 — PMF Search | 100 active users, validated retention | [Month range] |
| Phase 3 — Growth     | Paid tier, referral loop, team growth | [Month range] |

---

### Non-Functional Requirements

- **Performance**: [e.g., Page load <2s, API response <500ms]
- **Security**: [e.g., Auth via OAuth2, no PII stored without consent]
- **Scalability**: [e.g., Must support 10k concurrent users by Phase 3]
- **Accessibility**: [e.g., WCAG 2.1 AA]
- **Availability**: [e.g., 99.9% uptime SLA]
- **Data & Privacy**: [e.g., GDPR-compliant, data deletion on request]
```

---

### Output 5 — AI Instructions Document

This document defines how the AI assistant should help throughout the project lifecycle.
Tailor to the product type. Replace "[AI tool]" throughout with the actual AI the
founder is using (e.g., Claude, ChatGPT, Copilot).

```markdown
## AI Instructions — [Project Name]

> This document tells [AI tool] how to assist on this project. Paste it at the start
> of any new conversation to re-establish context.

### Project Context

[Project name], [one-line description], targeting [persona]. Stack: [tech stack if
known]. Current phase: [Discovery / Build / Launch / Growth].

### How to Help

**When I ask for code:**

- Default stack: [e.g., TypeScript, React, Node.js, serverless]
- Follow REST / OpenAPI conventions
- Write clean, commented code; avoid over-engineering for MVP
- Flag any security or scalability concerns inline

**When I ask for product decisions:**

- Ask clarifying questions before recommending; don't assume scope
- Present trade-offs (speed vs. quality, cost vs. control)
- Prioritize user value over technical elegance

**When I ask for copy or content:**

- Voice: [e.g., Direct, warm, jargon-free]
- Audience: [primary persona]
- Avoid hype language; be specific and concrete

**When I share user research or feedback:**

- Help me identify patterns and themes
- Challenge my assumptions if data suggests otherwise
- Suggest follow-up questions I should ask

### Guardrails

- Don't add features to the roadmap without flagging it
- Don't assume I want a full implementation — ask if I want a plan, a draft, or
  a full build
- If a request could affect security or privacy, flag before proceeding

### Context to Always Keep in Mind

- [Any domain-specific constraint, regulation, or business rule]
- [Budget or timeline pressure if relevant]
- [The one metric that matters most right now]
```

---

### Output 6 — Project Description `/startup/README.md` (body)

A short, portable overview for README files, pitch decks, or social sharing.

```markdown
## Project Description — [Project Name]

**[Project Name]** is a [product type] that helps [target user] [achieve outcome]
by [core mechanism].

**The problem**: [One sentence.]

**Our solution**: [One to two sentences on the core product value.]

**Who it's for**: [Primary persona, described plainly.]

**Current stage**: [Pre-seed / Validation / MVP / Beta / Live]

**Built with** _(if known)_: [Stack]

**AI-assisted development**: This project uses [AI tool] to support product design,
engineering, and content decisions throughout the build.
```

---

### Output 7 — Stub Files

Generate the following stub files after the 6 main outputs. Each stub uses this
format:

```markdown
# [Document Title]

[One-line description of what belongs in this file]

## Status

🔲 Not started — scaffold only

## Next Steps

[One or two prompts guiding the founder on what to fill in here and when]
```

| File path                                  | Title            | Next Steps prompt                                                                    |
| ------------------------------------------ | ---------------- | ------------------------------------------------------------------------------------ |
| `/startup/business/business-model.md`      | Business Model   | Define revenue streams, pricing, and cost structure once the MVP is validated.       |
| `/startup/product/roadmap.md`              | Product Roadmap  | Seed from the Phased Plan in your PRD; expand timelines as the team grows.           |
| `/startup/engineering/architecture.md`     | Architecture     | Sketch the system design once you've chosen your core stack.                         |
| `/startup/engineering/decisions.md`        | Decision Log     | Record architecture and product decisions here as you make them, with the rationale. |
| `/startup/engineering/coding-standards.md` | Coding Standards | Define conventions, linting rules, and patterns once your first engineer joins.      |
| `/startup/ai/prompt-library.md`            | Prompt Library   | Collect reusable prompts for recurring tasks as you discover them during the build.  |

---

## Phase 3 — Delivery Notes

After generating all 6 outputs:

1. **Review open placeholders** — List any items marked `[placeholder — to be confirmed]`
   and note which document and section they appear in. Prompt the founder to schedule
   time to resolve each one before the next build phase.
2. **Flag the biggest risk** — One honest sentence about the hardest thing to validate.
3. **Suggest the next action** — What should the founder do in the next 7 days?
   (Usually: talk to 5 real users _or_ build the smallest possible demo.)

---

## Handling Edge Cases

| Situation                                 | How to handle                                                                                                                                                                                     |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| User hasn't answered all intake questions | Do not proceed to document generation. Ask the remaining questions first, one round at a time if needed.                                                                                          |
| User says "assume X for now"              | Record X as `[placeholder — to be confirmed]` in the relevant section; continue.                                                                                                                  |
| User has no validation data               | Ask directly: "Have you spoken to anyone with this problem yet?" If no, note the gap in the Validation doc with 3 suggested discovery questions and a checklist. Do not fabricate interview rows. |
| User has a very technical idea            | Ask: "Who is the non-technical end user, if any?" before writing personas.                                                                                                                        |
| User is a solo non-technical founder      | In AI Instructions, emphasize no-code / low-code paths; note the current AI tool as primary builder.                                                                                             |
| User wants only one document              | Clarify which one, generate it fully, and note which others remain.                                                                                                                               |
| B2B vs B2C                                | Adjust personas (buyer vs. user split for B2B); add champion/economic buyer distinction in PRD.                                                                                                   |
| Physical product                          | Adjust NFRs; replace scalability section with manufacturing/supply chain constraints.                                                                                                             |

---

## Quality Bar

Every document should pass this test before delivery:

- [ ] Would a first-time reader understand who this is for and why it exists?
- [ ] Are the user stories specific enough to estimate effort?
- [ ] Does the phased plan reflect realistic startup sequencing?
- [ ] Could a developer open the AI Instructions doc and immediately know how to help?
- [ ] Is the Project Description usable in a README or pitch deck as-is?

If any answer is "no", improve before delivering.
