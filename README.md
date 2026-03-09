# DATA6900: AI-Assisted Software Design for Business Analysts

**Fairfield University — Spring 2026**

---

## Overview

This repository contains all course materials for **DATA6900**, organized by week. Each folder includes instructor demos, student lab kits, and pre-work prep kits for that week's session.

---

## How to Use This Repo

### 1. Clone It Once

```bash
git clone https://github.com/fairfield-data6900/course_materials.git
cd course_materials
```

### 2. Pull Before Every Class

New materials are added each week. Before each session, sync your local copy:

```bash
git pull
```

### 3. Navigate by Week

Each `week*/` folder maps directly to a class session:

```
course_materials/
├── Week_0_Environment_Setup_Guide_v4.md   ← Start here before Week 1
├── AI_Assisted_SDD_Course_8_Week_Schedule_v7.md
├── week1/    ← Foundations & Setup
├── week2/    ← Refinement & Guardrails
├── week3/    ← The Implementation Plan
├── week4/    ← Agentic Skills & Task Decomposition
├── week5/    ← Hooks & Observability
├── week6/    ← Sub-agents & Final Integration
└── week7/    ← Dress Rehearsal
```

---

## Before Week 1: Complete the Environment Setup

Follow **`Week_0_Environment_Setup_Guide_v4.md`** to:

1. Install **VS Code Insiders** and **GitHub Copilot**
2. Install `uv` and the **Spec Kit CLI** (`specify`)
3. Clone and rename the **starter repo** to your capstone project name
4. Run `specify init . --ai copilot` to initialize Spec Kit
5. Verify everything with `specify check`

Do not skip Week 0 — the gate check at the start of Week 1 confirms your setup is complete.

---

## File Types You'll See

| File Pattern | What It Is |
|---|---|
| `Week_1_Instructor_Lesson_Plan.md` | Full session plan (instructor reference) |
| `Lesson_X_X_Demo_Kit_*.md` | Step-by-step instructor demo script |
| `Lesson_X_X_Student_Lab_Kit.md` | Your hands-on lab instructions |
| `Pre_Week_X_Prep_Kit.md` | Pre-work to complete **before** that week's class |

---

## Weekly Commit Ritual

At the end of each week, commit and push your capstone progress:

```bash
git add .
git commit -m "Week X: [brief description]"
git push
```

Your instructor monitors commits to track team progress and flag teams that may need support.

---

## Questions?

Post in the course discussion forum or email the instructor before the next session.
