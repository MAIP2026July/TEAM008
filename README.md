# TEAM008 - DealFit

## DealFit - An AI-Assisted Brand Partnership Screener for Independent Creators

**Course:** MBA ZG583 - Management of AI Products  
**Team:** Team 008  
**Final Classroom MVP Status:** **PASS FOR DEMONSTRATION**  
**Commercial Status:** **IMPROVE AND VALIDATE FIRST**

> **Product principle: AI recommends. The creator decides.**

---

## Team Members

| Team Member | Register Number |
|---|---|
| Arunachala Gnana Ramanan | 2025MB26107 |
| Boggavarapu Jagannath | 2025MB26076 |
| Alamelu G | 2025MB26016 |
| Abdurrahman Lalsudhesh H | 2025MB26034 |
| Poojagiri V | 2025MB26084 |

---

## Product Overview

DealFit is a human-in-the-loop decision-support product for independent creators who manage inbound sponsorship opportunities without a full-service agent or agency.

The first product wedge is deliberately narrow:

> **Screen one inbound sponsorship opportunity against one persistent creator profile.**

Given a creator profile and sponsorship pitch, DealFit produces:

- a 0-100 screening score;
- **Accept / Negotiate / Decline / Manual Review / Need More Information** recommendation;
- High / Medium / Low confidence;
- provided facts;
- AI-style inferences;
- risk flags;
- missing information;
- external-verification requirements;
- recommended next action.

The score is a structured screening indicator and is **not** presented as a probability of campaign success.

---

## Target User

Primary target users are independent mid-tier creators with approximately **10K-200K followers** who manage sponsorship opportunities themselves.

A secondary segment is small **1-2 person creator-management teams** screening partnership opportunities on behalf of creators.

The design persona used in the classroom prototype is **Maya**, a fictional lifestyle/wellness creator with approximately 75K followers. Maya is a design persona, not a claimed interview participant.

---

## Current Workflow Problem

Inbound brand pitches arrive through channels such as email, direct messages and creator marketplaces. A creator may need to manually assess:

- creator-brand fit;
- audience relevance;
- compensation;
- deliverables;
- usage rights;
- exclusivity;
- personal values and category exclusions;
- existing partnership conflicts;
- missing or contradictory information.

DealFit addresses this repeated **first-pass screening problem**. It does not attempt to replace a creator, manager, lawyer or professional agent.

---

## Why AI + Rules + Human Review?

### Deterministic Rules

Rules are used for explicit conditions such as:

- creator-excluded categories;
- critical missing information;
- creator minimum-compensation preferences;
- usage-rights concerns;
- exclusivity concerns;
- explicit partnership conflicts.

### AI-Style Assessment

Flexible reasoning is used for softer/contextual signals such as:

- creator/campaign fit;
- audience relevance;
- values alignment;
- ambiguity;
- explanation;
- next-action synthesis.

### Human

The creator or manager retains responsibility for:

- final Accept / Negotiate / Decline decision;
- relationship context unavailable to DealFit;
- legal/professional review;
- external reputation verification;
- override.

DealFit never automatically accepts, declines, negotiates, contacts a brand, executes a contract or processes a payment.

---

## Functional Prototype

Final prototype:

`Prototype/DealFit_Prototype.html`

### Run the Prototype

1. Download or clone this repository.
2. Open the `Prototype` folder.
3. Open `DealFit_Prototype.html` in Microsoft Edge or Google Chrome.
4. Review or edit the default creator profile.
5. Select **Save Creator Profile**.
6. Enter a fictional partnership pitch or select one of the S01-S12 synthetic scenarios.
7. Select **Load Scenario** when using a built-in scenario.
8. Select **Analyze with DealFit**.
9. Review recommendation, confidence, facts, inferences, risks, missing information and verification requirements.
10. Continue to the creator-decision screen and record a final human decision or override.

No server, installation, account or API key is required.

Detailed prototype instructions:

`Prototype/README.md`

---

## Important Technical Disclosure

The classroom MVP uses:

- local HTML;
- CSS;
- JavaScript rules;
- configurable creator/deal inputs;
- hard-coded prototype scoring, domain and confidence logic;
- local AI-style assessment behavior.

The current MVP does **not** use:

- a live LLM API;
- live web search;
- live brand-reputation data;
- a real market-rate database;
- legal-analysis services;
- production authentication or cloud storage.

Any future LLM/API integration would require new privacy, reliability, cost, consistency and hallucination evaluation.

---

## Prototype Evaluation Evidence

### Version 1

The first AI-generated prototype was tested against all 12 synthetic scenarios.

- Scenarios executed: **12 / 12**
- Primary expected behaviors passed: **8 / 12 (66.7%)**
- Primary failures: S04, S06, S07 and S11

The testing also revealed weaknesses in audience scoring and confidence semantics.

### Human-Directed Revision

The observed failures were converted into explicit product changes, including:

- separating confidence from risk severity;
- strengthening critical missing-information precedence;
- requiring explicit evidence for strong partnership-conflict flags;
- improving creator/campaign domain comparison;
- propagating material values concerns into visible risk.

### Version 2

Targeted regression testing covered:

- S01 strong-fit regression;
- S03 creator exclusion;
- S04 missing compensation;
- S06 unclear exclusivity;
- S07 weak niche fit;
- S09 explicit partnership conflict;
- S11 ambiguous values fit.

**Result: 7 / 7 targeted regression behaviors passed.**

S10 separately demonstrated a valid human override: DealFit recommended **Accept / High / 75**, while the creator selected **Negotiate** based on context unavailable to the system. The override was recorded and no external action occurred.

Detailed evidence:

- `Appendix/Metrics/Metrics_and_Launch_Gates.md`
- `Appendix/AI_Self_Evaluation/AI_Product_Self_Evaluation.md`
- `09_Prototype_MVP.md`

---

## Trust and Responsible AI Design

The final MVP includes:

- `Creator Review Required` messaging;
- score-not-probability disclaimer;
- explicit creator exclusions;
- critical missing-information escalation;
- High / Medium / Low confidence;
- Provided Facts separated from AI Inferences;
- visible Risk Flags;
- External Verification Required section;
- human override;
- no automatic external action.

The prototype explicitly states:

- Brand reputation not verified
- Market-rate comparison unavailable
- Contract enforceability not assessed

Detailed governance:

- `07_Ethics_Governance_Risk.md`
- `Appendix/Risk_Note/Risk_Note.md`

---

## Roadmap to First Revenue

DealFit follows an evidence-gated roadmap:

```text
Classroom Prototype
        ->
Private Alpha
        ->
Creator Beta
        ->
First Paid Pilot
        ->
Creator Pro
        ->
Small Creator Teams
```

The first commercial objective is:

> **Obtain the first genuinely paying creator after recurring workflow value has been demonstrated.**

A future paid-pilot experiment may test a **hypothetical INR 499/month Creator Pilot plan**. This is a pricing hypothesis for real-payment testing, not validated market pricing or a revenue forecast.

Detailed commercial artifacts:

- `Appendix/Roadmap/Roadmap.md`
- `06_Business_Economics_Scaling.md`

---

## Final Product Decision

### Classroom Prototype

**PASS FOR DEMONSTRATION**

### Real Paid Pilot

**IMPROVE AND VALIDATE FIRST**

### Executive Recommendation

> **Proceed to a small, controlled Private Alpha with consenting creators. Do not scale or claim commercial readiness yet.**

The next investment should prioritize:

- real creator workflow validation;
- measured screening-time/value evidence;
- stronger audience/niche-fit logic;
- secure data handling;
- privacy/security review;
- willingness-to-pay validation.

---

## Repository Guide

### Root Product Artifacts

| File | Purpose |
|---|---|
| `01_Executive_Summary.md` | Leadership summary and final recommendation |
| `02_Product_Strategy.md` | Vision, user, JTBD, wedge and strategic hypotheses |
| `03_PM_Artifact_Pack.md` | Management-friendly PM synthesis and artifact index |
| `04_UX_Workflow_Trust.md` | UX states, confidence, human review and trust design |
| `05_Data_Model_Evaluation.md` | Data, rules, scoring, AI logic and evaluation strategy |
| `06_Business_Economics_Scaling.md` | Monetization hypotheses, economics and scaling logic |
| `07_Ethics_Governance_Risk.md` | Responsible AI, governance and monitoring |
| `08_AI_Collaboration_Log.md` | AI-human collaboration and V1-to-V2 development evidence |
| `09_Prototype_MVP.md` | Final prototype implementation and evaluation record |
| `10_Presentation_Plan.md` | 12-slide leadership presentation storyline |
| `11_Individual_Contribution.md` | Team contribution statement |

### Appendix Artifacts

| Location | Purpose |
|---|---|
| `Appendix/PRD/PRD.md` | Detailed Product Requirements Document |
| `Appendix/Workflows/Current_State_Workflow.puml` | Before-DealFit workflow |
| `Appendix/Workflows/DealFit_Future_Workflow.puml` | Future-state DealFit workflow |
| `Appendix/Wireframes/Wireframes.md` | Low-fidelity screen specifications |
| `Appendix/Data_Model/Data_Model_and_Output_Schema.md` | Logical data model and structured DealFit output schema |
| `Appendix/Topic_Approval/Approved_Topic_Proposal.md` | Original approved DealFit topic proposal |
| `Appendix/Metrics/Metrics_and_Launch_Gates.md` | Prototype evidence and go/no-go gates |
| `Appendix/AI_Self_Evaluation/AI_Product_Self_Evaluation.md` | AI-generated product self-evaluation |
| `Appendix/Roadmap/Roadmap.md` | MVP-to-first-revenue roadmap |
| `Appendix/Risk_Note/Risk_Note.md` | Detailed risk register |

### Prototype

```text
Prototype/
├── DealFit_Prototype.html
├── README.md
└── screenshots/
```

---

## AI Collaboration and Evidence Integrity

Generative AI was used for product-artifact drafting, workflow and wireframe design, prototype generation, test interpretation, revision support, economics structuring and governance drafting.

AI output was not treated as automatically correct. The human tester executed the synthetic scenarios, retained failed Version 1 results, required corrective changes and reran targeted Version 2 regressions.

The project distinguishes:

- design personas from real users;
- synthetic scenarios from real customer data;
- V1 evidence from V2 regression evidence;
- hypothetical prices from willingness-to-pay validation;
- planning assumptions from measured results.

No real-user time savings, satisfaction, retention, subscription conversion, CAC, LTV or willingness-to-pay figures are claimed.

Detailed AI collaboration record:

`08_AI_Collaboration_Log.md`

---

## Known Limitations

- Audience relevance uses a simplified prototype heuristic.
- Scoring weights are unvalidated design assumptions.
- Confidence is rule-based, not probability calibrated.
- Values-sensitive logic uses a small keyword set.
- Most prototype testing used one fictional creator persona.
- All scenario evidence is synthetic.
- No live LLM/API or external grounding is connected.
- Real creator value and willingness to pay remain unmeasured.
- The MVP is not production-secure.

---

## Submission Status

The repository currently documents a complete:

**Strategy -> PM requirements -> workflow/UX -> prototype -> evaluation -> AI self-evaluation -> revision -> roadmap -> economics -> governance**

cycle for DealFit.
