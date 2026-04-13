# Coding Agent Instruction Template — Reasoning Implementation Bridge

## Purpose

This utility prompt takes the **Critical Reasoning Gaps** identified by the Socratic Reasoning Auditor (Prompt 1) and translates them into **structured instructions** your coding agent can execute.

You don't need to write code. You don't need to know logging syntax. You paste your gaps, and this prompt generates the exact instructions you give to your coding agent (Copilot, ChatGPT, Claude, etc.) to update your skill.

---

## Where This Fits

| Step | Tool | Status |
|------|------|--------|
| 1. Audit | Socratic Reasoning Auditor | ✅ Done — you have your Critical Reasoning Gaps |
| **2. Implement** | **This template** | **← You are here** |
| 3. Distill | Decision Summary Distiller | Next |

---

## Prerequisites

Before using this template, you must have:

- [ ] Your **Critical Reasoning Gaps** from the Socratic Reasoning Auditor (Prompt 1)
- [ ] Your skill's current **file tree** (which files exist in `.skills/your-skill/`)
- [ ] Your **`constitution.md`** (for constraint verification)
- [ ] Your **`spec.md`** (for requirement traceability)

---

## Instructions

1. Copy the entire prompt below into your preferred LLM
2. Replace all `[BRACKETED PLACEHOLDERS]` with your actual content
3. Review the generated **Coding Agent Instructions**
4. Copy those instructions into your coding agent (Copilot Chat, etc.)
5. Let the agent update your skill
6. Re-run your skill and verify the reasoning now appears in the output

---

## The Prompt

Copy everything inside the fence below:

````markdown
You are a Coding Agent Instruction Writer.

Your job is to translate human-identified reasoning gaps into
precise, copy-paste-ready instructions that a coding agent
(GitHub Copilot, ChatGPT, Claude) can execute to update a skill.

You do NOT write the code yourself.
You write the INSTRUCTIONS that tell the coding agent what to build.

## CONTEXT

### About the Student
The student is a business analyst, not a developer. They cannot
write code directly. They use AI coding agents to build their skills.
All instructions you generate must be:
- Written in plain language
- Specific enough that a coding agent can execute without ambiguity
- Structured using the RTCF formula (Role, Task, Context, Format)

### About the Skill
**Skill Name:** [YOUR SKILL NAME]
**What it does:** [ONE-SENTENCE DESCRIPTION]
**Skill folder location:** `.skills/[YOUR-SKILL-FOLDER]/`

### Current File Tree
```
[PASTE YOUR SKILL'S FILE TREE HERE]

Example:
.skills/podcast-marketing/
├── SKILL.md
├── prompts/
│   └── extract-clips.md
├── code/
│   └── parse_transcript.py
└── recipes/
    └── brand-voice.md
```

### Constitution Constraints (Non-Negotiables)
```
[PASTE KEY RULES FROM YOUR CONSTITUTION.MD]

Example:
- Python 3.11 only
- No external API calls
- Clips must be ≤ 60 seconds
- No PII in any output
```

### Spec Requirements (What the Skill Must Do)
```
[PASTE THE RELEVANT SECTION FROM YOUR SPEC.MD]

Example:
- Input: Timestamped podcast transcript (.srt or .txt)
- Output: Social media clips, LinkedIn post, episode description
- Constraint: Must respect brand voice (see recipes/brand-voice.md)
```

## THE REASONING GAPS

The student ran the Socratic Reasoning Auditor and identified
these gaps in their skill's output:

```
[PASTE YOUR CRITICAL REASONING GAPS FROM PROMPT 1 HERE]

Example:
Gap 1: No Selection Criteria
Category: The "Why"
Evidence: "Selected clips: 1, 3, 5" — no explanation of why these clips.
Probing Question: What criteria drove the selection of these 3 clips
over the other candidates?

Gap 2: No Rejection Reasoning
Category: The "Why"
Evidence: Output shows selected clips but never mentions rejected candidates.
Probing Question: What clips were considered but rejected, and why?

Gap 3: No Confidence Signal
Category: The "Confidence"
Evidence: All clips presented with equal certainty.
Probing Question: Were some selections more confident than others?
How would a stakeholder know which clips to trust most?
```

## YOUR TASK

For each Critical Reasoning Gap, generate a **Coding Agent Instruction Block**
that the student can copy-paste directly into their coding agent.

### Instruction Block Format

For each gap, produce:

```
═══════════════════════════════════════════════════════════
INSTRUCTION BLOCK [N]: [Gap Label]
═══════════════════════════════════════════════════════════

ROLE:
You are a Senior SDD Coding Agent. Your primary directive is to
update the skill at [SKILL FOLDER PATH] to include reasoning
in its output, while adhering to the project Constitution.

TASK:
[Specific, plain-language instruction for what the agent must add
to the skill's output. Must directly address the reasoning gap.]

CONTEXT:
- Skill location: [path]
- File to modify: [specific file]
- Current behavior: [what the skill does now]
- Required behavior: [what the skill must do after this change]
- Constitution constraint: [any relevant rule that applies]

FORMAT:
The skill's output must now include a section called:
"[SECTION NAME]"

This section must contain:
- [Specific field 1]
- [Specific field 2]
- [Specific field 3]

The section must be written in plain language that a non-technical
audience can understand. No jargon. No raw data dumps.

GATE:
Before considering this task done, verify:
☐ The new section appears in the skill's output
☐ The reasoning is specific (not generic filler)
☐ The reasoning references actual input data
☐ The output still complies with constitution.md
☐ A non-technical person could read and understand it
```

### Additional Requirements

1. **Pre-Flight Check**
   Before generating instruction blocks, first verify:
   - Does the current file tree have the files needed to make these changes?
   - Are there any Constitution constraints that would prevent adding
     reasoning to the output?
   - Is there a `recipes/` folder that should inform the reasoning logic?

   If any issues are found, flag them as **Pre-Flight Warnings** before
   the instruction blocks.

2. **Sequencing**
   If gaps have dependencies (e.g., Gap 2 requires Gap 1 to be done first),
   note the required order.

3. **Recipe Integration**
   If any gap requires domain-specific knowledge (e.g., brand voice,
   evaluation criteria, style rules), reference the specific recipe file
   the coding agent should consult.

4. **Consolidation Check**
   After generating all instruction blocks, check:
   - Can any blocks be combined into a single instruction?
   - Are there overlapping changes to the same file?
   If so, provide a **Consolidated Instruction Block** that merges them.

5. **Verification Script**
   At the end, generate a simple **Verification Checklist** the student
   can use to confirm all gaps have been addressed:

   ```
   ## Verification Checklist

   Run your skill on the same sample input you used for the Auditor.
   Then check:

   ☐ Gap 1 ([Label]): Does the output now explain [specific thing]?
   ☐ Gap 2 ([Label]): Does the output now include [specific thing]?
   ☐ Gap 3 ([Label]): Does the output now show [specific thing]?
   ...
   ☐ All new output sections are in plain language
   ☐ No Constitution rules were violated
   ☐ Output is readable by a non-technical audience
   ```

## OUTPUT FORMAT

Return your response in this exact structure:

---

## Pre-Flight Check
[Any warnings or confirmations]

## Instruction Blocks

### Block 1: [Gap Label]
[Full instruction block in the format above]

### Block 2: [Gap Label]
[Full instruction block in the format above]

### Block 3: [Gap Label]
[Full instruction block in the format above]

[Continue for each gap]

## Consolidated Instruction Block (if applicable)
[Merged instruction if multiple blocks target the same file]

## Sequencing Notes
[Any dependency ordering between blocks]

## Verification Checklist
[The checklist the student uses to confirm all gaps are addressed]

---
````

---

## How to Use the Output

### What You'll Receive

The prompt above will generate **Instruction Blocks** — one per reasoning gap. Each block is a self-contained, copy-paste-ready instruction for your coding agent.

### Step-by-Step Workflow

#### Step 1: Review the Pre-Flight Check
Read any warnings. If the prompt flagged a missing file or a Constitution conflict, resolve it before proceeding.

#### Step 2: Check the Sequencing Notes
If blocks must be executed in order, follow the sequence. Otherwise, you can run them in any order.

#### Step 3: Copy Block 1 into Your Coding Agent
Open Copilot Chat (or your preferred agent). Paste the first Instruction Block. Let the agent make the changes.

#### Step 4: Verify Block 1
Before moving to Block 2, check:
- Did the agent modify the correct file?
- Does the output now include the new reasoning section?
- Is the reasoning specific, not generic?

#### Step 5: Repeat for Each Block
Work through each block sequentially. Verify after each one.

#### Step 6: Run the Consolidated Block (if provided)
If the prompt merged multiple blocks, use the consolidated version instead of individual blocks.

#### Step 7: Run the Verification Checklist
Re-run your skill on the same sample input. Walk through every checkbox. If any fail, go back to the relevant block and re-instruct your agent.

#### Step 8: Move to Prompt 3 (Decision Summary Distiller)
Once all gaps are filled and verified, your skill now produces reasoning alongside its results. You're ready to distill that into a demo-ready Decision Summary.

---

## Example Walkthrough

### Input: Gaps from the Auditor

```
Gap 1: No Drop Criteria
Category: The "Why"
Evidence: "Dropped 83 rows" — no explanation of why.
Probing Question: What rule determined these 83 rows should be dropped?

Gap 2: No Imputation Method
Category: The "Data"
Evidence: "Imputed 214 values" — no method stated.
Probing Question: Were values imputed with mean, median, mode, or something else?

Gap 3: No Confidence Signal
Category: The "Confidence"
Evidence: All results presented as equally certain.
Probing Question: Were some imputations more reliable than others?
```

### Output: Instruction Blocks (Abbreviated)

```
═══════════════════════════════════════════════════════════
INSTRUCTION BLOCK 1: Drop Criteria Transparency
═══════════════════════════════════════════════════════════

ROLE:
You are a Senior SDD Coding Agent updating the Data Prep skill.

TASK:
Update the skill so that when rows are dropped, the output
includes a "Rows Dropped" section that lists:
- How many rows were dropped
- The rule that triggered each drop (e.g., "missing 3+ required fields")
- A breakdown by drop reason

CONTEXT:
- Skill location: .skills/data-prep/
- File to modify: code/clean_dataset.py
- Current behavior: Outputs "Dropped 83 rows" with no explanation
- Required behavior: Outputs drop count + reason breakdown
- Constitution constraint: No PII in output (do not include row-level data)

FORMAT:
Add a section to the output called "## Rows Dropped"
containing a table:

| Reason | Count | Rule |
|--------|-------|------|
| Missing required fields | 71 | Threshold: 3+ missing |
| Duplicate entries | 12 | Matched on customer_id + date |

GATE:
☐ "Rows Dropped" section appears in output
☐ Each drop reason is specific (not "various reasons")
☐ No PII or row-level data exposed
☐ Constitution rules respected
```

```
═══════════════════════════════════════════════════════════
INSTRUCTION BLOCK 2: Imputation Method Disclosure
═══════════════════════════════════════════════════════════

ROLE:
You are a Senior SDD Coding Agent updating the Data Prep skill.

TASK:
Update the skill so that when values are imputed, the output
includes an "Imputation Details" section that lists:
- Which columns were imputed
- How many values per column
- The method used (mean, median, mode, etc.)
- The actual imputed value

CONTEXT:
- Skill location: .skills/data-prep/
- File to modify: code/clean_dataset.py
- Current behavior: Outputs "Imputed 214 values" with no method
- Required behavior: Outputs column-level imputation details
- Constitution constraint: Use only approved statistical methods

FORMAT:
Add a section to the output called "## Imputation Details"
containing a table:

| Column | Values Imputed | Method | Imputed Value |
|--------|---------------|--------|---------------|
| revenue | 142 | Median | $4,230 |
| region | 72 | Mode | "Northeast" |

GATE:
☐ "Imputation Details" section appears in output
☐ Method is named explicitly (not "standard method")
☐ Imputed values are shown
☐ Constitution rules respected
```

```
═══════════════════════════════════════════════════════════
INSTRUCTION BLOCK 3: Confidence Signals
═══════════════════════════════════════════════════════════

ROLE:
You are a Senior SDD Coding Agent updating the Data Prep skill.

TASK:
Update the skill so that the output includes a "Confidence Notes"
section that flags which results are high, moderate, or low
confidence, with a brief explanation.

CONTEXT:
- Skill location: .skills/data-prep/
- File to modify: code/clean_dataset.py
- Current behavior: All results presented with equal certainty
- Required behavior: Flag confidence levels with reasoning
- Recipe reference: Check recipes/ for any domain-specific
  confidence thresholds

FORMAT:
Add a section to the output called "## Confidence Notes"
containing bullet points:

- Revenue imputations: Moderate confidence (median is stable
  for this distribution)
- Region imputations: Low confidence (mode covers only 34%
  of known values — recommend manual review)

GATE:
☐ "Confidence Notes" section appears in output
☐ Each note has a confidence level AND a reason
☐ Low-confidence items include a recommendation
☐ Constitution rules respected
```

### Verification Checklist

```
## Verification Checklist

Run your skill on the same sample input. Then check:

☐ Gap 1 (Drop Criteria): Output now explains WHY rows were dropped
☐ Gap 2 (Imputation Method): Output now shows WHICH method was used per column
☐ Gap 3 (Confidence Signal): Output now flags HIGH/MODERATE/LOW confidence
☐ All new sections are in plain language
☐ No Constitution rules were violated
☐ A non-technical person could read the output and understand every decision
```

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| Coding agent says "I don't have access to that file" | Make sure you're running the agent in the correct workspace/directory |
| Agent adds reasoning but it's generic ("processed data efficiently") | Re-instruct: "The reasoning must reference specific input data, not generic descriptions" |
| Agent modifies the wrong file | Check the CONTEXT section — make sure the file path is correct |
| New output violates Constitution | Check the GATE section — re-instruct with the specific Constitution rule |
| Agent combines all reasoning into one paragraph | Re-instruct: "Use the exact section headers and table format specified in the FORMAT section" |
| Agent removes existing output to add reasoning | Re-instruct: "Add the new sections AFTER the existing output. Do not remove or modify existing output sections" |

---

## Quick Reference

| Step | What You Do | What You Get |
|------|-------------|--------------|
| **1. Paste gaps + context into this prompt** | Provide your Auditor gaps, file tree, constitution, spec | Instruction Blocks for your coding agent |
| **2. Copy Block 1 into coding agent** | Paste the instruction, let agent work | Updated skill file |
| **3. Verify Block 1** | Check output for new reasoning section | Confirmed or re-instruct |
| **4. Repeat for each block** | Work through all blocks | All gaps addressed |
| **5. Run Verification Checklist** | Re-run skill, check every box | Ready for Prompt 3 |

---

*Part 2 of 3 — Week 5 Observability Utility Prompts*
*Previous: Socratic Reasoning Auditor (Part 1)*
*Next: Decision Summary Distiller (Part 3)*
