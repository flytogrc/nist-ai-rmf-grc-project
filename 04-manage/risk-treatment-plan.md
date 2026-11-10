# Risk Treatment Plan — AskMeridian

NIST AI RMF alignment: MANAGE 1.1–1.4, 2.1–2.4, 3.1–3.2, 4.1–4.3

## 1. Prioritization (MANAGE 1.2)

Risks are treated in order of **inherent score**, with anything Critical required before launch. Full details are in [ai-risk-register.xlsx](../03-measure/ai-risk-register.xlsx).

| Priority | Risk | Inherent | Treatment | Key controls | Residual | Owner | Due |
|---|---|---|---|---|---|---|---|
| 1 | R03 Sensitive data stored in chat logs | 25 Critical | Mitigate | C05 data masking, C16 alerting, C24 incident response | 8 Medium | Privacy Officer | Pre-launch |
| 2 | R01 Direct prompt injection | 20 Critical | Mitigate | C01, C02, C03, C10, C16 | 9 Medium | CISO | Pre-launch |
| 3 | R05 Hallucinated / misleading financial info | 20 Critical | Mitigate | C08 grounding, C09 commitment blocklist, C13, C20 | 9 Medium | AI System Owner | Pre-launch |
| 4 | R07 Unannounced vendor model change | 16 Critical | Mitigate | C12 contract clauses, C13 regression suite, C14 | 6 Medium | Vendor Mgmt | Pre-launch |
| 5 | R20 Shadow AI use by staff | 16 Critical | Mitigate | C23 approved tool + DLP + training, C16 | 9 Medium | CISO | Launch + 60 days |
| 6 | R08 Vendor retains / trains on bank data | 15 Critical | Mitigate | C12, C14 | 4 Low | Vendor Mgmt | Pre-launch |
| 7 | R09 Password-reset abuse (excessive agency) | 15 Critical | Mitigate | C06, C07 step-up auth, C16 | 8 Medium | CISO | Pre-launch |
| 8–14 | R02, R04, R06, R13, R14, R15, R16 | 10–12 High | Mitigate | See register | 4–6 | Various | Pre-launch / Launch + 30 |
| 15–20 | R10, R11, R12, R17, R18, R19 | 8–9 Medium | Mitigate | See register | 2–4 | Various | Pre-launch |

## 2. Go-live conditions (must-fix before full launch)

The AI Risk Committee recommends **conditional approval**. Full launch can happen only when these six items are complete and verified by GRC:

| # | Must-fix item | Addresses | Evidence required |
|---|---|---|---|
| 1 | PII/PCI masking live in chat and logs; pilot logs scrubbed | R03 | DLP test report (100% masked) |
| 2 | Input/output guardrails and red-team test passed | R01, R02, R11 | Red-team report: ≤ 2% success, 0 data access |
| 3 | Grounded answers + commitment blocklist | R05 | Accuracy test ≥ 95%; 0 unauthorized commitments |
| 4 | Vendor contract amendment signed (no training, zero retention, version pinning, change notice) | R07, R08 | Signed amendment; vendor attestation |
| 5 | Step-up authentication for password reset | R09 | Security test results |
| 6 | AI disclosure banner and "talk to a person" button | R10, R15 | Screenshot; compliance sign-off |

## 3. Residual risk acceptance (MANAGE 1.4)

After treatment, **no residual risk is High or Critical**, so no CRO risk acceptance is needed. The 10 Medium residual risks are accepted by the **AI System Owner** within the bank's risk appetite and reviewed quarterly.

| Field | Value |
|---|---|
| Residual risks accepted | 10 Medium, 10 Low |
| Accepted by | VP Digital Banking (AI System Owner) |
| Conditions | KRIs stay green/amber; quarterly AI Risk Committee review |
| Re-assessment trigger | Any Red KRI, any Severity 1–2 AI incident, vendor model change, new integration, or new regulation |

## 4. Third-party risk (MANAGE 3.1, 3.2)

| Action | Detail |
|---|---|
| Due diligence | AI vendor questionnaire, SOC 2 Type II review, model card and safety documentation review |
| Contract clauses | Data use limits, zero retention, model version pinning, 30-day notice of model changes, 24-hour breach notice, audit rights, exit plan |
| Ongoing monitoring | Annual reassessment; regression suite on any model change; track vendor incidents |

## 5. Post-deployment monitoring (MANAGE 4.1–4.3)

- KRIs from the [Metrics & Testing Plan](../03-measure/metrics-and-testing-plan.md) reported monthly to the AI System Owner and quarterly to the AI Risk Committee
- Feedback channels: post-chat survey, complaints, front-line staff reports
- **Kill switch:** the AI System Owner or CISO can disable AskMeridian and fall back to static FAQ + live chat at any time
- **Decommission criteria** (MANAGE 2.4): two consecutive quarters with Red KRIs that cannot be fixed, or a Severity 1 incident with no effective fix within 30 days
