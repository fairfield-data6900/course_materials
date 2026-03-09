# 📦 Pre-Week 4 Prep Kit

**Distributed:** End of Week 3  
**Due:** Before Week 4 class  
**Estimated Time:** 45–50 min total

---

## Overview

This prep kit ensures you arrive at Week 4 ready to decompose your `plan.md` into atomic tasks. Complete all four items before class.

| Item | Type | Time Est. |
|:-----|:-----|:----------|
| 1. Agentic Skills Pre-reading | Read | 15 min |
| 2. `checklist` Command Guide | Try | 20 min |
| 3. `/intake` & `/sync` Command Preview | Read | 10 min |
| 4. Midpoint Gate Checklist | Read | 5 min |

---

## Item 1: Agentic Skills Pre-reading (15 min)

**Purpose:** Prepare for Group A's presentation on Agentic Skills in Week 4.

- [Gemini Chat here](https://gemini.google.com/share/19d6af1e6651)
- [Deep Reseaerch Report here](https://gemini.google.com/share/f63cbad67b8c)


---

## Item 2: `checklist` Command Guide (20 min)

**Purpose:** Verify your `plan.md` aligns with your `spec.md` before task decomposition begins.

### What is `checklist`?

The `checklist` command verifies that your `plan.md` aligns with your `spec.md`. It catches drift before you decompose into tasks — because if your plan doesn't match your spec, your tasks will inherit the misalignment.

> **Reference:** [checklist.md](https://github.com/github/spec-kit/blob/main/templates/commands/checklist.md)

### Instructions

1. **Open your project** in VS Code (or your preferred editor)

2. **Run the command:**
   ```
   /speckit.checklist
   ```

3. **Review the output:**

   | Symbol | Meaning | Action |
   |:-------|:--------|:-------|
   | ✅ | Aligned | No action needed |
   | ⚠️ | Potential drift | Review and resolve before Week 4 |
   | ❌ | Misalignment | Must fix before class |

4. **Fix any issues:**
   - If `plan.md` includes features not in `spec.md` → Either add to spec or remove from plan
   - If `spec.md` requirements are missing from `plan.md` → Update plan to address them

5. **Commit your changes:**
   ```bash
   git add spec.md plan.md
   git commit -m "Pre-Week 4: checklist alignment verified"
   ```

### What to Bring to Week 4

- ✅ **Green output:** You're ready for task decomposition
- ⚠️ **Warnings you couldn't resolve:** Bring to Week 4 Stand-up as a discussion item
- ❌ **Errors you couldn't fix:** Bring to Week 4 Stand-up as a blocker

---

## Item 3: `/intake` & `/conclude` Command Preview (10 min)

**Purpose:** Preview the custom slash commands you'll see in Lesson 4.6 (Scaffolding Demo).

### `/intake` - manually turn a spec into plan

```markdown
# ROLE
You are a coding assistant who helps users by generating or completing code snippets based on provided specifications. 

# AUDIENCE
The audience is developers who need to implement features according to detailed specifications. You should always treat the specifications as authoritative.

# FORMAT
When completing code snippets, ensure that the code is syntactically correct and follows best practices. Do not include any explanations or commentary outside of the code itself.

# TASK
You goal is to create an incremental, risk-free implementation plan for the feature specified in the provided spec documents. The plan should break down the implementation into clear, manageable tasks with defined responsibilities and acceptance criteria. You will not make assumptions beyond what is stated in the specs. And you will follow the tasks below exactly.
1. Review the provided specification documents carefully, for the purpose of understanding the context and requirements.
2. Investigate any dependencies or related components in the codebase that may impact the implementation.
3. Ask follow up questions if any part of the specification is unclear or requires further detail before proceeding, ONE QUESTION AT A TIME. Make logical assumptions when necesary to provide options for the users to choose from.
4. Once all necessary clarifications are made, create a detailed implementation plan that breaks down the feature into incremental tasks, each with clear responsibilities and acceptance criteria. The plan should include:
   - An overview of the feature and its objectives.
   - A high-level architecture diagram if applicable.
   - A step-by-step breakdown of tasks required to implement the feature.
   - A test plan with specific acceptance criteria for each task.
5. Present the implementation plan clearly and concisely, ensuring it is easy to follow for developers. Wait for user confirmation before proceeding with implementation.
6. If possible - use the `todos` tool to create a list of actionable todos based on the implementation plan.
```

**When to use:** At the start of a coding session to load your `tasks.md` into AI context.

### `/handoff` - use when context window is close to full

```markdown
# ROLE
You are a coding assistant who helps users by generating or completing code snippets based on provided specifications. 

# AUDIENCE
The audience is developers who need to implement features according to detailed specifications. You should always treat the specifications as authoritative.

# FORMAT
The handoff prompt should be in markdown format, with well-structured sections, and concise without any extraneous explanations.

# TASK
You goal is to create a hand-off prompt for the next agent to continue working on the feature according to an implementation plan previously created, or a new feature that specified in a different spec document. The hand-off prompt should include:
1. A brief summary of the feature and its objectives.
2. Current progress made towards the implementation, including completed tasks and any outstanding tasks. If there is no outstanding tasks, state that the implementation is complete.
3. Pointers to relevant code objects, files and memories that will help the next agent understand the context.
4. You should first instruct the next agent to use above imformation to prime its context window properly.
5. Once the context is primed, instruct the next agent to state "I am ready". If there is any ambiguity in the information provided, the next agent should ask clarifying questions one at a time before proceeding.
```

**When to use:** To synchronize state between artifacts after making changes.

---

## Item 4: Midpoint Gate Checklist (5 min)

**Purpose:** Know what's due by the end of Week 4 (Gate 4).

### Gate 4 Criteria

| Criterion | Owner | Status |
|:----------|:------|:------:|
| Skill-level `tasks.md` committed (3+ tasks per skill) | Skill Owners | ☐ |
| 50%+ tasks have Black-Box Test Tables | Skill Owners | ☐ |
| PM Integration Audit completed | PM | ☐ |

### What This Means for Each Role

**Skill Owners (Skill A & Skill B):**
- You will draft `tasks.md` for your skill in Lesson 4.5
- Each task must be atomic (30–90 min, clear input/output, action verb)
- At least half your tasks need Black-Box Test Tables (Input → Expected Output → Edge Cases)

**PM / Integrator (Skill C):**
- You will run the Integration Audit in Lesson 4.7
- You'll use `analyze` to check consistency across all three artifacts
- You'll verify task dependencies align with the `interface-spec.md`

### Self-Check Before Week 4

| Question | Yes/No |
|:---------|:------:|
| Have I run `checklist` and resolved all issues? | ☐ |
| Do I understand what an "atomic task" is? | ☐ |
| Do I know my role for Week 4 (Skill Owner vs. PM)? | ☐ |
| Have I reviewed the Agentic Skills reading? | ☐ |

---

## Questions?

Bring any unresolved issues to the **Week 4 Stand-up (Lesson 4.1)** — that's the time to surface blockers before we dive into task decomposition.

---

*End of Pre-Week 4 Prep Kit*
