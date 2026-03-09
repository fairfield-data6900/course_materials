# 💡 RTCF Framework: Your AI Thinking Tool

**The "Key" to Unlocking the Spec-Kit Template**

A specification is a contract for the AI. If your spec is vague, the AI will "hallucinate" the details. Use **RTCF** to ensure your instructions are precise and executable.

---

## 🧩 The Four Pillars of RTCF

| Element | Question to Ask | Why It Matters |
|---------|-----------------|----------------|
| **R**ole | **Who** is the AI or the User? | Sets the persona, expertise level, and tone |
| **T**ask | **What** exactly needs to be done? | Defines the specific action or transformation |
| **C**ontext | **What** are the rules and constraints? | Prevents the AI from making bad assumptions |
| **F**ormat | **How** should the output look? | Ensures the result fits into your project structure |

---

## 🛠 Applying RTCF to Your `spec.md`

Use these mental prompts to fill out the sections of your project template:

### 1. User Scenarios (The "Who & Why")

| RTCF | Question |
|------|----------|
| **Role** | Who is the specific person using this feature? |
| **Task** | What is their goal? |
| **Context** | What is the "Given/When" (the situation)? |
| **Format** | Use the **Given / When / Then** structure |

### 2. Functional Requirements (The "What")

| RTCF | Question |
|------|----------|
| **Role** | What part of the system is acting? |
| **Task** | What must the system do? |
| **Context** | What are the "Edge Cases" (e.g., what if the input is empty)? |
| **Format** | Use **"System MUST..."** statements |

### 3. Success Criteria (The "How Well")

| RTCF | Question |
|------|----------|
| **Role** | Who is judging if this works? |
| **Task** | What outcome are we measuring? |
| **Context** | What are the specific thresholds (e.g., "under 2 seconds")? |
| **Format** | A **Checklist** of measurable goals |

---

## 🤖 Pro-Tip: The "Spec Architect" Interview

If you get stuck, open **Copilot Chat** (or any AI) and use the **Spec Architect** persona. Instead of staring at a blank page, answer the Architect's questions:

| RTCF | Your Input |
|------|------------|
| **Role** | "I am a PM for a [Project Name] tool." |
| **Task** | "I need to define the User Scenarios." |
| **Context** | "The users are non-technical staff; the data is in CSV format." |
| **Format** | "Draft this for my `spec.md` file." |

The AI will interview you and generate the content — you just answer questions you already know the answers to.

---

## ⚠️ The Verification Ritual

**Read → Refine → Commit**

| Step | Action |
|------|--------|
| **Read** | Did the AI follow your RTCF constraints? |
| **Refine** | If the output is too vague, add more **Context** |
| **Commit** | Only save to your repo once it passes the "Knowledgeable Engineer" test |

---

## 🚫 Common RTCF Mistakes

| Mistake | Example | Fix |
|---------|---------|-----|
| Missing **Role** | "Process the data" | "The Data Analyst uploads a CSV..." |
| Vague **Task** | "Clean the data" | "Remove rows with >50% missing values" |
| No **Context** | "Handle errors" | "If file is empty, return error message: 'No data provided'" |
| Undefined **Format** | "Generate a report" | "Output as Markdown with H2 headers and bullet lists" |

---

## 🎯 Quick Reference: RTCF in One Sentence

> **"As a [ROLE], I need to [TASK], given [CONTEXT], and the output should be [FORMAT]."**

Use this sentence to check every requirement you write. If you can't fill in all four blanks, your spec isn't finished.

---

*Keep this handout next to your screen during Labs 1.4 and 1.6*