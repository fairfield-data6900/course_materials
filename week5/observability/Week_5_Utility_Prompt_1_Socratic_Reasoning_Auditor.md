# Socratic Reasoning Auditor

## Purpose

This utility prompt helps you discover **what reasoning is missing** from your skill's output. It does NOT fix your skill — it asks questions that reveal where your skill cannot explain its own decisions.

**Use this BEFORE the Decision Summary Distiller.** You can't distill reasoning that doesn't exist yet.

---

## When to Use

- After your skill produces output for the first time
- Before you try to write a Decision Summary
- When you can't answer: "Why did the agent do this?"

---

## What You'll Get

A list of **Critical Reasoning Gaps** — specific places where your skill's output fails to explain its decisions. You'll use this list to instruct your coding agent to add the missing reasoning.

---

## Instructions

1. Run your skill on a sample input
2. Copy the **full output** your skill produced
3. Paste the prompt below into an external AI (ChatGPT, Claude, etc.)
4. Replace `[PASTE YOUR SKILL OUTPUT HERE]` with your actual output
5. Replace `[BRIEF DESCRIPTION]` with a one-sentence description of what your skill does
6. Review the Critical Reasoning Gaps the auditor identifies
7. Use those gaps to instruct your coding agent (see "What to Do Next" at the bottom)

---

## The Prompt

Copy everything inside the fence below:

````markdown
You are a Senior Technical Auditor specializing in AI Observability.

You are skeptical but constructive. You do NOT fix problems.
You do NOT rewrite the student's output.
You ask questions that reveal where reasoning is invisible.

## CONTEXT

A student has built an AI agent skill that performs the following task:

> [BRIEF DESCRIPTION OF WHAT YOUR SKILL DOES]

The student has run the skill and received the output below.
Your job is to audit this output for **missing reasoning**.

## THE SKILL'S OUTPUT

```
[PASTE YOUR SKILL OUTPUT HERE]
```

## YOUR TASK

Examine the output above and identify where the skill **made decisions
but did not explain them**. Use the five questioning categories below.

For each gap you find, produce:
- A **Gap Label** (short name)
- The **Evidence** (quote or point to the specific part of the output)
- A **Probing Question** the student must answer

### Questioning Categories

**1. The "Why" — Clarification**
Look for places where the skill chose one option but didn't say why.
- "The output includes [X] but doesn't explain why [X] was chosen over [Y]."
- "What criteria drove this selection?"
- "Were there alternatives? What were they?"

**2. The "Data" — Evidence**
Look for places where the output doesn't trace back to specific input.
- "The output claims [X], but which part of the input supports this?"
- "Can you point to the exact data that triggered this decision?"
- "Is this based on the input, or did the agent infer/assume it?"

**3. The "Confidence" — Assumptions**
Look for places where the skill sounds certain but shouldn't be.
- "The output states [X] with no qualification. How confident should we be?"
- "What is the agent assuming that it never explicitly stated?"
- "Where might this be wrong, and how would we know?"

**4. The "Trade-offs" — Implications**
Look for places where the skill made a choice that has costs.
- "Choosing [X] means sacrificing [Y]. Was that intentional?"
- "If this decision is wrong, what breaks downstream?"
- "What was the cost of this choice?"

**5. The "Explain It" Test — Demo Readiness**
Imagine presenting this output to a non-technical audience.
- "If someone asked 'why did the agent do this?' — does the output answer that?"
- "If someone asked 'how do you know it didn't hallucinate?' — what evidence is here?"
- "Could a non-technical stakeholder understand this output without your verbal explanation?"

## CONSTRAINTS

- Identify **3 to 6 gaps** (no more, no fewer)
- Do NOT provide fixes or rewrites
- Do NOT generate replacement text for the output
- Each gap must reference a **specific part** of the output
- Keep the tone helpful but direct — like a curious senior colleague
- Prioritize gaps that would be **most visible at a demo** (i.e., gaps that
  a non-technical audience would notice or question)

## OUTPUT FORMAT

Return your findings in this exact format:

---

## Critical Reasoning Gaps

### Gap 1: [Short Label]
**Category:** [Which of the 5 categories]
**Evidence:** "[Quote or reference the specific part of the output]"
**Probing Question:** [The question the student must answer]

### Gap 2: [Short Label]
**Category:** [Which of the 5 categories]
**Evidence:** "[Quote or reference the specific part of the output]"
**Probing Question:** [The question the student must answer]

### Gap 3: [Short Label]
**Category:** [Which of the 5 categories]
**Evidence:** "[Quote or reference the specific part of the output]"
**Probing Question:** [The question the student must answer]

[Continue for up to 6 gaps]

---

## Summary

In 2–3 sentences, describe the overall observability state of this
skill's output. Is it mostly transparent with a few gaps, or is it
largely a black box?

---

## Priority Order

List the gaps in order of **demo-day risk** (highest risk first).
Which gap would be most embarrassing if a stakeholder asked about it?

---
````

---

## What to Do Next

After you receive the Critical Reasoning Gaps, use them to update your skill.

### Step 1: Review the gaps

Read each gap and ask yourself:
- Do I agree this is missing?
- Is this something my skill should explain?
- Would this come up at demo day?

### Step 2: Instruct your coding agent

For each gap you agree with, tell your coding agent to add the missing reasoning. Use this pattern:

> "Update the skill so that when it [DECISION DESCRIBED IN THE GAP], the output also includes:
> - What alternatives were considered
> - Why this option was chosen
> - What input data drove the decision
> - How confident the result is"

### Step 3: Re-run and verify

Run your skill again on the same input. Check:
- Does the output now include reasoning for each gap?
- Is the reasoning specific (not generic filler like "this was the best option")?
- Could a non-technical person read the reasoning and understand the decision?

### Step 4: Move to the Decision Summary Distiller

Once your skill produces reasoning alongside its results, use the **Decision Summary Distiller** prompt to polish it into a demo-ready artifact.

---

## Example Walkthrough

### Before the Auditor

A student's Data Prep skill produces:

```
Processed 1,247 rows.
Dropped 83 rows.
Imputed 214 values.
Output saved to cleaned_dataset.csv.
```

This output tells you **what** happened but not **why**.

### After the Auditor

The auditor might return:

> **Gap 1: No Drop Criteria**
> **Category:** The "Why"
> **Evidence:** "Dropped 83 rows" — no explanation of why these rows were dropped.
> **Probing Question:** What rule determined that these 83 rows should be dropped and not the other 1,164?

> **Gap 2: No Imputation Method**
> **Category:** The "Data"
> **Evidence:** "Imputed 214 values" — no indication of what method was used or what the original values were.
> **Probing Question:** Were values imputed with mean, median, mode, or something else? How would you verify the imputed values are reasonable?

> **Gap 3: No Confidence Signal**
> **Category:** The "Confidence"
> **Evidence:** The output presents all results as equally certain.
> **Probing Question:** Were some imputations more reliable than others? How would a stakeholder know which parts of the cleaned dataset to trust?

### After the Student Updates Their Skill

The same skill now produces:

```
Processed 1,247 rows.

Dropped 83 rows:
- 71 rows: missing 3+ required fields (threshold: 3)
- 12 rows: duplicate entry detected (matched on customer_id + date)

Imputed 214 values:
- 'revenue' column (142 values): median imputation ($4,230)
- 'region' column (72 values): mode imputation ("Northeast")

Confidence Notes:
- Revenue imputations are moderate confidence (median is stable for this distribution)
- Region imputations are low confidence (mode covers only 34% of known values)
- Recommend manual review of region imputations before downstream analysis

Output saved to cleaned_dataset.csv.
```

**Now** the Decision Summary Distiller has material to work with.

---

## Quick Reference

| Step | What You Do | What You Get |
|------|-------------|--------------|
| **1. Run your skill** | Execute on sample input | Raw output |
| **2. Paste into Auditor** | Copy output into this prompt | Critical Reasoning Gaps (3–6) |
| **3. Update your skill** | Instruct coding agent to fill gaps | Reasoning-rich output |
| **4. Verify** | Re-run on same input | Confirm gaps are filled |
| **5. Move to Distiller** | Use Decision Summary Distiller prompt | Demo-ready Decision Summary |

---

*Part 1 of 3 — Week 5 Observability Utility Prompts*
*Next: Decision Summary Distiller (Part 3)*
*Bridge: Implementation instructions are included above in "What to Do Next"*
