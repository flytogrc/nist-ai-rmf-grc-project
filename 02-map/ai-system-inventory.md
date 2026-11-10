# AI System Inventory

NIST AI RMF alignment: GOVERN 1.6 (inventory of AI systems), MAP 1.1, MAP 4.1.

**Risk tiering rule** (from POL-AI-001):
- **High-impact:** customer-facing, OR uses Confidential/Restricted data, OR influences decisions about customers' money, credit, or access.
- **Medium:** internal use with Internal/Confidential data and a human reviews all output.
- **Low:** internal use with Public/Internal data only.

| ID | System | Description | Type | Built / Bought | Vendor | Business Owner | Data used (highest class) | Customer-facing | Risk tier | EU AI Act category | Status | Last assessed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AI-001 | **AskMeridian** | GenAI chatbot for customer support (RAG + account lookups) | LLM / GenAI | Built on vendor model | Vendor A (foundation model API) | VP Digital Banking | Restricted (chat transcripts), Confidential (PII) | Yes | **High-impact** | Limited risk — transparency duties (Art. 50) | Pilot | [Date] — **this project** |
| AI-002 | FraudShield | Card transaction fraud scoring | ML classifier | Bought | Vendor B | Head of Fraud Ops | Confidential | Indirect | High-impact | Not high-risk (fraud detection carved out of Annex III 5(b)) | Production | Phase 2 |
| AI-003 | CreditAssist | Small-business credit pre-screening | ML model | Built | — | Chief Credit Officer | Confidential | Indirect | High-impact | **High-risk** (Annex III 5(b) creditworthiness) | Development | Phase 2 |
| AI-004 | Copilot for staff | Enterprise GenAI assistant for email/docs | LLM / GenAI | Bought | Vendor C | CIO | Confidential | No | Medium | Minimal risk | Production | Phase 2 |
| AI-005 | Call-center speech analytics | Transcribes and tags call topics | Speech-to-text + NLP | Bought | Vendor D | Head of Contact Center | Restricted | No | High-impact | Minimal / limited | Production | Phase 2 |

## Inventory fields — why they matter

| Field | Why a GRC analyst cares |
|---|---|
| Business Owner | Accountability — someone owns the risk (GOVERN 2.1) |
| Built / Bought + Vendor | Drives third-party risk work (GOVERN 6.1, MAP 4.1) |
| Data class | Drives privacy and security control requirements |
| Risk tier | Decides how much assessment and approval is needed |
| EU AI Act category | Decides legal obligations for EU customers |
| Last assessed | Shows whether the system is overdue for review |
