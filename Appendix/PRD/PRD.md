# DealFit - Product Requirements Document (PRD)

## Document Control

| Field | Value |
|---|---|
| Product | DealFit |
| Version | 1.0 - MVP Draft |
| Team | TEAM008 |
| Course | MBA ZG583 - Management of AI Products |
| Status | Proposed for Prototype Build |
| Primary User | Independent creators managing inbound brand partnerships |
| Product Principle | **AI recommends. The creator decides.** |

---

## 1. Product Summary

DealFit is an AI-assisted brand partnership screening product for independent creators and small creator-management teams. The product evaluates an inbound sponsorship pitch against a persistent creator profile and returns a structured first-pass assessment.

The assessment includes:

- a DealFit score;
- an **Accept**, **Negotiate**, **Decline**, or **Manual Review / Need More Information** recommendation;
- recommendation confidence;
- key supporting reasons;
- hard-rule conflicts;
- commercial and contractual risk flags;
- missing information;
- a recommended next step.

DealFit does not execute the decision. The creator reviews the assessment and records the final decision or override.

---

## 2. Problem Statement

Independent creators regularly receive sponsorship pitches through email, direct messages, creator marketplaces, and brand contacts. Each pitch must be manually assessed for creator-brand fit, audience relevance, compensation, deliverables, usage rights, exclusivity, creator-defined values, category exclusions, and missing information.

The current process is fragmented, repetitive, and inconsistent. Creators may spend excessive time on unsuitable opportunities, accept commercially weak terms, overlook risk factors, or miss good opportunities when screening under time pressure.

DealFit should reduce first-pass screening effort while improving the consistency, transparency, and trustworthiness of the evaluation process.

---

## 3. Product Objective

The MVP objective is to determine whether a hybrid decision-support workflow can help an independent creator screen an inbound sponsorship opportunity faster and more consistently without removing human control.

The MVP should demonstrate that DealFit can:

1. structure an unstructured sponsorship pitch;
2. apply creator-defined hard constraints consistently;
3. assess softer creator-brand fit using AI-assisted reasoning;
4. identify missing or uncertain information;
5. produce an explainable recommendation;
6. support creator review and override;
7. capture decisions for future product learning.

---

## 4. Goals

### G1 - Reduce Screening Effort

Reduce the manual effort required to extract, organize, and review important deal information.

### G2 - Improve Decision Consistency

Apply the same creator preferences, exclusions, and screening dimensions across comparable pitches.

### G3 - Surface Risks Early

Identify missing compensation, unclear deliverables, broad usage rights, exclusivity, category conflicts, and other meaningful concerns before the creator proceeds.

### G4 - Make AI Reasoning Understandable

Present the reasons, evidence, uncertainty, and missing information behind every recommendation.

### G5 - Preserve Human Authority

Require the creator or authorized manager to make the final decision and allow recommendations to be overridden.

### G6 - Generate Pilot Evidence

Capture sufficient usage, agreement, override, trust, and time-saved evidence to decide whether DealFit deserves a paid pilot.

---

## 5. Non-Goals

The MVP will not:

- automatically accept or decline a partnership;
- send external communications without creator approval;
- sign or execute contracts;
- provide legal advice;
- process payments;
- autonomously negotiate with brands;
- discover new sponsorship opportunities;
- operate as a complete creator CRM;
- claim verified live brand-reputation knowledge without a grounded source;
- replace an agent, manager, or legal reviewer;
- train a proprietary foundation model;
- guarantee commercial, audience, or reputational outcomes.
- make irreversible creator or partnership decisions.

---

## 6. Target User and Persona

### Primary User

Independent mid-tier creators with approximately 10,000-200,000 followers who manage sponsorship opportunities themselves.

### Secondary User

Small creator-management teams of one or two people who screen partnership opportunities on behalf of creators.

### Design Persona

**Maya**, an independent lifestyle and wellness creator with approximately 75,000 followers. Maya receives multiple sponsorship enquiries during active months, manages deals without a dedicated agent, and uses email, direct messages, spreadsheets, and personal notes.

Maya requires a fast, explainable first-pass assessment that highlights commercial and reputational concerns without making the final decision.

> Maya is a design persona for product development and is not presented as an interviewed participant.

---

## 7. Jobs to Be Done

### Functional Job

> When I receive a sponsorship pitch, help me determine whether the opportunity deserves acceptance, negotiation, rejection, or additional review without rebuilding the evaluation from scratch.

### Trust Job

> Show me why the recommendation was produced, what information is missing, and where I should use my own judgement.

### Business Job

> Help me focus time on commercially relevant opportunities while reducing effort spent on unsuitable or incomplete pitches.

---

## 8. MVP User Journey

1. The creator creates or edits a persistent creator profile.
2. The creator submits a new sponsorship pitch and known deal terms.
3. DealFit validates whether mandatory information is present.
4. The deterministic rules layer checks creator exclusions and explicit constraints.
5. The AI-assisted layer assesses softer fit and interprets the campaign brief.
6. DealFit calculates the screening result and confidence state.
7. DealFit displays the recommendation, reasons, risk flags, missing information, and next action.
8. The creator reviews the result.
9. The creator accepts the recommendation, overrides it, or requests further review.
10. DealFit stores the decision and optional override reason for future evaluation.

---

## 9. MVP Scope

### In Scope

- Creator profile setup and editing
- Preferred and excluded brand categories
- Creator-defined minimum commercial preferences
- Manual pitch entry or copy-paste
- Structured extraction of key pitch fields
- Missing-information detection
- Deterministic hard-rule checks
- AI-assisted creator-brand fit assessment
- DealFit score
- Recommendation: Accept / Negotiate / Decline / Manual Review
- Confidence state: High / Medium / Low
- Key reasons
- Risk flags
- Recommended next action
- Human confirmation or override
- Override-reason capture
- Synthetic test scenarios
- Prototype screenshots and demonstration

### Out of Scope

- Email or social-media inbox integration
- Real-time web reputation research
- Contract execution
- Payment processing
- Automated negotiation
- Automated replies
- Live market-rate database
- Multi-user enterprise administration
- Full creator pipeline or CRM
- Proprietary model training

---

## 10. User Stories

| ID | User Story | Priority |
|---|---|---|
| US-01 | As a creator, I want to create a reusable profile so that each pitch is evaluated against my niche, audience, preferences, and exclusions. | Must |
| US-02 | As a creator, I want to paste an inbound pitch so that DealFit can structure the information for screening. | Must |
| US-03 | As a creator, I want missing fields to be identified so that I know what to ask the brand before deciding. | Must |
| US-04 | As a creator, I want excluded categories to trigger a clear conflict so that hard personal boundaries are respected. | Must |
| US-05 | As a creator, I want a recommendation and fit score so that I can prioritize opportunities quickly. | Must |
| US-06 | As a creator, I want reasons and risk flags so that I understand the recommendation. | Must |
| US-07 | As a creator, I want confidence to be visible so that I know when additional review is required. | Must |
| US-08 | As a creator, I want to override DealFit so that contextual knowledge remains part of the final decision. | Must |
| US-09 | As a creator, I want the product to distinguish facts from AI inference so that I do not treat assumptions as verified information. | Must |
| US-10 | As a creator, I want a suggested next action so that I know whether to accept, negotiate, decline, or ask for information. | Should |
| US-11 | As a small manager, I want previous decisions and overrides stored so that screening patterns can be reviewed later. | Should |
| US-12 | As a creator, I want configurable scoring preferences so that DealFit reflects my priorities. | Could |

---

## 11. Functional Requirements

### FR-01 - Creator Profile

The product shall allow the user to capture and edit:

- creator name or profile label;
- creator niche and content themes;
- follower range;
- audience characteristics;
- preferred partnership categories;
- excluded categories;
- stated values or partnership boundaries;
- minimum compensation preference, if supplied;
- typical content formats;
- previous partnership notes, if available.

### FR-02 - Pitch Input

The product shall allow the user to enter:

- brand name;
- brand category;
- campaign brief or pitch text;
- proposed compensation;
- deliverables;
- campaign timeline;
- usage rights;
- exclusivity terms;
- target audience information;
- additional notes.

### FR-03 - Information Extraction

The product shall extract or organize available pitch information into structured fields while retaining the original user-entered text.

### FR-04 - Mandatory Field Validation

The product shall identify missing or unclear information, including where relevant:

- compensation;
- deliverables;
- deadline or campaign period;
- usage rights;
- exclusivity;
- payment terms;
- approval requirements.

### FR-05 - Hard-Rule Screening

The product shall evaluate deterministic creator constraints before generating a normal recommendation.

Examples include:

- excluded category conflict;
- compensation missing;
- explicit minimum compensation not met;
- usage-rights concern;
- exclusivity concern;
- mandatory information missing.

### FR-06 - AI-Assisted Fit Assessment

The product shall assess softer signals such as:

- niche alignment;
- audience relevance based on supplied information;
- campaign-creator consistency;
- values or tone alignment;
- brief clarity;
- potential negotiation opportunity.

### FR-07 - Recommendation

The product shall return one of four recommendations:

- **Accept** - strong fit with no material unresolved concern;
- **Negotiate** - potentially valuable but commercial or contractual terms require improvement;
- **Decline** - clear mismatch or unacceptable creator-defined conflict;
- **Manual Review / Need More Information** - insufficient evidence, low confidence, or elevated risk.

### FR-08 - DealFit Score

The product shall display a score on a 0-100 scale for screening convenience.

The score shall not be described as an objective truth or probability of success. The interface shall state that the score is a structured decision-support indicator.

### FR-09 - Confidence

The product shall display **High**, **Medium**, or **Low** confidence based on data completeness, conflict level, and assessment certainty.

Low confidence shall not produce an unqualified Accept recommendation.

### FR-10 - Explanation

Every recommendation shall include:

- at least two supporting reasons where sufficient information exists;
- the most important concern or trade-off;
- missing information;
- information requiring external verification;
- a suggested next action.

### FR-11 - Risk Flags

The product shall visibly flag relevant risks, including:

- category conflict;
- insufficient compensation information;
- high deliverable burden;
- broad or unclear usage rights;
- exclusivity;
- missing payment terms;
- unusually attractive or materially incomplete offer;
- unverified brand information;
- possible conflict with existing partnerships.

### FR-12 - Human Decision

The product shall allow the creator to record:

- Accept;
- Negotiate;
- Decline;
- Need More Information;
- Manual Review.

### FR-13 - Override

If the creator's decision differs from DealFit's recommendation, the product shall allow an optional override reason to be recorded.

### FR-14 - Decision Record

The MVP should retain a basic record of:

- pitch input;
- DealFit recommendation;
- confidence;
- risk flags;
- final creator decision;
- override reason, if any.

---

## 12. AI Requirements

### AIR-01 - Structured Output

The AI output shall follow a defined schema rather than free-form prose only.

Required fields:

- extracted pitch facts;
- inferred fit signals;
- recommendation;
- confidence;
- reasoning;
- risk flags;
- missing information;
- verification requirements;
- next action.

### AIR-02 - Grounding Boundary

The AI shall use only:

- creator-profile information;
- pitch information;
- configured product rules;
- explicitly connected and identified data sources.

The AI shall not present unsupported live reputation or market-rate information as verified fact.

### AIR-03 - Fact / Inference Separation

The output shall distinguish:

- **Provided Fact**;
- **AI Inference**;
- **External Verification Required**.

### AIR-04 - Uncertainty

When information is incomplete or contradictory, the AI shall lower confidence and recommend further review or information gathering.

### AIR-05 - Consistency

Equivalent inputs and settings should produce materially consistent recommendations during controlled testing.

### AIR-06 - No Legal or Financial Guarantee

The AI shall not claim that a deal is legally safe, guaranteed profitable, or certain to improve audience outcomes.

### AIR-07 - Explainability

The AI shall provide concise, user-relevant reasons rather than exposing internal chain-of-thought or unsupported technical detail.

---

## 13. Scoring and Recommendation Logic

The MVP may use a configurable weighted screening model with the following initial dimensions:

| Dimension | Illustrative Weight |
|---|---:|
| Creator / niche fit | 25% |
| Audience relevance | 20% |
| Commercial attractiveness | 20% |
| Campaign feasibility | 15% |
| Values / preference alignment | 10% |
| Risk and information completeness | 10% |

> These weights are prototype assumptions and must be documented as configurable rather than validated market truth.

### Illustrative Recommendation Bands

| Condition | Recommendation |
|---|---|
| Hard exclusion or unacceptable conflict | Decline or Manual Review |
| Material information missing or confidence low | Manual Review / Need More Information |
| Strong fit and acceptable terms | Accept |
| Good potential but commercial or contractual concern | Negotiate |
| Weak fit with no credible improvement path | Decline |

The recommendation shall not be based on score alone. Hard rules, missing information, risk severity, and confidence may override the normal score band.

---

## 14. Trust and Safety Requirements

### TSR-01 - No Automatic Execution

DealFit shall not accept, decline, negotiate, or communicate externally without creator approval.

### TSR-02 - Visible Uncertainty

Confidence and missing information shall be displayed near the recommendation.

### TSR-03 - Hard-Rule Protection

Creator-defined exclusions shall not be overridden by AI-generated positive reasoning.

### TSR-04 - Reputation Caution

Unverified brand-reputation assessments shall be labelled as unverified or omitted.

### TSR-05 - Privacy

Creator profile, audience information, compensation preferences, pitch content, and partnership history shall be treated as sensitive commercial data.

### TSR-06 - Override and Escalation

The creator shall be able to override the recommendation or escalate to manual review.

### TSR-07 - Appropriate Disclaimer

The interface shall state that DealFit provides decision support and does not provide legal, financial, or contractual advice.

---

## 15. UX States

The prototype shall demonstrate the following states:

1. **Empty State** - no creator profile or pitch submitted;
2. **Ready State** - creator profile exists and a pitch can be entered;
3. **Processing State** - the pitch is being assessed;
4. **Recommendation State** - score, recommendation, confidence, reasons, and flags displayed;
5. **Missing Information State** - critical information absent;
6. **Hard Conflict State** - creator exclusion or mandatory conflict detected;
7. **Low-Confidence State** - manual review required;
8. **Override State** - creator records a different decision;
9. **Error State** - analysis cannot be completed;
10. **No External Verification State** - brand/reputation information is not verified.

---

## 16. Acceptance Criteria

### AC-01 - Profile

Given a creator profile form, when the creator enters required information and saves it, then the profile is retained for pitch screening.

### AC-02 - Exclusion Rule

Given a pitch in a creator-excluded category, when the analysis runs, then DealFit displays a clear hard-conflict flag and does not return an unqualified Accept recommendation.

### AC-03 - Missing Compensation

Given a pitch without compensation information, when the analysis runs, then DealFit identifies compensation as missing and recommends Need More Information or Manual Review.

### AC-04 - Explainability

Given a completed analysis, then the result includes a recommendation, confidence, reasons, risks, missing information, and next action.

### AC-05 - Usage Rights

Given broad or unclear usage-rights terms, when the analysis runs, then DealFit displays a usage-rights risk flag.

### AC-06 - Human Override

Given any DealFit recommendation, when the creator selects a different final decision, then the product permits the override and optionally records the reason.

### AC-07 - Fact / Inference Separation

Given an analysis containing both supplied information and AI interpretation, then the interface distinguishes facts from inference and identifies external verification requirements.

### AC-08 - Low Confidence

Given incomplete or contradictory pitch information, then confidence is reduced and the product does not present the recommendation as definitive.

### AC-09 - No Automatic External Action

Given a completed screening result, then no message, acceptance, rejection, contract, or payment is executed automatically.

### AC-10 - Synthetic Test Coverage

The prototype shall be tested against at least 10 realistic synthetic pitch scenarios covering strong fit, poor fit, negotiation, missing information, hard conflict, and high-risk cases.

---

## 17. Prioritization - MoSCoW

### Must Have

- Creator profile
- Pitch input
- Mandatory-field validation
- Hard exclusion rules
- AI-assisted fit assessment
- Score
- Four-way recommendation
- Confidence
- Reasons
- Risk flags
- Missing information
- Human decision and override
- Disclaimer

### Should Have

- Basic decision history
- Suggested next action
- Configurable minimum compensation
- Override-reason capture
- Synthetic scenario selector for demonstration

### Could Have

- Configurable scoring weights
- Duplicate pitch detection
- Creator-specific learning from previous overrides
- Negotiation-message drafting with explicit approval
- Exportable deal summary

### Won't Have in MVP

- Live inbox integration
- Automated brand communication
- Contract signing
- Payment processing
- Live brand-reputation scraping
- Full market-rate database
- Custom model training
- Full creator CRM

---

## 18. Dependencies

The MVP depends on:

- an interface for creator profile and pitch input;
- deterministic rule configuration;
- an LLM or Wizard-of-Oz reasoning process;
- a structured output schema;
- local or prototype-level data storage;
- a synthetic test-scenario pack;
- documented scoring and confidence logic.

Production deployment would additionally require secure authentication, encrypted storage, privacy controls, observability, approved model/API access, and legal review.

---

## 19. Risks and Mitigations

| Risk | Product Impact | MVP Mitigation |
|---|---|---|
| Polished but poor-fit pitch receives a positive score | Misleading recommendation | Hard rules, risk flags, explanation, human review |
| Large well-known brands are favoured | Bias against smaller brands | Do not use brand popularity as a proxy for fit |
| AI invents brand reputation or market-rate facts | False confidence | Label unverified information and prohibit unsupported claims |
| Creator over-relies on score | Loss of judgement | Confidence, explanation, override, and disclaimer |
| Missing contract context | Incomplete risk assessment | Detect missing information and escalate |
| Sensitive commercial data is exposed | Privacy and trust failure | Minimal data collection and secure handling requirements |
| Fixed weights do not reflect creator priorities | Poor personalization | Mark weights as configurable assumptions |
| Recommendation inconsistency | Low product trust | Structured prompts, fixed schema, repeated-scenario testing |

A full risk register will be maintained in:

`Appendix/Risk_Note/Risk_Note.md`

---

## 20. Success Metrics

The MVP will be evaluated using:

### User Value

- median screening time per pitch;
- time reduction compared with manual screening;
- recommendation agreement rate;
- informed override rate;
- repeat-use intent;
- perceived usefulness.

### AI / Product Quality

- hard-rule compliance rate;
- missing-information detection rate;
- high-risk scenario flag rate;
- recommendation consistency;
- explanation relevance;
- unsupported-claim rate.

### Trust

- user understanding of the recommendation;
- confidence calibration by scenario completeness;
- percentage of low-confidence cases correctly escalated;
- percentage of users who recognize the recommendation as decision support.

Detailed definitions and launch gates will be maintained in:

`Appendix/Metrics/Metrics_and_Launch_Gates.md`

---

## 21. Prototype Release Criteria

The prototype may be considered ready for demonstration when:

- all Must Have requirements are represented;
- at least 10 synthetic scenarios can be assessed;
- exclusions and missing information produce the expected guarded behavior;
- every result contains recommendation, confidence, reasons, risks, and next action;
- human override works;
- all automated external actions remain disabled;
- hard-coded and configurable elements are documented;
- AI self-evaluation has been completed;
- known limitations are visible in the prototype documentation.

---

## 22. Open Questions

The following decisions require validation during prototype testing:

1. Which scoring dimensions should be creator-configurable?
2. Should compensation benchmarks be entered by creators or excluded from the first MVP?
3. How should confidence be calculated and explained?
4. Which risk flags should force Manual Review rather than Negotiate?
5. How much pitch history should be retained?
6. How should creator override data be used without introducing feedback bias?
7. What minimum value would justify a paid pilot?
8. Which LLM/API provides the best balance of quality, privacy, latency, and cost?
9. Should contract-language analysis remain limited to flagging potentially important clauses?
10. What creator data must never be sent to a third-party model provider?

---

## 23. Traceability to Product Strategy

This PRD implements the strategic decisions documented in:

`02_Product_Strategy.md`

The current manual workflow is documented in:

`Appendix/Workflows/Current_State_Workflow.puml`

The future DealFit workflow will be documented in:

`Appendix/Workflows/DealFit_Future_Workflow.puml`

The prototype implementation and deviations from this PRD will be documented in:

`09_Prototype_MVP.md`

The AI-generated product self-evaluation will be documented in:

`Appendix/AI_Self_Evaluation/AI_Product_Self_Evaluation.md`
