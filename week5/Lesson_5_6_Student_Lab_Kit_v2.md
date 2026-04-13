# Lesson 5.6 Student Lab Kit v3: Build Skills + Decision Summary

**Course:** AI-Assisted SDD for Business Analysts  
**Session:** Week 5 — Agentic Skills & Observability  
**Duration:** 77 minutes (72-minute lab + 5-minute Gate Check)  
**Type:** Team-based Hands-on  
**Goal:** Build your agent skills, audit them with `/scout` and `/trace`, then produce a demo-ready `decision-summary.md` using the 3-Prompt Observability Pipeline.

---

## Learning Objectives

By the end of this session, you will be able to:

- Find reference skills and scaffold your own using `/create-skill`
- Complete your skill with `/scripts` and `/assets` via chat-based follow-up prompts
- Map your skill's structure with `/scout` and investigate its decisions with `/trace`
- Run the 3-Prompt Observability Pipeline to produce a `decision-summary.md`
- Commit a complete, auditable, explainable skill to your repository

---

## Tooling Clarification

| Tool | Used For | How |
|------|----------|-----|
| **VS Code + GitHub Copilot** | Scaffolding, coding, `/scout`, `/trace` | Direct in editor |
| **Claude Desktop / Claude.ai** | Running the 3-Prompt Pipeline (Prompts 1, 2, 3) | Copy-paste workflow in browser or app |
| **Excel / Google Sheets** | Any data formatting or tabular work | Copy-paste — **not** "Claude for Excel" |
| **Git / Terminal** | Version control, commits | Command line in VS Code |

> **Note:** The 3-Prompt Pipeline runs in an **external AI** (Claude Desktop, Claude.ai, or ChatGPT) — not inside Copilot Chat. This gives you fresh context and avoids polluting your coding session.

---

## Team Roles

| Role | Person | Responsibility |
|------|--------|----------------|
| **PM** | __________ | Integration Test Plan; run `/scout` + `/trace` on combined project; review Decision Summaries for demo-readiness |
| **Skill Owner A** | __________ | Build Skill A; run 3-Prompt Pipeline on Skill A; produce `decision-summary.md` |
| **Skill Owner B** | __________ | Build Skill B; run 3-Prompt Pipeline on Skill B; produce `decision-summary.md` |

---

## Pre-Lab Checklist

| Item | ✅ |
|------|---|
| VS Code open with your capstone project | ☐ |
| `spec.md`, `constitution.md`, `plan.md`, `tasks.md` accessible | ☐ |
| `interface-spec.md` (PM-owned) accessible | ☐ |
| Copilot Chat ready in VS Code | ☐ |
| External AI open in browser (Claude.ai or ChatGPT) | ☐ |
| 3-Prompt Pipeline files downloaded and accessible | ☐ |
| Terminal ready for git commands | ☐ |

---

## The Workflow at a Glance

```
┌──────────────────────────────────────────────────────────────────────────────────────┐
│                                                                                      │
│  SEARCH → SCAFFOLD → COMPLETE → AUDIT → OBSERVE → FIX & COMMIT → GATE CHECK        │
│                                                                                      │
│  /skill-finder  /create-skill  Chat prompts  /scout   3-Prompt    git add/commit     │
│                                for /scripts  /trace   Pipeline    push               │
│                                and /assets            → decision-summary.md           │
│                                                                                      │
└──────────────────────────────────────────────────────────────────────────────────────┘
```

---

## Phase-by-Phase Instructions

---

### Phase 1: Search (0:00 – 0:10)

**Goal:** Find existing skills that match your requirements to use as reference patterns.

#### Skill Owners

1. Open Copilot Chat in VS Code
2. Run `/skill-finder` with your requirement:

```
/skill-finder Find skills that can parse audio transcripts and extract timestamps
```

3. Review the matches returned
4. Open 1–2 reference skills and note:
   - Folder structure
   - How `SKILL.md` is organized
   - Script patterns in `/scripts`

**Output:** List of 1–2 reference skills to use as patterns

#### PM (Parallel)

1. Run `/skill-finder` for Skill A's requirement
2. Run `/skill-finder` for Skill B's requirement
3. Share relevant matches with Skill Owners
4. Note any skills that handle integration between components

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Skill Owner A has 1–2 reference skills identified | ☐ |
| Skill Owner B has 1–2 reference skills identified | ☐ |
| PM has shared relevant matches | ☐ |

---

### Phase 2: Scaffold (0:10 – 0:25)

**Goal:** Generate your skill's initial structure using `/create-skill`.

#### Skill Owners

1. Run `/create-skill`:

```
/create-skill Create a skill based on my tasks.md located at [path/to/tasks.md]
```

2. Review the generated `SKILL.md` in your `.skills/[skill-name]/` folder
3. Verify it aligns with your `spec.md` and `constitution.md`

**Output:** `SKILL.md` generated in `.skills/[skill-name]/`

#### PM (Parallel)

**Goal:** Draft the Integration Test Plan while Skill Owners scaffold.

**Integration Test Plan Template:**

```markdown
## Integration Test Plan

### Skill A → Skill B Interface
| Test | Input | Expected Output | Status |
|------|-------|-----------------|--------|
| [Test 1] | [What Skill A produces] | [What Skill B expects] | ☐ |
| [Test 2] | [Edge case input] | [Expected handling] | ☐ |

### End-to-End Flow
| Step | Component | Input | Output | Status |
|------|-----------|-------|--------|--------|
| 1 | Skill A | [raw input] | [intermediate] | ☐ |
| 2 | Skill B | [intermediate] | [final output] | ☐ |
```

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Skill Owner A has `SKILL.md` generated | ☐ |
| Skill Owner B has `SKILL.md` generated | ☐ |
| PM has Integration Test Plan drafted | ☐ |

---

### Phase 3: Complete (0:25 – 0:45)

**Goal:** Create `/scripts` and `/assets` folders with necessary files using chat-based follow-up prompts.

> **Important:** Do NOT use `/speckit.implement`. Use the follow-up prompts below in Copilot Chat after `/create-skill` has generated your `SKILL.md`.

#### Skill Owners

**Prompt 1: Create /scripts**

```
Based on the skill.md you just created, now create the /scripts folder 
with the necessary Python files. Use the task breakdown from my tasks.md 
and follow the patterns from [reference skill name from Phase 1].
```

**Prompt 2: Create /assets**

```
Now create the /assets folder for this skill. Include any templates, 
sample inputs, or configuration files needed based on my tasks.md.
```

**Prompt 3: Verify Completeness**

```
Review the skill folder structure you've created. Compare it against 
my tasks.md and confirm:
1. All tasks have corresponding scripts
2. Input/output formats match my interface-spec.md
3. Any missing files or folders
```

**After each prompt:** Use the Verification Ritual — **Read → Run → Test → Commit**

#### PM (Parallel)

Continue refining the Integration Test Plan. Begin testing interfaces if Skill Owners have committed early outputs.

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Skill A has `/scripts` folder with Python files | ☐ |
| Skill A has `/assets` folder | ☐ |
| Skill B has `/scripts` folder with Python files | ☐ |
| Skill B has `/assets` folder | ☐ |
| Completeness check passed for both skills | ☐ |

---

### Phase 4: Audit — `/scout` + `/trace` (0:45 – 0:55)

**Goal:** Map your skill's structure and investigate its decision logic.

#### Skill Owners

**Step 1: Run `/scout`**

```
/scout
```

Target your skill folder. Review the generated `ARCHITECTURE.md`:
- File index — are all files accounted for?
- Mermaid diagram — does the data flow make sense?
- Decision surface — where does your skill make choices?

**Step 2: Run `/trace`**

Run your skill on a sample input first (so output exists), then:

```
/trace
```

Provide context:
- The `ARCHITECTURE.md` (just generated)
- Your skill's actual output
- Your `spec.md`

Review the trace output for:
- **Decision Path** — does the chain from spec → implementation → output make sense?
- **Assumption Challenges** — what is your skill assuming that it never stated?
- **Landmine List** — what could break silently?

| Priority | Meaning | Action |
|----------|---------|--------|
| 🔴 Red | It breaks | Must fix before demo |
| 🟡 Yellow | Degrades silently | Should fix or document |
| 🔵 Blue | Cosmetic | Document as known limitation |

#### PM (Parallel)

Run `/scout` and `/trace` on the **combined project** (not individual skills):
- Does the architecture show both skills connecting?
- Does the trace reveal integration assumptions?
- Are there landmines at the interface boundary?

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Skill A: `ARCHITECTURE.md` generated via `/scout` | ☐ |
| Skill A: `/trace` output reviewed; landmines noted | ☐ |
| Skill B: `ARCHITECTURE.md` generated via `/scout` | ☐ |
| Skill B: `/trace` output reviewed; landmines noted | ☐ |
| PM: Project-level `/scout` + `/trace` completed | ☐ |

---

### Phase 5: Observe — 3-Prompt Observability Pipeline (0:55 – 1:05)

**Goal:** Produce a `decision-summary.md` for each skill — a human-readable document that explains WHY your skill made its decisions.

> **This phase runs in an external AI (Claude Desktop / Claude.ai / ChatGPT) — not in Copilot Chat.**

#### The Pipeline

```
Skill Output (results only)
        │
        ▼
  ┌───────────┐
  │  Prompt 1  │  Socratic Reasoning Auditor
  │   AUDIT    │  "What reasoning is missing?"
  └─────┬──────┘
        │ Critical Reasoning Gaps
        ▼
  ┌───────────┐
  │  Prompt 2  │  Coding Agent Instruction Template
  │ IMPLEMENT  │  "Tell your agent to add the reasoning"
  └─────┬──────┘
        │ Updated skill with reasoning
        ▼
  ┌───────────┐
  │  Prompt 3  │  Decision Summary Distiller
  │  DISTILL   │  "Polish it for demo day"
  └─────┬──────┘
        │
        ▼
  decision-summary.md (demo-ready artifact)
```

#### Skill Owners: Step-by-Step

**Step 1: Run Prompt 1 — Socratic Reasoning Auditor (3 min)**

1. Open your external AI (Claude.ai, ChatGPT, etc.)
2. Paste the **Socratic Reasoning Auditor** prompt
3. Replace `[PASTE YOUR SKILL OUTPUT HERE]` with your skill's actual output
4. Replace `[BRIEF DESCRIPTION]` with what your skill does
5. Review the **Critical Reasoning Gaps** returned (3–6 gaps)

**Ask yourself for each gap:**
- Do I agree this is missing?
- Would this come up at demo day?

**Step 2: Run Prompt 2 — Coding Agent Instruction Template (4 min)**

1. In the same external AI session (or a new one), paste the **Coding Agent Instruction Template** prompt
2. Fill in:
   - Your skill name and description
   - Your skill's file tree
   - Key Constitution constraints
   - Relevant spec requirements
   - The Critical Reasoning Gaps from Step 1
3. Review the generated **Instruction Blocks**
4. Copy each Instruction Block into **Copilot Chat** (back in VS Code)
5. Let the coding agent update your skill
6. Re-run your skill to verify reasoning now appears in the output

**Step 3: Run Prompt 3 — Decision Summary Distiller (3 min)**

1. Back in external AI, paste the **Decision Summary Distiller** prompt
2. Paste your skill's **updated output** (now with reasoning)
3. Review the generated **Decision Summary**
4. Check for ⚠️ flags — these indicate gaps that still exist
5. Save as `decision-summary.md` in your skill folder:

```
.skills/your-skill/
├── SKILL.md
├── prompts/
├── code/
├── recipes/
├── scripts/
├── assets/
└── decision-summary.md    ← NEW
```

#### PM (Parallel)

While Skill Owners run the pipeline:
- Review any early Decision Summary drafts for clarity
- Ask: "Could a non-technical person understand this?"
- Flag any sections that use jargon or reference code

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Skill A: Prompt 1 completed — gaps identified | ☐ |
| Skill A: Prompt 2 completed — reasoning added to skill | ☐ |
| Skill A: Prompt 3 completed — `decision-summary.md` produced | ☐ |
| Skill B: Prompt 1 completed — gaps identified | ☐ |
| Skill B: Prompt 2 completed — reasoning added to skill | ☐ |
| Skill B: Prompt 3 completed — `decision-summary.md` produced | ☐ |

---

### Phase 6: Fix & Commit (1:05 – 1:12)

**Goal:** Address critical issues and commit everything.

#### Skill Owners

1. Fix any 🔴 Red landmines from `/trace` (Phase 4)
2. Address any ⚠️ flags from the Decision Summary (Phase 5)
3. Commit your complete skill folder:

```bash
git add .skills/[skill-name]/
git commit -m "Add [skill-name] skill with scripts, assets, and decision summary"
git push
```

#### PM

1. Document any integration blockers in `DEBT.md`:

```markdown
## DEBT.md

### Integration Blockers (Week 5)
| ID | Blocker | Owner | Status |
|:---|:--------|:------|:------:|
| D1 | [Description] | [Skill A/B/PM] | ☐ |
```

2. Verify both Skill Owners have committed
3. **Review both `decision-summary.md` files for demo-readiness:**

| Check | Skill A | Skill B |
|-------|---------|---------|
| Written in plain language (no jargon) | ☐ | ☐ |
| Explains WHY decisions were made | ☐ | ☐ |
| Includes what was rejected and why | ☐ | ☐ |
| Confidence levels are honest | ☐ | ☐ |
| Hallucination Check section is credible | ☐ | ☐ |
| One-Sentence Summary is clear and speakable | ☐ | ☐ |

4. Prepare Gate 5 status report

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Skill A committed with `decision-summary.md` | ☐ |
| Skill B committed with `decision-summary.md` | ☐ |
| PM reviewed both Decision Summaries | ☐ |
| `DEBT.md` updated (if blockers exist) | ☐ |

---

### Phase 7: Gate 5 Check — Skill Gate (1:12 – 1:17)

**PM delivers status report (< 60 seconds):**

> "Team [NAME] is Gate 5 ready.
>
> - Skill A: committed with `decision-summary.md` — [PASS/ISSUE]
> - Skill B: committed with `decision-summary.md` — [PASS/ISSUE]
> - Integration: [status] — blockers documented in `DEBT.md`
> - Decision Summaries: reviewed for demo-readiness — [PASS/NEEDS WORK]
>
> 🔴 Blockers: [None / Describe]"

#### Gate 5 Criteria

| # | Criterion | Owner | ✅ |
|---|-----------|-------|---|
| 1 | Skill A folder committed (`.skills/[name]/`) | Skill Owner A | ☐ |
| 2 | Skill A has `SKILL.md`, `/scripts`, `/assets` | Skill Owner A | ☐ |
| 3 | Skill A has `ARCHITECTURE.md` (from `/scout`) | Skill Owner A | ☐ |
| 4 | Skill A has `decision-summary.md` | Skill Owner A | ☐ |
| 5 | Skill B folder committed (`.skills/[name]/`) | Skill Owner B | ☐ |
| 6 | Skill B has `SKILL.md`, `/scripts`, `/assets` | Skill Owner B | ☐ |
| 7 | Skill B has `ARCHITECTURE.md` (from `/scout`) | Skill Owner B | ☐ |
| 8 | Skill B has `decision-summary.md` | Skill Owner B | ☐ |
| 9 | PM has reviewed both Decision Summaries for clarity | PM | ☐ |
| 10 | Integration blockers documented in `DEBT.md` | PM | ☐ |
| 11 | PM integration in progress | PM | ☐ |

---

## If You Don't Pass

| Issue | Resolution |
|-------|------------|
| Missing `SKILL.md` | Complete before Week 6 using `/create-skill` |
| Missing `/scripts` or `/assets` | Use follow-up prompts from Phase 3 |
| No `ARCHITECTURE.md` | Run `/scout` and commit output |
| No `decision-summary.md` | Run the 3-Prompt Pipeline (Phase 5) — start with Prompt 1 |
| Decision Summary has ⚠️ flags | Go back to Prompt 1 → 2 for those specific gaps |
| PM hasn't reviewed summaries | PM reviews before Week 6; send back if not demo-ready |
| Integration blockers unresolved | Document in `DEBT.md`; address in Week 6 lab |

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| `/create-skill` doesn't generate `/scripts` | Use follow-up prompts in Phase 3 — this is expected behavior |
| `/skill-finder` returns no matches | Broaden your search query; try different keywords |
| `/trace` doesn't find decision points | Your skill may be too simple. Ask: "Where does my skill make a choice?" |
| Prompt 1 finds zero gaps | Either your skill already has reasoning (rare) or the output is too minimal. Check: does your skill produce more than one line of output? |
| Prompt 2 instruction blocks confuse the coding agent | Check file paths. Re-run with more specific context. Include Constitution. |
| Decision Summary has generic reasoning | Go back to Prompt 2. Re-instruct: "The reasoning must reference specific input data, not generic descriptions." |
| Skill A output doesn't match Skill B input | PM documents in `DEBT.md`; fix in Week 6 |
| Agent stops mid-generation | Say "Continue" or re-prompt with specific request |
| External AI session times out | Start a new session; paste the prompt again with your latest output |

---

## Appendix: Suggested Follow-up Prompts

### If `/create-skill` only generates `SKILL.md`:

```
Based on the skill.md you just created, now create the /scripts folder 
with the necessary Python files. Use the task breakdown from my tasks.md 
and follow the patterns from [reference skill name].
```

### If a specific script is missing:

```
You created [file1.py] but my tasks.md also requires [task X]. 
Please create the script for that task.
```

### If `/assets` is missing:

```
Now create the /assets folder for this skill. Include any templates, 
sample inputs, or configuration files needed based on my tasks.md.
```

### If you need to verify completeness:

```
Review the skill folder structure you've created. Compare it against 
my tasks.md and confirm:
1. All tasks have corresponding scripts
2. Input/output formats match my interface-spec.md
3. Any missing files or folders
```

### If the agent made an error:

```
The [file/function] you created doesn't match my spec.md. According 
to my spec, it should [correct behavior]. Please fix it.
```

---

## Quick Reference: Phase Timing

| Phase | Time | Duration | Skill Owners | PM |
|-------|------|----------|--------------|-----|
| 1. Search | 0:00–0:10 | 10 min | Run `/skill-finder` | Run `/skill-finder` for both skills |
| 2. Scaffold | 0:10–0:25 | 15 min | Run `/create-skill` | Draft Integration Test Plan |
| 3. Complete | 0:25–0:45 | 20 min | Chat prompts for `/scripts` + `/assets` | Continue Integration Test Plan |
| 4. Audit | 0:45–0:55 | 10 min | Run `/scout` → `/trace` on own skill | Run `/scout` → `/trace` on combined project |
| 5. Observe | 0:55–1:05 | 10 min | Run 3-Prompt Pipeline → `decision-summary.md` | Review Decision Summaries |
| 6. Fix & Commit | 1:05–1:12 | 7 min | Address issues; commit | Document blockers; verify commits |
| 7. Gate Check | 1:12–1:17 | 5 min | Team verifies Gate 5 criteria | PM presents team status |

---

*End of Lesson 5.6 Student Lab Kit v3*
*Key change from v2: `/review` → `/trace` + 3-Prompt Observability Pipeline + `decision-summary.md`*
