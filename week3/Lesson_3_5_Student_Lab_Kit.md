# Lesson 3.5 Student Lab Kit: Plan Refinement & Triage

**Course:** AI-Assisted SDD for Business Analysts  
**Session:** Week 3 — Planning Phase  
**Duration:** 43 minutes  
**Type:** Team-based Hands-on  
**Goal:** Stress-test your `plan.md` using structured prompts, identify edge cases, and prioritize features using the Demo vs. Future Filter — grounded in your client interview notes.

---

## Learning Objectives

By the end of this session, you will be able to:

- Run a structured Plan Triage audit to catch gaps and security issues
- Identify edge cases (including LLM rate limits) that could break your demo
- Prioritize features into Tier 1 (Demo) vs. Tier 2 (Future) based on client needs
- Update your `plan.md` with triage notes, edge cases, and tier assignments
- Commit a refined, audit-clean plan ready for Gate 3

---

## Team Roles

| Role | Person | Responsibility |
|------|--------|----------------|
| **Driver (PM)** | __________ | Runs prompts; makes final edits to `plan.md` |
| **Triage Lead** | __________ | Focuses on Plan Triage; tracks 🔴/🟡/🟢 flags |
| **Edge Case Hunter** | __________ | Focuses on Edge Case Attack; documents grenades |

*All team members participate in Demo vs. Future Filter discussion — this requires client context that the whole team should contribute.*

---

## Pre-Lab Checklist

Before you begin, verify:

| Item | ✅ |
|------|---|
| `plan.md` exists (from Lesson 3.3) | ☐ |
| `spec.md` accessible | ☐ |
| `constitution.md` accessible | ☐ |
| **Client interview notes / discovery findings** accessible | ☐ |
| External AI ready (Claude, ChatGPT, or similar) | ☐ |
| VS Code open with your project | ☐ |

---

## The Workflow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   PLAN TRIAGE    →    EDGE CASE ATTACK    →    DEMO vs. FUTURE    →  COMMIT│
│                                                                             │
│   Find gaps &         Find grenades            Prioritize with        Update│
│   security issues     (incl. LLM limits)       client context         plan  │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Phase-by-Phase Instructions

### Phase 1: Setup & Role Assignment (0:00 – 0:03)

**Action:**

1. Assign team roles (Driver, Triage Lead, Edge Case Hunter)
2. Open your `plan.md`, `spec.md`, and `constitution.md`
3. **Gather your client interview notes** — you'll need these for Phase 4

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Roles assigned | ☐ |
| All three SDD files accessible | ☐ |
| Client interview notes ready | ☐ |

---

### Phase 2: Plan Triage (0:03 – 0:15)

**Goal:** Audit your `plan.md` for gaps, Constitution violations, and security issues.

**Action:**

1. Open an external AI (Claude, ChatGPT, or similar)
2. Copy the **Plan Triage Prompt** (Appendix A below)
3. Paste your `plan.md`, `spec.md`, and `constitution.md` content into the prompt
4. Run the prompt and review the Triage Report

**What to Look For:**

| Section | Key Questions |
|---------|---------------|
| **Requirement Coverage** | Are all spec requirements covered in the plan? |
| **Constitution Compliance** | Does the plan follow all Constitution rules? |
| **Security Compliance** | Are API keys handled via `.env`? Is `.gitignore` set up? |
| **Structural Issues** | Are milestones testable? Are dependencies clear? |

**Triage Lead Worksheet:**

| Flag | Severity | Description | Action Needed |
|------|----------|-------------|---------------|
| | 🔴 / 🟡 / 🟢 | | |
| | 🔴 / 🟡 / 🟢 | | |
| | 🔴 / 🟡 / 🟢 | | |
| | 🔴 / 🟡 / 🟢 | | |

**Hard Guardrail Check:**

| Security Item | Status | Action |
|---------------|--------|--------|
| API keys use `.env` (not hardcoded) | ✅ / ❌ | |
| `.env` mentioned in setup | ✅ / ❌ | |
| `.env` added to `.gitignore` | ✅ / ❌ | |

⚠️ **If any security item is ❌, fix it before proceeding. API keys in code = automatic fail.**

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Plan Triage Prompt executed | ☐ |
| All 🔴 Critical flags documented | ☐ |
| Security Compliance verified | ☐ |

---

### Phase 3: Edge Case Attack (0:15 – 0:25)

**Goal:** Find the "grenades" — inputs and conditions that could break your demo.

**Action:**

1. In the same external AI (or a new session)
2. Copy the **Edge Case Attack Prompt** (Appendix B below)
3. Paste your `plan.md` and `spec.md` content
4. Run the prompt and review the Edge Case Report

**What to Look For:**

| Category | Examples |
|----------|----------|
| **Input Edge Cases** | Empty files, malformed data, unexpected formats |
| **Output Edge Cases** | Boundary conditions, platform limits |
| **Infrastructure Edge Cases** | LLM rate limits, timeouts, malformed responses |

**Edge Case Hunter Worksheet:**

| # | Edge Case | Severity | Decision | Notes |
|---|-----------|----------|----------|-------|
| 1 | | 🔴 / 🟡 / 🟢 | Fix / Document / Defer | |
| 2 | | 🔴 / 🟡 / 🟢 | Fix / Document / Defer | |
| 3 | | 🔴 / 🟡 / 🟢 | Fix / Document / Defer | |
| 4 | | 🔴 / 🟡 / 🟢 | Fix / Document / Defer | |
| 5 | | 🔴 / 🟡 / 🟢 | Fix / Document / Defer | |

**Mandatory Edge Cases (Must Be Addressed):**

| Edge Case | Severity | Required Mitigation |
|-----------|----------|---------------------|
| LLM rate limit exceeded (429) | 🔴 High | Retry logic with exponential backoff |
| LLM timeout | 🟡 Medium | Timeout handling with graceful message |
| LLM malformed response | 🔴 High | Response validation before parsing |

⚠️ **If these LLM edge cases are not in your report, add them manually. Every AI project must address these.**

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Edge Case Attack Prompt executed | ☐ |
| At least 5 edge cases documented | ☐ |
| LLM rate limit handling addressed | ☐ |

---

### Phase 4: Demo vs. Future Filter (0:25 – 0:37)

**Goal:** Prioritize features into Tier 1 (must build for demo) vs. Tier 2 (document for future).

**⚠️ IMPORTANT: This phase requires your client interview notes.**

The AI cannot prioritize features without understanding what your client actually needs. Before running this prompt, gather:

- Notes from client interviews or discovery sessions
- Stakeholder requirements or preferences
- Any "must have" vs. "nice to have" distinctions the client mentioned
- What success looks like to the client

**Action:**

1. In the same external AI (or a new session)
2. Copy the **Demo vs. Future Filter Prompt** (Appendix C below)
3. Paste your `plan.md`, `spec.md`, **AND your client interview notes**
4. Run the prompt and review the Tier assignments
5. **Discuss as a team** — do the AI's recommendations match your client's priorities?

**Team Discussion Questions:**

| Question | Your Answer |
|----------|-------------|
| What did the client say is absolutely essential? | |
| What would embarrass us if it didn't work in the demo? | |
| What can we describe as "in production, we would also..."? | |
| Does the AI's Tier 1 list match our client's priorities? | |

**Demo vs. Future Worksheet:**

| Feature/Phase | Tier | Client Evidence | Action |
|---------------|------|-----------------|--------|
| | **Tier 1** / **Tier 2** | "Client said..." | Build / Document |
| | **Tier 1** / **Tier 2** | "Client said..." | Build / Document |
| | **Tier 1** / **Tier 2** | "Client said..." | Build / Document |
| | **Tier 1** / **Tier 2** | "Client said..." | Build / Document |

**Hard Rules (Always Tier 1):**

| Feature | Why It's Always Tier 1 |
|---------|------------------------|
| `.env` setup for API keys | Security — code goes to GitHub |
| LLM rate limit handling | Infrastructure — demo freezes without it |
| Happy Path features | Demo fails without the core flow |

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Client interview notes were included in prompt | ☐ |
| Demo vs. Future Filter Prompt executed | ☐ |
| Tier 1 vs. Tier 2 documented | ☐ |
| Team discussed and validated AI recommendations | ☐ |

---

### Phase 5: Update `plan.md` & Commit (0:37 – 0:43)

**Goal:** Add triage results, edge cases, and tier assignments to your `plan.md`, then commit.

**Action:**

Add the following section to your `plan.md`:

```markdown
## Demo Scope (Tier 1 vs. Tier 2)

### Tier 1: Demo Path (Must Build)
| Feature/Phase | Why It's Tier 1 | Client Evidence |
|---------------|-----------------|-----------------|
| [feature] | [rationale] | [what client said] |
| Environment setup (.env) | Security requirement | — |
| LLM rate limit handling | Infrastructure requirement | — |

### Tier 2: Future Roadmap (Document Only)
| Feature/Phase | Why It's Tier 2 | Demo Script |
|---------------|-----------------|-------------|
| [feature] | [rationale] | "In production, we would also..." |

### Edge Cases Addressed
| Edge Case | Severity | Mitigation | Status |
|-----------|----------|------------|--------|
| [edge case] | 🔴/🟡/🟢 | [mitigation] | Fix / Document / Defer |
| LLM rate limit | 🔴 High | Retry with backoff | Fix |
| LLM timeout | 🟡 Medium | Graceful error message | Fix |

### Triage Notes
- [Any 🔴 Critical issues that were fixed]
- [Any 🟡 Warnings that were addressed]
- [Any decisions made during triage]
```

**Commit:**

```bash
git add .specify/specs/[your-project]/plan.md
git commit -m "docs: finalize plan with triage, edge cases, and demo scope"
git push origin main
```

**Checkpoint:**

| Verify | ✅ |
|--------|---|
| Demo Scope section added to `plan.md` | ☐ |
| Edge Cases section added to `plan.md` | ☐ |
| Triage Notes section added to `plan.md` | ☐ |
| Committed with descriptive message | ☐ |

---

## Success Criteria for Lesson 3.5

| Checkpoint | ✅ |
|------------|---|
| Plan Triage completed — all 🔴 Critical flags addressed | ☐ |
| Security Compliance verified (API keys → `.env`) | ☐ |
| Edge Case Attack completed — at least 5 edge cases documented | ☐ |
| LLM rate limit handling marked as Tier 1 | ☐ |
| Demo vs. Future Filter completed with client context | ☐ |
| Tier 1 vs. Tier 2 documented in `plan.md` | ☐ |
| `plan.md` committed | ☐ |

---

## What's Next?

After this session:

- **Lesson 3.6 (10 min):** Planning Gate Check — verify `plan.md` is committed and complete
- **Gate 3 Criteria:** `plan.md` committed; skills assigned to Skill Owners
- **Week 4:** `/speckit.tasks` — decompose your plan into atomic tasks

**Remember:** Today we stress-tested and prioritized the roadmap. Next week we break it into turn-by-turn directions.

---

## Appendix A: Plan Triage Prompt (Copy-Ready)

```
You are a Quality Auditor reviewing an implementation plan for completeness, compliance, and security.

## Your Task
Audit the provided `plan.md` against the `spec.md` and `constitution.md` to identify:
1. **Requirement Coverage Gaps** — Features in the spec that are missing from the plan
2. **Constitution Violations** — Plan elements that break rules defined in the constitution
3. **Security Compliance (Hard Guardrail)** — API key handling and secrets management
4. **Structural Issues** — Vague milestones, missing dependencies, unclear phases

## Security Guardrail (MANDATORY)
This project's code will be pushed to GitHub. You MUST verify:
- [ ] Plan explicitly states that API keys must be stored in environment variables (`.env` file)
- [ ] Plan includes setup step for `.env` configuration
- [ ] Plan explicitly prohibits hardcoding secrets in source files
- [ ] Plan mentions adding `.env` to `.gitignore`

If ANY of these are missing, flag as 🔴 Critical — Security Violation.

## Input Documents

### plan.md
[PASTE YOUR PLAN.MD CONTENT HERE]

### spec.md
[PASTE YOUR SPEC.MD CONTENT HERE]

### constitution.md
[PASTE YOUR CONSTITUTION.MD CONTENT HERE]

## Output Format

Return a structured report with the following sections:

### 1. Requirement Coverage
| Spec Requirement | Covered in Plan? | Phase | Gap? |
|------------------|------------------|-------|------|
| [requirement] | ✅ / ❌ | [phase #] | 🔴 GAP / — |

### 2. Constitution Compliance
| Rule | Plan Compliance | Issue? |
|------|-----------------|--------|
| [rule from constitution] | ✅ / ❌ | [description if violated] |

### 3. Security Compliance (Hard Guardrail)
| Check | Status | Issue? |
|-------|--------|--------|
| API keys use environment variables | ✅ / ❌ / ⚠️ Not stated | [action needed] |
| No hardcoded secrets in plan | ✅ / ❌ | [action needed] |
| .env file mentioned in setup | ✅ / ❌ | [action needed] |
| .env added to .gitignore | ✅ / ❌ | [action needed] |

**Security Verdict:** PASS / 🔴 FAIL — [summary of issues]

### 4. Structural Issues
List any issues with:
- Vague or untestable milestones
- Missing dependencies between phases
- Unclear scope boundaries
- Phases that are too large or too small

Use severity markers:
- 🔴 Critical — Must fix before proceeding
- 🟡 Warning — Should address soon
- 🟢 Minor — Acceptable risk, document and proceed

### 5. Summary
- 🔴 Critical: [count]
- 🟡 Warning: [count]
- 🟢 Minor: [count]
- **Security Status:** PASS / FAIL

### 6. Recommended Actions
List the top 3–5 actions to improve this plan, in priority order.
Security issues should always be listed first if present.
```

---

## Appendix B: Edge Case Attack Prompt (Copy-Ready)

```
You are a QA Engineer tasked with finding edge cases that could break a software tool.

## Your Task
Review the provided `plan.md` and `spec.md` to identify:
1. **Input Edge Cases** — Unusual, malformed, or malicious inputs that could cause failures
2. **Output Edge Cases** — Boundary conditions or unexpected outputs that could cause problems
3. **Infrastructure Edge Cases** — System-level issues (rate limits, timeouts, API failures)

Think like a hostile user AND a chaotic production environment. What could go wrong?

## Mandatory Edge Case: LLM Rate Limits
This project uses AI/LLM APIs. You MUST include edge cases for:
- [ ] LLM rate limit exceeded (API returns 429 or equivalent)
- [ ] LLM timeout (slow response or no response)
- [ ] LLM returns malformed/unexpected response format
- [ ] LLM returns empty or null response

These are standard edge cases for ALL AI-powered projects.

## Input Documents

### plan.md
[PASTE YOUR PLAN.MD CONTENT HERE]

### spec.md
[PASTE YOUR SPEC.MD CONTENT HERE]

## Output Format

### Input Edge Cases
| # | Edge Case | Why It's Dangerous | Severity |
|---|-----------|-------------------|----------|
| 1 | [description] | [impact] | 🔴 High / 🟡 Medium / 🟢 Low |

### Output Edge Cases
| # | Edge Case | Why It's Dangerous | Severity |
|---|-----------|-------------------|----------|
| 1 | [description] | [impact] | 🔴 High / 🟡 Medium / 🟢 Low |

### Infrastructure Edge Cases (Including LLM Issues)
| # | Edge Case | Why It's Dangerous | Severity |
|---|-----------|-------------------|----------|
| 1 | LLM rate limit exceeded | [impact on this specific project] | 🔴 High |
| 2 | LLM timeout | [impact on this specific project] | 🟡 Medium / 🔴 High |
| 3 | LLM malformed response | [impact on this specific project] | 🔴 High |
| 4 | [other infrastructure issues] | [impact] | [severity] |

### Recommended Mitigations
For each 🔴 High severity edge case, suggest a mitigation:
1. [Edge case] → [Mitigation]

For LLM-related edge cases, always recommend:
- Retry logic with exponential backoff for rate limits
- Timeout handling with graceful degradation
- Response validation before parsing
- Fallback behavior or user-friendly error messages

### Known Limitations (Candidates)
List edge cases that are acceptable to document as "known limitations" rather than fix:
- [Edge case] — [Why it's acceptable to defer]

Note: LLM rate limit handling should NOT be deferred — it must be implemented.
```

---

## Appendix C: Demo vs. Future Filter Prompt (Copy-Ready)

```
You are a Product Manager helping prioritize features for a client demo.

## Your Task
Review the provided `plan.md` and categorize each feature/phase into:
- **Tier 1 (Demo)** — Must be working for the live demo
- **Tier 2 (Future)** — Documented but not built; can be shown as "roadmap"

## IMPORTANT: Client Context Required
You CANNOT prioritize features without understanding the client's actual needs. 
The student MUST provide their client interview notes below.

If no client context is provided, respond with:
"I need your client interview notes to prioritize features. Please provide:
- Who is the primary user/client?
- What problem are they trying to solve?
- What did they say is 'must have' vs. 'nice to have'?
- Any constraints or preferences they mentioned
- What does success look like to them?"

## Prioritization Criteria

**Tier 1 (Demo) if:**
- Client explicitly said it's essential or "must have"
- It's part of the "Happy Path" — the main use case the client described
- The demo will fail or look incomplete without it
- It's a security or infrastructure requirement (e.g., .env setup, rate limit handling)

**Tier 2 (Future) if:**
- Client said it's "nice to have" or "for later"
- It's an edge case handler (except LLM rate limits — those are Tier 1)
- It's a feature the client didn't mention or prioritize
- It can be described as "in a production version, we would also..."

## Input Documents

### plan.md
[PASTE YOUR PLAN.MD CONTENT HERE]

### spec.md (for context)
[PASTE YOUR SPEC.MD CONTENT HERE]

### Client Interview Notes / Discovery Knowledge (REQUIRED)
[PASTE YOUR CLIENT INTERVIEW NOTES HERE]

This should include:
- Who is the primary user/client?
- What problem are they trying to solve?
- What did they say is "must have" vs. "nice to have"?
- Any constraints or preferences they mentioned
- What does success look like to them?

## Output Format

### Client Context Summary
Before prioritizing, summarize what you understood from the client notes:
- **Primary User:** [who]
- **Core Problem:** [what they're trying to solve]
- **Must-Haves (per client):** [list]
- **Nice-to-Haves (per client):** [list]
- **Success Criteria:** [what success looks like]

### Tier 1: Demo (Must Build)
| Feature/Phase | Why It's Tier 1 | Client Evidence |
|---------------|-----------------|-----------------|
| [feature] | [rationale] | "Client said..." or "Infrastructure requirement" |
| Environment setup (.env) | Security requirement — code goes to GitHub | — |
| LLM rate limit handling | Infrastructure requirement — demo will freeze without it | — |

### Tier 2: Future (Document Only)
| Feature/Phase | Why It's Tier 2 | Demo Script |
|---------------|-----------------|-------------|
| [feature] | [rationale] | "In production, we would also..." |

### Recommended Demo Script Outline
Based on Tier 1 features and client priorities, suggest a 3-5 step demo flow:
1. [Step 1: Show input — what the client cares about]
2. [Step 2: Run tool — the core value proposition]
3. [Step 3: Show output — what success looks like to the client]
...

### Risk Flags
If any Tier 1 feature seems too complex to complete, flag it:
- ⚠️ [Feature] — [Why it's risky] — Consider simplifying or moving to Tier 2

### Validation Questions for the Team
Before finalizing, the team should discuss:
1. Does our Tier 1 list match what the client said was essential?
2. Would the client be satisfied with a demo that only includes Tier 1?
3. Are we building what the client needs, or what we think is cool?
```

---

## Troubleshooting

| Issue | Quick Fix |
|-------|-----------|
| **Plan Triage returns no gaps** | Either the plan is solid, or the prompt needs more context. Did you include the full spec? |
| **Security check not flagged** | Add it manually. "API keys in code = automatic fail." |
| **LLM rate limit not in edge cases** | Add it manually. This is mandatory for all AI projects. |
| **Demo vs. Future prompt asks for client notes** | Good! The prompt is working. Provide your client interview notes. |
| **No client interview notes available** | Discuss as a team: What do you *think* the client needs? Document your assumptions and validate later. |
| **AI's Tier 1 doesn't match client priorities** | Override the AI. Your client knowledge is authoritative. |
| **Too many Tier 1 features** | Be ruthless. Ask: "Would the demo fail without this?" If no, move to Tier 2. |

---

## Quick Reference: Tier Definitions

| Tier | Name | Criteria | Action |
|------|------|----------|--------|
| **Tier 1** | Demo Path | Client said "must have"; demo fails without it; security/infrastructure | **Build it** |
| **Tier 2** | Future Roadmap | Client said "nice to have"; not demo-critical; can be stubbed | **Document it** |

**Hard Rules:**
- ✅ `.env` setup for API keys → **Always Tier 1**
- ✅ LLM rate limit handling → **Always Tier 1**
- ✅ Features client called "essential" → **Tier 1**
- ⚠️ Features client didn't mention → **Probably Tier 2**

---

*End of Lesson 3.5 Student Lab Kit*
