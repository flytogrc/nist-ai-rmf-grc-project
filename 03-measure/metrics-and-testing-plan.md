# Metrics and Testing Plan — AskMeridian

NIST AI RMF alignment: MEASURE 1.1, 1.3, 2.1–2.11, 3.1–3.3, 4.1–4.3 · NIST AI 600-1 (GenAI Profile)

## 1. Risk scoring method

- 5×5 **Likelihood × Impact** matrix (definitions in the `Scoring` tab of [ai-risk-register.xlsx](ai-risk-register.xlsx))
- Ratings: **Critical** ≥ 15 · **High** 10–14 · **Medium** 5–9 · **Low** 1–4
- **Inherent** risk = before controls · **Residual** risk = after controls are in place and tested

### Results

| Rating | Inherent | Residual |
|---|---|---|
| Critical | 7 | 0 |
| High | 7 | 0 |
| Medium | 6 | 10 |
| Low | 0 | 10 |
| **Average score** | **13.1** | **5.4** (≈ 59% reduction) |

Residual results assume the controls in the [Risk Treatment Plan](../04-manage/risk-treatment-plan.md) are implemented and pass testing.

## 2. Pre-launch testing

| Test | What it checks | Method | Pass criteria | Owner | Risks |
|---|---|---|---|---|---|
| **Red-team / adversarial testing** | Prompt injection, jailbreaks, system-prompt leakage, data extraction, excessive agency | 300+ attack prompts based on OWASP LLM Top 10 and NIST AI 600-1; manual + automated | ≤ 2% attack success rate; **0** successful cross-customer data access | CISO | R01, R02, R04, R09, R11 |
| **Accuracy / groundedness** | Correct, sourced answers | Golden set of 500 real customer questions with approved answers; human-graded | ≥ 95% correct; ≥ 98% of answers cite an approved source; 0 unauthorized commitments | AI System Owner | R05, R14, R17 |
| **Fairness testing** | Equal quality across groups | Same 200 questions rewritten in plain/complex English, Spanish, and common dialects | Accuracy gap between groups ≤ 3 percentage points; refusal-rate gap ≤ 3 pp | Model Risk Mgmt | R06 |
| **Privacy / DLP testing** | Sensitive data masked | Seed 100 synthetic SSNs/card numbers into chats; inspect logs and vendor payloads | 100% masked in logs; 0 sent unmasked to vendor | Privacy Officer | R03, R08 |
| **Accessibility testing** | Usable with assistive tech | WCAG 2.2 AA audit with screen readers and keyboard-only use | No critical or serious issues open | AI System Owner | R19 |
| **Load and abuse testing** | Rate limits and cost controls | Simulated burst traffic | Rate limits trigger; spend cap holds; no outage | CTO | R12, R18 |
| **Failover testing** | Fallback when vendor is down | Block vendor API in staging | Fallback to FAQ and live chat within 60 seconds | CTO | R18 |

## 3. Ongoing metrics — Key Risk Indicators (KRIs)

| KRI | Target (green) | Amber | Red (escalate to AI Risk Committee) | Frequency | Source |
|---|---|---|---|---|---|
| Prompt-injection attempts blocked | Trend tracked | +50% month over month | Any **successful** injection | Daily | SIEM |
| Answers with no approved source | < 2% | 2–5% | > 5% | Weekly | Trace logs |
| Hallucination rate (weekly 100-conversation sample) | < 3% | 3–5% | > 5% | Weekly | QA review |
| Unauthorized commitments (fee waivers, rates) | 0 | — | ≥ 1 | Daily | Output filter logs |
| Unmasked PII/PCI found in logs | 0 | — | ≥ 1 | Daily | DLP scans |
| Accuracy gap between language groups | ≤ 3 pp | 3–5 pp | > 5 pp | Quarterly | Fairness test |
| Escalation-to-human rate | 15–25% | < 10% or > 35% | — | Weekly | Chat platform |
| Customer complaints mentioning the bot | < 0.1% of chats | 0.1–0.3% | > 0.3% | Monthly | Complaints system |
| Customer satisfaction (CSAT) | ≥ 4.2 / 5 | 3.8–4.2 | < 3.8 | Monthly | Post-chat survey |
| Regression suite pass rate after any model change | 100% critical, ≥ 95% overall | — | Any critical failure | Each change | CI pipeline |
| Monthly API spend vs. budget | ≤ 100% | 100–120% | > 120% | Daily | Cloud billing |
| Open overdue risk treatments | 0 | 1–2 | ≥ 3 | Monthly | Risk register |

## 4. Measurement limitations (MEASURE 1.3, 4.2)

- Hallucination and fairness rates come from **samples**, not every conversation, so they are estimates.
- Red-team testing can show weaknesses exist; it cannot prove they don't.
- Metrics are only meaningful if reviewers are independent of the development team — QA sampling is done by Model Risk Management, not the product team.
- Feedback from customers and front-line staff is collected monthly to catch issues metrics miss (MEASURE 3.3).
