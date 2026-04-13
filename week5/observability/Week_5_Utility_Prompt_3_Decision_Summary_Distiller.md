# Decision Summary Distiller

## Purpose

This utility prompt takes your skill's **reasoning-enriched output** (after you've used the Socratic Reasoning Auditor and the Coding Agent Instruction Template) and distills it into a **human-readable Decision Summary** you can present at demo day.

The Decision Summary answers two questions a non-technical audience will ask:

1. **"Why did the agent do this?"**
2. **"How do you know it didn't hallucinate?"**

---

## Where This Fits

| Step | Tool | Status |
|------|------|--------|
| 1. Audit | Socratic Reasoning Auditor | ✅ Done — gaps identified |
| 2. Implement | Coding Agent Instruction Template | ✅ Done — reasoning added to skill output |
| **3. Distill** | **This prompt** | **← You are here** |

---

## Prerequisites

Before using this prompt, verify:

- [ ] You ran the Socratic Reasoning Auditor (Prompt 1) and identified gaps
- [ ] You used the Coding Agent Instruction Template (Prompt 2) to add reasoning to your skill
- [ ] You re-ran your skill and the output **now includes reasoning** (not just results)
- [ ] The reasoning is specific (not generic filler like "this was the best option")

**If your skill output still has no reasoning, STOP.** Go back to Prompt 2. You can't distill what doesn't exist.

---

## What You'll Get

A **Decision Summary** — a polished, structured document that:

- Explains what the skill did and why
- Shows what was selected and what was rejected (with reasons)
- Flags confidence levels and uncertainty
- Is written in plain language for a non-technical audience
- Is ready to present on screen during your demo

---

## Instructions

1. Run your skill on a **representative sample input** (the same one you'll use at demo day if possible)
2. Copy the **full output** including all reasoning sections
3. Paste the prompt below into an external AI (ChatGPT, Claude, etc.)
4. Replace all `[BRACKETED PLACEHOLDERS]` with your actual content
5. Review the generated Decision Summary
6. Save it alongside your skill output as a demo artifact

---

## The Prompt

Copy everything inside the fence below:

````markdown
You are a Technical Writer specializing in AI Explainability.

Your job is to take the raw output of an AI agent skill — including
its reasoning — and distill it into a polished, human-readable
Decision Summary that a non-technical audience can understand.

You do NOT add reasoning that isn't in the output.
You do NOT invent justifications.
You ONLY organize, clarify, and polish what already exists.

## CONTEXT

### About the Audience
The Decision Summary will be presented to:
- Course instructors
- Fellow students (business analysts, not developers)
- Potentially external stakeholders or clients

None of them will read code. None of them will read logs.
They need to understand WHAT the skill did and WHY — in plain language.

### About the Skill
**Skill Name:** [YOUR SKILL NAME]
**What it does:** [ONE-SENTENCE DESCRIPTION]
**Sample input used:** [BRIEF DESCRIPTION OF THE INPUT YOU RAN]

### The Skill's Full Output (Including Reasoning)
```
[PASTE YOUR SKILL'S COMPLETE OUTPUT HERE — INCLUDING ALL
REASONING SECTIONS ADDED VIA PROMPT 2]
```

## YOUR TASK

Distill the output above into a Decision Summary using the
exact structure below. Follow these rules:

### Rules

1. **Only use information present in the output.**
   Do not infer, assume, or fabricate reasoning.
   If the output doesn't explain a decision, write:
   "⚠️ No reasoning provided for this decision."

2. **Plain language only.**
   No jargon. No code references. No variable names.
   Write as if explaining to a smart person who has never
   seen a terminal.

3. **Be specific.**
   "Selected because it had the highest relevance score"
   is too vague.
   "Selected because the speaker introduced the core argument
   about AI regulation, which matches the target topic keyword"
   is specific.

4. **Preserve uncertainty.**
   If the skill flagged low confidence or uncertainty,
   include it. Do not smooth over doubt.

5. **Keep it concise.**
   The entire Decision Summary should fit on one screen
   (roughly 300–500 words). This is a demo artifact,
   not a research paper.

## OUTPUT FORMAT

Return the Decision Summary in this exact structure:

---

# Decision Summary — [Skill Name]

## Run Context
- **Input:** [What was fed to the skill — one sentence]
- **Date:** [When this was run]
- **Skill Version:** [If available, otherwise omit]

## What the Skill Did
[2–3 sentences summarizing the overall action. What went in,
what came out, and the scale of the work.]

## Key Decisions Made

### Decision 1: [Short Label]
- **What:** [What was decided]
- **Why:** [The reasoning from the output — quote or paraphrase]
- **Alternatives Considered:** [What else was possible, if stated]
- **Why Alternatives Were Rejected:** [Reason, if stated]

### Decision 2: [Short Label]
- **What:** [What was decided]
- **Why:** [The reasoning from the output]
- **Alternatives Considered:** [If stated]
- **Why Alternatives Were Rejected:** [If stated]

### Decision 3: [Short Label]
[Continue as needed — typically 3–5 key decisions]

## What Was Selected

| Item | Reason Selected |
|------|-----------------|
| [Item 1] | [Specific reason from the output] |
| [Item 2] | [Specific reason from the output] |
| [Item 3] | [Specific reason from the output] |

## What Was Rejected

| Item | Reason Rejected |
|------|-----------------|
| [Item A] | [Specific reason from the output] |
| [Item B] | [Specific reason from the output] |

*If the output does not mention rejected items, write:
"The skill's output did not document rejected alternatives.
Consider adding rejection reasoning via the Socratic Reasoning
Auditor (Prompt 1)."*

## Confidence Assessment

| Area | Confidence | Reasoning |
|------|------------|-----------|
| [Area 1] | 🟢 High / 🟡 Moderate / 🔴 Low | [Why — from the output] |
| [Area 2] | 🟢 High / 🟡 Moderate / 🔴 Low | [Why — from the output] |

*If the output includes no confidence signals, write:
"⚠️ The skill did not flag confidence levels. All results
are presented without qualification. Consider adding confidence
signals via the Socratic Reasoning Auditor (Prompt 1)."*

## Hallucination Check

Answer these questions based ONLY on what the output contains:

| Question | Answer |
|----------|--------|
| Does every output trace back to specific input data? | ✅ Yes / ❌ No / ⚠️ Partially |
| Are there any claims not supported by the input? | ✅ None found / ❌ Yes — [describe] |
| Did the skill generate content not present in the source? | ✅ No / ❌ Yes — [describe] |

*This section helps the presenter answer: "How do you know
it didn't hallucinate?"*

## Limitations & Caveats

List any limitations, edge cases, or caveats mentioned in the output:

- [Limitation 1]
- [Limitation 2]

*If none are mentioned, write:
"The skill's output did not document limitations. Consider
running edge-case tests and documenting results."*

## One-Sentence Summary

[A single sentence a presenter can say out loud:
"Our [skill name] analyzed [input] and produced [output]
because [key reasoning]."]

---
````

---

## After You Receive the Decision Summary

### Step 1: Verify Accuracy

Read through the Decision Summary and check:

| Check | ✅ |
|-------|---|
| Every "Why" traces back to something in the skill's actual output | ☐ |
| No reasoning was invented or assumed by the Distiller | ☐ |
| Confidence levels match what the skill actually reported | ☐ |
| The Hallucination Check is honest (not just "all good") | ☐ |
| Plain language throughout — no jargon, no code references | ☐ |

### Step 2: Check for ⚠️ Flags

If the Distiller inserted any ⚠️ warnings like:
- "No reasoning provided for this decision"
- "The skill did not document rejected alternatives"
- "The skill did not flag confidence levels"

These are **gaps that still exist in your skill's output**. You have two options:

| Option | When to Use |
|--------|-------------|
| **Go back to Prompt 1 → 2** | If the gap is significant and would be embarrassing at demo day |
| **Document as a known limitation** | If the gap is minor and you're running out of time |

### Step 3: Practice the One-Sentence Summary

The last line of the Decision Summary is your **elevator pitch**. Practice saying it out loud. If it doesn't flow naturally, rewrite it until it does.

This is what you'll say when someone asks: "So what does your skill do?"

### Step 4: Save as a Demo Artifact

Save the Decision Summary as `decision-summary.md` in your skill folder:

```
.skills/your-skill/
├── SKILL.md
├── prompts/
├── code/
├── recipes/
└── decision-summary.md    ← NEW
```

Commit it:

```bash
git add .skills/your-skill/decision-summary.md
git commit -m "docs: add decision summary for demo"
git push origin main
```

---

## Example: Before and After

### Before (Raw Skill Output — After Prompt 2)

```
Processed transcript: Episode 47 — "AI in Healthcare" (42:18)

Identified 5 candidate segments.

Selected 3 clips:

Clip 1 (04:12 – 06:45):
  Reason: Speaker introduced the core argument about AI diagnostic
  accuracy. Clean topic boundary at 04:12 (3.2s silence gap).
  Keyword match: "diagnostic", "accuracy", "FDA approval" (3/5
  target keywords).

Clip 2 (18:30 – 21:15):
  Reason: Strongest audience-relevant insight. Speaker presented
  original research data. Natural pause at 18:30.
  Keyword match: "patient outcomes", "clinical trial" (2/5 target
  keywords). Relevance score: 0.89 (highest of all candidates).

Clip 3 (35:02 – 37:48):
  Reason: Closing summary with actionable takeaway. High keyword
  density (4/5 target keywords). Clean ending at 37:48.

Rejected candidates:

Candidate A (11:20 – 11:55):
  Reason: Too short (35s). Below minimum threshold of 60s.
  Incomplete thought — speaker was interrupted.

Candidate B (28:00 – 30:10):
  Reason: Off-topic tangent about personal anecdote. Low keyword
  match (0/5). Relevance score: 0.31.

Confidence notes:
- Clip 2: High confidence (highest relevance score, clean boundaries)
- Clip 3: Moderate confidence (boundary at 37:48 was borderline —
  speaker trailed off rather than stopping cleanly)
- Clip 1: Moderate confidence (good content but 2:33 duration is
  on the long side for social media)
```

### After (Distilled Decision Summary)

```markdown
# Decision Summary — Podcast Marketing Skill

## Run Context
- **Input:** Episode 47 transcript — "AI in Healthcare" (42 minutes, 18 seconds)
- **Date:** April 13, 2026

## What the Skill Did
The skill analyzed a 42-minute podcast transcript and identified
5 candidate segments for social media clips. It selected the 3
strongest candidates and rejected 2, based on topic relevance,
keyword matching, segment length, and boundary quality.

## Key Decisions Made

### Decision 1: Clip Selection Criteria
- **What:** Used a combination of keyword matching (against 5 target
  keywords), relevance scoring, segment length, and audio boundary
  quality to rank candidates.
- **Why:** These criteria ensure clips are topically relevant,
  appropriately sized for social media, and start/end at natural
  speaking pauses.

### Decision 2: Minimum Length Threshold
- **What:** Rejected any segment shorter than 60 seconds.
- **Why:** Segments under 60 seconds tend to contain incomplete
  thoughts that lack context when shared standalone.
- **Alternatives Considered:** Candidate A (35 seconds) was
  considered but rejected for being too short and containing
  an interrupted thought.

### Decision 3: Off-Topic Filtering
- **What:** Rejected segments with zero keyword matches and low
  relevance scores.
- **Why:** Candidate B scored 0 out of 5 on keyword matching and
  had a relevance score of 0.31 — it was a personal anecdote
  unrelated to the episode's core topic.

## What Was Selected

| Clip | Timestamp | Reason Selected |
|------|-----------|-----------------|
| Clip 1 | 04:12 – 06:45 | Core argument about AI diagnostic accuracy; matched 3 of 5 target keywords; clean topic boundary |
| Clip 2 | 18:30 – 21:15 | Strongest audience insight with original research data; highest relevance score (0.89); natural pause |
| Clip 3 | 35:02 – 37:48 | Closing summary with actionable takeaway; highest keyword density (4 of 5) |

## What Was Rejected

| Candidate | Timestamp | Reason Rejected |
|-----------|-----------|-----------------|
| Candidate A | 11:20 – 11:55 | Too short (35 seconds, below 60-second minimum); speaker was interrupted mid-thought |
| Candidate B | 28:00 – 30:10 | Off-topic personal anecdote; zero keyword matches; low relevance score (0.31) |

## Confidence Assessment

| Clip | Confidence | Reasoning |
|------|------------|-----------|
| Clip 1 | 🟡 Moderate | Strong content, but 2:33 duration is long for social media formats |
| Clip 2 | 🟢 High | Highest relevance score, clean audio boundaries, strong content |
| Clip 3 | 🟡 Moderate | Strong keyword match, but the ending was a trail-off rather than a clean stop — may need manual trim |

## Hallucination Check

| Question | Answer |
|----------|--------|
| Does every output trace back to specific input data? | ✅ Yes — all timestamps and keywords reference the source transcript |
| Are there any claims not supported by the input? | ✅ None found |
| Did the skill generate content not present in the source? | ✅ No — all clips are direct segments from the transcript |

## Limitations & Caveats

- Clip 3's ending boundary may need manual review (speaker trailed off)
- Clip 1 may be too long for some social media platforms (2:33 vs typical 60–90 second preference)
- Keyword matching is exact-match only — synonyms or related terms are not captured

## One-Sentence Summary

"Our Podcast Marketing skill analyzed a 42-minute transcript and
selected 3 clips based on keyword relevance, audience value, and
audio boundary quality — rejecting 2 candidates that were too short
or off-topic."
```

---

## Demo Day Usage

### When to Show the Decision Summary

| Moment | What to Do |
|--------|------------|
| **During your live demo** | After showing the skill's output, switch to the Decision Summary: "Here's how the skill explained its decisions." |
| **During Q&A: "Why did it choose this?"** | Pull up the relevant "Key Decisions Made" section |
| **During Q&A: "How do you know it didn't hallucinate?"** | Pull up the "Hallucination Check" section |
| **During Q&A: "What are the limitations?"** | Pull up the "Limitations & Caveats" section |

### What NOT to Do

| Don't | Why |
|-------|-----|
| Don't read the entire summary aloud | It's a reference document, not a script |
| Don't show it before the live demo | Show the skill working first, then explain the reasoning |
| Don't hide the ⚠️ flags or 🟡 Moderate confidence ratings | Honesty about limitations builds credibility |

---

## Gate 5 Checklist Addition

| Checkpoint | Owner | ✅ |
|------------|-------|---|
| Skill produces a **Decision Summary** (via this prompt) | Skill Owner | ☐ |
| Decision Summary is saved as `decision-summary.md` in skill folder | Skill Owner | ☐ |
| PM has reviewed the Decision Summary for clarity | PM | ☐ |
| One-Sentence Summary practiced aloud | Presenter | ☐ |

---

## Quick Reference: The Complete 3-Prompt Pipeline

| Step | Prompt | Input | Output |
|------|--------|-------|--------|
| **1. Audit** | Socratic Reasoning Auditor | Raw skill output (no reasoning) | Critical Reasoning Gaps (3–6 gaps) |
| **2. Implement** | Coding Agent Instruction Template | Gap list + file tree + constitution | Coding agent instruction blocks |
| **3. Distill** | Decision Summary Distiller (this prompt) | Reasoning-enriched skill output | Demo-ready Decision Summary |

### The Flow

```
Skill produces output (results only)
        │
        ▼
   ┌─────────┐
   │ Prompt 1 │  Socratic Reasoning Auditor
   │  AUDIT   │  "What reasoning is missing?"
   └────┬─────┘
        │ Critical Reasoning Gaps
        ▼
   ┌─────────┐
   │ Prompt 2 │  Coding Agent Instruction Template
   │IMPLEMENT │  "Tell your agent to add the reasoning"
   └────┬─────┘
        │ Updated skill with reasoning
        ▼
   Skill produces output (results + reasoning)
        │
        ▼
   ┌─────────┐
   │ Prompt 3 │  Decision Summary Distiller
   │ DISTILL  │  "Polish it for demo day"
   └────┬─────┘
        │
        ▼
   decision-summary.md (demo-ready artifact)
```

---

*Part 3 of 3 — Week 5 Observability Utility Prompts*
*Previous: Socratic Reasoning Auditor (Part 1) → Coding Agent Instruction Template (Part 2)*
*Pipeline complete.*
