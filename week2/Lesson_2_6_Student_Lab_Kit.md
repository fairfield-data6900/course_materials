# Lesson 2.6: Student Lab Kit — Spec Refinement Workshop

**Course:** AI-Assisted SDD for Business Analysts  
**Session:** Week 2 — Specification Phase  
**Duration:** 50 minutes  
**Type:** Hands-on (Team Collaborative)  
**Goal:** Refine your Week 1 `spec.md` using the Socratic Refinement workflow and verify alignment with your `constitution.md`.

---

## The Workflow at a Glance

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   ROUND 1              AGENT MODE           COMPARISON          ROUND 2    │
│   ────────             ──────────           ──────────          ────────   │
│                                                                             │
│   /speckit.clarify  →  AI updates spec  →  External AI    →  Interview  →  COMMIT
│   (AI asks, you        (save v1 first!)    flags risks        + verify      (human
│    answer)                                                    Constitution   reviews)
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Team Roles

| Role | Person | Responsibility |
|------|--------|----------------|
| **Driver** | PM | Controls VS Code; runs commands; makes final edits |
| **External AI Operator** | Skill Owner A | Pastes prompts into ChatGPT/Claude; reads results aloud |
| **Decision Logger** | Skill Owner B | Records key decisions in a shared doc or comments |

*Rotate roles between phases if desired.*

---

## Phase-by-Phase Instructions

### Phase 1: Setup (0:00 – 0:03)

| Step | Action | Checkpoint |
|------|--------|------------|
| 1 | Open your project in VS Code | ☐ |
| 2 | Open `spec.md` (from Week 1) in the editor | ☐ |
| 3 | Open `constitution.md` in a split pane | ☐ |
| 4 | **Save a copy of your current spec as `spec-v1.md`** | ☐ |

**Version Control Options:**
```bash
# Option A: Copy the file
cp .specify/specs/[project]/spec.md .specify/specs/[project]/spec-v1.md

# Option B: Git stash (if you prefer)
git stash push -m "spec-v1-backup"

# Option C: Just copy content to a separate file manually
```

⚠️ **Do NOT skip this step.** You need v1 for the Comparison phase.

---

### Phase 2: Round 1 — Socratic Interview (0:03 – 0:15)

| Step | Action | Checkpoint |
|------|--------|------------|
| 1 | In Copilot Chat, type: `/speckit.clarify` | ☐ |
| 2 | AI asks clarifying questions — **discuss as a team** | ☐ |
| 3 | PM answers each question aloud; team contributes | ☐ |
| 4 | Reference your `constitution.md` when relevant | ☐ |
| 5 | Continue until AI has asked 4–6 questions | ☐ |

**Key Principle:** The AI asks, you decide. Don't let the AI make assumptions for you.

**Sample Questions You Might See:**
- "What file formats are accepted for the input?"
- "What is the maximum length for [output]?"
- "What happens if [edge case] occurs?"
- "Does this comply with your Constitution's rule about [X]?"

---

### Phase 3: Agent Mode — AI Updates Spec (0:15 – 0:20)

| Step | Action | Checkpoint |
|------|--------|------------|
| 1 | Instruct the AI to update the spec based on your answers | ☐ |
| 2 | Watch the AI edit `spec.md` directly | ☐ |
| 3 | **Do NOT commit yet** — this is `spec-v2` (draft) | ☐ |

**How to Trigger Agent Mode:**
```
# In Copilot Chat:
"Based on my answers, update the spec.md file directly."

# Or use Copilot Agent Mode if available in your setup
```

⚠️ **Speed is great, but speed without verification is how hallucinations sneak in.**

---

### Phase 4: External Triage — Spec Comparison (0:20 – 0:30)

| Step | Action | Checkpoint |
|------|--------|------------|
| 1 | **Skill Owner A:** Open external AI (ChatGPT, Claude, etc.) | ☐ |
| 2 | Paste the **Spec Comparison Prompt** (see Appendix A below) | ☐ |
| 3 | Paste the content of `spec-v1.md` and `spec-v2.md` (current spec) | ☐ |
| 4 | Paste your `constitution.md` content | ☐ |
| 5 | Review the **Comparison Report** as a team | ☐ |
| 6 | **Decision Logger:** Note any flags that need discussion | ☐ |

**What to Look For in the Report:**
- 🔴 **Magic Buttons** — Features that assume AI "just knows" how to do something
- 🟡 **Vague Verbs** — Words like "optimize," "handle," "process" without criteria
- 🟠 **Scope Creep** — Features added that you didn't explicitly request
- ⚠️ **Constitution Violations** — Rules in your Constitution that aren't reflected in the spec

---

### Phase 5: Round 2 — Refinement Interview (0:30 – 0:45)

| Step | Action | Checkpoint |
|------|--------|------------|
| 1 | **Skill Owner A:** Paste the **Round 2 Interview Prompt** (see Appendix B) | ☐ |
| 2 | Paste your current `spec.md` (v2) and `constitution.md` | ☐ |
| 3 | Optionally paste the Comparison Report from Phase 4 | ☐ |
| 4 | AI asks targeted questions — **discuss as a team** | ☐ |
| 5 | **PM:** Make final edits to `spec.md` based on your answers | ☐ |

**Key Principle:** Round 2 is about alignment — does your spec match your Constitution?

---

### Phase 6: Commit (0:45 – 0:50)

| Step | Action | Checkpoint |
|------|--------|------------|
| 1 | **PM:** Read through the final `spec.md` one more time | ☐ |
| 2 | Run the **Gate 2 Self-Assessment** (see below) | ☐ |
| 3 | Commit both `spec.md` and `constitution.md` | ☐ |
| 4 | Write a meaningful commit message | ☐ |

**Commit Command:**
```bash
git add .specify/specs/[project]/spec.md
git add .specify/memory/constitution.md
git commit -m "Gate 2: Refined spec + constitution after Socratic refinement"
```

---

## Gate 2 Self-Assessment Checklist

Before committing, verify your work meets Gate 2 criteria.

### spec.md

| Checkpoint | ✅ |
|------------|---|
| All placeholder text removed or replaced | ☐ |
| Inputs defined with formats (e.g., `.srt`, `.txt`, `JSON`) | ☐ |
| Outputs defined with constraints (e.g., "≤60 seconds", "max 280 characters") | ☐ |
| No "Magic Buttons" — vague features that assume AI "just knows" | ☐ |
| Error handling / edge cases addressed | ☐ |
| No vague verbs without measurable criteria | ☐ |

### constitution.md

| Checkpoint | ✅ |
|------------|---|
| Core Principles filled in (3–5 principles) | ☐ |
| Tech Stack & Platform Rules defined | ☐ |
| Security & Data Boundaries defined ("Never-Ever" list) | ☐ |
| Out of Scope section completed | ☐ |
| Governance section completed (roles, change process) | ☐ |

### Alignment

| Checkpoint | ✅ |
|------------|---|
| Spec complies with all Constitution rules | ☐ |
| No contradictions between spec and constitution | ☐ |
| Comparison Report flags have been addressed or documented | ☐ |

### Version Control

| Checkpoint | ✅ |
|------------|---|
| Both files committed to `.specify/` folder | ☐ |
| Commit message describes what changed | ☐ |
| `spec-v1.md` preserved for reference (optional but recommended) | ☐ |

---

## Troubleshooting FAQ

| Issue | Quick Fix |
|-------|-----------|
| `/speckit.clarify` returns no questions | Your spec may already be tight — or too vague for the AI to parse. Check formatting and try again. |
| Agent Mode makes unwanted changes | Revert to `spec-v1.md` and re-run with more specific instructions. |
| Comparison Prompt misses obvious issues | Add more specific flags to the prompt (e.g., "check for undefined error handling"). |
| Round 2 Interview goes off-topic | Re-anchor: "Focus only on Constitution alignment and ambiguous terms." |
| Team disagrees on a decision | PM has tie-breaking authority (per your Governance rules). Log the disagreement and move on. |
| Running out of time | Prioritize: (1) Address any 🔴 High-severity flags, (2) Commit what you have, (3) Note remaining items for follow-up. |

---

## Appendix A: Spec Comparison Prompt

**Copy this entire prompt into an external AI (ChatGPT, Claude, etc.):**

```
You are a Specification Auditor. Your job is to compare two versions of a software specification and produce a structured Comparison Report.

## Your Constraints
- Be precise and factual
- Flag potential issues, but do NOT rewrite the spec
- Focus on what changed, what's risky, and what might be a hallucination

## Inputs

### SPEC-V1 (Original — from Week 1)
```
[PASTE SPEC-V1.MD CONTENT HERE]
```

### SPEC-V2 (AI-Updated — after Round 1)
```
[PASTE SPEC-V2.MD CONTENT HERE]
```

### CONSTITUTION (Project Rules)
```
[PASTE CONSTITUTION.MD CONTENT HERE — OR SUMMARIZE KEY RULES]
```

## Your Task

Produce a **Comparison Report** with the following sections:

### 1. Summary of Changes
List all additions, deletions, and modifications between v1 and v2. Use a table format:

| Section | Change Type | Description |
|---------|-------------|-------------|
| Inputs | Addition | Added `.srt` format support |
| Outputs | Modification | Changed clip length from "short" to "≤60 seconds" |
| ... | ... | ... |

### 2. Constitution Alignment Check
For each rule in the Constitution, confirm whether v2 complies:

| Constitution Rule | v2 Status | Notes |
|-------------------|-----------|-------|
| Clips ≤ 60 seconds | ✅ Compliant | Explicitly stated in Outputs |
| No PII in logs | ⚠️ Not addressed | Spec does not mention logging |
| ... | ... | ... |

### 3. Risk Flags
Identify any of the following issues in v2:

- **Magic Buttons:** Features that assume the system "just knows" (e.g., "automatically detect X")
- **Vague Verbs:** Words like "optimize," "process," "handle" without measurable criteria
- **Happy Path Traps:** Missing error handling or edge cases
- **Scope Creep:** Features not present in v1 that were added without explicit human request
- **Hallucinations:** Invented details (APIs, libraries, formats) that weren't in v1 or the conversation

Format as:

| Risk Type | Location | Description | Severity |
|-----------|----------|-------------|----------|
| Magic Button | Outputs | "Automatically detect speaker names" | 🔴 High |
| Vague Verb | Constraints | "Ensure quality output" | 🟡 Medium |
| ... | ... | ... | ... |

### 4. Questions for Human Review
List 3–5 questions the human should answer before finalizing v2:

1. "Did you intend to add [X feature], or did the AI assume it?"
2. "How should the system handle [edge case Y]?"
3. ...

## Output Format
Return the full Comparison Report in markdown format, ready to review.
```

---

## Appendix B: Round 2 Interview Prompt

**Copy this entire prompt into an external AI (ChatGPT, Claude, etc.):**

```
You are a Specification Refinement Coach using the Socratic method. Your job is to help a team finalize their software specification by asking targeted questions — NOT by writing the spec for them.

## Your Role
- Ask clarifying questions ONE AT A TIME
- Focus on ambiguities, gaps, and Constitution alignment
- Never rewrite the spec — only ask questions
- After each answer, acknowledge it and ask the next question
- Stop after 5–7 questions or when the team says "done"

## Your Constraints
- Do NOT generate draft text for the spec
- Do NOT make decisions for the team
- Reference the Constitution explicitly when relevant
- Flag any remaining "Magic Buttons" or vague terms

## Inputs

### SPEC-V2 (AI-Updated Specification)
```
[PASTE SPEC-V2.MD CONTENT HERE]
```

### CONSTITUTION (Project Rules)
```
[PASTE CONSTITUTION.MD CONTENT HERE]
```

### COMPARISON REPORT (Optional — from previous step)
```
[PASTE COMPARISON REPORT HERE IF AVAILABLE]
```

## Interview Flow

### Opening
Start with:
> "I've reviewed your updated spec and Constitution. I have a few questions to help you finalize this before Gate 2. Ready?"

### Question Categories (Use as Needed)

**Constitution Alignment:**
- "Your Constitution says [RULE]. Does your spec explicitly address this? If not, should it?"
- "I see a potential conflict between [SPEC ITEM] and [CONSTITUTION RULE]. How do you want to resolve this?"

**Ambiguity Detection:**
- "When you say '[VAGUE TERM]', what specifically do you mean? Can we make this measurable?"
- "What happens if [INPUT] is malformed or missing? Your spec doesn't say."

**Magic Button Detection:**
- "Your spec says '[FEATURE]'. How will the system actually do this? Is this one feature or multiple?"
- "This sounds like it assumes the AI 'just knows' how to [X]. Can we break this down?"

**Scope Verification:**
- "Is [FEATURE] in scope for this phase, or should it be in 'Out of Scope'?"
- "Your Constitution's Out of Scope section says [X]. Does your spec accidentally include this?"

**Edge Cases:**
- "What's the expected behavior when [EDGE CASE] occurs?"
- "Your spec covers the happy path. What about [FAILURE SCENARIO]?"

### Closing
After 5–7 questions (or when team says "done"), close with:
> "Based on your answers, here's what you should update in your spec:
> 1. [SUMMARY OF DECISION 1]
> 2. [SUMMARY OF DECISION 2]
> 3. ...
>
> Make these edits, then commit your spec. You're ready for Gate 2."

## Output Format
- Ask questions one at a time
- Wait for the team's response before continuing
- Summarize decisions at the end (but do NOT write the spec text)
```

---

## Quick Reference Card

| Phase | Time | Key Action | Tool |
|-------|------|------------|------|
| Setup | 3 min | Save `spec-v1.md` | VS Code / Terminal |
| Round 1 | 12 min | `/speckit.clarify` → Answer questions | Copilot Chat |
| Agent Mode | 5 min | AI updates spec | Copilot Agent |
| Comparison | 10 min | External AI flags risks | ChatGPT / Claude |
| Round 2 | 15 min | Interview → Final edits | ChatGPT / Claude + VS Code |
| Commit | 5 min | Self-assess → Commit | Git |

---

## Remember

> **"The AI asks, you decide. The AI updates, you verify. The AI flags, you fix. You commit."**

Good luck — you've got this! 🚀

---

*End of Lesson 2.6 Student Lab Kit*
