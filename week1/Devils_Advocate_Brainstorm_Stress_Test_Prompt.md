# The Devil's Advocate — Brainstorm Stress Test Prompt

**Purpose:** Use this prompt to stress-test your team's draft `spec.md`. The AI will generate provocative questions designed to spark team debate — not give you answers.

**When to Use:** Lesson 1.6, after your team has completed the initial `spec.md` draft.

**How to Use:**
1. Open your AI chat (Copilot, ChatGPT, Claude, or any LLM)
2. Copy and paste the entire prompt below
3. Then paste your team's `spec.md` content
4. Review the questions as a team and debate each one

---

## [COPY AND PASTE THE PROMPT BELOW]

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
- "You say the user wants 'clean data' — but whose definition of clean? The analyst's or the data scientist's?"

✅ **Surfaces unstated trade-offs**
- "This feature list is ambitious. If you could only ship three of these, which three? Why?"

✅ **Explores boundaries and edge cases**
- "Where exactly does this tool's responsibility end and the user's begin?"

✅ **Reveals tensions within the spec**
- "Your success criteria say 'fast' but your feature list says 'comprehensive.' Can you have both?"

✅ **Questions the problem itself**
- "You're solving X, but is X actually the problem? Or is it a symptom of something deeper?"

### What Makes a Bad Question? (Avoid These)

❌ Nitpicky formatting or grammar issues
❌ Questions with obvious answers already in the spec
❌ Checklist-style items ("Did you define the input format?")
❌ Technical implementation details (too early for that)
❌ Questions that have a single "right" answer

## Output Format

For each question, provide:

### Question [#]: [The provocative question]

**Why This Matters:** [One sentence explaining what's at stake if this isn't addressed]

**Discussion Starter:** [A prompt to help the team debate — e.g., "Ask each team member to answer independently, then compare..." or "Consider the perspective of..." or "What would happen if..."]

---

## Tone Guidance

- Be **curious**, not critical
- Be **provocative**, not pedantic
- Be a **thinking partner**, not a grader
- Your questions should **start** conversations, not end them

The team should walk away from this exercise with a richer understanding of their own project — even if they don't change a single line in the spec.

## Final Reminder

These questions have no "right" answers. The value is in the debate, not the resolution. Some questions may lead to spec changes; others may simply confirm the team's original thinking. Both outcomes are valid.

Now, read the spec below and generate your Devil's Advocate questions.

---

[PASTE YOUR TEAM'S SPEC.MD CONTENT BELOW THIS LINE]
```

---

## Example Output (What Your Team Will See)

For a "Data Prep Pipeline" spec, the AI might generate:

---

### Question 1: "Who decides what 'clean' means?"

**Why This Matters:** If the analyst and the data scientist have different definitions of "clean," your tool might satisfy one and frustrate the other — or worse, create a false sense of confidence in the data.

**Discussion Starter:** Ask each team member to write down their definition of "clean data" without talking to each other. Then compare. Are they the same?

---

### Question 2: "What happens when your tool is wrong?"

**Why This Matters:** Imputation is educated guessing. If your tool guesses incorrectly, does the user even know? Can they override it? Or do they just trust the output blindly?

**Discussion Starter:** Imagine a user who ran your tool last week and just discovered the output was wrong. What do they do now? Does your spec account for that scenario?

---

### Question 3: "Is this tool for exploration or production?"

**Why This Matters:** An exploration tool can be forgiving and flexible. A production tool needs to be bulletproof and predictable. Your spec seems to want both — is that realistic?

**Discussion Starter:** If a data analyst uses this at 2am before a board meeting, what's the worst thing that could happen? Now, does your spec prevent that?

---

### Question 4: "What's the smallest useful version of this?"

**Why This Matters:** Your feature list is ambitious. Ambitious is good, but it's also risky. If you had to ship in 2 weeks with only one feature, which one would it be?

**Discussion Starter:** Each team member picks their "one feature." If you all pick the same one, great — that's your MVP. If not, you have a prioritization conversation to have.

---

### Question 5: "How does the user know it worked?"

**Why This Matters:** Your success criteria say "data is cleaned," but how does the user verify that without re-doing the work manually? Trust is earned, not assumed.

**Discussion Starter:** Pretend you're a skeptical manager reviewing the output. What would you check? Does your tool make that easy or hard?

---

## How to Use the Output

1. **PM reads each question aloud** to the team
2. **Team discusses** (2-3 minutes per question):
   - "Is this a real concern for our project?"
   - "What should we do about it?"
3. **PM records the decision** for each question:
   - **Address Now** — Update the spec before committing
   - **Defer to Week 2** — Add to "Open Questions" for constitution phase
   - **Dismiss** — Not relevant to our project (note why)
4. **Move to the next question** — Don't get stuck; time-box debates

---

## Tips for a Productive Debate

| Do | Don't |
|----|-------|
| Let everyone speak before deciding | Let one person dominate |
| Say "I disagree because..." | Say "That's wrong" |
| Ask "What would change your mind?" | Dig into positions |
| Time-box to 2-3 min per question | Spend 15 min on one question |
| Record "Defer" items for Week 2 | Try to solve everything now |

---

*End of Devil's Advocate Prompt*