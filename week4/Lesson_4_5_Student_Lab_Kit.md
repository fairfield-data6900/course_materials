# 📘 Lesson 4.5 Student Lab Kit: Task Drafting

**Duration:** 30 min  
**Format:** Hands-on  
**Prerequisite:** Completed `checklist` pre-work; watched Lesson 4.4 demo  
**Goal:** Draft `tasks.md` for your capstone skill using `/speckit.tasks`, refine into atomic tasks with Black-Box Test Tables, and verify alignment with `analyze`.

---

## 👥 Role Assignments

| Role | Activity This Lesson | Next Lesson (4.7) |
|:-----|:---------------------|:------------------|
| **Skill Owner A** | Draft `tasks.md` for Skill A | Receive PM audit feedback |
| **Skill Owner B** | Draft `tasks.md` for Skill B | Receive PM audit feedback |
| **PM / Integrator** | Observe; take notes on cross-skill dependencies | Run Integration Audit |

> **PMs:** Your job this lesson is to watch, not intervene. Note any concerns about how Skill A and Skill B outputs will connect — you'll address these in Lesson 4.7.

---

## ⏱ Timeline (30 min)

| Phase | Time | Activity |
|:------|:-----|:---------|
| 1 | 0:00–0:05 | Generate initial `tasks.md` with `/speckit.tasks` |
| 2 | 0:05–0:12 | Atomic Refinement — eliminate vague verbs |
| 3 | 0:12–0:22 | Add Black-Box Test Tables (3–5 per task) |
| 4 | 0:22–0:28 | Run `analyze` and resolve warnings |
| 5 | 0:28–0:30 | Commit and confirm ready for PM audit |

---

## 📋 Phase-by-Phase Instructions

### Phase 1: Generate Initial `tasks.md` (0:00–0:05)

**Action:** Run `/speckit.tasks` in your project terminal.

**What happens:**
- The AI reads your `plan.md` and generates an initial task breakdown
- Expect 4–6 tasks for a typical skill

**Checkpoint:**
- [ ] `tasks.md` file created
- [ ] Contains at least 3 tasks

**⚠️ Pitfall:** If the AI asks clarifying questions, keep answers short. Long answers invite scope creep.

---

### Phase 2: Atomic Refinement (0:05–0:12)

**Action:** Review each task. Identify and fix vague verbs.

**Red Flag Words → Replacements:**

| ❌ Vague | ✅ Atomic |
|:---------|:----------|
| "Process" | "Parse," "Transform," "Convert" |
| "Handle" | "Validate," "Route," "Log" |
| "Manage" | "Create," "Update," "Delete" |
| "Deal with" | "Catch," "Retry," "Skip" |

**Atomic Task Checklist (apply to each task):**

| Criterion | ✓/✗ |
|:----------|:---:|
| Completable in one sitting (30–90 min)? | |
| Has a clear INPUT? | |
| Has a testable OUTPUT? | |
| Uses an action verb? | |

**Example Refinement:**

| Before | After |
|:-------|:------|
| `Task 2: Process the data` | `Task 2: Parse input CSV and extract rows with missing values as JSON array` |

**Checkpoint:**
- [ ] All tasks use action verbs
- [ ] Each task has clear input and output

---

### Phase 3: Add Black-Box Test Tables (0:12–0:22)

**Action:** For each task, define the contract: What goes IN? What comes OUT?

**Template:**

```markdown
### Task [N]: [Task Name]

**Black-Box Test Table:**

| Input | Expected Output | Edge Case? |
|:------|:----------------|:-----------|
| [Normal input] | [Expected result] | No |
| [Boundary input] | [Expected result] | Yes |
| [Empty input] | [Expected result] | Yes |
| [Malformed input] | [Error handling] | Yes |
```

**Coverage Guide:**
- **Happy path:** Normal, expected input
- **Empty input:** What happens when there's nothing?
- **Malformed input:** What happens when the format is wrong?
- **Boundary cases:** Edge values (max length, special characters, etc.)

**Checkpoint:**
- [ ] At least 50% of tasks have Black-Box Test Tables
- [ ] Each table has 3–5 test cases
- [ ] Edge cases are explicitly marked

**⚠️ Pitfall:** Don't write 20 test cases. 3–5 per task is enough.

---

### Phase 4: Run `analyze` and Resolve Warnings (0:22–0:28)

**Action:** Run `/analyze` to check consistency across `spec.md`, `plan.md`, and `tasks.md`.

**What `analyze` checks:**
- Inconsistencies between artifacts
- Duplications
- Ambiguities
- Underspecified items

**Output Legend:**

| Symbol | Meaning | Action |
|:-------|:--------|:-------|
| ✅ | Consistent | No action needed |
| ⚠️ | Ambiguity or underspecified | Resolve before Gate 4 |
| ❌ | Contradiction | Must fix immediately |
| 🔄 | Duplication | Consolidate or clarify ownership |

**Resolution Options:**

| Issue Type | Resolution |
|:-----------|:-----------|
| Task references requirement not in `spec.md` | Add to spec OR remove from task |
| `spec.md` requirement missing from tasks | Add new task OR clarify out-of-scope |
| Ambiguous output format | Define explicitly in task description |

**Checkpoint:**
- [ ] `analyze` run completed
- [ ] All ❌ errors resolved
- [ ] ⚠️ warnings addressed or documented for PM review

---

### Phase 5: Commit and Confirm (0:28–0:30)

**Action:** Commit your work and confirm readiness for PM audit.

```bash
git add tasks.md
git commit -m "Week 4: tasks.md drafted with Black-Box Test Tables"
```

**Final Checkpoint:**
- [ ] `tasks.md` committed to repo
- [ ] 3+ tasks defined
- [ ] 50%+ tasks have Black-Box Test Tables
- [ ] `analyze` output clean (or warnings documented)

---

## ✅ Success Criteria (Gate 4 Ready)

| Criterion | Owner | Status |
|:----------|:------|:------:|
| Skill-level `tasks.md` committed (3+ tasks per skill) | Skill Owners | ☐ |
| 50%+ tasks have Black-Box Test Tables | Skill Owners | ☐ |
| `analyze` run with no unresolved ❌ errors | Skill Owners | ☐ |

---

## 🔧 Troubleshooting

| Problem | Solution |
|:--------|:---------|
| `/speckit.tasks` generates too few tasks | Check if `plan.md` has enough detail; add specificity to Demo Scope section |
| `/speckit.tasks` generates too many tasks | Tasks may be over-atomized; consolidate 5-minute tasks into 30–90 min chunks |
| `analyze` shows contradictions | Review the flagged items; decide whether to update `spec.md` or `tasks.md` |
| Unsure if task is atomic enough | Apply the "one sitting" test: Can you complete it in 30–90 min without context-switching? |
| PM has concerns during observation | PM notes them silently; address in Lesson 4.7 Integration Audit |

---

## 📎 Appendix: Companion Prompts

### How to Use These Prompts

These are **exact copy-paste prompts** for each phase. Use them when you need AI assistance refining your work.

---

### Prompt 1: Atomic Refinement

```
Review my tasks.md and identify any tasks with vague verbs like "process," "handle," "manage," or "deal with."

For each vague task:
1. Flag the vague verb
2. Suggest 2-3 atomic alternatives with clear inputs and outputs
3. Recommend the best option and explain why

Here is my tasks.md:
[paste your tasks.md content]
```

---

### Prompt 2: Black-Box Test Table Generator

```
For the following task, generate a Black-Box Test Table with 4-5 test cases.

Include:
- 1 happy path (normal input)
- 1 empty input case
- 1 malformed input case
- 1-2 boundary/edge cases

Task: [paste your task description]

Expected input format: [describe expected input]
Expected output format: [describe expected output]
```

---

### Prompt 3: Edge Case Discovery

```
I'm building a Black-Box Test Table for this task. Help me discover edge cases I might have missed.

Task: [paste your task description]

Ask me 3-5 questions about:
- What happens at the boundaries?
- What inputs could break this?
- What assumptions am I making about the input format?

Then suggest edge cases based on my answers.
```

---

### Prompt 4: `analyze` Warning Resolution

```
The `analyze` command flagged this warning:

[paste the warning]

My current artifacts:
- spec.md says: [paste relevant section]
- plan.md says: [paste relevant section]
- tasks.md says: [paste relevant section]

Help me decide:
1. Should I update spec.md to include this requirement?
2. Should I remove it from tasks.md as out-of-scope?
3. Is there a third option I'm missing?

Explain the trade-offs of each approach.
```

---

### Meta-Prompt: Task Architect Catalyst

> Use this meta-prompt to generate custom companion prompts for your specific project context.

```
You are my Task Architect Catalyst. Your job is NOT to write my tasks for me, but to help me think critically about my task decomposition.

My project: [brief description]
My skill: [Skill A or Skill B]
My current tasks.md: [paste content]

Guide me through these challenges:

1. **Atomicity Check:** Ask me questions that reveal whether each task is truly atomic (30-90 min, single responsibility, testable output).

2. **Dependency Discovery:** Help me identify hidden dependencies between tasks that I might have missed.

3. **Edge Case Excavation:** For each task, ask probing questions that surface edge cases I should add to my Black-Box Test Tables.

4. **Alignment Audit:** Before I run `analyze`, help me spot potential drift between my tasks and my spec.md.

Ask me ONE question at a time. Wait for my response before asking the next question.
```

---

*End of Lesson 4.5 Student Lab Kit*
