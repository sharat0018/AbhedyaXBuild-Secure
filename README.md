# Build Secure 24 — Participant Starter Repository

**Abhedya — VBIT Cybersecurity Forum, Vignana Bharathi Institute of Technology, Hyderabad**

Welcome to the official Build Secure 24 hackathon starter repository. This repository contains the standardized documentation and evidence structure for your team's project during the 24-hour competition.

---

## Competition Overview

- **Duration**: 24 Hours
- **Team Size**: Exactly 4 participants per team
- **Evaluation Weightage**: 
  - Development & Implementation: 50 Marks
  - Abhedya Security Evaluation: 30 Marks
  - External Cybersecurity Experts: 20 Marks
- **Core Requirement**: All code must be authored live during the event. Importing pre-built or third-party repositories is strictly prohibited.

---

## Repository Structure

```
├── AGENTS.md                  ← AI agent behavioral contract (Trust Root)
├── README.md                  ← This file
├── PARTICIPANT_RULES.md       ← Official competition rules
├── SECURITY.md                ← Security evaluation scope & assessed domains
├── AI_USAGE.md                ← AI usage provenance documentation
│
├── docs/                      ← Project approach & prompts log
│   ├── APPROACH.md            ← Architecture & implementation strategy
│   └── PROMPTS_LOG.md         ← Significant AI prompts & engineering log
│
├── agent/                     ← Standardized evidence layer
│   ├── security/              ← Security evidence documentation
│   │   ├── SECURITY_IMPLEMENTATIONS.md
│   │   ├── THREAT_MODEL.md
│   │   ├── SECURITY_TESTING.md
│   │   ├── SECURITY_DECISIONS.md
│   │   └── REPOSITORY_THREAT_MODEL.md
│   ├── development/           ← System design documentation
│   │   ├── ARCHITECTURE.md
│   │   ├── TECH_STACK.md
│   │   └── DESIGN_DECISIONS.md
│   └── metadata/              ← Machine-readable metadata
│       ├── team.yaml
│       ├── security-manifest.yaml
│       └── submission.yaml
│
├── src/                       ← Application source code
└── deployment/                ← Deployment configuration & documentation
```

---

## Workflow Guide

### 1. Initialize Team Metadata
Edit `agent/metadata/team.yaml` with your organizer-assigned Team ID and all 4 team members.

### 2. Strategy & AI Onboarding
- When opened in an AI coding environment, the AI agent reads [`AGENTS.md`](AGENTS.md) and automatically logs prompt records and architecture strategy into [`docs/APPROACH.md`](docs/APPROACH.md) and [`docs/PROMPTS_LOG.md`](docs/PROMPTS_LOG.md).

### 3. Build & Implement
- Develop your application inside [`src/`](src/).
- Teams are free to choose any language, framework, or architecture suitable for the problem statement.

### 4. Provide Security & Design Evidence
As features and security controls are built:
- The AI agent automatically synchronizes implemented security controls into [`agent/security/SECURITY_IMPLEMENTATIONS.md`](agent/security/SECURITY_IMPLEMENTATIONS.md) and [`agent/metadata/security-manifest.yaml`](agent/metadata/security-manifest.yaml).
- Document threat analysis in [`agent/security/THREAT_MODEL.md`](agent/security/THREAT_MODEL.md) and system architecture in [`agent/development/ARCHITECTURE.md`](agent/development/ARCHITECTURE.md).

### 5. Final Submission Freeze
1. Deploy your application and record deployment instructions in [`deployment/README.md`](deployment/README.md).
2. Record your final submission details and commit SHA in [`agent/metadata/submission.yaml`](agent/metadata/submission.yaml).
3. Freeze repository before the 24-hour deadline.

---

*Build freely. Use AI freely. Secure what you build. Document what you claim. Prove what you implemented.*
