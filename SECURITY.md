# Security Evaluation Scope & Policy — Build Secure 24

**Abhedya — VBIT Cybersecurity Forum, Vignana Bharathi Institute of Technology, Hyderabad**

---

## 1. Security Evaluation Overview

Security contributes **50% of the total competition score**.

Your submitted codebase, architecture, and live deployment will undergo automated and manual security evaluation by the Abhedya Security Team (30 marks) and External Cybersecurity Experts (20 marks).

Teams are responsible for identifying, designing, and implementing appropriate security controls for their application.

---

## 2. Assessed Security Domains

Evaluators will independently test and audit your solution across core security dimensions, including but not limited to:

1. **Authentication & Identity Management**
2. **Access Control & Authorization Boundaries**
3. **Input Handling & Injection Resistance**
4. **API Security & Transport Layer Security**
5. **Data Protection, Storage, & Cryptography**
6. **Session Management & Token Lifecycle**
7. **Secrets Management & Credential Handling**
8. **Logging, Auditing, & Error Handling**
9. **File and Asset Processing Security**
10. **System Configuration, Dependencies, & Deployment Hardening**

---

## 3. Evaluation Principles & Penalties

- **No Guidance / Independent Engineering**: Evaluators will inspect code for vulnerabilities, misconfigurations, and weaknesses. Architectural flaws and security regressions will impact the final score.
- **Evidence Verification**: Any claim made in `agent/security/SECURITY_IMPLEMENTATIONS.md` and `agent/metadata/security-manifest.yaml` must be backed by working code in `src/` and verified tests in `tests/`.
- **False Claims Penalty**: Claiming a security control as `IMPLEMENTED` when it is absent, broken, or vulnerable will incur scoring penalties.
- **Zero Secrets Policy**: Committing API keys, private keys, database credentials, or tokens anywhere in the repository will result in immediate security check failure.


