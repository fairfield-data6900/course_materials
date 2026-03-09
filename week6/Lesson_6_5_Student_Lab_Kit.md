# 🛠️ Lesson 6.5 Student Lab Kit: Final Sprint

**Duration:** 99 min  
**Format:** Hands-on Lab  
**Prerequisite:** Watched Lesson 6.4 demo (`/scout` → `/review` → `/trace`)  
**Goal:** Finalize integration, run full observability stack, prepare Happy Path for Week 7 dress rehearsal

---

## Overview

| Phase | Time | Duration | Skill Owners | PM |
|:------|:-----|:---------|:-------------|:---|
| **1. Integration Finalization** | 0:00–0:30 | 30 min | Connect Skill A → Skill B; verify data handoff | Coordinate; resolve blockers |
| **2. Observability Stack** | 0:30–0:55 | 25 min | Run `/scout` → `/review` → `/trace` on **own skill** | Run `/scout` → `/review` → `/trace` on **integrated project** |
| **3. Landmine Triage** | 0:55–1:10 | 15 min | Address 🔴 High-risk landmines OR document in `DEBT.md` | Triage project-level landmines; update `DEBT.md` |
| **4. Happy Path Verification** | 1:10–1:25 | 15 min | Test end-to-end flow with sample input | Verify output matches expectations |
| **5. README Draft** | 1:25–1:34 | 9 min | **Team effort** — all members contribute | Facilitate; ensure Anthropic template structure |
| **6. Gate 6 Check** | 1:34–1:39 | 5 min | Team verifies Gate 6 criteria | PM presents team status |

---

## Role Assignments

| Role | Primary Focus | Key Deliverables |
|:-----|:--------------|:-----------------|
| **Skill Owner A** | Skill A completion + audit | `/review` passing on Skill A; landmines addressed or documented |
| **Skill Owner B** | Skill B completion + audit | `/review` passing on Skill B; landmines addressed or documented |
| **PM / Integrator** | Integration + project-level audit | Integration verified; project `/trace` run; `DEBT.md` updated; README facilitated |

---

## Phase 1: Integration Finalization (30 min)

### Goal

Connect Skill A output → Skill B input; verify the data handoff works end-to-end.

---

### Skill Owners

**Skill Owner A:**

1. Verify your skill produces output in the expected format
2. Run your skill with sample input:
   ```bash
   python .skills/[skill-a]/scripts/main.py --input sample_input.txt
   ```
3. Confirm output file is generated (e.g., `skill_a_output.json`)
4. Share output location with Skill Owner B

**Skill Owner B:**

1. Verify your skill can consume Skill A's output format
2. Run your skill with Skill A's output:
   ```bash
   python .skills/[skill-b]/scripts/main.py --input ../skill-a/output/skill_a_output.json
   ```
3. Confirm final output is generated
4. Report success or blockers to PM

---

### PM

**Coordination Checklist:**

- [ ] Skill Owner A has produced sample output
- [ ] Skill Owner B has consumed Skill A output successfully
- [ ] End-to-end data flow verified
- [ ] Any format mismatches identified and logged

**If Blockers Arise:**

1. Document the blocker immediately in `DEBT.md`
2. Determine if it's fixable in this session (< 10 min fix)
3. If not fixable, create a workaround for Happy Path demo

---

### Integration Verification Checklist

| Check | Status |
|:------|:------:|
| Skill A runs without errors | ☐ |
| Skill A output format matches `interface-spec.md` | ☐ |
| Skill B accepts Skill A output | ☐ |
| Skill B runs without errors | ☐ |
| Final output generated | ☐ |

---

## Phase 2: Observability Stack (25 min)

### Goal

Run the full observability sequence on your skill (Skill Owners) and on the integrated project (PM).

---

### Skill Owners: Audit Your Own Skill

**Step 1: Run `/scout`**

```
/scout
```

- Verify `ARCHITECTURE.md` is generated for your skill
- Check that file index and Mermaid diagram are accurate

**Step 2: Run `/review`**

```
/review
```

- Check Consistency against Holy Trinity (`constitution.md`, `spec.md`, `plan.md`)
- Review any ⚠️ warnings or ❌ errors
- **Target:** No ❌ critical errors

**Step 3: Run `/trace`**

```
/trace
```

- Review Decision Path diagram
- Note any Assumption Challenges
- Identify 🔴 High-risk landmines

**Output Checklist (per Skill Owner):**

- [ ] `ARCHITECTURE.md` generated and committed
- [ ] `/review` run — no ❌ critical errors
- [ ] `/trace` run — landmines identified

---

### PM: Audit the Integrated Project

**Step 1: Pull Latest Changes**

```bash
git pull origin main
```

**Step 2: Run `/scout` on Project Root**

```
/scout
```

- Verify combined architecture includes both skills
- Check cross-skill data flow in Mermaid diagram

**Step 3: Run `/review` on Integrated Project**

```
/review
```

- Check for integration-level violations
- Look for interface mismatches between skills

**Step 4: Run `/trace` on Integrated Project**

```
/trace
```

- Review cross-skill Decision Path
- Identify project-level landmines (e.g., format mismatch, context overflow)

**Output Checklist (PM):**

- [ ] Combined `ARCHITECTURE.md` reviewed
- [ ] `/review` run on integrated project — no ❌ critical errors
- [ ] `/trace` run — project-level landmines identified

---

## Phase 3: Landmine Triage (15 min)

### Goal

Address 🔴 High-risk landmines OR document them in `DEBT.md` with a remediation plan.

---

### Decision Tree

```
┌─────────────────────────────────────────────────────────────┐
│                    LANDMINE TRIAGE                          │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   For each 🔴 High-risk landmine:                           │
│                                                             │
│   ┌─────────────────────────────────────────────────────┐   │
│   │ Can you fix it in < 10 minutes?                     │   │
│   └─────────────────────────────────────────────────────┘   │
│                    │                                        │
│          ┌────────┴────────┐                                │
│          ▼                 ▼                                │
│        YES                NO                                │
│          │                 │                                │
│          ▼                 ▼                                │
│   ┌──────────────┐  ┌──────────────────────────────────┐   │
│   │ FIX IT NOW   │  │ DOCUMENT IN DEBT.md              │   │
│   │              │  │ + Add remediation plan           │   │
│   │ Then re-run  │  │ + Assign owner                   │   │
│   │ /review      │  │ + Set target (Week 7)            │   │
│   └──────────────┘  └──────────────────────────────────┘   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

### Skill Owners

1. Review your `/trace` output — focus on 🔴 High-risk landmines
2. For each landmine, decide: **Fix now** or **Document**
3. If fixing:
   - Make the change
   - Re-run `/review` to verify no new errors
   - Commit the fix
4. If documenting:
   - Add entry to `DEBT.md` using the template below
   - Include remediation plan and target date

---

### PM

1. Collect landmine reports from both Skill Owners
2. Review project-level landmines from your `/trace`
3. Update `DEBT.md` with all unresolved landmines
4. Assign owners and set targets (Week 7)

---

### `DEBT.md` Landmine Entry Template

```markdown
## Unresolved Landmines (Week 6)

| ID | Landmine | Risk | Trigger Condition | Remediation Plan | Owner | Target |
|:---|:---------|:-----|:------------------|:-----------------|:------|:-------|
| L1 | [Name] | 🔴 High | [When does this break?] | [How will you fix it?] | [Name] | Week 7 |
| L2 | [Name] | 🔴 High | [When does this break?] | [How will you fix it?] | [Name] | Week 7 |
```

**Example Entry:**

```markdown
| L1 | No Speaker Labels | 🔴 High | Auto-transcribed input without diarization | Add fallback segmentation on pauses > 3s | Skill Owner A | Week 7 |
| L2 | Context Overflow | 🔴 High | Transcript > 50k tokens | Implement chunking before LLM call | Skill Owner B | Week 7 |
```

---

## Phase 4: Happy Path Verification (15 min)

### Goal

Test the complete end-to-end flow with sample input; verify output matches expectations.

---

### Team Workflow

**Step 1: Select Sample Input**

- Use a representative sample (not edge case)
- Ensure input is committed to repo (e.g., `samples/sample_input.txt`)

**Step 2: Run End-to-End**

```bash
# Run Skill A
python .skills/[skill-a]/scripts/main.py --input samples/sample_input.txt

# Run Skill B with Skill A output
python .skills/[skill-b]/scripts/main.py --input .skills/[skill-a]/output/result.json
```

**Step 3: Verify Output**

- Open final output file
- Compare against expected behavior from `spec.md`
- Check for obvious errors (empty output, malformed data, missing sections)

**Step 4: Document Result**

| Check | Status | Notes |
|:------|:------:|:------|
| Skill A produces output | ☐ | |
| Skill B consumes output | ☐ | |
| Final output generated | ☐ | |
| Output matches spec expectations | ☐ | |
| No runtime errors | ☐ | |

---

### If Happy Path Fails

1. Identify the failure point (Skill A, Skill B, or integration)
2. Determine if it's a quick fix (< 5 min)
3. If not fixable now:
   - Document in `DEBT.md`
   - Prepare a "demo workaround" (e.g., pre-generated output)
   - Note this for Week 7 dress rehearsal

---

## Phase 5: README Draft (9 min)

### Goal

Draft `README.md` using the Anthropic Agent skill template as a reference.

**Template Reference:** [Anthropic Skills README](https://github.com/anthropics/skills/blob/main/README.md)

---

### Team Workflow

This is a **team effort** — all members contribute.

| Section | Owner | Time |
|:--------|:------|:-----|
| Project Title + Description | PM | 1 min |
| Features / What It Does | Skill Owner A | 2 min |
| Installation / Setup | Skill Owner B | 2 min |
| Usage / How to Run | PM | 2 min |
| Review & Commit | Team | 2 min |

---

### README Template (Adapted from Anthropic)

```markdown
# [Project Name]

[One-line description of what this project does]

## Overview

[2-3 sentences explaining the project's purpose and value]

## Features

- [Feature 1: What Skill A does]
- [Feature 2: What Skill B does]
- [Feature 3: Integration benefit]

## Prerequisites

- [Required software, e.g., Python 3.10+]
- [Required dependencies]
- [Any API keys or credentials needed]

## Installation

```bash
# Clone the repository
git clone [repo-url]
cd [project-name]

# Install dependencies
pip install -r requirements.txt
```

## Usage

```bash
# Run the pipeline
python main.py --input [input-file]
```

### Example

```bash
python main.py --input samples/sample_transcript.txt
```

**Output:** `output/marketing_kit.md`

## Project Structure

```
.
├── .skills/
│   ├── skill-a/
│   └── skill-b/
├── samples/
├── output/
├── spec.md
├── constitution.md
├── plan.md
└── README.md
```

## Team

- [Name] — [Role]
- [Name] — [Role]
- [Name] — [Role]

## License

[License type]
```

---

### Commit the Draft

```bash
git add README.md
git commit -m "Add README draft (Week 6)"
git push
```

---

## Phase 6: Gate 6 Check (5 min)

### Goal

Verify all Gate 6 criteria are met; PM presents team status.

---

### Gate 6 Criteria (Integration Gate)

| Criterion | Owner | Status |
|:----------|:------|:------:|
| **Happy Path:** Core functionality working end-to-end | Team | ☐ |
| **Integration:** Skill A → Skill B data flow verified | Skill Owners | ☐ |
| **`/review` Audit (Skill A):** No ❌ critical errors | Skill Owner A | ☐ |
| **`/review` Audit (Skill B):** No ❌ critical errors | Skill Owner B | ☐ |
| **`/review` Audit (Integrated):** No ❌ critical errors | PM | ☐ |
| **`/trace` Run:** Landmines documented (fixed OR in `DEBT.md`) | PM | ☐ |
| **README.md:** Draft started (Anthropic template) | Team | ☐ |

---

### PM Status Report Template

```markdown
## Gate 6 Status: [Team Name]

**Date:** [Date]

### Summary
- **Happy Path:** [Working / Partial / Blocked]
- **Integration:** [Complete / In Progress / Blocked]
- **Audit Status:** [All passing / X warnings / X errors]

### Landmine Status
| Resolved | Documented | Total |
|:--------:|:----------:|:-----:|
| [#] | [#] | [#] |

### Blockers
1. [Blocker 1 — Owner — Target]
2. [Blocker 2 — Owner — Target]

### Week 7 Focus
- [Priority 1]
- [Priority 2]
```

---

## Troubleshooting

| Problem | Solution |
|:--------|:---------|
| Skill A output format doesn't match Skill B input | Check `interface-spec.md`; add format conversion if needed |
| `/review` shows ❌ critical error | Fix the violation; re-run `/review` |
| `/trace` shows too many landmines | Focus on 🔴 High-risk only; document the rest |
| Happy Path fails at integration | Isolate the failure point; test each skill independently first |
| README draft incomplete | Focus on Usage section; other sections can be completed in Week 7 |
| Git conflicts | PM resolves; ensure everyone pulls before pushing |

---

## Appendix A: Integration Troubleshooting Prompts

*Use these prompts if you encounter integration issues.*

### Format Mismatch

```
Skill A outputs JSON with this structure: [paste sample]
Skill B expects this structure: [paste expected]
Help me create a transformation function to convert Skill A output to Skill B input format.
```

### Missing Fields

```
Skill B requires these fields: [list fields]
Skill A output is missing: [list missing fields]
How should I handle the missing fields? Options: default values, error, or skip.
```

### Data Type Mismatch

```
Skill A outputs [field] as a string: "123"
Skill B expects [field] as an integer: 123
Add type conversion to the integration layer.
```

### Debugging Integration Failure

```
When I run Skill B with Skill A's output, I get this error: [paste error]
Here's Skill A's output: [paste output]
Here's Skill B's input handler: [paste code]
Help me identify and fix the issue.
```

---

## Appendix B: `DEBT.md` Full Template

```markdown
# Technical Debt Register

## Overview

This document tracks known issues, unresolved landmines, and planned improvements.

---

## Unresolved Landmines (Week 6)

| ID | Landmine | Risk | Trigger Condition | Remediation Plan | Owner | Target |
|:---|:---------|:-----|:------------------|:-----------------|:------|:-------|
| L1 | | | | | | |
| L2 | | | | | | |

---

## Known Issues

| ID | Issue | Severity | Workaround | Owner | Target |
|:---|:------|:---------|:-----------|:------|:-------|
| I1 | | | | | |

---

## Deferred Features

| ID | Feature | Reason Deferred | Owner | Target |
|:---|:--------|:----------------|:------|:-------|
| F1 | | | | |

---

## Resolved Items

| ID | Item | Resolution | Date |
|:---|:-----|:-----------|:-----|
| | | | |
```

---

## What's Next: Week 7

**Week 7 Focus:** Pre-Flight Gate — Dress Rehearsal

- Feature freeze
- Address remaining `DEBT.md` items
- Finalize `README.md`
- Full dress rehearsal of Happy Path demo
- Peer feedback session

**Bring to Week 7:**
- Working Happy Path
- Updated `DEBT.md` with remediation status
- Draft `README.md`

---

*End of Lesson 6.5 Student Lab Kit*
