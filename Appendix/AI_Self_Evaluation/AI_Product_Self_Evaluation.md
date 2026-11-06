# DealFit - AI Product Self-Evaluation

## 1. Purpose

This document records the required AI self-evaluation of the DealFit MVP after the PM artifacts were used to build the first functional prototype.

The evaluation specifically asks:

1. What product did the AI build from the PM artifacts?
2. What was ambiguous or assumed?
3. What was hard-coded versus configurable?
4. What failed during structured testing?
5. What human-directed changes were made?
6. What limitations remain before a real pilot?

> **Product principle: AI recommends. The creator decides.**

---

## 2. Artifacts Used as Build Inputs

The prototype was built from the following product artifacts:

- `02_Product_Strategy.md`
- `Appendix/PRD/PRD.md`
- `Appendix/Workflows/Current_State_Workflow.puml`
- `Appendix/Workflows/DealFit_Future_Workflow.puml`
- `04_UX_Workflow_Trust.md`
- `Appendix/Wireframes/Wireframes.md`
- `05_Data_Model_Evaluation.md`
- `Appendix/Metrics/Metrics_and_Launch_Gates.md`

These artifacts defined the target user, product scope, deterministic rules, AI role, human-in-the-loop design, recommendation states, trust requirements, synthetic scenarios, and launch gates.

---

## 3. AI Build Request

The effective product-build instruction was:

> **Using the DealFit Product Strategy, PRD, workflows, UX/trust specification, wireframes, data/model strategy and evaluation framework as the source of truth, build a functional browser MVP. Implement the Must Have requirements, keep final partnership decisions human-controlled, use synthetic scenarios for demonstration, and do not silently invent external reputation or market-rate facts. Document assumptions and hard-coded logic.**

The resulting prototype was implemented as a self-contained browser application:

`Prototype/DealFit_Prototype.html`

The classroom MVP uses deterministic rules and local AI-style scoring/interpretation logic. It does not call an external LLM or perform live web/reputation research.

---

## 4. What the AI Built

The first implementation provided:

- persistent creator-profile configuration during the browser session;
- sponsorship pitch input;
- 12 synthetic test scenarios;
- missing-information detection;
- creator-exclusion rules;
- creator minimum-compensation checks;
- simple niche/audience scoring;
- usage-rights and exclusivity risk flags;
- a 0-100 DealFit score;
- Accept / Negotiate / Decline / Manual Review recommendations;
- High / Medium / Low confidence;
- Provided Facts and AI Inferences sections;
- External Verification Required labels;
- five separate creator final-decision actions;
- override detection and optional reason capture;
- session-level decision history;
- explicit prevention of automatic external action.

---

## 5. What Was Hard-Coded vs Configurable

| Component | V1 / V2 implementation | Classification | Self-evaluation |
|---|---|---|---|
| Creator profile | User-editable form | Configurable | Appropriate for MVP |
| Excluded categories | Creator-entered | Configurable | Appropriate; creator boundary preserved |
| Minimum compensation | Creator-entered | Configurable | Appropriate; not presented as market benchmark |
| Pitch terms | Per-deal inputs | Configurable | Appropriate |
| Synthetic test scenarios | Embedded S01-S12 | Hard-coded demo data | Appropriate for evaluation; not production data |
| Screening dimensions | Six fixed dimensions | Hard-coded | Acceptable prototype assumption; requires validation |
| Dimension weights | 25/20/20/15/10/10 | Hard-coded defaults | Should become configuration before broader use |
| Recommendation precedence | Rule logic in JavaScript | Hard-coded safety logic | Appropriate to document and test explicitly |
| Risk severity mapping | Rule logic | Hard-coded | Requires validation before pilot |
| Critical missing fields | Rule logic | Hard-coded | Revised after V1 testing |
| Confidence calculation | Rule logic | Hard-coded | Revised after V1 testing |
| Niche/audience domain map | JavaScript category groups | Hard-coded | Known limitation; should become richer/configurable |
| Values-sensitive phrases | Keyword list | Hard-coded | Useful for demonstration only |
| External reputation | Not implemented | Not available | Correctly labelled unverified |
| Market-rate benchmarking | Not implemented | Not available | Correctly labelled unavailable |
| Final creator decision | User-selected | Human-controlled | Required and retained |

---

## 6. Version 1 Structured Evaluation

The initial AI-built prototype was tested against all 12 synthetic scenarios defined in the evaluation pack.

### 6.1 V1 Primary Results

| Scenario | Intended behavior | V1 behavior | Evaluation |
|---|---|---|---|
| S01 Strong fit | Accept | Accept / High / 75 | PASS |
| S02 Low compensation | Negotiate | Negotiate / High / 65 | PASS |
| S03 Excluded category | Decline / hard conflict | Decline / Low / 53 | PASS, confidence issue noted |
| S04 Compensation missing | Need More Information / Low | Negotiate / Medium / 59 | FAIL |
| S05 Broad paid-media rights | Negotiate | Negotiate / High / 75 | PASS |
| S06 Unclear exclusivity | Manual Review / clarification | Decline / Low / 75 | FAIL |
| S07 Weak niche/audience fit | Decline | Accept / High / 75 | FAIL |
| S08 Attractive but incomplete | Manual Review / Low | Manual Review / Low / 65 | PASS |
| S09 Existing partnership conflict | Decline / conflict | Decline / Low / 75 | PASS |
| S10 Creator-only context | Demonstrate override | Accept / High / 75; creator overrode to Negotiate | PASS |
| S11 Ambiguous values fit | Cautious review | Negotiate / High / 71 | FAIL |
| S12 Contradictory terms | Manual Review / Low | Manual Review / Low / 64 | PASS |

V1 passed the intended primary behavior in **8 of 12 scenarios (66.7%)**. This is retained as development evidence and is not presented as a production-quality metric.

---

## 7. Problems Identified in V1

### L1 - Audience-Relevance Heuristic Was Too Crude

Several apparently aligned cases repeatedly received an audience score around 45 because the prototype relied on simple textual/domain overlap.

**Impact:** The dimension score could understate seemingly relevant audiences and was not sufficiently semantic.

**Decision:** Improve the domain comparison for V2, but retain audience-scoring sophistication as a known limitation because the prototype has no trained semantic model or validated audience taxonomy.

### L2 - Confidence Mixed Risk Severity with Evidence Certainty

S03 contained an unambiguous creator exclusion. V1 correctly recommended Decline but lowered confidence simply because a High-risk flag existed.

**Impact:** The interface could imply uncertainty about a rule that was actually deterministic.

**Change:** In V2, confidence represents evidence quality/completeness rather than risk severity. S03 became Decline / High confidence.

### L3 - Critical Missing Information Had Insufficient Precedence

S04 omitted compensation and payment terms. V1 detected the missing fields but returned Negotiate / Medium confidence.

**Impact:** A creator could be pushed toward negotiation without enough information to assess commercial attractiveness.

**Change:** V2 treats missing compensation, deliverables or usage rights as critical. S04 became Manual Review / Need More Information / Low confidence.

### L4 - Existing-Partnership Conflict Detection Was Too Broad

S06 incorrectly produced a High existing-partnership-conflict flag because broad beauty/skincare keyword logic interacted with Maya's skincare exclusivity note.

**Impact:** False conflict detection caused an excessive Decline recommendation.

**Change:** V2 requires explicit conflict evidence in creator notes. S06 became Manual Review / Medium for unclear exclusivity, while S09 retained genuine conflict detection.

### L5 - Niche Matching Was Vulnerable to Incidental Keywords

S07 described an enterprise-software campaign for enterprise IT buyers. V1 still produced niche fit 85 and Accept because the pitch included wording referring to a lifestyle creator.

**Impact:** Keyword overlap was mistaken for campaign fit.

**Change:** V2 compares the brand category and target audience against creator domains rather than relying on the entire pitch. S07 became Decline / High with niche fit 25.

### L6 - Low Values Alignment Did Not Become an Actionable Risk

S11 produced values/preference alignment of 35 but no visible risk and retained High confidence.

**Impact:** An important creator-boundary concern was hidden inside a dimension score.

**Change:** V2 propagates values-sensitive messaging into a visible Medium risk and reduces confidence. S11 became Manual Review / Medium.

---

## 8. Human-Directed V2 Changes

The human review of V1 instructed the following product changes:

1. Separate confidence from risk severity.
2. Define critical missing fields with decision precedence.
3. Require explicit evidence for strong partnership-conflict flags.
4. Replace broad pitch keyword matching with campaign-category / audience-domain comparison.
5. Propagate low values alignment into visible risk and guarded recommendations.
6. Preserve hard creator exclusions over commercial attractiveness.
7. Retain fact / inference / external-verification separation.
8. Retain human override and no-automatic-action rules.

The revised implementation was saved as the final classroom MVP:

`Prototype/DealFit_Prototype.html`

---

## 9. V2 Regression Evidence

Targeted regression testing focused on the changed behaviors plus a previously successful Accept case.

| Scenario | V1 | V2 | Regression outcome |
|---|---|---|---|
| S01 Strong fit | Accept / High / 75 | Accept / High / 74 | PASS; Accept path preserved |
| S03 Excluded category | Decline / Low / 53 | Decline / High / 48 | PASS; confidence semantics fixed |
| S04 Compensation missing | Negotiate / Medium / 59 | Manual Review / Low / 58 | PASS; critical missing-field precedence fixed |
| S06 Unclear exclusivity | Decline / Low / 75 | Manual Review / Medium / 74 | PASS; false conflict removed |
| S07 Weak niche/audience fit | Accept / High / 75 | Decline / High / 55 | PASS; niche mismatch corrected |
| S09 Existing conflict | Decline / Low / 75 | Decline / High / 74 | PASS; genuine conflict still detected |
| S11 Values ambiguity | Negotiate / High / 71 | Manual Review / Medium / 70 | PASS; values risk propagated |

All targeted behavioral corrections passed the V2 regression set.

---

## 10. Human-in-the-Loop Evidence

S10 was used to test human override behavior.

### DealFit output

- Recommendation: Accept
- Confidence: High
- Score: 75

### Human action

The creator selected **Negotiate** based on additional context unavailable to DealFit.

The prototype:

- displayed an override warning;
- allowed the reason `Personal relationship or context`;
- captured the note `Creator has additional context unavailable to DealFit.`;
- recorded the final decision as Negotiate;
- recorded `Override: Yes`;
- confirmed that no external action was taken.

This supports the intended product principle that override is a legitimate human-control mechanism rather than automatically a model failure.

---

## 11. Remaining Known Limitations

### KL1 - Audience Scoring Remains Simplified

The V2 audience matcher remains a hard-coded domain heuristic. For example, S01 remained a correct Accept outcome but audience relevance was still conservatively scored at 40.

**Pilot implication:** Replace or augment the heuristic with a validated audience taxonomy, creator-configurable audience priorities, or a grounded semantic-comparison method.

### KL2 - Scoring Weights Are Unvalidated

The 25/20/20/15/10/10 weights are design assumptions.

**Pilot implication:** Test sensitivity and allow creator configuration before using scores as a meaningful comparison between deals.

### KL3 - Confidence Is Rule-Based

High / Medium / Low confidence is determined by documented prototype logic, not probability calibration.

**Pilot implication:** Maintain the label as evidence-quality confidence and validate the rules with real users.

### KL4 - No Live LLM or External Grounding

The classroom MVP simulates AI-style reasoning locally and performs no live reputation, market-rate or legal research.

**Pilot implication:** If an LLM/API is added, re-evaluate privacy, structured-output reliability, cost, unsupported claims, prompt behavior and consistency.

### KL5 - Keyword-Based Values Detection

Values-sensitive terms are currently a small configured keyword set.

**Pilot implication:** Use creator-configurable values policies and richer semantic assessment, while preserving deterministic hard boundaries.

### KL6 - Synthetic Evaluation Only

The completed evidence comes from fictional scenarios rather than real creator decisions.

**Pilot implication:** Classroom testing supports prototype demonstration only. Real-user evidence is required before commercial claims.

---

## 12. Ambiguities Revealed by the Build

The build exposed several product questions that were not fully determined by the original PM artifacts:

1. Does confidence represent recommendation certainty, evidence completeness, or rule certainty?
2. Which missing fields are always critical versus context-dependent?
3. When should exclusivity create a hard conflict versus a clarification request?
4. How should related but non-identical creator and campaign audiences be compared?
5. Which creator-value concerns should force Manual Review?
6. Should dimension weights differ by creator or deal type?
7. How should past creator overrides affect future recommendations?
8. At what point does a recommendation require external data rather than AI inference?

The V2 implementation resolves only the minimum needed for a safe classroom demonstration. These questions remain validation topics for a real pilot.

---

## 13. What Should Become Configurable Before Pilot

Recommended configuration priorities:

### High Priority

- creator-excluded categories;
- creator minimum compensation;
- creator values / boundaries;
- creator audience priorities;
- existing partnership conflicts;
- scoring weights or relative importance;
- critical-field policy by deal type.

### Medium Priority

- risk severity mapping;
- Manual Review triggers;
- allowed usage-rights patterns;
- exclusivity tolerance;
- preferred content formats;
- explanation verbosity.

### Keep Centrally Controlled

- no automatic external action;
- fact / inference separation;
- unsupported external-claim safeguards;
- mandatory human review for defined high-impact states;
- audit/override capture requirements.

---

## 14. Changes Required Before a Real Paid Pilot

DealFit should not move directly from this classroom prototype to commercial use.

Before a paid pilot:

1. Test with multiple creator personas, not only Maya.
2. Conduct consented testing with real independent creators.
3. Replace or strengthen audience-fit and niche-fit heuristics.
4. Validate scoring dimensions and sensitivity to weights.
5. Define secure data storage, retention and deletion.
6. Review third-party LLM/API privacy terms if an external model is introduced.
7. Establish monitoring for unsupported claims and inconsistent recommendations.
8. Validate override and decision-history semantics with users.
9. Measure real screening-time change rather than assuming productivity benefit.
10. Test willingness to pay instead of assuming the proposed subscription range.
11. Review legal boundaries around contractual-term flagging.
12. Define escalation paths for high-risk or ambiguous deals.

---

## 15. Self-Evaluation Conclusion

The AI-generated V1 was useful because it rapidly converted the PM artifacts into a functioning product that could be tested. However, structured scenario testing showed that successful software execution was not the same as correct product behavior.

V1 handled straightforward creator exclusions, compensation negotiation, usage-rights risk, missing-information overload, contradictory terms and human override reasonably well. It also exposed brittle assumptions in audience matching, critical-field precedence, partnership-conflict detection, confidence semantics and values-risk propagation.

Human review converted those failures into explicit product requirements and produced V2. The targeted V2 regression set passed all intended behavioral corrections while preserving the core Accept path and genuine conflict detection.

The final classroom conclusion is therefore:

> **DealFit is suitable as a functional, human-in-the-loop prototype for demonstration and further controlled evaluation. It is not yet validated for autonomous decisions, production deployment, scale, or claims of creator business impact.**

The most important learning from the build is that AI product quality depends not only on generating plausible recommendations, but on defining evidence boundaries, deterministic safeguards, uncertainty, override mechanisms, evaluation scenarios and human accountability before deployment.

---

## 16. Traceability

This self-evaluation should be read together with:

- `02_Product_Strategy.md`
- `Appendix/PRD/PRD.md`
- `04_UX_Workflow_Trust.md`
- `05_Data_Model_Evaluation.md`
- `Appendix/Metrics/Metrics_and_Launch_Gates.md`
- `Prototype/DealFit_Prototype.html`

The AI build-and-revision process will also be summarized in:

`08_AI_Collaboration_Log.md`
