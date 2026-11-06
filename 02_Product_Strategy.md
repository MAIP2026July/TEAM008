# DealFit - Product Strategy

## 1. Product Vision

DealFit aims to become a trusted AI-assisted decision-support tool for independent creators who manage brand partnerships without the support of a professional agent or large management team.

> **Product Vision:** Help independent creators evaluate inbound brand partnerships quickly, consistently, and confidently while keeping the creator in control of the final decision.

DealFit converts fragmented information from a sponsorship pitch and a creator profile into a structured assessment consisting of a fit score, recommendation, confidence level, risk flags, missing information, and an explanation.

> **Core Product Principle: AI recommends. The creator decides.**

---

## 2. Problem and Opportunity

Independent creators increasingly receive sponsorship opportunities through email, social-media direct messages, creator marketplaces, and brand representatives.

For creators without professional representation, every opportunity creates a repeated screening task. The creator must evaluate:

- creator-brand fit;
- audience relevance;
- compensation and commercial attractiveness;
- campaign deliverables;
- exclusivity and usage-rights requirements;
- creator-defined values and excluded categories;
- previous partnership context;
- missing or ambiguous information;
- potential commercial or reputational risks.

This information usually arrives in inconsistent formats and must be combined with subjective judgement. Under time pressure, the screening process can become slow and inconsistent, causing creators to spend time on poor-fit opportunities or overlook promising deals.

The opportunity for DealFit is to provide a structured first-pass screening workflow before the creator invests substantial time researching, negotiating, or reviewing the opportunity.

---

## 3. Target User

The primary target segment is:

> **Independent mid-tier creators with approximately 10,000-200,000 followers who manage their own sponsorship opportunities, together with small creator-management teams of one or two people.**

The MVP deliberately focuses on creators who already receive inbound partnership opportunities. DealFit does not attempt to discover sponsors or generate new partnership leads in the first product stage.

---

## 4. Primary Persona

### Persona: Maya, Independent Lifestyle Creator

**Profile**

- Approximately 75,000 followers
- Primary niche: lifestyle and wellness
- Manages sponsorship decisions independently
- Receives multiple credible or semi-credible partnership enquiries during active months
- Uses email, direct messages, spreadsheets, and personal notes to manage opportunities
- Has previous collaboration experience but no dedicated agent

**Goals**

- Select partnerships that fit the creator's audience and content identity
- Avoid commercially weak deals
- Protect audience trust
- Reduce time spent screening unsuitable pitches
- Identify opportunities worth negotiating rather than prematurely accepting or declining

**Frustrations**

- Partnership information arrives in inconsistent formats
- Important commercial terms may be buried inside long messages
- Comparing compensation and deliverables is difficult without structured information
- Creator-brand fit involves subjective judgement
- Usage rights and exclusivity terms can be overlooked
- Time pressure can produce inconsistent decisions

**Need**

Maya needs a fast first-pass screening mechanism that identifies important facts, highlights concerns, explains the reasoning, and leaves Maya in control of the final partnership decision.

> **Persona Note:** Maya is a design persona created for this product exercise and is not presented as an interviewed or observed real creator.

---

## 5. Jobs to Be Done

### 5.1 Functional Job

> **When I receive a new sponsorship pitch, help me determine whether the opportunity deserves acceptance, negotiation, rejection, or additional review without manually rebuilding the evaluation from scratch every time.**

Supporting functional jobs include:

- extract important deal information;
- compare the opportunity against creator preferences;
- identify missing information;
- flag hard conflicts;
- assess softer creator-brand alignment;
- identify campaign or commercial risks;
- recommend an appropriate next step.

### 5.2 Emotional / Trust Job

> **Help me make a partnership decision with clear supporting information while showing where the recommendation is uncertain or requires my judgement.**

DealFit therefore needs to explain why a recommendation was produced rather than displaying only a numerical score.

### 5.3 Business Job

> **Help me spend more time on commercially relevant opportunities and reduce time lost reviewing unsuitable, incomplete, or misaligned partnership pitches.**

The intended business value is improved screening efficiency and prioritization, not autonomous deal-making.

---

## 6. Current Creator Workflow

Without DealFit, an independent creator may follow a fragmented process:

1. Receive an inbound partnership through email, DM, or marketplace.
2. Read the pitch and campaign brief.
3. Identify the brand, compensation, and expected deliverables.
4. Judge whether the brand fits the creator's niche.
5. Consider likely audience relevance.
6. Check whether the category conflicts with creator preferences or exclusions.
7. Review exclusivity and usage requirements.
8. Search externally for additional brand information when required.
9. Compare the opportunity against previous deals or personal benchmarks.
10. Decide whether to accept, negotiate, decline, or request more information.
11. Record the decision manually if the creator maintains a tracking system.

The workflow repeatedly requires the creator to combine structured facts with contextual judgement.

A detailed current-state swimlane is maintained separately in:

`Appendix/Workflows/Current_State_Workflow.puml`

---

## 7. Key Pain Points

### Fragmented Information

Pitch information may be distributed across email, direct messages, campaign briefs, attachments, and external sources.

### Inconsistent Evaluation

Similar deals may be evaluated differently depending on workload, urgency, memory, or experience.

### Hidden Commercial Risk

Attractive compensation may distract from restrictive usage rights, exclusivity requirements, or demanding deliverables.

### Missing Information

A pitch may omit compensation, deliverables, campaign duration, usage conditions, or other important details.

### Time Cost

Creators spend time manually reviewing opportunities that could potentially be screened quickly.

### Soft-Fit Complexity

Niche fit, audience relevance, tone, and values alignment cannot always be reduced to simple yes/no rules.

### Decision Uncertainty

An imperfect opportunity may still be worth negotiating, making binary Accept/Decline thinking insufficient.

---

## 8. Existing Alternatives and Their Limitations

### Manual Screening

**Strength:** Maximum creator control and contextual judgement.

**Limitation:** Repetitive, time-consuming, and potentially inconsistent.

### Spreadsheet / Checklist

**Strength:** Cheap, transparent, and configurable.

**Limitation:** Effective for hard constraints but weak at synthesizing ambiguous natural-language and contextual information.

### Generic Generative AI Assistant

**Strength:** Can summarize pitch content and provide flexible reasoning.

**Limitation:** Does not inherently provide persistent creator-specific product logic, standardized risk controls, structured output, or an explicit human-review workflow.

### Creator Marketplaces

**Strength:** Can structure portions of the brand-creator relationship.

**Limitation:** Do not necessarily solve cross-channel screening for independently received opportunities.

### Professional Agent / Manager

**Strength:** High-context human judgement, relationship knowledge, and negotiation expertise.

**Limitation:** Not every mid-tier creator has access to, needs, or wants professional representation.

### DealFit Opportunity

DealFit occupies the space between a static checklist and full human representation:

> **Structured rules for hard constraints + AI-assisted synthesis for ambiguous signals + creator judgement for the final decision.**

---

## 9. Why AI?

DealFit does not use AI merely because AI is available. The product separates tasks requiring flexible interpretation from tasks that can be handled deterministically.

### 9.1 What AI Adds

AI can assist with:

- extracting structured information from unstructured pitch text;
- interpreting campaign briefs;
- comparing pitch content with creator-profile information;
- identifying possible niche and values alignment;
- identifying ambiguities and missing information;
- synthesizing multiple weak signals;
- generating concise explanations;
- producing a structured first-pass recommendation.

These tasks involve natural language and context-dependent interpretation, making them less suitable for rigid rule sets alone.

### 9.2 What Should Remain Rule-Based

Deterministic rules should handle clearly defined conditions such as:

- creator-excluded product categories;
- missing compensation;
- creator-defined minimum commercial requirements;
- exclusivity flags;
- broad usage-rights flags;
- mandatory information requirements;
- creator-defined prohibited partnership categories.

A hard creator constraint should not be overridden by persuasive AI reasoning.

### 9.3 What Must Remain Human

The creator must retain responsibility for:

- the final Accept / Negotiate / Decline decision;
- assessing personal or relationship context unavailable to DealFit;
- evaluating legally significant contractual terms;
- making reputational trade-offs;
- determining negotiation strategy;
- overriding the AI recommendation.

DealFit should escalate uncertainty rather than conceal it.

---

## 10. Product Value Proposition

> **DealFit helps independent creators turn an unstructured sponsorship pitch into a structured, explainable partnership decision without manually evaluating every signal from scratch.**

For creators, DealFit aims to provide:

- faster first-pass screening;
- more consistent evaluation;
- visibility into overlooked risks;
- structured negotiation triggers;
- transparent reasoning;
- explicit uncertainty;
- preserved human control.

DealFit's differentiation is therefore **decision quality and workflow support**, not simply AI-generated text.

---

## 11. First Product Wedge

The first product wedge is:

> **Screen one inbound sponsorship opportunity against one persistent creator profile.**

The creator configures a profile once and subsequently submits individual brand pitches for screening.

For each pitch, the MVP returns:

- DealFit score;
- recommendation;
- confidence level;
- key reasons;
- risk flags;
- missing information;
- recommended next action.

The first wedge intentionally excludes broader creator-management capabilities to keep the MVP focused and testable.

---

## 12. Product Principles

### 1. AI Recommends. Creator Decides.

No sponsorship decision should be executed automatically.

### 2. Explain Before Persuading

Every recommendation must identify the important reasons behind it.

### 3. Make Uncertainty Visible

Low-confidence analysis should trigger additional review rather than stronger automation.

### 4. Hard Rules Remain Hard Rules

Creator-defined exclusions cannot be overridden by AI reasoning.

### 5. Separate Facts from Inference

The product should distinguish supplied information, AI interpretation, and information requiring external verification.

### 6. Missing Information Is a Product Output

When evidence is insufficient, DealFit should explicitly identify what is missing.

### 7. Overrides Are Legitimate

Creators can disagree with DealFit and record the reason for their decision.

### 8. Prefer Configuration to False Personalization

Creator-controlled preferences should be used instead of opaque assumptions about creator priorities wherever possible.

---

## 13. Strategic Non-Goals

The MVP will not:

- autonomously accept or decline sponsorships;
- send messages to brands without creator approval;
- execute contracts;
- provide legal advice;
- process payments;
- autonomously negotiate commercial terms;
- claim live brand-reputation knowledge without a grounded source;
- operate as a complete creator CRM;
- discover sponsors;
- replace professional managers, agents, or legal reviewers;
- make irreversible creator or partnership decisions;

These boundaries reduce scope and limit the consequences of incorrect AI output.

---

## 14. Build vs Buy vs API

### Recommended MVP Strategy: API-First Hybrid Build

A custom foundation model is unnecessary for the first DealFit MVP.

### Build

DealFit should own:

- the screening workflow;
- creator-profile configuration;
- deterministic rules;
- scoring logic;
- recommendation interface;
- risk and confidence presentation;
- human override workflow.

### Buy / API

An existing general-purpose LLM API can support natural-language extraction, semantic comparison, and explanation generation during prototype and pilot development.

### Do Not Build Yet

The MVP does not require:

- a custom deep-learning model;
- a proprietary brand-reputation model;
- a creator-market pricing model;
- large-scale recommendation infrastructure.

### Rationale

At MVP stage, the core product hypothesis is not that DealFit owns a unique foundation model.

The hypothesis is that:

> **A carefully designed creator-specific decision workflow combining deterministic rules, AI reasoning, and human judgement produces enough recurring value that independent creators will repeatedly use and eventually pay for the product.**

If later usage produces sufficient high-quality labelled creator decisions and overrides, proprietary modelling can be reconsidered.

---

## 15. Key Product Hypotheses

### H1 - Efficiency

Creators can screen sponsorship opportunities faster with DealFit than through their current manual process.

### H2 - Decision Support

DealFit recommendations and risk flags align sufficiently with informed human judgement to improve prioritization.

### H3 - Explainability

Creators value knowing why a recommendation was generated rather than receiving only a numerical score.

### H4 - Human Override

Users will sometimes override the AI because important creator, relationship, or external context is unavailable to the product. Overrides should be treated as useful feedback rather than automatically classified as product failure.

### H5 - Hybrid Architecture

Combining deterministic rules with AI-assisted reasoning produces more trustworthy screening than relying entirely on generative AI.

### H6 - Recurring Value

The screening problem occurs frequently enough among the target segment to justify repeated product usage.

### H7 - Monetization Potential

If DealFit demonstrably saves time and improves screening confidence, a subset of independent creators may be willing to pay for a recurring plan.

This remains a product hypothesis until tested during a paid pilot.

---

## 16. Initial Success Criteria

The MVP should initially be evaluated across three dimensions.

### Efficiency

- Reduction in time required for first-pass sponsorship screening.
- Reduction in manual information extraction.

### Decision Quality

- Recommendation agreement with an informed human reviewer.
- Ability to identify intentionally seeded high-risk scenarios.
- Ability to detect missing or ambiguous deal information.
- Appropriate use of **Negotiate** and **Manual Review** rather than forcing every opportunity into Accept or Decline.

### Trust and Human Control

- Reasons are provided for every recommendation.
- Confidence or uncertainty is communicated.
- Creator-defined hard exclusions are consistently respected.
- The creator can override the recommendation.
- Unsupported brand-reputation claims are not presented as verified facts.

Detailed quantitative metrics and pilot launch gates will be defined separately in:

`Appendix/Metrics/Metrics_and_Launch_Gates.md`
