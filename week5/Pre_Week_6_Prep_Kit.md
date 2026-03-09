# 📚 Pre-Week 6 Prep Kit

**Complete before:** Week 6 class  
**Total time:** ~45 min  
**Goal:** Prepare for integration, understand observability as a "logic test," and verify your skills are demo-ready.

---

## Overview

| Item | Type | Purpose | Time |
|:-----|:-----|:--------|:-----|
| 1. Sub-agents & Manager-Worker Pattern | 📖 Read | Prep for Group C presentation | 15 min |
| 2. Observability as a Post-hoc Logic Test | 📖 Read | Understand traces and diagrams as validation | 10 min |
| 3. Demo Readiness Audit | 🛠️ Try | Run pipeline + `/scout` → `/review`; document "landmine" | 15 min |
| 4. Gate 6 Checklist Preview | 📖 Read | Know what's due by end of Week 6 | 5 min |

---

## Item 1: Sub-agents & Manager-Worker Pattern (15 min)

### 📖 Read

> Instructor will provide reading material on sub-agents and the Manager-Worker pattern before Week 6.

- [Gemini Chat](https://gemini.google.com/share/9948722e052b)
- [Deep Research Report](https://gemini.google.com/share/c373fd112572)

### Key Concepts to Understand

| Concept | Definition | Why It Matters |
|:--------|:-----------|:---------------|
| **Sub-agent** | A specialized AI agent that handles one specific task | Breaks complex work into manageable pieces |
| **Manager-Worker Pattern** | One "manager" agent delegates tasks to multiple "worker" agents | Enables parallel work; mirrors PM/Skill Owner structure |
| **Delegation** | Manager decides WHAT to do; workers decide HOW | Clear separation of concerns |

### Connection to Your Capstone

| Course Role | Manager-Worker Parallel |
|:------------|:------------------------|
| PM / Integrator | Manager agent — coordinates, delegates, integrates |
| Skill Owner A | Worker agent — executes Skill A tasks |
| Skill Owner B | Worker agent — executes Skill B tasks |

### Prep Questions (Bring to Class)

1. In your capstone, what decisions should the "manager" (PM) make vs. the "workers" (Skill Owners)?
2. How does your `interface-spec.md` define the contract between manager and workers?
3. What happens if a worker agent fails? Who handles the error?

---

## Item 2: Observability as a Post-hoc Logic Test (10 min)

### 📖 Read

**The Problem:** You're a non-coder. You can't read pytest assertions or debug stack traces. But you still need to verify that the AI did what you intended.

**The Solution:** Observability — making the AI's decision-making visible so you can audit it AFTER execution.

---

### The Non-Coder Validation Stack

| Traditional Dev Test | Non-Coder "Observability" Test |
|:---------------------|:-------------------------------|
| Unit Tests (Pytest) | **Trace Logs** — "Why did the AI make this decision?" |
| Integration Tests | **Mermaid Logic Diagrams** — "What path did it take?" |
| Code Coverage | **`/review` vs. Constitution** — "Did it follow the rules?" |
| Manual Debugging | **Devil's Advocate Questions** — "What could go wrong?" |

---

### What is a "Post-hoc Logic Test"?

A **post-hoc logic test** means you verify the AI's decisions AFTER it runs, by comparing:

| What You Compare | Against What | Question You're Answering |
|:-----------------|:-------------|:--------------------------|
| **Trace output** (decision logs) | `spec.md` acceptance criteria | "Did it do what the spec required?" |
| **Mermaid diagram** (logic path) | `plan.md` expected flow | "Did it follow the intended path?" |
| **`/review` output** | `constitution.md` rules | "Did it violate any constraints?" |

---

### Example: Podcast Skill Observability

**Scenario:** Your Podcast Marketing Skill processes a 60-minute transcript and generates LinkedIn posts.

| What the Skill Did | Trace Log Output | Post-hoc Validation |
|:-------------------|:-----------------|:--------------------|
| Cut at timestamp 12:34 | `"Cut at 12:34: Speaker change (Host → Guest)"` | ✅ Matches spec: "Segment on speaker changes" |
| Cut at timestamp 18:02 | `"Cut at 18:02: Topic shift ('AI ethics' → 'regulation')"` | ✅ Matches spec: "Segment on topic shifts" |
| Skipped timestamp 22:15 | `"Skip 22:15: Segment too short (< 30s threshold)"` | ⚠️ Check spec: Is 30s threshold defined? |
| Generated 5 LinkedIn posts | `"Generated 5 posts; avg length 280 chars"` | ✅ Matches spec: "Max 300 chars per post" |

**The Key Insight:** You didn't write code. You didn't run pytest. But you validated the AI's logic by reading its trace and comparing against your spec.

---

### How This Connects to Week 6

| Week 5 | Week 6 |
|:-------|:-------|
| Built individual skills | Integrate skills together |
| Ran `/review` on single skill | Run `/review` on integrated pipeline |
| Verified skill logic in isolation | Verify **cross-skill logic** via observability |

In Week 6, you'll trace data flowing from Skill A → Skill B and verify the handoff logic matches your `interface-spec.md`.

---

## Item 3: Demo Readiness Audit (15 min)

### 🛠️ Try

**Goal:** Verify your integrated pipeline works end-to-end AND identify your "landmine" (what usually breaks).

---

### Part A: Run Pipeline End-to-End (7 min)

1. Open your capstone project in VS Code / Codespaces
2. Run your skill(s) with sample input:
   - Skill A: Does it produce expected output?
   - Skill B: Does it consume Skill A's output correctly?
3. Document the result:

```markdown
## Pipeline Test — [Date]

### Skill A
- Input: [what you provided]
- Output: [what it produced]
- Status: ✅ Working / ⚠️ Partial / ❌ Broken

### Skill B
- Input: [Skill A output]
- Output: [what it produced]
- Status: ✅ Working / ⚠️ Partial / ❌ Broken

### Integration
- Data handoff: ✅ Smooth / ⚠️ Manual step required / ❌ Broken
```

---

### Part B: Run `/scout` → `/review` (5 min)

1. Run `/scout` on your project:

```
/scout
```

2. Verify `ARCHITECTURE.md` is up to date
3. Run `/review`:

```
/review
```

4. Check for:
   - ❌ Critical errors (must fix before Week 6)
   - ⚠️ Warnings (document for Week 6 lab)

---

### Part C: Document Your "Landmine" (3 min)

Every project has a "landmine" — the thing that usually breaks during demos.

```markdown
## My Landmine

**What usually breaks:** [describe]

**Why it breaks:** [root cause if known]

**Workaround:** [what you do when it breaks]

**Fix plan:** [how you'll address it in Week 6]
```

**Common Landmines:**

| Landmine | Example | Mitigation |
|:---------|:--------|:-----------|
| API timeout | LLM takes too long on large input | Add timeout handling; use smaller test input |
| Format mismatch | Skill A outputs JSON, Skill B expects CSV | Align formats in `interface-spec.md` |
| Missing dependency | Script fails because library not installed | Add to `requirements.txt` |
| Context overflow | AI loses context mid-task | Use `/handoff` to save state |

---

## Item 4: Gate 6 Checklist Preview (5 min)

### 📖 Read

**Gate 6: Integration Gate** — Due at end of Week 6

| Criterion | Owner | What It Means |
|:----------|:------|:--------------|
| Happy Path working | Team | End-to-end pipeline runs with sample input |
| All skills integrated | Skill Owners | Skill A output flows into Skill B |
| `/review` audit completed | PM | No ❌ critical errors on integrated project |
| Integration Test Plan executed | PM | At least Happy Path + 1 edge case tested |
| Blockers documented in `DEBT.md` | PM | Any unresolved issues tracked |

---

### Self-Assessment: Are You Ready for Gate 6?

| Question | Yes | No | Action if No |
|:---------|:---:|:--:|:-------------|
| Can you run your pipeline end-to-end? | ☐ | ☐ | Fix in Week 6 lab |
| Does Skill A output match Skill B input format? | ☐ | ☐ | Update `interface-spec.md`; align formats |
| Have you run `/review` with no ❌ errors? | ☐ | ☐ | Address critical errors before class |
| Do you know your "landmine"? | ☐ | ☐ | Complete Item 3 above |
| Is your Integration Test Plan drafted? | ☐ | ☐ | PM completes before Week 6 |

---

## Checklist: Pre-Week 6 Complete

| Item | Status |
|:-----|:------:|
| 1. Sub-agents & Manager-Worker reading reviewed | ☐ |
| 2. Observability concept understood | ☐ |
| 3. Demo Readiness Audit completed | ☐ |
| 4. Gate 6 criteria understood | ☐ |
| **Landmine documented** | ☐ |
| **`/review` run with no ❌ errors** | ☐ |

---

## Bring to Week 6

1. Your documented "landmine" and mitigation plan
2. Any ⚠️ warnings from `/review` that need discussion
3. Questions about sub-agents / Manager-Worker pattern
4. Your Integration Test Plan (PM)

---

*End of Pre-Week 6 Prep Kit*
