# Lesson 3.3 Student Lab Kit: Generate Your Implementation Plan

**Course:** AI-Assisted SDD for Business Analysts  
**Session:** Week 3 — Planning Phase  
**Duration:** 45 minutes  
**Type:** Team-based Hands-on  
**Goal:** Transform your refined `spec.md` and `constitution.md` into a template-aligned `plan.md` using `/speckit.plan`.

---

## Learning Objectives

By the end of this session, you will be able to:

- Execute the "Copy Template → Run Command → Refine Sections" workflow
- Fill in each section of the official `plan-template.md`
- Verify Technical Context against your Constitution
- Mark your Constitution Check as PASS (or fix violations first)
- Make and document a Project Structure decision
- Commit a valid `plan.md` to your repository

---

## Team Roles

| Role | Person | Responsibility |
|------|--------|----------------|
| **Driver (PM)** | __________ | Controls VS Code; runs commands; makes final edits to `plan.md` |
| **Constitution Auditor** | __________ | Cross-references every Technical Context field against `constitution.md` |
| **Structure Architect** | __________ | Focuses on Project Structure decision; ensures dependencies make sense |

*Rotate roles if desired, but PM should drive the commit.*

---

## Pre-Lab Checklist

Before you begin, verify:

| Item | ✅ |
|------|---|
| VS Code open with your project | ☐ |
| `spec.md` (refined in Week 2) accessible | ☐ |
| `constitution.md` (drafted in Week 2) accessible | ☐ |
| Copilot Chat ready | ☐ |
| Terminal accessible for git commands | ☐ |

---

## The Workflow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   COPY TEMPLATE    →    RUN COMMAND    →    REFINE SECTIONS    →    COMMIT │
│                                                                             │
│   plan-template.md      /speckit.plan      Section-by-section      git add │
│   → plan.md             with preferences   verification            commit  │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Phase-by-Phase Instructions

### Phase 1: Copy Template (0:00 – 0:05)

**Action:**

1. Copy the official `plan-template.md` into your feature folder:

```bash
cp .specify/templates/plan-template.md .specify/specs/[your-project]/plan.md
```

2. Open `plan.md` in VS Code alongside `spec.md` and `constitution.md` (3-pane layout recommended)

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| `plan.md` exists in `.specify/specs/[your-project]/` | ☐ |
| `plan.md` contains the raw template structure | ☐ |
| You can see all three files (spec, constitution, plan) | ☐ |

---

### Phase 2: Fill Header & Run `/speckit.plan` (0:05 – 0:12)

**Step 2a: Fill in the Header**

Edit the top of `plan.md`:

```markdown
# Implementation Plan: [YOUR FEATURE NAME]

**Branch**: `[your-branch-name]` | **Date**: [TODAY'S DATE] | **Spec**: [../spec.md]

**Input**: Feature specification from `/specs/[your-project]/spec.md`
```

**Step 2b: Discuss PM Preferences (2 min)**

Before running the command, discuss as a team:

| Question | Your Answer |
|----------|-------------|
| What should be built first (Phase 1 priority)? | |
| What can wait until later phases? | |
| What's the riskiest part to de-risk early? | |

**Step 2c: Run `/speckit.plan`**

In Copilot Chat, run:

```text
/speckit.plan

Context:
- spec.md: [Your feature name] — [one-line description]
- constitution.md: [Key constraints: language, dependencies, storage, security]

My preferences as PM:
- [Priority 1: What should be built first?]
- [Priority 2: What can wait?]
- [Risk: What's the hardest part to de-risk early?]

Goal:
Fill in the plan.md template with:
- Summary (2–3 sentences)
- Technical Context (all fields)
- Constitution Check (list rules and compliance status)
- Project Structure (recommend one option)
```

**Step 2d: Copy Output to `plan.md`**

Copy the AI-generated content into the appropriate sections of your `plan.md`.

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Header is complete (Branch, Date, Spec link) | ☐ |
| PM preferences were discussed before running | ☐ |
| AI output has been copied into `plan.md` | ☐ |

---

### Phase 3: Refine Summary (0:12 – 0:15)

**Template Section:**

```markdown
## Summary

[Extract from feature spec: primary requirement + technical approach from research]
```

**Team Action:**

1. Read the generated Summary aloud
2. Cross-check against `spec.md`:
   - Does it accurately describe what you're building?
   - Does it mention the correct technical approach?
3. Edit if needed

**Quality Check:**

| Criterion | ✅ Good | ❌ Bad |
|-----------|---------|--------|
| Length | 2–3 sentences | A full paragraph or single word |
| Content | Primary requirement + technical approach | Vague ("build a tool") |
| Traceability | Clearly derived from `spec.md` | Introduces new requirements |

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Summary matches what's in `spec.md` | ☐ |
| Summary is 2–3 sentences, not vague | ☐ |

---

### Phase 4: Verify Technical Context (0:15 – 0:25)

**Template Section:**

```markdown
## Technical Context

**Language/Version**: [e.g., Python 3.11]  
**Primary Dependencies**: [e.g., pandas, FFmpeg]  
**Storage**: [e.g., local filesystem]  
**Testing**: [e.g., pytest]  
**Target Platform**: [e.g., CLI / Local]

**Project Type**: [e.g., cli]  
**Performance Goals**: [e.g., process 1-hour transcript in <30 seconds]  
**Constraints**: [e.g., offline-capable, no cloud dependencies]  
**Scale/Scope**: [e.g., single-user CLI tool]
```

**Team Action (Constitution Auditor leads):**

Go field-by-field and cross-check against `constitution.md`:

| Field | AI Output | Constitution Says | Match? |
|-------|-----------|-------------------|--------|
| Language/Version | | | ☐ |
| Primary Dependencies | | | ☐ |
| Storage | | | ☐ |
| Testing | | | ☐ |
| Target Platform | | | ☐ |
| Project Type | | | ☐ |
| Performance Goals | | | ☐ |
| Constraints | | | ☐ |
| Scale/Scope | | | ☐ |

**If a field doesn't match:**

1. The Constitution wins — edit the plan
2. If the field says `NEEDS CLARIFICATION`, make the decision now as a team

**Common Issues to Catch:**

| Red Flag | Example | Fix |
|----------|---------|-----|
| Unauthorized library | AI suggests `requests` but Constitution says "no external APIs" | Delete and note "local processing only" |
| Wrong storage | AI suggests PostgreSQL but Constitution says "local files" | Change to "local filesystem" |
| Missing field | AI left a field as `NEEDS CLARIFICATION` | Discuss and fill in now |

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Every Technical Context field has been reviewed | ☐ |
| All fields match Constitution (or have been fixed) | ☐ |
| No `NEEDS CLARIFICATION` fields remain | ☐ |

---

### Phase 5: Mark Constitution Check (0:25 – 0:30)

**Template Section:**

```markdown
## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

[Gates determined based on constitution file]
```

**Team Action:**

Based on your Technical Context verification, fill in this section:

```markdown
## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

**Status: [PASS / FAIL]**

| Rule | Plan Compliance |
|------|-----------------|
| [Rule 1 from Constitution] | ✅ / ❌ [How plan complies or violates] |
| [Rule 2 from Constitution] | ✅ / ❌ [How plan complies or violates] |
| [Rule 3 from Constitution] | ✅ / ❌ [How plan complies or violates] |
```

**Decision Point:**

| Status | What It Means | Next Step |
|--------|---------------|-----------|
| **PASS** | All Constitution rules respected | Proceed to Phase 6 |
| **FAIL** | One or more violations detected | Go back and fix Technical Context, then re-check |

⚠️ **Do NOT proceed with a FAIL status.** Fix the plan first.

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Constitution Check section is filled in | ☐ |
| Status is marked as PASS | ☐ |
| If FAIL, violations have been fixed and re-checked | ☐ |

---

### Phase 6: Document Project Structure (0:30 – 0:38)

**Template Section (Documentation):**

```markdown
### Documentation (this feature)

specs/[###-feature]/
├── plan.md              # This file
├── research.md          # Phase 0 output
├── data-model.md        # Phase 1 output
├── quickstart.md        # Phase 1 output
├── contracts/           # Phase 1 output
└── tasks.md             # Phase 2 output (/speckit.tasks)
```

**Team Action:**

1. Verify this tree matches your actual folder structure
2. Update the `[###-feature]` placeholder with your actual folder name

---

**Template Section (Source Code):**

```markdown
### Source Code (repository root)

# [REMOVE IF UNUSED] Option 1: Single project (DEFAULT)
src/
├── models/
├── services/
├── cli/
└── lib/

tests/
├── contract/
├── integration/
└── unit/

# [REMOVE IF UNUSED] Option 2: Web application
...

# [REMOVE IF UNUSED] Option 3: Mobile + API
...

**Structure Decision**: [Document your choice and why]
```

**Team Action (Structure Architect leads):**

1. **Choose ONE option** that fits your project
2. **Delete the other options** (leave only the one you're using)
3. **Customize the paths** if needed (e.g., rename folders to match your project)
4. **Fill in the Structure Decision** field:

```markdown
**Structure Decision**: [Which option you chose] because [brief rationale].
```

**Example:**

```markdown
**Structure Decision**: Single-project layout using `src/` + `tests/` as shown above. 
This is a CLI tool with no web or mobile components.
```

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Documentation tree has correct folder name | ☐ |
| Only ONE Source Code option remains (others deleted) | ☐ |
| Structure Decision field is filled in | ☐ |

---

### Phase 7: Review Complexity Tracking (0:38 – 0:40)

**Template Section:**

```markdown
## Complexity Tracking

> **Fill ONLY if Constitution Check has violations that must be justified**

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
```

**Team Action:**

- If your Constitution Check is PASS with no exceptions: **Leave this section empty**
- If you intentionally broke a Constitution rule: Document it here with justification

**Most teams will leave this empty. That's correct.**

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Complexity Tracking is empty (normal) OR has justified exceptions | ☐ |

---

### Phase 8: Final Review & Commit (0:40 – 0:45)

**Pre-Commit Checklist:**

| Section | Checkpoint | ✅ |
|---------|------------|---|
| **Header** | Branch, Date, Spec link filled in | ☐ |
| **Summary** | 2–3 sentences, matches `spec.md` | ☐ |
| **Technical Context** | All fields verified against Constitution | ☐ |
| **Constitution Check** | Status is PASS | ☐ |
| **Project Structure — Docs** | Folder name is correct | ☐ |
| **Project Structure — Code** | Only ONE option remains; Structure Decision filled | ☐ |
| **Complexity Tracking** | Empty or justified | ☐ |

**Commit:**

```bash
git add .specify/specs/[your-project]/plan.md
git commit -m "Week 3: Add implementation plan (template-aligned)"
git push origin main
```

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| All pre-commit checks passed | ☐ |
| `plan.md` committed and pushed | ☐ |

---

## Success Criteria

Your `plan.md` is complete when:

| Criterion | ✅ |
|-----------|---|
| File exists at `.specify/specs/[your-project]/plan.md` | ☐ |
| Header metadata is complete | ☐ |
| Summary is 2–3 sentences, traceable to spec | ☐ |
| Technical Context matches Constitution (no conflicts) | ☐ |
| Constitution Check is marked PASS | ☐ |
| Project Structure has ONE option with Structure Decision | ☐ |
| Complexity Tracking is empty or justified | ☐ |
| File is committed to git | ☐ |

---

## Troubleshooting

| Issue | Quick Fix |
|-------|-----------|
| **AI generates vague Summary** | Your spec is probably vague. Ask: "Rewrite the Summary to specifically state what the tool does and what technology it uses, based on spec.md." |
| **Technical Context has wrong tech stack** | Edit manually. Say: "The Constitution wins. Fix the plan." |
| **Field says `NEEDS CLARIFICATION`** | That's a decision gap. Discuss as a team and fill it in now. |
| **Constitution Check fails** | Do not proceed. Fix the Technical Context first, then re-check. |
| **AI proposes multiple Project Structure options** | Delete all but one. There should be exactly one truth. |
| **Not sure which Structure option to pick** | For this course, use Option 1 (Single project) unless you have a clear reason for web or mobile. |
| **`/speckit.plan` command not found** | Ensure you're in the correct directory and your environment is active. Try `uv run speckit plan` as alternative. |

---

## What's Next?

After this session:

1. **Lesson 3.4–3.5:** Plan Triage + Edge Case Attack — stress-test your plan
2. **Lesson 3.6:** Planning Gate Check — verify `plan.md` is committed and complete
3. **Week 4:** `/speckit.tasks` — decompose your plan into atomic tasks

**Remember:** Today we built the roadmap. Next week we break it into turn-by-turn directions.

---

## Quick Reference: Template Sections

| Section | What Goes Here | Who Verifies |
|---------|----------------|--------------|
| Header | Branch, Date, Spec link | PM |
| Summary | 2–3 sentences from spec | PM |
| Technical Context | Tech stack fields | Constitution Auditor |
| Constitution Check | PASS/FAIL status + rule table | Constitution Auditor |
| Project Structure — Docs | Feature folder tree | Structure Architect |
| Project Structure — Code | ONE layout option + decision | Structure Architect |
| Complexity Tracking | Justified exceptions only | PM |

---

*End of Lesson 3.3 Student Lab Kit*
