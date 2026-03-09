# Lesson 3.2 Demo Kit: Implementation Planning with `/speckit.plan`

**Course:** AI-Assisted SDD for Business Analysts  
**Session:** Week 3 — Planning Phase  
**Duration:** 30 minutes  
**Type:** Live Demo (talk-through, no formal slides)  
**Goal:** Demonstrate how to generate a template-aligned `plan.md` using `/speckit.plan`, walking through each section of the official `plan-template.md`.

---

## Pre-Demo Setup

### Files Open in VS Code (3-Pane Layout)

| Pane | File | Purpose |
|------|------|---------|
| Left | `.specify/specs/001-podcast-skill/spec.md` | The "what" — refined in Week 2 |
| Center | `.specify/memory/constitution.md` | The "rules" — drafted in Week 2 |
| Right | `.specify/specs/001-podcast-skill/plan.md` | The "how" — raw template, ready to fill |

### Pre-Demo Checklist

| Item | Status |
|------|--------|
| `plan.md` contains raw `plan-template.md` content | ☐ |
| Terminal visible for `/speckit.plan` command | ☐ |
| Students have their own `spec.md` + `constitution.md` ready | ☐ |

---

## Instructor Talking Points Card

Keep these visible during the demo. Reference them naturally, not as a script.

| Concept | What to Say |
|---------|-------------|
| **Template as Truth** | "We never start from a blank page. The template is the contract for what a valid plan looks like." |
| **The Roadmap Metaphor** | "Spec is the destination. Constitution is the traffic laws. Plan is the GPS route — it tells you the sequence of turns, not every inch of road." |
| **AI Proposes, Human Disposes** | "The AI fills in sections. You verify, edit, and decide. Every field with 'NEEDS CLARIFICATION' is a decision you haven't made yet." |
| **Constitution as Filter** | "Before you commit, cross-check every Technical Context field against your Constitution. If they conflict, the Constitution wins." |
| **Plan ≠ Tasks** | "Today we build the roadmap. Next week we decompose it into atomic tasks with `/speckit.tasks`. Don't jump ahead." |

---

## Demo Flow: Template-Driven Walkthrough (30 min)

### Phase 1: Setup & Context (0:00 – 0:03)

**Action:**
- Show the 3-pane layout
- Point to each file

**Narration:**

> "Here's where we are: We have our Spec — the contract for *what* we're building. We have our Constitution — the rules we must follow. Now we need the Plan — the roadmap for *how* we'll build it."

> "Notice I've already copied the official `plan-template.md` into my feature folder as `plan.md`. This is the same workflow you'll follow: Copy Template → Run Command → Refine Sections."

---

### Phase 2: Header & Metadata (0:03 – 0:05)

**Template Section:**

```markdown
# Implementation Plan: [FEATURE]

**Branch**: `[###-feature-name]` | **Date**: [DATE] | **Spec**: [link]

**Input**: Feature specification from `/specs/[###-feature-name]/spec.md`
```

**Action:**
- Fill in the header fields live:
  - `# Implementation Plan: Podcast Marketing Tool`
  - `**Branch**: 001-podcast-skill`
  - `**Date**: 2026-03-06`
  - `**Spec**: ../spec.md`

**Narration:**

> "Every plan must be traceable. The branch name, date, and spec link tell future-you (and future-AI) exactly what version of the spec this plan was built from."

> "If your spec changes significantly, you may need to regenerate the plan. This metadata makes that decision easy."

---

### Phase 3: Summary (0:05 – 0:10)

**Template Section:**

```markdown
## Summary

[Extract from feature spec: primary requirement + technical approach from research]
```

**Action:**
- Run `/speckit.plan` in Copilot Chat with context:

```text
/speckit.plan

Context:
- spec.md: Podcast Marketing Tool — transcript to social content
- constitution.md: Python 3.11, local files only, no external APIs, clips ≤60 seconds

My preferences as PM:
- Prioritize transcript-to-clips pipeline in Phase 1
- Social post generation (LinkedIn, Twitter) in Phase 2
- De-risk timestamp parsing early — that's the hardest part

Fill in the plan.md template, starting with the Summary section.
```

- Review the generated Summary
- Cross-check against `spec.md`

**Narration:**

> "Watch what happens. The AI reads my spec and constitution, then fills in the Summary."

> "Now I verify: Does this Summary match what's in my spec? If the AI says we're building a 'Video Editor' but the spec says 'Podcast Marketing Tool,' we stop and fix it here."

**Teaching Moment:**

> "A good Summary is 2–3 sentences: what we're building and the high-level technical approach. If it's vague or wrong, your spec is probably still mushy. Fix the spec, then re-run."

---

### Phase 4: Technical Context (0:10 – 0:16)

**Template Section:**

```markdown
## Technical Context

**Language/Version**: [e.g., Python 3.11, Swift 5.9, Rust 1.75 or NEEDS CLARIFICATION]  
**Primary Dependencies**: [e.g., FastAPI, UIKit, LLVM or NEEDS CLARIFICATION]  
**Storage**: [if applicable, e.g., PostgreSQL, CoreData, files or N/A]  
**Testing**: [e.g., pytest, XCTest, cargo test or NEEDS CLARIFICATION]  
**Target Platform**: [e.g., Linux server, iOS 15+, WASM or NEEDS CLARIFICATION]

**Project Type**: [e.g., library/cli/web-service/mobile-app/compiler/desktop-app or NEEDS CLARIFICATION]  
**Performance Goals**: [domain-specific, e.g., 1000 req/s, 10k lines/sec, 60 fps or NEEDS CLARIFICATION]  
**Constraints**: [domain-specific, e.g., <200ms p95, <100MB memory, offline-capable or NEEDS CLARIFICATION]  
**Scale/Scope**: [domain-specific, e.g., 10k users, 1M LOC, 50 screens or NEEDS CLARIFICATION]
```

**Action:**
- Scroll to Technical Context in the generated output
- Walk through each field, cross-checking against `constitution.md`

**Field-by-Field Walkthrough:**

| Field | AI Output | Constitution Check | Verdict |
|-------|-----------|-------------------|---------|
| Language/Version | Python 3.11 | Constitution says Python 3.11 | ✅ Match |
| Primary Dependencies | pandas, FFmpeg | Constitution allows local tools | ✅ Match |
| Storage | Local filesystem | Constitution says "no database" | ✅ Match |
| Testing | pytest | Constitution says pytest | ✅ Match |
| Target Platform | CLI / Local | Constitution says local execution | ✅ Match |

**Narration:**

> "This is where we catch hallucinations. The AI might suggest a library that isn't in our Constitution, or propose cloud storage when we said 'local files only.'"

> "I'm going field by field: Language — Python 3.11, matches Constitution. Dependencies — pandas and FFmpeg, both allowed. Storage — local filesystem, correct."

> "If any field says 'NEEDS CLARIFICATION,' that's a decision I haven't made yet. I either make it now or flag it for the team."

**Live Edit (if needed):**

> "The AI suggested 'requests' library here, but our Constitution says 'no external APIs.' I'm deleting that and noting 'local processing only.'"

---

### Phase 5: Constitution Check (0:16 – 0:19)

**Template Section:**

```markdown
## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

[Gates determined based on constitution file]
```

**Action:**
- Point to the GATE note
- Verbally mark the check as PASS or FAIL
- Fill in the section:

```markdown
## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

**Status: PASS**

| Rule | Plan Compliance |
|------|-----------------|
| Python 3.11 only | ✅ Confirmed in Technical Context |
| No external APIs | ✅ All processing is local |
| Clips ≤ 60 seconds | ✅ Constraint noted in spec |
| Local file storage | ✅ No database proposed |
```

**Narration:**

> "This is the most important section of the demo. The Constitution Check is a formal gate."

> "I'm looking at my Constitution — specifically Tech Stack, Out of Scope, and Security — and verifying the plan doesn't violate any of them."

> "For our podcast tool, I'm marking this as PASS: tech stack matches, no out-of-scope features, security rules honored."

**Teaching Moment:**

> "If this check fails, you don't proceed. Fix the plan first. A plan that violates your own rules is worse than no plan at all."

---

### Phase 6: Project Structure (0:19 – 0:25)

**Template Section (Documentation):**

```markdown
## Project Structure

### Documentation (this feature)

specs/[###-feature]/
├── plan.md              # This file (/speckit.plan command output)
├── research.md          # Phase 0 output (/speckit.plan command)
├── data-model.md        # Phase 1 output (/speckit.plan command)
├── quickstart.md        # Phase 1 output (/speckit.plan command)
├── contracts/           # Phase 1 output (/speckit.plan command)
└── tasks.md             # Phase 2 output (/speckit.tasks command - NOT created by /speckit.plan)
```

**Action:**
- Show the documentation tree
- Emphasize the lifecycle

**Narration:**

> "This tree shows the documentation lifecycle for your feature. Today we're creating `plan.md`. Over time, we'll add `research.md`, `data-model.md`, and `quickstart.md`."

> "Notice: `tasks.md` comes from `/speckit.tasks`, not from `/speckit.plan`. That's next week. Don't jump ahead."

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

# [REMOVE IF UNUSED] Option 2: Web application (when "frontend" + "backend" detected)
...

# [REMOVE IF UNUSED] Option 3: Mobile + API (when "iOS/Android" detected)
...
```

**Action:**
- Delete Options 2 and 3 live (they don't apply)
- Keep and customize Option 1:

```markdown
### Source Code (repository root)

src/
├── models/          # Data structures (Clip, Post, Transcript)
├── services/        # Core logic (parser, extractor, generator)
├── cli/             # Command-line interface
└── lib/             # Shared utilities

tests/
├── contract/        # Black-box tests against spec
├── integration/     # End-to-end pipeline tests
└── unit/            # Function-level tests
```

- Fill in the Structure Decision:

```markdown
**Structure Decision**: Single-project layout using `src/` + `tests/` as shown above. 
This is a CLI tool with no web or mobile components.
```

**Narration:**

> "The template gives us options. As the PM, I'm making the decision: we're using the single-project layout."

> "I'm deleting Options 2 and 3 — they don't apply to our CLI tool. Now there's exactly one truth about where code lives."

> "I'm also filling in the Structure Decision field so future-me (and the AI) knows why I chose this layout."

**Teaching Moment:**

> "This section tells `/speckit.implement` where to put code later. If you skip this, the AI will guess — and it will guess wrong."

---

### Phase 7: Complexity Tracking (0:25 – 0:27)

**Template Section:**

```markdown
## Complexity Tracking

> **Fill ONLY if Constitution Check has violations that must be justified**

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
| [e.g., 4th project] | [current need] | [why 3 projects insufficient] |
```

**Action:**
- Scroll to this section
- Leave it empty for the demo

**Narration:**

> "Most of you will leave this section empty during the course. It's only for justified exceptions."

> "If you ever need to break a Constitution rule — like adding a 4th sub-project or using a banned library — you document it here with a clear justification."

> "For our podcast tool, we have no violations, so this stays empty. That's a good sign."

---

### Phase 8: Commit & Transition (0:27 – 0:30)

**Action:**
- Save `plan.md`
- Run git commands:

```bash
git add .specify/specs/001-podcast-skill/plan.md
git commit -m "Add implementation plan for podcast skill (template-aligned)"
```

**Narration:**

> "The plan is now a versioned artifact. It's traceable, it's Constitution-compliant, and it's structured for the next phase."

> "Your turn. In the next 45 minutes, you'll do exactly the same for your capstone: Copy Template → Run `/speckit.plan` → Refine each section → Commit."

---

## Transition to Lesson 3.3

> "You've seen me do it. Now it's your turn.
>
> 1. Copy `plan-template.md` into your feature folder as `plan.md`
> 2. Open your `spec.md` and `constitution.md` side by side
> 3. Run `/speckit.plan` with your PM preferences
> 4. Walk through each section — verify Technical Context against your Constitution
> 5. Mark your Constitution Check as PASS (or fix violations first)
> 6. Choose and document your Project Structure
> 7. Commit
>
> PM drives. Team contributes to decisions. You have 45 minutes."

---

## Instructor Cheat Sheet: Troubleshooting

| Issue | Quick Fix |
|-------|-----------|
| AI generates vague Summary | Spec is probably vague. Ask: "What exactly does this tool do? What are the inputs and outputs?" |
| Technical Context has "NEEDS CLARIFICATION" | That's a decision gap. Either make the decision now or flag it for team discussion. |
| AI proposes tech not in Constitution | Edit it out. Say: "The Constitution wins. Fix the plan." |
| Constitution Check fails | Do not proceed. Fix the plan first, then re-check. |
| Student skips Project Structure decision | Stop them. "Where will your code live? If you don't decide, the AI will guess wrong." |
| Student wants to fill Complexity Tracking | Ask: "Are you breaking a Constitution rule? If not, leave it empty." |
| Plan looks good but student hasn't committed | Remind: "An uncommitted plan doesn't exist. Commit it." |

---

## Key Phrases to Repeat

| Phrase | When to Use |
|--------|-------------|
| "Copy Template → Run Command → Refine Sections" | Opening and closing |
| "The Constitution wins. Fix the plan." | When Technical Context conflicts with Constitution |
| "A plan that violates your own rules is worse than no plan." | When explaining Constitution Check |
| "Delete unused options so there's one truth." | When editing Project Structure |
| "Tasks come next week. Don't jump ahead." | When students ask about `tasks.md` |
| "An uncommitted plan doesn't exist." | When wrapping up |

---

## Appendix A: Sample `/speckit.plan` Prompt

```text
/speckit.plan

Context:
- spec.md: [Feature name] — [one-line description]
- constitution.md: [Key constraints: language, dependencies, storage, security]

My preferences as PM:
- [Priority 1: What should be built first?]
- [Priority 2: What can wait?]
- [Risk: What's the hardest part to de-risk early?]

Goal:
Fill in the plan.md template with:
- Summary (2–3 sentences)
- Technical Context (all fields, mark NEEDS CLARIFICATION if unknown)
- Constitution Check (list rules and compliance status)
- Project Structure (recommend one option; I'll finalize)
```

---

## Appendix B: Annotated Plan Template (Student Reference)

Use this to self-check your `plan.md` before committing.

---

### Header

```markdown
# Implementation Plan: [FEATURE]

**Branch**: `[###-feature-name]` | **Date**: [DATE] | **Spec**: [link]
```

| Field | What "Good" Looks Like |
|-------|------------------------|
| Feature Name | Matches your spec title exactly |
| Branch | Follows naming convention (e.g., `001-feature-name`) |
| Date | Today's date (when plan was created/updated) |
| Spec Link | Relative path to your `spec.md` |

---

### Summary

```markdown
## Summary

[Extract from feature spec: primary requirement + technical approach from research]
```

| Criterion | ✅ Good | ❌ Bad |
|-----------|---------|--------|
| Length | 2–3 sentences | A full paragraph or single word |
| Content | Primary requirement + technical approach | Vague ("build a tool") or off-topic |
| Traceability | Clearly derived from `spec.md` | Introduces new requirements not in spec |

**Example (Good):**
> "Build a CLI tool that processes podcast transcripts to generate social media content. Uses Python 3.11 with local file processing. Outputs include timestamped clips (≤60 sec) and platform-specific posts (LinkedIn, Twitter)."

**Example (Bad):**
> "Make a marketing thing."

---

### Technical Context

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

| Field | Must Match | Red Flag |
|-------|------------|----------|
| Language/Version | Constitution Tech Stack | Different version or language |
| Primary Dependencies | Constitution allowed libraries | Library not in Constitution |
| Storage | Constitution storage rules | Database when Constitution says "files only" |
| Testing | Constitution testing framework | Different framework or "TBD" |
| Target Platform | Constitution deployment target | Cloud when Constitution says "local" |

**Rule:** Every field should either match your Constitution or be marked `NEEDS CLARIFICATION`. No surprises.

---

### Constitution Check

```markdown
## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

**Status: [PASS / FAIL]**

| Rule | Plan Compliance |
|------|-----------------|
| [Rule from Constitution] | ✅ / ❌ [How plan complies or violates] |
```

| Status | What It Means | Next Step |
|--------|---------------|-----------|
| **PASS** | All Constitution rules are respected | Proceed to Project Structure |
| **FAIL** | One or more violations detected | Fix the plan, then re-check |

**This is a gate.** Do not proceed with a FAIL status.

---

### Project Structure — Documentation

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

| File | Created By | When |
|------|------------|------|
| `plan.md` | `/speckit.plan` | Week 3 (today) |
| `research.md` | `/speckit.plan` | Later phases |
| `data-model.md` | `/speckit.plan` | Later phases |
| `quickstart.md` | `/speckit.plan` | Later phases |
| `contracts/` | `/speckit.plan` | Later phases |
| `tasks.md` | `/speckit.tasks` | Week 4 |

**Note:** `tasks.md` is NOT created by `/speckit.plan`. Don't try to fill it in today.

---

### Project Structure — Source Code

```markdown
### Source Code (repository root)

# Choose ONE option and delete the others

# Option 1: Single project (DEFAULT)
src/
├── models/
├── services/
├── cli/
└── lib/

tests/
├── contract/
├── integration/
└── unit/

**Structure Decision**: [Document your choice and why]
```

| Criterion | ✅ Good | ❌ Bad |
|-----------|---------|--------|
| Options | Only ONE remains; others deleted | Multiple options still present |
| Customization | Paths reflect your actual project | Generic placeholders unchanged |
| Structure Decision | Filled in with rationale | Empty or "TBD" |

**Rule:** Delete unused options. There should be exactly one truth about where code lives.

---

### Complexity Tracking

```markdown
## Complexity Tracking

> **Fill ONLY if Constitution Check has violations that must be justified**

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
```

| When to Fill | When to Leave Empty |
|--------------|---------------------|
| You're intentionally breaking a Constitution rule | No violations (most common) |
| You're adding unusual complexity with justification | Standard project structure |

**Default:** Leave empty unless you have a justified exception.

---

### Pre-Commit Checklist

Before running `git commit`, verify:

| Check | ✅ |
|-------|---|
| Header metadata is complete (Branch, Date, Spec link) | ☐ |
| Summary matches `spec.md` (2–3 sentences) | ☐ |
| Technical Context fields verified against `constitution.md` | ☐ |
| Constitution Check marked as **PASS** | ☐ |
| Project Structure has ONE option (others deleted) | ☐ |
| Structure Decision is filled in | ☐ |
| Complexity Tracking is empty (or justified) | ☐ |

**If any check fails, fix it before committing.**

---

*End of Lesson 3.2 Demo Kit*
