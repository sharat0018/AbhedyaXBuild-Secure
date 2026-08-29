# Agent Evidence Directory

## Purpose

This directory is the **structured evidence layer** for your Build Secure 24 project.
It provides standardized templates for documenting your security posture, development
architecture, and project metadata.

This evidence is consumed during evaluation. Accurate, honest documentation is essential.

---

## Directory Structure

```
agent/
├── README.md                 ← This file
├── security/                 ← Security evidence
│   ├── SECURITY_IMPLEMENTATIONS.md   ← What you secured and how
│   ├── THREAT_MODEL.md               ← Your threat analysis
│   ├── SECURITY_TESTING.md           ← Security tests performed
│   ├── SECURITY_DECISIONS.md         ← Why you chose specific approaches
│   └── REPOSITORY_THREAT_MODEL.md    ← Threat model of repo infrastructure
├── development/              ← Development documentation
│   ├── ARCHITECTURE.md       ← System design and components
│   ├── TECH_STACK.md         ← Technologies used
│   └── DESIGN_DECISIONS.md   ← Design rationale
└── metadata/                 ← Machine-readable metadata
    ├── team.yaml             ← Team information
    ├── security-manifest.yaml ← Machine-readable security evidence
    └── submission.yaml       ← Submission metadata
```

---

## Evaluator Integration Contract

This section defines the interface between participant repositories and the future
**Abhedya Security Evidence Agent**.

### What the Evaluator Consumes

The organizer-side evaluation system may consume the following from your repository:

| Asset | Location | Format |
|-------|----------|--------|
| Source code | `src/` | Language-specific |
| Project approach | `docs/APPROACH.md` | Markdown |
| AI prompts log | `docs/PROMPTS_LOG.md` | Markdown |
| Security manifest | `agent/metadata/security-manifest.yaml` | YAML (schema-validated) |
| Security implementations | `agent/security/SECURITY_IMPLEMENTATIONS.md` | Markdown (structured) |
| Threat model | `agent/security/THREAT_MODEL.md` | Markdown (structured) |
| Security tests | `agent/security/SECURITY_TESTING.md` | Markdown (structured) |
| Security decisions | `agent/security/SECURITY_DECISIONS.md` | Markdown (structured) |
| Architecture | `agent/development/ARCHITECTURE.md` | Markdown |
| Tech stack | `agent/development/TECH_STACK.md` | Markdown |
| AI usage log | `AI_USAGE.md` | Markdown |
| Team metadata | `agent/metadata/team.yaml` | YAML (schema-validated) |
| Submission metadata | `agent/metadata/submission.yaml` | YAML (schema-validated) |
| Test suite | `tests/` | Language-specific |
| Deployment config | `deployment/` | Format varies |

---

## Evidence Integrity Principle

Every security claim follows this chain:

```
CLAIM → EVIDENCE → VERIFICATION → HUMAN DECISION
```

**Example:**

| Stage | Detail |
|-------|--------|
| **Claim** | `SEC-AUTHZ-001 IMPLEMENTED` |
| **Evidence** | `src/middleware/rbac.ts` |
| **Automated Verification** | Authorization test passes |
| **Runtime Verification** | Protected endpoint rejects unauthorized access |
| **Human Decision** | Verified / Partial / Failed |
