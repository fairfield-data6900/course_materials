# Lesson 1.1: The "Overconfident Intern" Lecture

**Course:** AI-Assisted SDD for Business Analysts  
**Session:** Week 1 — Foundations & Setup  
**Duration:** 20 minutes  
**Goal:** Shift students from "AI as magic box" to "AI as talented but reckless subordinate"

---

## Learning Objectives

By the end of this lecture, students will be able to:
1. Explain why "vibe coding" fails in professional workflows
2. Define "context drift" and "hallucination debt"
3. Articulate the value of Executable Specifications
4. Describe the Verification Ritual (Read → Run → Test → Commit)

---

## Lecture Script

### Opening (0:00 – 0:03) — Welcome & Hook

**[SLIDE 1: Welcome to AI-Assisted Development]**

> "Welcome to AI-Assisted Software Design. Before we touch any tools, I want to change how you think about AI.
>
> Here's a question: How many of you have asked ChatGPT to 'build me an app' or 'write me some code'?"
>
> *(Pause for hands)*
>
> "And how many of you got something that worked... at first... and then broke spectacularly?"
>
> *(Knowing laughter)*
>
> "That's what we're here to fix."

---

### The Problem: Vibe Coding (0:03 – 0:08)

**[SLIDE 2: The Problem — "Vibe Coding"]**

> "There's a term for what most people do with AI: **vibe coding**. You type a vague prompt, the AI gives you something, you paste it, it sort of works, you move on.
>
> Vibe coding feels productive. You're shipping! You're moving fast!
>
> But here's the problem: **vibe coding is technical debt on a credit card with 100% interest.**
>
> Every vague prompt compounds. Every unchecked output introduces errors. And when it breaks — and it will break — you have no idea why, because you never understood what you built."

**Key Point:** Vibe coding = prompting without structure. It works until it doesn't.

---

### The Metaphor: The Overconfident Intern (0:08 – 0:15)

**[SLIDE 3: The Overconfident Intern]**

> "So how should you think about AI? Here's the mental model that will save you:
>
> **AI is an overconfident intern.**
>
> This intern has read every book. Every Stack Overflow post. Every tutorial ever written. They're brilliant. They're fast. They're eager to help.
>
> But they have **zero real-world experience.**
>
> And here's the dangerous part: they don't know what they don't know. They will confidently hand you a report that's completely wrong — with a smile."

**[SLIDE 4: The Three Behaviors of the Overconfident Intern]**

> "The overconfident intern has three signature behaviors:
>
> 1. **Assumes instead of asks.** You say 'build me a dashboard.' They don't ask 'for whom?' or 'what metrics?' They just build... something.
>
> 2. **Forgets previous instructions.** You told them the brand voice is professional. Three prompts later, they're writing like a teenager on TikTok.
>
> 3. **Confidently delivers wrong answers.** They'll cite a library that doesn't exist. They'll invent an API endpoint. And they'll do it with complete confidence.
>
> This forgetting — this drift from your original intent — is called **context drift**. And it's the root cause of most AI failures."

**Key Point:** Context drift = the AI loses track of your intent over time.

---

### The Cost: Hallucination Debt (0:15 – 0:18)

**[SLIDE 5: Hallucination Debt]**

> "When you don't catch the intern's mistakes early, you accumulate what I call **hallucination debt**.
>
> *(Point to visual: small snowball → avalanche)*
>
> Catching a logic error in a specification takes **seconds**.
>
> Catching that same error buried in 500 lines of generated code? **Hours**. Maybe days.
>
> The earlier you verify, the cheaper the fix. That's why we start with specs, not code."

**Key Point:** Hallucination debt compounds. Catch errors early or pay 10x later.

---

### The Solution: You Are the Knowledgeable Engineer (0:18 – 0:22)

**[SLIDE 6: The Knowledgeable Engineer (That's You)]**

> "So if AI is the overconfident intern, what's your role?
>
> **You are the Knowledgeable Engineer.**
>
> You don't write the code. You don't lay the bricks. You're the **architect** — you design the blueprint, and the intern executes it.
>
> Your job is **intent over syntax**. You define *what* needs to happen and *why*. The AI handles *how*.
>
> But here's the catch: **you are responsible for the output**. If the intern builds the wrong thing, that's on you. You signed off on it."

**Key Point:** You are the architect. The AI is the builder. You own the result.

---

### The Contract: Executable Specifications (0:22 – 0:26)

**[SLIDE 7: Good Spec vs. Bad Spec]**

> "So how do you manage an overconfident intern? You give them a **written contract**.
>
> In this course, that contract is called a `spec.md` — a specification document.
>
> Let me show you the difference between a bad spec and a good spec."

*(Display side-by-side comparison)*

| Bad Spec (Vibe Coding) | Good Spec (SDD) |
|------------------------|-----------------|
| "Make a podcast tool" | **Overview:** An agent skill that analyzes podcast transcripts to generate marketing content |
| *(No inputs defined)* | **Inputs:** Timestamped transcript (.txt or .srt) |
| *(No outputs defined)* | **Outputs:** Social media clips (≤60s), LinkedIn post, episode description |
| *(No constraints)* | **Constraints:** Must respect brand voice (see constitution.md); clips ≤ 60 seconds |

> "The bad spec is a wish. The good spec is a contract.
>
> And here's the key insight: **specs are executable**. They don't just document your intent — they control AI behavior. A vague spec produces vague results. A precise spec produces precise results."

**Key Point:** The `spec.md` is your contract with the intern. Precision in, precision out.

---

### The Protocol: The Verification Ritual (0:26 – 0:30)

**[SLIDE 8: The Verification Ritual]**

> "Finally, even with a good spec, you still need a management protocol. We call it the **Verification Ritual**.
>
> Every time the AI produces output, you run through four steps:"

| Step | Question |
|------|----------|
| **1. Read** | Do I understand what the AI produced? |
| **2. Run** | Does it execute without errors? |
| **3. Test** | Does it do what I asked? |
| **4. Commit** | Only now does it enter the repository |

> "Never skip steps. Never commit code you haven't personally verified.
>
> This ritual is how you prevent hallucination debt. It's how you stay in control. It's how you turn an overconfident intern into a productive team member."

**Key Point:** Read → Run → Test → Commit. Never skip steps.

---

### Preview & Transition (0:30 – 0:32)

**[SLIDE 9: What We'll Build]**

> "By Week 6, you'll build something like this."
>
> *(Show Podcast Marketing Tool end-state demo or screenshot)*
>
> "A complete agent skill that takes a raw podcast transcript and produces a marketing kit — social clips, LinkedIn posts, episode descriptions.
>
> But we don't start with code. We start with the contract. Today, you'll write your first `spec.md`.
>
> First, let's make sure everyone's environment is ready."

---

## Slide Deck Design

### Slide 1: Welcome to AI-Assisted Development

**Visual:** A human pilot and an AI co-pilot in a cockpit. The human has hands on the controls; the AI is pointing at instruments.

**Text:**
- **Headline:** Welcome to AI-Assisted Development
- **Subhead:** You are the pilot. AI is the co-pilot.
- **Footer:** You are responsible for the flight.

**Design Notes:**
- Clean, professional imagery
- Emphasize human control (hands on controls)
- Avoid cartoonish AI imagery

---

### Slide 2: The Problem — "Vibe Coding"

**Visual:** A tangled mess of code on one side; a clean blueprint on the other. Or: a person typing frantically with a "SHIP IT" button.

**Text:**
- **Headline:** The Problem: Vibe Coding
- **Bullet 1:** Vague prompt → Vague result
- **Bullet 2:** Feels productive, but compounds errors
- **Bullet 3:** When it breaks, you don't know why

**Design Notes:**
- Use contrast (chaos vs. order)
- Keep text minimal — the visual tells the story

---

### Slide 3: The Overconfident Intern

**Visual:** A cartoon intern holding a stack of papers stamped "100% CORRECT" — but the papers are upside down. Or: an eager young professional giving a thumbs-up while a small fire burns behind them.

**Text:**
- **Headline:** AI = The Overconfident Intern
- **Subhead:** Brilliant. Fast. Eager. Zero real-world experience.
- **Footer:** Your job is to manage their output, not just accept it.

**Design Notes:**
- Humor is okay here — this is the memorable metaphor
- Avoid making the intern look incompetent; they're talented but inexperienced

---

### Slide 4: The Three Behaviors

**Visual:** Three icons or illustrations representing each behavior:
1. 🤔 → ❌ (Assumes instead of asks)
2. 🧠 → 💨 (Forgets previous instructions)
3. ✅ → ❌ (Confidently wrong)

**Text:**
- **Headline:** The Intern's Three Behaviors
- **Behavior 1:** Assumes instead of asks
- **Behavior 2:** Forgets previous instructions (Context Drift)
- **Behavior 3:** Confidently delivers wrong answers

**Design Notes:**
- Use icons or simple illustrations
- Highlight "Context Drift" as a key term

---

### Slide 5: Hallucination Debt

**Visual:** A small snowball at the top of a hill transforming into an avalanche at the bottom. Or: a crack in a foundation spreading into a collapsed building.

**Text:**
- **Headline:** Hallucination Debt
- **Subhead:** Errors compound. Catch them early or pay 10x later.
- **Comparison:**
  - Catching error in spec: **Seconds**
  - Catching error in 500 lines of code: **Hours**

**Design Notes:**
- The visual should convey exponential growth of problems
- Use the snowball/avalanche metaphor for memorability

---

### Slide 6: The Knowledgeable Engineer (That's You)

**Visual:** An architect reviewing blueprints at a desk, with construction happening in the background. The architect is calm and in control; the builders are busy.

**Text:**
- **Headline:** You Are the Knowledgeable Engineer
- **Subhead:** Intent over syntax. You design; AI executes.
- **Footer:** You own the result.

**Design Notes:**
- Emphasize the human as the decision-maker
- Blueprints = specs; construction = code generation

---

### Slide 7: Good Spec vs. Bad Spec

**Visual:** Side-by-side comparison (two columns or two panels)

**Left Panel (Bad Spec):**
- Header: ❌ Vibe Coding
- "Make a podcast tool"
- *(No inputs)*
- *(No outputs)*
- *(No constraints)*

**Right Panel (Good Spec):**
- Header: ✅ Executable Spec
- **Overview:** Analyze transcripts → marketing content
- **Inputs:** Timestamped transcript (.txt/.srt)
- **Outputs:** Clips, LinkedIn post, description
- **Constraints:** Brand voice; clips ≤ 60s

**Text:**
- **Headline:** Good Spec vs. Bad Spec
- **Footer:** A vague spec produces vague results.

**Design Notes:**
- Use color coding (red for bad, green for good)
- Keep the good spec readable but detailed enough to show contrast

---

### Slide 8: The Verification Ritual

**Visual:** A circular flow diagram with four nodes:
1. **Read** (eye icon)
2. **Run** (play button icon)
3. **Test** (checkmark icon)
4. **Commit** (git commit icon)

Arrows connect them in a clockwise loop.

**Text:**
- **Headline:** The Verification Ritual
- **Subhead:** Your management protocol for the intern.
- **Footer:** Never commit code you haven't personally verified.

**Design Notes:**
- The circular design emphasizes this is a repeatable ritual
- Each step should be visually distinct

---

### Slide 9: What We'll Build

**Visual:** Screenshot or mockup of the Podcast Marketing Tool output:
- A transcript on the left
- Generated outputs on the right (social clips, LinkedIn post, episode description)

**Text:**
- **Headline:** By Week 6, You'll Build This
- **Subhead:** Raw transcript → Complete marketing kit
- **Footer:** But we start with the spec, not the code.

**Design Notes:**
- Show the end-state to motivate students
- Keep it aspirational but achievable

---

## Appendix: Key Terms Glossary

| Term | Definition |
|------|------------|
| **Vibe Coding** | Prompting AI without structure; produces unpredictable results |
| **Context Drift** | The AI loses track of your original intent over multiple interactions |
| **Hallucination Debt** | Accumulated errors from unchecked AI output; compounds over time |
| **Executable Specification** | A `spec.md` that defines inputs, outputs, and constraints — controls AI behavior |
| **Verification Ritual** | Read → Run → Test → Commit — the protocol for managing AI output |
| **Knowledgeable Engineer** | Your role: define intent, verify output, own the result |

---

## Appendix: Pitfall Warnings for Instructor

| Pitfall | Mitigation |
|---------|------------|
| Students think specs are "just documentation" | Emphasize: "Specs are executable — they control AI behavior" |
| Students want to jump to code | Remind: "The intern needs instructions first. Code comes in Week 5." |
| Skeptics ask "Why not just prompt better?" | Answer: "Prompts are ephemeral. Specs persist and compound." |
| Students feel overwhelmed by the ritual | Reassure: "It becomes automatic. Like checking mirrors before driving." |
| Students dismiss the intern metaphor as silly | Lean in: "It's memorable because it's true. You'll see." |

---

## Appendix: Transition to Lesson 1.2

After Slide 9, transition with:

> "Now let's make sure everyone's environment is ready. If you completed Week 0, this will be quick. If not, we'll get you caught up."

Proceed to **Lesson 1.2: Environment Check**.

---

*End of Lesson 1.1: The "Overconfident Intern" Lecture*