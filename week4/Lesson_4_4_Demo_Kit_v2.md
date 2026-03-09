# 📋 Lesson 4.4 Demo Kit: `/speckit.tasks` & Atomic Decomposition

**Duration:** 25 min  
**Format:** Instructor Live Demo  
**Prerequisite:** Finalized `plan.md` from Week 3 (Podcast Skill); students have run `checklist` as pre-work  
**Goal:** Model how to transform a `plan.md` into atomic, testable tasks with Black-Box Test Tables, then verify alignment using `analyze`.

---

## 🛠 Setup Checklist

| Item | Status |
|:-----|:------:|
| Podcast Skill repo open in VS Code | ☐ |
| `plan.md` visible in editor (left pane) | ☐ |
| `spec.md` accessible (for `analyze` comparison) | ☐ |
| Terminal ready for `/speckit.tasks` (right pane) | ☐ |
| Fallback commit tagged: `pre-tasks-demo` | ☐ |
| `constitution.md` accessible (for Tech Stack reference) | ☐ |

---

## 🖥 Screen Layout Recommendation

```
┌─────────────────────────────┬─────────────────────────────┐
│                             │                             │
│   plan.md (read-only)       │   Terminal / AI Chat        │
│                             │                             │
│   - Technical Context       │   > /speckit.tasks          │
│   - Project Structure       │   > /analyze                │
│   - Demo Scope              │                             │
│                             │   [AI output appears here]  │
│                             │                             │
└─────────────────────────────┴─────────────────────────────┘
```

---

## ⏱ Phase-by-Phase Breakdown

### Phase 1: The Hand-off (0:00–0:03)

| Element | Content |
|:--------|:--------|
| **Action** | Scroll through `plan.md` on screen |
| **Narration** | *"We finished Week 3 with a solid `plan.md` — it tells us WHAT we're building and WHY. But it doesn't tell us the exact STEPS. That's what `tasks.md` is for. We're handing off from strategy to execution."* |
| **Key Teaching Moment** | *"Think of `plan.md` as the architect's blueprint. `tasks.md` is the construction schedule — which wall gets built first, which wiring comes before drywall."* |
| **On Screen** | Highlight the "Demo Scope" and "Project Structure" sections of `plan.md` |
| **Pre-Work Check** | *"You all ran `checklist` before class, right? That confirmed your `plan.md` aligns with your `spec.md`. Now we can safely decompose into tasks."* |

---

### Phase 2: The Trigger (0:03–0:08)

| Element | Content |
|:--------|:--------|
| **Action** | Run `/speckit.tasks` in terminal |
| **Narration** | *"Watch what happens. The AI reads our `plan.md` and proposes a task breakdown. But remember — this is the 'Overconfident Intern.' We don't accept blindly."* |
| **Key Teaching Moment** | *"Notice how fast it generates. That speed is a feature AND a risk. Fast output means fast mistakes. Our job is verification."* |
| **On Screen** | AI generates initial `tasks.md` with 4–6 tasks |
| **Pitfall Warning** | *"If the AI asks clarifying questions here, answer them — but keep answers short. Long answers invite scope creep."* |

---

### Phase 3: Atomic Refinement (0:08–0:14)

| Element | Content |
|:--------|:--------|
| **Action** | Review each generated task; identify one that's too vague |
| **Narration** | *"Let's check: Is each task ATOMIC? Can it be completed in one sitting? Can we test it independently?"* |

**Live Edit Example:**

| Before | After |
|:-------|:------|
| `Task 2: Process the transcript` | `Task 2: Parse transcript.txt and extract timestamped speaker segments as JSON array` |

| Element | Content |
|:--------|:--------|
| **Key Teaching Moment** | *"'Process' is a red flag word. So is 'handle,' 'manage,' and 'deal with.' These are vague verbs. We need action verbs with clear outputs: 'parse,' 'extract,' 'generate,' 'validate.'"* |
| **Pitfall Warning** | *"Don't over-atomize. If a task takes 5 minutes, it's probably too small. Aim for 30–90 minute chunks."* |

---

### Phase 4: The Contract — Black-Box Test Tables (0:14–0:19)

| Element | Content |
|:--------|:--------|
| **Action** | Add a Black-Box Test Table to the refined Task 2 |
| **Narration** | *"Now we write the CONTRACT. Before any code exists, we define: What goes IN? What comes OUT? This is how we'll know the task is DONE."* |

**Live Edit Example:**

```markdown
### Task 2: Parse transcript.txt → JSON segments

**Black-Box Test Table:**

| Input | Expected Output | Edge Case? |
|:------|:----------------|:-----------|
| `transcript.txt` with 3 speakers | JSON array with 3 speaker objects | No |
| `transcript.txt` with timestamps `[00:00]`, `[01:23]` | Each segment includes `start_time` field | No |
| Empty `transcript.txt` | Empty JSON array `[]` | Yes |
| `transcript.txt` with malformed timestamp `[99:99]` | Error logged; segment skipped | Yes |
```

| Element | Content |
|:--------|:--------|
| **Key Teaching Moment** | *"Notice the edge cases. The intern won't think of these. YOU must. What happens when the input is empty? Malformed? This is where bugs hide."* |
| **Pitfall Warning** | *"Don't write 20 test cases. 3–5 per task is enough. Cover: happy path, empty input, malformed input."* |

---

### Phase 5: Alignment Check with `analyze` (0:19–0:25)

| Element | Content |
|:--------|:--------|
| **Action** | Run `/analyze` in terminal |
| **Narration** | *"Final check: We've decomposed our plan into tasks. But did we drift? Did the intern sneak in requirements that aren't in the spec? Did we miss something? The `analyze` command audits all three artifacts at once."* |

**What `analyze` Does:**

> Identifies inconsistencies, duplications, ambiguities, and underspecified items across the three core artifacts (`spec.md`, `plan.md`, `tasks.md`).

**On Screen — Sample `analyze` Output:**

```
🔍 Analyzing spec.md ↔ plan.md ↔ tasks.md...

✅ CONSISTENT:
   - Output formats (LinkedIn, X thread) match across all artifacts
   - Input source (transcript.txt) consistent

⚠️ AMBIGUITY DETECTED:
   - Task 3 references "summary length" but spec.md doesn't define max character count
   - Recommendation: Add character limit to spec.md or remove from task

⚠️ UNDERSPECIFIED:
   - spec.md mentions "error handling" but no task covers error logging
   - Recommendation: Add Task 5 for error handling or clarify scope

✅ NO DUPLICATIONS FOUND
```

| Element | Content |
|:--------|:--------|
| **Key Teaching Moment** | *"See that ambiguity? The intern added 'summary length' to Task 3, but our spec never defined it. That's Feature Creep — the intern getting creative. We catch it NOW, not in Week 6 when the code is written."* |
| **Live Fix** | Either update `spec.md` to include the requirement, OR remove it from `tasks.md` — show the decision process |
| **Pitfall Warning** | *"Don't ignore warnings. Every ⚠️ you skip becomes a 🔴 during the Integration Gate."* |

**Logical Dependency Check (within Phase 5):**

| Element | Content |
|:--------|:--------|
| **Action** | Review the task sequence in `tasks.md` |
| **Narration** | *"Now that we've verified alignment, let's check construction logic. Can we build these in order? Does Task 3 depend on Task 2's output?"* |

**Live Edit Example:**

```markdown
## Task Dependency Map

1. Task 1: Load transcript.txt → raw string
2. Task 2: Parse raw string → JSON segments  ← depends on Task 1
3. Task 3: Generate LinkedIn post from segments ← depends on Task 2
4. Task 4: Generate X thread from segments ← depends on Task 2 (parallel with Task 3)
```

| Element | Content |
|:--------|:--------|
| **Key Teaching Moment** | *"See how Tasks 3 and 4 both depend on Task 2, but NOT on each other? That means they can be built in parallel. This is how Skill Owners can divide work."* |
| **Connection to PM Role** | *"PMs — this is what you'll audit in Lesson 4.7. You'll run `analyze` on your team's artifacts and check that each Skill Owner's `tasks.md` has a logical sequence that aligns with the `interface-spec.md` you built in Week 1."* |

---

## 🚀 Transition Cue to Lesson 4.5

| Element | Content |
|:--------|:--------|
| **Narration** | *"You've seen me do it. Now it's your turn. In the next 30 minutes, Skill Owners will draft `tasks.md` for YOUR capstone skill using `/speckit.tasks`. PMs — observe, but don't intervene yet. Your audit comes after the scaffolding demo."* |
| **Action** | Display Lesson 4.5 Lab Kit instructions on screen |

---

## 💡 Instructor Quick Reference

### Red Flag Words → Replacements

| Red Flag Words | Replace With |
|:---------------|:-------------|
| "Process" | "Parse," "Transform," "Convert" |
| "Handle" | "Validate," "Route," "Log" |
| "Manage" | "Create," "Update," "Delete" |
| "Deal with" | "Catch," "Retry," "Skip" |

### Atomic Task Checklist

| Criterion | ✓/✗ |
|:----------|:---:|
| Completable in one sitting (30–90 min)? | |
| Has a clear INPUT? | |
| Has a testable OUTPUT? | |
| Uses an action verb? | |
| Black-Box Test Table attached? | |

### `analyze` Output Legend

| Symbol | Meaning | Action |
|:-------|:--------|:-------|
| ✅ | Consistent across artifacts | No action needed |
| ⚠️ | Ambiguity or underspecified | Resolve before Gate 4 |
| ❌ | Contradiction detected | Must fix immediately |
| 🔄 | Duplication found | Consolidate or clarify ownership |

### Spec-Kit Command Summary (Week 4)

| Command | Purpose | When to Use |
|:--------|:--------|:------------|
| `checklist` | Verify `plan.md` aligns with `spec.md` | Pre-Week 4 homework; before decomposition |
| `/speckit.tasks` | Generate `tasks.md` from `plan.md` | Lesson 4.4 demo; Lesson 4.5 hands-on |
| `analyze` | Audit consistency across `spec.md`, `plan.md`, `tasks.md` | After task decomposition; before Gate 4 |

---

## 📊 Success Criteria for Lesson 4.4

| Criterion | Verification |
|:----------|:-------------|
| **Atomic Tasks Demonstrated** | At least 1 vague task refined into atomic form with action verb |
| **Black-Box Test Table Created** | At least 1 task has Input → Expected Output → Edge Case table |
| **`analyze` Command Run** | Output displayed; at least 1 warning addressed live |
| **Dependency Map Shown** | Task sequence visualized with dependency arrows |
| **Transition Set Up** | Students understand they will now do this themselves in 4.5 |

---

*End of Lesson 4.4 Demo Kit*
