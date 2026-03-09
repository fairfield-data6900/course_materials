# Lesson 2.2: The Constitution — Tech Stack, Security Rules, "Out of Scope"

**Course:** AI-Assisted SDD for Business Analysts  
**Session:** Week 2 — Specification Phase  
**Duration:** 25 minutes  
**Goal:** Shift students from *one-off specs* to *project-level governance* by defining a shared `constitution.md` for tech stack, security rules, and out-of-scope boundaries.

---

## Learning Objectives

By the end of this lecture, students will be able to:

1. Explain the purpose of `constitution.md` in the SDD pipeline.
2. Distinguish **global constraints** (Constitution) from **local constraints** (`spec.md`).
3. Define project-wide rules for **tech stack**, **security/compliance**, and **"Out of Scope"** items.
4. Describe how the Constitution prevents **context drift** and "accidental complexity" during later weeks (planning, skills, and code).

---

## Lecture Script

### Opening (0:00 – 0:03) — "The Intern Needs an Employee Handbook"

**[SLIDE 1: The Intern Is Working… But the Rules Are Missing]**

> "Last week, we hired our *Overconfident Intern* and gave them their first contract: `spec.md`.  
> They did the job: you now have a working specification for your capstone.
> 
> But now imagine this:  
> You ask the intern to build a small data pipeline. They pick **three different Python frameworks**, deploy to **whatever cloud they feel like**, and hardcode API keys in the code.  
> 
> Did they 'do the task'? Technically yes.  
> Did they follow your team's standards? Absolutely not.  
> 
> Today is where we fix that. We're going to give the intern an **Employee Handbook** for your project — your `constitution.md`."

**Key Point:** Week 1 gave the intern a *task* (`spec.md`). Week 2 gives them the *rules of the company* (`constitution.md`).

---

### The Problem: Hidden Rules & Repeating Yourself (0:03 – 0:08)

**[SLIDE 2: The Problem — Everyone Has Rules, No One Writes Them Down]**

> "Every real project has rules, written or unwritten:
> 
> - 'We only deploy to **X cloud**.'  
> - 'We never store **PII** in logs.'  
> - 'We always write docs in **plain language**.'  
> 
> In traditional projects, these rules live in people's heads or in random Slack threads.  
> With AI, that's a problem, because:
> 
> - You keep **repeating the same constraints** in every prompt and spec.  
> - You forget one constraint once, and suddenly the AI happily violates it.  
> - New teammates (or future you) have **no idea** what the non-negotiables are.
> 
> This is constraint fatigue. If the rules aren't centralized, the rules will be broken."

**Key Point:** Centralization = consistency. If it applies to *every* task, repeating it in every spec is a smell.

---

### The Solution: `constitution.md` as the Project's Law (0:08 – 0:13)

**[SLIDE 3: `constitution.md` — The Project's Law]**

> "Our solution is a single source of truth called `constitution.md`.
> 
> Think of it as:
> - The **Employee Handbook** for your Overconfident Intern.  
> - The **Project Constitution** that outlives any individual spec.  
> 
> While `spec.md` tells the AI **what to do right now**,  
> `constitution.md` tells the AI **who to be and what lines it must never cross**."

**[SLIDE 4: Global vs. Local Constraints]**

> "We're going to split our instructions into two buckets:
> 
> 1. **Global Constraints (Constitution)** — always true in this project  
>    - Tech stack: 'Use Python 3.11, FastAPI, and PostgreSQL only.'  
>    - Security: 'Never log full emails; mask user IDs.'  
>    - Output rules: 'Always write in plain English, no jargon.'  
>    - Brand voice: 'Concise, skeptical of hype, data-driven.'  
> 
> 2. **Local Constraints (Spec)** — only true for one task or feature  
>    - 'This summary must be under 200 words.'  
>    - 'Include the guest's LinkedIn URL in the output.'  
>    - 'Run on a daily schedule at 6am UTC.'  
> 
> Rule of thumb:  
> **If you'd be annoyed to repeat it 10 times, it probably belongs in the Constitution.**"

**Key Point:** Constitution = "always" rules (global). Spec = "this task" rules (local).

---

### Pillar 1: Tech Stack & Platform Rules (0:13 – 0:17)

**[SLIDE 5: Tech Stack — Guardrails, Not Just Preferences]**

> "Let's start with the **tech stack** section of the Constitution.
> 
> AI will happily:
> - Suggest 5 different libraries for the same problem  
> - Mix frameworks (Django here, Flask there)  
> - Use tools your team can't support
> 
> As the **Knowledgeable Engineer**, you decide:
> 
> - **Approved languages & frameworks**  
>   - e.g., 'Use Python 3.11, FastAPI for APIs, Pandas for data work.'  
> - **Deployment/infra boundaries**  
>   - e.g., 'Deploy to Azure only; no custom servers.'  
> - **Performance or cost constraints** (if relevant)  
>   - e.g., 'Avoid GPU-heavy models; optimize for low cost.'  
> 
> These aren't just preferences. They are **constraints that shape every proposal** the AI makes."

> "When your `constitution.md` clearly states the tech stack:
> - Your `/speckit.plan` in Week 3 becomes dramatically easier.  
> - Skill Owners in Weeks 4–6 don't waste time arguing about frameworks.  
> - The AI stops 'shopping' for random tools and stays inside your lane."

**Key Point:** A clear tech stack in the Constitution prevents the AI from exploring tools your team will never support.

---

### Pillar 2: Security, Privacy & Data Boundaries (0:17 – 0:21)

**[SLIDE 6: Security & Data Rules — The "Never-Ever" List]**

> "Next: **security and data boundaries**.
> 
> This is where the intern is most dangerous:
> 
> - They'll log full API responses that contain PII.  
> - They'll copy sample keys from docs into code.  
> - They'll recommend storing secrets in plain text.
> 
> Your Constitution needs a **'Never-Ever' section**:
> 
> - 'Never store raw user emails or phone numbers in logs.'  
> - 'Never hardcode API keys or secrets in code; use environment variables.'  
> - 'Do not send proprietary data to third-party APIs unless explicitly approved.'  
> - 'When generating examples, use **synthetic or anonymized data only**.'  
> 
> You don't need legal language. You need **plain, enforceable rules** the AI can follow."

> "Remember: the AI is not evil. It's just naive.  
> If you don't write down the boundary, it doesn't know it exists."

**Key Point:** Security rules belong in `constitution.md` so they apply to every spec, every skill, every future teammate.

---

### Pillar 3: "Out of Scope" to Prevent Scope Creep (0:21 – 0:23)

**[SLIDE 7: Out of Scope — What This Project Will NOT Do]**

> "Finally, the most underrated part of a good Constitution:  
> **What this project will NOT do.**
> 
> The Overconfident Intern *loves* to over-deliver:
> - 'While I was at it, I built a notification system…'  
> - 'I added support for 10 more file types…'  
> - 'I refactored your entire pipeline for microservices…'
> 
> That might sound generous, but in real projects it's **scope creep** and **integration risk**.
> 
> In your `constitution.md`, you want a short **Out of Scope** section, like:
> 
> - 'No real-time streaming features in this phase.'  
> - 'No user-level personalization; only aggregate analytics.'  
> - 'No multi-tenant architecture; single-team use only.'  
> - 'No code generation for production deployment (dev-environment only).'"

> "This section protects:
> - Your team's **time** (you don't chase shiny features).  
> - Your **assessment** (Gate 2 is about good specs, not shipping an entire startup).  
> - Your **future self** (you remember what you intentionally decided *not* to take on)."

**Key Point:** Out-of-scope rules keep both humans and AI focused on the actual capstone, not a fantasy product.

---

### The Refinement Loop: Fix the Constitution, Not Just the Output (0:23 – 0:24)

**[SLIDE 8: The Refinement Loop — Update the Handbook]**

> "As you work with your AI intern across Weeks 2–6, you'll notice a pattern:
> 
> 1. **Generate** — The AI proposes a plan, code, or explanation.  
> 2. **Notice a violation** — Wrong tone, risky logging, off-tech-stack suggestion.  
> 3. **Instead of just editing the output**, you:  
>    - Fix this once **in the Constitution** so it doesn't happen again.
> 
> This is the **Refinement Loop**:
> - Don't just clean up the mess.  
> - Update the Employee Handbook so the intern stops making that kind of mess.
> 
> That's how your `constitution.md` grows from a rough draft in Week 2 into a powerful governance artifact by Week 6."

**Key Point:** Every recurring mistake is feedback for `constitution.md`, not just a one-time patch.

---

### Preview & Transition to 2.3 (0:24 – 0:25)

**[SLIDE 9: Your Turn — Drafting `constitution.md`]**

> "You now have three pillars for your Constitution:
> 
> 1. **Tech Stack & Platform Rules** — What tools the intern is allowed to use.  
> 2. **Security & Data Boundaries** — The 'never-ever' list.  
> 3. **Out of Scope** — What this project will *not* attempt.
> 
> In the next block:
> - Your **PM** will lead the first draft of `constitution.md`.  
> - Your team will contribute concrete rules from your own context.  
> 
> You don't have to get it perfect today.  
> You just need a solid **first version** that we can test and refine as we go.
> 
> Let's switch over to the template you'll use for your project and start drafting."

---

## Slide Deck Design

### Slide 1: The Intern Is Working… But the Rules Are Missing

**Visual:**  
- The same "Overconfident Intern" from Week 1, now happily typing at a desk with multiple tools/framework logos floating around (VS Code, random cloud logos, DB icon, etc.) in a chaotic swirl.

**Text:**
- **Headline:** The Intern Is Working… But the Rules Are Missing  
- **Subhead:** Specs gave them tasks. Now they need rules.  
- **Footer:** Today: `constitution.md` — your Employee Handbook.

**Design Notes:**
- Call back explicitly to Week 1 metaphor for continuity.  
- Show productivity + potential chaos visually.

---

### Slide 2: The Problem — Everyone Has Rules, No One Writes Them Down

**Visual:**  
- Two columns:
  - Left: Sticky notes / Slack bubbles with rules like "No PII in logs", "Azure only", "Plain English docs".  
  - Right: A single clean document labeled `constitution.md`.

**Text:**
- **Headline:** The Problem: Hidden Rules & Constraint Fatigue  
- **Bullets:**
  - Rules live in heads and Slack.  
  - You repeat the same constraints in every prompt.  
  - Forget once → AI happily breaks them.

**Design Notes:**
- Use faded/overlapping sticky notes to convey chaos.  
- Highlight `constitution.md` as the calming center.

---

### Slide 3: `constitution.md` — The Project's Law

**Visual:**  
- Blueprint/foundation metaphor:
  - Bottom: A solid slab labeled `constitution.md`.  
  - Top: A structure labeled `spec.md`, `plan.md`, `tasks.md`, `skills/…`.

**Text:**
- **Headline:** `constitution.md` — The Project's Law  
- **Bullets:**
  - Defines who the AI is.  
  - Captures non-negotiable rules.  
  - Outlives any single spec or task.

**Design Notes:**
- Emphasize "foundation" visually; other docs sit on top.

---

### Slide 4: Global vs. Local Constraints

**Visual:**  
- A two-column comparison table (similar treatment to "Good Spec vs. Bad Spec" in 1.1).

**Left: Global (Constitution)**  
- "Always use Python 3.11 + FastAPI."  
- "Never log PII."  
- "Always write in plain language."

**Right: Local (Spec)**  
- "This summary ≤ 200 words."  
- "Include guest's LinkedIn URL."  
- "Run job daily at 6am UTC."

**Text:**
- **Headline:** Global vs. Local Constraints  
- **Footer:** If you'd repeat it 10 times, put it in `constitution.md`.

**Design Notes:**
- Color-code: blue for global, green for local.  
- Keep examples short and concrete.

---

### Slide 5: Tech Stack — Guardrails, Not Just Preferences

**Visual:**  
- "Allowed" zone and "Not Allowed" zone:
  - Left: A fenced-in area with a few logos (Python, FastAPI, Postgres).  
  - Right: A pile of random tools outside the fence (crossed out).

**Text:**
- **Headline:** Tech Stack Rules  
- **Bullets:**
  - Approved languages & frameworks  
  - Deployment boundaries  
  - Performance/cost considerations

**Design Notes:**
- Visual should feel like a safe, constrained sandbox.

---

### Slide 6: Security & Data Rules — The "Never-Ever" List

**Visual:**  
- A bold warning list labeled "NEVER-EVER:"
  - Hardcoded keys icon with a red X  
  - Database icon with "PII" stamped and padlock  
  - Log file icon with blurred/anonymized data.

**Text:**
- **Headline:** Security & Data Boundaries  
- **Bullets:**
  - No PII in logs  
  - No hardcoded secrets  
  - No unapproved third-party data sharing

**Design Notes:**
- Use high-contrast colors for "Never" (red, warning symbols) but keep overall slide clean.

---

### Slide 7: Out of Scope — What This Project Will NOT Do

**Visual:**  
- A "Backlog" board with some cards stamped **OUT OF SCOPE** and moved to a greyed-out column.

**Text:**
- **Headline:** Out of Scope  
- **Bullets:**
  - No real-time features in this phase  
  - No multi-tenant architecture  
  - No production deployment automation

**Design Notes:**
- Make "OUT OF SCOPE" visually satisfying — this is a relief, not a punishment.

---

### Slide 8: The Refinement Loop — Update the Handbook

**Visual:**  
- A loop diagram:
  - Generate → Notice issue → Update `constitution.md` → Generate again (improved).

**Text:**
- **Headline:** The Refinement Loop  
- **Subhead:** Don't just fix the output. Fix the rules.  
- **Footer:** Every recurring mistake = a Constitution update.

**Design Notes:**
- Keep the loop simple and readable; highlight `constitution.md` at the "update" step.

---

### Slide 9: Your Turn — Drafting `constitution.md`

**Visual:**  
- A simple markdown document mockup with three headers:
  - `## Tech Stack & Platform Rules`  
  - `## Security & Data Boundaries`  
  - `## Out of Scope`

**Text:**
- **Headline:** Your First `constitution.md`  
- **Bullets:**
  - PM leads the draft  
  - Team contributes rules from your real context  
  - We'll refine as we go

**Design Notes:**
- Make the template look lightweight and approachable — "you can fill this in today."

---

## Appendix A: Key Terms Glossary

| Term | Definition |
|------|------------|
| **Global Constraints** | Project-wide rules captured in `constitution.md` that apply to all specs, skills, and code. |
| **Local Constraints** | Task-specific rules that live in a single `spec.md` or skill-level spec. |
| **Tech Stack Rules** | Approved languages, frameworks, and platforms that the AI should stay within. |
| **Security & Data Boundaries** | Non-negotiable rules about handling secrets, PII, and external APIs. |
| **Out of Scope** | Explicitly excluded features or requirements for this capstone phase. |
| **Refinement Loop** | Process of updating `constitution.md` based on mistakes or friction observed in AI output. |

---

## Appendix B: Pitfall Warnings for Instructor

| Pitfall | Mitigation |
|---------|------------|
| Students dump *everything* into the Constitution (too long, too detailed) | Coach: "Keep it to the **essential global rules**. If it only applies to one feature, move it back into the spec." |
| Students put task-specific requirements (e.g., "daily at 6am") into `constitution.md` | Ask: "Will *every* future task need this? If not, it belongs in the local `spec.md`, not the Constitution." |
| Overly vague rules like "Be secure" or "Use best practices" | Push for concrete, checkable statements: "What *exactly* do you want to forbid? What should the AI *always* do?" |
| Students feel they must get the Constitution 'perfect' today | Emphasize the **Refinement Loop**: "This is v1. We'll update it every time the intern misbehaves." |
| Skeptical students ask "Why not just write this in every spec?" | Answer: "Because repetition leads to drift and inconsistency. `constitution.md` is your **single source of truth**." |

---

## Appendix C: Transition to Lesson 2.3 (Hands-On: Drafting `constitution.md`)

After Slide 9, transition with:

> "We've seen why the Constitution matters and what belongs in it:  
> tech stack, security & data rules, and clear out-of-scope boundaries.
> 
> Now we're going to **draft your team's `constitution.md`**:
> - PMs will drive,  
> - Skill Owners will contribute rules from your domain,  
> - and we'll treat this as version 1 of your Employee Handbook.
> 
> Open your project repo, navigate to `.specify/memory/`, and get ready to create or edit `constitution.md` together."

---

## Appendix D: Enriched Constitution Template

*Based on [GitHub Spec Kit's native template](https://github.com/github/spec-kit/blob/main/templates/constitution-template.md), enriched with course-specific scaffolding.*

```markdown
[PROJECT_NAME] Constitution
===========================

Core Principles
---------------

Principle 1 — Purpose & Scope
Describe, in 2–3 sentences, the primary purpose of this project and who it serves.
- What problem are we solving?
- Who is the primary user or stakeholder?
- What outcome matters most?

Principle 2 — AI as Overconfident Intern
State how this project will manage AI assistance.
- Confirm that AI is treated as a capable but unreliable assistant.
- Commit to using the Verification Ritual (Read → Run → Test → Commit).
- Emphasize that humans remain responsible for final decisions.

Principle 3 — Plain-Language Commitment
Define how the team will communicate.
- State that all specs, plans, and docs must be understandable to a non-developer stakeholder.
- Avoid jargon where possible; explain acronyms on first use.

Principle 4 — Guardrails Over Features
Clarify that guardrails are first-class.
- Decisions about tech stack, security, and constraints are **not optional**.
- If a feature conflicts with guardrails, the guardrails win.

Principle 5 — Iterative Refinement
Describe how the Constitution evolves.
- This is versioned and updated as we learn.
- Recurring problems in AI output should trigger **Constitution updates**, not only one-off fixes.


Tech Stack & Platform Rules
---------------------------

Clearly define what tools and platforms the project is allowed to use. Be specific enough that an AI (or new teammate) can follow these rules without guessing.

Approved Languages & Frameworks
- Primary language(s): e.g., `Python 3.11`
- Web/API framework(s): e.g., `FastAPI` only
- Data/analysis tools: e.g., `pandas` for dataframes
- Prohibited languages/frameworks (if any)

Infrastructure & Deployment
- Allowed cloud(s) or environments: e.g., `Azure only`, `Local dev only`, or `Codespaces only`
- Database choice(s): e.g., `PostgreSQL`, `SQLite`, etc.
- Any explicit restrictions: e.g., "No Kubernetes", "No Docker in this phase"

Performance & Cost Considerations (Optional)
- Any limits on model size, latency, or cost per run
- Example: "Prefer CPU-friendly models; avoid GPU-only solutions"


Security, Privacy & Data Boundaries
-----------------------------------

Define the "Never-Ever" rules for this project. These should be written in plain language and be **checkable**.

Secrets & Credentials
- Never hardcode API keys, tokens, or passwords in code.
- Store secrets in environment variables or approved secret stores only.
- Do not commit secrets to version control.

PII & Sensitive Data
- Define what counts as sensitive for this project (e.g., emails, phone numbers, payment info).
- Rules for logs: e.g., "Do not log raw emails or phone numbers; mask or hash identifiers."
- Rules for sample data: e.g., "Use synthetic or anonymized data in demos and examples."

External Services & Data Sharing
- Which third-party APIs are allowed, if any?
- Any restrictions on sending proprietary or user data to external services.
- Escalation rule: e.g., "If in doubt, escalate to PM before integrating a new service."


Out of Scope
------------

Explicitly list what this project will **not** do in this phase. This protects the team from scope creep and keeps the AI focused.

Functional Exclusions
- Features we are intentionally NOT building (e.g., "No real-time streaming", "No user-level personalization").
- Integrations we will not attempt (e.g., "No integration with payment providers in this capstone").

Technical Exclusions
- Architectures or patterns we will not adopt (e.g., "No microservices", "No multi-tenant architecture").
- Tools or platforms we will not use (e.g., "No on-prem deployment", "No unmanaged servers").

Phase Boundaries
- Clarify what "success" looks like for this course: e.g., "Happy-path PoC only, not production-ready system."
- Anything explicitly deferred to "future work" beyond the capstone.


Governance
----------

Define how this Constitution is created, updated, and enforced.

Roles & Ownership
- PM owns this document and is responsible for updating it.
- Skill Owners propose changes when they encounter recurring issues.
- The team must review and agree on major changes before they are adopted.

Change Process
- How changes are proposed (e.g., PR + short rationale).
- How often the Constitution is reviewed (e.g., at each Gate, or weekly).
- How versioning is handled (see version fields below).

Enforcement
- All specs (`spec.md`), plans (`plan.md`), tasks, and skills must comply with this Constitution.
- If a conflict arises, the team must either:
  - Update the Constitution (with explicit agreement), OR
  - Adjust the spec/plan to comply.
- AI prompts and commands (e.g., `/speckit.clarify`, `/speckit.plan`) should reference this Constitution when relevant.

Version: [CONSTITUTION_VERSION] | Ratified: [RATIFICATION_DATE] | Last Amended: [LAST_AMENDED_DATE]
```

---

*End of Lesson 2.2: The Constitution Lecture*
