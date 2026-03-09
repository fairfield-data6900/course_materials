# Lesson 3.4 Demo Kit: Plan Triage — Quality Audit

**Course:** AI-Assisted SDD for Business Analysts  
**Session:** Week 3 — Planning Phase  
**Duration:** 25 minutes  
**Type:** Instructor Demo (Quality Audit)  
**Goal:** Model how to stress-test a `plan.md` using structured prompts before committing — catching gaps, Constitution violations, security issues, and edge cases that could derail the demo.

---

## Pre-Demo Setup

### Files Open in VS Code

| Pane | File | Purpose |
|------|------|---------|
| Left | `.specify/specs/001-podcast-skill/plan.md` | The plan to audit (just drafted in 3.2/3.3) |
| Center | `.specify/specs/001-podcast-skill/spec.md` | Cross-reference for requirement coverage |
| Right | `.specify/memory/constitution.md` | Cross-reference for rule compliance |

### Prompts Ready to Paste

| Prompt | Location | When Used |
|--------|----------|-----------|
| Plan Triage Prompt | Appendix A | Part 1 of demo |
| Edge Case Attack Prompt | Appendix B | Part 2 of demo |

### Pre-Demo Checklist

| Item | Status |
|------|--------|
| `plan.md` exists and has content from 3.2/3.3 | ☐ |
| External AI ready (Claude, ChatGPT, or similar) | ☐ |
| Students can see your screen clearly | ☐ |

---

## Instructor Talking Points Card

| Concept | What to Say |
|---------|-------------|
| **Quality Audit Purpose** | "This is your last checkpoint before you start building. Catch drift now, not in Week 5." |
| **AI as Auditor** | "The AI finds gaps. You decide what to do about them. It's a second pair of eyes, not a judge." |
| **Triage = Prioritization** | "Not every flag is critical. We categorize: 🔴 Must Fix, 🟡 Should Address, 🟢 Acceptable Risk." |
| **Security is Non-Negotiable** | "API keys in code = automatic fail. This is a hard guardrail. No exceptions." |
| **Edge Cases = Grenades** | "These are the inputs that will blow up your demo. Find them now, not on stage in front of the client." |
| **LLM Rate Limits** | "Every AI-powered project hits rate limits eventually. Plan for it now, not when your demo freezes." |
| **Known Limitations** | "Some edge cases don't get solved — they get documented. That's a valid outcome." |

---

## Demo Flow: Quality Audit Walkthrough (25 min)

### Part 1: Plan Triage (0:00 – 0:12)

#### Step 1: Context Setting (0:00 – 0:02)

**Narration:**

> "We just created our `plan.md` in the last session. It passed the Constitution Check. But is it actually *complete*? Does it cover everything in the spec? Are there hidden gaps? Are there security issues?"

> "This is where Plan Triage comes in. We're going to run a structured audit using an external AI — a fresh set of eyes that hasn't seen our work before."

---

#### Step 2: Run the Plan Triage Prompt (0:02 – 0:06)

**Action:**

1. Open an external AI (Claude, ChatGPT, or similar)
2. Paste the **Plan Triage Prompt** (Appendix A)
3. Include your `plan.md`, `spec.md`, and `constitution.md` content

**Narration while pasting:**

> "I'm giving the auditor three things: my plan, my spec, and my constitution. Its job is to find mismatches."

> "Notice I'm using an *external* AI — not the same one that helped me write the plan. Fresh context means fresh perspective."

---

#### Step 3: Review the Triage Report (0:06 – 0:10)

**Expected Output Structure:**

The AI should return something like:

```
## Plan Triage Report

### 1. Requirement Coverage
| Spec Requirement | Covered in Plan? | Gap? |
|------------------|------------------|------|
| Parse transcript timestamps | ✅ Phase 1 | — |
| Generate clips ≤60 seconds | ✅ Phase 2 | — |
| LinkedIn post generation | ✅ Phase 3 | — |
| Twitter post generation | ❌ Not found | 🔴 GAP |

### 2. Constitution Compliance
| Rule | Plan Compliance | Issue? |
|------|-----------------|--------|
| Python 3.11 only | ✅ Confirmed | — |
| No external APIs | ✅ Confirmed | — |
| Local file storage | ✅ Confirmed | — |

### 3. Security Compliance (Hard Guardrail)
| Check | Status | Issue? |
|-------|--------|--------|
| API keys use environment variables | ⚠️ Not explicitly stated | 🔴 MUST ADD |
| No hardcoded secrets in plan | ✅ No violations found | — |
| .env file mentioned in setup | ❌ Missing | 🔴 MUST ADD |

### 4. Structural Issues
- 🟡 Phase 2 milestone is not testable ("clips work correctly")
- 🟢 No dependencies stated between Phase 2 and Phase 3

### 5. Summary
- 🔴 Critical: 2 (Twitter post missing; .env setup missing)
- 🟡 Warning: 1 (vague milestone)
- 🟢 Minor: 1 (missing dependency)
```

**Narration while reviewing:**

> "Look at this. The auditor found that Twitter post generation is in my spec but not in my plan. That's a 🔴 Critical gap."

> "But here's the important one: **Security Compliance**. The plan doesn't explicitly mention using environment variables for API keys. Since all our code goes to GitHub, this is a **hard guardrail**. I need to add a setup step that says 'Configure `.env` file with API keys — never hardcode secrets.'"

> "It also flagged a vague milestone: 'clips work correctly.' That's not testable. I need to rewrite it."

**Teaching Moment (Security Guardrail):**

> "Let me be very clear: **API keys in code = automatic fail**. Every plan must include a setup step for environment variables. If the auditor doesn't see it, you add it. No exceptions."

---

#### Step 4: Model How to Address Flags (0:10 – 0:12)

**Action:**

- For the 🔴 Security gap: Add to Phase 0/Setup in `plan.md`:
  ```markdown
  ### Environment Setup
  - Create `.env` file from `.env.example`
  - Configure API keys as environment variables
  - **NEVER hardcode API keys in source files**
  - Add `.env` to `.gitignore`
  ```
- For the 🔴 Coverage gap: Add Twitter post generation to Phase 3
- For the 🟡 Warning: Rewrite the milestone to be testable

**Narration:**

> "I'm not asking the AI to fix these. I'm making the edits myself. The AI found the gaps; I decide how to close them."

> "For the security issue, I'm adding an explicit Environment Setup section. This is now part of every plan you create in this course."

**Teaching Moment:**

> "Triage means prioritization. Not everything needs to be fixed immediately. But security? That's always 🔴 Critical. Always."

---

### Part 2: Edge Case Attack (0:12 – 0:22)

#### Step 1: Transition (0:12 – 0:13)

**Narration:**

> "The plan is now structurally sound and security-compliant. But will it survive contact with reality? What inputs will break it?"

> "This is the Edge Case Attack. We're looking for grenades — the inputs that will blow up our demo."

---

#### Step 2: Run the Edge Case Attack Prompt (0:13 – 0:17)

**Action:**

1. In the same external AI session (or a new one)
2. Paste the **Edge Case Attack Prompt** (Appendix B)
3. Include your `plan.md` and `spec.md` content

**Narration while pasting:**

> "I'm asking the AI to think like a hostile user. What weird, broken, or malicious inputs could someone throw at this tool?"

> "I'm also asking it to consider **infrastructure edge cases** — things like rate limits that aren't about user input but will still break your demo."

---

#### Step 3: Review the Edge Cases (0:17 – 0:20)

**Expected Output Structure:**

```
## Edge Case Attack Report

### Input Edge Cases
| # | Edge Case | Why It's Dangerous | Severity |
|---|-----------|-------------------|----------|
| 1 | Transcript with no timestamps | Parser will fail silently | 🔴 High |
| 2 | Transcript > 10MB | Memory overflow risk | 🟡 Medium |
| 3 | Non-English transcript | Clip extraction may break | 🟡 Medium |
| 4 | Transcript with profanity | Social posts may be inappropriate | 🔴 High |
| 5 | Empty transcript file | Undefined behavior | 🟡 Medium |

### Output Edge Cases
| # | Edge Case | Why It's Dangerous | Severity |
|---|-----------|-------------------|----------|
| 6 | Clip exactly 60 seconds | Boundary condition | 🟢 Low |
| 7 | LinkedIn post > 3000 chars | Platform rejection | 🟡 Medium |

### Infrastructure Edge Cases
| # | Edge Case | Why It's Dangerous | Severity |
|---|-----------|-------------------|----------|
| 8 | LLM rate limit exceeded | API calls fail mid-processing; demo freezes | 🔴 High |
| 9 | LLM timeout (slow response) | User sees hanging UI or partial output | 🟡 Medium |
| 10 | LLM returns malformed JSON | Parser crashes on unexpected format | 🔴 High |

### Recommended Mitigations
1. Add input validation for timestamps (reject if missing)
2. Add file size check (warn if > 5MB)
3. Add content filter for profanity (or flag for human review)
4. **Implement retry logic with exponential backoff for LLM rate limits**
5. **Add timeout handling with graceful degradation message**
6. **Validate LLM response format before parsing**
```

**Narration while reviewing:**

> "Look at #1: 'Transcript with no timestamps.' If someone uploads a plain text transcript without `[00:00]` markers, my parser will fail. That's a grenade."

> "And look at #8: **LLM rate limit exceeded**. This is a standard edge case for *every* AI-powered project. If you're calling an LLM API and you hit the rate limit, your demo freezes. That's embarrassing."

> "The mitigation is clear: implement retry logic with exponential backoff. We'll cover this in the implementation phase, but the *plan* should acknowledge it now."

**Teaching Moment (LLM Rate Limits):**

> "Every project in this course uses AI. Every AI API has rate limits. This edge case should be in *every* Edge Case Attack you run. If you don't see it in the output, add it yourself."

---

#### Step 4: Model How to Handle Edge Cases (0:20 – 0:22)

**Action:**

- For each edge case, decide: **Fix**, **Document**, or **Defer**

| Edge Case | Decision | Rationale |
|-----------|----------|-----------|
| No timestamps | **Fix** — add validation | Demo will fail without this |
| File > 10MB | **Document** — known limitation | Unlikely in demo; note in README |
| Non-English | **Defer** — out of scope | Constitution says English only |
| Profanity | **Fix** — add content filter | High embarrassment risk |
| Empty file | **Fix** — add validation | Easy to implement |
| LLM rate limit | **Fix** — add retry logic | Demo will freeze without this |
| LLM timeout | **Fix** — add timeout handling | User experience issue |
| Malformed JSON | **Fix** — add response validation | Parser crash risk |

**Narration:**

> "Not every edge case gets fixed. Some get documented as known limitations. Some get deferred because they're out of scope."

> "But notice: all three LLM-related edge cases are marked **Fix**. These are infrastructure issues that will break any AI-powered demo. They're non-negotiable."

**Teaching Moment:**

> "Edge Case Attack is about awareness, not perfection. You can't fix everything. But you can know what might break — and you *must* handle the infrastructure issues."

---

### Part 3: Wrap & Transition (0:22 – 0:25)

**Narration:**

> "We've done two things: Plan Triage to catch structural gaps and security issues, and Edge Case Attack to find grenades — including the LLM rate limit issue that affects every AI project."

> "Your turn. In the next session, you'll run both prompts on your own `plan.md`. You'll also get a third prompt — Demo vs. Future Filter — to help you prioritize what to build now versus what to document for later."

> "Goal: By the end of 3.5, your plan should be audit-clean, security-compliant, and grenade-aware."

---

## Instructor Cheat Sheet: Troubleshooting

| Issue | Quick Fix |
|-------|-----------|
| **Triage returns no gaps** | Either the plan is solid, or the prompt needs more context. Ask: "Did you include the full spec?" |
| **Security check not flagged** | Add it manually. Say: "This is a hard guardrail. If the auditor missed it, you catch it." |
| **Too many 🔴 Critical flags** | Prioritize. Ask: "Which one will break the demo? Fix that first." |
| **LLM rate limit not in edge cases** | Add it manually. Say: "This is a standard edge case for all AI projects." |
| **Edge cases feel overwhelming** | Remind: "You don't fix all of them. You *know* about them. Document and move on." |
| **Students want AI to fix the plan** | Redirect: "The AI finds gaps. You decide how to close them. That's the Verification Ritual." |
| **External AI not available** | Use Copilot Chat as fallback, but note: "Fresh context is better for audits." |

---

## Key Phrases to Repeat

| Phrase | When to Use |
|--------|-------------|
| "This is your last checkpoint before building." | Opening |
| "API keys in code = automatic fail." | When reviewing Security Compliance |
| "The AI finds gaps. You decide how to close them." | After reviewing Triage Report |
| "Triage means prioritization. Not everything is 🔴." | When categorizing flags |
| "Edge cases are grenades. Find them now, not on stage." | Opening Edge Case Attack |
| "Every AI project hits rate limits. Plan for it." | When reviewing LLM edge cases |
| "You can't fix everything. But you can know what might break." | Closing Edge Case Attack |

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

## Appendix C: Demo vs. Future Filter Prompt (For Lesson 3.5 Use)

*This prompt is NOT used in the 3.4 demo. Provide it to students for use in the 3.5 hands-on session.*

```
You are a Product Manager helping prioritize features for a demo.

## Your Task
Review the provided `plan.md` and categorize each feature/phase into:
- **Tier 1 (Demo)** — Must be working for the live demo
- **Tier 2 (Future)** — Documented but not built; can be shown as "roadmap"

## Prioritization Criteria
Tier 1 (Demo) if:
- It's part of the "Happy Path" — the main use case
- The demo will fail or look incomplete without it
- It's explicitly required by the spec's primary user story
- It's a security or infrastructure requirement (e.g., .env setup, rate limit handling)

Tier 2 (Future) if:
- It's an edge case handler (except LLM rate limits — those are Tier 1)
- It's a "nice to have" enhancement
- It's complex and not essential for the core demo
- It can be described as "in a production version, we would also..."

## Input Documents

### plan.md
[PASTE YOUR PLAN.MD CONTENT HERE]

### spec.md (optional, for context)
[PASTE YOUR SPEC.MD CONTENT HERE]

## Output Format

### Tier 1: Demo (Must Build)
| Feature/Phase | Why It's Tier 1 |
|---------------|-----------------|
| [feature] | [rationale] |
| Environment setup (.env) | Security requirement — code goes to GitHub |
| LLM rate limit handling | Infrastructure requirement — demo will freeze without it |

### Tier 2: Future (Document Only)
| Feature/Phase | Why It's Tier 2 | How to Present in Demo |
|---------------|-----------------|------------------------|
| [feature] | [rationale] | "In production, we would also..." |

### Recommended Demo Script Outline
Based on Tier 1 features, suggest a 3-5 step demo flow:
1. [Step 1: Show input]
2. [Step 2: Run tool]
3. [Step 3: Show output]
...

### Risk Flag
If any Tier 1 feature seems too complex to complete, flag it:
- ⚠️ [Feature] — [Why it's risky] — Consider simplifying or moving to Tier 2
```

---

## Transition to Lesson 3.5

> "You've seen me run Plan Triage and Edge Case Attack on the Podcast Skill plan.
>
> Now it's your turn. In the next session, you'll:
> 1. Run the **Plan Triage Prompt** on your own `plan.md` — including the security check
> 2. Run the **Edge Case Attack Prompt** to find your grenades — including LLM rate limits
> 3. Run the **Demo vs. Future Filter Prompt** to prioritize what to build
>
> By the end of 3.5, your plan should be:
> - ✅ Audit-clean (no 🔴 Critical gaps)
> - ✅ Security-compliant (API keys in `.env`, not in code)
> - ✅ Grenade-aware (edge cases documented, LLM rate limits addressed)
> - ✅ Prioritized (Tier 1 vs. Tier 2 clear)
>
> Then we commit and move to the Planning Gate Check."

---

*End of Lesson 3.4 Demo Kit*
