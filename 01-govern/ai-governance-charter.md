# AI Risk Committee — Governance Charter

| Field | Value |
|---|---|
| Document ID | GOV-AI-001 |
| Version | 1.0 |
| Owner | Chief Risk Officer |
| NIST AI RMF alignment | GOVERN 1.3, 2.1, 2.2, 2.3, 3.1, 3.2, 5.1 |

## 1. Purpose

The AI Risk Committee (AIRC) provides oversight of all AI systems at Meridian Trust Bank to make sure AI risks are identified, measured, managed, and reported within the bank's risk appetite.

## 2. Authority

The AIRC is a management committee reporting to the **Enterprise Risk Committee**, which reports to the **Board Risk Committee**. The AIRC can:
- Approve, conditionally approve, or reject high-impact AI systems for production
- Require a pause or shutdown of any AI system that exceeds risk tolerance
- Approve AI policies and standards
- Recommend risk acceptance to the CRO

## 3. Membership

| Role | Member | Voting |
|---|---|---|
| Chair | Chief Risk Officer (CRO) | Yes |
| Member | Chief Information Security Officer (CISO) | Yes |
| Member | Chief Data / Privacy Officer | Yes |
| Member | Chief Compliance Officer | Yes |
| Member | Chief Technology Officer | Yes |
| Member | General Counsel (or delegate) | Yes |
| Member | Head of Model Risk Management | Yes |
| Advisory | AI System Owners (when their system is discussed) | No |
| Secretary | GRC Analyst — AI Risk | No |

**Diversity of perspective:** the committee includes risk, security, privacy, legal, technology, and business viewpoints, as recommended by GOVERN 3.1.

## 4. Meetings and quorum

- Meets **monthly**, and ad hoc for urgent AI incidents
- Quorum: a majority of voting members, including the CRO or delegate
- Minutes are kept by the Secretary and retained for 7 years

## 5. Responsibilities

1. Maintain the AI Acceptable Use and Risk Management Policy
2. Review the AI System Inventory quarterly
3. Review AI Impact Assessments and Risk Registers for high-impact systems
4. Set AI risk tolerance thresholds and key risk indicators (KRIs)
5. Oversee AI incident trends and lessons learned
6. Track regulatory changes (e.g., EU AI Act, U.S. federal and state AI laws, banking regulator guidance)
7. Make sure staff receive AI risk training
8. Report to the Enterprise Risk Committee quarterly

## 6. AI system approval workflow

```
Business idea
   │
   ▼
Register in AI System Inventory ──► Risk tier assigned (Low / Medium / High-impact)
   │
   ▼
AI Impact Assessment (System Owner + GRC)
   │
   ├── Low/Medium ─► Approved by GRC + CISO delegate
   │
   └── High-impact ─► Security, privacy, fairness testing
                          │
                          ▼
                     AI Risk Committee review
                          │
           ┌──────────────┼───────────────┐
           ▼              ▼               ▼
       Approved   Conditionally approved   Rejected
                  (must-fix items + date)
                          │
                          ▼
              Ongoing monitoring (quarterly)
```

## 7. Reporting

| Report | Audience | Frequency |
|---|---|---|
| AI risk dashboard (KRIs, top risks, incidents) | Enterprise Risk Committee | Quarterly |
| AI program summary | Board Risk Committee | Semi-annually |
| AI incident notification | CRO, CISO, General Counsel | Within 24 hours of a Severity 1 or 2 incident |

## 8. Charter review

Reviewed annually and approved by the Enterprise Risk Committee.
