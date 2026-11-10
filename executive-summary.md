# Executive Summary — AskMeridian AI Risk Assessment

**To:** Chief Risk Officer, AI Risk Committee
**From:** GRC Analyst — AI Risk
**Date:** [Insert date]
**Subject:** Go-live risk recommendation for the AskMeridian AI chatbot

---

## Bottom line

**Recommendation: Conditional approval.** AskMeridian can launch to all customers once **6 must-fix items** are complete (estimated 6–8 weeks). With these controls, no risk remains above our risk appetite.

## What we assessed

AskMeridian is a generative AI chatbot that answers customer questions and can look up account information. It is expected to handle ~40,000 conversations a month and save ~$900k a year. We assessed it using the **NIST AI Risk Management Framework**, the NIST Generative AI Profile, and the OWASP Top 10 for LLM Applications.

## What we found

| | Before controls | After controls |
|---|---|---|
| Critical risks | **7** | 0 |
| High risks | **7** | 0 |
| Medium risks | 6 | 10 |
| Low risks | 0 | 10 |
| Average risk score (out of 25) | 13.1 | 5.4 |

**Top 5 risks**

1. **Customer card numbers and SSNs stored in chat logs** — already happened in the pilot.
2. **Customers can trick the bot** (prompt injection) into ignoring its rules — already happened in the pilot.
3. **The bot can state false information** such as fee waivers — already happened in the pilot.
4. **Our AI vendor can change the model without telling us**, changing how the bot behaves.
5. **Staff may paste customer data into public AI tools** when handling escalations.

## What we need to launch (must-fix items)

1. Mask sensitive data in chats and logs; scrub pilot logs
2. Pass security (red-team) testing with input/output guardrails
3. Restrict answers to approved sources and block unauthorized promises
4. Sign a vendor contract amendment: no training on our data, no data retention, advance notice of model changes
5. Require extra verification before password resets
6. Show a clear "you're chatting with AI" notice and a "talk to a person" button

## What happens after launch

- Monthly risk metrics (accuracy, data leaks, attacks, complaints) with clear red-flag thresholds
- Quarterly review by the AI Risk Committee
- A tested **kill switch** and AI incident response playbook
- Re-assessment after any vendor model change or serious incident

## Decision requested

Approve AskMeridian for full launch **conditional on** completion and GRC verification of the six must-fix items.

---
*Supporting documents: AI Policy, Governance Charter, AI Inventory, Impact Assessment, Risk Register, Metrics & Testing Plan, Risk Treatment Plan, Incident Response Playbook, Control Crosswalk.*
