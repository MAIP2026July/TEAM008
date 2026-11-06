# DealFit - Data Model and Output Schema

## 1. Purpose

This artifact defines the concrete information structures used by the DealFit classroom MVP and the logical data model that would support a future hosted pilot.

It complements `05_Data_Model_Evaluation.md`, which defines the broader scoring, rules, confidence and evaluation strategy.

The schema preserves DealFit's product principle:

> **AI recommends. The creator decides.**

---

## 2. Logical Data Model

```text
Creator Profile
      |
      | 1
      |
      |------ N Sponsorship Pitches
                        |
                        | 1
                        |
                        v
                  DealFit Analysis
                        |
                        | 1
                        |
                        v
                  Creator Decision
```

A creator profile may be reused across multiple sponsorship pitches. Each screening run produces one analysis record. Each completed analysis may then receive one final creator decision.

The classroom MVP keeps these structures in browser-session state. The relationships below describe the logical model, not a deployed production database.

---

## 3. Entity A - Creator Profile

### Purpose

Store reusable creator context, preferences, commercial boundaries and partnership constraints used during pitch screening.

### Proposed Schema

| Field | Type | Required | Example | Purpose |
|---|---|---|---|---|
| `creator_profile_id` | String / UUID | Future hosted version | `cp_001` | Unique profile identifier |
| `profile_name` | String | Yes | `Maya - Lifestyle Creator` | Human-readable profile label |
| `primary_niche` | String | Yes | `Lifestyle & Wellness` | Primary creator domain |
| `content_themes` | Array/String | Recommended | `Wellness, routines, travel` | Additional fit context |
| `follower_range` | Enum/String | No | `50K-100K` | Descriptive creator scale |
| `audience_characteristics` | String | Recommended | `Urban, 18-34, wellness interested` | Audience relevance context |
| `preferred_categories` | Array | No | `Wellness, travel, beauty` | Positive creator preferences |
| `excluded_categories` | Array | No | `Gambling, tobacco, payday loans` | Deterministic creator boundaries |
| `values_boundaries` | String/Array | No | `No misleading health claims` | Values-alignment context |
| `minimum_compensation_inr` | Number | No | `25000` | Creator-defined commercial preference |
| `typical_content_formats` | Array/String | No | `Short video, Stories` | Campaign-feasibility context |
| `previous_partnership_notes` | String | No | `Existing 3-month exclusivity with a skincare brand` | Potential conflict context |
| `created_at` | Datetime | Future hosted version | TBD | Audit field |
| `updated_at` | Datetime | Future hosted version | TBD | Profile-staleness / audit field |

### Validation Rules

- `profile_name` must not be empty.
- `primary_niche` must not be empty.
- `minimum_compensation_inr`, when supplied, must be non-negative.
- A category should not silently exist in both `preferred_categories` and `excluded_categories`.
- Optional fields remain optional; users should not invent data to satisfy the form.

### Sensitivity

Treat the following as sensitive commercial/profile information:

- compensation preference;
- audience information;
- prior partnership notes;
- exclusions and boundaries.

---

## 4. Entity B - Sponsorship Pitch

### Purpose

Store the original inbound pitch and the structured deal information used for screening.

### Proposed Schema

| Field | Type | Required | Example | Purpose |
|---|---|---|---|---|
| `pitch_id` | String / UUID | Future hosted version | `pitch_001` | Unique pitch identifier |
| `creator_profile_id` | Foreign key | Future hosted version | `cp_001` | Creator being evaluated |
| `brand_name` | String | Yes | `WellSpring Nutrition` | Brand reference |
| `brand_category` | String | Recommended | `Wellness` | Category-fit / exclusion checks |
| `original_pitch_text` | Text | Yes | Campaign email/brief text | Preserve source input |
| `proposed_compensation_inr` | Number / Null | Critical when known | `35000` | Commercial assessment |
| `deliverables` | String/Array / Null | Critical when known | `2 short videos + 3 stories` | Workload / feasibility |
| `campaign_timeline` | String / Null | Recommended | `3 weeks` | Feasibility / missing-info check |
| `usage_rights` | String / Null | Critical when known | `Perpetual worldwide paid media` | Commercial / contractual risk |
| `exclusivity_terms` | String / Null | Recommended | `None` | Conflict / clarification check |
| `target_audience` | String / Null | No | `Urban wellness audience` | Audience relevance |
| `payment_terms` | String / Null | Recommended | `45 days` | Commercial completeness |
| `approval_requirements` | String / Null | No | `Brand review before publishing` | Workflow burden |
| `additional_creator_notes` | Text | No | Creator-only context | Human/contextual evidence |
| `synthetic_scenario_id` | String / Null | Demo only | `S05` | Evaluation traceability |
| `created_at` | Datetime | Future hosted version | TBD | Audit field |

### Missing-Value Representation

The product should distinguish:

- field intentionally supplied with value;
- field genuinely missing;
- field explicitly marked `Not Provided`.

An empty field or `Not Provided` must not be converted into a negative factual claim.

---

## 5. Entity C - DealFit Analysis

### Purpose

Store the product's structured screening result for one pitch/profile combination.

### Proposed Schema

| Field | Type | Required | Example |
|---|---|---|---|
| `analysis_id` | String / UUID | Future hosted version | `ana_001` |
| `pitch_id` | Foreign key | Future hosted version | `pitch_001` |
| `provided_facts` | Array<Object/String> | Yes | Brand, compensation, usage rights |
| `ai_inferences` | Array<String> | Yes where applicable | `Strong apparent niche alignment` |
| `rule_triggers` | Array<Object> | Yes / may be empty | Creator-excluded category |
| `creator_niche_fit_score` | Integer 0-100 | Yes | `85` |
| `audience_relevance_score` | Integer 0-100 | Yes | `40` |
| `commercial_attractiveness_score` | Integer 0-100 | Yes | `85` |
| `campaign_feasibility_score` | Integer 0-100 | Yes | `70` |
| `values_preference_alignment_score` | Integer 0-100 | Yes | `70` |
| `risk_information_completeness_score` | Integer 0-100 | Yes | `100` |
| `dealfit_score` | Integer 0-100 | Yes | `74` |
| `recommendation` | Enum | Yes | `Negotiate` |
| `confidence` | Enum | Yes | `High` |
| `risk_flags` | Array<RiskFlag> | Yes / may be empty | Broad paid-media rights |
| `missing_information` | Array<String> | Yes / may be empty | `Payment terms` |
| `external_verification_required` | Array<String> | Yes / may be empty | `Brand reputation not verified` |
| `reason_summary` | Array<String> | Yes | Concise supporting reasons |
| `recommended_next_action` | String | Yes | `Negotiate the flagged terms...` |
| `rule_version` | String | Future hosted version | `v2` |
| `analysis_timestamp` | Datetime | Future hosted version | TBD |

---

## 6. Recommendation Enum

The product-level recommendation should be one of:

```text
Accept
Negotiate
Decline
Manual Review / Need More Information
```

The creator's final action is tracked separately and may use five choices:

```text
Accept
Negotiate
Decline
Need More Information
Manual Review
```

This separation allows DealFit to express a guarded combined state while allowing the creator to record a more precise human action.

---

## 7. Confidence Enum

```text
High
Medium
Low
```

### Interpretation

Confidence represents the quality, completeness and clarity of the available evidence in the prototype.

Confidence is **not**:

- a probability that the recommendation is correct;
- a probability of campaign success;
- a measure of risk severity.

### Current Prototype Rule

- Critical missing information or contradiction can force `Low`.
- Non-critical ambiguity, unclear exclusivity or values concern can produce `Medium`.
- Complete, internally consistent evidence can produce `High`.

A High-risk deterministic creator exclusion can still have High confidence when the evidence is explicit.

---

## 8. Risk Flag Schema

A risk flag logically contains:

```json
{
  "risk_type": "usage_rights",
  "severity": "Medium",
  "message": "Broad paid-media or usage rights",
  "evidence_type": "Provided Fact / Rule Trigger / AI Inference"
}
```

### Severity Enum

```text
High
Medium
Low
```

### Example Risk Types

- `category_conflict`
- `existing_partnership_conflict`
- `compensation_below_creator_minimum`
- `broad_usage_rights`
- `unclear_exclusivity`
- `payment_terms_missing`
- `high_deliverable_burden`
- `contradictory_terms`
- `materially_incomplete_offer`
- `values_alignment_concern`
- `weak_niche_fit`
- `weak_audience_relevance`

The classroom MVP does not persist a normalized `risk_type`; this is the recommended logical schema for future implementation.

---

## 9. Fact / Inference / Verification Model

Every user-facing assessment should conceptually classify information into the following types.

### Provided Fact

Directly entered by the creator or present in the supplied pitch.

Examples:

- compensation = INR 35,000;
- usage rights = perpetual worldwide paid media;
- category = Wellness.

### Rule Trigger

A deterministic product rule activated by provided data.

Example:

- creator excludes Gambling;
- new pitch category is Gambling;
- rule trigger = creator-defined excluded category.

### AI Inference

A DealFit interpretation based on the supplied context.

Example:

- `Strong apparent niche alignment`.

### External Verification Required

Information the MVP does not verify.

Examples:

- brand reputation;
- market-rate comparison;
- contract enforceability.

This separation is required to prevent users from treating interpretation or missing external evidence as verified fact.

---

## 10. Entity D - Creator Decision

### Purpose

Store the final human action independently from DealFit's recommendation.

### Proposed Schema

| Field | Type | Required | Example |
|---|---|---|---|
| `decision_id` | String / UUID | Future hosted version | `dec_001` |
| `analysis_id` | Foreign key | Future hosted version | `ana_001` |
| `creator_final_decision` | Enum | Yes | `Negotiate` |
| `is_override` | Boolean | Yes | `true` |
| `override_reason` | String / Enum / Null | No | `Personal relationship or context` |
| `override_notes` | Text / Null | No | `Creator has additional context unavailable to DealFit.` |
| `decision_timestamp` | Datetime | Future hosted version | TBD |

### Override Rule

`is_override = true` when the creator final decision materially differs from the DealFit recommendation.

For the combined DealFit state `Manual Review / Need More Information`, either human action below may be treated as aligned rather than an override:

- `Manual Review`
- `Need More Information`

---

## 11. Suggested Override Reason Enum

```text
Personal relationship or context
Existing partnership conflict
Commercial context unavailable to DealFit
Audience context unavailable to DealFit
Contract concern
Known brand information
Recommendation reasoning was not persuasive
Other
```

Override reasons are evaluation evidence. They must not automatically become model-training labels.

---

## 12. Structured Output Contract

A future AI-assisted implementation should return a structured object comparable to:

```json
{
  "provided_facts": [
    {
      "field": "brand_category",
      "value": "Wellness"
    },
    {
      "field": "compensation_inr",
      "value": 35000
    }
  ],
  "ai_inferences": [
    "Strong apparent niche alignment"
  ],
  "rule_triggers": [],
  "dimension_assessments": {
    "creator_niche_fit": 85,
    "audience_relevance": 40,
    "commercial_attractiveness": 85,
    "campaign_feasibility": 70,
    "values_preference_alignment": 70,
    "risk_information_completeness": 100
  },
  "dealfit_score": 74,
  "recommendation": "Negotiate",
  "confidence": "High",
  "risk_flags": [
    {
      "severity": "Medium",
      "risk_type": "broad_usage_rights",
      "message": "Broad paid-media or usage rights"
    }
  ],
  "missing_information": [],
  "external_verification_required": [
    "Brand reputation not verified",
    "Market-rate comparison unavailable",
    "Contract enforceability not assessed"
  ],
  "reason_summary": [
    "Strong apparent niche alignment",
    "Compensation meets the creator-defined minimum"
  ],
  "recommended_next_action": "Negotiate the flagged commercial or contractual terms before accepting."
}
```

The JSON above is a conceptual contract using the S05-style output. It is not evidence of a live LLM response.

---

## 13. Prototype vs Future Hosted Storage

### Classroom MVP

Storage characteristics:

- browser-session state;
- no production database;
- no user authentication;
- no cloud persistence;
- no third-party model transmission.

### Private Alpha / Pilot

A hosted version would require:

- authenticated user identity;
- creator-profile persistence;
- pitch/deal persistence;
- analysis-version persistence;
- creator decision / override audit record;
- encryption in transit and at rest;
- retention/deletion policy;
- access-control policy;
- separation of synthetic/test and real user data.

---

## 14. Data Retention Principles

The classroom prototype does not define production retention periods.

Before a real pilot, the product must define:

- how long pitch text is retained;
- how long creator profiles are retained;
- whether decision history can be deleted/exported;
- whether model/API providers retain request content;
- whether audit data is retained separately;
- what happens after account deletion.

No production retention value should be invented before privacy/security review.

---

## 15. Data Quality Controls

Recommended controls:

- preserve original pitch text;
- allow correction of structured/extracted facts;
- treat missing data as missing rather than negative evidence;
- detect contradictory terms;
- prevent negative compensation values;
- warn about conflicting preferred/excluded categories;
- record rule/model/configuration version in future hosted analyses;
- preserve final human decision independently from the recommendation.

---

## 16. Data Not Required for MVP

DealFit should not request or store without a validated need:

- passwords entered into DealFit content fields;
- payment-card numbers;
- government identity numbers;
- creator banking details;
- unrelated private messages;
- protected/sensitive personal attributes inferred by the product;
- unnecessary follower-level personal data.

---

## 17. Hard-Coded vs Configurable Data Logic

| Item | Classroom MVP State |
|---|---|
| Creator profile values | Configurable |
| Excluded categories | Configurable |
| Minimum compensation | Configurable |
| Pitch inputs | Per deal |
| Final creator decision | Human-controlled |
| Synthetic scenarios | Hard-coded |
| Screening dimensions | Hard-coded |
| Dimension weights | Hard-coded defaults |
| Critical-field policy | Hard-coded |
| Domain taxonomy | Hard-coded simplified mapping |
| Risk severity mapping | Hard-coded |
| Confidence logic | Hard-coded |
| Recommendation precedence | Hard-coded safety logic |

These implementation choices are documented prototype assumptions and should not be mistaken for validated market rules.

---

## 18. Traceability

This schema supports:

- `../../05_Data_Model_Evaluation.md`
- `../PRD/PRD.md`
- `../../04_UX_Workflow_Trust.md`
- `../Wireframes/Wireframes.md`
- `../Metrics/Metrics_and_Launch_Gates.md`
- `../../09_Prototype_MVP.md`
- `../../Prototype/DealFit_Prototype.html`

The broader privacy, governance and risk requirements are documented in:

- `../../07_Ethics_Governance_Risk.md`
- `../Risk_Note/Risk_Note.md`

