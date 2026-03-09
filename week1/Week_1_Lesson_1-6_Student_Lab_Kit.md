# Lesson 1.6: Logic Stress Test & Refinement — Student Lab Kit

**Duration:** 49 Minutes (02:06 – 02:55)  
**Format:** AI-Assisted Brainstorm Stress Test + Team Debate + Spec Refinement  
**Goal:** Use AI-generated "Devil's Advocate" questions to surface hidden assumptions, debate as a team, and document design decisions.

---

## 🎯 What You'll Accomplish

By the end of this session, your team will have:

- ✅ Used the **Devil's Advocate prompt** to stress-test your own `spec.md`
- ✅ **Debated as a team** which questions are real concerns vs. noise
- ✅ **Documented decisions** in your `decisions.md` file
- ✅ **Refined your spec** based on the debate outcomes
- ✅ Committed draft v1 of your `spec.md` to GitHub

---

## 👥 Team Roles During This Lab

| Role | Responsibility |
|------|----------------|
| **PM** | Runs the Devil's Advocate prompt; facilitates debate; owns the commit |
| **Skill Owner A** | Contributes domain perspective; challenges assumptions for their skill area |
| **Skill Owner B** | Contributes domain perspective; plays "skeptic" role during debate |
| **Everyone** | Participates in debate; votes on decisions; contributes to refinement |

---

## ⏱️ Session Timeline

| Time | Phase | Activity |
|------|-------|----------|
| **00:00 – 00:05** | **Setup** | PM pastes Devil's Advocate prompt into AI; shares team's `spec.md` |
| **00:05 – 00:15** | **AI Provocation** | AI generates 5-7 provocative questions; PM screen-shares |
| **00:15 – 00:30** | **Team Debate** | Team discusses each question; PM records decisions in `decisions.md` |
| **00:30 – 00:45** | **Refinement Sprint** | Team updates `spec.md` based on debate conclusions |
| **00:45 – 00:49** | **Commit Draft v1** | PM commits `spec.md` and `decisions.md` to GitHub |

---

## Phase 1: Setup (5 min)

### Step 1.1: Create Your Decision Log File

In VS Code, create a new file:

```bash
touch decisions.md
```

Or manually create `decisions.md` in your project root.

### Step 1.2: Open Your AI Chat

Open any AI chat interface:
- **GitHub Copilot Chat** (in VS Code)
- **ChatGPT** (chat.openai.com)
- **Claude** (claude.ai)

### Step 1.3: Paste the Devil's Advocate Prompt

Copy and paste the **entire prompt from Section 6** of this kit into your AI chat.

### Step 1.4: Share Your Spec with the AI

After pasting the prompt, share your `spec.md`:

**Option A — Upload:** Attach your `spec.md` file (if supported)

**Option B — Copy/Paste:**
1. Open `.specify/specs/001-your-project-name/spec.md`
2. Select all (`Ctrl+A` or `Cmd+A`)
3. Copy and paste into the chat after the prompt

---

## Phase 2: AI Provocation (10 min)

### What to Expect

The AI will generate **5-7 provocative questions** about your spec. Each question will include:

- **The Question** — A challenge to your assumptions
- **Why This Matters** — What's at stake if this isn't addressed
- **Discussion Starter** — A prompt to help your team debate

### Example Output

> **Question 1: "Who decides what 'clean' means?"**
>
> **Why This Matters:** If the analyst and the data scientist have different definitions of "clean," your tool might satisfy one and frustrate the other.
>
> **Discussion Starter:** Ask each team member to write down their definition of "clean data" without talking to each other. Then compare.

### PM Action

- **Screen-share** the AI output so the whole team can see
- **Read each question aloud** before moving to the debate phase
- **Don't react yet** — just capture the questions

---

## Phase 3: Team Debate (15 min)

This is the most important phase. The goal is **discussion**, not just fixing.

### Debate Protocol

For each question (aim for 2-3 minutes per question):

| Step | PM Action | Team Action |
|------|-----------|-------------|
| 1 | Read the question aloud | Everyone listens |
| 2 | Read "Why This Matters" | Everyone considers the stakes |
| 3 | Ask: "Is this a real concern for our project?" | Team discusses openly |
| 4 | Ask: "What should we do about it?" | Team proposes options |
| 5 | Call for a decision | Team agrees on action |
| 6 | Record in `decisions.md` | PM logs the decision |

### Decision Options

For each question, choose ONE:

| Decision | When to Use | What to Record |
|----------|-------------|----------------|
| **Address Now** | This is critical; we need to update the spec today | Log the decision + update spec in Phase 4 |
| **Defer to Week 2** | Important but needs more thought; constitution will help | Log as "Open Question" for Week 2 |
| **Dismiss** | Not relevant to our project | Log briefly with rationale |

### Time Management

- **Don't get stuck!** If debate exceeds 3 minutes, PM says: "Let's mark this as 'Needs more discussion' and move on."
- **Prioritize:** If you have 7 questions and only 15 minutes, focus on the 5 most important ones.

---

## Phase 4: Refinement Sprint (15 min)

### Step 4.1: Review Your Decision Log

Look at your `decisions.md`. For every row marked **"Address Now"**:

1. Open your `spec.md`
2. Find the relevant section
3. Make the update

### Step 4.2: Common Refinements

| Decision Type | Spec Update |
|---------------|-------------|
| "We need to define 'clean'" | Add a definition to Section 1 (Project Overview) or Section 4 (Constraints) |
| "We need error handling" | Add edge cases to Section 6 (Out of Scope) |
| "Success criteria are vague" | Make Section 5 more measurable |
| "Scope is too broad" | Move features to "Out of Scope" or mark as COULD (P3) |

### Step 4.3: Mark Open Questions

For items marked **"Defer to Week 2"**, add a note in your spec:

```markdown
<!-- OPEN QUESTION: [Question from Devil's Advocate] — To be resolved in Week 2 with constitution.md -->
```

This creates a visible reminder for next week.

---

## Phase 5: Commit Draft v1 (4 min)

### Step 5.1: Save Both Files

- Save `spec.md`
- Save `decisions.md`

### Step 5.2: Stage and Commit

1. Open **Source Control** in VS Code (`Ctrl+Shift+G`)
2. Stage both files (click "+" next to each)
3. Commit message: `"docs: spec draft v1 + decision log after stress test"`
4. Click **Commit**, then **Sync Changes**

### Step 5.3: Verify

Your repo should now contain:
- `.specify/specs/001-your-project-name/spec.md` — Updated draft
- `decisions.md` — Your debate record

---

## 📝 Debate Decision Log Template

Copy this template into your `decisions.md` file:

```markdown
# Debate Decision Log — [Your Project Name]

**Date:** [Today's Date]  
**Team Members Present:** [Names]

## Purpose

This log captures the outcomes of our Devil's Advocate stress test. Each row represents a question raised by the AI and our team's decision on how to handle it.

---

## Decision Log

| # | Question / Conflict | Options Considered | Decision | Rationale |
|---|---------------------|-------------------|----------|-----------|
| 1 | *Example: Who decides what "clean" means?* | A) User-defined rules; B) AI-standard defaults; C) Defer to constitution | **Option A** | User must maintain control over data integrity definitions |
| 2 | | | | |
| 3 | | | | |
| 4 | | | | |
| 5 | | | | |

---

## Open Questions (Deferred to Week 2)

| # | Question | Why Deferred | Week 2 Action |
|---|----------|--------------|---------------|
| 1 | | | |
| 2 | | | |

---

## Dismissed Questions

| # | Question | Why Dismissed |
|---|----------|---------------|
| 1 | | |

---

## Summary

- **Total Questions Raised:** [#]
- **Addressed Now:** [#]
- **Deferred to Week 2:** [#]
- **Dismissed:** [#]

**Key Insight from This Session:**  
[One sentence summarizing the most important thing your team learned]
```

---

## 🗣️ The Devil's Advocate Prompt

Copy and paste this entire prompt into your AI chat:

```
# The Devil's Advocate — Brainstorm Stress Test

## Your Role

You are a curious but skeptical colleague reviewing an early-stage project specification. You've seen many projects fail not because of bad code, but because teams didn't ask the hard questions early enough.

Your job is NOT to:
- Find bugs or formatting issues
- Grade the spec
- Provide answers or solutions

Your job IS to:
- Ask the questions that make the team pause and say "Hmm, we should talk about that"
- Surface assumptions the team may not realize they're making
- Provoke healthy debate that strengthens the spec

## Important Context

This spec is a **brainstorming draft**. The team hasn't defined technical guardrails yet (that comes in Week 2 with `constitution.md`). Focus on the *ideas and logic*, not the *rules, formatting, or implementation details*.

## Your Task

Read the spec carefully, then generate **5-7 "Devil's Advocate" questions**.

### What Makes a Good Devil's Advocate Question?

✅ **Challenges hidden assumptions**
- "You say the user wants 'clean data' — but whose definition of clean?"

✅ **Surfaces unstated trade-offs**
- "This feature list is ambitious. If you could only ship three, which three?"

✅ **Explores boundaries and edge cases**
- "Where exactly does this tool's responsibility end and the user's begin?"

✅ **Reveals tensions within the spec**
- "Your success criteria say 'fast' but your feature list says 'comprehensive.' Can you have both?"

✅ **Questions the problem itself**
- "You're solving X, but is X actually the problem? Or is it a symptom?"

### What Makes a Bad Question? (Avoid These)

❌ Nitpicky formatting or grammar issues
❌ Questions with obvious answers already in the spec
❌ Checklist-style items ("Did you define the input format?")
❌ Technical implementation details (too early for that)
❌ Questions that have a single "right" answer

## Output Format

For each question, provide:

### Question [#]: [The provocative question]

**Why This Matters:** [One sentence explaining what's at stake]

**Discussion Starter:** [A prompt to help the team debate — e.g., "Ask each team member..." or "Consider what happens if..." or "Compare this to..."]

---

## Tone Guidance

- Be **curious**, not critical
- Be **provocative**, not pedantic
- Be a **thinking partner**, not a grader

The team should walk away with a richer understanding of their project — even if they don't change a single line.

## Final Reminder

These questions have no "right" answers. The value is in the debate, not the resolution.

Now, read the spec below and generate your Devil's Advocate questions.

---

[PASTE YOUR SPEC.MD CONTENT BELOW THIS LINE]
```

---

## ✅ Success Checklist

Before the session ends, verify your team has completed:

| Criterion | ✓ |
|-----------|---|
| Devil's Advocate prompt generated 5-7 questions | ☐ |
| Team debated at least 5 questions | ☐ |
| `decisions.md` has at least 3 rows completed | ☐ |
| At least 2 refinements made to `spec.md` | ☐ |
| Any "automatic" features now have human-in-the-loop notes | ☐ |
| Both `spec.md` and `decisions.md` committed to GitHub | ☐ |

---

## 🆘 Troubleshooting

| Problem | Solution |
|---------|----------|
| **AI gives checklist-style questions** | Remind it: "These are too checklist-like. Give me questions that would spark a 5-minute debate among the team." |
| **Team can't agree on a decision** | Mark it as "Defer to Week 2" and move on. The constitution will help. |
| **Debate is taking too long** | PM enforces 3-minute limit per question. Say: "Let's capture this as 'Needs more discussion' and move on." |
| **We don't have time for all questions** | Prioritize. Ask: "Which 3 questions feel most important?" Focus on those. |
| **Spec changes feel too big** | That's okay! Mark major changes as "Defer to Week 2" and make a note. |

---

## 💡 Tips for a Productive Debate

| Do | Don't |
|----|-------|
| Let everyone speak before deciding | Let one person dominate |
| Say "I disagree because..." | Say "That's wrong" |
| Ask "What would change your mind?" | Dig into fixed positions |
| Time-box to 2-3 min per question | Spend 15 min on one question |
| Record "Defer" items for Week 2 | Try to solve everything today |
| Celebrate disagreement — it means you're thinking | Rush to consensus |

---

## 🔜 What's Next?

**End of Week 1:** You now have a stress-tested draft `spec.md` and a decision log.

**Week 2 Preview:** Your spec is still **unbounded** — it has logic, but no guardrails.

In Week 2, you'll:
1. Create `constitution.md` — the rules that constrain your spec
2. Run `/speckit.clarify` — the AI "Final Boss" that interrogates your spec
3. Refine your spec based on the clarify output

**The real test is coming. Today was the warm-up.**

---

*End of Lesson 1.6 Student Lab Kit*