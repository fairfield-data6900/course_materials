# Lesson 5.4 Demo Kit: `/scout` → `/trace` → Decision Summary

**Course:** AI-Assisted SDD for Business Analysts  
**Session:** Week 5 — Agentic Skills & Observability  
**Duration:** 41 minutes  
**Type:** Live Demo (all actions on screen — no slides)  
**Goal:** Show students how to map a skill's structure (`/scout`), investigate its decision logic (`/trace`), and produce a human-readable Decision Summary for demo day.

---

## The Arc

This demo tells a single story in four phases:

| Phase | Tool | Metaphor | Question Answered |
|-------|------|----------|-------------------|
| **1** | `/scout` | 🗺️ The Cartographer | "What are the moving parts?" |
| **2** | `/trace` | 🔍 The Investigator | "Why did the agent make this decision?" |
| **3** | Instructor's Report | 📋 The Example | "What does good observability look like?" |
| **4** | 3-Prompt Pipeline | 🛠️ The Toolkit | "How do I build this for my own skill?" |

**The teaching line:**

> "First we map the terrain. Then we investigate the decisions. Then we make those decisions explainable to anyone in the room."

---

## Pre-Demo Setup

### Files Open in VS Code (3-Pane Layout)

| Pane | File | Purpose |
|------|------|---------|
| Left | `.skills/podcast-marketing/` folder tree | The skill we're investigating |
| Center | Terminal | For running `/scout` and `/trace` |
| Right | Empty — will fill with generated artifacts | `ARCHITECTURE.md`, trace output, Decision Summary |

### Pre-Demo Checklist

| Item | Status |
|------|--------|
| Podcast Marketing skill is functional (produces output) | ☐ |
| Sample transcript ready as input | ☐ |
| Skill has been run at least once (output exists) | ☐ |
| Terminal visible and ready | ☐ |
| 3-Prompt Pipeline files accessible (for Phase 4) | ☐ |
| Instructor's Podcast Skill report with reasoning ready to show | ☐ |

---

## Instructor Talking Points Card

| Concept | What to Say |
|---------|-------------|
| **Map Before Investigate** | "You can't investigate a building you haven't mapped. `/scout` gives you the floor plan. `/trace` lets you follow the footprints." |
| **Observability ≠ Logs** | "Observability for us is not terminal output. It's the ability to answer 'why did the agent do this?' with evidence a non-technical audience can understand." |
| **The Demo-Day Test** | "If someone asks 'how do you know it didn't hallucinate?' and you can't point to evidence — you have a black box." |
| **Two Audiences** | "`/scout` and `/trace` are for YOU — the builder. The Decision Summary is for your AUDIENCE — the demo room." |
| **You Can't Distill What Doesn't Exist** | "If your skill only outputs results with no reasoning, the Distiller has nothing to work with. That's why Prompt 1 comes first." |

---

## Demo Flow (41 Minutes)

---

### Opening: The Nervous System (0:00 – 0:01)

**Action:** Stand at the screen. One sentence.

**Narration:**

> "Week 5 is about the nervous system — can your project feel what's happening inside itself? Today I'll show you two tools that let you see inside a skill, and then I'll show you how to make that visibility presentable for demo day."

**Transition:** Open the `.skills/podcast-marketing/` folder in VS Code.

---

### Phase 1: `/scout` — The Cartographer (0:01 – 0:12)

**Purpose:** Map the skill's structure before investigating its decisions.

---

#### 1A: Run `/scout` (0:01 – 0:03)

**Action:** Type and run `/scout` targeting the podcast-marketing skill.

**Narration:**

> "Before I can investigate decisions, I need to know what I'm looking at. `/scout` maps the terrain."

**On Screen:** Command executing, output generating.

---

#### 1B: Walk Through the File Index (0:03 – 0:06)

**Action:** Scroll through the generated `ARCHITECTURE.md` — file index section.

**Narration:**

> "Here's what `/scout` found. Every file in the skill, what it does, and how they connect."

**Walk through each file:**

| File | What to Say |
|------|-------------|
| `SKILL.md` | "The skill's identity card — what it does, what it expects." |
| `prompts/extract-clips.md` | "The instruction that tells the AI how to find clip-worthy segments." |
| `prompts/write-linkedin.md` | "The instruction for generating LinkedIn posts from clips." |
| `code/parse_transcript.py` | "The code that actually processes the transcript — this is where decisions happen." |
| `recipes/brand-voice.md` | "The style guide — how the output should sound." |

**Teaching Moment:**

> "Notice: I haven't read any code yet. I just know the map. That's the value of `/scout` — you understand the structure before you dive into the details."

---

#### 1C: Walk Through the Mermaid Diagram (0:06 – 0:09)

**Action:** Scroll to the Mermaid architecture diagram in `ARCHITECTURE.md`. Render it if possible.

**Narration:**

> "And here's the visual. The Mermaid diagram shows how data flows through the skill."

**Trace the flow on screen:**

```
Transcript Input
    → parse_transcript.py (segmentation + scoring)
        → extract-clips.md (clip selection)
            → write-linkedin.md (post generation)
                → brand-voice.md (style filter)
                    → Final Output
```

**Teaching Moment:**

> "This diagram tells me where the decision points are. The parser segments and scores. The prompt selects clips. The recipe filters the voice. Now I know WHERE to look. Next question: WHY did it make those choices?"

---

#### 1D: Identify the Decision Surface (0:09 – 0:12)

**Action:** Point to specific files in the architecture diagram.

**Narration:**

> "Every skill has a 'decision surface' — the places where the agent makes choices that affect the output. For this skill, the decision surface is:"

**On Screen — highlight these:**

| Decision Point | File | What It Decides |
|----------------|------|-----------------|
| Segment boundaries | `parse_transcript.py` | Where to cut the transcript |
| Clip selection | `extract-clips.md` | Which segments become clips |
| Rejection criteria | `parse_transcript.py` | Which segments are filtered out |
| Voice styling | `brand-voice.md` | How the output sounds |

**Narration:**

> "These are the places I need to investigate. If something goes wrong — or if someone asks 'why did it do that?' — the answer lives at one of these decision points."

**Transition:**

> "Now I know the map. Time to follow the footprints."

---

### Phase 2: `/trace` — The Investigator (0:12 – 0:23)

**Purpose:** Reveal WHY the skill made specific decisions.

---

#### 2A: Set Up the Trace (0:12 – 0:14)

**Action:** Prepare the `/trace` command with three inputs:
1. The `ARCHITECTURE.md` (just generated by `/scout`)
2. The skill's actual output (from a previous run)
3. The `spec.md` (to trace decisions back to requirements)

**Narration:**

> "I'm giving `/trace` three things: the architecture map we just made, the actual output my skill produced, and the spec — so it can trace decisions all the way from requirements to results."

**On Screen:** The command with context files visible.

---

#### 2B: Run `/trace` (0:14 – 0:16)

**Action:** Execute `/trace`. Watch output generate.

**Narration:**

> "Now `/trace` is doing something `/scout` didn't — it's not just mapping structure. It's asking: given this architecture and this output, what decisions were made and why?"

---

#### 2C: Decision Path Visualization (0:16 – 0:19)

**Action:** Scroll to the Decision Path — a Mermaid flowchart showing how requirements led to implementation choices led to output.

**Narration:**

> "Here's the decision path. Watch how it traces from the spec requirement — 'extract clip-worthy segments' — through the implementation choice — 'keyword matching + silence detection' — to the actual output — '3 clips selected, 2 rejected.'"

**On Screen:** The Mermaid decision flow:

```
spec.md: "Extract clip-worthy segments"
    → Implementation: keyword matching + silence detection
        → Candidate pool: 5 segments identified
            → Selected: 3 (met threshold)
            → Rejected: 2 (too short / off-topic)
                → Output: 3 clips with timestamps
```

**Teaching Moment:**

> "This is the chain of reasoning. Every output traces back to a spec requirement through a specific implementation choice. If the output is wrong, I can follow this chain backwards to find where it went off track."

---

#### 2D: Assumption Challenges (0:19 – 0:21)

**Action:** Scroll to the Assumption Challenges table.

**Narration:**

> "Now here's where `/trace` gets interesting. It doesn't just show what happened — it challenges the silent choices."

**On Screen:** The Assumption Challenges table:

| Silent Choice | What Was Assumed | Challenge |
|---------------|-----------------|-----------|
| Regex for speaker detection | Transcript has consistent speaker labels | What if labels are inconsistent or missing? |
| 60-second max clip length | Social media preference | What if the best content spans 90 seconds? |
| Keyword exact-match only | Target keywords cover the topic | What about synonyms or related terms? |

**Narration:**

> "These are the things the skill assumed but never stated. Regex for speaker detection — what if the transcript doesn't have clean speaker labels? 60-second max — what if the best insight is 90 seconds? These are landmines."

**Teaching Moment:**

> "Every assumption is a potential failure point. `/trace` makes them visible so you can decide: is this assumption safe, or do I need to handle the edge case?"

---

#### 2E: Landmine List (0:21 – 0:23)

**Action:** Scroll to the Landmine List — prioritized risks.

**On Screen:**

| Priority | Landmine | Trigger | Impact |
|----------|----------|---------|--------|
| 🔴 Red | Transcript lacks diarization | No speaker labels in input | Segmentation fails silently — outputs garbage clips |
| 🟡 Yellow | Context overflow | Transcript > 50,000 tokens | AI truncates without warning — clips from first half only |
| 🟡 Yellow | Keyword synonyms missed | Topic uses varied terminology | Relevant segments scored as low-relevance |
| 🔵 Blue | Brand voice drift | Recipe is vague on edge cases | LinkedIn posts sound inconsistent across clips |

**Narration:**

> "Red means it breaks. Yellow means it degrades silently. Blue means it's cosmetic but noticeable."

> "The red one is critical: if the transcript doesn't have speaker labels, my segmentation logic fails silently. It doesn't crash — it just produces bad clips. That's worse than crashing, because I might not notice."

**Teaching Moment:**

> "Silent failures are the most dangerous kind. `/trace` surfaces them so you can decide what to do about them before demo day — not during."

**Transition:**

> "So now I have the map and the investigation. But here's the problem: everything you just saw — the decision path, the assumptions, the landmines — that's for ME, the builder. My demo audience won't read any of this. They need something different."

---

### Phase 3: The Instructor's Report — What Good Looks Like (0:23 – 0:30)

**Purpose:** Show students a concrete example of observability that a non-technical audience can understand.

---

#### 3A: Open the Podcast Skill Report (0:23 – 0:26)

**Action:** Open the Podcast Skill's actual output report — the one that already includes reasoning alongside results.

**Narration:**

> "Here's what my Podcast Skill actually produces. Look — it doesn't just output clips. It tells me WHY each clip was selected and WHY others were rejected."

**On Screen:** The instructor's report with reasoning visible. Walk through three specific elements:

**Element 1 — A Selected Item with Reason:**

> "Clip 1 (04:12 – 06:45): Selected because the speaker introduced the core argument about AI diagnostic accuracy. Clean topic boundary at 04:12. Matched 3 of 5 target keywords."

**Narration:**

> "See that? It's not just 'Clip 1.' It's 'Clip 1 BECAUSE...' — the reasoning is built into the output."

**Element 2 — A Rejected Item with Reason:**

> "Candidate A (11:20 – 11:55): Rejected. Too short (35 seconds, below 60-second minimum). Speaker was interrupted mid-thought."

**Narration:**

> "And here's a rejected candidate. It tells me what was considered AND why it didn't make the cut. This is how you answer 'why didn't the agent include this?'"

**Element 3 — A Confidence Flag:**

> "Clip 3: Moderate confidence. Boundary at 37:48 was borderline — speaker trailed off rather than stopping cleanly. May need manual trim."

**Narration:**

> "And this — a confidence flag. The skill is telling me 'I'm not 100% sure about this one.' That's honesty. That's what builds trust with your audience."

---

#### 3B: The Demo-Day Test (0:26 – 0:28)

**Action:** Pause. Look at the class.

**Narration:**

> "Here's the test. When someone at your demo asks 'why did the agent do this?' — you should be able to pull up a report like this and point to the answer."

> "When someone asks 'how do you know it didn't hallucinate?' — you point to the evidence: 'Every clip timestamp traces back to the source transcript. Every selection reason references specific input data.'"

> "If your skill only produces results but can't explain its decisions, you have a black box. And a black box can't survive a Q&A."

---

#### 3C: The Gap (0:28 – 0:30)

**Action:** Pause again.

**Narration:**

> "Now — your skills probably don't do this yet. Most of your skills produce results only. No reasoning. No rejection explanations. No confidence flags."

> "That's okay. I'm about to give you a tool to get there."

**Transition:**

> "The question is: how do you go from 'results only' to 'results plus reasoning'? That's what the 3-Prompt Pipeline does."

---

### Phase 4: The 3-Prompt Pipeline — Your Toolkit (0:30 – 0:41)

**Purpose:** Introduce the three utility prompts that take students from black-box output to demo-ready Decision Summary.

---

#### 4A: The Pipeline Overview (0:30 – 0:33)

**Action:** Open the pipeline diagram (markdown file or draw live).

**On Screen:**

```
Skill Output (results only)
        │
        ▼
  ┌───────────┐
  │  Prompt 1  │  Socratic Reasoning Auditor
  │   AUDIT    │  "What reasoning is missing?"
  └─────┬──────┘
        │ Critical Reasoning Gaps
        ▼
  ┌───────────┐
  │  Prompt 2  │  Coding Agent Instruction Template
  │ IMPLEMENT  │  "Tell your agent to add the reasoning"
  └─────┬──────┘
        │ Updated skill with reasoning
        ▼
  Skill Output (results + reasoning)
        │
        ▼
  ┌───────────┐
  │  Prompt 3  │  Decision Summary Distiller
  │  DISTILL   │  "Polish it for demo day"
  └─────┬──────┘
        │
        ▼
  decision-summary.md (demo-ready artifact)
```

**Narration:**

> "Three prompts. Three steps. Each one builds on the previous."

---

#### 4B: Prompt 1 — The Socratic Reasoning Auditor (0:33 – 0:35)

**Action:** Open Prompt 1 file briefly. Don't read the whole thing — just show the concept.

**Narration:**

> "Step 1: You paste your skill's output into this prompt. It asks Socratic questions that reveal where reasoning is missing."

> "It doesn't fix anything. It doesn't write code. It asks: 'Your skill selected 3 clips but didn't say why. What criteria drove the selection?' 'Your output says high relevance but doesn't define what relevance means. What specific input features made it relevant?'"

> "The output is a list of Critical Reasoning Gaps — specific places where your skill can't explain itself."

**Teaching Moment:**

> "This is the most important step. You can't fix what you can't see. Prompt 1 shows you what's missing."

---

#### 4C: Prompt 2 — The Coding Agent Instruction Template (0:35 – 0:37)

**Action:** Open Prompt 2 file briefly.

**Narration:**

> "Step 2: You take those gaps and paste them into this prompt along with your skill's file tree and your Constitution. It generates copy-paste-ready instruction blocks for your coding agent."

> "You don't write code. You give the instruction block to Copilot or ChatGPT and say 'update my skill to include this reasoning.' The prompt does the translation for you."

**Show one example instruction block briefly:**

> "See — it tells the agent: 'Update the skill so that when rows are dropped, the output includes a Rows Dropped section that lists how many, the rule that triggered each drop, and a breakdown by reason.' That's specific enough for the agent to execute."

**Teaching Moment:**

> "The gap list from Prompt 1 becomes the instruction set for Prompt 2. Each gap turns into a concrete update to your skill."

---

#### 4D: Prompt 3 — The Decision Summary Distiller (0:37 – 0:39)

**Action:** Open Prompt 3 file briefly.

**Narration:**

> "Step 3: After your skill now produces reasoning alongside results, you paste the enriched output into this prompt. It distills everything into a polished Decision Summary."

> "The Decision Summary has a specific structure: What the skill did. Key decisions made. What was selected and why. What was rejected and why. Confidence levels. A hallucination check. And a one-sentence summary you can say out loud at your demo."

**Show the example Decision Summary briefly — the Podcast Skill one from the Distiller file.**

**Teaching Moment:**

> "This is the artifact you show at demo day. Not logs. Not trace output. A human-readable document that answers 'why' and 'how do you know.'"

---

#### 4E: The Key Principle (0:39 – 0:40)

**Action:** Pause. Emphasize.

**Narration:**

> "You can't distill what doesn't exist. That's why the order matters."

> "Prompt 1 reveals the gaps. Prompt 2 fills the gaps. Prompt 3 polishes the result. Skip Prompt 1 and you're polishing nothing."

---

#### 4F: Transition to Lab (0:40 – 0:41)

**Action:** Set expectations for the lab session.

**Narration:**

> "In the lab, you'll run this pipeline on your own skills. Start with Prompt 1 — paste your skill's output and see what gaps it finds. Then use Prompt 2 to instruct your coding agent. Then use Prompt 3 to produce your Decision Summary."

> "By the end of today, each skill should have a `decision-summary.md` committed to your repo. That's your Gate 5 deliverable."

> "PM: your job is to review both Decision Summaries for clarity. If a non-technical person can't understand them, send them back."

---

## Artifacts Produced During Demo

| Artifact | Phase | How It's Shown |
|----------|-------|----------------|
| `ARCHITECTURE.md` (file index + Mermaid) | Phase 1 (`/scout`) | Generated live |
| Decision Path Visualization (Mermaid) | Phase 2 (`/trace`) | Generated live |
| Assumption Challenges Table | Phase 2 (`/trace`) | Generated live |
| Landmine List (Red/Yellow/Blue) | Phase 2 (`/trace`) | Generated live |
| Instructor's Podcast Skill Report | Phase 3 | Opened and walked through |
| 3-Prompt Pipeline Diagram | Phase 4 | Shown on screen |

---

## Updated Gate 5 Criteria

| Checkpoint | Owner | ✅ |
|------------|-------|---|
| Both skills pass functional test (happy path works) | Skill Owner | ☐ |
| Each skill produces a `decision-summary.md` | Skill Owner | ☐ |
| Decision Summary is readable by a non-technical audience | PM verifies | ☐ |
| PM integration in progress | PM | ☐ |
| One-Sentence Summary practiced aloud | Presenter | ☐ |

---

## Instructor Cheat Sheet: Troubleshooting

| Issue | Quick Fix |
|-------|-----------|
| `/scout` output is sparse | Skill folder may be incomplete. Check: does it have `SKILL.md`, `prompts/`, `code/`, `recipes/`? |
| `/trace` doesn't find decision points | The skill may be too simple (single file, no branching logic). Ask: "Where does your skill make a choice?" |
| Students are overwhelmed by `/trace` output | Remind: "This output is for YOU. Your audience gets the Decision Summary. You don't need to understand every line — focus on the Assumption Challenges and Landmines." |
| Students want to skip Prompt 1 | Stop them: "You can't distill what doesn't exist. Run the Auditor first." |
| Prompt 1 finds zero gaps | Either the skill already has great reasoning (rare) or the output is too minimal for the Auditor to analyze. Ask: "Does your skill produce more than one line of output?" |
| Prompt 2 instruction blocks confuse the coding agent | Check: is the file path correct? Is the Constitution included? Re-run with more specific context. |
| Decision Summary has ⚠️ flags | That means gaps still exist. Go back to Prompt 1 → 2 for those specific gaps. |
| Student says "my skill doesn't make decisions" | Every skill makes decisions. Ask: "Does your skill filter, select, rank, transform, or format anything? That's a decision." |

---

## Key Phrases to Repeat

| Phrase | When to Use |
|--------|-------------|
| "Map the terrain, then follow the footprints." | Opening and Phase 1→2 transition |
| "Observability is not logs. It's the ability to answer 'why did the agent do this?'" | Phase 2 and Phase 3 |
| "If your skill can't explain its decisions, you have a black box." | Phase 3 |
| "You can't distill what doesn't exist." | Phase 4 — the key principle |
| "The Decision Summary is for your audience. The trace is for you." | When students confuse the two |
| "Silent failures are worse than crashes." | Phase 2E — Landmines |

---

## Timing Summary

| Phase | Time | Duration | Content |
|-------|------|----------|---------|
| Opening | 0:00–0:01 | 1 min | Nervous System framing |
| Phase 1: `/scout` | 0:01–0:12 | 11 min | Map the skill structure |
| Phase 2: `/trace` | 0:12–0:23 | 11 min | Investigate decisions, assumptions, landmines |
| Phase 3: Report | 0:23–0:30 | 7 min | Show instructor's Podcast Skill report |
| Phase 4: Pipeline | 0:30–0:41 | 11 min | Introduce 3-Prompt observability toolkit |
| **Total** | | **41 min** | |

---

*End of Lesson 5.4 Demo Kit*
*Tools: `/scout` → `/trace` → 3-Prompt Pipeline*
*No `/review` — that's Week 6.*
