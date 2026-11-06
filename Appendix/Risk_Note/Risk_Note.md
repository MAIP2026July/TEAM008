# DealFit - Detailed Risk Register

## 1. Purpose

This register operationalizes the risks described in `07_Ethics_Governance_Risk.md`.

Ratings are qualitative planning categories for the proposed product and are not empirically estimated probabilities.

### Rating Scale

**Likelihood:** Low / Medium / High  
**Impact:** Low / Medium / High / Critical  
**Treatment:** Accept / Monitor / Mitigate / Block

---

## 2. Risk Register

| ID | Risk | Likelihood | Impact | Primary Control | Owner | Pilot Treatment |
|---|---|---|---|---|---|---|
| R-01 | Unsupported brand reputation claim presented as fact | Medium if live LLM added | High | Grounding boundary + verification labels | AI/Evaluation Owner | BLOCK if unresolved |
| R-02 | Market-rate hallucination influences negotiation | Medium | High | Do not claim live market benchmark without source | Product Owner | BLOCK if presented as verified |
| R-03 | Creator over-relies on DealFit score | Medium | High | Score disclaimer + review required + explanation | Product Owner | MITIGATE |
| R-04 | Creator exclusion fails | Low after V2 targeted test | High | Deterministic rule + regression test | Engineering / Product | BLOCK |
| R-05 | Missing critical information still produces positive recommendation | Low after V2 targeted test | High | Critical-field precedence + Low-confidence escalation | Product / AI | BLOCK |
| R-06 | Niche/audience fit is mis-scored | Medium | Medium/High | Multi-niche testing + configurable priorities | AI/Evaluation | MITIGATE before pilot |
| R-07 | Existing partnership conflict falsely triggered | Medium | Medium | Require explicit evidence, allow correction | Product / AI | MITIGATE |
| R-08 | Genuine conflict is missed | Medium | High | Structured conflict fields + manual review | Product / AI | MITIGATE |
| R-09 | Values mismatch not surfaced | Medium | High | Creator values config + risk propagation | Product / AI | MITIGATE |
| R-10 | Broad usage rights are overlooked | Medium | High | Explicit usage-right field + risk rule | Product | MITIGATE |
| R-11 | Contract-language output is mistaken for legal advice | Medium | High | Disclaimer + clarification/review framing | Product / Legal | BLOCK if legal conclusions shown |
| R-12 | Sensitive deal data exposed | Low/Medium in hosted pilot | Critical | Encryption, access control, retention policy | Security/Privacy | BLOCK |
| R-13 | Third-party LLM retains creator data | Unknown until provider selected | Critical | Vendor privacy review + minimization | Privacy / AI | BLOCK |
| R-14 | Prompt injection manipulates a future LLM | Medium if LLM added | High | Input isolation, system controls, output schema, monitoring | Engineering / AI | MITIGATE |
| R-15 | Model/provider update changes behavior | Medium | High | Version control + regression suite | AI/Evaluation | MITIGATE |
| R-16 | Small/unknown brands are unfairly penalized | Medium | Medium | Treat missing info as uncertainty, not negative reputation | Product / AI | MONITOR/MITIGATE |
| R-17 | Famous brands receive unjustified positive bias | Medium | Medium | Do not score brand popularity as fit | Product / AI | MONITOR/MITIGATE |
| R-18 | Override data becomes biased training labels | Medium | Medium | Human review before personalization | AI/Evaluation | MITIGATE |
| R-19 | Automated external action is added without adequate control | Low in current MVP | Critical | Human approval gate, architectural prohibition | Product / Engineering | BLOCK |
| R-20 | Decision history used beyond creator expectations | Medium | High | Purpose limitation, consent, retention controls | Privacy/Product | MITIGATE |
| R-21 | Creator's profile becomes stale | High over time | Medium | Edit reminders + profile last-reviewed date | Product | MONITOR |
| R-22 | Recommendation inconsistency reduces trust | Medium if live LLM added | Medium/High | Repeated-scenario testing + prompt/version logging | AI/Evaluation | MITIGATE |
| R-23 | Live retrieval source is unavailable/outdated | Medium if retrieval added | Medium | Source status + fallback to verification required | Engineering / AI | MITIGATE |
| R-24 | Product expands into unsupported CRM/legal/negotiation scope | Medium | Medium/High | Product non-goals + roadmap gates | Product Owner | MITIGATE |
| R-25 | Creators will not pay despite liking the product | Medium/High | High commercial impact | Small real paid pilot | Product/Commercial | VALIDATE |

---

## 3. Launch Blockers

The following risks must be resolved before processing real creator data in a paid pilot:

- R-01 unsupported external factual claims;
- R-04 failure of hard creator exclusions;
- R-05 unsafe handling of critical missing information;
- R-11 legal-advice boundary failure;
- R-12 inadequate security/privacy controls;
- R-13 unacceptable external-model data handling;
- R-19 automated external action without human approval.

---

## 4. Pilot Monitoring Watchlist

Monitor closely during Alpha/Beta/Paid Pilot:

- R-06 niche/audience scoring;
- R-07/R-08 partnership conflicts;
- R-09 values alignment;
- R-10 usage-rights detection;
- R-16/R-17 brand-size/familiarity bias;
- R-18 override-learning bias;
- R-21 stale creator profiles;
- R-22 recommendation consistency;
- R-25 willingness to pay.

---

## 5. Evidence from Classroom Testing

### V1

Structured synthetic testing exposed:

- critical missing-field precedence issue;
- false existing-partnership conflict;
- poor-fit campaign misclassification;
- values risk not propagating to the recommendation;
- confidence ambiguity;
- simplified audience scoring.

### V2

Targeted regression showed corrected behavior for:

- S03 creator exclusion;
- S04 critical missing compensation;
- S06 unclear exclusivity without false existing conflict;
- S07 weak niche fit;
- S09 explicit partnership conflict;
- S11 values ambiguity.

S01 confirmed the Accept path remained functional.

The simplified audience-relevance heuristic remains a known non-blocking classroom limitation.

---

## 6. Risk Review Cadence

### Classroom / Prototype

Review after each build or logic revision.

### Private Alpha / Beta

Review weekly and after any safety incident.

### Paid Pilot

- Critical incidents: immediate review
- High-risk trend indicators: weekly
- Full risk register: monthly
- Model/prompt/rule changes: before deployment

---

## 7. Risk Acceptance Rule

Risk may be accepted only when:

- the user impact is understood;
- a responsible owner is named;
- human override remains available where relevant;
- monitoring exists;
- the risk is not a listed launch blocker;
- the expected product value reasonably justifies the residual exposure.

---

## 8. Traceability

This register supports:

- `07_Ethics_Governance_Risk.md`
- `Appendix/Metrics/Metrics_and_Launch_Gates.md`
- `Appendix/AI_Self_Evaluation/AI_Product_Self_Evaluation.md`
- `09_Prototype_MVP.md`
- `Appendix/Roadmap/Roadmap.md`
