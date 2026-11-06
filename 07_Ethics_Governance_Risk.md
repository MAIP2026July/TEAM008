# DealFit - Ethics, Governance and Risk

## 1. Purpose

DealFit influences commercially and reputationally important creator decisions. A recommendation may affect whether a creator accepts, negotiates, declines, or delays a sponsorship opportunity.

The governance objective is therefore not to eliminate all product risk. It is to ensure that DealFit remains a **decision-support system with visible evidence boundaries, explicit uncertainty, human accountability, and the ability to stop or challenge unsafe behavior**.

> **Governance principle: AI recommends. The creator decides.**

---

## 2. Responsible AI Position

DealFit should be governed around seven principles:

1. **Human authority** - creators retain final decision rights.
2. **Transparency** - facts, rules, AI inferences, missing information, and unverified claims are distinguishable.
3. **Uncertainty awareness** - incomplete or contradictory evidence causes escalation rather than false confidence.
4. **Privacy and minimization** - collect only information required for screening.
5. **Fairness** - do not equate brand size, popularity, or familiarity with suitability.
6. **Accountability** - product/model owners must monitor failures and own corrective actions.
7. **Reversibility** - recommendations can be challenged, overridden, corrected, or disabled without irreversible external execution.

---

## 3. Key Risk Categories

DealFit's main risk areas are:

- hallucinated or unsupported external information;
- creator over-reliance on the DealFit score;
- incorrect Accept / Negotiate / Decline recommendations;
- false-positive risk flags;
- missed commercial or contractual risks;
- brand-size or familiarity bias;
- creator-profile bias or stale preferences;
- privacy of commercially sensitive creator data;
- security and unauthorized access;
- unsafe contract-language interpretation;
- model / prompt drift if an external LLM is introduced;
- misuse of override history;
- automation creep beyond the approved human-in-the-loop scope.

---

## 4. Hallucination and Grounding Risk

### Risk

A generative model may invent or overstate information about:

- brand reputation;
- market rates;
- controversies;
- legal terms;
- contract enforceability;
- expected campaign performance.

### Current MVP Control

The classroom MVP performs no live external research and explicitly displays:

- `Brand reputation not verified`
- `Market-rate comparison unavailable`
- `Contract enforceability not assessed`

### Pilot Control

If external retrieval is introduced:

- identify each connected source;
- distinguish retrieval results from AI inference;
- prohibit unsupported external factual claims from appearing as verified;
- log retrieval/source failures;
- fall back to `External Verification Required` when grounding is unavailable.

### Launch Blocker

Any repeated behavior that presents unsupported reputation, legal, or market information as verified fact.

---

## 5. Over-Reliance and Automation Bias

### Risk

Creators may treat:

- a high score;
- High confidence;
- or an Accept recommendation

as a directive rather than decision support.

### Controls

- Label all results `Creator Review Required`.
- Explain that the 0-100 score is **not** a probability of campaign success.
- Show confidence beside the recommendation.
- Show risk and missing-information blocks before final decision.
- Provide five separate human actions.
- Allow override with optional reason.
- Do not execute external actions automatically.

### Monitoring Signal

Track whether users repeatedly accept recommendations without reviewing risk or missing-information sections during real-user testing.

### Launch Blocker

Any workflow change that removes final human approval for accepting, declining, negotiating, messaging, contracting, or payment.

---

## 6. False Positive and False Negative Risk

### False Positive Example

DealFit may flag a partnership as risky even when creator-specific context makes it acceptable.

Potential consequence:

- missed commercial opportunity;
- unnecessary manual review;
- reduced trust in the product.

S06 V1 demonstrated this type of risk when partnership-conflict logic was too broad.

### False Negative Example

DealFit may miss a meaningful commercial, values, audience, or contractual concern.

Potential consequence:

- creator accepts weak terms;
- audience trust is affected;
- creator enters an avoidable category conflict;
- creator gives excessive usage rights.

### Controls

- deterministic hard rules;
- Manual Review / Need More Information state;
- risk flags;
- creator override;
- scenario testing;
- failure analysis;
- conservative escalation for incomplete/contradictory information.

---

## 7. Bias and Fairness

### 7.1 Brand Familiarity Bias

A model may assume large or recognizable brands are safer or better-fit.

**Control:** Brand popularity must not be used as a proxy for partnership quality unless an explicit, valid data source and product rationale exist.

### 7.2 Small-Brand Disadvantage

Smaller brands may have less public information and therefore appear more uncertain.

**Control:** Missing public information should be labelled as uncertainty rather than negative reputation.

### 7.3 Creator-Niche Bias

Hard-coded domain taxonomies may perform better for some creator niches than others.

**Evidence:** The classroom MVP retains simplified audience/domain logic as a known limitation.

**Control before pilot:** Test multiple creator niches and allow creator-configurable priorities.

### 7.4 Feedback Bias

Creator overrides should not automatically become training labels. A creator may override because of exceptional private context rather than because the recommendation was objectively wrong.

**Control:** Review override reasons before using them for personalization or learning.

---

## 8. Privacy and Data Protection

DealFit may process sensitive commercial information such as:

- compensation preferences;
- deal offers;
- partnership history;
- audience information;
- category exclusions;
- creator notes;
- private brand communication.

### MVP Position

The classroom prototype stores only session-level browser data and does not send data to a live external model.

### Production Principles

Before a real pilot:

- define a clear privacy notice;
- obtain user consent for processing;
- collect only necessary data;
- encrypt data in transit and at rest;
- implement authentication and authorization;
- define retention periods;
- allow deletion/export where appropriate;
- minimize sensitive information sent to third-party model providers;
- review vendor data-retention/model-training terms;
- separate production data from test/synthetic data.

### Launch Blocker

Real creator data must not be used in a hosted pilot until storage, access, retention, deletion, and third-party processing are defined.

---

## 9. Security Risk

### Threats

- unauthorized access to creator deal history;
- leaked compensation preferences;
- exposed brand communications;
- manipulated inputs or prompt injection if an LLM is connected;
- insecure API keys;
- unauthorized team-member access in future multi-user products.

### Controls Before Pilot

- secure authentication;
- role/permission checks;
- secrets management;
- server-side API key protection;
- input validation;
- logging and monitoring;
- rate limiting where appropriate;
- dependency/security updates;
- backup and recovery plan;
- incident-response contacts.

---

## 10. Contract and Legal Interpretation Risk

DealFit may surface issues such as usage rights or exclusivity, but should not claim to provide legal advice.

### Allowed Product Behavior

- identify that usage rights appear broad;
- identify missing exclusivity duration;
- recommend clarification;
- recommend professional review where appropriate.

### Disallowed / High-Risk Behavior

- declare that a contract is legally enforceable or unenforceable;
- provide definitive legal conclusions;
- guarantee contract safety;
- replace qualified legal review for material terms.

### UX Control

Maintain the disclaimer:

> DealFit provides AI-assisted screening and does not provide legal, financial, contractual, or reputation-verification services.

---

## 11. Confidence and Explainability Governance

### Confidence

Confidence means evidence completeness/clarity in the prototype. It is not calibrated probability.

### Required Explanation Elements

A recommendation should expose, where applicable:

- provided facts;
- AI inferences;
- deterministic rule triggers;
- risk flags;
- missing information;
- external verification required;
- recommended next action.

### Governance Rule

A recommendation must not be presented without an explanation state except during a system error.

---

## 12. Model / Prompt Drift

The classroom MVP has no external model, but a future API-based product would require drift monitoring.

### Drift Sources

- model-provider version changes;
- prompt changes;
- creator behavior changes;
- sponsorship contract patterns changing;
- new creator niches;
- new partnership formats;
- retrieval-source changes.

### Controls

- version prompts and product rules;
- maintain a fixed regression test pack;
- rerun safety scenarios after model/prompt changes;
- log recommendation changes;
- compare override/risk patterns over time;
- require approval before major model/prompt changes reach production.

---

## 13. Human Review and Override Policy

Human review is mandatory for final action.

### Creator Should Trust the Product More When

- necessary deal information is present;
- recommendation rationale matches provided facts;
- deterministic rules are correctly triggered;
- no contradictory information exists.

### Creator Should Question the Product When

- confidence is Medium or Low;
- important context is missing;
- a recommendation conflicts with known relationship context;
- external reputation/market/legal information matters;
- the score conflicts with the detailed risk explanation.

### Creator Should Seek Additional Evidence When

- payment terms are missing;
- usage rights are broad or unclear;
- exclusivity is ambiguous;
- brand reputation matters materially;
- contract-language interpretation matters;
- market-rate comparison is required.

### Creator Should Override When

- creator-specific context unavailable to DealFit changes the decision;
- an input/extracted fact is wrong;
- the creator applies a stricter personal boundary;
- a relationship, audience, or commercial factor is missing from the system.

Overrides must remain auditable but should not automatically be interpreted as model error.

---

## 14. Accountability Model

### Product Owner

Accountable for:

- product scope;
- recommendation policy;
- user communication;
- prioritization of corrective changes.

### AI / Evaluation Owner

Accountable for:

- scenario/regression pack;
- prompt/model evaluation if introduced;
- failure analysis;
- monitoring recommendation behavior.

### Engineering Owner

Accountable for:

- implementation quality;
- access controls;
- logging;
- reliability;
- secure integrations.

### Privacy / Security Owner

Accountable for:

- data handling;
- retention;
- vendor review;
- security controls;
- incident coordination.

### Creator / Manager

Accountable for:

- final sponsorship decision;
- correcting inaccurate supplied information;
- seeking specialist advice when required.

No single AI output is the accountable decision-maker.

---

## 15. Monitoring Framework

### Prototype

Monitor per test cycle / release.

### Alpha / Beta

Review at least weekly during a small controlled test:

- recommendation distribution;
- override reasons;
- hard-rule failures;
- missing-information misses;
- unsupported-claim incidents;
- application errors;
- privacy/security incidents.

### Paid Pilot

Suggested operating cadence:

**Continuous / per event**

- system errors;
- security incidents;
- automatic-action violations;
- external grounding failures.

**Weekly**

- override patterns;
- risk-flag patterns;
- support issues;
- harmful recommendation reports.

**Monthly**

- usage;
- retention;
- recommendation distribution;
- cost per screening;
- creator feedback;
- prompt/model performance if applicable.

**After any material model/prompt/rule change**

- rerun regression/safety pack before release.

---

## 16. Retraining / Reconfiguration Triggers

The MVP has no trained proprietary model, so the near-term action is **reconfiguration or prompt/rule revision**, not retraining.

Trigger review when:

- hard-rule failures occur;
- unsupported claims appear;
- override patterns reveal repeated systematic error;
- a creator segment performs materially worse;
- a model/provider version changes;
- new deal formats are not understood;
- risk-severity or confidence logic is repeatedly challenged;
- audience/niche scoring fails across real creator tests.

A future trained model should have separate retraining criteria only after sufficient validated data exists.

---

## 17. Incident Response

### Severity 1 - Critical

Examples:

- automated external action without approval;
- sensitive data exposure;
- repeated fabricated legal/reputation claims presented as verified.

**Action:** Disable affected feature / pause pilot immediately, preserve evidence, investigate, notify responsible owners.

### Severity 2 - High

Examples:

- creator exclusion not enforced;
- systematic unsafe recommendation pattern;
- high-impact false conflict or missing-risk pattern.

**Action:** Disable affected recommendation path if necessary and issue rapid corrective release after regression testing.

### Severity 3 - Moderate

Examples:

- misleading explanation;
- isolated scoring inconsistency;
- non-critical UX bug.

**Action:** Log, prioritize, correct through normal release process.

---

## 18. Launch-Blocking Risks

DealFit should not proceed to a real paid pilot while any of the following remain unresolved:

- creator exclusions are not reliably enforced;
- unsupported external claims are presented as verified;
- final decisions can execute automatically;
- privacy/security controls for real creator data are undefined;
- usage-rights/contract outputs are presented as legal advice;
- users cannot distinguish facts from AI inference;
- repeated systematic recommendation failures remain unexplained;
- the connected LLM/API, if any, has unacceptable data-handling terms;
- incident ownership is undefined.

---

## 19. Governable vs Non-Governable Scope

### Governable for Near-Term Pilot

- pitch structuring;
- creator rules;
- missing-information prompts;
- category constraints;
- first-pass fit assessment;
- risk flags;
- recommendation explanation;
- human override.

### Avoid Automating in Early Stages

- final deal acceptance/rejection;
- contract execution;
- legal conclusions;
- autonomous negotiation;
- payment decisions;
- public brand accusations;
- financially consequential external actions.

---

## 20. Current Responsible AI Decision

### Classroom MVP

**PASS FOR DEMONSTRATION**

The prototype demonstrates that deterministic guardrails, transparent confidence, evidence labels, Manual Review, and human override can be integrated into the product workflow.

### Real Paid Pilot

**NOT YET READY WITHOUT ADDITIONAL CONTROLS**

Before a paid pilot, DealFit needs real-user validation, secure storage/access, privacy controls, richer creator-fit evaluation, and governance for any external LLM/API.

---

## 21. Traceability

This governance artifact should be read with:

- `02_Product_Strategy.md`
- `Appendix/PRD/PRD.md`
- `04_UX_Workflow_Trust.md`
- `05_Data_Model_Evaluation.md`
- `Appendix/Metrics/Metrics_and_Launch_Gates.md`
- `09_Prototype_MVP.md`
- `Appendix/AI_Self_Evaluation/AI_Product_Self_Evaluation.md`
- `06_Business_Economics_Scaling.md`

The detailed risk register is maintained in:

`Appendix/Risk_Note/Risk_Note.md`

