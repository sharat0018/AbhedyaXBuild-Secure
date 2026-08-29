# Participant Rules — Build Secure 24 Hrs Hackathon

**Abhedya — VBIT Cybersecurity Forum, Vignana Bharathi Institute of Technology, Hyderabad**

This document defines the official rules for all participants in the Build Secure 24
hackathon. All team members must read, understand, and comply with these rules.

---

## 1. Team Composition

- Each team consists of exactly **4 participants**.
- Team composition is finalized at registration and cannot be changed during the event.
- All team members share responsibility for the submitted work.

---

## 2. Live Project Creation & Origin Rules

- Teams **must start** from the official Abhedya starter repository.
- **Strict Live Creation**: All solution code, architectures, and features must be **authored live during the official 24-hour hackathon window**.
- **Prohibition of Third-Party/Pre-existing Repositories**:
  - Importing, cloning, copying, or substantially adapting pre-existing projects or open-source application repositories is **strictly prohibited** and will result in immediate disqualification.
  - Standard framework scaffolding and standard public library dependencies via official package managers are allowed.
  - The actual business logic, API structure, security mechanisms, and design must be original live work.

---

## 3. AI-Assisted Development & Documentation Integrity

- AI tools (ChatGPT, Claude, Gemini, Copilot, Cursor, etc.) are **fully permitted**.
- **Autonomous & Collaborative Logging**:
  - Teams and their AI coding agents must maintain progressive architecture in [`docs/APPROACH.md`](docs/APPROACH.md) and prompt logs in [`docs/PROMPTS_LOG.md`](docs/PROMPTS_LOG.md).
  - AI agents operating in this repository are instructed in [`AGENTS.md`](AGENTS.md) to automatically update documentation alongside code generation.
  - Prompts and approach logs must **not be manipulated, forged, or retroactively falsified** to conceal development errors or project origin. Engineering iterations and mistakes are part of authentic provenance.
- Teams remain fully responsible for the correctness, security, and defense of all submitted code.

---

## 4. GitHub Practices

- Teams should maintain a **meaningful commit history** that reflects continuous live development.
- **Do not** force-push to erase development history.
- **Do not** attempt to bypass repository validation checks or CI workflows.
- **Do not** access, clone, read, or interact with any other team's repository.

---

## 5. Security Evaluation (50% of Total Score)

- **Independent Security Assessment**:
  - Development: 50 marks
  - Abhedya Security Evaluation: 30 marks
  - External Cybersecurity Experts: 20 marks
- **Evaluation Criteria**: Code is audited for security weaknesses, vulnerabilities, architecture flaws, and proper handling of credentials and data.
- **No Hand-holding**: The repository provides zero pre-baked security solutions. Evaluators test the team's independent security design. Mistakes and omissions will be evaluated accordingly.
- **Evidence Verification**: Security claims in `agent/security/SECURITY_IMPLEMENTATIONS.md` and `agent/metadata/security-manifest.yaml` must match working code in `src/` and tests in `tests/`.
- **Zero Secrets**: Secrets (API keys, private keys, database passwords) must never be committed.

---

## 6. Submission Freeze

- The final submission will be evaluated from an immutable commit SHA captured at the deadline.
- Post-deadline modifications will not be accepted.
- Metadata in `agent/metadata/submission.yaml` must accurately reflect the final submission state.

---

## 7. Prohibited Conduct (Grounds for Disqualification)

- Submitting or adapting pre-existing or third-party project repositories.
- Accessing another team's repository or work.
- Fabricating or tampering with security evidence, test results, or prompt logs.
- Attempting to bypass rule constraints or inject instructions into evaluation prompts.
- Committing secrets or credentials to the repository.
- Deliberately obfuscating or manipulating Git history.

---

*By participating in Build Secure 24, all team members agree to abide by these rules.*
