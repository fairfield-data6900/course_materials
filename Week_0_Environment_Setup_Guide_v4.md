# Week 0: Environment Setup Guide

**Course:** AI-Assisted SDD for Business Analysts  
**Time Required:** 20–30 minutes  
**Goal:** Prepare your local machine for Spec-Driven Development (SDD) and verify all tools before Week 1

---

## 1. What is Git? (Conceptual Primer)

Before installing tools, understand the mental model behind our workflow:

| Concept | Analogy | What It Does |
|---------|---------|--------------|
| **Repository (Repo)** | A "project folder with memory" | Stores your entire project + its complete history |
| **Clone** | "Download a copy" | Creates a local copy of a remote repository on your machine |
| **Commit** | A "save point" | Records a snapshot of your changes—no more `v1`, `v2`, `final_FINAL` |
| **Push** | "Upload your saves" | Syncs your local commits to GitHub for backup and sharing |
| **Branch** | A "sandbox" | Lets you try new ideas without affecting the main project |

**Key Insight:** In this course, we use Git not just for code, but to manage **Executable Specifications**—the blueprints that guide our AI tools. You will commit your `spec.md`, `plan.md`, and `tasks.md` just like code.

---

## 2. Prerequisites

Complete these before proceeding:

| Requirement | Action |
|-------------|--------|
| **GitHub Account** | [Sign up here](https://github.com/join) if needed |
| **GitHub Copilot Access** | Verify your subscription is active, or [apply for GitHub Education](https://education.github.com/discount_requests/application) if eligible |

---

## 3. Install Visual Studio Code Insiders

Download and install **VS Code Insiders** for your operating system. Insiders gives you the latest features — including the most up-to-date GitHub Copilot agent capabilities — updated daily.

👉 [https://code.visualstudio.com/insiders](https://code.visualstudio.com/insiders)

> **Why Insiders?** Copilot Agent Mode and the newest slash commands ship to the Insiders build first. Using Insiders ensures your tools match what is demonstrated in class.

Install it the same way you would install any application. When it launches, the title bar will show **"Visual Studio Code - Insiders"** and the icon will be green (instead of the standard blue).

---

## 4. Create Your Course Workspace and Clone the Starter Repo

You will create the `data6900` workspace folder **first** using your operating system, then open it in VS Code, and do everything else from VS Code's integrated terminal.

### Step 1: Create the `data6900` Folder

**Mac:**
1. Open **Finder**
2. Navigate to `Documents` (or wherever you keep course work)
3. Right-click → **New Folder**, name it `data6900`

**Windows:**
1. Open **File Explorer**
2. Navigate to `Documents`
3. Right-click → **New → Folder**, name it `data6900`

### Step 2: Open the Folder in VS Code Insiders

1. Launch **VS Code Insiders**
2. Select **File → Open Folder**
3. Navigate to and select your `data6900` folder
4. Click **Open**

VS Code will now open with `data6900` as your workspace. You should see the folder name in the **Explorer** panel (left sidebar) and in the window title bar.

### Step 3: Open the Integrated Terminal

Everything from here is done via VS Code's built-in terminal — no separate terminal app needed.

- **Mac:** Press `` Cmd + ` `` (backtick)
- **Windows/Linux:** Press `` Ctrl + ` `` (backtick)

Confirm the terminal prompt shows your `data6900` folder path before continuing.

> **Important:** All remaining steps must be run from this terminal, with `data6900` as the working directory.

---

## 5. Tool Installation

In the VS Code Insiders terminal (still inside your `data6900` folder), run the appropriate install command for your operating system.

### 🍎 Mac / Linux (zsh)

Copy and paste this **single line** into the VS Code terminal and press Enter:

```zsh
curl -LsSf https://astral.sh/uv/install.sh | sh && source $HOME/.local/bin/env && uv tool install specify-cli --from git+https://github.com/github/spec-kit.git && specify check
```

**What this does:**
1. Downloads and installs `uv` (Python environment manager)
2. Makes `uv` available immediately (without restarting)
3. Installs the Spec Kit CLI (`specify`)
4. Verifies the installation with `specify check`

**If the single-line command fails**, run each step individually:

```zsh
# Step 1: Install uv
curl -LsSf https://astral.sh/uv/install.sh | sh
```

```zsh
# Step 2: Make uv available
source $HOME/.local/bin/env
```

```zsh
# Step 3: Install Spec Kit CLI
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```

```zsh
# Step 4: Verify installation
specify check
```

---

### 🪟 Windows (PowerShell)

Copy and paste the **entire script** into the VS Code terminal:

```powershell
#===============================================================================
# SDD Course - Environment Setup Script (Windows)
# Run this inside VS Code's integrated terminal (PowerShell)
# Installs: uv, specify-cli (GitHub Spec Kit)
#===============================================================================

Write-Host "==============================================" -ForegroundColor Cyan
Write-Host "  SDD Course - Environment Setup (Windows)"    -ForegroundColor Cyan
Write-Host "==============================================" -ForegroundColor Cyan
Write-Host ""

#---------------------------------------
# Step 1: Set Execution Policy
#---------------------------------------
Write-Host "[1/5] Configuring PowerShell execution policy..." -ForegroundColor Yellow
try {
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser -Force
    Write-Host "      ✓ Execution policy configured" -ForegroundColor Green
} catch {
    Write-Host "      ! Could not set execution policy (may require admin)" -ForegroundColor Yellow
}

#---------------------------------------
# Step 2: Install uv
#---------------------------------------
Write-Host "[2/5] Installing uv (Python environment manager)..." -ForegroundColor Yellow
$uvCheck = Get-Command uv -ErrorAction SilentlyContinue
if ($uvCheck) {
    Write-Host "      ✓ uv is already installed" -ForegroundColor Green
} else {
    powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
    Write-Host "      ✓ uv installed successfully" -ForegroundColor Green
}

#---------------------------------------
# Step 3: Refresh environment variables
#---------------------------------------
Write-Host "[3/5] Refreshing environment variables..." -ForegroundColor Yellow
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
Write-Host "      ✓ Environment refreshed" -ForegroundColor Green

#---------------------------------------
# Step 4: Install Spec Kit CLI
#---------------------------------------
Write-Host "[4/5] Installing specify-cli (GitHub Spec Kit)..." -ForegroundColor Yellow
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
Write-Host "      ✓ specify-cli installed" -ForegroundColor Green

#---------------------------------------
# Step 5: Verify installation
#---------------------------------------
Write-Host "[5/5] Verifying installation..." -ForegroundColor Yellow
Write-Host ""

$uvCheck = Get-Command uv -ErrorAction SilentlyContinue
if ($uvCheck) {
    Write-Host "      ✓ uv:      installed" -ForegroundColor Green
} else {
    Write-Host "      ✗ uv:      NOT FOUND" -ForegroundColor Red
}

$specifyCheck = Get-Command specify -ErrorAction SilentlyContinue
if ($specifyCheck) {
    Write-Host "      ✓ specify: installed" -ForegroundColor Green
} else {
    Write-Host "      ✗ specify: NOT FOUND" -ForegroundColor Red
}

Write-Host ""
Write-Host "==============================================" -ForegroundColor Cyan
Write-Host "  Tool Installation Complete!"                  -ForegroundColor Cyan
Write-Host "==============================================" -ForegroundColor Cyan
Write-Host ""
Write-Host "Next: Continue to Section 6 (Clone the Starter Repository)" -ForegroundColor White
Write-Host ""
```

**If the script fails**, run each command individually:

```powershell
# Step 1: Set execution policy
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser -Force
```

```powershell
# Step 2: Install uv
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

```powershell
# Step 3: Refresh PATH
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
```

```powershell
# Step 4: Install Spec Kit CLI
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```

```powershell
# Step 5: Verify installation
specify check
```

---

## 6. Clone and Rename the Starter Repository

In the same VS Code terminal (still inside your `data6900` folder), run:

```bash
git clone https://github.com/fairfield-data6900/starter-repo.git
```

**What this does:** This repository contains a collection of **Copilot Agent Skills** and **Slash Commands** specifically designed for our course. These tools help you explore code, review architecture, and trace design decisions using GitHub Copilot.

### Rename the Folder to Your Capstone Project Name

The folder will be cloned as `starter-repo`. **Rename it** to reflect your team's capstone project before doing anything else. Use lowercase letters and hyphens — no spaces.

**Mac / Linux:**
```bash
mv starter-repo data6900-your-project-name
```

**Windows (PowerShell):**
```powershell
Rename-Item starter-repo data6900-your-project-name
```

**Examples:**

| Project | Rename command (Mac/Linux) |
|---------|---------------------------|
| Automated Data Prep | `mv starter-repo data6900-auto-data-prep` |
| Customer Churn Predictor | `mv starter-repo data6900-churn-predictor` |
| Sales Forecast Dashboard | `mv starter-repo data6900-sales-forecast` |

> **Why this matters:** The folder name becomes your project's identity in Git. Renaming it now avoids confusion later when multiple teams' repos are visible on GitHub.

After cloning and renaming, your folder structure should look like this:

```
data6900/
└── data6900-your-project-name/   ← Renamed from starter-repo
    ├── .github/                   ← Contains Copilot Agent Skills (/scout, /trace, /add-skill)
    ├── .gitignore
    ├── README.md
    └── ...
```

### Open the Project in VS Code

1. **File → Open Folder**
2. Navigate to `data6900/data6900-your-project-name`
3. Click **Open**

You should now see the project structure in VS Code's Explorer panel.

---

## 6b. Initialize Spec Kit in Your Project

With the project open in VS Code, you need to initialize **Spec Kit** inside it. This is what creates the `.specify/` folder structure your team will use throughout the course to manage specifications, plans, and tasks.

In the VS Code integrated terminal (make sure you are **inside** your renamed project folder), run:

```bash
specify init . --ai copilot
```

> **What this does:** Initializes Spec-Driven Development tooling in the current directory, configured for GitHub Copilot. It creates the `.specify/` folder with templates, memory, and agent command files.

After running this command, your project repo should look like this:

```
data6900-your-project-name/
├── .github/             ← Copilot Agent Skills (from cloning)
│   ├── skills/          ← /scout, /trace, /add-skill
│   └── prompts/         ← /review, /conclude, /handoff
├── .specify/            ← Created by specify init
│   ├── memory/          ← constitution.md lives here
│   ├── scripts/         ← Automation helpers
│   ├── specs/           ← Your project's spec.md, plan.md, tasks.md
│   └── templates/       ← Starter templates for specs and plans
├── README.md
└── .gitignore
```

### Spec Kit Commands (Available After Init)

Once initialized, your Copilot Chat agent will have access to these **slash commands** for structured development:

| Command | When to Use |
|---------|-------------|
| `/speckit.constitution` | Week 1 — Establish your team's governing principles |
| `/speckit.specify` | Week 1 — Define *what* you are building |
| `/speckit.clarify` | Week 2 — Clarify ambiguous requirements |
| `/speckit.plan` | Week 3 — Generate a technical implementation plan |
| `/speckit.tasks` | Week 3 — Break the plan into actionable tasks |
| `/speckit.implement` | Week 4+ — Execute tasks and build the feature |

> **Tip:** These commands only become active after you run `specify init`. If Copilot Chat does not recognize them, check that you opened the `starter-repo` folder (not a parent folder) in VS Code.

---

## 7. Install VS Code Extensions & Sign Into GitHub

### Step 1: Install Extensions

1. Click the **Extensions** icon in the left sidebar (or press `Ctrl+Shift+X` / `Cmd+Shift+X`)
2. Search for and install:
   - **GitHub Copilot**
   - **GitHub Copilot Chat**

### Step 2: Sign Into GitHub

1. Click the **Accounts** icon (bottom-left corner of VS Code)
2. Select **Sign in to use GitHub Copilot**
3. Complete the browser authentication flow
4. Return to VS Code—you should see a checkmark next to your GitHub username

### Step 3: Verify Copilot is Active

- Look for the **Copilot icon** in the bottom-right status bar
- Open Copilot Chat: `Ctrl+Shift+I` (Windows/Linux) or `Cmd+Shift+I` (Mac)
- Type "Hello" and confirm you receive a response

---

## 8. Verification Checkpoint

Run the following command in VS Code's integrated terminal:

```bash
specify check
```

**✅ Success Criteria:**

| Check | Expected Result |
|-------|-----------------|
| `uv` command | Recognized (no "command not found" error) |
| `specify check` | Returns version or status message |
| Copilot icon | Visible in VS Code status bar (bottom right) |
| Copilot Chat | Responds when opened |
| Starter repo | `.github` and `.specify` folders visible in VS Code Explorer panel |
| Python version | Python 3.11+ installed (verify with `python --version`) |

If all checks pass, you are ready for Week 1.

---

## 9. Troubleshooting FAQ

### `specify` or `uv` command not found

**Cause:** Terminal hasn't refreshed the PATH after installation.

**Fix:**
1. Close and reopen VS Code completely
2. On Mac/Linux, run: `source $HOME/.local/bin/env`
3. On Windows, open a new terminal in VS Code

### GitHub Copilot isn't giving suggestions

**Cause:** Not signed into GitHub within VS Code.

**Fix:**
1. Click the **Accounts** icon (bottom-left corner)
2. Select **Sign in to use GitHub Copilot**
3. Complete the browser authentication

### Copilot shows "No access" or subscription error

**Cause:** GitHub account doesn't have an active Copilot subscription.

**Fix:**
1. Visit [github.com/settings/copilot](https://github.com/settings/copilot)
2. Verify subscription status
3. If using GitHub Education, ensure your application was approved

### Script fails on Windows with "execution policy" error

**Cause:** PowerShell is blocking script execution.

**Fix:** Run this command first:
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### `git clone` fails with authentication error

**Cause:** Git isn't configured with your GitHub credentials.

**Fix:**
1. Run: `git config --global user.name "Your Name"`
2. Run: `git config --global user.email "your.email@example.com"`
3. Try cloning again—authenticate via browser when prompted

### I'm on a locked corporate laptop or Chromebook

**Fallback:** Notify the instructor before Week 1. We will provide a **GitHub Codespaces** link for a browser-based environment.

---

## 10. Course Expectations: The Weekly Commit Ritual

Throughout this course, you will follow the **Verification Ritual** for all AI-generated content:

| Step | Action |
|------|--------|
| **1. Read** | Do you understand what the AI produced? |
| **2. Run** | Does it execute without errors? |
| **3. Test** | Does it do what you asked? |
| **4. Refine** | Is it clean and well-organized? |
| **5. Commit** | Only now does it enter the repository |

### Weekly Commit Expectation

**At the end of each week, commit and push your progress:**

```bash
git add .
git commit -m "Week X complete - [brief description]"
git push
```

**Why this matters:**
- **Safety Net:** Git provides "infinite undo"—you can always recover previous versions
- **Team Sync:** Your teammates can see and build on your work
- **Progress Tracking:** The instructor monitors commits to identify teams that need support
- **Gate Compliance:** Each week's gate check requires committed artifacts

---

## 11. Next Steps

With your environment verified and starter repo cloned, you are ready for **Week 1: Foundations & Setup**.

**What to expect in Week 1:**
- The "Overconfident Intern" lecture (why SDD matters)
- Running `/speckit.constitution` to set your team's governing principles
- Introduction to **Copilot Agent Skills**: Try `/scout` in Copilot Chat to map your project!
- PM leads: Draft your team's `spec.md` using `/speckit.specify`

**Optional Pre-Reading:**
- [GitHub Spec Kit Documentation](https://github.com/github/spec-kit)
- [VS Code Copilot Setup Guide](https://code.visualstudio.com/docs/copilot/setup)
- [Copilot Agent Skills Guide](https://github.com/fairfield-data6900/starter-repo)

---

## Quick Reference: Your Folder Structure

After completing Week 0, your machine should look like this:

```
Documents/
└── data6900/                         ← Your course workspace
    └── data6900-your-project-name/   ← Renamed from starter-repo
        ├── .github/                  ← Copilot Agent Skills (from starter-repo)
        │   ├── skills/               ← /scout, /trace, /add-skill
        │   └── prompts/              ← /review, /conclude, /handoff
        ├── .specify/                 ← Created by `specify init . --ai copilot`
        │   ├── memory/               ← constitution.md (your project's governing rules)
        │   ├── scripts/              ← Automation helpers
        │   ├── specs/                ← spec.md, plan.md, tasks.md per feature
        │   └── templates/            ← Starter templates
        ├── README.md
        └── .gitignore
```

All course capstone work will happen inside the `starter-repo` folder.

---

*Questions? Post in the course discussion forum or email the instructor before Week 1.*