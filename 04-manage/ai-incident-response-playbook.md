# AI Incident Response Playbook — AskMeridian

| Field | Value |
|---|---|
| Document ID | PB-AI-001 |
| Owner | CISO |
| NIST AI RMF alignment | MANAGE 2.3, 2.4, 4.1, 4.3; GOVERN 4.3 |
| Related | Enterprise Incident Response Plan (NIST SP 800-61 based) |

This playbook adds AI-specific steps to the bank's existing incident response plan.

## 1. What counts as an AI incident

| Type | Examples |
|---|---|
| Security | Successful prompt injection, system-prompt leak, jailbreak, abuse of bot tools |
| Privacy | PII/PCI exposed in output or logs; one customer sees another's data; vendor data misuse |
| Harmful / inaccurate output | False promises (fee waivers), wrong rates, offensive content, unsafe advice |
| Fairness | Evidence a group of customers gets worse service |
| Availability / cost | Vendor outage, runaway API spend |
| Third-party | Vendor model change breaks behavior; vendor breach |

## 2. Severity levels

| Severity | Definition | Examples | Response time |
|---|---|---|---|
| **SEV 1 – Critical** | Customer data exposed, active exploitation, or widespread customer harm | Cross-customer data leak; mass prompt-injection exploit | Engage within **15 min**; consider kill switch immediately |
| **SEV 2 – High** | Limited data exposure or harmful output reaching customers | Card number shown in output; viral offensive answer | Within **1 hour** |
| **SEV 3 – Medium** | Contained issue; no confirmed customer harm | Guardrail bypass found by red team; KRI turns Red | Within **1 business day** |
| **SEV 4 – Low** | Minor quality issue | Small number of outdated answers | Normal ticket |

## 3. Response phases

### Phase 1 — Detect and report
- Sources: SIEM alerts (C16), DLP alerts, KRI breaches, customer complaints, staff reports, vendor notices, social media
- Anyone can report to the Security Operations Center (SOC) hotline or `#ai-incidents` channel
- SOC opens a ticket tagged **AI-Incident** and assigns severity

### Phase 2 — Triage and contain
- [ ] Confirm the issue using conversation traces (prompt, retrieved documents, model version, output — control C19)
- [ ] **SEV 1/2:** decide on the **kill switch** (disable bot → fallback to FAQ + live chat). Authority: CISO or AI System Owner
- [ ] Block attacker accounts / IPs; tighten input filters
- [ ] Remove or quarantine any bad knowledge-base document
- [ ] Roll back to the last known-good prompt or model version
- [ ] Preserve evidence (logs, traces, screenshots) — do not delete

### Phase 3 — Notify

| Who | When | Owner |
|---|---|---|
| CISO, CRO, AI System Owner | SEV 1–2: within 1 hour | SOC lead |
| General Counsel, Privacy Officer, Compliance | Any data exposure or consumer harm | CISO |
| AI Risk Committee | SEV 1–2: within 24 hours | GRC Analyst |
| Vendor A | If vendor model or platform involved | Vendor Mgmt |
| Regulators | As required by law (e.g., banking regulator notification rules, state breach laws, GDPR 72-hour rule) | General Counsel |
| Affected customers | As required by law, or if harm occurred | Compliance + Communications |

### Phase 4 — Eradicate and recover
- [ ] Fix the root cause (prompt, filter, integration code, document, vendor setting)
- [ ] Add the attack/failure case to the **regression test suite** (C13) and red-team library (C10)
- [ ] Re-run regression and red-team tests; must pass before re-enabling
- [ ] Re-enable with extra monitoring for 7 days
- [ ] Make customers whole (refund fees, correct information) where harmed

### Phase 5 — Lessons learned (within 10 business days)
- [ ] Blameless post-incident review
- [ ] Update the **risk register** — re-score likelihood/impact
- [ ] Update controls, KRIs, and this playbook
- [ ] Report summary to the AI Risk Committee

## 4. AI-specific scenarios

| Scenario | First actions |
|---|---|
| Bot leaks its system prompt | Rotate any secrets in prompt (there should be none); harden prompt; add case to tests; SEV 3 unless it enabled further attacks |
| Bot shows another customer's data | **SEV 1.** Kill switch; disable account-lookup tool; legal + privacy; identify affected customers |
| Bot promised a fee waiver | SEV 3 (SEV 2 if many). Honor or remediate per Compliance; add phrase to commitment blocklist |
| Unmasked card numbers found in logs | SEV 2. Purge and verify; check DLP rule; assess PCI DSS impact |
| Vendor changed the model and accuracy dropped | Pin previous version; run regression suite; escalate under contract |
| Attacker running up API costs | Hard spend cap; block sources; tighten rate limits |

## 5. Tabletop exercise

Run a tabletop exercise **twice a year** using one of the scenarios above. Track: time to detect, time to contain, and whether notification deadlines were met.
