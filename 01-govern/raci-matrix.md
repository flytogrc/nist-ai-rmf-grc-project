# AI Risk Management — RACI Matrix

**R** = Responsible (does the work) · **A** = Accountable (owns the outcome, one per task) · **C** = Consulted · **I** = Informed

NIST AI RMF alignment: GOVERN 2.1 (roles and responsibilities are documented and clear).

| Activity | AI System Owner (VP Digital) | AI Product / Dev Team | GRC Analyst | CISO / Security | Privacy Officer | Compliance | Legal | Model Risk Mgmt | CRO / AI Risk Committee | Vendor Mgmt |
|---|---|---|---|---|---|---|---|---|---|---|
| Maintain AI policy | I | I | R | C | C | C | C | C | **A** | I |
| Register system in AI inventory | **A** | R | C | I | I | I | – | I | I | I |
| AI Impact Assessment | **A** | R | R | C | C | C | C | C | I | C |
| Risk identification & scoring | C | C | **A/R** | C | C | C | – | C | I | – |
| Security / red-team testing | I | C | I | **A/R** | – | – | – | I | I | – |
| Bias / fairness testing | I | R | C | – | C | C | C | **A** | I | – |
| Privacy review (data flows, retention) | C | C | C | C | **A/R** | C | C | – | I | – |
| Vendor due diligence & contract | C | I | C | C | C | – | C | – | I | **A/R** |
| Production approval | R | C | C | C | C | C | C | C | **A** | – |
| Implement controls | **A** | R | C | C | C | – | – | – | I | C |
| Ongoing monitoring & KRIs | **A** | R | R | C | I | I | – | C | I | – |
| AI incident response | C | R | C | **A/R** | C | C | C | I | I | C |
| Risk acceptance | R | – | C | C | C | C | C | C | **A** | – |
| Quarterly reporting to ERC | I | I | R | C | C | C | – | C | **A** | – |
| Staff AI training | I | I | R | C | C | **A** | – | – | I | – |
