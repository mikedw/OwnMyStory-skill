# OwnMyStory — Executive Career Storytelling Skill

An AI-powered career coaching skill that guides professionals through leadership discovery, narrative synthesis, and STAR story generation for executive contexts.

## Overview

OwnMyStory is an AI agent skill designed to help executives craft compelling career narratives and behavioral stories. It guides users through a structured coaching conversation to discover their leadership identity and produce polished, executive-ready stories for:

- Networking and LinkedIn bios
- Board presentations and governance roles
- Promotion cases and career transitions
- Behavioral interviews at the executive level
- Stakeholder addresses and conference talks

## What This Skill Produces

| Output | Description | Use Case |
|---|---|---|
| **Executive Narrative (North Star)** | 3-part leadership identity: Strategic Motivation, Leadership Pillar, Value Proposition | Foundation for all storytelling — networking bios, LinkedIn, elevator pitches |
| **Executive STAR Stories** | Situation → Task → Action → Result stories aligned to career leverage scenarios | Board presentations, promotion cases, role transitions, behavioral interviews |
| **Inspirational Story** | 3-phase narrative: Hook → Journey → Vision | Stakeholder influence, team addresses, conference talks, networking |

## Workflow

```
Phase 1: DYNAMIC DISCOVERY (context gathering)
   Fixed opener → adaptive follow-ups → fixed closer
   + Optional: resume text, brain dump, prior narrative
          │
          ▼
Phase 2: EXECUTIVE NARRATIVE (intermediate)
   AI synthesizes → North Star (3 pillars)
   User approves or refines
          │
     ┌────┴─────┐
     ▼          ▼
Phase 3      Phase 4
STAR Stories Inspirational Story
(output)     (output)
```

The user may choose Phase 3, Phase 4, or both, and can iterate on any phase.

## Files

- `SKILL.md` — Full skill specification and workflow
- `references/prompts.md` — AI prompt templates for narrative and story generation
- `references/output_formats.md` — File output templates for exports

## Key Features

1. **Adaptive Discovery Conversation** — NOT fixed questions, but targeted follow-ups based on the user's responses
2. **Three-Pillar Synthesis** — Strategic Motivation, Leadership Pillar, Value Proposition
3. **STAR Story Generation** — For board opportunities, new roles, and promotion cases
4. **Inspirational Story Builder** — Hook → Journey → Vision structure

## Keywords

executive narrative, career story, STAR stories, behavioral interview, leadership discovery, north star, value proposition, board preparation, promotion case, role transition, career storytelling, executive coach, inspirational story
