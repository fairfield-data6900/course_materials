# Lesson 1.3: Instructor Script — Anatomy of an Executable Spec (v3)

**Course:** AI-Assisted SDD for Business Analysts  
**Session:** Week 1 — Foundations & Setup  
**Duration:** 30 minutes (00:50 – 01:20)  
**Goal:** Students understand the structure of a `spec.md`, copy the official template, and learn how to use the Spec Architect to update each section.

---

## What Changed in v3

| Previous Approach | Updated Approach |
|-------------------|------------------|
| Students create an empty `spec.md` file | Students **copy the official template** first |
| Spec Architect generates content from scratch | Spec Architect helps **update existing sections** |
| One spec per project | **Multiple specs per project** (project-level + skill-level) |
| Integration Ritual: "paste into empty file" | Integration Ritual: "**replace placeholder text**" |

---

## Learning Objectives

By the end of this lesson, students will be able to:

1. Explain why a `spec.md` is a "contract" with the AI (not just documentation)
2. Navigate the **official spec template** and understand each section's purpose
3. Copy the template into the correct folder location for CLI compatibility
4. Use the **Spec Architect System Prompt** to update sections via interview
5. Understand the difference between **project-level specs** and **skill-level specs**

---

## Pre-Lesson Checklist

| Task | Status |
|------|--------|
| Spec Architect System Prompt v3.1 ready to display | ☐ |
| Official template URL ready: `https://raw.githubusercontent.com/github/spec-kit/main/templates/spec-template.md` | ☐ |
| VS Code open with `starter-repo` | ☐ |
| AI chat interface ready (Copilot, ChatGPT, or Claude) | ☐ |
| Folder structure diagram ready to display | ☐ |

---

## Lesson Structure (30 min)

| Time | Segment | Duration | Content |
|------|---------|----------|---------|
| 00:00 – 00:03 | **The Spec as Contract** | 3 min | Brief recap: Specs control AI behavior |
| 00:03 – 00:10 | **The Official Template** | 7 min | Walk through each section of the template |
| 00:10 – 00:15 | **Project vs. Skill Specs** | 5 min | Explain the multi-spec structure |
| 00:15 – 00:25 | **Live Demo: Copy Template + Spec Architect** | 10 min | Model the full workflow |
| 00:25 – 00:30 | **Lab Setup** | 5 min | Distribute materials; preview Lab 1 expectations |

---

## Segment 1: The Spec as Contract (3 min)

**Purpose:** Quick bridge from Lesson 1.1 (Overconfident Intern) to the practical tool.

### Talking Points

> "In Lesson 1.1, we talked about the Overconfident Intern — brilliant, fast, but prone to assumptions and drift.
>
> How do you manage an intern like that? You give them a **written contract**.
>
> In this course, that contract is called a `spec.md`. It's not just documentation — it's an **executable specification** that controls AI behavior.
>
> A vague spec produces vague results. A precise spec produces precise results.
>
> The good news? You don't have to write this contract from scratch. GitHub provides an **official template**, and we have a tool called the **Spec Architect** that helps you fill it in."

---

## Segment 2: The Official Template (7 min)

**Purpose:** Walk students through the template structure so they understand what they're updating.

### Display: The Template Sections

> "Let me show you the official `spec-kit` template. This is what you'll be working with."

| Section | Purpose | Key Questions It Answers |
|---------|---------|--------------------------|
| **1. Project Overview** | Who, what, why | Who is the user? What problem does this solve? |
| **2. User Scenarios & Testing** | How it's used | What does the user journey look like? How do we test it? |
| **3. Functional Requirements** | What it must do | What are the MUST/SHOULD/COULD features? |
| **4. Technical Constraints** | Guardrails | What platform? What limits? What's prohibited? |
| **5. Success Criteria** | Definition of done | How do we know it's working? |
| **6. Out of Scope** | Boundaries | What are we NOT building? |

### Key Points to Emphasize

> "Notice that this template is **comprehensive**. Not every section will apply to every project.
>
> Part of your job is to **update the sections that matter** and **remove the ones that don't**.
>
> For example, if your project doesn't have an API, you'd delete the 'API Endpoints' section. That's not cheating — that's good spec hygiene."

### Show: A Section Example

Display the "User Scenarios" section from the template:

```markdown
## 2. User Scenarios & Testing

### Scenario 1: [Title]
- **Priority:** P1
- **Given:** [Initial state]
- **When:** [User action]
- **Then:** [Expected outcome]
- **Test:** [How to verify]
```

> "See this placeholder text? Your job is to **replace** `[Title]`, `[Initial state]`, etc. with your actual project details.
>
> The Spec Architect will help you figure out what to write."

---

## Segment 3: Project vs. Skill Specs (5 min)

**Purpose:** Introduce the multi-spec structure so students understand the bigger picture.

### Display: Folder Structure

```
📁 capstone-project/
├── .specify/
│   ├── specs/
│   │   ├── 001-project-overview/      ← PM owns (Weeks 1-3)
│   │   │   └── spec.md                ← PROJECT-LEVEL SPEC
│   │   ├── 002-imputation-skill/      ← Skill Owner A owns (Week 4+)
│   │   │   └── spec.md                ← SKILL-LEVEL SPEC
│   │   └── 003-feature-engineering/   ← Skill Owner B owns (Week 4+)
│   │       └── spec.md                ← SKILL-LEVEL SPEC
```

### Talking Points

> "Your capstone project will have **multiple specs** — not just one.
>
> **Project-level spec** (Weeks 1-3): This is the big picture. What's the overall goal? Who's the user? What are the major features? The **PM leads** this, with contributions from the whole team.
>
> **Skill-level specs** (Weeks 4-6): These are the detailed specs for each skill. What inputs does this skill take? What outputs does it produce? **Skill Owners** write these.
>
> Today, we're focused on the **project-level spec**. You'll create skill-level specs starting in Week 4."

### Example: Data Prep Pipeline

| Spec | Owner | Focus |
|------|-------|-------|
| `001-project-overview/spec.md` | PM | Overall pipeline: inputs, outputs, success criteria |
| `002-imputation-skill/spec.md` | Skill Owner A | Imputation logic: missing value strategies, edge cases |
| `003-feature-engineering/spec.md` | Skill Owner B | Feature engineering: transformations, validation rules |

> "Think of it like a contract hierarchy. The project-level spec is the **master contract**. The skill-level specs are **sub-contracts** that must align with the master."

---

## Segment 4: Live Demo — Copy Template + Spec Architect (10 min)

**Purpose:** Model the complete workflow from copying the template to updating sections.

### Demo Setup

| Tool | State |
|------|-------|
| VS Code | Open with `starter-repo`; terminal visible |
| AI Chat | New conversation (Copilot Chat, ChatGPT, or Claude) |
| Split Screen | AI chat on left; VS Code on right |

### Demo Script

#### Part A: Copy the Official Template (3 min)

| Time | Action | Narration |
|------|--------|-----------|
| 0:00 – 0:01 | **Open terminal in VS Code** | "First, let's set up our project folder and copy the official template." |
| 0:01 – 0:02 | **Create project folder** | Type: `mkdir -p .specify/specs/001-podcast-skill` — "I'm creating the folder for my project-level spec. The `001-` prefix helps with ordering." |
| 0:02 – 0:03 | **Download the template** | Type: `curl -o .specify/specs/001-podcast-skill/spec.md https://raw.githubusercontent.com/github/spec-kit/main/templates/spec-template.md` — "This downloads the official template into my spec file." |
| 0:03 – 0:03:30 | **Open the file** | Open `.specify/specs/001-podcast-skill/spec.md` in VS Code. "Now I have the full template with all sections and placeholder text." |

#### Part B: Start the Spec Architect (2 min)

| Time | Action | Narration |
|------|--------|-----------|
| 0:03:30 – 0:04 | **Open AI chat** | "Now I'll start the Spec Architect. Watch what happens when I paste the system prompt." |
| 0:04 – 0:04:30 | **Paste Spec Architect prompt** | Paste the full Spec Architect System Prompt v3.1. |
| 0:04:30 – 0:05 | **AI asks for template** | "Notice the AI's first question: it asks me to **upload or paste my template**. This is the key difference from v3.0 — the AI wants to see what I'm working with." |
| 0:05 – 0:05:30 | **Paste template contents** | Copy the contents of `spec.md` and paste into the chat. "I'm giving the AI my template so it knows the structure." |

#### Part C: Update a Section (5 min)

| Time | Action | Narration |
|------|--------|-----------|
| 0:05:30 – 0:06 | **AI acknowledges template** | "The AI confirms it can see my template and lists the sections. Now it starts the interview." |
| 0:06 – 0:06:30 | **Answer: Project name** | AI asks: "What is the name of your project?" — Type: "Podcast Marketing Tool" |
| 0:06:30 – 0:07 | **Answer: Primary user** | AI asks: "Who is the primary user?" — Type: "Marketing Managers who need to repurpose podcast content" |
| 0:07 – 0:07:30 | **Answer: Problem statement** | AI asks: "What problem does this solve?" — Type: "They spend hours manually creating social clips and show notes" |
| 0:07:30 – 0:08 | **AI drafts Section 1** | "The AI drafts the Project Overview section. Notice it's in Markdown format, ready to paste." |
| 0:08 – 0:08:30 | **Review and approve** | "I read it... looks good. I type 'Approved' to move on." |
| 0:08:30 – 0:09 | **Copy the output** | "Now I copy the Markdown using the **copy button** on the code block." |
| 0:09 – 0:09:30 | **Replace in spec.md** | Switch to VS Code. Find Section 1 in the template. Select the placeholder text and paste. "I'm **replacing** the placeholder, not appending." |
| 0:09:30 – 0:10 | **Save and continue** | Save the file. "Now I continue with the AI for Section 2, and repeat the process." |

### Key Points During Demo

> "Let me highlight what just happened:
>
> 1. I **copied the official template** — I didn't start from scratch
> 2. The Spec Architect **asked for my template** — it's template-aware
> 3. I **replaced placeholder text** — not pasted into an empty file
> 4. The AI guides me **one question at a time** — I control the pace
>
> This is the workflow you'll follow in Lab 1. The PM drives the conversation; Skill Owners contribute answers."

---

## Segment 5: Lab Setup (5 min)

**Purpose:** Distribute materials and set expectations for Lab 1.

### Distribute Materials

| Material | Purpose |
|----------|---------|
| **Spec Architect System Prompt v3.1** | The core tool for Lab 1 |
| **Lesson 1.4 Student Lab Kit** | Step-by-step guide for the hands-on session |

### Lab 1 Preview

> "In Lab 1, your PM will lead your team through the Spec Architect interview.
>
> **Step 1:** Create your project folder and copy the template (5 min)
>
> **Step 2:** PM pastes the Spec Architect prompt and shares the template with the AI (5 min)
>
> **Step 3:** Team answers questions together; PM types the responses (35 min)
>
> **Step 4:** Commit your updated `spec.md` to GitHub (5 min)
>
> **PMs:** You facilitate. Ask your Skill Owners: 'What do you think?' before typing each answer.
>
> **Skill Owners:** Contribute your domain knowledge. When the AI asks about edge cases, you should be chiming in."

### Commands to Display

> "Here are the commands you'll run at the start of Lab 1:"

**Create folder and copy template:**

```bash
# Create your project folder (replace 'your-project-name')
mkdir -p .specify/specs/001-your-project-name

# Download the official template
curl -o .specify/specs/001-your-project-name/spec.md \
  https://raw.githubusercontent.com/github/spec-kit/main/templates/spec-template.md
```

**Per capstone:**

| Project | Command |
|---------|---------|
| Data Prep Pipeline | `mkdir -p .specify/specs/001-data-prep-pipeline && curl -o .specify/specs/001-data-prep-pipeline/spec.md https://raw.githubusercontent.com/github/spec-kit/main/templates/spec-template.md` |
| Code Generation Comparison | `mkdir -p .specify/specs/001-code-gen-comparison && curl -o .specify/specs/001-code-gen-comparison/spec.md https://raw.githubusercontent.com/github/spec-kit/main/templates/spec-template.md` |
| Code Documentation | `mkdir -p .specify/specs/001-code-documentation && curl -o .specify/specs/001-code-documentation/spec.md https://raw.githubusercontent.com/github/spec-kit/main/templates/spec-template.md` |

### Success Criteria for Lab 1

| Criterion | Owner | Verification |
|-----------|-------|--------------|
| Template copied to correct location | PM | File exists at `.specify/specs/[project]/spec.md` |
| At least 4 sections updated | Team | Placeholder text replaced with real content |
| Irrelevant sections identified | Team | Team knows which sections to remove |
| `spec.md` committed to GitHub | PM | Visible in repo |

### Transition to Lab 1

> "Alright — time to put this into practice. 
>
> **First:** Run the commands to create your folder and copy the template.
>
> **Then:** PM pastes the Spec Architect prompt and shares the template with the AI.
>
> You have 50 minutes. By the end, I want to see an updated `spec.md` committed to your team's GitHub repo.
>
> I'll circulate to help. If you get stuck, raise your hand. Let's go!"

---

## Appendix A: Template Section Reference

For instructor reference — the official template sections and their purposes:

| Section | Required? | Purpose | Common Removals |
|---------|-----------|---------|-----------------|
| Project Overview | ✅ Yes | Who, what, why | Never remove |
| User Scenarios | ✅ Yes | User journeys + tests | Never remove |
| Functional Requirements | ✅ Yes | MUST/SHOULD/COULD | Never remove |
| Technical Constraints | ✅ Yes | Platform, limits, security | Never remove |
| Success Criteria | ✅ Yes | Definition of done | Never remove |
| Out of Scope | ✅ Yes | Boundaries | Never remove |
| API Endpoints | ⚠️ Optional | REST/GraphQL specs | Remove if no API |
| Data Models | ⚠️ Optional | Schema definitions | Remove if no database |
| UI/UX Requirements | ⚠️ Optional | Interface specs | Remove if CLI-only |

---

## Appendix B: Pitfall Warnings

| Pitfall | Likelihood | Mitigation |
|---------|------------|------------|
| Students skip template copy, start from scratch | High | Emphasize: "The template is your starting point, not optional" |
| Students paste AI output without replacing placeholder | Medium | Demo the "select and replace" action explicitly |
| Students keep irrelevant sections | Medium | Remind: "Delete sections that don't apply — that's good spec hygiene" |
| PM dominates without Skill Owner input | High | Announce: "PMs, ask your team before typing each answer" |
| Students forget to commit | High | Announce commit checkpoints at 25 min and 45 min |
| Template download fails (network issue) | Low | Have a backup: paste template contents directly |

---

## Appendix C: Spec Architect Onboarding Flow

What students will see when they paste the Spec Architect prompt:

```
AI: "Hello! I'm your Spec Architect. I'll guide you through updating your 
    project specification.

    Before we begin, I need to see your spec template.

    Please do ONE of the following:
    1. Upload your spec.md file (if your AI tool supports file uploads), OR
    2. Copy/paste the contents of your spec.md file into this chat, OR
    3. If you haven't created your spec.md yet, run these commands first:
       [commands shown]
       Then upload or paste the contents here.

    Once I can see your template, I'll guide you through updating each section."
```

**Instructor Note:** If students are confused by this, remind them: "The AI needs to see your template so it knows what sections to help you update. Just copy the contents of your `spec.md` file and paste it into the chat."

---

## Appendix D: Multi-Spec Timeline

| Week | Spec Type | Owner | Activity |
|------|-----------|-------|----------|
| 1 | Project-level spec | PM (team contributes) | Draft via Spec Architect |
| 2 | Project-level spec | PM (team contributes) | Refine via `/speckit.clarify` |
| 3 | Project-level spec | PM | Finalize; create `plan.md` |
| 4 | Skill-level specs | Skill Owners | Draft skill specs; PM writes `interface-spec.md` |
| 5 | Skill-level specs | Skill Owners | Refine; build skills |
| 6 | All specs | Team | Final integration; demo |

---

*End of Lesson 1.3 Instructor Script (v3 — Template-First Approach)*