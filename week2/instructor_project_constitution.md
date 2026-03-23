PodClip Skillset Constitution
==============================

Version: v1.0.0 | Ratified: 2026-03-23 | Last Amended: 2026-03-23


Core Principles
---------------

### Principle 1 — Purpose & Scope

PodClip Skillset helps marketing managers and podcast creators identify and package
the most shareable moments from podcast episodes as social media clips. The primary
users are marketing managers who need to repurpose podcast content efficiently across
Instagram Reels (IG), TikTok, YouTube Shorts, and LinkedIn. The outcome that matters
most is a ranked, publish-ready clip report that requires minimal human editing before
distribution.

- **Problem we are solving**: Manually identifying strong social media clips from
  long-form podcast transcripts is time-consuming and inconsistent.
- **Primary user**: Marketing managers at companies producing podcast content.
- **Outcome that matters most**: A ranked clip report the marketing manager can act on
  immediately — correct timestamps, on-brand captions, platform-appropriate metadata.


### Principle 2 — AI as Overconfident Intern

AI is treated as a capable but unreliable assistant. It can produce fluent, plausible
output that is factually wrong, off-brand, or subtly broken. We do not trust AI output
without verification.

**Verification Ritual** — applied to all AI-generated output before acceptance:

1. **Read** — Review the output carefully for accuracy, tone, and completeness.
2. **Run** — Execute the associated scripts and confirm they produce correct results.
3. **Test** — Validate with unit and integration tests, plus human quality review
   by Jie Tao (as podcast host) on final clip report output.
4. **Commit** — Accept and record only verified output.

**Human responsibility**: The marketing manager using the tool holds final
responsibility for approving any clip report before it is shared or published.
"Approving" means checking: (a) timestamps are accurate, (b) captions are
factually correct and on-brand, (c) clip quality meets the publish-ready standard
before any content is distributed.

**Script vs. LLM ownership**: At every feature-level spec, the team must explicitly
evaluate and document whether each functionality is best owned by a deterministic
script or by the LLM. Default to scripts where consistency and auditability matter.
Reserve LLM ownership for tasks requiring genuine language understanding and editorial
judgment. This decision must be recorded in the Functional Requirements table using
the Owner column (Script / LLM / Script+LLM / User). Do not assume a prior ownership
decision carries forward — re-evaluate at each feature.


### Principle 3 — Plain-Language Commitment

All specs, plans, and project documents must be understandable to a non-developer
stakeholder — including the marketing managers and podcast hosts who use the skillset.

- Avoid jargon where plain language works equally well.
- Explain all acronyms on first use (e.g., LLM = Large Language Model, CTA =
  Call to Action, IG = Instagram).
- This principle applies to internal project documents, not to the generated clip
  reports, whose language is governed by platform assets and branding guidelines.


### Principle 4 — Guardrails Over Features

Decisions about tech stack, security, privacy, and scope constraints are not optional
and are not subject to negotiation under feature pressure.

- If a proposed feature conflicts with a guardrail — for example, adding a frontend
  UI or integrating an agent harness — the guardrail wins.
- The conflicting feature must be deferred or redesigned to comply.
- Guardrails may be updated, but only through the formal change process defined in
  the Governance section below — not bypassed quietly.


### Principle 5 — Iterative Refinement

This constitution is versioned and updated as the project learns. It is a living
document, not a one-time artifact.

- Recurring problems in AI output — for example, consistently poor caption quality
  for a specific platform, or repeated ownership confusion between script and LLM —
  must trigger a **constitution update**, not just a one-off workaround.
- Jie Tao logs recurring issues in a `CHANGELOG.md` file or as inline notes in this
  document. These logs serve as the primary input for the next scheduled review.
- The constitution is reviewed at each development milestone/gate and after each
  episode run post-deployment.


---

Tech Stack & Platform Rules
----------------------------

### Approved Languages & Frameworks

- **Primary language**: Python only (V1). No other programming languages are
  approved in this phase.
- **Libraries**: Only necessary packages are permitted. Prefer vanilla Python where
  possible. Examples of acceptable packages: `json`, `rich`, `pytest`.
  When in doubt, ask: "Can I do this in standard Python without a library?" If yes,
  do not add a dependency.
- **Prohibited frameworks**: `langchain`, `langgraph`, `agent-sdk`, and all other
  agent harness libraries are explicitly banned in V1. No exceptions.
- **No web or API framework required**: The skillset is not a web service. Do not
  introduce `FastAPI`, `Flask`, or similar frameworks.

### Infrastructure & Deployment

- **Environment**: Local development only (V1). No cloud, no remote servers.
- **Deployment**: The skillset is distributed as a packaged zip file containing the
  skill folder (`SKILL.md` + `scripts/` + `assets/`). Users upload the zip to
  Claude.ai or place the folder in a local project directory.
- **Explicit restrictions**: No Docker, no Kubernetes, no containerization, no
  managed cloud services (AWS, Azure, GCP) in this phase.
- **Future (post-V1)**: API-based LLM access and official Git workflows will be
  adopted in a future version. Do not pre-build for these now.

### Database

- **V1**: No database. All storage is file-based (flat files only): transcripts,
  speaker JSON, branding assets, and output reports are read from and written to
  the local filesystem.
- **Future (post-V1)**: `DuckDB` is the preferred document store for future
  versions requiring persistent storage.

### Performance & Cost

- Prefer smaller, cheaper LLM models over large or expensive ones. Cost efficiency
  is a first-class concern.
- Avoid GPU-only solutions; prefer CPU-friendly models.
- **Future goal**: Local model execution via `llama.cpp` to eliminate API dependency
  entirely. Do not architect against this future direction.


---

Security, Privacy & Data Boundaries
-------------------------------------

### Secrets & Credentials

- **Never** hardcode API keys, tokens, or passwords in code or configuration files.
- Store all secrets in a local `.env` file. The `.env` file must **never** be
  committed to version control.
- A `.gitignore` file **must** be present in the project root and **must** include
  `.env` before any version control system is adopted.
- **V1 note**: V1 uses subscription-based access (Claude.ai, ChatGPT) and requires
  no API keys. The `.env` rule applies as soon as any API-based access is introduced.

### PII & Sensitive Data

The following data is classified as **internal/confidential** in this project:

- **Guest info**: Guest names, roles, titles, and any other identifying information
  provided in the speaker JSON file.
- **Output clip report**: The generated markdown report containing clip suggestions,
  captions, scores, and reasoning.

The following data is **not sensitive** in this project:

- **Transcripts**: Podcast transcripts are ready-to-publish content and are not
  subject to confidentiality restrictions.

**Logging rules**:
- Processing steps may be logged for debugging purposes.
- Guest names and guest PII must **never** appear in log output.
- Log at the step level (e.g., "Sliding window scan complete: 12 candidates
  generated"), not at the content level (e.g., never log transcript excerpts or
  guest attribution results).

**Sample and demo data**:
- Use synthetic or anonymized guest info in all examples, tests, and documentation.
- Never use real guest data in demos, test fixtures, or sample files.

### External Services & Data Sharing

- **V1 approved**: The built-in web search tool provided by the active LLM interface
  (Claude.ai, ChatGPT) is permitted for fetching external content such as branding
  URLs. This is considered part of the LLM interface, not a separate integration.
- **V1 prohibited**: No other third-party API integrations, webhooks, or external
  service calls are permitted.
- **Data boundary**: Confidential data (guest info, output reports) must not be
  sent to any external service beyond the active LLM interface.
- **Future integrations** (social platform APIs, Slack/Telegram MCPs) require
  explicit review and written approval from Jie Tao before adoption.
- **Escalation rule**: If in doubt about whether a new external service is
  acceptable, escalate to Jie Tao before integrating.


---

Out of Scope
------------

> ⚠️ Before starting any new feature, check it against the exclusions below. If the
> feature appears on any exclusion list, a written constitution amendment is required
> before work begins. Do not proceed without it.

### Functional Exclusions

The following features will **not** be built in V1:

- Slack or Telegram integration for input or output delivery
- Real-time or streaming transcript processing (async/batch only)
- Platform-weighted scoring — all four dimensions (viralness, impact, reach,
  personal stories) are equally weighted in V1
- Multi-episode batch processing or episode history tracking
- User-level personalization or per-user preference settings
- Automated publishing or direct posting to any social platform

### Technical Exclusions

The following architectures, tools, and patterns will **not** be adopted in V1:

- Frontend UIs of any kind (web app, desktop app, mobile app, browser extension)
- Agent harnesses: `langchain`, `langgraph`, `agent-sdk`, or any equivalent library
- Fully autonomous agents — human-in-the-loop approval is required at all times
- Cloud or server deployment of any kind
- Docker or containerization
- Database or persistent storage beyond flat files
- Multi-tenant architecture
- Unmanaged or self-hosted servers

### Phase Boundaries

- **V1 scope**: Strictly limited to the four user stories defined in
  `podclip-skillset-spec.md`. No additional features without a constitution
  amendment.
- **Testing**: Unit and integration tests only (`pytest`). No stress testing,
  load testing, or performance benchmarking in this phase.
- **Quality bar**: PoC/pilot quality — not production-ready. Human review by
  Jie Tao (as podcast host and domain expert) is required on final output before
  any report is used or shared.
- **Deferred to future phases**: API-based LLM access, Git workflow, `DuckDB`
  document store, `llama.cpp` local models, Slack/Telegram delivery,
  platform-weighted scoring, social platform API integrations.


---

Governance
----------

### Roles & Ownership

- **Jie Tao (Skill Developer)** is the sole owner of this constitution for V1.
- Jie Tao is responsible for maintaining, updating, enforcing, and versioning
  this document.
- There are no separate skill owners in V1. All decisions vest with Jie Tao.

### Change Process

Changes to this constitution may be made in one of two ways:

1. **With rationale**: Propose the change with a short written explanation of why
   it is needed — what recurring problem triggered it, or what new constraint
   it addresses.
2. **Direct edit with note**: Jie Tao may edit the document directly, adding an
   inline note (e.g., `<!-- Amended 2026-04-10: Added DuckDB to approved stack
   after V1 pilot. -->`) to record the reason.

In both cases, the version number and Last Amended date must be updated.

**Review cadence**:
- During development: review at each milestone or gate.
- Post-deployment: review after each episode run.
- Recurring AI output issues must be logged in `CHANGELOG.md` (or as inline notes)
  and addressed at the next review — not patched silently.

**Versioning**: Semantic versioning (`v[major].[minor].[patch]`).
- Patch: minor clarifications or wording fixes.
- Minor: new rules, new exclusions, or extended guidance.
- Major: fundamental changes to principles, stack, or scope.

### Enforcement

- All specs (`spec.md`), plans, tasks, and skill files must comply with this
  constitution.
- The Script vs. LLM ownership principle (Principle 2) must be explicitly applied
  and documented in the Owner column of the Functional Requirements table at every
  feature-level spec. It is not inherited from prior decisions.
- If a conflict arises between a proposed feature and this constitution, the team
  must either:
  - (a) Update the constitution with an explicit written rationale before proceeding,
    OR
  - (b) Adjust the spec or plan to comply with the constitution as written.
- AI prompts and skill instructions should reference this constitution when relevant —
  particularly the out-of-scope rules, tech stack restrictions, and the Script vs.
  LLM ownership principle.
- Silent workarounds that bypass constitution rules are not permitted. If a rule
  is not working, amend the constitution — do not ignore it.


---

Version: v1.0.0 | Ratified: 2026-03-23 | Last Amended: 2026-03-23
