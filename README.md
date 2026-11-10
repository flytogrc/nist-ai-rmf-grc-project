# AI Risk Management Program — NIST AI RMF 1.0

**Portfolio project:** An AI governance, risk, and compliance (GRC) program for a generative AI customer-support chatbot at a fictional bank, built on the **NIST AI Risk Management Framework (AI RMF 1.0)** and the **NIST AI 600-1 Generative AI Profile**.

> **Disclaimer:** Meridian Trust Bank and its "AskMeridian" assistant are fictional. All people, numbers, and findings are made up for learning purposes.

## Why I built this

I wanted to learn how companies manage the risks of AI, so I created a fictional bank that's launching an AI chatbot and played the role of the GRC analyst checking it before launch. I used the NIST AI Risk Management Framework to find the risks, score them, and decide what controls the bank needs.

GRC matters to me because it lets me help and protect people, which is something I've always wanted to do. When I was 11, I was diagnosed with cancer, and I beat it at 15. That experience showed me how much it means when people look out for you, and now I want to do the same for others.

---

## Scenario at a glance

| Item | Detail |
|---|---|
| Organization | Meridian Trust Bank (fictional regional bank, ~2,400 employees, ~600k customers) |
| AI system | **AskMeridian** — an LLM-powered chatbot on the website and mobile app |
| What it does | Answers account questions, explains products, helps reset online banking, hands off to human agents |
| Why it's risky | Handles customer financial data, gives answers customers rely on, faces the public internet |
| My role | GRC Analyst assigned to stand up the AI risk program before full launch |

Full background: [00-scenario/company-scenario.md](00-scenario/company-scenario.md)

---

## Project structure (mapped to the NIST AI RMF functions)

| Folder | AI RMF function | Deliverables |
|---|---|---|
| [00-scenario](00-scenario/) | — | Company and system background |
| [01-govern](01-govern/) | **GOVERN** — culture, policy, accountability | AI Acceptable Use Policy, AI Governance Charter, RACI matrix |
| [02-map](02-map/) | **MAP** — context and risk identification | AI System Inventory, AI Impact Assessment |
| [03-measure](03-measure/) | **MEASURE** — analyze, assess, track | AI Risk Register (Excel), Metrics & Testing Plan |
| [04-manage](04-manage/) | **MANAGE** — prioritize, treat, monitor | Risk Treatment Plan, AI Incident Response Playbook |
| [05-crosswalk](05-crosswalk/) | — | Control mapping: NIST AI RMF ↔ ISO/IEC 42001 ↔ EU AI Act ↔ NIST CSF 2.0 ↔ OWASP LLM Top 10 |
| [executive-summary.md](executive-summary.md) | — | One-page risk brief for leadership |

---

## Key results

- Identified and scored **20 AI risks** using a 5×5 likelihood × impact model.
- **14 risks rated High or Critical before controls** (7 Critical, 7 High) — including PII in chat logs, prompt injection, hallucinated financial information, and unannounced vendor model changes.
- Designed **26 controls**; after treatment, **0 risks remain High or Critical** and the average risk score drops from 13.1 to 5.4 (~59%).
- Mapped controls to 5 frameworks (NIST AI RMF, ISO/IEC 42001, EU AI Act, NIST CSF 2.0, OWASP LLM Top 10).
- Wrote a governance structure (AI Risk Committee, RACI) and an AI-specific incident response playbook.
- Recommended a **conditional go-live** with 6 must-fix items.

---

## Skills demonstrated

- Risk assessment and risk register management (likelihood × impact, inherent vs. residual risk)
- Policy writing and governance design
- Framework mapping (NIST AI RMF, ISO/IEC 42001, EU AI Act, NIST CSF 2.0)
- Generative AI threat awareness (OWASP Top 10 for LLM Applications)
- Third-party / vendor risk management
- Communicating risk to executives

---

## References

- NIST AI 100-1, *Artificial Intelligence Risk Management Framework (AI RMF 1.0)*, January 2023
- NIST AI 600-1, *AI RMF: Generative Artificial Intelligence Profile*, July 2024
- NIST AI RMF Playbook — NIST Trustworthy & Responsible AI Resource Center (airc.nist.gov)
- ISO/IEC 42001:2023, *AI management system*
- Regulation (EU) 2024/1689 (EU AI Act)
- NIST Cybersecurity Framework (CSF) 2.0
- OWASP Top 10 for Large Language Model Applications (2025)
