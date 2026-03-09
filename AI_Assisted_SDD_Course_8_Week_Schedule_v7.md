# AI-Assisted SDD for Business Analysts — 8-Week Schedule

**Course Title:** AI-Assisted Software Design Document (SDD) for Business Analysts  
**Version:** 8.0  
**Last Updated:** March 8, 2026

---

## Schedule Overview

| Week | Duration | Theme | Student-Led Topic |
|------|----------|-------|-------------------|
| 1 | 3 hours | Foundations & Setup | — |
| 2 | 3 hours | Refinement & Guardrails | — |
| 3 | 3 hours | The Implementation Plan | — |
| 4 | 3 hours | Agentic Skills & Task Decomposition | Group A: Agentic Skills |
| 5 | 3 hours | Hooks & Observability | Group B: Hooks & Guardrails |
| 6 | 3 hours | Sub-agents & Final Integration | Group C: Sub-agents |
| 7 | 3 hours | Dress Rehearsal | — |
| 8 | 2 hours | Final Showcase | — |

**Total Contact Hours:** 23 hours

---

## Structural Changes from v7

| Change | Details |
|--------|---------|
| **Week 1 timing corrected** | Lesson 1.2 = 20 min (not 30); Mid-session stand-up added as Lesson 1.5; lessons renumbered to 1.7 total |
| **Week 1 Lab 2 updated** | Now explicitly includes `/speckit.clarify`; `interface-spec.md` removed from Week 1 gate |
| **Week 4 Lesson 4.5 replaced** | Scaffolding Demo (no content file exists) → Student Lab A: Task Drafting with `/speckit.tasks` |
| **Week 4 Lesson 4.7 clarified** | Now PM Integration Audit only (39 min); `AUDIT.md` is the key artifact |
| **Week 5 Lesson 5.4 replaced** | "Extension + Observability / `/trace`" → `/scout` → `/review` Demo (41 min); stale Cutting Logic table removed |
| **Week 5 Gate 5 fixed** | `/review-skill` → `/review` (command corrected) |
| **Week 6 Lesson 6.4 updated** | "Code Review & Final Guardrails" → "Full Observability Stack" (`/scout` → `/review` → `/trace`, 30 min) |
| **Week 6 Gate 6 fixed** | `/test-first` removed; `/trace` + `DEBT.md` added |
| **Podcast Skill table updated** | Weeks 4–6 demo progression reflects actual demo kit content |
| **Consulting Moments table updated** | Commands corrected to match actual lesson files |
| **Student Presentation table updated** | `.skills/` → `.github/skills/`; `/review-skill` → `/review`; `/test-first` removed |
| **Key Artifacts table updated** | `interface-spec.md` removed from Week 1; `AUDIT.md`, `ARCHITECTURE.md`, `DEBT.md` added |
| **Gate Criteria table updated** | All gates reflect actual lesson content |
| **Hands-on time recalculated** | Week 1: 99 min (55%); Week 4: 69 min (38%); Week 5: 62 min (34%); Week 6: 73 min (40%) |

---

## Podcast Skill Demo Progression (Weeks 4–6)

| Week | Lesson | Focus | Key Commands | Metaphor |
|------|--------|-------|--------------|----------|
| **4** | 4.4 | **Task Decomposition** — Transform `plan.md` into atomic tasks; verify alignment with `spec.md` | `/speckit.tasks`, `/speckit.analyze` | 📋 The Construction Schedule |
| **5** | 5.4 | **Codebase Mapping + Audit** — Map structure with `/scout`; audit against Holy Trinity with `/review` | `/scout`, `/review` | 🗺️ The Cartographer + ⚖️ The Auditor |
| **6** | 6.4 | **Full Observability Stack** — Complete audit: map → review → trace decisions | `/scout`, `/review`, `/trace` | 🔍 The Investigator |

---

## Week 1: Foundations & Setup (3 Hours)

**Theme:** The "Overconfident Intern" mental model; environment verification; drafting initial `spec.md`

| Time | Lesson | Duration | Type | Topic |
|------|--------|----------|------|-------|
| 00:00 – 00:20 | 1.1 | 20 min | Lecture | **Why SDD?** — The "Overconfident Intern" metaphor |
| 00:20 – 00:40 | 1.2 | 20 min | Verification | **Environment Check** — VS Code Insiders + Copilot + Spec Kit confirmed |
| 00:40 – 01:10 | 1.3 | 30 min | Demo | **Instructor Demo:** `specify init` + draft `spec.md` for Podcast Skill (RTCF framework) |
| 01:10 – 02:00 | 1.4 | 50 min | Hands-on | **PM leads:** Draft project-level `spec.md` for capstone |
| 02:00 – 02:06 | 1.5 | 6 min | Stand-up | **Mid-Session Stand-up** — Project names & blockers (30 sec per team) |
| 02:06 – 02:55 | 1.6 | 49 min | Hands-on | **Lab 2:** Peer review specs (2 strengths + 2 suggestions); run `/speckit.clarify`; commit |
| 02:55 – 03:00 | 1.7 | 5 min | Gate | **Environment Gate Check** |

**Gate 1 Criteria:**
- VS Code Insiders + Copilot working (`specify check` passes)
- Draft `spec.md` committed and pushed
- Student can explain "context drift" (verbal spot-check)

**Key Artifacts:** Draft `spec.md`

**Hands-on Total:** 99 min (55%)

---

## Week 2: Refinement & Guardrails (3 Hours)

**Theme:** Refining specs with `/speckit.clarify`; establishing project rules via `constitution.md`

| Time | Lesson | Duration | Type | Topic |
|------|--------|----------|------|-------|
| 00:00 – 00:15 | 2.1 | 15 min | Recap | **Week 1 Review** — Spec quality audit; celebrate committed specs |
| 00:15 – 00:40 | 2.2 | 25 min | Lecture | **The Constitution** — Tech stack, security rules, "Out of Scope" |
| 00:40 – 01:25 | 2.3 | 45 min | Hands-on | **PM leads:** Draft `constitution.md`; team contributes |
| 01:25 – 01:31 | 2.4 | 6 min | Stand-up | **Mid-Session Stand-up** — Constitution decisions & blockers |
| 01:31 – 01:56 | 2.5 | 25 min | Demo | **Instructor Demo:** `/speckit.clarify` for Socratic Refinement |
| 01:56 – 02:46 | 2.6 | 50 min | Hands-on | **Team Collaborative:** Refine `spec.md` via `/speckit.clarify` |
| 02:46 – 02:55 | 2.7 | 9 min | Gate | **Specification Gate Check** |

**Gate 2 Criteria:**
- Refined `spec.md` committed
- `constitution.md` committed

**Key Artifacts:** Refined `spec.md`, `constitution.md`

**Hands-on Total:** 95 min (53%)

---

## Week 3: The Implementation Plan (3 Hours)

**Theme:** Moving from *what* to *how*; using `/speckit.plan`; Plan Triage; Edge Cases; Demo vs. Future Filter

| Time | Lesson | Duration | Type | Topic |
|------|--------|----------|------|-------|
| 00:00 – 00:06 | 3.1 | 6 min | Stand-up | **Weekly Stand-up** — Status, Blockers, Focus |
| 00:06 – 00:21 | 3.2 | 15 min | Recap | **Week 2 Review** — Constitution completeness; spec refinement status |
| 00:21 – 00:51 | 3.3 | 30 min | Demo | **Instructor Demo:** `/speckit.plan` (template-aligned) |
| 00:51 – 01:36 | 3.4 | 45 min | Hands-on | **PM leads:** Generate `plan.md` for capstone (full template) |
| 01:36 – 01:42 | 3.5 | 6 min | Stand-up | **Mid-Session Stand-up** — Plan decisions & blockers |
| 01:42 – 02:07 | 3.6 | 25 min | Demo | **Plan Triage + Edge Case Attack** (instructor models) |
| 02:07 – 02:55 | 3.7 | 48 min | Hands-on | **Team:** Run Plan Triage; Edge Case Attack; Demo vs. Future Filter |
| 02:55 – 03:00 | 3.8 | 5 min | Gate | **Planning Gate Check** |

**Gate 3 Criteria:**
- `plan.md` committed with Demo Scope (Tier 1/Tier 2)
- Edge Cases documented
- Skills identified

**Key Artifacts:** `plan.md` (Technical Context, Constitution Check, Project Structure, Demo Scope, Edge Cases)

**Hands-on Total:** 93 min (52%)

**End of Week 3 Assignment:** Distribute Agentic Skills pre-reading (for Group A presentation)

---

## Week 4: Agentic Skills & Task Decomposition (3 Hours)

**Theme:** Group A teaches Agentic Skills; Skill Owners decompose plans into atomic tasks using `/speckit.tasks`; PM performs Integration Audit

| Time | Lesson | Duration | Type | Topic |
|------|--------|----------|------|-------|
| 00:00 – 00:06 | 4.1 | 6 min | Stand-up | **Weekly Stand-up** — Status, Blockers, Focus |
| 00:06 – 00:36 | 4.2 | 30 min | Student-Led | **Group A Presentation: Agentic Skills** (Prompts + Code + Recipes; `.github/skills/` structure; `/review`) |
| 00:36 – 00:51 | 4.3 | 15 min | Discussion | **Q&A & Class Discussion** — Connecting skills to capstone architecture |
| 00:51 – 01:01 | — | 10 min | Buffer | **Instructor Demo Buffer** |
| 01:01 – 01:26 | 4.4 | 25 min | Demo | **Instructor Demo:** `/speckit.tasks` — Atomic task decomposition + Black-Box Test Tables + `/speckit.analyze` alignment check |
| 01:26 – 01:56 | 4.5 | 30 min | Hands-on | **Lab A — Skill Owners:** Draft `tasks.md` using `/speckit.tasks`; refine into atomic tasks; add Black-Box Test Tables; run `/speckit.analyze` |
| 01:56 – 02:11 | 4.6 | 15 min | Lecture | **The Integration Audit** — How PM verifies tasks align with `interface-spec.md` |
| 02:11 – 02:50 | 4.7 | 39 min | Hands-on | **Lab B — PM Integration Audit:** PM collects artifacts; runs `/speckit.analyze` on each skill; documents cross-skill dependencies in `AUDIT.md` |
| 02:50 – 03:00 | 4.8 | 10 min | Gate | **Task Gate Check** |

> **Note:** The Podcast Skill Scaffolding Demo (`.github/skills/` structure, `SKILL.md`, `scripts/`) has been deferred — no dedicated demo kit exists yet. The skill-building work begins in Week 5.

**Gate 4 Criteria:**
- Skill-level `tasks.md` committed (3+ tasks per skill)
- 50%+ tasks have Black-Box Test Tables
- PM Integration Audit (`AUDIT.md`) completed and committed

**Key Artifacts:** Skill-level `tasks.md`, `AUDIT.md` (Integration Audit notes)

**Hands-on Total:** 69 min (38%)

**End of Week 4 Assignment:** Distribute Hooks & Guardrails pre-reading (for Group B presentation)

---

## Week 5: Hooks & Observability (3 Hours)

**Theme:** Group B teaches Hooks & Guardrails; instructor demonstrates `/scout` → `/review` audit; Skill Owners build skills

| Time | Lesson | Duration | Type | Topic |
|------|--------|----------|------|-------|
| 00:00 – 00:06 | 5.1 | 6 min | Stand-up | **Weekly Stand-up** — Status, Blockers, Focus |
| 00:06 – 00:36 | 5.2 | 30 min | Student-Led | **Group B Presentation: Hooks & Guardrails** (Pre-commit hooks; linting with `ruff`; spec-checking) |
| 00:36 – 00:51 | 5.3 | 15 min | Discussion | **Q&A & Class Discussion** — Applying hooks to capstone projects |
| 00:51 – 01:01 | — | 10 min | Buffer | **Instructor Demo Buffer** |
| 01:01 – 01:42 | 5.4 | 41 min | Demo | **Instructor Demo: `/scout` → `/review`** — Map the codebase; audit against the Holy Trinity (`spec.md`, `constitution.md`, `plan.md`); generate Mermaid logic trace (35 min demo + 6 min Q&A) |
| 01:42 – 01:48 | 5.5 | 6 min | Stand-up | **Mid-Session Stand-up** — Skill progress & blockers |
| 01:48 – 02:50 | 5.6 | 62 min | Hands-on | **Deep Work:** Skill Owners build skills; PM begins integration |
| 02:50 – 03:00 | 5.7 | 10 min | Gate | **Skill Gate Check** |

### Lesson 5.4 Demo Flow: `/scout` → `/review` (35 min + 6 min Q&A)

| Phase | Time | What You Show | Teaching Moment |
|-------|------|---------------|-----------------|
| 1. Opening | 0:00–0:01 | Introduce "adding the nervous system" to the project | "Code that runs is not code you understand" |
| 2. Live `/scout` — Run | 0:01–0:03 | Run `/scout` in terminal; no arguments needed | "Auto-detects working directory; maps what's there" |
| 3. Live `/scout` — Read Architecture | 0:03–0:10 | Walk through generated `ARCHITECTURE.md`: modules, dependencies, hotspots | "This is your map before the audit" |
| 4. Live `/scout` — Mermaid Diagram | 0:10–0:16 | Show auto-generated Mermaid dependency graph | "A visual logic trace — you can now SEE the structure" |
| 5. Live `/review` | 0:16–0:28 | Run `/review`; step through each check against `spec.md`, `constitution.md`, `plan.md` | **Consulting Moment:** "Without this, the AI is a black box. With `/review`, you see the craft." |
| 6. Q&A | 0:29–0:35 | Class questions; connect to capstone projects | "What would `/review` flag in YOUR project?" |

**Gate 5 Criteria:**
- Both skills pass `/review` audit (no critical violations)
- PM integration in progress

**Key Artifacts:** `.github/skills/` directories with Prompts + Code; `ARCHITECTURE.md` (from `/scout`); integration tests started

**Hands-on Total:** 62 min (34%)

**End of Week 5 Assignment:** Distribute Sub-agents pre-reading + Visual Logic Map (for Group C presentation)

---

## Week 6: Sub-agents & Final Integration (3 Hours)

**Theme:** Group C teaches Sub-agents (Manager-Worker pattern); instructor runs Full Observability Stack on Podcast Skill; teams finalize integration

| Time | Lesson | Duration | Type | Topic |
|------|--------|----------|------|-------|
| 00:00 – 00:06 | 6.1 | 6 min | Stand-up | **Weekly Stand-up** — Integration status check |
| 00:06 – 00:36 | 6.2 | 30 min | Student-Led | **Group C Presentation: Sub-agents** (Manager-Worker pattern; delegation; `.github/copilot-instructions.md`) |
| 00:36 – 00:51 | 6.3 | 15 min | Discussion | **Q&A & Class Discussion** — Manager-Worker patterns in capstones |
| 00:51 – 01:01 | — | 10 min | Buffer | **Instructor Demo Buffer** |
| 01:01 – 01:31 | 6.4 | 30 min | Demo | **Instructor Demo: Full Observability Stack** — `/scout` → `/review` → `/trace` on the integrated Podcast Skill |
| 01:31 – 01:37 | 6.5 | 6 min | Stand-up | **Mid-Session Stand-up** — Final integration blockers |
| 01:37 – 02:50 | 6.6 | 73 min | Hands-on | **Final Integration Sprint:** Connect Skill A → Skill B; run full observability stack; triage landmines; verify Happy Path; draft README |
| 02:50 – 03:00 | 6.7 | 10 min | Gate | **Integration Gate Check** |

### Lesson 6.4 Demo Flow: Full Observability Stack (30 min)

| Phase | Time | Command | Metaphor | Teaching Moment |
|-------|------|---------|----------|-----------------|
| 1. Recap | 0:00–0:02 | — | — | "We have a working, integrated skill. Now we ensure it's transparent and compliant." |
| 2. `/scout` | 0:02–0:08 | `/scout` | 🗺️ The Cartographer | "Before we audit, we need a map." |
| 3. `/review` | 0:08–0:18 | `/review` | ⚖️ The Auditor | **Consulting Moment:** "The best way to manage an AI intern is with an AI supervisor." |
| 4. `/trace` | 0:18–0:28 | `/trace` | 🔍 The Investigator | "Now we reveal WHY decisions were made — and what could break." |
| 5. Wrap-up | 0:28–0:30 | — | — | "This is your pre-flight checklist before every demo." |

**Gate 6 Criteria:**
- Happy Path working end-to-end
- All skills integrated (Skill A → Skill B data flow verified)
- `/review` audit completed on all skills (no critical violations)
- `/trace` run; landmines documented in `DEBT.md` or resolved
- README.md draft started

**Key Artifacts:** Integrated capstone (Happy Path functional); `DEBT.md`; `ARCHITECTURE.md`; README.md draft; `/review` audit results

**Hands-on Total:** 73 min (40%)

**End of Week 6 Assignment:** Complete README.md; prepare demo script for dress rehearsal

---

## Week 7: Dress Rehearsal (3 Hours)

**Theme:** Full end-to-end run-through; structured peer feedback; final polish before Demo Day

| Time | Lesson | Duration | Type | Topic |
|------|--------|----------|------|-------|
| 00:00 – 00:15 | 7.1 | 15 min | Stand-up | **Pre-Flight Check** — Feature freeze confirmation; demo readiness |
| 00:15 – 00:30 | 7.2 | 15 min | Lecture | **Demo Day Expectations** — Format, timing, Q&A handling, rubric review |
| 00:30 – 01:45 | 7.3 | 75 min | Rehearsal | **Team Dress Rehearsals** (25 min per team: 5 min presentation + 10 min demo + 10 min Q&A) |
| 01:45 – 02:15 | 7.4 | 30 min | Feedback | **Structured Peer Feedback Session** — Teams use rubric to evaluate each other |
| 02:15 – 02:50 | 7.5 | 35 min | Hands-on | **Final Polish Sprint** — Address critical feedback; fix blockers |
| 02:50 – 03:00 | 7.6 | 10 min | Gate | **Pre-Flight Gate Check** |

### Structured Peer Feedback Rubric

| Criterion | Weight | 1 (Needs Work) | 3 (Acceptable) | 5 (Excellent) |
|-----------|--------|----------------|----------------|---------------|
| **Spec Compliance** | 30% | Demo doesn't match spec | Most spec requirements shown | All spec requirements demonstrated |
| **UI/UX Clarity** | 20% | Confusing flow; hard to follow | Understandable with some gaps | Clear, intuitive, professional |
| **Edge Case Handling** | 20% | No edge cases addressed | Some edge cases handled | Graceful handling of key edge cases |
| **Presentation Flow** | 15% | Disorganized; over time | Logical flow; minor timing issues | Smooth, confident, within time |
| **Q&A Readiness** | 15% | Unable to answer questions | Adequate answers | Confident, knowledgeable responses |

**Gate 7 (Pre-Flight) Criteria:**

| Checkpoint | Owner |
|------------|-------|
| **Feature Freeze:** Happy Path 100% functional and locked | Team |
| **Edge Case Mitigation:** Evidence that Edge Case Attack has been addressed | Team |
| **Documentation Audit:** README.md clear enough for a "stranger" to install and run | PM |
| **Demo Script:** Rehearsed and timed (within 10 min) | Team |
| **Handoff Document:** Draft complete | PM |
| **Peer Feedback:** Critical issues from feedback session addressed | Team |

**Key Artifacts:** Rehearsed demo; peer feedback incorporated; README.md finalized; HANDOFF.md draft

**Hands-on Total:** 35 min (19%) — *Lower due to rehearsal focus*

---

## Week 8: Final Showcase (2 Hours)

**Theme:** Capstone demonstrations; final handoff; course celebration

| Time | Lesson | Duration | Type | Topic |
|------|--------|----------|------|-------|
| 00:00 – 00:10 | 8.1 | 10 min | Opening | **Opening Speakers** — Welcome, context setting, acknowledgments |
| 00:10 – 00:35 | 8.2 | 25 min | Demo | **Team 1 Capstone Demo** (5 min presentation + 10 min demo + 10 min Q&A) |
| 00:35 – 01:00 | 8.3 | 25 min | Demo | **Team 2 Capstone Demo** (5 min presentation + 10 min demo + 10 min Q&A) |
| 01:00 – 01:25 | 8.4 | 25 min | Demo | **Team 3 Capstone Demo** (5 min presentation + 10 min demo + 10 min Q&A) |
| 01:25 – 01:35 | 8.5 | 10 min | Handoff | **Handoff Document Highlights** — PM presents sustainability plan |
| 01:35 – 01:50 | 8.6 | 15 min | Closing | **Closing Speakers** — Reflections, lessons learned, next steps |
| 01:50 – 02:00 | 8.7 | 10 min | Celebration | **Wrap-up & Celebration** |

**Gate 8 (Final Mile) Criteria:**

| Checkpoint | Owner |
|------------|-------|
| **Happy Path Demo:** Working end-to-end demonstration | Team |
| **README.md:** Complete and client-ready | PM |
| **HANDOFF.md:** Complete sustainability guide | PM |
| **All SDD Artifacts Committed:** spec.md, constitution.md, plan.md, interface-spec.md, tasks.md | Team |
| **Presentation Delivered:** Within time limit; Q&A handled professionally | Team |

**Key Artifacts:** Final capstone demo; README.md; HANDOFF.md; complete SDD artifact portfolio

**Note:** Schedule accommodates 3 teams. For additional teams, extend showcase time accordingly (25 min per team).

---

## Summary: Student-Led Presentation Topics

| Week | Group | Topic | Key Concepts | Duration |
|------|-------|-------|--------------|----------|
| **4** | Group A | **Agentic Skills** | Prompts + Code + Recipes; `.github/skills/` structure; `/review` | 30 min |
| **5** | Group B | **Hooks & Guardrails** | Pre-commit hooks; `ruff` linting; spec-checking; observability with `/review` | 30 min |
| **6** | Group C | **Sub-agents** | Manager-Worker pattern; delegation; `.github/copilot-instructions.md` | 30 min |

---

## Summary: Consulting Moments (Podcast Skill Progression)

| Week | Lesson | Focus | Tool/Pattern | What Students Learn |
|------|--------|-------|--------------|---------------------|
| **4** | 4.4 | Task Decomposition | `/speckit.tasks`, `/speckit.analyze` | Transforming a plan into atomic, testable steps; verifying spec alignment before building |
| **5** | 5.4 | Codebase Mapping + Audit | `/scout`, `/review` | Generating architecture maps; auditing code against the Holy Trinity (spec, constitution, plan) |
| **6** | 6.4 | Full Observability Stack | `/scout`, `/review`, `/trace` | Pre-flight checklist: map → audit → trace decisions; catching drift before Demo Day |

---

## Summary: Key Artifacts by Week

| Week | PM Artifacts | Skill Owner Artifacts |
|------|--------------|----------------------|
| **1** | Draft `spec.md` | Environment verified; contributed to spec |
| **2** | Refined `spec.md`, `constitution.md` | Contributed to constitution; identified skill boundaries |
| **3** | `plan.md` (with Demo Scope, Edge Cases) | Skill-level planning begun |
| **4** | `AUDIT.md` (Integration Audit) | Skill-level `tasks.md` (with Black-Box Test Tables) |
| **5** | Integration in progress; `ARCHITECTURE.md` (from `/scout`) | Skills pass `/review` audit |
| **6** | Integration complete; `DEBT.md`; README.md draft; full observability stack run | Skills integrated; `/review` + `/trace` completed |
| **7** | README.md finalized; HANDOFF.md draft | Demo rehearsed; peer feedback incorporated |
| **8** | HANDOFF.md finalized | Demo delivered |

---

## Summary: Gate Criteria by Week

| Week | Gate Name | Key Criteria |
|------|-----------|--------------|
| **1** | Environment Gate | VS Code Insiders + Copilot working; draft `spec.md` committed; student can explain "context drift" |
| **2** | Specification Gate | Refined `spec.md` + `constitution.md` committed |
| **3** | Planning Gate | `plan.md` committed with Demo Scope + Edge Cases; skills identified |
| **4** | Task Gate | `tasks.md` committed (3+ tasks/skill); 50%+ Black-Box Test Tables; `AUDIT.md` committed |
| **5** | Skill Gate | Both skills pass `/review` audit; PM integration in progress |
| **6** | Integration Gate | Happy Path working; all skills integrated; `/review` + `/trace` completed; `DEBT.md` updated |
| **7** | Pre-Flight Gate | Feature freeze; peer feedback addressed; README.md finalized; demo rehearsed |
| **8** | Final Mile Gate | Happy Path demo working; README.md + HANDOFF.md complete |

---

## Appendix A: Hands-on Time Summary

| Week | Hands-on Time | Percentage |
|------|---------------|------------|
| 1 | 99 min | 55% |
| 2 | 95 min | 53% |
| 3 | 93 min | 52% |
| 4 | 69 min | 38% |
| 5 | 62 min | 34% |
| 6 | 73 min | 40% |
| 7 | 35 min | 19% |
| 8 | — | — |

**Average (Weeks 1–6):** 82 min (45%)

---

## Appendix B: Pre-Reading Assignments

| Distributed | Topic | For Group | Used In |
|-------------|-------|-----------|---------|
| End of Week 3 | Agentic Skills | Group A | Week 4 Presentation |
| End of Week 4 | Hooks & Guardrails | Group B | Week 5 Presentation |
| End of Week 5 | Sub-agents + Visual Logic Map | Group C | Week 6 Presentation |

---

## Appendix C: Security & Infrastructure Guardrails

These guardrails apply to ALL weeks and ALL artifacts:

### Hard Security Guardrail: API Keys

- API keys MUST be stored in environment variables (`.env` file)
- `.env` MUST be added to `.gitignore`
- NEVER hardcode secrets in source files
- All plans must include Environment Setup section

### Standard Edge Case: LLM Rate Limits

Every AI-powered project must address:

| Edge Case | Severity | Required Mitigation |
|-----------|----------|---------------------|
| LLM rate limit exceeded (429) | 🔴 High | Retry logic with exponential backoff |
| LLM timeout | 🟡 Medium | Timeout handling with graceful message |
| LLM malformed response | 🔴 High | Response validation before parsing |

---

## Appendix D: Capstone Parallels

| Capstone Project | Week 4 Parallel (Scaffolding) | Week 5 Parallel (Observability) | Week 6 Parallel (Code Review) |
|------------------|-------------------------------|--------------------------------|------------------------------|
| **Data Prep Pipeline** | `clean_dataset.py` structure | `"Dropped row 142: Missing 3+ required fields"` | Audit against data quality constitution |
| **Code Generation** | `generate_code.py` structure | `"Classified as 'Medium': 2 loops + 1 conditional"` | Audit against difficulty rubrics |
| **Code Documentation** | `parse_functions.py` structure | `"Identified function at line 45: def keyword + docstring missing"` | Audit against style guide |

---

*End of 8-Week Schedule v7*
