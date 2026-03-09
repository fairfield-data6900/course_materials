# Lesson 1.4: Your First Spec — Student Lab Kit (v2)

**Duration:** 50 Minutes  
**Goal:** Update your team's `spec.md` using the Spec Architect interview process.

---

## 🎯 What You'll Accomplish

By the end of this session, your team will have:

- ✅ Copied the **official spec template** into your project folder
- ✅ Used the **Spec Architect** to update all 6 sections of your spec
- ✅ **Replaced placeholder text** with your project-specific content
- ✅ Identified and **removed sections** that don't apply to your project
- ✅ Committed your `spec.md` to GitHub
- ✅ Verified the `spec-kit` CLI can find your spec

---

## 👥 Team Roles During This Lab

| Role | Responsibility | Focus Areas |
|------|----------------|-------------|
| **PM** | Drives the AI conversation; owns the file and commit | "Who is the user?", "What's the goal?", "What's out of scope?" |
| **Skill Owner A** | Contributes domain knowledge for your skill area | "What inputs does my module need?", "What format should outputs be?" |
| **Skill Owner B** | Contributes edge cases and constraints | "What could go wrong?", "What happens if the input is empty?" |
| **Everyone** | Reviews and approves each section before moving on | "Does this look right? Any edits?" |

**Remember:** The PM facilitates, but **everyone contributes**. Don't let one person answer all the questions!

---

## ⏱️ Session Timeline

| Time | Phase | What to Do |
|------|-------|------------|
| **00:00 – 00:05** | Setup | Copy the official template into your project folder |
| **00:05 – 00:10** | Initialize | PM pastes Spec Architect prompt; shares template with AI |
| **00:10 – 00:25** | Interview Part 1 | Update Sections 1–3 (Overview, Scenarios, Requirements) |
| **00:25 – 00:30** | Integration Check | Replace placeholder text in your `spec.md` file |
| **00:30 – 00:45** | Interview Part 2 | Update Sections 4–6 (Constraints, Success, Out of Scope) |
| **00:45 – 00:50** | Commit & Verify | Commit to GitHub; run `/speckit.clarify` to verify |

---

## Phase 1: Setup — Copy the Official Template (5 min)

### Step 1.1: Open Your Terminal in VS Code

1. Open VS Code
2. Open your team's `starter-repo` folder
3. Open the terminal: `View` → `Terminal` (or press `` Ctrl+` ``)

### Step 1.2: Create Your Project Folder and Copy the Template

Run these commands (replace `your-project-name` with your actual project):

```bash
# Create the project folder inside .specify/specs/
mkdir -p .specify/specs/001-your-project-name

# Download the official template into your spec.md file
curl -o .specify/specs/001-your-project-name/spec.md \
  https://raw.githubusercontent.com/github/spec-kit/main/templates/spec-template.md
```

**Use your actual project name:**

| Capstone | Command |
|----------|---------|
| Data Prep Pipeline | `mkdir -p .specify/specs/001-data-prep-pipeline && curl -o .specify/specs/001-data-prep-pipeline/spec.md https://raw.githubusercontent.com/github/spec-kit/main/templates/spec-template.md` |
| Code Generation Comparison | `mkdir -p .specify/specs/001-code-gen-comparison && curl -o .specify/specs/001-code-gen-comparison/spec.md https://raw.githubusercontent.com/github/spec-kit/main/templates/spec-template.md` |
| Code Documentation | `mkdir -p .specify/specs/001-code-documentation && curl -o .specify/specs/001-code-documentation/spec.md https://raw.githubusercontent.com/github/spec-kit/main/templates/spec-template.md` |

### Step 1.3: Open and Explore the Template

1. In VS Code, navigate to `.specify/specs/001-your-project-name/spec.md`
2. Open the file
3. Take 1 minute to scroll through and see the sections:
   - Project Overview
   - User Scenarios & Testing
   - Functional Requirements
   - Technical Constraints
   - Success Criteria
   - Out of Scope

**Notice:** Each section has **placeholder text** like `[Project Name]` and `[Initial state]`. Your job is to **replace** this placeholder text with your actual project details.

---

## Phase 2: Initialize the Spec Architect (5 min)

### Step 2.1: Open Your AI Chat

Open any AI chat interface:
- **GitHub Copilot Chat** (in VS Code: `Ctrl+Shift+I` or `Cmd+Shift+I`)
- **ChatGPT** (chat.openai.com)
- **Claude** (claude.ai)
- **Any other LLM**

### Step 2.2: Paste the Spec Architect System Prompt

Copy and paste the **entire** Spec Architect System Prompt v3.1 into the chat.

The AI will respond with:

> "Hello! I'm your **Spec Architect**. I'll guide you through updating your project specification.
>
> **Before we begin, I need to see your spec template.**
>
> Please do ONE of the following:
> 1. **Upload** your `spec.md` file, OR
> 2. **Copy/paste** the contents of your `spec.md` file into this chat..."

### Step 2.3: Share Your Template with the AI

**Option A — Upload (if supported):**
- Click the attachment/upload button in your AI chat
- Select your `spec.md` file from `.specify/specs/001-your-project-name/`

**Option B — Copy/Paste:**
1. In VS Code, open your `spec.md` file
2. Select all (`Ctrl+A` or `Cmd+A`)
3. Copy (`Ctrl+C` or `Cmd+C`)
4. Paste into the AI chat

The AI will acknowledge your template and begin the interview:

> "Thanks! I can see your spec template. It has the following sections: [list]
>
> Let's start with **Section 1: Project Overview**.
>
> **Question 1:** What is the name of your project?"

---

## Phase 3: Interview Part 1 — Sections 1–3 (15 min)

The AI will guide you through updating each section. Answer the questions as a team.

### Section 1: Project Overview

**Questions the AI will ask:**
- What is the name of your project?
- Who is the primary user? (Be specific — role, not just "users")
- What problem does this solve for them?
- What is the one-sentence goal?

**Starter answers for each capstone:**

| Capstone | Project Name | Primary User | Problem Statement |
|----------|--------------|--------------|-------------------|
| **Data Prep Pipeline** | "Data Prep Pipeline" | "Data Analysts who need to clean messy datasets" | "They spend hours manually imputing missing values and engineering features" |
| **Code Generation Comparison** | "Code Generation Comparison Tool" | "Developers evaluating AI code generators" | "They can't objectively compare output quality across different LLMs" |
| **Code Documentation** | "Code Documentation Generator" | "Developers maintaining legacy codebases" | "They inherit undocumented code and spend days understanding it" |

**When the AI drafts the section:**
1. **Read it out loud** to your team
2. Discuss: "Does this capture our intent?"
3. Reply: **"Approved"** to continue, **"Edit: [your changes]"** to revise, or **"Remove"** if this section doesn't apply

---

### Section 2: User Scenarios & Testing

**Questions the AI will ask:**
- Describe a typical user journey — what does the user start with, what do they do, what do they expect?
- What's a second important scenario?
- What's an edge case or "unhappy path" we should handle?
- How would you verify each scenario works?

**Tips:**
- Think about the "happy path" first (everything works perfectly)
- Include at least one "unhappy path" (what if something goes wrong?)
- Use specific examples, not abstract descriptions

**Format the AI will produce:**
```markdown
### Scenario 1: [Title]
- **Priority:** P1
- **Given:** [Initial state]
- **When:** [User action]
- **Then:** [Expected outcome]
- **Test:** [How to verify]
```

---

### Section 3: Functional Requirements

**Questions the AI will ask:**
- What are the absolute must-have capabilities? (System MUST...)
- What input validation rules apply?
- What are important but not critical features? (System SHOULD...)
- What are nice-to-haves for future versions? (System COULD...)

**Tips:**
- **MUST** = Critical for v1 — project fails without this
- **SHOULD** = Important but not blocking — can ship without it
- **COULD** = Nice-to-have — defer to v2
- If you're unsure, mark it as `[NEEDS CLARIFICATION]`

---

## Phase 4: Integration Checkpoint (5 min)

**⏰ STOP! Before continuing to Section 4, save your work.**

### Step 4.1: Copy the Updated Sections

1. Find the AI's code block containing Sections 1–3
2. Click the **"Copy" button** in the top-right corner of the code block
3. **DO NOT** select and copy the conversational text — use the code block only

### Step 4.2: Replace Placeholder Text in Your `spec.md`

1. In VS Code, open `.specify/specs/001-your-project-name/spec.md`
2. Find **Section 1: Project Overview**
3. **Select the entire section** (from the `## 1.` header to just before `## 2.`)
4. **Paste** to replace the placeholder text with your updated content
5. Repeat for Sections 2 and 3
6. Save the file (`Ctrl+S` or `Cmd+S`)

### Step 4.3: Preview the Markdown

1. Press `Ctrl+Shift+V` (Windows) or `Cmd+Shift+V` (Mac) to preview
2. Check that headers, bullets, and formatting look correct

**⚠️ Don't skip this step!** If you leave everything in the chat window and your laptop crashes, you lose your work.

---

## Phase 5: Interview Part 2 — Sections 4–6 (15 min)

Continue the interview with the AI:

### Section 4: Technical Constraints

**Questions the AI will ask:**
- What platform or tools will this run on? (e.g., Python 3.11+, VS Code)
- Are there any data limits? (e.g., file size, row count)
- What dependencies are allowed or prohibited?
- Any security or privacy requirements?

**Tips:**
- If you don't know the tech stack yet, write "TBD" but be specific about what you DO know
- Think about file size limits, API rate limits, etc.
- Consider: "What should this tool NEVER do?"

---

### Section 5: Success Criteria

**Questions the AI will ask:**
- How will you know this project is successful?
- Is there a performance target? (e.g., processing time)
- Is there a usability goal? (e.g., user can complete task in X steps)
- Is there a business metric? (e.g., reduce manual effort by X%)

**Tips:**
- Make criteria **measurable** (numbers, not feelings)
- Include at least one criterion for each category:
  - **Functional:** "Does it work?" (e.g., "All P1 scenarios pass")
  - **Performance:** "Is it fast enough?" (e.g., "Processes 10K rows in under 30 seconds")
  - **Usability:** "Can users figure it out?" (e.g., "User completes task in 3 steps or fewer")

---

### Section 6: Out of Scope (The "What Ifs")

**Questions the AI will ask:**
- What features are explicitly NOT part of this project?
- What user requests are deferred to a future version?
- Why are these items out of scope?

**🔴 This is where most teams struggle!**

The AI will prompt you with edge case categories:

| Category | Question | Example Answer |
|----------|----------|----------------|
| **Empty Input** | What if the user provides a blank file? | "Return error: 'No data provided'" |
| **Oversized Input** | What if the file is too large? | "Return error: 'File exceeds 100MB limit'" |
| **Malformed Input** | What if the data is corrupted? | "Skip row and log warning" |
| **Missing Fields** | What if required fields are blank? | "Abort with clear error message" |
| **Duplicate Data** | What if there are duplicate entries? | "Deduplicate by [key field] before processing" |
| **Timeout** | What if processing takes too long? | "Abort after 60 seconds and notify user" |

**Aim for at least 3 specific edge cases!**

---

## Phase 6: Commit & Verify (5 min)

### Step 6.1: Final Assembly

1. Ask the AI: **"Please compile the complete spec.md"**
2. Copy the final output from the code block
3. In VS Code, **select all** content in your `spec.md` file (`Ctrl+A` or `Cmd+A`)
4. **Paste** to replace with the complete spec
5. Save the file

### Step 6.2: Remove Irrelevant Sections

Review your spec and **delete any sections that don't apply** to your project:

| Section | Keep or Remove? |
|---------|-----------------|
| API Endpoints | Remove if your project has no API |
| Data Models | Remove if your project has no database |
| UI/UX Requirements | Remove if your project is CLI-only |

**Removing irrelevant sections is good spec hygiene — not cheating!**

### Step 6.3: Check for Ambiguity

1. Press `Ctrl+F` (or `Cmd+F`) to open Find
2. Search for: `[NEEDS`
3. If you find any `[NEEDS CLARIFICATION]` tags, **resolve them now** by typing the answer
4. Search for: `[TBD`
5. If you find any `[TBD]` tags, either fill them in or add a comment explaining when they'll be resolved

### Step 6.4: Commit to GitHub

1. Open the **Source Control** tab in VS Code (left sidebar, or `Ctrl+Shift+G`)
2. You should see `spec.md` listed under "Changes"
3. Click the **"+"** next to `spec.md` to stage it
4. Enter a commit message: `"docs: initial project spec for [project name]"`
5. Click **"✓ Commit"**
6. Click **"Sync Changes"** to push to GitHub

### Step 6.5: Verify CLI Compatibility

1. Open Copilot Chat in VS Code
2. Type: `/speckit.clarify`
3. **Expected result:** The AI asks clarifying questions about your project
4. **If you see "No spec found":** Your file is in the wrong location — ask the instructor for help

---

## ✅ Success Checklist

Before the session ends, verify your team has completed:

| Criterion | ✓ |
|-----------|---|
| Template copied to `.specify/specs/001-[project]/spec.md` | ☐ |
| Section 1: Project Overview — placeholder text replaced | ☐ |
| Section 2: At least 3 User Scenarios defined | ☐ |
| Section 3: Functional Requirements use MUST/SHOULD/COULD | ☐ |
| Section 4: Technical Constraints documented | ☐ |
| Section 5: Success Criteria are measurable | ☐ |
| Section 6: At least 3 Edge Cases documented | ☐ |
| Irrelevant sections removed | ☐ |
| All `[NEEDS CLARIFICATION]` tags resolved | ☐ |
| `spec.md` committed and pushed to GitHub | ☐ |
| `/speckit.clarify` finds your spec | ☐ |

---

## 🆘 Troubleshooting

| Problem | Solution |
|---------|----------|
| **"curl: command not found"** | On Windows, use PowerShell: `Invoke-WebRequest -Uri "https://raw.githubusercontent.com/github/spec-kit/main/templates/spec-template.md" -OutFile ".specify/specs/001-your-project-name/spec.md"` |
| **"AI is giving too much at once"** | Tell the AI: "Stop. Let's go back to Section 2. Ask me one question at a time." |
| **"We don't know our tech stack yet"** | Write "TBD — to be determined in Week 2" in Constraints. |
| **"Permission Denied" on mkdir** | Make sure you're in the root of `starter-repo`, not inside a subfolder. |
| **"Can't find .specify/ folder"** | Run `specify init . --ai copilot` first, then repeat Phase 1. |
| **"Markdown looks broken after pasting"** | Re-copy using the code block's copy button, not by selecting text. |
| **"/speckit.clarify says 'No spec found'"** | Check your file path — must be `.specify/specs/[project]/spec.md` |
| **"Commit button is greyed out"** | Stage the file first by clicking the "+" next to it. |

---

## 🔜 What's Next?

In **Lesson 1.5: Peer Review & Refinement**, you will:

1. Swap specs with another team
2. Review their spec for gaps and ambiguities
3. Run `/speckit.clarify` on your own spec to stress-test it
4. Refine based on feedback

**Your first draft is never perfect — that's okay!** The goal of this session is to get something committed. You'll improve it in the next session.

---

## 📎 Quick Reference: The Integration Ritual

| Step | Action | Why |
|------|--------|-----|
| **1. Approve** | Reply "Approved" after reviewing each section | Confirms you've verified the AI's output |
| **2. Copy** | Use the code block's copy button | Gets clean Markdown without chat artifacts |
| **3. Replace** | Select placeholder text in `spec.md` and paste | Updates the template with your content |
| **4. Verify** | Preview Markdown; resolve `[NEEDS CLARIFICATION]` | Catches errors before commit |
| **5. Commit** | Stage → Commit → Sync | Creates permanent record |

**Rule:** If it's not committed, it doesn't exist.

---

*End of Lesson 1.4 Student Lab Kit (v2 — Template-First Approach)*