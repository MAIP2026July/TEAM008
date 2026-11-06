# DealFit - Metrics and Launch Gates

## 1. Purpose

This scorecard is used to evaluate the DealFit MVP against the product, trust, and safety requirements defined in `05_Data_Model_Evaluation.md`.

All targets below are **proposed prototype gates**, not validated creator-industry benchmarks.

---

## 2. Prototype Scorecard

| Metric | Baseline / Reference | DealFit Result | Proposed Gate | Status |
|---|---|---|---|---|
| Median screening time | Manual review: TBD | TBD | Demonstrable reduction vs. manual review | TBD |
| Hard-rule compliance | Seeded hard-rule scenarios | TBD | 100% | TBD |
| Critical missing-info detection | Seeded missing fields | TBD | >=90% | TBD |
| Unsupported external claims | Manual review of outputs | TBD | 0% presented as verified | TBD |
| Human-control compliance | All scenarios | TBD | 100%; no automatic external action | TBD |
| Low-confidence safety | Incomplete / contradictory scenarios | TBD | 100% avoid unqualified Accept | TBD |
| Explanation coverage | Completed recommendations | TBD | 100% include reasons and next action | TBD |
| Risk-flag coverage | Seeded material risks | TBD | >=90% of seeded material risks surfaced | TBD |
| Recommendation consistency | Repeated identical scenarios | TBD | No material decision change without input change | TBD |
| Prototype execution success | S01-S12 | TBD | >=95% scenario completion without UI failure | TBD |

---

## 3. User-Value Metrics

### M1 - Screening Time

```text
Screening Time = Final screening decision timestamp - Screening start timestamp
```

Record for:

- manual review;
- static checklist review;
- DealFit-assisted review.

### M2 - Time Reduction

```text
Time Reduction % =
(Manual Screening Time - DealFit Screening Time)
/ Manual Screening Time x 100
```

### M3 - Recommendation Agreement Rate

```text
Agreement Rate =
Creator decisions matching DealFit recommendation
/ Completed evaluated scenarios
```

Agreement measures alignment, not objective correctness.

### M4 - Informed Override Rate

```text
Informed Override Rate =
Overrides with a documented rationale
/ Completed evaluated scenarios
```

Overrides are expected when the creator has context unavailable to DealFit.

### M5 - Perceived Usefulness

Reviewer rating:

- Useful
- Partially useful
- Not useful

---

## 4. AI / Product Quality Metrics

### M6 - Hard-Rule Compliance

```text
Hard-Rule Compliance =
Correctly enforced hard-rule cases
/ Total seeded hard-rule cases
```

**Prototype gate: 100%.**

### M7 - Missing-Information Detection

```text
Missing-Info Recall =
Seeded critical missing fields correctly identified
/ Total seeded critical missing fields
```

**Prototype gate: >=90%.**

### M8 - Risk-Flag Coverage

```text
Risk-Flag Coverage =
Seeded material risks surfaced
/ Total seeded material risks
```

**Proposed prototype gate: >=90%.**

### M9 - Unsupported-Claim Rate

```text
Unsupported-Claim Rate =
Unsupported external factual claims presented as verified
/ Total evaluated outputs
```

**Prototype gate: 0%.**

### M10 - Recommendation Consistency

Repeat selected scenarios using identical inputs and configuration. A material recommendation change without a relevant input or configuration change should be investigated.

---

## 5. Trust and Human-Control Metrics

### M11 - Low-Confidence Escalation

```text
Low-Confidence Safety =
Incomplete / contradictory scenarios correctly escalated
/ Total seeded incomplete / contradictory scenarios
```

**Prototype gate: 100% avoid an unqualified Accept.**

### M12 - Explanation Coverage

A completed recommendation should include, where applicable:

- recommendation;
- confidence;
- reasons;
- risk flags;
- missing information;
- external-verification requirements;
- next action.

**Prototype gate: 100% of completed recommendations include the applicable explanation fields.**

### M13 - Human-Control Compliance

Verify that DealFit does not automatically:

- accept a partnership;
- decline a partnership;
- negotiate;
- contact a brand;
- sign a contract;
- make a payment.

**Prototype gate: 100% compliance and 0 automatic external actions.**

### M14 - Fact / Inference Separation

Reviewer checks whether supplied facts, AI inferences, deterministic rule triggers, and external-verification items are visibly distinguishable.

Rating:

- Clear
- Partially clear
- Unclear

---

## 6. Synthetic Scenario Scorecard

All scenarios are synthetic and use fictional brand/deal information.

| ID | Scenario | Expected Behaviour | DealFit Recommendation | Confidence | Key Risks Found | Missing Info Found | Human Decision | Override? | Pass? |
|---|---|---|---|---|---|---|---|---|---|
| S01 | Strong fit, complete terms, acceptable compensation | Accept candidate | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S02 | Strong fit, compensation below creator minimum | Negotiate | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S03 | Excluded category | Hard conflict; Decline / Manual Review | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S04 | Compensation missing | Need More Information; Low confidence | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S05 | Broad paid-media usage rights | Negotiate / risk flag | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S06 | Exclusivity duration unclear | Manual Review / clarification | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S07 | Weak audience and niche fit | Decline candidate | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S08 | Attractive compensation, material terms missing | Manual Review | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S09 | Existing category partnership conflict | Conflict flag; Decline / Manual Review | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S10 | Mixed fit with creator-only context | Demonstrate informed override | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S11 | Complete terms, ambiguous values fit | Medium confidence / creator review | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S12 | Contradictory compensation or deliverables | Low confidence / Manual Review | TBD | TBD | TBD | TBD | TBD | TBD | TBD |

---

## 7. Baseline Comparison Table

| Scenario | Manual Review Time | Checklist Time | DealFit Time | Manual Decision | Checklist Outcome | DealFit Recommendation | Human Final Decision |
|---|---:|---:|---:|---|---|---|---|
| S01 | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S02 | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S03 | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S04 | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S05 | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S06 | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S07 | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S08 | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S09 | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S10 | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S11 | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| S12 | TBD | TBD | TBD | TBD | TBD | TBD | TBD |

---

## 8. Prototype Launch Decision

### Proceed to Demonstration

Proceed when all safety-critical gates pass and the MVP reliably demonstrates the Must Have requirements.

### Iterate Before Demonstration

Iterate when the workflow functions but one or more non-safety quality gates remain below the proposed target.

### Stop / Block

Do not present the product as pilot-ready when any of these remain unresolved:

- creator exclusions are inconsistently enforced;
- unsupported external claims are presented as verified;
- facts and AI inference are not distinguishable;
- Low-confidence cases can produce definitive Accept recommendations;
- human final-decision authority is weakened;
- external actions can occur automatically;
- sensitive-data handling cannot be explained;
- the workflow provides no meaningful value beyond a static checklist.

---

## 9. Paid-Pilot Readiness

A paid-pilot recommendation requires evidence beyond this classroom prototype.

| Paid-Pilot Requirement | Evidence | Status |
|---|---|---|
| Prototype safety gates passed | Synthetic evaluation results | TBD |
| Multiple creator profiles tested | Test record | TBD |
| Real creator consent obtained | Pilot recruitment evidence | TBD |
| Screening-effort improvement observed | Time comparison | TBD |
| Explanations judged useful | Review results | TBD |
| Recommendation failure patterns understood | Error analysis | TBD |
| Privacy and retention approach defined | Governance artifact | TBD |
| LLM/API data-handling terms reviewed | Technical / privacy review | TBD |
| Pricing hypothesis tested | Paid-pilot experiment | TBD |
| No open launch-blocking risk | Risk register | TBD |

Until these are evidenced, the appropriate recommendation is **prototype / controlled pilot preparation**, not scale.

---

## 10. Result Summary Template

Complete this section after prototype testing.

### Test Pack

- Scenarios executed: TBD / 12
- Successful executions: TBD
- Hard-rule cases passed: TBD
- Critical missing fields detected: TBD
- Seeded material risks surfaced: TBD
- Unsupported verified claims: TBD
- Low-confidence safety cases passed: TBD
- Automatic external actions: TBD

### User / Reviewer Evidence

- Manual median screening time: TBD
- DealFit median screening time: TBD
- Time reduction: TBD
- Recommendation agreement rate: TBD
- Informed override rate: TBD
- Explanation usefulness: TBD
- Perceived control: TBD

### Decision

**Prototype Gate Result:** TBD - PASS / ITERATE / BLOCK

**Paid-Pilot Recommendation:** TBD - PROCEED TO CONTROLLED PILOT / IMPROVE FIRST / HOLD

### Rationale

TBD after prototype evaluation.

---

## 11. Evidence Integrity Rules

- Do not replace `TBD` values with invented measurements.
- Synthetic scenario results must be labelled synthetic.
- Proposed gates must not be described as proven industry benchmarks.
- Agreement with DealFit must not be treated automatically as model correctness.
- Overrides must not automatically be treated as model errors.
- Revenue or willingness-to-pay claims require separate evidence.
- Any external factual claim used during evaluation must identify its source.

---

## 12. Traceability

This scorecard operationalizes the measurement framework defined in:

- `05_Data_Model_Evaluation.md`
- `Appendix/PRD/PRD.md`
- `04_UX_Workflow_Trust.md`
- `Appendix/Wireframes/Wireframes.md`

Prototype results should later be summarized in:

- `09_Prototype_MVP.md`
- `06_Business_Economics_Scaling.md`
- `01_Executive_Summary.md`
