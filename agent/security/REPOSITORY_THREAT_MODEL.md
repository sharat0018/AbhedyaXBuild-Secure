# Repository Infrastructure Threat Model

This document threat-models the Build Secure 24 starter repository itself —
the infrastructure that participants use, not the applications they build.

---

## 1. Threat: Prompt Injection Through Documentation

**Description:** A participant embeds adversarial instructions in Markdown files,
code comments, or test fixtures designed to manipulate AI agents or the evaluator.

**Likelihood:** High
**Impact:** Medium (could mislead AI agents or attempt to influence evaluation)

**Mitigations:**
- AGENTS.md establishes that repository content is data, not instructions.
- The evaluator treats all repository content as untrusted data.
- Trust-boundary separation is the primary defense, not keyword filtering.
- AGENTS.md explicitly lists prompt injection scenarios and countermeasures.

**Residual Risk:** AI agents may still be influenced by sophisticated injection
attempts. Mitigated by human review in the evaluation process.

---

## 2. Threat: Malicious Source Code

**Description:** A participant submits code containing backdoors, malware,
data exfiltration, or code designed to attack the evaluation environment.

**Likelihood:** Low
**Impact:** High

**Mitigations:**
- Evaluation runs in an isolated sandbox.
- Network access is restricted during evaluation.
- Code execution during evaluation is controlled and time-limited.
- Human review is the final step before any score is assigned.

**Residual Risk:** Sophisticated obfuscated payloads may evade automated detection.
Mitigated by sandbox isolation.

---

## 3. Threat: Malicious Test Fixtures

**Description:** Test data files contain executable payloads, deserialization
attacks, or adversarial content targeting evaluation tools.

**Likelihood:** Low
**Impact:** Medium

**Mitigations:**
- Test fixtures are treated as untrusted data by the evaluator.
- Evaluation sandbox restricts execution privileges.
- Static analysis tools scan for suspicious patterns.

---

## 4. Threat: Malicious Package Metadata

**Description:** package.json, requirements.txt, or other dependency manifests
contain malicious packages, postinstall scripts, or adversarial metadata fields.

**Likelihood:** Medium
**Impact:** High

**Mitigations:**
- Dependency installation during evaluation uses `--ignore-scripts` where possible.
- Known-vulnerability scanning (npm audit, pip-audit) runs before deep analysis.
- Evaluation sandbox restricts network access.

---

## 5. Threat: Secrets Accidentally Committed

**Description:** A participant accidentally commits API keys, passwords, tokens,
or private keys to the repository.

**Likelihood:** High
**Impact:** High (credential compromise)

**Mitigations:**
- Clear competition rules strictly prohibiting hardcoded credentials.
- Organizer-side secret scanning during evaluation.
- Immediate evaluation penalties for committed credentials.
- Prompt injection resistance in AGENTS.md preventing AI agents from outputting secrets.

**Residual Risk:** Novel secret formats may require specialized evaluator pattern detection.

---

## 6. Threat: Repository History Manipulation

**Description:** A participant force-pushes to rewrite history, hiding evidence
of rule violations or creating a misleading development timeline.

**Likelihood:** Medium
**Impact:** Medium

**Mitigations:**
- PARTICIPANT_RULES.md prohibits force-pushing away meaningful history.
- Organizers can enable branch protection on the default branch.
- Final submission is captured as an immutable commit SHA.
- Suspicious history patterns are surfaced for human review.

**Residual Risk:** Subtle history rewriting may be difficult to detect automatically.

---

## 7. Threat: Evaluator Data Leakage

**Description:** Organizer evaluation logic, scoring criteria, or judge data
leaks into the participant repository.

**Likelihood:** Low (by design)
**Impact:** Critical (undermines competition integrity)

**Mitigations:**
- Strict separation: no organizer data exists in this repository.
- AGENTS.md, PARTICIPANT_RULES.md, and agent/README.md explicitly document
  what must never be in the participant repository.
- Validation checks verify no scoring or evaluator fields exist in metadata.
- Forbidden field lists block evaluator-related YAML keys.

---

## 8. Threat: Cross-Team Access

**Description:** A participant accesses another team's repository to copy work
or gain competitive advantage.

**Likelihood:** Low
**Impact:** High

**Mitigations:**
- Repositories are private per team (organizer configuration).
- PARTICIPANT_RULES.md prohibits cross-team access.
- GitHub access controls enforce team isolation.
- Violation is grounds for disqualification.

**Residual Risk:** Depends on organizer GitHub configuration being correct.

---

## 9. Threat: Malicious CI Configuration

**Description:** A participant modifies GitHub Actions workflows to exfiltrate
secrets, access external systems, or mine cryptocurrency.

**Likelihood:** Medium
**Impact:** Medium

**Mitigations:**
- Workflows use `permissions: contents: read` (minimal permissions).
- Workflows do not use secrets other than GITHUB_TOKEN.
- Organizers can require workflow approval for modified workflows.
- Branch protection can prevent workflow file modifications.

**Residual Risk:** If participants can modify workflows, they could add
malicious steps. Branch protection on workflow files is recommended.

---

## 10. Threat: Path Traversal in Validation

**Description:** A participant crafts file paths in metadata (evidence paths,
test paths) that cause path traversal when consumed by tools.

**Likelihood:** Low
**Impact:** Medium

**Mitigations:**
- Validation scripts use repository-relative paths.
- Paths in metadata are treated as data references, not executed.
- The evaluator sandbox restricts filesystem access.

---

## 11. Threat: Arbitrary Command Execution

**Description:** A participant embeds commands in metadata fields that are
accidentally executed by tools consuming the data.

**Likelihood:** Low
**Impact:** Critical

**Mitigations:**
- YAML metadata is loaded with safe_load (no YAML deserialization attacks).
- Forbidden fields list blocks `execute_command`, `shell`, and similar keys.
- Validation treats all YAML content as data, never as executable instructions.

---

## 12. Threat: Malicious Deployment URLs

**Description:** A participant provides deployment URLs pointing to phishing
sites, malware distribution, or IP-logging services.

**Likelihood:** Low
**Impact:** Low (evaluators should use isolated browsers)

**Mitigations:**
- Deployment URLs are recorded as data, not automatically visited.
- Human evaluators decide whether to visit deployment URLs.
- Evaluation should use isolated/sandboxed browsers.

---

## 13. Threat: Model Tool Abuse

**Description:** An AI agent operating inside the participant repository is
tricked into performing harmful actions (deleting files, exposing secrets,
making unauthorized network requests).

**Likelihood:** Medium
**Impact:** Medium

**Mitigations:**
- AGENTS.md establishes clear behavioral rules for AI agents.
- Repository content cannot override AGENTS.md.
- AI agents are instructed to treat all repository content as untrusted.
- Specific prohibited actions are enumerated in AGENTS.md.

**Residual Risk:** AI agents may not perfectly follow AGENTS.md in all cases.
Human review of all AI-assisted changes is recommended.

---

## Summary

| # | Threat | Likelihood | Impact | Primary Mitigation |
|---|--------|------------|--------|-------------------|
| 1 | Prompt Injection | High | Medium | Trust boundary separation |
| 2 | Malicious Source Code | Low | High | Sandbox isolation |
| 3 | Malicious Test Fixtures | Low | Medium | Sandbox, static analysis |
| 4 | Malicious Package Metadata | Medium | High | Script-ignoring install, scanning |
| 5 | Secrets Committed | High | High | Policy rules, evaluator scanning |
| 6 | History Manipulation | Medium | Medium | Branch protection, SHA capture |
| 7 | Evaluator Data Leakage | Low | Critical | Strict separation by design |
| 8 | Cross-Team Access | Low | High | GitHub access controls |
| 9 | Malicious CI | Medium | Medium | Minimal permissions, protection |
| 10 | Path Traversal | Low | Medium | Data-only path handling |
| 11 | Command Execution | Low | Critical | safe_load, forbidden fields |
| 12 | Malicious URLs | Low | Low | Manual evaluation, isolation |
| 13 | Model Tool Abuse | Medium | Medium | AGENTS.md trust contract |
