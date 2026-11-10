# AI Impact Assessment — AskMeridian

| Field | Value |
|---|---|
| System ID | AI-001 |
| System Owner | VP Digital Banking |
| Assessor | GRC Analyst — AI Risk |
| Assessment date | [Insert date] |
| Risk tier | **High-impact** |
| NIST AI RMF alignment | MAP 1.1–1.6, 2.1–2.3, 3.1–3.5, 4.1–4.2, 5.1–5.2 |

---

## 1. Context (MAP 1)

### 1.1 Intended purpose
Answer customer questions 24/7, reduce call-center volume by ~30%, and give faster help with common tasks (balance checks, product questions, password-reset requests).

### 1.2 Intended users and setting
- Retail and small-business customers on the website and mobile app
- Customers may be stressed (e.g., suspected fraud), have low financial literacy, use English as a second language, or use assistive technology

### 1.3 Out-of-scope / prohibited uses
The bot **must not**: give investment, tax, or legal advice; approve or promise credit, fee waivers, or rate changes; move money; change account details; collect full SSNs, card numbers, or passwords.

### 1.4 Business value vs. risk (MAP 1.4, 3.1)
| Benefit | Estimate |
|---|---|
| Call deflection | ~12,000 calls/month |
| Cost savings | ~$900k/year (estimate) |
| Customer experience | 24/7 availability, shorter wait times |

The benefits are meaningful, so the recommendation is to **launch with controls** rather than cancel the project.

### 1.5 Legal and regulatory context (MAP 1.1)
| Requirement | Applies because | Impact on the system |
|---|---|---|
| GLBA (Safeguards & Privacy Rules) | Customer financial data | Protect PII; vendor oversight |
| UDAAP / consumer protection | Bot statements to consumers | Inaccurate promises can be "deceptive" |
| Fair lending / anti-discrimination laws | Customer treatment | Consistent service quality across groups |
| PCI DSS | Customers may type card numbers | Card data must not be stored in logs |
| ADA (accessibility) | Public-facing digital service | Must work with screen readers |
| GDPR | EU customers | Lawful basis, data minimization, transfer safeguards |
| EU AI Act, Article 50 | Chatbot interacting with EU users | Must tell users they are talking to AI |
| Banking regulator guidance on third-party risk and model risk | Vendor model; outputs relied on by customers | Due diligence, ongoing monitoring, validation |

## 2. System categorization (MAP 2)

| Question | Answer |
|---|---|
| AI task | Text generation + retrieval (RAG) + limited tool use (account lookup, ticket creation) |
| Autonomy | Acts on its own in conversation; escalates to a human on request or when confidence is low |
| Human oversight | Human agents review escalations; no human reviews each answer before it is sent |
| Known limitations (MAP 2.2) | LLMs can produce false but confident answers ("hallucinations"); can be manipulated by crafted input; knowledge limited to retrieved documents |
| Scientific/technical validity (MAP 2.3) | Vendor model card reviewed; internal accuracy testing on 500 sample questions planned (see Metrics & Testing Plan) |

## 3. Stakeholders and impacts (MAP 3, MAP 5)

| Stakeholder | Possible positive impact | Possible negative impact | Severity |
|---|---|---|---|
| Customers | Fast, 24/7 help | Wrong info leading to fees or losses; data exposure; account takeover | High |
| Vulnerable customers (elderly, limited English, disabilities) | Easier access | Lower answer quality; harder to reach a human; manipulation by fraudsters | High |
| Call-center staff | Fewer repetitive calls | Job changes; handling angrier escalations | Medium |
| The bank | Cost savings, modern brand | Regulatory fines, lawsuits, reputational damage | High |
| Regulators | — | Consumer-harm complaints | Medium |
| Society | Better financial access | Erosion of trust in banking if AI fails publicly | Low |

**How stakeholders were engaged (MAP 5.2):** pilot customer survey (n=300), call-center focus group, accessibility review with an external tester, compliance and legal workshops.

## 4. Trustworthiness analysis (NIST AI RMF characteristics)

| Characteristic | Key concern for AskMeridian | Linked risks |
|---|---|---|
| Valid and reliable | Hallucinated product info, outdated rates | R05, R14 |
| Safe | Harmful or manipulative output to vulnerable customers | R11 |
| Secure and resilient | Prompt injection, data leakage, vendor outage, cost abuse | R01, R02, R04, R09, R12, R18 |
| Accountable and transparent | Customers unaware of AI; weak logging | R10, R13 |
| Explainable and interpretable | Cannot explain answers in a complaint | R16 |
| Privacy-enhanced | PII in logs; vendor data use | R03, R08, R20 |
| Fair, with harmful bias managed | Uneven quality across language/dialect; accessibility | R06, R19 |

## 5. Third-party components (MAP 4)

| Component | Supplier | Key risks | Mitigation |
|---|---|---|---|
| Foundation model | Vendor A | Silent model updates, data retention, outage | Contract terms (version pinning, change notice, no training on data, zero-retention), SLA, regression tests |
| Vector database | Cloud provider | Data exposure | Encryption, access controls, private networking |
| Content-safety filter | Vendor A | Gaps in filtering | Layer with in-house rules; red-team testing |

## 6. Risk identification summary

**20 risks** identified. Full scoring in [`03-measure/ai-risk-register.xlsx`](../03-measure/ai-risk-register.xlsx).

## 7. Assessment conclusion

AskMeridian is a **High-impact** AI system. It is **not** a "high-risk" system under the EU AI Act (it does not decide creditworthiness), but it has **transparency obligations** under Article 50.

**Recommendation:** Proceed to MEASURE and MANAGE. Production approval is conditional on the must-fix items in the [Risk Treatment Plan](../04-manage/risk-treatment-plan.md).
