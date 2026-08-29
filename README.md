# Build Secure 24 — Participant Starter Repository

**Abhedya — VBIT Cybersecurity Forum, Vignana Bharathi Institute of Technology, Hyderabad**

Welcome to the official Build Secure 24 starter repository.

---

## 1. Challenge Overview

- **Duration**: 24 Hours
- **Team Size**: Exactly 4 participants per team
- **Core Requirement**: All project code must be created live during the 24-hour hackathon. Importing pre-built or third-party repositories is strictly prohibited.

---

## 2. Repository Structure

```
├── AGENTS.md                  ← AI agent behavioral contract & logging gate
├── README.md                  ← This file
├── PARTICIPANT_RULES.md       ← Competition rules
│
├── docs/                      ← Autonomous documentation layer
│   ├── APPROACH.md            ← Problem breakdown & architecture approach
│   └── PROMPTS_LOG.md         ← Turn-by-turn AI prompts log (managed by agent)
│
├── metadata/                  ← Submission metadata
│   ├── team.yaml              ← Team information (4 members)
│   └── submission.yaml        ← Final submission details
│
├── src/                       ← Application source code directory
└── deployment/                ← Deployment configuration directory
    └── README.md              ← Deployment record
```

---

## 3. Getting Started

### Step 1: Team Registration
Fill in `metadata/team.yaml` with your assigned Team ID, team name, and all 4 member details.

### Step 2: AI Agent Onboarding
When you open this repository in an AI coding assistant (Cursor, Windsurf, Claude Code, Copilot, ChatGPT, etc.):
- The agent will read `AGENTS.md`, greet your team, recite the competition ground rules, and collect your `I agree` confirmation.
- Once confirmed, the agent will **automatically log every prompt and task** in `docs/PROMPTS_LOG.md` as you build.

### Step 3: Build & Ship
- Author your application code inside `src/`.
- Document your technical approach in `docs/APPROACH.md`.
- Deploy your application and record live details in `deployment/README.md`.
- Update `metadata/submission.yaml` with your final commit SHA before the deadline.

---

*Build freely. Use AI freely. Secure what you build. Document what you claim. Prove what you implemented.*
