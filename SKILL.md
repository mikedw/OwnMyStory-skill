---
name: ownmystory
description: Executive career storytelling harness — an agentic coaching loop with persistent story-bank memory, red-team interrogation, and multi-format deploy. Guides professionals through leadership discovery, narrative synthesis, STAR story generation, adversarial refinement, and rendering stories for interviews, networking, and LinkedIn. Use whenever the user wants to craft their career story, bank and refine STAR stories over time, pressure-test a story like a skeptical interviewer would, prepare executive narratives, generate STAR-format behavioral stories, build inspirational stakeholder narratives, prepare for board positions, promotions, or role transitions, or articulate their leadership identity. Also use when users mention "story bank", "red team my story", "north star narrative", "executive story", "leadership discovery", "career storytelling", or "agentic storytelling harness".
---

# OwnMyStory v2 — Executive Career Storytelling Harness

*OwnMyStory — Because the best leaders tell the best stories.*

## What This Harness Produces

| Output | Description | Use Case |
|---|---|---|
| **Story Bank (Memory)** | Persistent, versioned repository of stories, stubs, and competency coverage | Compounding career storytelling across sessions |
| **Executive Narrative (North Star)** | 3-part leadership identity: Strategic Motivation, Leadership Pillar, Value Proposition | Foundation for all storytelling — networking bios, LinkedIn, elevator pitches |
| **Red-Teamed STAR Stories** | Situation → Task → Action → Result stories stress-tested by a skeptical interviewer loop | Board presentations, promotion cases, role transitions, behavioral interviews |
| **Inspirational Story** | 3-phase narrative: Hook → Journey → Vision | Stakeholder influence, team addresses, conference talks, networking |
| **Deploy Formats** | Any banked story rendered as a 2-min interview answer, 30-sec intro, or LinkedIn post | Last-mile delivery for the exact room or channel |

## What Changed in v2 (the Harness Upgrade)

v1 was a **skill**: a coaching script the AI runs once per session — adaptive discovery, narrative synthesis, story generation. It worked, but every session started from zero.

v2 is a **harness**: everything around the skill that makes the AI actually coach — it **remembers** your stories across sessions (Story Bank), **interrogates** them like a skeptical interviewer (Red-Team Loop), **deploys** them in the format each moment needs (Deploy Formats), and **comes to you** so the bank keeps growing (Proactive Capture).

| v1: the Skill | v2: the Harness |
|---|---|
| Single-session coaching script | Persistent loop across sessions |
| AI as editor — polishes what you bring | AI as coach — interviews, pushes back, remembers |
| Stories generated, then forgotten | Every story banked, tagged, versioned |
| You hope the story is strong | Red-team loop proves it before you walk in |
| One output format | Interview answer, 30-sec intro, LinkedIn post |

## The Harness Loop

```
 ┌──────────────────────────────────────────────────────┐
 │  PHASE 0: STORY BANK (memory — persists everything)  │
 └───────────────────────┬──────────────────────────────┘
                         ▼
 ┌──────────────┐   ┌──────────────┐   ┌──────────────┐
 │ PHASE 6      │   │ PHASE 1      │   │ PHASE 2      │
 │ CAPTURE      │──▶│ DISCOVERY    │──▶│ NARRATIVE    │
 │ weekly nudge │   │ adaptive     │   │ North Star   │
 │ quick stubs  │   │ interview    │   │ synthesis    │
 └──────────────┘   └──────────────┘   └──────┬───────┘
                                             ▼
                        ┌─────────────────────────────────┐
                        │ PHASE 3: STAR STORY GENERATION  │
                        └────────────────┬────────────────┘
                                         ▼
                        ┌─────────────────────────────────┐
                        │ PHASE 3b: RED-TEAM LOOP         │
                        │ interrogate → refine (max 2x)   │◀┐
                        └────────────────┬────────────────┘ │
                                         │  score < bar ────┘
                                         ▼  score ≥ bar
                        ┌─────────────────────────────────┐
                        │ PHASE 0: BANK IT (save+version) │
                        └────────────────┬────────────────┘
                        ┌────────────────┴────────────────┐
                        ▼                                 ▼
              ┌──────────────────┐            ┌──────────────────┐
              │ PHASE 4          │            │ PHASE 5: DEPLOY  │
              │ INSPIRATIONAL    │            │ interview /      │
              │ STORY BUILDER    │            │ networking /     │
              └──────────────────┘            │ LinkedIn         │
                                              └──────────────────┘
```

The loop never really ends: deployed stories create new experiences worth capturing, and capture feeds the next session. That compounding is the whole point of the harness.

---

## Phase 0: Story Bank (Memory)

The bank is the harness's memory. Without it, every session starts from zero; with it, the user's storytelling compounds.

### Session Start

At the start of every session, check for an existing bank (in conversation memory or provided by the user) and report:

> "Welcome back. You have **N stories** banked across **M competencies**. Strong coverage: [competencies with 2+ stories]. Gaps: [competencies with 0–1 stories]. What are we working on today?"

If no bank exists, create one and say so. Ask if the user has existing materials (a prior Story Bank markdown export, Executive Narrative, resume text, or career notes). If the user has an approved Executive Narrative from a prior session, load it — do not re-run discovery unless asked.

### Bank Schema

Each banked story carries:

- **id** — short slug (e.g., `launch-turnaround-2024`)
- **title, competency, category, tags, leverage_types**
- **situation / task / action / result** — the STAR body
- **reflection, executive_insight**
- **metrics_status** — `confirmed` (real numbers, user-verified) or `placeholder` (X%, $Y — still needs real numbers)
- **versions[]** — every refinement kept; never overwrite, always version
- **formats{}** — which deploy formats exist: `interview_answer`, `networking_intro`, `linkedin_post`
- **created, updated**

### Bank Commands

The user may at any time say: `bank list`, `bank search [competency or tag]`, `bank refine [id]`, `bank deploy [id] [format]`, `bank gaps` (show thin competencies).

### Auto-Bank Rule

Every story produced in Phase 3 or 4 is appended to the bank automatically unless the user declines. Before banking, check for near-duplicates against existing stories — if one is similar, offer to **merge** (new version of the existing story) rather than creating a duplicate.

### Storage

When the user requests export, save the bank as markdown. See `references/output_formats.md` → Section "Story Bank" for the exact file template.

---

## Phase 1: Dynamic Discovery

### Offer Two Entry Modes

Start by offering **Full Discovery** or **Quick Capture mode**:

> "Two ways in: the full discovery interview (3–5 questions, ~10 minutes), or quick capture — drop a 60-second brain dump of something that happened and I'll turn it into a story stub we refine later."

### Mode A: Full Discovery Conversation

Conduct an adaptive coaching conversation:

**1. Fixed Opener** (always the same):
> "Tell me about where you are in your career and what's driving you to think about what's next."

**2. After each response, internally assess three pillars:**

| Pillar | What to Listen For | Rated As |
|---|---|---|
| **Strategic Motivation** | Career ambitions, reasons for change, what excites them | strong / partial / missing |
| **Leadership Pillar** | Team building, conflict resolution, defining leadership moments | strong / partial / missing |
| **Value Proposition** | Signature achievements, systemic impact, quantifiable results | strong / partial / missing |

**3. Generate a targeted follow-up** for the weakest pillar. The follow-up MUST:
- Reference the user's specific words, examples, or themes from their prior answers
- Feel conversational — like building on what they shared, not a form field
- Never repeat something they've already covered well

**Example follow-ups by target pillar:**

| Pillar | Example |
|---|---|
| Strategic Motivation | *"You mentioned [X] — it sounds like there's a bigger ambition behind that. What does the next chapter look like?"* |
| Leadership Pillar | *"You mentioned navigating [X] — walk me through how you led the team through that."* |
| Value Proposition | *"The [X] transformation is compelling. If you had to quantify that impact, what would the numbers look like?"* |

**4. Fixed Closer** (when 2+ pillars are strong, remaining is at least partial):
> "Based on everything you've shared — in one sentence, what do you bring that no one else can?"

**5. Exit** when all 3 pillars are strong OR the closer has been answered. Typical: 3 questions. Maximum: 5.

**6. Collect optional inputs:**
- **Resume text**: *"Would you like to provide CV/resume text to strengthen the AI's story generation?"*
- **Brain dump**: *"Any additional career notes — achievements, metrics, team sizes?"*

### Mode B: Quick Capture Mode

Read `references/prompts.md` → Section "Capture Prompts" for the stub extraction prompt.

Accept any raw dump (text or transcribed voice). Extract: a working title, a 2-line situation sketch, and 2–3 open questions the follow-up loop will need answered. Save as a `draft` stub in the bank with `metrics_status: placeholder`. Tell the user what's missing and that the red-team loop will demand it later.

---

## Phase 2: Executive Narrative Synthesis

Read `references/prompts.md` → Section "Narrative Generation Prompt" for the exact prompt specification. If a prior approved narrative exists in the bank, reuse it unless the user wants to refresh it.

### Generate the Narrative

Feed all discovery Q&A pairs + resume text + brain dump into the narrative generation prompt. The output has exactly three fields:

- **Strategic Motivation** — What drives their career trajectory (2–3 sentences)
- **Leadership Pillar** — Core leadership philosophy in practice (2–3 sentences)
- **Value Proposition** — Unique differentiating value (1–2 sentences)

### Present for Approval

```
═══════════════════════════════════════════
         EXECUTIVE NARRATIVE — NORTH STAR
═══════════════════════════════════════════

🚀 STRATEGIC MOTIVATION
"{strategic_motivation}"

🏛 LEADERSHIP PILLAR
"{leadership_pillar}"

⭐ VALUE PROPOSITION
"{value_proposition}"

═══════════════════════════════════════════
```

Offer the user: approve → Phase 3/4, refine → continue conversation, or edit directly.

---

## Phase 3: Executive STAR Story Generation

**Prerequisite:** Approved Executive Narrative.

Read `references/prompts.md` → Section "Executive Story Generation Prompt" for the exact prompt specification.

### Select Leverage Type

| Type | Focus |
|---|---|
| `board_opportunity` | Board-level strategic thinking, governance, enterprise-wide impact |
| `new_role` | Adaptability, vision-setting, rapid value creation in new environments |
| `promotion` | Increased scope readiness, team scaling, organizational transformation |

### Generate 3 Stories

Each story contains: title, competency, category, tags, situation, task, action (most detailed), result (with metric placeholders if needed), reflection, executive_insight, estimatedReadTime.

### Present Each Story

```
📌 [Competency]     ⏱ [Read Time]
   Category: [Category Label]

"[Title]"

── S │ SITUATION ──
[situation]

── T │ TASK ──
[task]

── A │ ACTION ⭐ ──
[action]

── R │ RESULT 📊 ──
[result]

💡 Reflection: "[reflection]"
🔗 Executive Insight: "[executive_insight]"
Tags: #[tags]
```

Every story generated or selected for refinement flows into **Phase 3b (Red-Team Interrogation Loop)** before final banking.

---

## Phase 3b: Red-Team Interrogation Loop (NEW)

Read `references/prompts.md` → Section "Red-Team Interrogation Prompt" for the exact prompt specification.

This is the agentic heart of the harness. The agent switches roles from coach to **skeptical executive interviewer** and stress-tests the story before it ever reaches a real room.

### The Scorecard

Score the story 1–5 on four dimensions:

| Dimension | What earns a 5 |
|---|---|
| **Action Specificity** | "I" actions are concrete and verifiable; no hiding behind "we"; specific verbs, decisions, and moments |
| **Quantified Result** | Real numbers with context; placeholders explicitly flagged, never fudged |
| **STAR Balance** | Situation + Task are tight; Action + Result carry the weight — the story *proves*, not just tells |
| **Authenticity Risk** | No inflated claims, no generic platitudes, no borrowed glory — a sharp interviewer would believe it |

### The Loop

1. Present the scorecard with one-line justification per dimension.
2. Ask **up to 3 probing questions**, targeting the weakest dimensions. Examples:
   - *"You said 'we turned it around' — what did* you *personally decide or do that no one else did?"*
   - *"The result says 'significant improvement' — what was the number? If you don't have it, what's your best estimate and how would you verify it?"*
   - *"A skeptical interviewer will ask what went wrong. What's the honest version?"*
3. Regenerate the story incorporating the answers. Re-score.
4. **Exit:** all dimensions ≥ 4, or 2 loops completed — then present the best version with honest flags (e.g., "Result still needs a real number — fill this in before you use it").

### Present Before / After

Always show what changed: 2–3 bullets of what the interrogation caught and fixed so the user clearly sees how the story got sharper.

### Bank It & Offer Next Steps

The surviving story is banked (Phase 0) as a new version, with `metrics_status` set honestly. Then offer: red-team another story, deploy this story into a format (Phase 5), move to Phase 4, or export.

---

## Phase 4: Inspirational Story Builder

**Prerequisite:** Approved Executive Narrative.

Read `references/prompts.md` → Section "Inspirational Refine Prompt" for the exact prompt specification.

### The 3 Phases

| Phase | Name | Length | Connects To |
|---|---|---|---|
| `hook` | The Hook — Opening with Impact | 2–4 sentences | Strategic Motivation |
| `journey` | The Journey — Conflict & Strategic Pivot | 3–5 sentences | Leadership Pillar |
| `vision` | The Vision — Resolution & Future Call to Action | 2–4 sentences | Value Proposition |

### For Each Phase, Offer Three Paths

1. **AI Generate** — from scratch based on the narrative
2. **User Writes** — collect their text
3. **AI Refine** — improve their draft

### Present Complete Story

```
═══════════════════════════════════════════
         YOUR INSPIRATIONAL STORY
═══════════════════════════════════════════

── PHASE ONE ─────────────────────────────
   The Hook — Opening with Impact
   "[hook]"

── PHASE TWO ─────────────────────────────
   The Journey — Conflict & Strategic Pivot
   "[journey]"

── PHASE THREE ───────────────────────────
   The Vision — Resolution & Future Call to Action
   "[vision]"
═══════════════════════════════════════════
```

Completed inspirational stories are auto-banked (Phase 0).

---

## Phase 5: Deploy Formats (NEW)

Read `references/prompts.md` → Section "Deploy Format Prompts" for the exact prompt specification.

One banked story, rendered for the moment it's needed. Generate on demand via `bank deploy [id] [format]` (or whenever the user asks to adapt a story for an interview, intro, or LinkedIn):

| Format | Spec |
|---|---|
| `interview_answer` | ~2 minutes spoken. Conversational register, not written prose. Tight situation, decisive actions, crisp result. Ends cleanly — no trailing. |
| `networking_intro` | ~30 seconds. Hook + one proof point + forward lean ("which is why I'm focused on…"). Designed to be said aloud to a stranger. |
| `linkedin_post` | 150–220 words. Opening hook line, short paragraphs, concrete detail over adjectives. Executive tone — no hashtag spam, no hustle clichés. |

All formats inherit the guardrails: never fabricate metrics (carry placeholders through and flag them), preserve the user's voice, keep narrative alignment with the North Star pillars.

---

## Phase 6: Proactive Capture (NEW)

Read `references/prompts.md` → Section "Capture Prompts" for exact nudge and stub-extraction prompts.

The harness comes to the user, so the bank compounds without heroic effort. (In scheduled/agentic setups, run these as nudges; in chat, offer them.)

**Weekly nudge:**

> "Story-banking minute — what happened this week worth keeping? A win, a hard conversation, or something you'd do differently — 60 seconds, messy is fine."

**Interview debrief:** after a real interview, the user pastes the questions they were asked. The agent maps them against bank coverage, flags gaps ("you had nothing strong for conflict — let's build one"), and creates stubs for the missing stories.

**Stub lifecycle:** every stub enters the bank as `draft` → gets refined through Phases 1–3b when the user has time → graduates to `ready`. The bank should always show the pipeline: how many drafts are waiting. A bank full of drafts and no ready stories is a dashboard warning, stated plainly.

---

## Output Files

When the user requests export, save artifacts as markdown (`executive_narrative.md`, `executive_star_stories.md`, `inspirational_story.md`, `story_bank.md`). See `references/output_formats.md` for exact file templates.

---

## Key Guardrails

1. **Never fabricate metrics** — use placeholder variables (X%, $Y, Z) when real numbers aren't available. Placeholders must survive every format and be flagged every time.
2. **Narrative alignment** — every story connects back to the 3 North Star pillars.
3. **Diverse competencies** — each batch highlights different competencies.
4. **Authentic voice** — use the user's actual language from their inputs.
5. **Executive register** — confident, polished prose (no bullet-point stories).
6. **Respect prior work** — when refining, preserve voice and intent.
7. **Red-team honesty** — never soften a weak story to spare feelings. Flag it, say what would fix it, and loop. A kind lie here costs the user a real opportunity.
8. **Bank integrity** — dedupe before banking; version, never overwrite; metric placeholders always marked.
9. **Loop discipline** — maximum 2 red-team loops per story; always exit with a usable artifact, not perfection. Momentum beats polish.

---

## Keywords

executive narrative, career story, STAR stories, behavioral interview, leadership discovery, north star, value proposition, board preparation, promotion case, role transition, career storytelling, executive coach, inspirational story, story bank, red team, agentic loop, storytelling harness, interview preparation, networking intro, LinkedIn storytelling
