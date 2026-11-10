# Company Scenario — Meridian Trust Bank (Fictional)

## 1. Organization

**Meridian Trust Bank** is a fictional regional bank in the United States.

- ~2,400 employees, ~600,000 retail and small-business customers
- Regulated by federal and state banking regulators; subject to GLBA (customer data privacy), consumer-protection laws (e.g., fair lending, UDAAP), and PCI DSS for card data
- Has a mature cybersecurity program (aligned to NIST CSF 2.0) but **no formal AI governance** yet
- Has ~50,000 customers in the EU (expats and business accounts), so the EU AI Act and GDPR are in scope for those users

## 2. The AI system — "AskMeridian"

| Attribute | Detail |
|---|---|
| Type | Generative AI chatbot (large language model) |
| Model | Third-party foundation model accessed through a cloud API (vendor: "Vendor A", fictional) |
| Architecture | Retrieval-augmented generation (RAG): the bot searches Meridian's product docs and FAQs, then writes an answer |
| Integrations | Read-only access to account balance and recent transactions (after login); can open a password-reset ticket; can hand off to a live agent |
| Users | Customers on the website and mobile app; ~40,000 conversations/month expected |
| Owner | VP of Digital Banking |
| Status | Pilot with 2,000 customers; full launch planned in 90 days |

### Data the system touches
- Customer names, account numbers (masked), balances, transactions — **Confidential / PII**
- Chat transcripts (may include anything a customer types, including SSNs or card numbers) — **Restricted**
- Product documentation and FAQs — **Internal**

## 3. Why leadership asked for this

During the pilot, three incidents were reported:

1. A customer got the bot to reveal part of its hidden system instructions ("prompt injection").
2. The bot told a customer an overdraft fee "would be waived," which was not true.
3. A customer pasted their full card number into the chat, and it was stored in plain text in chat logs.

The Chief Risk Officer (CRO) asked the GRC team to build an AI risk management program **before full launch**, using the NIST AI RMF.

## 4. Scope

**In scope:** AskMeridian (model, prompts, RAG pipeline, integrations, logs, vendor relationship, people and processes around it).

**Out of scope:** Credit decisioning models, fraud models, internal employee AI tools (to be covered in Phase 2).

## 5. My role

As the **GRC Analyst**, I was asked to:

1. Write the governance foundation (policy, charter, roles) — **GOVERN**
2. Document the system and its context, and identify risks — **MAP**
3. Score the risks and define how we will measure them — **MEASURE**
4. Recommend treatments and a response plan — **MANAGE**
5. Show how this aligns with other frameworks and regulations
6. Brief leadership with a go / no-go recommendation
