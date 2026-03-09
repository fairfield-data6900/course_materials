# Lesson 5.4 Demo Kit: `/scout` → `/review`

**Duration:** 41 min (35 min demo + 6 min Q&A)  
**Format:** Instructor Live Demo  
**Prerequisite:** Functional `parse_transcript.py` from Week 4; Holy Trinity (`spec.md`, `constitution.md`, `plan.md`) in place  
**Goal:** Demonstrate how `/scout` maps the codebase and how `/review` audits it against the Holy Trinity

---

## 🛠 Setup Checklist

| Item | Status |
|:-----|:------:|
| Podcast Skill repo open in VS Code | ☐ |
| Working directory set to `.skills/podcast-marketing/` | ☐ |
| `parse_transcript.py` functional (not just scaffolded) | ☐ |
| Holy Trinity files accessible (`spec.md`, `constitution.md`, `plan.md`) | ☐ |
| Terminal ready for `/scout` and `/review` | ☐ |
| Fallback commit tagged: `pre-scout-demo` | ☐ |

---

## 🖥 Screen Layout

```
┌─────────────────────────────┬─────────────────────────────┐
│                             │                             │
│   File Explorer             │   Terminal / AI Chat        │
│   .skills/podcast-marketing │                             │
│   ├── SKILL.md              │   > /scout                  │
│   ├── scripts/              │                             │
│   │   └── parse_transcript  │   [Output appears here]     │
│   └── ...                   │                             │
│                             │                             │
└─────────────────────────────┴─────────────────────────────┘
```

---

## ⏱ Phase-by-Phase Breakdown

---

### Opening (0:00–0:01)

| Element | Content |
|:--------|:--------|
| **Narration** | *"Week 5 is about adding the nervous system to your project — the ability to sense what's happening inside your codebase. We'll do that with two commands: `/scout` and `/review`."* |
| **Key Teaching Moment** | Mention the metaphor once, then move to practical demonstration. |

---

### Phase 1: Live `/scout` (0:01–0:16)

#### 1A: Run the Command (0:01–0:03)

| Element | Content |
|:--------|:--------|
| **Action** | Run `/scout` in terminal |
| **Narration** | *"I'm in the podcast-marketing skill folder. `/scout` auto-detects my working directory — no arguments needed. Watch what it generates."* |
| **On Screen** | `/scout` runs and generates `ARCHITECTURE.md` |

---

#### 1B: Repository Overview (0:03–0:05)

| Element | Content |
|:--------|:--------|
| **Action** | Scroll to Repository Overview section |
| **Narration** | *"First, we get a high-level summary. This tells us what the project IS — in plain English. If this doesn't match your `spec.md`, you have drift."* |
| **Key Teaching Moment** | *"This is your elevator pitch, generated from code. If you can't explain your project in 30 seconds, neither can the AI."* |

---

#### 1C: File Summaries (0:05–0:08)

| Element | Content |
|:--------|:--------|
| **Action** | Scroll to File Summaries section |
| **Narration** | *"Next, one-liner summaries for every file. This is your inventory. Notice how `parse_transcript.py` is described — does that match what you INTENDED it to do?"* |
| **Key Teaching Moment** | *"If a file summary surprises you, that's a red flag. Either the code drifted from your plan, or the AI misunderstood. Either way, investigate."* |

---

#### 1D: Architecture Diagram (0:08–0:11)

| Element | Content |
|:--------|:--------|
| **Action** | Scroll to Architecture Diagram (Mermaid) |
| **Narration** | *"Here's the visual — a Mermaid diagram showing how files relate. You can see the data flow: transcript in, JSON segments out, posts generated."* |
| **Key Teaching Moment** | *"This diagram is generated FROM your code, not your plan. If the arrows don't match your `plan.md`, you have architectural drift."* |
| **Consulting Moment** | *"For your capstones: Group A — your data flow should show imputation → feature engineering. Group B — Python gen and SQL gen should be parallel paths. Group C — parser → generator → packager."* |

---

#### 1E: Module Descriptions (0:11–0:13)

| Element | Content |
|:--------|:--------|
| **Action** | Scroll to Module Descriptions section |
| **Narration** | *"Deeper than file summaries — this explains what each module DOES and WHY. Think of it as auto-generated documentation."* |
| **Key Teaching Moment** | *"If you had to hand this project to a new developer tomorrow, this section is their onboarding guide."* |

---

#### 1F: Hotspot Report (0:13–0:16)

| Element | Content |
|:--------|:--------|
| **Action** | Scroll to Hotspot Report section |
| **Narration** | *"Hotspots are complex or risky areas — places where bugs are likely to hide. The AI flags these so you know where to focus your testing."* |
| **Key Teaching Moment** | *"In a real project, hotspots get extra code review, extra tests, and extra documentation. Don't ignore this section."* |
| **Pitfall Warning** | *"If your entire codebase is flagged as a hotspot, your code is too complex. Simplify before you scale."* |

---

### Phase 2: Live `/review` (0:16–0:31)

#### 2A: The Handoff (0:16–0:18)

| Element | Content |
|:--------|:--------|
| **Action** | Show `ARCHITECTURE.md` file created by `/scout` |
| **Narration** | *"Now we have `ARCHITECTURE.md` — a complete map of our codebase. `/review` takes this as input and compares it against our Holy Trinity: `spec.md`, `constitution.md`, and `plan.md`."* |
| **Key Teaching Moment** | *"Think of `/scout` as the census — it counts what exists. `/review` is the audit — it checks if what exists is what SHOULD exist."* |

---

#### 2B: Run the Command (0:18–0:20)

| Element | Content |
|:--------|:--------|
| **Action** | Run `/review` in terminal |
| **Narration** | *"Let's see what the auditor finds."* |
| **On Screen** | `/review` runs and generates Architecture Review Report |

---

#### 2C: Summary (0:20–0:22)

| Element | Content |
|:--------|:--------|
| **Action** | Scroll to Summary section |
| **Narration** | *"First, the headline: total issues and critical risks. This is your go/no-go indicator. Zero critical risks? You're on track. Any critical risks? Stop and fix before proceeding."* |
| **Key Teaching Moment** | *"In Week 6, you'll run `/review` before your Integration Gate. Critical risks are blockers — you cannot pass the gate with unresolved critical risks."* |

---

#### 2D: Constitution Violations (0:22–0:24)

| Element | Content |
|:--------|:--------|
| **Action** | Scroll to Constitution Violations section |
| **Narration** | *"These are violations of your `constitution.md` — your non-negotiable rules. If you said 'Python 3.11 only' and the AI used 3.12 syntax, it shows up here."* |
| **Key Teaching Moment** | *"Constitution violations are the most serious. These aren't style preferences — these are laws. Fix them first."* |
| **Expected Result** | *"Our Podcast Skill should show zero violations here — we've been disciplined about our tech stack."* |

---

#### 2E: Spec Coverage Gaps (0:24–0:26)

| Element | Content |
|:--------|:--------|
| **Action** | Scroll to Spec Coverage Gaps section |
| **Narration** | *"These are features in your `spec.md` that don't exist in your code yet. The AI is asking: 'You promised this — where is it?'"* |
| **Key Teaching Moment** | *"Not all gaps are problems. If it's in your Tier 2 (stretch goals), it's expected. If it's in Tier 1 (must-have), it's a blocker."* |
| **Consulting Moment** | *"For your capstones: Check your client success criteria. If a client requirement shows up as a gap, prioritize it."* |

---

#### 2F: Plan Alignment Issues (0:26–0:28)

| Element | Content |
|:--------|:--------|
| **Action** | Scroll to Plan Alignment Issues section |
| **Narration** | *"These are drifts from your `plan.md`. Maybe you planned to use pandas but switched to polars. Maybe you planned three tasks but built five. The AI catches these."* |
| **Key Teaching Moment** | *"Plan drift isn't always bad — sometimes you learn better approaches. But UNDOCUMENTED drift is dangerous. If you changed the plan, update `plan.md`."* |

---

#### 2G: Internal Architecture Issues (0:28–0:30)

| Element | Content |
|:--------|:--------|
| **Action** | Scroll to Internal Architecture Issues section |
| **Narration** | *"These are problems WITHIN the code itself — circular dependencies, orphan files, dead code. The AI is checking logical consistency."* |
| **Key Teaching Moment** | *"These issues don't violate your Holy Trinity — they violate good engineering. Fix them to make your code maintainable."* |

---

#### 2H: Suggested Fixes (0:30–0:31)

| Element | Content |
|:--------|:--------|
| **Action** | Scroll to Suggested Fixes section |
| **Narration** | *"Finally, actionable recommendations. The AI doesn't just complain — it tells you HOW to fix each issue. This is your to-do list."* |
| **Key Teaching Moment** | *"Don't blindly accept these fixes. Read them, understand them, then decide. The AI is still an intern — a helpful one, but still an intern."* |

---

### Phase 3: The Relationship (0:31–0:35)

| Element | Content |
|:--------|:--------|
| **Action** | Show both outputs side by side (split screen) |
| **Narration** | *"Let's connect the dots. `/scout` generates `ARCHITECTURE.md` — a map of what EXISTS. `/review` reads that map and compares it to what SHOULD exist. You cannot govern what you haven't first mapped."* |
| **Key Teaching Moment** | *"The sequence matters. If you run `/review` without `/scout`, you're auditing against stale information. Always scout first, then review."* |
| **Capstone Connection** | *"In your capstones, you'll run this sequence before every gate. It's your pre-flight checklist."* |

---

### Q&A (0:35–0:41)

| Element | Content |
|:--------|:--------|
| **Prompt** | *"Questions? This is a good time to ask about how `/scout` and `/review` apply to your specific capstone."* |

**Anticipated Questions:**

| Question | Response |
|:---------|:---------|
| *"What if `/review` finds issues we can't fix in time?"* | *"Document them in `DEBT.md`. Acknowledge the gap, explain why, and note when you'll address it."* |
| *"How often should we run these?"* | *"Before every gate, minimum. Ideally, after every major code change."* |
| *"Can we run `/review` on just one file?"* | *"Currently, `/review` reads the full `ARCHITECTURE.md`. For file-level checks, use `/review-skill` on individual skills."* |

---

## 🚀 Transition Cue to Lesson 5.5

| Element | Content |
|:--------|:--------|
| **Narration** | *"You've seen the nervous system in action. Now it's your turn. In the next session, you'll run `/scout` and `/review` on your own capstone skills. PMs — this is where you start building your integration audit muscle."* |

---

## 👨‍🏫 Instructor Notes

| Note | Detail |
|:-----|:-------|
| **No code walkthrough needed** | `/scout` output replaces manual code explanation |
| **Clean code expected** | Demo runs on compliant code; explain what flags WOULD appear if drift existed |
| **Live results only** | No pre-generated sample outputs; trust the live demo |
| **Consulting moments** | Use capstone-specific examples when explaining each `/review` section |
| **If live demo fails** | Reset to `pre-scout-demo` commit and re-run; do not switch to slides |

---

## 💡 Quick Reference: `/scout` vs `/review`

| Aspect | `/scout` | `/review` |
|:-------|:---------|:----------|
| **Purpose** | Map what EXISTS | Audit against what SHOULD exist |
| **Input** | Auto-detects working directory | Reads `ARCHITECTURE.md` |
| **Output** | `ARCHITECTURE.md` | Architecture Review Report |
| **Checks against** | The codebase itself | Holy Trinity (`spec.md`, `constitution.md`, `plan.md`) |
| **When to run** | After major code changes | Before every gate |

---

## 📄 `/scout` Output Structure

| Section | Content |
|:--------|:--------|
| **Repository Overview** | High-level summary of the project |
| **File Summaries** | One-liner description per file |
| **Architecture Diagram** | Mermaid diagram showing file relationships and data flow |
| **Module Descriptions** | Detailed explanation of what each module does and why |
| **Hotspot Report** | Complex or risky areas flagged for extra attention |
| **Example Diagrams** | Additional Mermaid visualizations |

---

## 📄 `/review` Output Structure

| Section | Content |
|:--------|:--------|
| **Summary** | Total issues + critical risks |
| **Constitution Violations** | Drift from `constitution.md` |
| **Spec Coverage Gaps** | Missing requirements from `spec.md` |
| **Plan Alignment Issues** | Drift from `plan.md` |
| **Internal Architecture Issues** | Logical inconsistencies in the code itself |
| **Suggested Fixes** | Actionable recommendations |

---

*End of Lesson 5.4 Demo Kit*
