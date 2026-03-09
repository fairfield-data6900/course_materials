# 📘 Lesson 4.7 Student Lab Kit: PM Integration Audit

**Duration:** 39 min  
**Format:** Hands-on  
**Prerequisite:** Skill Owners have drafted `tasks.md` (Lesson 4.5); watched scaffolding demo (Lesson 4.6)  
**Goal:** PMs audit their team's `tasks.md` files for consistency, dependency alignment, and integration readiness using `analyze` and `interface-spec.md`.

---

## 👥 Role Assignments

| Role | Activity This Lesson |
|:-----|:---------------------|
| **PM / Integrator** | Run Integration Audit; identify cross-skill issues; document findings |
| **Skill Owner A** | Respond to PM questions; refine `tasks.md` based on feedback |
| **Skill Owner B** | Respond to PM questions; refine `tasks.md` based on feedback |

> **PMs:** This is YOUR lesson. You observed in 4.5 — now you lead. Your job is to catch integration issues BEFORE code is written.

---

## ⏱ Timeline (39 min)

| Phase | Time | Activity | Owner |
|:------|:-----|:---------|:------|
| 1 | 0:00–0:05 | Collect artifacts | PM |
| 2 | 0:05–0:15 | Run `analyze` on each skill | PM |
| 3 | 0:15–0:25 | Cross-skill dependency check | PM + Skill Owners |
| 4 | 0:25–0:35 | Document findings in `AUDIT.md` | PM |
| 5 | 0:35–0:39 | Confirm Gate 4 readiness | Team |

---

## 📋 Phase-by-Phase Instructions

### Phase 1: Collect Artifacts (0:00–0:05)

**Action:** Gather all artifacts needed for the audit.

**PM Checklist:**

| Artifact | Location | Status |
|:---------|:---------|:------:|
| `interface-spec.md` | Project root (from Week 1) | ☐ |
| `spec.md` | Project root | ☐ |
| `plan.md` | Project root | ☐ |
| Skill A `tasks.md` | `.skills/[skill-a]/tasks.md` or project root | ☐ |
| Skill B `tasks.md` | `.skills/[skill-b]/tasks.md` or project root | ☐ |

**Quick Verification:**

```bash
# Confirm all files exist
ls -la spec.md plan.md interface-spec.md
ls -la .skills/*/tasks.md
```

**Checkpoint:**
- [ ] All 5 artifacts located
- [ ] Files are committed (not just local drafts)

---

### Phase 2: Run `analyze` on Each Skill (0:05–0:15)

**Action:** Run `/analyze` for each skill's artifact chain.

**For Skill A:**

```
/analyze --scope skill-a
```

**For Skill B:**

```
/analyze --scope skill-b
```

**What `analyze` Checks:**

| Check | Description |
|:------|:------------|
| **Consistency** | Do `tasks.md` requirements match `spec.md`? |
| **Completeness** | Are all `spec.md` requirements covered by tasks? |
| **Ambiguity** | Are there vague terms that need clarification? |
| **Duplication** | Are any tasks redundant across skills? |

**Output Legend:**

| Symbol | Meaning | Action |
|:-------|:--------|:-------|
| ✅ | Consistent | No action needed |
| ⚠️ | Ambiguity or gap | Discuss with Skill Owner |
| ❌ | Contradiction | Must resolve before Gate 4 |
| 🔄 | Duplication | Clarify ownership |

**PM Recording Template:**

```markdown
## Skill A: `analyze` Results

**Run time:** [timestamp]

### ✅ Consistent Items
- [list items]

### ⚠️ Warnings
- [ ] [Warning 1] — Assigned to: [Skill Owner A]
- [ ] [Warning 2] — Assigned to: [Skill Owner A]

### ❌ Errors
- [ ] [Error 1] — BLOCKING — Must resolve before Gate 4

---

## Skill B: `analyze` Results

[Same structure]
```

**Checkpoint:**
- [ ] `analyze` run on Skill A
- [ ] `analyze` run on Skill B
- [ ] All ❌ errors flagged for immediate resolution

---

### Phase 3: Cross-Skill Dependency Check (0:15–0:25)

**Action:** Verify that Skill A's outputs match Skill B's expected inputs (and vice versa).

**Reference:** Open `interface-spec.md` from Week 1.

**The Core Question:**

> *"Does Skill A's output format match what Skill B expects as input?"*

**Dependency Audit Table:**

| Skill A Output | Expected Format | Skill B Input | Expected Format | Match? |
|:---------------|:----------------|:--------------|:----------------|:------:|
| [e.g., `segments.json`] | [e.g., JSON array] | [e.g., `segments.json`] | [e.g., JSON array] | ✅ / ❌ |
| [e.g., `summary.txt`] | [e.g., Plain text] | [e.g., `summary.txt`] | [e.g., Markdown] | ✅ / ❌ |

**Common Integration Issues:**

| Issue | Example | Resolution |
|:------|:--------|:-----------|
| **Format mismatch** | Skill A outputs JSON, Skill B expects CSV | Agree on single format; update both `tasks.md` |
| **Missing field** | Skill A outputs `{speaker, text}`, Skill B needs `{speaker, text, timestamp}` | Skill A adds `timestamp` to output |
| **Naming conflict** | Both skills output `output.json` | Rename to `skill_a_output.json` and `skill_b_output.json` |
| **Undefined handoff** | No task covers "pass data from A to B" | Add integration task to PM's scope |

**Discussion Protocol:**

1. PM presents the Dependency Audit Table
2. Skill Owner A confirms their output format
3. Skill Owner B confirms their input expectation
4. If mismatch: decide who adjusts (usually the producer, Skill A)
5. Document the decision

**Checkpoint:**
- [ ] All cross-skill dependencies mapped
- [ ] Mismatches identified and assigned for resolution
- [ ] `interface-spec.md` still accurate (or flagged for update)

---

### Phase 4: Document Findings in `AUDIT.md` (0:25–0:35)

**Action:** PM creates `AUDIT.md` to document all findings.

**File Location:** Project root

**`AUDIT.md` Template:**

```markdown
# Integration Audit — Week 4

**Auditor:** [PM Name]  
**Date:** [Date]  
**Gate:** 4 (Task Gate)

---

## 1. Artifact Verification

| Artifact | Present | Committed | Notes |
|:---------|:-------:|:---------:|:------|
| `spec.md` | ✅ / ❌ | ✅ / ❌ | |
| `plan.md` | ✅ / ❌ | ✅ / ❌ | |
| `interface-spec.md` | ✅ / ❌ | ✅ / ❌ | |
| Skill A `tasks.md` | ✅ / ❌ | ✅ / ❌ | |
| Skill B `tasks.md` | ✅ / ❌ | ✅ / ❌ | |

---

## 2. `analyze` Summary

### Skill A

| Type | Count | Details |
|:-----|:-----:|:--------|
| ✅ Consistent | | |
| ⚠️ Warnings | | |
| ❌ Errors | | |

**Action Items:**
- [ ] [Action 1] — Owner: [Name] — Due: [Date]

### Skill B

| Type | Count | Details |
|:-----|:-----:|:--------|
| ✅ Consistent | | |
| ⚠️ Warnings | | |
| ❌ Errors | | |

**Action Items:**
- [ ] [Action 1] — Owner: [Name] — Due: [Date]

---

## 3. Cross-Skill Dependencies

| Skill A Output | Format | Skill B Input | Format | Status |
|:---------------|:-------|:--------------|:-------|:------:|
| | | | | ✅ / ⚠️ / ❌ |

**Mismatches Identified:**
- [ ] [Mismatch 1] — Resolution: [Decision] — Owner: [Name]

---

## 4. Gate 4 Readiness

| Criterion | Status | Notes |
|:----------|:------:|:------|
| 3+ tasks per skill | ✅ / ❌ | |
| 50%+ Black-Box Test Tables | ✅ / ❌ | |
| No unresolved ❌ errors | ✅ / ❌ | |
| Cross-skill dependencies mapped | ✅ / ❌ | |

**Overall Status:** READY / NOT READY

**Blocking Issues (if any):**
1. [Issue]
2. [Issue]

---

## 5. PM Notes

[Free-form observations, concerns, or recommendations for Week 5]

---

*End of Audit*
```

**Checkpoint:**
- [ ] `AUDIT.md` created
- [ ] All sections completed
- [ ] Action items assigned with owners

---

### Phase 5: Confirm Gate 4 Readiness (0:35–0:39)

**Action:** Team reviews `AUDIT.md` together and confirms Gate 4 status.

**Gate 4 Criteria (from v7 Schedule):**

| Criterion | Owner | Status |
|:----------|:------|:------:|
| Skill-level `tasks.md` committed (3+ tasks per skill) | Skill Owners | ☐ |
| 50%+ tasks have Black-Box Test Tables | Skill Owners | ☐ |
| PM Integration Audit completed | PM | ☐ |

**Decision Tree:**

```
All criteria met?
    │
    ├── YES → Gate 4 PASSED ✅
    │         Commit AUDIT.md
    │         Ready for Week 5
    │
    └── NO → Gate 4 FLAGGED ⚠️
             Document in DEBT.md
             Assign resolution owners
             Must resolve before Week 5 Lab
```

**If Flagged — Add to `DEBT.md`:**

```markdown
## Gate 4 Debt

| Issue | Owner | Due | Status |
|:------|:------|:----|:------:|
| [Issue description] | [Name] | Before Week 5 | ⏳ |
```

**Final Commit:**

```bash
git add AUDIT.md DEBT.md
git commit -m "Week 4: Integration Audit complete — Gate 4 [PASSED/FLAGGED]"
```

**Checkpoint:**
- [ ] Gate 4 status determined (PASSED or FLAGGED)
- [ ] `AUDIT.md` committed
- [ ] `DEBT.md` updated (if applicable)
- [ ] Team aligned on Week 5 priorities

---

## ✅ Success Criteria

| Criterion | Verification |
|:----------|:-------------|
| `analyze` run on both skills | Output reviewed; warnings addressed |
| Cross-skill dependencies mapped | Dependency Audit Table completed |
| `AUDIT.md` created and committed | File exists in repo |
| Gate 4 status determined | PASSED or FLAGGED with documented debt |

---

## 🔧 Troubleshooting

| Problem | Solution |
|:--------|:---------|
| `analyze` returns too many warnings | Prioritize ❌ errors first; ⚠️ warnings can be addressed in Week 5 |
| Skill Owners disagree on format | PM makes the call; document decision in `AUDIT.md` |
| `interface-spec.md` is outdated | Flag for update; add to `DEBT.md` |
| Not enough time to complete audit | Focus on Phase 3 (cross-skill dependencies) — this is the highest-value check |
| Skill Owner hasn't committed `tasks.md` | They commit NOW; audit proceeds on committed version |

---

## 📎 Appendix: PM Companion Prompts

### Prompt 1: Dependency Discovery

```
I'm the PM auditing my team's capstone project. Help me identify potential integration issues.

Skill A outputs: [describe outputs]
Skill B expects as input: [describe inputs]

Questions:
1. Are there any format mismatches?
2. Are there any missing fields?
3. What edge cases might cause integration failures?
```

### Prompt 2: `analyze` Warning Triage

```
The `analyze` command returned these warnings:

[paste warnings]

Help me triage:
1. Which warnings are BLOCKING (must fix before Gate 4)?
2. Which warnings can be deferred to Week 5?
3. For each blocking warning, suggest a resolution.
```

### Prompt 3: AUDIT.md Generator

```
Generate an AUDIT.md file based on my findings:

Artifacts present: [list]
Skill A analyze results: [summary]
Skill B analyze results: [summary]
Cross-skill dependencies: [list matches/mismatches]
Gate 4 criteria status: [list]

Format it using the standard AUDIT.md template with tables and checkboxes.
```

### Meta-Prompt: Integration Auditor Catalyst

```
You are my Integration Auditor Catalyst. Your job is NOT to do the audit for me, but to help me think critically about integration risks.

My project: [brief description]
Skill A: [description]
Skill B: [description]

Guide me through these challenges:

1. **Interface Alignment:** Ask me questions that reveal whether Skill A's outputs truly match Skill B's inputs.

2. **Hidden Dependencies:** Help me identify dependencies I might have missed (shared resources, execution order, error propagation).

3. **Edge Case Propagation:** For each cross-skill handoff, ask what happens when Skill A produces an edge case output.

4. **PM Ownership:** Help me identify any integration tasks that belong to ME, not the Skill Owners.

Ask me ONE question at a time. Wait for my response before asking the next question.
```

---

*End of Lesson 4.7 Student Lab Kit*
