# AI Acceptable Use and Risk Management Policy

| Field | Value |
|---|---|
| Policy ID | POL-AI-001 |
| Version | 1.0 |
| Owner | Chief Risk Officer |
| Approved by | AI Risk Committee |
| Effective date | [Insert date] |
| Review cycle | Annually, or after a major AI incident or regulatory change |
| NIST AI RMF alignment | GOVERN 1.1, 1.2, 1.4, 1.6, 2.1, 4.1, 6.1 |

---

## 1. Purpose

This policy sets the rules for how Meridian Trust Bank selects, builds, buys, deploys, and monitors artificial intelligence (AI) systems so that they are **safe, secure, fair, transparent, and compliant** with law and regulation.

## 2. Scope

Applies to all employees, contractors, and third parties who build, buy, configure, operate, or use AI systems on behalf of Meridian, including generative AI (GenAI) tools, machine learning models, and AI features embedded in vendor products.

## 3. Definitions

| Term | Meaning |
|---|---|
| **AI system** | A machine-based system that produces outputs such as predictions, content, recommendations, or decisions (per NIST AI RMF / OECD definition). |
| **Generative AI** | AI that creates text, images, code, or other content (e.g., large language models). |
| **High-impact AI** | An AI system that interacts directly with customers, uses Confidential/Restricted data, or influences decisions about customers' money, credit, or access to services. |
| **AI System Owner** | The business leader accountable for an AI system and its risks. |
| **Human-in-the-loop** | A person reviews or can override AI output before it affects a customer. |

## 4. Policy statements

### 4.1 Governance and accountability
1. Every AI system **must** have a named AI System Owner and be recorded in the **AI System Inventory** before use.
2. The **AI Risk Committee** (see AI Governance Charter) oversees AI risk and approves all high-impact AI systems before production.
3. AI risk is part of the enterprise risk management (ERM) program and uses the same risk-appetite statement.

### 4.2 Risk assessment before deployment
1. All AI systems **must** complete an **AI Impact Assessment** before production use.
2. High-impact AI systems **must** also complete security testing (including adversarial/red-team testing for GenAI), bias/fairness testing where relevant, and a privacy review.
3. Risks must be recorded in the **AI Risk Register** and scored using the enterprise 5×5 risk matrix.
4. Risks rated **High or Critical** after controls require formal risk acceptance by the CRO.

### 4.3 Data protection
1. Customer PII, account numbers, card data, and authentication secrets **must not** be sent to an AI model unless the use is approved and the data is minimized, masked, or tokenized.
2. Employees **must not** paste Confidential or Restricted data into public or unapproved AI tools.
3. AI vendors **must not** use Meridian data to train their models unless approved in contract.
4. AI logs and transcripts are classified **Restricted** and follow the records retention schedule.

### 4.4 Transparency
1. Customers **must** be told when they are interacting with an AI system.
2. Customer-facing AI must offer an easy way to reach a human.
3. AI-generated content used in customer communications must be reviewed or clearly labeled.

### 4.5 Fairness and consumer protection
1. AI systems **must not** treat customers differently based on protected characteristics.
2. Customer-facing AI must not make binding promises (e.g., fee waivers, rate changes, credit approvals) unless the action is authorized by a system of record.

### 4.6 Security
1. AI systems follow the Information Security Policy and secure development standards.
2. GenAI systems must have controls against prompt injection, data leakage, and misuse (see OWASP Top 10 for LLM Applications).
3. AI systems must be monitored, and AI-related incidents handled under the **AI Incident Response Playbook**.

### 4.7 Third-party AI
1. AI vendors must complete third-party risk due diligence, including the AI vendor questionnaire.
2. Contracts must address data use, security, model change notification, incident notification, and audit rights.

### 4.8 Monitoring and decommissioning
1. High-impact AI systems are reviewed **at least quarterly** against defined metrics.
2. AI systems that no longer meet risk tolerance must be paused, fixed, or retired.

## 5. Approved and prohibited uses (employees)

| Allowed | Not allowed |
|---|---|
| Using approved enterprise AI tools for drafting, summarizing, and coding with Internal data | Pasting customer PII, account numbers, or passwords into any AI tool not approved for that data |
| Using AI output as a starting point that you review | Sending AI output to customers without review |
| Experimenting in approved sandboxes | Using AI to make final credit, employment, or account-closure decisions without human review |
| | Using personal AI accounts for bank work |

## 6. Roles and responsibilities

See the [RACI matrix](raci-matrix.md).

## 7. Exceptions

Exceptions must be requested in writing, include a risk assessment and compensating controls, be approved by the CRO, and expire within 12 months.

## 8. Enforcement

Violations may result in disciplinary action up to and including termination, and may be reported to regulators where required.

## 9. Related documents

- AI Governance Charter (`01-govern/ai-governance-charter.md`)
- AI System Inventory (`02-map/ai-system-inventory.md`)
- AI Risk Register (`03-measure/ai-risk-register.xlsx`)
- AI Incident Response Playbook (`04-manage/ai-incident-response-playbook.md`)
- Information Security Policy, Data Classification Standard, Third-Party Risk Management Policy (existing)
