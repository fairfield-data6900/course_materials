# Week 1: Instructor Lesson Plan

**Course:** AI-Assisted SDD for Business Analysts  
**Session:** Week 1 — Foundations & Setup  
**Duration:** 3 Hours (180 Minutes)  
**Gate:** Environment Gate  
**Goal:** 100% of students verified; first team `spec.md` committed

---

## Pre-Session Checklist

| Task | Status |
|------|--------|
| Verify `starter-repo` is accessible for all students | ☐ |
| Prepare Podcast Marketing Tool `spec.md` draft for live demo | ☐ |
| Print/share RTCF Cheat Sheet (1 per student) | ☐ |
| Print/share `spec.md` Scaffold Template (1 per team) | ☐ |
| Test `specify init` and `/speckit.clarify` in your demo environment | ☐ |
| Prepare "speed setup" backup for students who skipped Week 0 | ☐ |
| Have Environment Gate Checklist ready for end of session | ☐ |

---

## Session Schedule Overview

| Time | Lesson | Duration | Type | Topic |
|------|--------|----------|------|-------|
| 00:00 – 00:20 | **1.1** | 20 min | Lecture | Why SDD? — The "Overconfident Intern" Metaphor |
| 00:20 – 00:40 | **1.2** | 20 min | Verification | Environment Check |
| 00:40 – 01:10 | **1.3** | 30 min | Demo | Instructor Demo: `specify init` + draft `spec.md` |
| 01:10 – 02:00 | **1.4** | 50 min | Hands-on | Lab 1: PM leads project-level `spec.md` drafting |
| 02:00 – 02:06 | **1.5** | 6 min | Stand-up | Mid-Session Stand-up |
| 02:06 – 02:55 | **1.6** | 49 min | Hands-on | Lab 2: Peer review specs; run `/speckit.clarify` |
| 02:55 – 03:00 | **1.7** | 5 min | Gate | Environment Gate Check |

**Hands-on Ratio:** 99 min / 180 min = **55%**

---

## Lesson 1.1: Why SDD? — The "Overconfident Intern" Metaphor

**Time:** 00:00 – 00:20 (20 minutes)  
**Type:** Lecture  
**Materials:** Slides, whiteboard/digital board

### Learning Objectives

By the end of this lesson, students will be able to:
- Explain why "vibe coding" fails in professional workflows
- Define "context drift" and its consequences
- Articulate the value of Executable Specifications

### Talking Points

| Time | Topic | Key Points |
|------|-------|------------|
| 0:00 – 0:03 | **Welcome & Agenda** | Overview of today's session; set expectations for the Environment Gate |
| 0:03 – 0:08 | **The Problem: Vibe Coding** | "Has anyone asked ChatGPT to 'build me an app'?" → Discuss what happens (works initially, then breaks). Introduce the term "vibe coding" — prompting without structure. |
| 0:08 – 0:15 | **The Metaphor: Overconfident Intern** | "AI is like an overconfident intern — eager, fast, but lacks context." Key behaviors: (1) Assumes instead of asks, (2) Forgets previous instructions, (3) Confidently delivers wrong answers. This is **context drift** — the AI loses track of your intent over time. |
| 0:15 – 0:18 | **The Solution: Executable Specs** | "What if you could give the intern a written contract?" Introduce `spec.md` as the "source of truth" that prevents drift. Specs are **executable** — they guide AI behavior, not just document intent. |
| 0:18 – 0:20 | **Preview: What We'll Build** | Show the Podcast Marketing Tool end-state (Week 6 demo). "By Week 6, you'll build something like this — but we start with the spec." |

### Pitfall Warnings

| Pitfall | Mitigation |
|---------|------------|
| Students think specs are "just documentation" | Emphasize: "Specs are executable — they control AI behavior" |
| Students want to jump to code | Remind: "The intern needs instructions first. Code comes in Week 5." |
| Skeptics ask "Why not just prompt better?" | Answer: "Prompts are ephemeral. Specs persist and compound." |

### Transition

> "Now let's make sure everyone's environment is ready. If you completed Week 0, this will be quick. If not, we'll get you caught up."

---

## Lesson 1.2: Environment Check

**Time:** 00:20 – 00:40 (20 minutes)  
**Type:** Verification  
**Materials:** Week 0 Setup Guide (for stragglers)

### Purpose

- Confirm Week 0 setup is complete for all students
- Troubleshoot any remaining issues
- Ensure 100% readiness before hands-on labs

### Activity Flow

| Time | Activity | Instructor Action |
|------|----------|-------------------|
| 0:00 – 0:02 | **Quick Poll** | "Raise your hand if `specify check` passed in Week 0." Identify stragglers. |
| 0:02 – 0:05 | **Group Verification** | Everyone runs `specify check` in VS Code terminal. Display expected output on screen. |
| 0:05 – 0:08 | **Copilot Check** | Everyone opens Copilot Chat (`Cmd+Shift+I` / `Ctrl+Shift+I`). Type "Hello" — confirm response. |
| 0:08 – 0:18 | **Troubleshooting** | Pair struggling students with verified peers. Circulate to assist. Common issues: (1) Not signed into GitHub, (2) PATH not refreshed, (3) Copilot subscription inactive. |
| 0:18 – 0:20 | **Confirm 100%** | "Everyone should now have a green checkmark. If not, see me during Lab 1." |

### Speed Setup (For Stragglers)

If a student hasn't completed Week 0, provide this single command:

**Mac/Linux:**
```zsh
curl -LsSf https://astral.sh/uv/install.sh | sh && source $HOME/.local/bin/env && uv tool install specify-cli --from git+https://github.com/github/spec-kit.git && specify check
```

**Windows:**
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"; $env:Path = [System.Environment]::GetEnvironmentVariable("Path","User"); uv tool install specify-cli --from git+https://github.com/github/spec-kit.git; specify check
```

### Pitfall Warnings

| Pitfall | Mitigation |
|---------|------------|
| Stragglers slow down the whole class | Pair them with verified peers; don't let troubleshooting exceed 10 min |
| Students haven't cloned `starter-repo` | Have them run: `git clone https://github.com/fairfield-data6900/starter-repo.git` |
| Copilot shows "No access" | Direct to GitHub Education application; offer Codespaces fallback |

### Transition

> "Great — everyone's verified. Now let me show you how to initialize a project and draft your first spec."

---

## Lesson 1.3: Instructor Demo — `specify init` + Draft `spec.md`

**Time:** 00:40 – 01:10 (30 minutes)  
**Type:** Demo  
**Materials:** VS Code (screen shared), Podcast Marketing Tool spec draft

### Learning Objectives

By the end of this demo, students will be able to:
- Run `specify init` to create the `.specify/` folder structure
- Understand the purpose of each section in `spec.md`
- Apply the RTCF framework (Role, Task, Context, Format) to write clear specs

### Demo Script

| Time | Action | Narration |
|------|--------|-----------|
| 0:00 – 0:03 | **Open VS Code** | "I'm in my `data6900/starter-repo` folder. Let's initialize the Spec Kit." |
| 0:03 – 0:05 | **Run `specify init`** | Type: `specify init . --ai copilot`. "This creates the `.specify/` folder — the brain of our project." |
| 0:05 – 0:08 | **Explore folder structure** | Show `.specify/agents/`, `.specify/memory/`, `.specify/specs/`. "This is where all our specifications live." |
| 0:08 – 0:12 | **Open `spec.md` template** | "Let's look at the spec template. Notice the sections: Overview, Inputs, Outputs, Constraints, User Stories." |
| 0:12 – 0:18 | **Introduce RTCF Framework** | "Before we write, let's talk about RTCF — the formula for clear AI instructions." Display RTCF Cheat Sheet. **Role:** Who is the AI acting as? **Task:** What specific action? **Context:** What background info? **Format:** What output structure? |
| 0:18 – 0:25 | **Draft Podcast Skill spec** | Live-type the spec for Podcast Marketing Tool: **Overview:** "An agent skill that analyzes podcast transcripts to generate marketing content." **Inputs:** "Timestamped transcript (.txt or .srt)" **Outputs:** "Social media clips, LinkedIn post, episode description" **Constraints:** "Must respect brand voice (see constitution.md); clips ≤ 60 seconds" |
| 0:25 – 0:28 | **Show bad vs. good spec** | Bad: "Make a podcast tool" → Too vague. Good: [Show the spec you just wrote] → Clear inputs, outputs, constraints. |
| 0:28 – 0:30 | **Preview `/speckit.clarify`** | "Later, you'll run `/speckit.clarify` to get AI feedback on your spec. But first — you write it." |

### Key Points to Emphasize

- **Specs are contracts** — They define what the AI will and won't do
- **Inputs/Outputs are non-negotiable** — If it's not in the spec, the AI won't know about it
- **Constraints prevent drift** — "Must respect brand voice" keeps the intern on track

### Pitfall Warnings

| Pitfall | Mitigation |
|---------|------------|
| Students copy your spec verbatim | Remind: "Your capstone is different — use RTCF to write YOUR spec" |
| Demo runs long | Keep spec drafting to 7 min max; don't over-polish |
| Students ask about code | Redirect: "Code comes in Week 5. Today we focus on the contract." |

### Transition

> "Now it's your turn. PMs — you'll lead your team in drafting your capstone's `spec.md`. Skill Owners — contribute ideas, but let the PM drive."

---

## Lesson 1.4: Lab 1 — PM Leads Project-Level `spec.md` Drafting

**Time:** 01:10 – 02:00 (50 minutes)  
**Type:** Hands-on  
**Materials:** `spec.md` Scaffold Template, RTCF Cheat Sheet

### Learning Objectives

By the end of this lab, teams will have:
- A draft `spec.md` for their capstone project
- Applied the RTCF framework to define clear inputs, outputs, and constraints

### Activity Instructions

**For PMs:**
1. Open your team's `starter-repo` in VS Code
2. Navigate to `.specify/specs/` and create your project folder
3. Use the `spec.md` Scaffold Template as your starting point
4. Facilitate discussion — ask Skill Owners: "What inputs do we need? What should the output look like?"
5. Apply RTCF to each section

**For Skill Owners:**
1. Contribute ideas for inputs, outputs, and constraints
2. Think about your future skill boundaries — what will YOUR skill handle?
3. Don't take over — let the PM lead

### Facilitation Notes

| Time | Instructor Action |
|------|-------------------|
| 0:00 – 0:05 | Circulate; ensure all teams have opened their repos |
| 0:05 – 0:20 | Check that PMs are leading (not Skill Owners); redirect if needed |
| 0:20 – 0:35 | Look for vague specs; prompt with: "What's the specific input format?" |
| 0:35 – 0:50 | Warn teams: "5 minutes left — wrap up your draft" |

### Prompts to Spark Discussion

If a team is stuck, ask:
- "Who is the user of this tool?"
- "What does the user hand to the tool? (Input)"
- "What does the user get back? (Output)"
- "What should the tool NEVER do? (Constraints)"

### Pitfall Warnings

| Pitfall | Mitigation |
|---------|------------|
| PM dominates without input | Remind: "PM facilitates, all contribute. Use round-robin." |
| Specs are too vague | Prompt: "Can you be more specific about the input format?" |
| Teams try to write code | Redirect: "No code yet — just the contract." |
| One team finishes early | Challenge: "Add 2 more constraints. What could go wrong?" |

### Transition

> "Let's pause for a quick stand-up. Each team: 30 seconds — what's your project and one blocker you hit."

---

## Lesson 1.5: Mid-Session Stand-up

**Time:** 02:00 – 02:06 (6 minutes)  
**Type:** Stand-up  
**Materials:** Timer

### Purpose

- Surface blockers before Lab 2
- Build team accountability ritual (continues in future weeks)
- Keep energy high without a full break

### Format

Each team gets **30 seconds** to answer:
1. **Project name** (one sentence)
2. **One blocker or question** (if any)

### Facilitation Notes

| Action | Notes |
|--------|-------|
| Set a visible timer | Keeps teams concise |
| Don't solve blockers now | Note them; address in Lab 2 or after class |
| If no blockers | "Great — you're on track. Keep that momentum." |

### Transition

> "Good check-in. Now let's refine those specs. You'll peer review another team's work, then run `/speckit.clarify` for AI feedback."

---

## Lesson 1.6: Lab 2 — Peer Review + `/speckit.clarify`

**Time:** 02:06 – 02:55 (49 minutes)  
**Type:** Hands-on  
**Materials:** Peer Review Checklist (below)

### Learning Objectives

By the end of this lab, teams will have:
- Received feedback from another team
- Run `/speckit.clarify` and incorporated AI suggestions
- A refined `spec.md` ready for commit

### Activity Flow

| Time | Activity | Instructions |
|------|----------|--------------|
| 0:00 – 0:05 | **Pair teams** | Assign Team A ↔ Team B pairs for peer review |
| 0:05 – 0:20 | **Peer review** | Teams swap specs (share screen or push to GitHub). Reviewers use the checklist below. |
| 0:20 – 0:25 | **Feedback exchange** | Teams share 2 strengths + 2 suggestions with each other |
| 0:25 – 0:40 | **Run `/speckit.clarify`** | Each team runs the command on their own spec. Review AI suggestions. |
| 0:40 – 0:49 | **Incorporate feedback** | Teams refine their `spec.md` based on peer + AI feedback. **Commit the result.** |

### Peer Review Checklist

Reviewers should check:

| Criterion | ✓/✗ | Notes |
|-----------|-----|-------|
| **Overview** is clear and specific | | |
| **Inputs** are defined with format | | |
| **Outputs** are defined with format | | |
| **Constraints** include at least 2 boundaries | | |
| **RTCF** is evident (Role, Task, Context, Format) | | |
| No vague language ("make it good", "handle errors") | | |

### `/speckit.clarify` Instructions

1. Open Copilot Chat in VS Code
2. Type: `/speckit.clarify`
3. Review the AI's questions and suggestions
4. **You decide** what to accept — the AI is the intern, you are the manager

### Pitfall Warnings

| Pitfall | Mitigation |
|---------|------------|
| Peer review becomes criticism | Frame as: "2 strengths + 2 suggestions" |
| Teams accept all AI suggestions blindly | Remind: "You are the manager. The intern suggests, you decide." |
| Teams don't commit | Announce: "You must commit before the gate check." |

### Commit Reminder

Before the gate, all teams must run:

```bash
git add .
git commit -m "Week 1: Initial spec.md draft"
git push
```

### Transition

> "Time for the gate check. Let's verify everyone's environment and first commit."

---

## Lesson 1.7: Environment Gate Check

**Time:** 02:55 – 03:00 (5 minutes)  
**Type:** Gate  
**Materials:** Environment Gate Checklist

### Gate Criteria

| Criterion | Owner | Verification Method |
|-----------|-------|---------------------|
| VS Code + Copilot working | All students | `specify check` passes |
| First `spec.md` committed | PM (team) | Visible in GitHub repo |
| Can explain "context drift" | All students | Verbal spot-check or exit ticket |

### Verification Process

| Time | Action |
|------|--------|
| 0:00 – 0:02 | "Everyone run `specify check` one more time. Thumbs up when it passes." |
| 0:02 – 0:04 | "PMs — confirm your `spec.md` is pushed. I'll verify in GitHub after class." |
| 0:04 – 0:05 | "Quick exit question: What is context drift? [Cold-call 1-2 students]" |

### If a Team Fails the Gate

- **Environment issue:** Schedule office hours before Week 2
- **No commit:** Must push before midnight; instructor verifies async

### Closing Remarks

> "Great work today. You've written your first Executable Specification — the contract that keeps your AI intern on track. Next week, we'll add the constitution — the rules your AI must follow. See you then."

---

## Post-Session Tasks

| Task | Owner | Deadline |
|------|-------|----------|
| Verify all teams have `spec.md` committed | Instructor | Before Week 2 |
| Review specs for quality; note teams needing support | Instructor | Before Week 2 |
| Send Week 2 pre-reading (if any) | Instructor | 48 hours before Week 2 |

---

## Appendix: Capstone Project Options

For reference, here are the three capstone projects from Syllabus v5:

| Project | PM Responsibility | Skill Owner A | Skill Owner B |
|---------|-------------------|---------------|---------------|
| **Data Prep Pipeline** | Pipeline integration; end-to-end tests | Imputation Skill | Feature Engineering Skill |
| **Code Generation Comparison** | Evaluation framework; comparison logic | Python Generation Skill | SQL Generation Skill |
| **Code Documentation** | Style enforcement; integration | Parser Skill | Docstring Generator Skill |

---

*End of Week 1 Lesson Plan*