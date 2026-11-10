# Control Crosswalk — NIST AI RMF ↔ ISO/IEC 42001 ↔ EU AI Act ↔ NIST CSF 2.0 ↔ OWASP LLM Top 10

**Why this matters:** Most organizations must satisfy several frameworks at once. A crosswalk shows that one control can provide evidence for many requirements ("test once, comply many"). Control IDs match the `Control Library` tab in [ai-risk-register.xlsx](../03-measure/ai-risk-register.xlsx).

> **Note:** ISO/IEC 42001 references are to the 2023 edition (clauses 4–10 and Annex A). EU AI Act references are to Regulation (EU) 2024/1689. Mappings are my professional judgment for a portfolio project — always verify against the official texts.

## 1. Program-level mapping (NIST AI RMF functions)

| NIST AI RMF function | ISO/IEC 42001 | EU AI Act (as applied to AskMeridian) | NIST CSF 2.0 | Project deliverable |
|---|---|---|---|---|
| **GOVERN** | Cl. 5 Leadership, 5.2 AI policy; A.2 Policies; A.3 Internal organization | Art. 4 AI literacy | GV (Govern): GV.OC, GV.RM, GV.RR, GV.PO, GV.OV, GV.SC | AI Policy, Governance Charter, RACI |
| **MAP** | Cl. 4 Context; 6.1.4 AI system impact assessment; A.5 Assessing impacts; A.4 Resources | Art. 6 + Annex III (risk classification); Art. 50 applicability | ID.AM (asset mgmt), ID.RA (risk assessment), GV.OC | AI Inventory, Impact Assessment |
| **MEASURE** | 6.1.2 AI risk assessment; Cl. 9 Performance evaluation; A.6.2.4 Verification & validation | Art. 50 (transparency testing); Art. 15 concepts (accuracy, robustness, cybersecurity) as good practice | ID.RA, DE.CM (continuous monitoring), ID.IM | Risk Register, Metrics & Testing Plan |
| **MANAGE** | 6.1.3 AI risk treatment; Cl. 8 Operation; Cl. 10 Improvement; A.10 Third-party relationships | Art. 73 concepts (serious-incident reporting) as good practice | RS (Respond), RC (Recover), GV.SC, ID.IM | Treatment Plan, Incident Playbook |

### EU AI Act classification for AskMeridian
- **Not high-risk:** a customer-service chatbot is not listed in Annex III. (Credit scoring — AI-003 CreditAssist — *is* high-risk and is covered in Phase 2.)
- **Transparency obligations apply (Art. 50(1)):** users must be told they are interacting with an AI system.
- **AI literacy (Art. 4):** staff operating the system need adequate AI training.
- **General-purpose AI model obligations (Art. 53–55)** fall mainly on **Vendor A** as the model provider; Meridian should obtain the vendor's technical documentation through due diligence.

## 2. Control-level crosswalk

| ID | Control | NIST AI RMF | ISO/IEC 42001 | EU AI Act | NIST CSF 2.0 | OWASP LLM 2025 | Risks |
|---|---|---|---|---|---|---|---|
| C01 | System prompt hardening | MEASURE 2.7, MANAGE 2.2 | A.6.2.4 | — | PR.PS | LLM01, LLM07 | R01 |
| C02 | Input screening | MEASURE 2.7 | A.6.2.6 | — | PR.PS, DE.CM | LLM01 | R01 |
| C03 | Output screening | MEASURE 2.6, 2.7 | A.6.2.6 | — | PR.DS | LLM02, LLM05 | R01, R02, R11 |
| C04 | RAG content governance | MAP 4.1, MEASURE 2.7 | A.7.2, A.7.5 | — | PR.DS, PR.PS | LLM01, LLM04, LLM08 | R02, R14 |
| C05 | Data masking (DLP) | MEASURE 2.10 | A.7.4, A.6.2.8 | — | PR.DS | LLM02 | R03 |
| C06 | Least-privilege tool access | MEASURE 2.7 | A.6.2.4 | — | PR.AA | LLM06 | R04, R09 |
| C07 | Step-up auth for sensitive actions | MEASURE 2.7, MAP 3.5 | A.9.2 | Human oversight concept | PR.AA | LLM06 | R09 |
| C08 | Grounded answers with citations | MEASURE 2.5, 2.9 | A.6.2.4 | — | — | LLM09 | R05, R16, R17 |
| C09 | Commitment blocklist & disclaimers | MEASURE 2.5, MANAGE 2.2 | A.9.4 | — | — | LLM09 | R05, R15 |
| C10 | Red-team testing | MEASURE 2.7, 1.1 | A.6.2.4 | — | ID.RA, ID.IM | All | R01, R02, R04, R11 |
| C11 | Fairness testing | MEASURE 2.11 | A.5.4 | — | — | — | R06 |
| C12 | Vendor contract AI clauses | GOVERN 6.1, 6.2; MANAGE 3.1 | A.10.2, A.10.3 | Art. 53 (vendor info) | GV.SC | LLM03 | R07, R08 |
| C13 | Model regression suite | MEASURE 2.4, MANAGE 3.2 | A.6.2.4, A.6.2.6 | — | ID.IM, PR.PS | LLM03, LLM09 | R05, R06, R07 |
| C14 | Third-party due diligence | GOVERN 6.1, MAP 4.1 | A.10.3 | — | GV.SC | LLM03 | R07, R08 |
| C15 | AI disclosure & human handoff | GOVERN 4.2, MEASURE 2.8, MAP 3.5 | A.8.2 | **Art. 50(1)** | — | — | R06, R10, R15 |
| C16 | Logging & SIEM alerting | MEASURE 2.7, 3.1 | A.6.2.8 | — | DE.CM, DE.AE | LLM01, LLM02, LLM10 | R01, R03, R04, R09, R12, R13, R20 |
| C17 | Rate limiting & spend caps | MEASURE 2.7 | A.6.2.6 | — | PR.IR | LLM10 | R12 |
| C18 | Content freshness review | MEASURE 2.4 | A.7.4 | — | — | LLM08, LLM09 | R14 |
| C19 | Trace retention for explainability | MEASURE 2.8, 2.9 | A.6.2.8 | — | DE.AE | — | R16 |
| C20 | Customer guidance | MAP 3.4, GOVERN 4.2 | A.8.2 | Art. 50 (spirit) | — | LLM09 | R05, R17 |
| C21 | Failover & SLA | MANAGE 2.4, 3.1 | A.6.2.6 | — | PR.IR, RC.RP | — | R18 |
| C22 | Accessibility testing | MEASURE 2.11 | A.5.4 | Art. 16(l) concept (accessibility) | — | — | R19 |
| C23 | Shadow AI controls | GOVERN 1.4, 4.1 | A.2.2, A.9.2 | Art. 4 | PR.AT, PR.DS | LLM02 | R20 |
| C24 | AI incident response | MANAGE 2.3, 4.3; GOVERN 4.3 | A.8.4, Cl. 10.2 | Art. 73 concept | RS.MA, RS.CO, RC.RP | — | R03 |
| C25 | Regulatory change monitoring | GOVERN 1.1 | Cl. 4.1, 4.2 | All applicable | GV.OC | — | R15 |
| C26 | KRI monitoring & committee review | GOVERN 1.5, MEASURE 3.1, MANAGE 4.1 | Cl. 9.1, 9.3 | — | GV.OV, ID.IM | — | R13 |

## 3. OWASP Top 10 for LLM Applications (2025) coverage

| OWASP risk | Covered by risks | Covered by controls |
|---|---|---|
| LLM01 Prompt Injection | R01, R02 | C01, C02, C03, C04, C10, C16 |
| LLM02 Sensitive Information Disclosure | R03, R04, R08, R20 | C03, C05, C06, C12, C23 |
| LLM03 Supply Chain | R07, R08 | C12, C13, C14 |
| LLM04 Data and Model Poisoning | R02 (knowledge base) | C04 |
| LLM05 Improper Output Handling | R11 | C03 |
| LLM06 Excessive Agency | R04, R09 | C06, C07 |
| LLM07 System Prompt Leakage | R01 | C01 |
| LLM08 Vector and Embedding Weaknesses | R02, R14 | C04, C18 |
| LLM09 Misinformation | R05, R17 | C08, C09, C13, C20 |
| LLM10 Unbounded Consumption | R12 | C17 |

All 10 OWASP LLM risk categories are addressed.
