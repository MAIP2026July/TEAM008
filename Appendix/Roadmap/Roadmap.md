# DealFit - MVP to First Revenue Roadmap

## 1. Purpose

This roadmap shows how DealFit can progress from the current classroom prototype to a controlled, evidence-based product pilot and then to its first paying users.

The roadmap deliberately avoids assuming product-market fit. Each stage has a clear learning objective, entry gate, product scope, evidence requirement, and stop/continue decision.

> **Roadmap principle: validate value before scaling cost or automation.**

---

## 2. Current Starting Point

DealFit currently has:

- a functional browser MVP;
- creator-profile configuration;
- structured pitch screening;
- deterministic guardrails;
- score, recommendation, confidence and explanation output;
- human override and decision history;
- 12 synthetic evaluation scenarios;
- documented V1 failures and V2 corrections;
- a final classroom status of **Pass for Demonstration**.

DealFit does **not yet have**:

- real creator validation;
- measured screening-time improvement;
- validated willingness to pay;
- production identity/security controls;
- a live LLM/API integration;
- live inbox or marketplace integrations;
- validated creator-market benchmarks.

---

## 3. Roadmap Overview

```text
Phase 0
Classroom Prototype
0-1 month
        |
        v
Phase 1
Private Alpha
1-2 months
        |
        v
Phase 2
Creator Beta
2-3 months
        |
        v
Phase 3
First Paid Pilot
3-5 months
        |
        v
Phase 4
Creator Pro
5-8 months
        |
        v
Phase 5
Small Creator Teams
8-12+ months
```

The first monetization objective occurs in **Phase 3**, not at prototype stage.

---

## 4. Phase 0 - Classroom Prototype

### Timeline

**Current state / 0-1 month**

### Objective

Demonstrate the complete DealFit workflow and identify product-logic weaknesses before involving real users.

### Product Scope

- Local browser application
- One design persona
- Manual pitch entry
- Deterministic rules
- Local AI-style assessment logic
- Four-way product recommendation
- Five human decision actions
- Human override
- Synthetic scenarios

### Evidence Completed

- 12/12 V1 scenarios executed
- 8/12 initial primary behaviors passed
- Six implementation/design findings documented
- V2 corrections implemented
- 7/7 targeted V2 regression checks passed
- Human override demonstrated

### Revenue Objective

**None.**

Charging at this stage would be premature because user value and willingness to pay have not been validated.

### Exit Gate

Proceed only if:

- prototype safety gates pass;
- Must Have workflow is demonstrable;
- known limitations are documented;
- no automatic external actions occur.

### Current Decision

**PASS FOR DEMONSTRATION.**

---

## 5. Phase 1 - Private Alpha

### Timeline

**Month 1-2**

### Target Participants

Approximately **3-5 consenting independent creators** across at least two creator niches.

This is a proposed validation sample, not a claim that participants have already been recruited.

### Objective

Validate whether the workflow solves a real repeated screening problem outside the Maya design persona.

### Product Changes

- Secure prototype hosting
- Basic authentication
- Clear consent flow
- Basic encrypted data storage
- Ability to delete creator/deal records
- Creator-configurable audience priorities
- Improved creator/campaign fit logic
- Structured audit log
- Bug/error logging

### Human Process

- Creator submits real or anonymized historical pitches.
- Creator independently records the preferred decision.
- DealFit recommendation is compared with the creator review.
- Overrides and missing context are discussed qualitatively.

### Evidence to Collect

- Screening frequency
- Screening time before/with DealFit
- Reasons creators accept, negotiate or decline
- Explanation usefulness
- Missing-information usefulness
- Override reasons
- Trust concerns
- Privacy concerns
- Repeat-use intent

### Revenue Objective

**No revenue required yet.**

The objective is problem/solution validation, not monetization.

### Exit Gate

Proceed to Beta only if:

- users repeatedly encounter the target workflow;
- DealFit reduces or structures manual effort in a way creators value;
- critical guardrails remain reliable;
- creators understand AI limitations;
- no major privacy or trust blocker appears.

---

## 6. Phase 2 - Creator Beta

### Timeline

**Month 2-3**

### Target Participants

Approximately **10-20 invited creators**.

### Objective

Test repeat usage, product usability and whether DealFit deserves a paid experiment.

### Product Scope

Add only features supported by Alpha evidence, potentially:

- improved profile onboarding;
- creator-configurable weighting/preferences;
- persistent deal history;
- better missing-information prompts;
- exportable deal summary;
- improved responsive/mobile experience;
- optional LLM-assisted extraction/reasoning under controlled privacy settings.

### Possible Technical Upgrade

If an LLM API is introduced, require:

- structured-output schema;
- provider privacy review;
- prompt/version logging;
- unsupported-claim monitoring;
- fallback behavior;
- cost-per-screening logging.

### Evidence to Collect

- Weekly active beta users
- Number of pitches screened per creator
- Repeat usage
- Median screening-time difference
- Recommendation agreement and override patterns
- Explanation usefulness
- Error/failure rate
- Retention across the short beta period
- Pricing interviews

### Revenue Objective

Still primarily validation, but introduce a **willingness-to-pay test**.

Example pricing research prompts may test ranges such as:

- INR 299/month
- INR 499/month
- INR 999/month

These are **pricing hypotheses only**, not validated prices.

### Exit Gate

Proceed to a paid pilot only if:

- creators demonstrate recurring usage;
- measurable workflow value exists;
- safety/trust issues are manageable;
- at least some participants express credible willingness to pay;
- estimated serving cost leaves room for positive contribution margin.

---

## 7. Phase 3 - First Paid Pilot

### Timeline

**Month 3-5**

### Objective

Generate DealFit's **first real revenue** while limiting commercial and operational exposure.

### Pilot Size

Proposed initial paid cohort:

**5-10 creators**

### Pricing Hypothesis

A simple pilot offer could test:

**Creator Pilot Plan: INR 499 per month**

Possible included allowance:

- up to 30 partnership screenings per month;
- persistent creator profile;
- decision history;
- risk and missing-information screening;
- human-controlled recommendations.

The INR 499 price is a **hypothesis for testing**, not validated willingness to pay.

### First-Revenue Milestones

| Milestone | Illustrative Revenue |
|---|---:|
| First paying creator | INR 499 MRR |
| 5 paying creators | INR 2,495 MRR |
| 10 paying creators | INR 4,990 MRR |

These figures are simple arithmetic based on the hypothetical INR 499 monthly pilot price. They are not revenue forecasts.

### Why Start Small

A small paid cohort allows the team to test:

- whether creators pay, not merely say they would pay;
- support burden;
- real usage frequency;
- AI/API serving cost;
- cancellation reasons;
- trust incidents;
- false positive/negative recommendation patterns.

### Paid-Pilot Success Evidence

- At least several creators pay and actively use the product
- Repeated pitch-screening behavior
- No launch-blocking safety incident
- Positive contribution margin per active user under observed usage
- Useful override and failure data
- Evidence that the tool is more valuable than a generic AI prompt/checklist

### Stop Conditions

Stop or redesign the paid pilot if:

- usage drops after initial curiosity;
- creators will not pay at a sustainable price;
- API/support costs approach or exceed revenue;
- trust or privacy concerns are material;
- recommendations create repeated harmful screening errors;
- value is not meaningfully better than a generic checklist/AI assistant.

---

## 8. Phase 4 - Creator Pro

### Timeline

**Month 5-8, only after paid-pilot evidence**

### Objective

Improve retention and increase value per creator without expanding into a full creator-management suite.

### Candidate Features

Only prioritize features supported by user evidence, potentially:

- inbox ingestion with human confirmation;
- reusable negotiation notes;
- configurable scoring priorities;
- better audience-fit semantics;
- creator-specific screening policies;
- searchable decision history;
- exportable deal summaries;
- limited negotiation-draft assistance requiring explicit approval.

### Possible Pricing Experiment

A higher-value Creator Pro tier may be tested after usage evidence exists, for example:

- INR 999/month with higher screening allowance and workflow automation.

Again, this is a **future pricing hypothesis**, not a committed price.

### Exit Gate

Scale only if:

- retention supports recurring value;
- product reliability improves;
- margins remain healthy;
- users value DealFit-specific workflow rather than only generic model output.

---

## 9. Phase 5 - Small Creator-Management Teams

### Timeline

**Month 8-12+**

### Target Segment

- 1-5 person creator-management teams;
- boutique talent managers;
- small creator collectives.

### Objective

Test whether the same screening workflow creates greater value when one team manages multiple creators.

### Candidate Capabilities

- multiple creator profiles;
- role-based access;
- shared deal queue;
- creator-specific rules;
- manager review;
- portfolio-level conflict checks;
- export/audit capabilities.

### Potential Business Model

Per-seat or workspace pricing may become more appropriate than a single-creator subscription.

No team pricing should be finalized before the individual-creator pilot establishes product value.

---

## 10. Product and Revenue Milestones

| Stage | Product Evidence | Commercial Evidence | Decision |
|---|---|---|---|
| Classroom Prototype | Workflow + safety demonstrated synthetically | None | Demonstrate |
| Private Alpha | Real workflow and trust validation | None | Continue / redesign |
| Creator Beta | Repeat usage + user-value evidence | Pricing interviews | Prepare paid test / hold |
| Paid Pilot | Real usage from paying creators | First MRR | Continue / redesign |
| Creator Pro | Retention + improved unit economics | Higher ARPU test | Expand carefully |
| Small Teams | Multi-creator operational value | Workspace pricing test | Scale selectively |

---

## 11. Responsible Team / Function by Stage

| Workstream | Prototype | Alpha/Beta | Paid Pilot / Scale |
|---|---|---|---|
| Product Management | TEAM008 | Product owner | Product owner |
| UX / Research | TEAM008 | Product + user researcher | Product/UX |
| Engineering | Prototype build | Full-stack engineer | Product engineering |
| AI / Evaluation | Rule logic + synthetic tests | AI engineer / evaluator | AI/ML + evaluation owner |
| Privacy / Security | Documented principles | Security/privacy review | Formal controls and monitoring |
| Legal / Contract Boundaries | Prototype disclaimer | Legal consultation | Defined policy and escalation |
| Customer Support | Not required | Founder/product-led | Support process |
| Commercial / Pricing | Hypothesis only | Pricing interviews | Paid pilot management |

---

## 12. Key Resources Required

### Alpha

- secure web hosting;
- authentication;
- encrypted data store;
- analytics / error logging;
- basic user-research capacity.

### Beta

- controlled LLM/API budget if introduced;
- prompt/version management;
- structured evaluation tooling;
- issue/feedback tracking;
- privacy and security review.

### Paid Pilot

- billing/subscription capability;
- customer support process;
- monitoring/dashboarding;
- incident response;
- production data policies;
- documented service limits.

---

## 13. Roadmap Risks

### Premature Monetization

Charging before repeat value exists may create churn and damage trust.

**Control:** use Alpha/Beta evidence before paid launch.

### Feature Creep

Creator-product requests could expand DealFit into a full CRM, negotiation agent or marketplace.

**Control:** preserve the first wedge: screening and decision support.

### AI Cost Growth

A future API-based product may become expensive if prompts, context or screening volumes grow.

**Control:** measure cost per screening and use deterministic logic where AI adds little value.

### Trust Failure

Incorrect commercial or reputational recommendations may create disproportionate harm.

**Control:** human review, evidence labels, monitoring, override and escalation.

### Weak Willingness to Pay

Creators may find the workflow useful but still prefer spreadsheets or general-purpose AI tools.

**Control:** test actual payment during a small pilot rather than relying only on survey intent.

---

## 14. Roadmap Decision Logic

```text
Does the workflow problem occur repeatedly?
        |
        No --> Stop / Reframe
        |
        Yes
        v
Does DealFit create measurable workflow value?
        |
        No --> Improve / Stop
        |
        Yes
        v
Do creators trust and repeatedly use it?
        |
        No --> Improve UX / Guardrails
        |
        Yes
        v
Will some creators actually pay?
        |
        No --> Reprice / Reposition / Stop
        |
        Yes
        v
Can DealFit serve them with positive contribution margin?
        |
        No --> Reduce serving cost / Reprice
        |
        Yes
        v
Expand carefully to Creator Pro and small teams
```

---

## 15. Roadmap Conclusion

The recommended path is deliberately staged:

> **Prototype -> Private Alpha -> Creator Beta -> First Paid Pilot -> Creator Pro -> Small Teams**

The first meaningful financial objective is not a large revenue target. It is much simpler:

> **Obtain the first genuinely paying creator after evidence of recurring workflow value.**

A small pilot at a hypothetical INR 499/month allows DealFit to test willingness to pay, usage frequency, serving cost and trust before making larger commercial commitments.

The roadmap therefore connects the classroom MVP to a credible first-money milestone without treating untested pricing or adoption assumptions as forecasts.

---

## 16. Traceability

This roadmap builds on:

- `02_Product_Strategy.md`
- `Appendix/PRD/PRD.md`
- `05_Data_Model_Evaluation.md`
- `Appendix/Metrics/Metrics_and_Launch_Gates.md`
- `09_Prototype_MVP.md`
- `Appendix/AI_Self_Evaluation/AI_Product_Self_Evaluation.md`

Detailed economics and scaling assumptions will be maintained in:

`06_Business_Economics_Scaling.md`
