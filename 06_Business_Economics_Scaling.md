# DealFit - Business, Economics and Scaling View

## 1. Purpose

This artifact explains how DealFit could create economic value, test monetization, control serving cost, and scale responsibly from a classroom prototype to a small paid product.

All prices, usage levels and cost figures in this document are **planning assumptions for experimentation**, not validated market prices, forecasts or measured willingness to pay.

> **Commercial principle: prove recurring user value before optimizing growth.**

---

## 2. Business Value Hypothesis

DealFit is intended to create value in three ways.

### 2.1 Time Value

Independent creators currently screen sponsorship pitches manually. DealFit may reduce the time required to extract terms, check creator rules, identify missing information and decide what deserves further attention.

**Evidence status:** Not yet measured with real creators.

### 2.2 Decision-Process Value

DealFit provides a consistent structure across deals:

- creator-fit screening;
- commercial checks;
- risk flags;
- missing-information prompts;
- confidence;
- explanation;
- human override.

The product therefore competes on **workflow quality and decision support**, not simply text generation.

### 2.3 Risk-Avoidance Value

DealFit may help creators notice issues such as:

- compensation below a creator-defined threshold;
- broad usage rights;
- unclear exclusivity;
- creator-defined category conflicts;
- contradictory deal terms;
- missing payment information.

The MVP does not quantify monetary loss avoided. Any future risk-savings claim would require real evidence.

---

## 3. Customer and Payer

### Primary Buyer

Independent creators who already receive enough inbound brand opportunities for screening to be a repeated workflow.

### Secondary Buyer

Small creator-management teams that screen deals for multiple creators.

### Initial Commercial Focus

Start with the individual creator because:

- the workflow is simpler;
- purchasing can be self-service;
- the MVP already models one creator profile;
- product learning can occur before multi-user complexity is introduced.

---

## 4. Competitive / Substitute Economics

DealFit must create enough incremental value to justify payment relative to substitutes.

| Substitute | User Cost | Strength | DealFit Must Be Better At |
|---|---|---|---|
| Manual screening | Creator time | Highest context | Speed and consistency |
| Spreadsheet/checklist | Usually low/free | Transparent rules | Soft-fit synthesis and next action |
| Generic AI assistant | Often existing subscription or free tier | Flexible reasoning | Persistent creator rules, structured guardrails, override workflow |
| Human agent/manager | Potential commission/fee | Deep context and negotiation | Affordable first-pass support, not full replacement |
| Creator marketplace tools | Platform dependent | Structured opportunities | Cross-channel independent screening |

DealFit should not attempt to compete with professional representation on relationship management, negotiation expertise or legal review.

---

## 5. Pricing Strategy - Hypotheses Only

### 5.1 Private Alpha

**Price:** Free

Purpose: Validate problem frequency, trust and workflow value.

### 5.2 Creator Beta

**Price:** Free or invitation-only trial

Purpose: Measure repeat usage and test willingness-to-pay conversations.

Potential pricing research points:

- INR 299/month
- INR 499/month
- INR 999/month

These are research anchors, not committed prices.

### 5.3 First Paid Pilot

Proposed experiment:

> **Creator Pilot - INR 499/month**
> The INR 499 price is a pilot hypothesis designed to test real payment behavior. It is not based on completed willingness-to-pay research.

Illustrative allowance:

- up to 30 partnership screenings per month;
- persistent creator profile;
- decision history;
- risk/missing-information analysis;
- human-controlled recommendations.

### 5.4 Future Creator Pro Hypothesis

Potential experiment after paid-pilot evidence:

> **Creator Pro - INR 999/month**

Possible incremental value:

- higher usage allowance;
- inbox-assisted ingestion;
- richer history;
- configurable scoring preferences;
- exportable deal summaries;
- governed negotiation-draft support.

---

## 6. First-Revenue Economics

Using the hypothetical INR 499 monthly pilot price:

| Paying Creators | Illustrative Monthly Recurring Revenue |
|---:|---:|
| 1 | INR 499 |
| 5 | INR 2,495 |
| 10 | INR 4,990 |
| 25 | INR 12,475 |
| 50 | INR 24,950 |
| 100 | INR 49,900 |

These values are arithmetic scenarios, not forecasts.

The first meaningful commercial milestone is:

> **One creator voluntarily pays for repeated use after experiencing the product.**

The next milestone is not rapid scale. It is proving that several paying creators continue to screen real deals after the initial novelty period.

---

## 7. Cost Structure

### 7.1 Current Classroom MVP

Incremental serving cost is effectively negligible for demonstration because the prototype:

- runs locally;
- uses JavaScript rules;
- has no production hosting requirement;
- does not call an external LLM API.

This does **not** represent the expected production cost structure.

### 7.2 Future Pilot Cost Categories

A real pilot may incur:

- web hosting;
- database/storage;
- authentication;
- analytics/logging;
- LLM/API inference if introduced;
- payment processing;
- monitoring;
- support;
- privacy/security work;
- legal/compliance review.

### 7.3 Variable vs Fixed Cost

**Variable costs may include:**

- LLM tokens/API requests;
- storage per creator/deal;
- transactional email if later used;
- payment fees;
- support time.

**Fixed/semi-fixed costs may include:**

- development;
- observability tools;
- hosting baseline;
- security/privacy review;
- product management;
- legal review.

---

## 8. API / Inference Cost Model

Because the final classroom MVP has no LLM integration, **no actual LLM cost has been measured**.

Before introducing an API, DealFit should measure:

```text
Cost per Screening =
Input-token cost
+ Output-token cost
+ Any retrieval/tool cost
+ Allocated infrastructure cost
```

Then:

```text
Monthly Variable AI Cost per Creator =
Average screenings per creator per month
x Average cost per screening
```

A paid plan should not be priced until observed usage and serving cost are known.

### Illustrative Sensitivity Framework

For a 30-screening monthly allowance:

| Assumed Variable Cost per Screening | Monthly Variable Cost per Creator | Share of INR 499 Price |
|---:|---:|---:|
| INR 0.50 | INR 15 | 3.0% |
| INR 1.00 | INR 30 | 6.0% |
| INR 2.00 | INR 60 | 12.0% |
| INR 5.00 | INR 150 | 30.1% |

These values are **sensitivity assumptions only**. They are not claims about any current model provider's pricing.

The table shows why DealFit should measure real cost per screening before choosing an LLM architecture or final price.

---

## 9. Contribution Margin Framework

For a subscription plan:

```text
Contribution Margin per Creator =
Monthly Subscription Revenue
- Variable AI/API Cost
- Variable Infrastructure Cost
- Payment Fees
- Variable Support Cost
```

```text
Contribution Margin % =
Contribution Margin per Creator
/ Monthly Subscription Revenue x 100
```

### Example Planning Scenario

Assume, purely for planning:

- Price = INR 499/month
- AI/API variable cost = INR 30/month
- Other variable infrastructure/payment/support allocation = INR 70/month

Then:

```text
Illustrative Contribution = 499 - 30 - 70 = INR 399
Illustrative Contribution Margin = 399 / 499 = approximately 80%
```

This is **not a forecast** and must not be presented as actual DealFit economics. Its purpose is to show the framework that the paid pilot should populate with observed costs.

---

## 10. Break-Even Framework

Break-even should be calculated only when the team has a realistic estimate of fixed monthly operating cost.

```text
Break-even Paying Creators =
Monthly Fixed Operating Cost
/ Contribution Margin per Paying Creator
```

For example, if a future pilot had INR 20,000 of monthly fixed/semi-fixed cost and INR 399 contribution per creator:

```text
20,000 / 399 = approximately 51 paying creators
```

Again, INR 20,000 and INR 399 are illustrative planning assumptions, not actual DealFit operating results.

---

## 11. Scaling Scenarios

### Scenario A - 5 Paying Creators

- Revenue at INR 499 price: INR 2,495/month
- Primary objective: prove real payment and repeat usage
- Operational model: founder/product-led support
- Decision: learn, not scale

### Scenario B - 10 Paying Creators

- Revenue: INR 4,990/month
- Primary objective: observe usage frequency, cancellations and support burden
- Decision: refine economics and reliability

### Scenario C - 50 Paying Creators

- Revenue: INR 24,950/month
- Primary objective: validate whether support and inference costs remain manageable
- Requirement: basic production monitoring and billing discipline

### Scenario D - 100 Paying Creators

- Revenue: INR 49,900/month
- Primary objective: determine whether the creator-only product can sustain acquisition and retention
- Requirement: stronger automation, observability, security and support processes

No scenario should be interpreted as a user-growth forecast.

---

## 12. Build vs Buy vs API Economics

### Build Internally

DealFit should build the workflow-specific differentiated layer:

- creator profiles;
- creator rules;
- recommendation precedence;
- risk display;
- evidence labels;
- human override;
- evaluation and audit logic.

### Buy / Use APIs

Commodity capabilities may be sourced through existing services:

- foundation-model inference;
- authentication;
- payments;
- hosting;
- analytics;
- secure storage.

### Do Not Build Initially

Avoid expensive proprietary infrastructure before evidence exists:

- custom foundation model;
- large recommendation platform;
- proprietary reputation crawler;
- complex market-rate prediction engine.

### Economic Rationale

The first-stage moat hypothesis is **workflow design + creator configuration + trust controls + decision history**, not ownership of an expensive base model.

---

## 13. Scaling Constraints

### User Acquisition

The product still needs evidence that creators can be reached at a customer-acquisition cost compatible with INR 499-999/month pricing.

**Current evidence:** None collected.

### Retention

Screening frequency may vary month to month. If sponsorship volume is episodic, monthly subscription retention may be weak.

Possible future alternatives include:

- lower subscription price;
- credit/usage packs;
- seasonal plans;
- team/workspace pricing.

These should be tested rather than assumed.

### Support Burden

Commercial/contract-like questions may cause users to expect expert advice beyond DealFit's product boundary.

**Control:** maintain decision-support disclaimers and escalation boundaries.

### AI Cost

Long prompts, historical context and external retrieval may materially increase cost.

**Control:** preserve deterministic rules where they are sufficient and measure cost per screening.

### Trust and Liability

Scaling increases exposure to incorrect recommendations.

**Control:** auditability, evidence labels, human review and launch gates must scale with usage.

---

## 14. Individual Creator vs Small-Team Economics

### Individual Creator

Potential strengths:

- self-service onboarding;
- simple pricing;
- direct user feedback;
- low organizational complexity.

Potential weaknesses:

- low willingness to pay;
- variable deal frequency;
- higher relative acquisition cost.

### Small Creator-Management Team

Potential strengths:

- more deals screened per account;
- clearer operational productivity value;
- higher potential willingness to pay;
- shared workflow benefits.

Potential weaknesses:

- multi-user permissions;
- stronger security requirements;
- more complex conflict logic;
- higher service expectations.

### Strategic View

DealFit should validate the creator wedge first but remain alert to evidence that small management teams have stronger economics.

---

## 15. Monetization Experiments

Recommended order:

### Experiment 1 - Problem Frequency

Do creators screen enough inbound sponsorships for DealFit to matter repeatedly?

### Experiment 2 - Value

Does DealFit reduce effort or improve prioritization compared with current workflow?

### Experiment 3 - Price Interview

Test reaction to hypothetical INR 299 / 499 / 999 monthly options.

### Experiment 4 - Real Payment

Offer a limited paid pilot, for example INR 499/month.

### Experiment 5 - Retention

Do paying users continue after the first month?

### Experiment 6 - Plan Design

Compare subscription, usage allowance and team/workspace models only after usage data exists.

---

## 16. Business KPIs for a Paid Pilot

Track:

- invited creators;
- activated creators;
- paying creators;
- monthly recurring revenue;
- pitches screened per paying creator;
- 30-day paid retention;
- cancellation reason;
- cost per screening;
- variable cost per creator;
- contribution margin per creator;
- support minutes per creator;
- override rate;
- safety incidents;
- refund requests;
- willingness to recommend / qualitative value feedback.

Do not create target values until the pilot design is finalized.

---

## 17. Scaling Decision Gates

### Continue Investing

Continue when:

- creators use DealFit repeatedly;
- multiple users pay voluntarily;
- contribution margin is positive at observed usage;
- retention supports recurring value;
- trust/safety performance remains acceptable;
- product value is clearer than a generic checklist or prompt.

### Iterate

Iterate when:

- users value the concept but usage is infrequent;
- pricing resistance is high;
- support burden is high;
- inference cost is too high;
- recommendation failures cluster in fixable areas.

### Stop / Reposition

Stop or reposition when:

- creators do not have enough repeated screening volume;
- users prefer generic AI/checklists and will not pay;
- the product cannot maintain trust at acceptable cost;
- the economics require unrealistic scale to break even;
- contractual/reputational risk cannot be responsibly bounded.

---

## 18. Evidence We Do Not Yet Have

DealFit currently has **no evidence** for:

- actual creator willingness to pay;
- real subscription conversion;
- retention;
- customer acquisition cost;
- lifetime value;
- real screening-time savings;
- real API/inference cost;
- real support cost;
- production infrastructure cost;
- churn reduction or revenue uplift for creators;
- creator satisfaction or NPS.

These must not be fabricated in the final report or presentation.

---

## 19. Investment Recommendation

### Current Recommendation

**Fund / support a small validation stage, not scale.**

DealFit has enough prototype evidence to justify:

- Private Alpha preparation;
- real creator interviews/testing;
- improved audience-fit logic;
- secure lightweight hosting;
- controlled willingness-to-pay research.

DealFit does **not** yet have enough evidence to justify:

- significant production infrastructure investment;
- custom-model development;
- broad paid acquisition;
- autonomous decision execution;
- revenue forecasts;
- a claim of product-market fit.

### First Commercial Goal

> **Get the first paying creator only after demonstrating recurring workflow value.**

That milestone provides more useful evidence than an ambitious but unsupported market-size or revenue forecast.

---

## 20. Conclusion

The economic case for DealFit is currently a **testable business hypothesis**, not a proven business model.

The proposed INR 499 paid-pilot price provides a simple mechanism to test whether creators will exchange money for structured sponsorship screening. The business should measure observed usage, variable serving cost, retention, support burden and trust before expanding pricing or functionality.

DealFit should therefore scale in evidence stages:

> **Value validation -> willingness to pay -> first revenue -> contribution margin -> retention -> selective expansion**

This approach minimizes premature infrastructure and model investment while keeping the product economically disciplined.

---

## 21. Traceability

This business/economics view should be read with:

- `Appendix/Roadmap/Roadmap.md`
- `02_Product_Strategy.md`
- `05_Data_Model_Evaluation.md`
- `Appendix/Metrics/Metrics_and_Launch_Gates.md`
- `09_Prototype_MVP.md`
- `Appendix/AI_Self_Evaluation/AI_Product_Self_Evaluation.md`

Detailed ethics, governance and risk controls will be documented in:

`07_Ethics_Governance_Risk.md`

