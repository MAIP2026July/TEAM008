# DealFit - UX, Workflow and Trust Design

## 1. UX Objective

DealFit should help an independent creator move from an unstructured sponsorship pitch to a structured, explainable screening decision with less manual effort.

The experience must not create the impression that DealFit is an autonomous agent, legal reviewer, verified reputation service, or guaranteed predictor of campaign success.

> **UX Principle: AI recommends. The creator decides.**

The interface should make the following visible at every important decision point:

- what information was provided by the creator or brand;
- what DealFit inferred;
- what is missing;
- what requires external verification;
- why the recommendation was produced;
- how confident the system is;
- what the creator should do next;
- how the creator can override the recommendation.

---

## 2. Experience Principles

### 2.1 Reduce Cognitive Load

DealFit should convert long, inconsistent pitch content into a short and consistent screening summary.

### 2.2 Progressive Disclosure

The first result view should show the recommendation, score, confidence, key reasons, and major risks. Detailed analysis should be available without overwhelming the user.

### 2.3 Facts Before Interpretation

Provided facts should appear before AI-generated interpretation. A user should never have to guess whether a piece of information came from the pitch, creator profile, a configured rule, or AI inference.

### 2.4 Make Uncertainty Actionable

Low confidence should lead to a clear next step such as requesting compensation details, clarifying usage rights, or escalating for manual review.

### 2.5 Guardrails Before Persuasion

Hard creator exclusions and mandatory-field failures should be evaluated before softer AI reasoning.

### 2.6 Preserve User Agency

The creator should be able to disagree with every recommendation and record a different decision.

### 2.7 Avoid False Precision

The DealFit score is a structured screening indicator, not a probability of deal success. The interface must not imply mathematical certainty that the prototype cannot support.

---

## 3. End-to-End User Flow

1. Creator opens DealFit.
2. Creator creates or selects a persistent profile.
3. Creator pastes a pitch and enters known deal terms.
4. DealFit checks whether mandatory information is present.
5. Deterministic rules check exclusions and explicit constraints.
6. AI-assisted analysis assesses softer fit dimensions.
7. DealFit combines the rule results and AI assessment.
8. DealFit displays the recommendation, score, confidence, reasons, risk flags, missing information, and verification requirements.
9. Creator reviews the output.
10. Creator records a final decision or override.
11. DealFit stores the recommendation, final decision, and optional override reason for evaluation.
12. Creator takes any external action manually.

The complete future-state swimlane is maintained in:

`Appendix/Workflows/DealFit_Future_Workflow.puml`

---

## 4. Information Architecture

The MVP should use four primary product areas.

| Area | Purpose |
|---|---|
| Creator Profile | Stores creator context, preferences, exclusions, and commercial boundaries |
| New Deal | Captures pitch text and known deal terms |
| DealFit Analysis | Displays structured facts, recommendation, confidence, reasons, risks, and missing information |
| Decision Review | Captures the creator's final decision, override, and optional feedback |

A lightweight history section may be included as a **Should Have** feature to demonstrate stored recommendations and creator decisions.

---

## 5. Screen 1 - Creator Profile

### Purpose

Capture reusable creator context before individual pitches are assessed.

### Required Fields

- Creator/profile name
- Primary niche
- Content themes
- Follower range
- Audience characteristics
- Preferred brand categories
- Excluded categories
- Creator values or boundaries
- Minimum compensation preference, if used
- Typical content formats

### Optional Fields

- Previous partnership notes
- Existing category conflicts
- Preferred campaign formats
- Preferred deal characteristics

### Primary Action

**Save Creator Profile**

### Secondary Action

**Reset to Demo Persona**

### Trust Requirements

- Explain why each sensitive field is collected.
- Mark commercial preferences and past deal information as sensitive.
- Allow the creator to skip optional fields.
- Do not infer protected or sensitive personal attributes.
- Show that profile information can be edited before every analysis.

### Validation

- A niche or content theme is required.
- At least one audience descriptor is recommended.
- Preferred and excluded categories cannot silently conflict.
- Minimum compensation must be non-negative when supplied.

---

## 6. Screen 2 - New Partnership / Pitch Input

### Purpose

Allow the creator to submit an inbound sponsorship opportunity for first-pass screening.

### Input Methods

The MVP should support:

1. pasting the original pitch text; and
2. entering or confirming structured deal fields.

### Required or Recommended Fields

- Brand name
- Brand category
- Pitch / campaign brief
- Proposed compensation
- Deliverables
- Campaign timeline
- Usage rights
- Exclusivity terms
- Target audience, if supplied
- Payment terms, if supplied
- Additional notes

### Primary Action

**Analyze with DealFit**

### Secondary Actions

- **Clear Pitch**
- **Load Synthetic Scenario**
- **Save Draft**, if implemented

### Inline UX Guidance

- Show example content beneath complex fields.
- Mark unknown terms as **Not Provided** instead of forcing the creator to guess.
- Do not treat an empty field as a negative fact; treat it as missing information.
- Allow the creator to review extracted fields before final analysis where practical.

### Validation and Guardrails

- Brand name and pitch text are required to run the normal flow.
- Missing compensation, deliverables, usage rights, or exclusivity should remain visible as missing information.
- A creator-excluded category should trigger the hard-conflict path.
- Unusually attractive but incomplete offers should be flagged for additional scrutiny rather than labelled fraudulent.

---

## 7. Screen 3 - DealFit Analysis

### Purpose

Present one compact, explainable screening result without implying that the product has made the final partnership decision.

### 7.1 Result Header

The top of the result should display:

- **DealFit Score:** 0-100
- **Recommendation:** Accept / Negotiate / Decline / Manual Review
- **Confidence:** High / Medium / Low
- **Decision-Support Label:** “Creator review required”

### 7.2 Recommendation Design

Recommended visual treatment:

| Recommendation | Visual Treatment | Meaning |
|---|---|---|
| Accept | Positive label, not celebratory | Strong apparent fit with no material unresolved concern |
| Negotiate | Amber label | Potentially valuable, but terms should change |
| Decline | Red label | Clear mismatch or unacceptable creator-defined conflict |
| Manual Review / Need More Information | Neutral or purple label | Insufficient evidence, low confidence, or elevated risk |

Color must not be the only way the recommendation is communicated. Text labels and icons should also be used.

### 7.3 Score Communication

Display this helper text near the score:

> “The DealFit score is a structured screening indicator based on supplied information and configured product logic. It is not a probability of campaign success.”

### 7.4 Explanation Blocks

The result should contain five distinct blocks.

#### A. Provided Facts

Examples:

- Brand category: Wellness
- Compensation: INR 35,000
- Deliverables: Two short-form videos and three stories
- Usage rights: Six months, paid media included

#### B. AI Inferences

Examples:

- The campaign appears broadly aligned with the creator's wellness niche.
- The requested deliverables may be high relative to the supplied compensation preference.

Each line must be labelled as an inference, not a verified fact.

#### C. Risk Flags

Examples:

- Broad paid-media usage rights
- Category excluded by creator
- Exclusivity period unclear
- Payment terms not provided
- Deliverable burden appears high

Risk severity may be shown as **High**, **Medium**, or **Low**, but the MVP must document how severity is assigned.

#### D. Missing Information

Examples:

- Payment timeline
- Content approval process
- Exclusivity duration
- Product shipping responsibility

#### E. External Verification Required

Examples:

- Brand reputation not verified
- Market-rate comparison unavailable
- Contract enforceability not assessed

### 7.5 Recommended Next Action

The next action should be concise and operational.

Examples:

- “Proceed, subject to creator review of final contract terms.”
- “Negotiate compensation and narrow paid-media usage rights.”
- “Request payment terms and exclusivity duration before deciding.”
- “Decline because the category conflicts with the creator's exclusion list.”

### 7.6 Detailed Analysis

An expandable section may show dimension-level assessments:

- Creator / niche fit
- Audience relevance
- Commercial attractiveness
- Campaign feasibility
- Values / preference alignment
- Risk and information completeness

The interface should show dimension labels and explanations. It should not expose hidden chain-of-thought.

---

## 8. Screen 4 - Creator Decision and Override

### Purpose

Ensure the final partnership decision remains human-controlled and capture evaluation evidence.

### Available Final Decisions

- Accept
- Negotiate
- Decline
- Need More Information
- Manual Review

### Agreement Flow

If the creator agrees with DealFit:

1. Creator selects the matching decision.
2. DealFit records the agreement.
3. No external action is performed automatically.

### Override Flow

If the creator chooses a different decision:

1. DealFit displays: **“You are overriding the recommendation.”**
2. Creator may select or enter an override reason.
3. DealFit records the final creator decision and reason.
4. The override is treated as feedback, not automatically as proof that the model was wrong.

### Suggested Override Reasons

- Personal relationship with brand contact
- Existing category conflict not represented in profile
- Better or worse commercial context than entered
- Audience context unavailable to DealFit
- Contract concern
- Brand information known to creator
- Recommendation reasoning was not persuasive
- Other

### Final Confirmation

Display:

> “Decision recorded. DealFit has not contacted the brand or executed any external action.”

---

## 9. Critical UX States

### 9.1 Empty State

**Situation:** No creator profile exists.

**Message:** “Create a creator profile before screening a partnership.”

**Action:** Create Profile

### 9.2 Ready State

**Situation:** Creator profile exists and the pitch form is available.

**Message:** “Paste a pitch or load a synthetic scenario.”

### 9.3 Processing State

**Situation:** DealFit is evaluating the pitch.

**Requirements:**

- Show a visible progress state.
- Do not claim external research unless an external source is actually connected.
- Use wording such as **“Evaluating supplied information”**, not **“Verifying the brand.”**

### 9.4 Missing Information State

**Situation:** Critical fields are absent.

**Behavior:**

- Set confidence to Low.
- List missing fields.
- Recommend Need More Information or Manual Review.
- Provide suggested questions for the brand where appropriate.

### 9.5 Hard Conflict State

**Situation:** Pitch conflicts with a creator-defined exclusion.

**Behavior:**

- Display a prominent hard-conflict flag.
- Do not return an unqualified Accept recommendation.
- Identify the exact creator rule triggered.

### 9.6 Low-Confidence State

**Situation:** Information is incomplete, contradictory, or ambiguous.

**Behavior:**

- Display Low confidence near the recommendation.
- Explain what caused low confidence.
- Recommend further information or manual review.

### 9.7 No External Verification State

**Situation:** Reputation, market-rate, or legal information is not grounded.

**Message:** “External verification was not performed. Review relevant sources before making a final decision.”

### 9.8 Error State

**Situation:** The system cannot complete the analysis.

**Behavior:**

- Preserve entered data where possible.
- Explain that the analysis was not completed.
- Allow retry or manual review.
- Do not show a stale or partial recommendation as final.

---

## 10. Confidence Design

Confidence should represent the quality and completeness of the available evidence, not how persuasive the recommendation sounds.

### High Confidence

Possible conditions:

- mandatory fields are complete;
- no major contradiction exists;
- creator profile is sufficiently complete;
- rule results and AI assessment are aligned.

### Medium Confidence

Possible conditions:

- one or more non-critical fields are missing;
- softer fit indicators are mixed;
- creator preferences are incomplete;
- some external verification remains necessary.

### Low Confidence

Possible conditions:

- material fields are missing;
- information is contradictory;
- risk is elevated;
- the creator profile is insufficient;
- the recommendation depends on unverified assumptions.

### Confidence UX Rules

- Confidence must be displayed beside the recommendation.
- Low confidence cannot produce an unqualified Accept recommendation.
- The cause of Medium or Low confidence must be stated.
- Confidence must not be portrayed as statistical probability unless technically validated.

---

## 11. Trust Design

### 11.1 Fact / Inference / Verification Labels

Use consistent labels:

- **Provided Fact** - entered by the creator or present in the pitch
- **AI Inference** - DealFit interpretation
- **Rule Trigger** - deterministic product rule
- **External Verification Required** - not verified by the MVP

### 11.2 Explanation Style

Explanations should be:

- concise;
- specific to the pitch;
- linked to provided facts or configured rules;
- free from unsupported certainty;
- written in business language.

### 11.3 No Hidden Automation

The interface should never imply that DealFit has contacted the brand, accepted a contract, altered terms, or performed external research unless that action actually occurred.

### 11.4 Product Disclaimer

Display near the result or decision area:

> “DealFit provides AI-assisted screening and does not provide legal, financial, contractual, or reputation-verification services. Review important terms and external information before acting.”

### 11.5 Creator Control

The creator can:

- edit the profile;
- correct extracted facts;
- rerun the assessment;
- override the recommendation;
- request further information;
- choose manual review.

---

## 12. Accessibility and Inclusive Design

The MVP should:

- use descriptive labels, not color alone;
- provide sufficient contrast;
- support keyboard navigation where technically feasible;
- use readable text sizes;
- avoid unexplained technical terminology;
- provide error messages next to relevant fields;
- use a logical heading order;
- avoid animations that distract from decision content;
- ensure recommendation and confidence states are understandable without relying on icons alone.

---

## 13. Responsive Design

The interface should support desktop and mobile-width layouts.

### Desktop

- Profile and pitch input may use two-column sections.
- Analysis can show a summary column and detailed evidence column.

### Mobile

- Use a single-column flow.
- Keep recommendation, confidence, and major risks at the top.
- Avoid horizontal tables.
- Make final decision controls easy to tap.

---

## 14. Prototype Navigation

Recommended navigation:

1. **Profile**
2. **New Deal**
3. **Analysis**
4. **Decision / History**
5. **About the Prototype**

For the MVP, these may be represented as steps in one page rather than separate routed pages.

---

## 15. Prototype Demonstration Scenarios

The interface should support loading synthetic scenarios that demonstrate different UX states.

Minimum scenarios:

1. Strong fit with complete terms - Accept
2. Strong fit but low compensation - Negotiate
3. Excluded category - Hard Conflict / Decline
4. Missing compensation - Need More Information
5. Broad paid-media usage rights - Negotiate or Manual Review
6. Unclear exclusivity - Manual Review
7. Weak audience fit - Decline
8. Attractive but materially incomplete offer - Manual Review
9. Existing partnership conflict - Decline or Manual Review
10. Mixed fit with creator override - Override flow

All scenarios must be clearly labelled as synthetic.

---

## 16. UX Success Measures

The UX should be assessed using:

- median time to submit and screen a pitch;
- percentage of users who can identify why the recommendation was made;
- percentage of users who correctly identify missing information;
- percentage of users who recognize unverified information;
- time required to record a final decision;
- recommendation agreement and informed override rates;
- perceived usefulness;
- perceived control;
- frequency of accidental over-reliance indicators.

Quantitative definitions and pilot launch gates will be maintained in:

`Appendix/Metrics/Metrics_and_Launch_Gates.md`

---

## 17. Traceability to PRD

| UX Component | PRD Link |
|---|---|
| Creator Profile | FR-01, AC-01 |
| Pitch Input | FR-02, FR-03 |
| Missing Information | FR-04, AC-03, AC-08 |
| Hard Rules | FR-05, AC-02 |
| AI Fit Assessment | FR-06, AIR-01 to AIR-07 |
| Recommendation | FR-07 |
| Score | FR-08 |
| Confidence | FR-09, TSR-02 |
| Explanation | FR-10, AC-04 |
| Risk Flags | FR-11, AC-05 |
| Human Decision | FR-12, TSR-01 |
| Override | FR-13, AC-06 |
| Decision Record | FR-14 |
| Fact / Inference Separation | AIR-03, AC-07 |
| Disclaimer | TSR-07 |

---

## 18. Wireframe Deliverables

Detailed wireframes will be maintained in:

`Appendix/Wireframes/Wireframes.md`

The required wireframes are:

1. Creator Profile
2. New Partnership / Pitch Input
3. DealFit Analysis
4. Creator Decision and Override
5. Missing Information / Low-Confidence State
6. Hard-Conflict State

The final prototype implementation and any UX deviations will be documented in:

`09_Prototype_MVP.md`

