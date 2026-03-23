# Project Specification: PodClip Skillset

**Project Repo**: `podclip-skillset`
**Created**: 2026-03-23
**Status**: Draft
**Version**: 0.1

## Overview

PodClip Skillset is an agent skillset that analyzes podcast episode transcripts and suggests ranked social media clip candidates — complete with timestamps, captions, scores, and platform-specific metadata — delivered as a structured markdown report.

It is designed primarily for marketing managers who need to repurpose podcast content for social media, and secondarily for podcast creators and hosts managing their own distribution. The skillset is built on the Claude Agent Skills architecture (SKILL.md + scripts + assets) and is designed to be instruction-portable across Claude, ChatGPT, GitHub Copilot, and other LLM agent frameworks.

---

## User Scenarios & Testing *(mandatory)*

<!--
  User stories are PRIORITIZED as user journeys ordered by importance.
  Each story is INDEPENDENTLY TESTABLE — implementing just one still delivers a viable MVP.
  P1 is the most critical.
-->

### User Story 1 — Generate a Clip Report (Priority: P1)

A marketing manager provides a podcast transcript, a speaker JSON file, a target platform, and branding information. The skillset processes the transcript and returns a ranked markdown report containing 5 clip candidates — each with timestamps, a suggested caption, platform-specific metadata, dimension scores, and reasoning.

**Why this priority**: This is the core end-to-end workflow. Every other story is a variation or extension of this one. A working P1 is a shippable MVP.

**Independent Test**: Can be fully tested by providing a sample transcript + speaker JSON + platform selection and verifying the returned markdown report contains all required fields for 5 ranked clips.

**Acceptance Scenarios**:

1. **Given** a valid timestamped transcript, speaker JSON, target platform (e.g., LinkedIn), and branding info, **When** the user invokes the skillset, **Then** the system returns a markdown report with exactly 5 ranked clip candidates, each containing timestamps, caption, platform metadata, scores, and reasoning.
2. **Given** the same inputs, **When** the user invokes the skillset twice, **Then** the ranked order and scores are identical both times (deterministic script-layer output).
3. **Given** valid inputs, **When** the report is returned, **Then** the system prompts the user to save the report before the session ends.

---

### User Story 2 — Platform-Specific Output (Priority: P2)

A marketing manager runs the skillset on the same transcript twice — once targeting LinkedIn and once targeting Instagram Reels — and receives two distinct reports reflecting each platform's conventions: different clip durations, caption styles, and hashtag usage.

**Why this priority**: Validates that the built-in platform asset system works correctly and that platform selection meaningfully changes the output. Can be tested independently of the full pipeline in Story 1.

**Independent Test**: Can be fully tested by running the skillset on a single transcript for two different platforms and confirming the clip duration ranges, caption formats, and hashtag presence differ appropriately between the two reports.

**Acceptance Scenarios**:

1. **Given** the same transcript and speaker JSON, **When** the user selects Instagram Reels, **Then** all suggested clips fall within Instagram's platform-specified duration range and captions include hashtags formatted per Instagram conventions.
2. **Given** the same transcript and speaker JSON, **When** the user selects LinkedIn, **Then** all suggested clips fall within LinkedIn's platform-specified duration range and post text follows LinkedIn's professional tone and format.
3. **Given** an invalid platform name (e.g., "Twitter"), **When** the user invokes the skillset, **Then** the system rejects the input with a clear error message listing the four valid platforms.

---

### User Story 3 — Guest & Branding Customization (Priority: P3)

A marketing manager provides per-episode guest info (name, role, title) and custom branding documents for a specific episode. The generated report's captions and CTAs reflect the guest's identity and the brand's tone — distinct from the default bundled assets.

**Why this priority**: Validates the dynamic per-episode input layer. Independently demonstrable without needing to change the core pipeline.

**Independent Test**: Can be fully tested by running the skillset once with default branding and once with custom branding for the same transcript, then confirming CTA language and guest attribution differ between the two reports.

**Acceptance Scenarios**:

1. **Given** per-episode guest info is provided, **When** the report is generated, **Then** all clip captions correctly attribute the guest by name and role.
2. **Given** custom branding documents are provided, **When** the report is generated, **Then** CTA language in all captions reflects the custom branding, not the default bundled assets.
3. **Given** branding assets are updated after an execution, **When** the skillset is next invoked, **Then** the new report reflects the updated branding in 100% of CTA and caption fields.

---

### User Story 4 — Configurable Clip Count (Priority: P4)

A podcast creator requests 3 clips instead of the default 5. The report contains exactly 3 ranked clip candidates.

**Why this priority**: A simple runtime parameter test. Independently demonstrable in isolation, but represents the lowest complexity increment over Story 1.

**Independent Test**: Can be fully tested by invoking the skillset with `clip_count=3` and verifying the report contains exactly 3 candidates.

**Acceptance Scenarios**:

1. **Given** the user specifies `clip_count=3`, **When** the skillset runs, **Then** the report contains exactly 3 ranked clip candidates.
2. **Given** the user specifies `clip_count=10`, **When** the skillset runs, **Then** the report contains exactly 10 ranked clip candidates.
3. **Given** the user specifies `clip_count=11` (out of range), **When** the skillset runs, **Then** the system rejects the input with a clear error message stating the valid range (3–10) and allows the user to correct the value without restarting the session.

---

### Edge Cases

- **No strong clip candidates**: What happens when no candidates meet the minimum quality threshold after LLM evaluation? System should surface the best available candidates with a warning, not return an empty report.
- **Missing guest info**: System falls back to static host/co-host attribution from the bundled speaker JSON; report notes that guest info was not provided.
- **Missing branding info**: System falls back to default bundled branding assets; report notes which branding defaults were applied.
- **Transcript shorter than minimum clip duration**: System returns an error explaining that the transcript is too short for the selected platform's minimum clip duration, with the minimum duration value included.
- **Clip count out of range**: System rejects the value, states the valid range (3–10), and allows the user to correct it without restarting.
- **Minimal-input mode**: User provides only a transcript (no guest info, no custom branding, platform specified). System proceeds using static host/co-host from bundled speaker JSON and default branding assets, noting all defaults applied.

---

## Requirements *(mandatory)*

### Functional Requirements

| FR | Description | Owner |
|---|---|---|
| **FR-001** | System MUST accept a timestamped text file as the primary transcript input | Script |
| **FR-002** | System MUST accept a speaker JSON file defining static host/co-host and per-episode guest info (name, role, title) | Script |
| **FR-003** | System MUST accept per-episode branding information (web links and/or documents); if not provided, system MUST fall back to default bundled branding assets | Script |
| **FR-004** | User MUST specify a target platform at runtime; system MUST validate the value against an allowlist of four platforms: Instagram Reels, TikTok, YouTube Shorts, LinkedIn | Script |
| **FR-005** | User MAY specify clip count at runtime (valid range: 3–10); system MUST default to 5 if not specified and MUST reject out-of-range values with an actionable error message | Script |
| **FR-006** | System MUST perform a full-transcript sliding window scan using a bundled Python script under `scripts/` to generate a set of candidate clip windows with structural scores | Script |
| **FR-007** | System MUST apply LLM editorial judgment to evaluate each candidate window, identifying strong moments based on question-answer pairs, emotional language, and story openings | LLM |
| **FR-008a** | LLM MUST evaluate each clip candidate on four scoring dimensions: viralness, impact, reach, and personal stories — each scored independently | LLM |
| **FR-008b** | A script MUST aggregate the four dimension scores per candidate and produce a deterministic ranked order of clip candidates | Script |
| **FR-009** | System MUST apply platform-specific rules (clip duration range, tone, hashtag conventions, caption format) sourced from bundled skill assets; the LLM uses these rules to generate captions; these rules are NOT user-configurable at runtime | Script + LLM |
| **FR-010** | System MUST produce a structured markdown report containing: ranked clip list, timestamps, suggested captions, platform-specific metadata, dimension scores, and LLM-generated reasoning per clip; report structure and formatting enforced by a script template | Script + LLM |
| **FR-011** | System MUST deliver the report inline in the chat or IDE interface and MUST prompt the user to save the report before the session ends | User |
| **FR-012** | System MUST be compatible with the Claude Agent Skills architecture (SKILL.md + `scripts/` + `assets/`) and designed to be instruction-portable across GPT, Gemini, and GitHub Copilot agent frameworks | Script |
| **FR-013** | Branding assets MUST be updatable after each skillset execution to reflect new episode context; updates MUST be reflected in the next execution | Script |
| **FR-014** | All input validation — file format, platform allowlist check, clip count range, speaker JSON schema — MUST be handled by deterministic script logic before any LLM processing begins | Script |
| **FR-015** | The markdown report structure and field labels MUST be enforced by a script-based report template; only the reasoning and caption content is LLM-generated | Script + LLM |

---

### Key Entities *(data and concepts central to the project)*

- **Transcript** — A timestamped text file containing the full podcast episode dialogue. Primary input for clip candidate generation.

- **Speaker Profile** — A JSON file defining the static host and co-host (present every episode) and dynamic per-episode guest info (name, role, title, nickname). Used for speaker attribution in captions and CTAs.

- **Branding Assets** — Bundled default documents and/or web links specifying brand tone, CTA language, hashtags, and promotional links. Overridable per episode. Updated after each execution to stay current.

- **Platform Profile** — A built-in skill asset for each supported platform (Instagram Reels, TikTok, YouTube Shorts, LinkedIn) specifying clip duration range, tone, caption format, and hashtag conventions. Not user-configurable.

- **Clip Candidate** — A scored, ranked transcript segment produced by the two-layer pipeline. Contains: start/end timestamps, transcript excerpt, per-dimension scores (viralness, impact, reach, personal stories), aggregate score, and LLM-generated reasoning.

- **Candidate Handoff Payload** — The structured JSON format output by the sliding window script (FR-006) and consumed by the LLM (FR-007 and FR-008a). Bridges the deterministic and generative layers of the pipeline. Schema to be defined at feature-level spec.

- **Clip Report** — The final structured markdown document returned to the user. Treated as internal/confidential. Contains all ranked clip candidates with full metadata, captions, and reasoning.

---

## Success Criteria *(mandatory)*

<!--
  All criteria are technology-agnostic and measurable.
  "Publish-ready" rubric: correct platform duration, no timestamp or caption edits needed,
  on-brand CTA language, platform-appropriate hashtags.
-->

### Measurable Outcomes

| SC | Outcome | Theme |
|---|---|---|
| **SC-001** | ≥4 out of 5 suggested clips are rated "publish-ready" by a marketing manager using the publish-ready rubric: correct duration, no editing required, on-brand CTA, platform-appropriate hashtags | Output Quality |
| **SC-002** | 100% of generated reports include all required fields: timestamps, captions, platform metadata, dimension scores, and reasoning for each clip | Output Quality |
| **SC-003** | Clip durations in all generated reports fall within the platform-specified duration range from skill assets, 100% of the time | Platform Correctness |
| **SC-004** | Platform-specific metadata (hashtags, caption format, CTA style) is correctly applied per platform in 100% of reports | Platform Correctness |
| **SC-005** | Script-based components (input validation, sliding window scan, score aggregation, report formatting) produce identical outputs for identical inputs 100% of the time | Processing Reliability |
| **SC-006** | When no per-episode branding is provided, the system correctly falls back to default bundled branding assets in 100% of executions | Processing Reliability |
| **SC-007** | A marketing manager with no prior training on the skillset produces a complete, publish-ready clip report within 10 minutes of first use | User Experience |
| **SC-008** | The system surfaces a clear, actionable error message for every invalid input; the user can correct individual inputs without restarting the full session | User Experience |
| **SC-009** | Using a standard test transcript with fixed inputs (platform, clip count, guest info, branding), the skillset produces output of equivalent quality when run on Claude, ChatGPT, and GitHub Copilot | Portability |
| **SC-010** | V1: The system returns a complete clip report within a single synchronous chat session; the user is never required to re-submit inputs or wait across multiple sessions | Latency |
| **SC-011** | After a branding asset is updated post-execution, the next report reflects the updated branding in 100% of CTA and caption fields | Processing Reliability |
