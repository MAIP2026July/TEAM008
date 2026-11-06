# DealFit - Data, Model and Evaluation Strategy

## 1. Purpose

This artifact defines how the DealFit MVP converts creator-profile information and an inbound sponsorship pitch into a structured screening recommendation, and how the product will be evaluated before any paid pilot.

The MVP uses a **hybrid decision-support architecture**:

```text
Creator Profile + Sponsorship Pitch
                |
                v
       Input Validation / Parsing
                |
                v
       Deterministic Rule Layer
                |
                v
        AI Assessment Layer
                |
                v
   Score + Risk + Confidence Layer
                |
                v
        DealFit Recommendation
                |
                v
          Creator Review
                |
                v
 Final Human Decision / Override
```

> **Core principle: AI recommends. The creator decides.**

---

## 2. MVP Analytical Problem

DealFit is not positioned as a statistically trained predictor of sponsorship success.

The MVP addresses a **structured decision-support problem**:

> Given a creator profile, creator-defined constraints, and the information contained in an inbound sponsorship pitch, produce a consistent first-pass screening assessment that helps the creator decide whether to Accept, Negotiate, Decline, or conduct Manual Review / request more information.

The system combines:

1. deterministic rules for explicit constraints;
2. configurable weighted scoring for screening dimensions;
3. AI-assisted interpretation of natural-language inputs;
4. confidence based on evidence completeness and ambiguity;
5. human judgement for the final decision.

---

## 3. Data Inputs

### 3.1 Creator Profile Data

Potential fields include:

- creator/profile name;
- primary niche;
- content themes;
- follower range;
- audience characteristics;
- preferred brand categories;
- excluded brand categories;
- creator values and boundaries;
- minimum compensation preference, if supplied;
- typical content formats;
- previous partnership notes;
- current exclusivity or category conflicts.

### 3.2 Sponsorship Pitch Data

Potential fields include:

- brand name;
- brand category;
- original pitch text;
- campaign brief;
- compensation;
- deliverables;
- campaign timeline;
- usage rights;
- exclusivity;
- target audience;
- payment terms;
- approval requirements;
- additional creator notes.

### 3.3 Data Classification

| Data Type | Example | MVP Treatment |
|---|---|---|
| User-provided fact | Compensation = INR 35,000 | Treated as supplied evidence |
| Pitch-provided fact | Two videos + three stories | Extracted and shown as provided fact |
| Creator rule | Gambling excluded | Deterministic rule |
| AI inference | Broad niche alignment | Labelled as inference |
| Missing data | Payment terms absent | Explicitly flagged |
| External fact | Current brand controversy | Not asserted unless grounded by an identified source |

---

## 4. Data Minimization and Privacy

The MVP should collect only the information required to demonstrate sponsorship screening.

### Sensitive Commercial Information

The following should be treated as sensitive:

- minimum compensation preferences;
- previous deal notes;
- audience information;
- brand communications;
- partnership history;
- creator-defined exclusions and boundaries.

### MVP Privacy Principles

- Do not collect passwords, payment-card information, government IDs, or unnecessary personal data.
- Do not infer protected or sensitive personal characteristics.
- Do not send creator data to an external model provider in a production implementation without explicit privacy and contractual review.
- Prototype storage should be local or clearly documented.
- Synthetic scenarios should use fictional brands and fictional deal information.

---

## 5. Deterministic Rule Layer

Hard creator constraints should be checked before AI-assisted fit reasoning.

### Initial Rule Set

| Rule ID | Condition | Result |
|---|---|---|
| R1 | Brand category matches creator exclusion | Hard conflict; Decline or Manual Review |
| R2 | Compensation absent | Missing-information flag; Low confidence |
| R3 | Creator minimum compensation exists and offer is below it | Commercial risk; normally Negotiate |
| R4 | Deliverables absent | Missing-information flag |
| R5 | Usage rights absent or materially unclear | Risk flag; reduce confidence |
| R6 | Broad paid-media usage rights supplied | Commercial/contractual risk flag |
| R7 | Exclusivity absent or unclear | Missing-information / risk flag |
| R8 | Known creator partnership conflict is entered | Hard or elevated conflict depending on context |
| R9 | Payment terms absent | Missing-information flag |
| R10 | Creator profile is materially incomplete | Reduce confidence; possible Manual Review |

Rules should be configurable where practical. Rule values must not be presented as universal creator-industry standards.

---

## 6. AI Assessment Layer

### 6.1 AI Tasks

The AI-assisted component may perform:

- extraction of structured information from pitch text;
- semantic creator-niche alignment assessment;
- audience-fit interpretation using supplied information;
- campaign-brief clarity assessment;
- values/preference alignment interpretation;
- identification of softer negotiation signals;
- identification of ambiguities;
- concise explanation generation;
- suggested next-action drafting.

### 6.2 AI Tasks Explicitly Excluded from the MVP

The AI must not independently claim:

- verified brand reputation;
- current market-rate benchmarks;
- legal enforceability;
- guaranteed audience response;
- future campaign ROI;
- fraud status;
- contract legality.

These require grounded sources, specialist review, or capabilities outside the MVP.

---

## 7. Structured AI Output Schema

The AI should return structured fields equivalent to the following conceptual schema:

```json
{
  "provided_facts": [],
  "ai_inferences": [],
  "rule_triggers": [],
  "dimension_assessments": {
    "creator_niche_fit": 0,
    "audience_relevance": 0,
    "commercial_attractiveness": 0,
    "campaign_feasibility": 0,
    "values_preference_alignment": 0,
    "risk_information_completeness": 0
  },
  "missing_information": [],
  "external_verification_required": [],
  "risk_flags": [],
  "recommended_action": "",
  "reason_summary": []
}
```

The actual MVP may implement the schema through rule logic, simulated AI output, an LLM API, or Wizard-of-Oz orchestration.

The user-facing product must not expose hidden chain-of-thought. It should show concise reasons and evidence labels only.

---

## 8. DealFit Score

### 8.1 Purpose

The 0-100 DealFit score provides a consistent summary of screening dimensions.

It is **not**:

- a probability that the creator should accept;
- a probability of campaign success;
- a predicted ROI;
- an objective measure of brand quality.

### 8.2 Initial Configurable Dimensions

| Dimension | Prototype Weight |
|---|---:|
| Creator / niche fit | 25% |
| Audience relevance | 20% |
| Commercial attractiveness | 20% |
| Campaign feasibility | 15% |
| Values / preference alignment | 10% |
| Risk and information completeness | 10% |
| **Total** | **100%** |

These weights are prototype assumptions, not validated creator-market standards.

### 8.3 Illustrative Formula

```text
DealFit Score =
(Niche Fit x 0.25)
+ (Audience Relevance x 0.20)
+ (Commercial Attractiveness x 0.20)
+ (Campaign Feasibility x 0.15)
+ (Values Alignment x 0.10)
+ (Risk / Information Completeness x 0.10)
```

Each dimension may be normalized to 0-100.

### 8.4 Precedence Rules

The score does not determine the final recommendation by itself.

The following may override normal score interpretation:

1. creator-defined hard exclusion;
2. materially missing information;
3. Low confidence;
4. severe usage-rights or exclusivity concern;
5. known partnership conflict;
6. contradictory inputs.

---

## 9. Confidence Logic

Confidence indicates the **quality and completeness of the available evidence**, not the strength of the recommendation.

### High Confidence

Typical conditions:

- mandatory fields complete;
- creator profile sufficiently populated;
- no major contradictory input;
- deterministic rules and AI interpretation are aligned;
- limited dependence on unverified assumptions.

### Medium Confidence

Typical conditions:

- non-critical information missing;
- softer indicators are mixed;
- some creator preferences are incomplete;
- limited external verification remains necessary.

### Low Confidence

Typical conditions:

- compensation or another material term is missing;
- material information is contradictory;
- creator profile is insufficient;
- recommendation depends on important unverified assumptions;
- elevated risk requires deeper human review.

### Confidence Guardrail

A Low-confidence assessment must not produce an unqualified **Accept** recommendation.

---

## 10. Recommendation Logic

DealFit returns one AI/product recommendation state:

- **Accept**
- **Negotiate**
- **Decline**
- **Manual Review / Need More Information**

### Recommendation Precedence

```text
1. Hard rule conflict?
   -> Decline or Manual Review

2. Material information missing / Low confidence?
   -> Manual Review / Need More Information

3. Strong fit + acceptable terms + no material risk?
   -> Accept

4. Good potential + improvable commercial/contractual concern?
   -> Negotiate

5. Weak fit with no credible improvement path?
   -> Decline
```

The creator's final human action remains separate:

- Accept
- Negotiate
- Decline
- Need More Information
- Manual Review

---

## 11. Risk Severity Logic

The MVP may classify risk flags as **High**, **Medium**, or **Low**.

### Illustrative Severity Definitions

**High**

- creator-defined exclusion triggered;
- known creator conflict materially affects eligibility;
- material contradiction makes automated screening unsafe.

**Medium**

- broad usage rights;
- unclear exclusivity;
- compensation below creator-defined minimum;
- high deliverable burden relative to provided commercial preference.

**Low**

- non-critical information missing;
- minor brief ambiguity;
- optional detail unavailable.

Severity definitions are prototype configuration and must be reviewed during pilot design.

---

## 12. Baseline Comparisons

DealFit should not be evaluated only against its own outputs.

### Baseline A - Manual Review

A human independently reviews the synthetic pitch without DealFit.

Capture:

- screening time;
- final decision;
- risks noticed;
- missing information noticed.

### Baseline B - Static Checklist

Use a simple checklist containing:

- category allowed?;
- compensation present?;
- deliverables present?;
- usage rights present?;
- exclusivity present?;
- payment terms present?;
- creator minimum compensation met?;
- known conflict present?

### DealFit Comparison

DealFit should demonstrate whether the hybrid workflow adds value beyond the static checklist through:

- soft-fit synthesis;
- recommendation prioritization;
- clearer explanation;
- ambiguity detection;
- structured next actions.

---

## 13. Synthetic Evaluation Pack

The MVP will be evaluated using synthetic test scenarios. All scenarios must be explicitly labelled synthetic and use fictional brand information.

| ID | Scenario | Expected Primary Behaviour |
|---|---|---|
| S01 | Strong creator fit, complete terms, acceptable compensation | Accept candidate |
| S02 | Strong fit, compensation below creator minimum | Negotiate |
| S03 | Excluded category | Hard conflict; Decline / Manual Review |
| S04 | Compensation missing | Need More Information / Low confidence |
| S05 | Broad paid-media usage rights | Negotiate / risk flag |
| S06 | Exclusivity duration unclear | Manual Review / clarification |
| S07 | Weak audience and niche fit | Decline candidate |
| S08 | Very attractive compensation but material terms missing | Manual Review; do not over-trust offer |
| S09 | Existing category partnership conflict | Conflict flag; Decline / Manual Review |
| S10 | Mixed fit where creator has important context unavailable to DealFit | Demonstrate informed override |
| S11 | Complete terms but ambiguous brand values fit | Medium confidence / creator review |
| S12 | Contradictory compensation or deliverable information | Low confidence / Manual Review |

At least 10 scenarios must be executed for the prototype release criteria. Twelve are proposed to improve coverage.

---

## 14. Evaluation Dimensions

Evaluation is divided into four areas:

1. **Workflow Efficiency**
2. **Decision-Support Quality**
3. **Trust and Safety**
4. **Prototype Reliability**

---

## 15. Workflow Efficiency Metrics

### M1 - Screening Time

```text
Screening Time = Decision timestamp - Screening start timestamp
```

Compare manual review, checklist review, and DealFit-assisted review where practical.

### M2 - Time Reduction

```text
Time Reduction % =
(Manual Screening Time - DealFit Screening Time)
/ Manual Screening Time x 100
```

### M3 - Information Extraction Effort

Record whether the creator had to manually reconstruct important deal fields after DealFit parsing.

---

## 16. Decision-Support Quality Metrics

### M4 - Recommendation Agreement Rate

```text
Agreement Rate =
Number of creator final decisions matching DealFit recommendation
/ Number of completed scenarios
```

Agreement is not automatically equivalent to correctness.

### M5 - Informed Override Rate

Track how often the creator overrides DealFit and whether the override is supported by context unavailable to the system.

### M6 - Hard-Rule Compliance

```text
Hard-Rule Compliance =
Correctly enforced hard-rule scenarios
/ Total hard-rule scenarios
```

### M7 - Missing-Information Detection

```text
Missing-Info Recall =
Known missing critical fields correctly identified
/ Total seeded missing critical fields
```

### M8 - Risk-Flag Coverage

Measure whether intentionally seeded material risks are surfaced.

### M9 - Recommendation Consistency

Run the same controlled scenario more than once where an AI model is used and assess whether materially equivalent outputs are produced.

---

## 17. Trust and Safety Metrics

### M10 - Unsupported-Claim Rate

```text
Unsupported-Claim Rate =
Unsupported external factual claims
/ Total evaluated scenario outputs
```

Target direction: **0%**.

### M11 - External-Verification Labelling

Measure whether reputation, market-rate, legal, or other ungrounded claims are correctly labelled as requiring verification.

### M12 - Low-Confidence Escalation

Measure whether seeded incomplete or contradictory scenarios are routed to Manual Review / Need More Information.

### M13 - Explanation Usefulness

Human reviewer rates the explanation as:

- Useful
- Partially useful
- Not useful

### M14 - Human-Control Compliance

Verify that no tested flow performs an external Accept, Decline, Negotiate, message send, contract action, or payment automatically.

Target: **100% compliance**.

---

## 18. Prototype Reliability Metrics

Track:

- scenario execution success rate;
- validation errors;
- broken UI actions;
- inconsistent stored decisions;
- failed reruns;
- mobile rendering defects;
- failure to preserve creator input after recoverable errors.

---

## 19. Proposed Prototype Launch Gates

The following are **proposed prototype gates**, not validated industry benchmarks.

### Gate 1 - Core Functional Coverage

- 100% of Must Have PRD requirements represented in the prototype.

### Gate 2 - Hard-Rule Safety

- 100% compliance on seeded creator-exclusion scenarios.

### Gate 3 - Missing-Information Safety

- At least 90% of seeded critical missing fields identified across the synthetic test pack.

### Gate 4 - Unsupported Claims

- 0 unsupported brand-reputation, market-rate, legal, or external factual claims presented as verified.

### Gate 5 - Human Control

- 100% of scenarios retain creator final-decision authority.
- 0 automatic external actions.

### Gate 6 - Explanation Coverage

- 100% of completed recommendations contain reasons, risks, missing information, and next action where applicable.

### Gate 7 - Guarded Low-Confidence Behaviour

- 100% of deliberately incomplete critical scenarios avoid an unqualified Accept recommendation.

These gates determine readiness for **prototype demonstration**, not commercial launch.

---

## 20. Paid-Pilot Gates

A paid pilot should require stronger evidence than a classroom prototype.

Proposed conditions include:

1. Prototype safety gates passed.
2. Repeated testing with multiple creator profiles.
3. Real creators consent to pilot participation.
4. Meaningful reduction in first-pass screening effort is observed.
5. Creators report that explanations improve prioritization or confidence.
6. False positive/negative recommendation patterns are understood.
7. Data retention and privacy controls are defined.
8. LLM/API terms and data handling are reviewed.
9. Pricing hypothesis is tested rather than assumed.
10. No unresolved launch-blocking trust or legal risk remains.

No paid-pilot claim should be made until evidence is collected.

---

## 21. Stop / Do-Not-Proceed Conditions

DealFit should **not** progress toward a paid pilot if any of the following remain true:

- hard creator exclusions are inconsistently enforced;
- the system frequently invents external facts;
- users cannot tell facts from AI inference;
- Low-confidence cases are presented as definitive Accept recommendations;
- the product encourages users to skip important contractual review;
- sensitive data handling cannot be explained;
- recommendation inconsistency materially reduces trust;
- the prototype cannot demonstrate meaningful workflow value beyond a static checklist;
- creator final-decision authority is weakened;
- a launch-blocking legal, privacy, security, or ethical issue remains unresolved.

---

## 22. Evaluation Procedure

For each synthetic scenario:

1. Record expected seeded conditions and risks.
2. Perform the static-checklist baseline.
3. Run the DealFit prototype.
4. Record score, recommendation, confidence, reasons, flags, missing information, and verification labels.
5. Record the human review decision.
6. Record whether the human agrees or overrides.
7. Record override reason where applicable.
8. Measure screening time where practical.
9. Review unsupported claims.
10. Compare output with expected scenario behavior.

Results should be stored in a simple evaluation table under:

`Appendix/Metrics/`

---

## 23. Evaluation Result Template

| Field | Value |
|---|---|
| Scenario ID | S01 |
| Scenario Type | Strong Fit / Complete |
| Synthetic | Yes |
| Expected Key Risks | None material |
| Checklist Outcome | Proceed |
| DealFit Score | TBD |
| DealFit Recommendation | TBD |
| Confidence | TBD |
| Risk Flags | TBD |
| Missing Information | TBD |
| Unsupported Claims | TBD |
| Human Decision | TBD |
| Override? | TBD |
| Screening Time | TBD |
| Reviewer Notes | TBD |

---

## 24. Model / API Selection Approach

The MVP should remain model-agnostic at product-strategy level.

If an external LLM API is used, candidate selection should consider:

- structured-output reliability;
- instruction following;
- latency;
- cost per screening;
- privacy and data-retention terms;
- availability of enterprise or zero-retention configurations;
- consistency under repeated inputs;
- suitability for controlled prototyping.

The prototype should document the exact provider/model if one is ultimately connected.

If no API is connected, the prototype must clearly describe whether the AI behavior is:

- simulated;
- rule-generated;
- precomputed;
- Wizard-of-Oz;
- or a combination.

---

## 25. Hard-Coded vs Configurable Design

This distinction is required for the later AI self-evaluation.

| Component | MVP Position |
|---|---|
| Creator exclusions | Configurable by creator |
| Minimum compensation | Configurable / optional |
| Creator profile | Configurable |
| Pitch fields | Per deal |
| Screening dimensions | Initially hard-coded |
| Dimension weights | Prototype defaults; should become configurable |
| Recommendation precedence | Hard-coded product safety logic |
| Missing-field definitions | Initially hard-coded |
| Risk-severity mapping | Initially hard-coded / documented |
| LLM prompt | Hard-coded prototype configuration |
| Confidence rules | Initially hard-coded / documented |
| Human final decision | Always creator-controlled |

---

## 26. Feedback and Learning Loop

Creator decisions and overrides may provide future product-learning signals, but they must not automatically become training labels.

Before using override history for personalization, DealFit would need to distinguish:

- genuine product error;
- creator-specific preference;
- context unavailable to the system;
- exceptional one-off decision;
- changed creator strategy;
- data-entry error.

For the MVP, override data is evaluation evidence only.

---

## 27. Traceability

This strategy supports:

- `02_Product_Strategy.md`
- `Appendix/PRD/PRD.md`
- `04_UX_Workflow_Trust.md`
- `Appendix/Wireframes/Wireframes.md`
- `Appendix/Workflows/DealFit_Future_Workflow.puml`

Detailed metric definitions and recorded results will be stored under:

`Appendix/Metrics/`

The prototype implementation will be documented in:

`09_Prototype_MVP.md`

The model/API assumptions, hard-coded logic, configuration gaps, ambiguities, and recommended changes will be assessed in:

`Appendix/AI_Self_Evaluation/AI_Product_Self_Evaluation.md`

