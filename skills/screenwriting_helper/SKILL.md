---
name: screenwriting-helper
description: >
  Use when writing, developing, or analyzing screenplays, scripts, stories, or narrative outlines
  for film or TV. Also use when brainstorming movie/show ideas, creating characters, building
  beat sheets, writing dialogue, diagnosing script weaknesses, or working with storytelling
  frameworks (Save the Cat, Hero's Journey, Story Circle). Applies to short films, features,
  TV pilots, and Indian cinema traditions (Tollywood, Bollywood).
---

# Screenwriting Craft Skill

A comprehensive storytelling craft system distilled from the best screenwriting literature (Iglesias, Snyder, McKee, Swain, Bell, Cleland, Campbell, and others), reorganized by workflow rather than topic.

## Approach

This skill presents frameworks, checklists, and techniques as **options and tools** — not rules. The user decides which frameworks to adopt, which to ignore, and when to break conventions deliberately. Claude's job is to surface the relevant craft knowledge, explain trade-offs, and support the user's creative vision.

When generating structured analysis (character sheets, beat sheets, diagnostic reports), create files (.md or .docx). For brainstorming, ideation, and exploratory discussion, stay conversational.

## Quick-Reference: Story Essentials Checklist

Before diving into any reference file, this checklist applies universally. A compelling story needs all 8:

1. **CHARACTER** — An empathetic, proactive vessel for the audience
2. **GOAL** — One strong main goal that sets the story in motion
3. **STAKES** — Why the goal matters; consequences of failure
4. **CLOCK** — Why the goal must be pursued now, not later
5. **OBSTACLE** — What prevents easy achievement of the goal
6. **ENDING** — Resolution that answers dramatic questions
7. **THEME** — A philosophical argument underlying the surface conflict
8. **CHANGE** — Something meaningful is different by the end

## Quick-Reference: Character Checklist

For any character of significance, consider:

1. Basics (name, age, occupation, etc.)
2. A Limp and an Eyepatch (distinguishing trait/mannerism)
3. Emotion Evoked (what should the audience feel?)
4. Traits (positive and negative surface characteristics)
5. Values / Ideology (what shapes their worldview?)
6. Flaw (psychological error that hinders them)
7. Past Wound (what made them this way?)
8. Secret (what are they hiding?)
9. Goals + Stakes
10. Want (conscious motivation) vs Need (deeper yearning)
11. Arc (which of the 5 arc types?)

## Cross-Cutting Principles

These apply regardless of which reference file is loaded:

- **Conflict in every scene** — If a scene lacks conflict (internal or external), it should be reworked or cut
- **Change in every scene** — Something must be different by the end of each scene
- **Show, don't tell** — Reveal through action, decision, and subtext rather than direct statement
- **Efficiency** — Every scene must serve plot, character, or theme (ideally 2-3 at once)
- **"Give them 2+2, not 4"** (Andrew Stanton) — Trust the audience to connect dots

## Workflow Routing

Based on what the user needs, read the appropriate reference file(s) before responding. Multiple files can be loaded for complex requests.

### IDEATION MODE
**When**: User is brainstorming, developing an initial concept, asking "what if," or needs help turning a seed idea into a full story.
**Load**: `references/01-ideation.md`

### CHARACTER MODE
**When**: User is creating, developing, or deepening characters; working on protagonist empathy, antagonist design, or character relationships.
**Load**: `references/02-character-design.md`

### STRUCTURE MODE
**When**: User is outlining, building a beat sheet, working on act structure, choosing a theme, or designing scene-sequel flow.
**Load**: `references/03-theme-and-structure.md`

### WRITING MODE
**When**: User is writing or rewriting actual scenes — dialogue, openings, comedy, exposition.
**Load**: `references/04-scene-craft.md`

### TENSION MODE
**When**: User wants to build suspense, create mystery/intrigue, design reveals, or plan setup/payoff chains.
**Load**: `references/05-tension-engine.md`

### POLISH MODE
**When**: User is working on emotional impact, pacing, tone, subplot integration, endings, or twists.
**Load**: `references/06-emotion-and-polish.md`

### DIAGNOSTIC MODE
**When**: User wants their script, outline, or story analyzed for weaknesses.
**Load**: `references/07-script-doctor.md`

### INDIAN CINEMA MODE
**When**: User references Indian cinema, Tollywood, Bollywood, regional Indian film, or wants to incorporate Indian storytelling traditions.
**Load**: `references/08-indian-cinema.md` (plus whatever other reference is relevant)

## Output Formats

- **Conversational**: Default for brainstorming, discussion, quick feedback
- **Markdown file (.md)**: Beat sheets, character sheets, diagnostic reports, outlines
- **Document file (.docx)**: Polished deliverables for sharing or printing
- **Artifact (.jsx)**: Interactive tools when explicitly requested

## When Multiple Modes Apply

Load all relevant reference files and synthesize. Examples:
- "My protagonist feels flat" → CHARACTER + DIAGNOSTIC
- "Write the opening scene of my thriller" → WRITING + TENSION
- "Help me outline a story about a man returning to India" → IDEATION + STRUCTURE + INDIAN CINEMA
- "The ending doesn't land emotionally" → POLISH + DIAGNOSTIC
