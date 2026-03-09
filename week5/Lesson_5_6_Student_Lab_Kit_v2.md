# 🛠️ Lesson 5.6 Student Lab Kit: Deep Work — Build & Audit

**Duration:** 77 min (72 min lab + 5 min gate check)  
**Format:** Hands-on Lab  
**Goal:** Skill Owners build skills using `/skill-finder` → `/create-skill` → Chat follow-up; PM prepares integration test plan then audits with `/scout` → `/review`

---

## Overview

| Phase | Time | Skill Owners | PM |
|:------|:-----|:-------------|:---|
| **1. Search** | 0:00–0:10 | Run `/skill-finder` to find reference skills | Run `/skill-finder` for both skills |
| **2. Scaffold** | 0:10–0:25 | Run `/create-skill` with `tasks.md` | Draft Integration Test Plan |
| **3. Complete** | 0:25–0:50 | Follow up in chat to create `/scripts` and `/assets` | Continue Integration Test Plan |
| **4. Audit** | 0:50–0:65 | Run `/scout` → `/review` on own skill | Run `/scout` → `/review` on combined project |
| **5. Fix & Commit** | 0:65–0:72 | Address flagged issues; commit | Document blockers in `DEBT.md` |
| **6. Gate Check** | 0:72–0:77 | Team verifies Gate 5 criteria | PM presents team status |

---

## Role Assignments

| Role | Primary Focus | Deliverables |
|:-----|:--------------|:-------------|
| **Skill Owner A** | Build Skill A | `skill.md`, `/scripts`, `/assets`, passing `/review` |
| **Skill Owner B** | Build Skill B | `skill.md`, `/scripts`, `/assets`, passing `/review` |
| **PM / Integrator** | Integration planning + audit | Integration Test Plan, `/review` on combined project |

---

## Phase 1: Search (10 min)

### Skill Owners

**Goal:** Find existing skills that match your requirements to use as reference patterns.

**Steps:**

1. Open Copilot Chat in VS Code
2. Run `/skill-finder` with your requirement:

```
/skill-finder Find skills that can parse audio transcripts and extract timestamps
```

3. Review the matches returned
4. Open 1–2 reference skills and note:
   - Folder structure
   - How `skill.md` is organized
   - Script patterns in `/scripts`

**Output:** List of 1–2 reference skills to use as patterns

---

### PM

**Goal:** Search for reference skills for BOTH team skills.

**Steps:**

1. Run `/skill-finder` for Skill A's requirement
2. Run `/skill-finder` for Skill B's requirement
3. Share relevant matches with Skill Owners
4. Note any skills that handle **integration** between components

---

## Phase 2: Scaffold (15 min)

### Skill Owners

**Goal:** Generate `skill.md` from your `tasks.md`.

**Steps:**

1. Ensure your `tasks.md` is complete and committed
2. Run `/create-skill` in Copilot Chat:

```
/create-skill Create a skill based on my tasks.md located at [path/to/tasks.md]
```

3. Review the generated `skill.md`
4. Verify it includes:
   - [ ] Skill name and description
   - [ ] Input/output definitions
   - [ ] Invocation instructions

**Output:** `skill.md` generated in your `.skills/[skill-name]/` folder

---

### PM

**Goal:** Draft the Integration Test Plan while Skill Owners scaffold.

**Integration Test Plan Template:**

```markdown
## Integration Test Plan

### Happy Path Definition
- **Input:** [What triggers the pipeline?]
- **Skill A Output → Skill B Input:** [What data passes between skills?]
- **Final Output:** [What does success look like?]

### Test Cases

| ID | Scenario | Input | Expected Output | Status |
|:---|:---------|:------|:----------------|:------:|
| T1 | Happy Path | [sample input] | [expected result] | ☐ |
| T2 | Edge Case: Empty input | [empty] | [graceful error] | ☐ |
| T3 | Edge Case: Malformed input | [bad data] | [validation error] | ☐ |

### Integration Points
| From | To | Data Format | Validation |
|:-----|:---|:------------|:-----------|
| Skill A | Skill B | [JSON/CSV/etc.] | [Schema check?] |

### Blockers
- [ ] [Any known blockers]
```

---

## Phase 3: Complete (25 min)

### Skill Owners

**Goal:** Create `/scripts` and `/assets` folders with necessary files.

**Steps:**

After `/create-skill` generates `skill.md`, follow up in chat:

---

**Prompt 1: Create `/scripts`**

```
Based on the skill.md you just created, now create the /scripts folder with the necessary Python files. Use the task breakdown from my tasks.md and follow the patterns from [reference skill name from Phase 1].
```

---

**Prompt 2: Create `/assets`**

```
Now create the /assets folder for this skill. Include any templates, sample inputs, or configuration files needed based on my tasks.md.
```

---

**Prompt 3: Verify Completeness**

```
Review the skill folder structure you've created. Compare it against my tasks.md and confirm:
1. All tasks have corresponding scripts
2. Input/output formats match my interface-spec.md
3. Any missing files or folders
```

---

**If the agent misses something:**

```
You missed [specific file/folder]. Please create it now following the same patterns.
```

---

**Output:** Complete skill folder with:
- [ ] `skill.md`
- [ ] `/scripts` with Python files
- [ ] `/assets` with templates/configs (if applicable)

---

### PM

**Goal:** Continue drafting Integration Test Plan; prepare for Phase 4 audit.

**Additional Tasks:**

1. Review Skill Owners' progress (check-in at 0:35)
2. Identify any interface mismatches early
3. Prepare to run `/scout` on the combined project structure

---

## Phase 4: Audit (15 min)

### Skill Owners

**Goal:** Run `/scout` → `/review` on your skill and fix flagged issues.

**Steps:**

1. Run `/scout` to generate `ARCHITECTURE.md`:

```
/scout
```

2. Review the generated architecture diagram
3. Run `/review` to audit against the Holy Trinity:

```
/review
```

4. Review the output:
   - **Consistency Check:** Any drift from `constitution.md`, `spec.md`, `plan.md`?
   - **Logic Trace:** Does the Mermaid diagram reflect your intended logic?

**Output:** 
- [ ] `ARCHITECTURE.md` committed
- [ ] `/review` output reviewed
- [ ] Issues identified for fixing

---

### PM

**Goal:** Run `/scout` → `/review` on the combined project structure.

**Steps:**

1. Pull latest changes from both Skill Owners
2. Run `/scout` on the project root:

```
/scout
```

3. Review the combined architecture diagram
4. Run `/review`:

```
/review
```

5. Check for:
   - [ ] Interface mismatches between Skill A and Skill B
   - [ ] Constitution violations across both skills
   - [ ] Integration points flagged as warnings

**Output:**
- [ ] Combined `ARCHITECTURE.md` reviewed
- [ ] Integration issues documented

---

## Phase 5: Fix & Commit (7 min)

### Skill Owners

**Goal:** Address critical issues and commit.

**Steps:**

1. Fix any ❌ errors flagged by `/review`
2. Address ⚠️ warnings if time permits
3. Commit your skill folder:

```bash
git add .skills/[skill-name]/
git commit -m "Add [skill-name] skill with scripts and assets"
git push
```

---

### PM

**Goal:** Document blockers and prepare for Gate 5.

**Steps:**

1. Add any integration blockers to `DEBT.md`:

```markdown
## DEBT.md

### Integration Blockers (Week 5)

| ID | Blocker | Owner | Status |
|:---|:--------|:------|:------:|
| D1 | [Description] | [Skill A/B/PM] | ☐ |
```

2. Verify both Skill Owners have committed
3. Prepare Gate 5 status report

---

## Phase 6: Gate 5 Check — Skill Gate (5 min)

**Format:** PM presents team status to instructor

---

### Gate 5 Criteria

| Criterion | Owner | Status |
|:----------|:------|:------:|
| `skill.md` committed for both skills | Skill Owners | ☐ |
| `/scripts` folder with Python files for both skills | Skill Owners | ☐ |
| `/review` run with no ❌ critical errors | Skill Owners | ☐ |
| `ARCHITECTURE.md` committed | Skill Owners | ☐ |
| Integration Test Plan drafted | PM | ☐ |
| PM ran `/scout` → `/review` on combined project | PM | ☐ |
| Blockers documented in `DEBT.md` | PM | ☐ |

---

### Gate Check Process

1. **PM presents** (2 min):
   - "Both skills scaffolded: ✅ / ❌"
   - "Both skills pass `/review`: ✅ / ❌"
   - "Integration blockers: [list or none]"

2. **Instructor verifies** (2 min):
   - Spot-check one `skill.md`
   - Spot-check one `/review` output
   - Confirm `ARCHITECTURE.md` exists

3. **Gate Decision** (1 min):
   - ✅ **Pass:** Proceed to Week 6 (Integration)
   - ⚠️ **Conditional:** Minor issues to fix before Week 6
   - ❌ **Blocked:** Critical issues require office hours before Week 6

---

### If You Don't Pass

| Issue | Resolution |
|:------|:-----------|
| Missing `skill.md` | Complete before Week 6 using `/create-skill` |
| `/review` shows ❌ errors | Fix violations against Holy Trinity |
| No `ARCHITECTURE.md` | Run `/scout` and commit output |
| Integration blockers unresolved | Document in `DEBT.md`; address in Week 6 lab |

---

## Troubleshooting

| Problem | Solution |
|:--------|:---------|
| `/create-skill` doesn't generate `/scripts` | Use follow-up prompts in Phase 3 |
| `/skill-finder` returns no matches | Broaden your search query; try different keywords |
| `/review` flags too many issues | Focus on ❌ errors first; ⚠️ warnings can wait |
| Skill A output doesn't match Skill B input | PM documents in `DEBT.md`; fix in Week 6 |
| Agent stops mid-generation | Say "Continue" or re-prompt with specific request |

---

## Appendix: Suggested Follow-up Prompts

### If `/create-skill` only generates `skill.md`:

```
Based on the skill.md you just created, now create the /scripts folder with the necessary Python files. Use the task breakdown from my tasks.md and follow the patterns from [reference skill name].
```

### If `/scripts` is incomplete:

```
You created [file1.py] but my tasks.md also requires [task X]. Please create the script for that task.
```

### If `/assets` is missing:

```
Now create the /assets folder for this skill. Include any templates, sample inputs, or configuration files needed based on my tasks.md.
```

### If you need to verify completeness:

```
Review the skill folder structure you've created. Compare it against my tasks.md and confirm:
1. All tasks have corresponding scripts
2. Input/output formats match my interface-spec.md
3. Any missing files or folders
```

### If the agent made an error:

```
The [file/function] you created doesn't match my spec.md. According to my spec, it should [correct behavior]. Please fix it.
```

---


*End of Lesson 5.6 Student Lab Kit*
