# Lesson 2.5: Instructor Demo — `/speckit.clarify` for Socratic Refinement

**Course:** AI-Assisted SDD for Business Analysts  
**Session:** Week 2 — Specification Phase  
**Duration:** 25 minutes  
**Type:** Instructor Demo (I Do)  
**Goal:** Model the complete spec refinement workflow: Socratic Q&A → AI updates spec (Agent Mode) → External AI comparison → Round 2 interview for final refinement.

---

## The Refined Specification Workflow

| Phase | Tool/Mode | What Happens | Output |
|-------|-----------|--------------|--------|
| **Round 1: Socratic Interview** | `/speckit.clarify` | AI asks clarifying questions → Human answers | Answers captured in conversation |
| **Agent Mode Update** | Copilot Agent Mode | AI updates `spec.md` directly based on Round 1 answers | `spec-v2.md` (keep `spec-v1.md`) |
| **External Triage** | External AI + Comparison Prompt | Compare v1 vs v2 → Flag changes, risks, hallucinations | Comparison Report |
| **Round 2: Refinement Interview** | External AI + Interview Prompt | AI interviews human → Refine details + verify Constitution alignment | Human makes final edits → commit |

---

## Pre-Demo Setup

| Item | Status |
|------|--------|
| Podcast Marketing Tool `spec.md` from Week 1 | Open in VS Code (this is `spec-v1.md`) |
| `constitution.md` (drafted in 2.3) | Open in split pane |
| Terminal ready for `/speckit.clarify` | Visible |
| External AI (ChatGPT or Claude) | Open in browser tab |
| Comparison Prompt + Round 2 Interview Prompt | Ready to paste |
| Students have their own `spec.md` + `constitution.md` ready | Confirmed in 2.4 Stand-up |

---

## Demo Flow (25 min)

### Phase 1: Hook & Context (0:00 – 0:03)

| Time | Instructor Action | Narration |
|------|-------------------|-----------|
| 0:00–0:02 | Show Week 1 `spec.md` on screen | "This is where we left off in Week 1. It passed Gate 1, but is it *tight* enough to build from? Let's find out." |
| 0:02–0:03 | Point to `constitution.md` in split pane | "We now have our Constitution — the rules. The question is: does our spec *comply* with those rules? And is it precise enough that our Overconfident Intern won't make assumptions?" |

---

### Phase 2: Round 1 — Socratic Interview (0:03 – 0:10)

| Time | Instructor Action | Narration |
|------|-------------------|-----------|
| 0:03–0:04 | Type `/speckit.clarify` in Copilot Chat | "Watch what happens. The AI doesn't *rewrite* the spec yet. It *interrogates* it first." |
| 0:04–0:08 | AI asks 3–4 clarifying questions; Instructor answers aloud | "See? It's asking *me* to decide. 'What format should the transcript be?' I say `.srt` or `.txt` — that's a *human* decision, not an AI guess." |
| 0:08–0:10 | Continue answering questions; reference Constitution where relevant | "Our Constitution says 'clips ≤ 60 seconds.' So when it asks about clip length, I already have my answer." |

**Key Teaching Moment:**  
> "The AI asks, you decide. Keep your Constitution open — it often has the answers already."

---

### Phase 3: Agent Mode — AI Updates Spec (0:10 – 0:14)

| Time | Instructor Action | Narration |
|------|-------------------|-----------|
| 0:10–0:11 | Save current `spec.md` as `spec-v1.md` (or note the git state) | "Before we let the AI edit, I'm saving this as v1. We need both versions for comparison." |
| 0:11–0:12 | Enable Copilot Agent Mode (or instruct AI to update the spec) | "Now I'm going to let the AI update the spec directly based on our conversation. This is Agent Mode — the intern is now *writing*, not just asking." |
| 0:12–0:14 | AI updates `spec.md`; show the changes appearing | "Watch it work. It's incorporating all my answers into the spec. Fast, right? But here's the question: did it get everything *right*?" |

**Key Teaching Moment:**  
> "Speed is great, but speed without verification is how hallucinations sneak in. That's why we compare."

---

### Phase 4: External Triage — Spec Comparison (0:14 – 0:19)

| Time | Instructor Action | Narration |
|------|-------------------|-----------|
| 0:14–0:15 | Open external AI (ChatGPT) in browser | "Now we bring in a second opinion. A different AI, fresh context, no memory of our conversation." |
| 0:15–0:16 | Paste the **Spec Comparison Prompt** (see Appendix A) | "This prompt tells the AI exactly what to look for: additions, deletions, changes, and — most importantly — potential hallucinations or 'Magic Buttons'." |
| 0:16–0:17 | Paste `spec-v1.md` and `spec-v2.md` content | "I'm giving it both versions. Old and new." |
| 0:17–0:19 | Review the Comparison Report; highlight any flags | "Look — it flagged this line: 'automatically detect speaker names.' That's a Magic Button. The AI added a feature I never asked for. This is why we compare." |

**Key Teaching Moment:**  
> "Two AIs agreeing doesn't mean it's right. But two AIs *disagreeing* — or one flagging something suspicious — is a signal to slow down and think."

---

### Phase 5: Round 2 — Refinement Interview (0:19 – 0:23)

| Time | Instructor Action | Narration |
|------|-------------------|-----------|
| 0:19–0:20 | Paste the **Round 2 Interview Prompt** (see Appendix B) into external AI | "Now we do a second interview — but this time focused on *refining* the updated spec and *verifying* it against our Constitution." |
| 0:20–0:22 | AI asks 2–3 targeted questions; Instructor answers | "It's asking: 'Your Constitution says no PII in logs. Does your spec explicitly exclude transcript speaker names from logs?' Good catch — I need to add that." |
| 0:22–0:23 | Manually edit `spec.md` based on Round 2 answers | "I make the final edits myself. The AI asked the question; I write the answer into the spec." |

**Key Teaching Moment:**  
> "Round 2 is about alignment — does your spec match your Constitution? If not, fix the spec or update the Constitution."

---

### Phase 6: Commit & Transition (0:23 – 0:25)

| Time | Instructor Action | Narration |
|------|-------------------|-----------|
| 0:23–0:24 | Commit the refined `spec.md` | "Now — and only now — do I commit. The spec has been interrogated, updated, compared, and refined. It's Gate-2 ready." |
| 0:24–0:25 | Transition to Lesson 2.6 | "Your turn. You have 50 minutes to run this same workflow on your own spec. PM drives, team contributes. Goal: a refined `spec.md` that's ready for Gate 2." |

---

## Transition to Lesson 2.6

> "You've seen the full workflow:
> 1. **Round 1:** `/speckit.clarify` — AI asks, you answer
> 2. **Agent Mode:** AI updates the spec directly
> 3. **Comparison:** External AI flags changes and risks
> 4. **Round 2:** Interview to refine and verify Constitution alignment
> 5. **Commit:** Only after human review
>
> Now it's your turn. Open your team's `spec.md` and `constitution.md` side by side. You have 50 minutes. Go."

---

## Instructor Cheat Sheet: Troubleshooting

| Issue | Quick Fix |
|-------|-----------|
| `/speckit.clarify` returns no questions | Spec may already be tight — or too vague for the AI to parse. Check formatting. |
| Agent Mode makes unwanted changes | Revert to v1 and re-run with more specific instructions. |
| Comparison Prompt misses obvious issues | Add more specific flags to the prompt (e.g., "check for undefined error handling"). |
| Round 2 Interview goes off-topic | Re-anchor: "Focus only on Constitution alignment and ambiguous terms." |
| Students want to skip comparison step | Remind: "The comparison is your safety net. It takes 3 minutes and catches hallucinations." |

---

## Appendix A: Spec Comparison Prompt

**Purpose:** Compare `spec-v1.md` (original) with `spec-v2.md` (AI-updated) and produce a structured report of changes, risks, and potential hallucinations.

**How to Use:**
1. Copy this entire prompt into an external AI (ChatGPT, Claude, etc.)
2. Paste the full text of `spec-v1.md` and `spec-v2.md` where indicated
3. Review the Comparison Report before proceeding to Round 2

---

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

## Appendix B: Round 2 Interview Prompt (Refinement + Constitution Verification)

**Purpose:** Conduct a Socratic interview to refine the AI-updated spec and verify alignment with the Constitution.

**How to Use:**
1. Copy this entire prompt into an external AI (ChatGPT, Claude, etc.)
2. Paste your `spec-v2.md` and `constitution.md` where indicated
3. Answer the AI's questions as a team
4. Make final edits to your spec based on your answers

---

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

## Appendix C: Lesson 2.6 Timing Guide (50-minute Hands-on)

| Phase | Time | Activity |
|-------|------|----------|
| Setup | 0:00–0:03 | Open `spec.md` + `constitution.md`; save v1 |
| Round 1 | 0:03–0:15 | Run `/speckit.clarify`; answer questions as team |
| Agent Mode | 0:15–0:20 | Let AI update spec; review changes |
| Comparison | 0:20–0:30 | Paste into external AI; review Comparison Report |
| Round 2 | 0:30–0:45 | Run Interview Prompt; answer questions; make final edits |
| Commit | 0:45–0:50 | Commit refined `spec.md`; prepare for Gate 2 |

---

## Appendix D: Key Teaching Points Summary

| Principle | What to Emphasize |
|-----------|-------------------|
| **AI asks, human decides** | Round 1 is interrogation, not delegation |
| **Version control matters** | Always keep v1 before letting AI edit |
| **Fresh eyes catch hallucinations** | External AI comparison is your safety net |
| **Constitution is the law** | Round 2 verifies alignment — no exceptions |
| **Human commits** | Never commit without reading every change |

---

*End of Lesson 2.5 Demo Kit*
