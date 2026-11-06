# DealFit - Functional Prototype / MVP

## 1. Prototype Objective

The DealFit MVP demonstrates the smallest credible product experience for screening an inbound creator-brand partnership.

The prototype is designed to test whether a hybrid workflow can convert creator preferences and sponsorship-pitch information into an explainable first-pass recommendation while preserving human decision authority.

> **Product principle: AI recommends. The creator decides.**

The prototype is a classroom demonstrator. It is not a production application, autonomous agent, legal reviewer, verified reputation service, or statistically validated predictor of sponsorship success.

---

## 2. Prototype Location

Final browser prototype:

`Prototype/DealFit_Prototype.html`

The application is self-contained and runs locally in a modern browser without a server, external API key, or network connection.

Prototype screenshots are stored under:

`Prototype/screenshots/`

---

## 3. How to Run the MVP

1. Download or clone the TEAM008 repository.
2. Open `Prototype/DealFit_Prototype.html` in a modern browser such as Microsoft Edge or Google Chrome.
3. Review or edit the default Maya creator profile.
4. Select **Save Creator Profile**.
5. Enter a partnership pitch or load one of the synthetic S01-S12 scenarios.
6. Select **Analyze with DealFit**.
7. Review the score, recommendation, confidence, reasons, risk flags, missing information, and verification requirements.
8. Select **Continue to Creator Decision**.
9. Record a final human decision.
10. If the human decision differs from DealFit, optionally record the override reason.

No external brand communication or irreversible action is executed by the prototype.

---

## 4. Prototype Architecture

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
    Local AI-Style Assessment Logic
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

The classroom build uses JavaScript rules and local scoring logic to simulate the AI-assisted product workflow described in the PM artifacts. It does not call a live LLM and does not perform external research.

---

## 5. Implemented MVP Features

### Creator Profile

The user can configure:

- profile name;
- follower range;
- primary niche;
- content formats;
- content themes;
- audience characteristics;
- preferred categories;
- excluded categories;
- creator values / boundaries;
- optional minimum compensation;
- previous partnership notes.

### Partnership Input

The user can enter:

- brand name;
- brand category;
- compensation;
- timeline;
- deliverables;
- usage rights;
- exclusivity;
- target audience;
- payment terms;
- original pitch;
- additional creator notes.

### DealFit Analysis

The product displays:

- DealFit score from 0-100;
- Accept / Negotiate / Decline / Manual Review / Need More Information recommendation;
- High / Medium / Low confidence;
- creator-review requirement;
- recommended next action;
- provided facts;
- AI-style inferences;
- risk flags with severity;
- missing information;
- external-verification requirements;
- six dimension-level scores;
- decision-support disclaimer.

### Human Decision / Override

The creator can choose:

- Accept;
- Negotiate;
- Decline;
- Need More Information;
- Manual Review.

If the creator chooses a different decision from DealFit, the product:

- displays an override warning;
- allows an optional reason;
- allows additional context notes;
- records the final creator decision;
- records whether an override occurred;
- updates the local session Decision History.

---

## 6. Synthetic Demonstration Scenarios

The MVP embeds twelve fictional scenarios.

| ID | Scenario | Intended Product Test |
|---|---|---|
| S01 | Strong fit, complete terms | Accept path |
| S02 | Strong fit, low compensation | Commercial negotiation |
| S03 | Excluded category | Deterministic creator boundary |
| S04 | Compensation missing | Critical missing information |
| S05 | Broad paid-media rights | Usage-rights risk |
| S06 | Unclear exclusivity | Clarification / manual review |
| S07 | Weak niche and audience fit | Poor-fit decline |
| S08 | High pay, materially incomplete terms | Avoid over-trusting attractive offer |
| S09 | Existing partnership conflict | Explicit conflict handling |
| S10 | Mixed fit with creator-only context | Human override |
| S11 | Ambiguous values alignment | Values-risk escalation |
| S12 | Contradictory terms | Contradiction / low-confidence review |

All built-in brands and deal terms are synthetic.

---

## 7. Version 1 Build and Evaluation

The first AI-generated implementation successfully produced a functioning end-to-end product, but structured testing exposed several product-logic weaknesses.

### V1 Primary Test Result

- Synthetic scenarios executed: **12 / 12**
- Primary expected behaviors passed: **8 / 12 (66.7%)**
- Primary failures: **S04, S06, S07, S11**

### V1 Issues Identified

- L1: Audience relevance heuristic was too crude.
- L2: Confidence mixed risk severity with evidence certainty.
- L3: Missing critical information had insufficient decision precedence.
- L4: Existing-partnership conflict detection was too broad.
- L5: Niche matching could be fooled by incidental keywords.
- L6: Low values alignment was not consistently propagated into visible risk and guarded recommendations.

The detailed diagnosis is documented in:

`Appendix/AI_Self_Evaluation/AI_Product_Self_Evaluation.md`

---

## 8. Human-Directed Version 2 Changes

Based on V1 evidence, Version 2 changed the product logic to:

1. separate confidence from risk severity;
2. treat compensation, deliverables and usage rights as critical missing fields;
3. require explicit evidence for strong existing-partnership conflict detection;
4. compare campaign category / target audience with creator domains rather than the entire pitch;
5. convert values-sensitive messaging into a visible risk and guarded recommendation;
6. preserve deterministic exclusions over high compensation or other positive signals.

The final classroom prototype in the repository is Version 2.

---

## 9. Version 2 Regression Evidence

| Scenario | Final V2 Evidence | Result |
|---|---|---|
| S01 | Accept / High / 74 | PASS - Accept path preserved |
| S03 | Decline / High / 48 | PASS - exclusion and confidence semantics corrected |
| S04 | Manual Review / Low / 58 | PASS - critical missing information corrected |
| S06 | Manual Review / Medium / 74 | PASS - false conflict removed, exclusivity clarification retained |
| S07 | Decline / High / 55 | PASS - weak niche fit corrected |
| S09 | Decline / High / 74 | PASS - genuine explicit conflict retained |
| S11 | Manual Review / Medium / 70 | PASS - values risk propagated |

All seven targeted V2 regression behaviors passed.

Scenarios that already behaved as intended in V1 were not all rerun in V2; the repository documentation preserves that evidence distinction.

---

## 10. Human-in-the-Loop Demonstration

S10 demonstrates that DealFit can be useful without owning the final decision.

### DealFit Recommendation

- Brand: EcoMove
- Recommendation: **Accept**
- Confidence: **High**
- Score: **75**

### Creator Decision

The creator intentionally selected **Negotiate** because additional relationship context was unavailable to DealFit.

The prototype:

- showed the override warning;
- captured `Personal relationship or context`;
- captured the note `Creator has additional context unavailable to DealFit.`;
- recorded `Creator Decision: Negotiate`;
- recorded `Override: Yes`;
- displayed the result in Decision History;
- executed no brand communication or external action.

This behavior is central to the product's trust model.

---

## 11. Trust and Guardrail Implementation

The final MVP demonstrates the following controls:

### Hard Creator Boundaries

An excluded category can override an attractive commercial offer. In S03, a high-paying gambling offer still resulted in Decline because Gambling was creator-excluded.

### Critical Missing Information

Missing critical commercial information now routes the user toward Manual Review / Need More Information rather than pretending the deal can be confidently assessed.

### Contradictory Information

The product does not choose between contradictory terms. S12 is escalated instead.

### Unsupported External Information

Analysis views explicitly display:

- Brand reputation not verified
- Market-rate comparison unavailable
- Contract enforceability not assessed

### Score Disclaimer

The 0-100 score is described as a screening indicator, not a probability of success.

### Human Final Authority

The product has no automatic Accept, Decline, negotiation, message, contract or payment action.

---

## 12. Hard-Coded vs Configurable Implementation

| Component | Final MVP State |
|---|---|
| Creator profile | Configurable |
| Preferred / excluded categories | Configurable |
| Minimum compensation | Configurable / optional |
| Deal fields | Per-deal input |
| Synthetic scenarios | Hard-coded demonstration set |
| Screening dimensions | Hard-coded |
| Dimension weights | Hard-coded prototype defaults |
| Critical-field definition | Hard-coded |
| Recommendation precedence | Hard-coded safety logic |
| Risk severity | Hard-coded |
| Domain taxonomy | Hard-coded simplified mapping |
| Values-sensitive phrases | Hard-coded small keyword set |
| Confidence logic | Hard-coded rule-based logic |
| Final creator decision | Human-controlled |

The hard-coded elements are visible product assumptions, not hidden claims of learned intelligence.

---

## 13. Known Limitations

### Simplified Audience-Relevance Logic

Audience matching remains a lightweight heuristic. S01 V2 produces the correct Accept recommendation but conservatively scores audience relevance at 40.

### Prototype Weights Are Unvalidated

The 25/20/20/15/10/10 weighting scheme is a design assumption.

### Rule-Based Confidence

Confidence represents evidence-quality rules, not probability calibration.

### No Live LLM

The final classroom build uses local JavaScript logic to demonstrate the intended AI workflow. A future LLM integration would require new evaluation of structured-output reliability, privacy, hallucination, latency and cost.

### No Live Reputation / Market / Legal Grounding

External reputation, market-rate and legal conclusions are explicitly outside the MVP.

### Single Design Persona

Testing concentrated on Maya, a fictional lifestyle/wellness design persona.

### Synthetic Scenario Evidence

No real creator user test, retention measurement, satisfaction study, productivity study or willingness-to-pay experiment has yet been conducted.

---

## 14. Required Screenshot Set

Store final screenshots under:

`Prototype/screenshots/`

Recommended final evidence set:

1. `01_Creator_Profile.png` - Maya default profile
2. `02_New_Deal.png` - populated synthetic pitch input
3. `03_Analysis_Negotiate.png` - S05 or S02 negotiated-deal state
4. `04_Decision_Override.png` - S10 override / Decision History state
5. `05_Missing_Information.png` - S04 V2 or S08 guarded state
6. `06_Hard_Conflict.png` - S03 V2 excluded-category state
7. `07_Weak_Fit_Decline.png` - S07 V2, optional but useful
8. `08_Values_Manual_Review.png` - S11 V2, optional but useful

### Screenshot Integrity

- Use only final V2 screenshots for states that changed in V2.
- Do not present V1 failure screenshots as final product behavior.
- V1 evidence remains documented in the self-evaluation and metrics artifacts.
- Do not alter outcome values in screenshots.

---

## 15. Prototype README Requirements

`Prototype/README.md` should state:

- how to open the HTML file;
- that no installation is required;
- that the classroom build uses local deterministic / AI-style logic;
- that no live LLM API is connected;
- that all built-in scenarios are synthetic;
- that creator inputs remain within the browser session in this prototype;
- known limitations;
- the product disclaimer;
- the final classroom status: **Pass for demonstration**.

---

## 16. What Would Change for a Real Pilot

Before using DealFit with real creators:

1. Introduce secure authentication and data storage.
2. Define data retention and deletion policies.
3. Test with multiple creator niches and audiences.
4. Replace or improve the hard-coded audience/niche taxonomy.
5. Validate scoring dimensions and weights.
6. Validate confidence semantics with users.
7. Add a governed LLM/API only after privacy and data-processing review.
8. Keep external reputation, market and legal information grounded to identified sources.
9. Add product observability and recommendation audit logs.
10. Monitor override and failure patterns.
11. Run usability and screening-time studies.
12. Test pricing and willingness to pay.

---

## 17. Prototype Status

### Final Classroom MVP Status

**PASS FOR DEMONSTRATION**

The final Version 2 successfully demonstrates:

- creator-profile configuration;
- structured pitch screening;
- hard-rule safety;
- explainable recommendation output;
- uncertainty and missing-information handling;
- visible external-verification limits;
- manual review states;
- creator override;
- no automatic external action.

### Commercial Status

**NOT YET VALIDATED FOR A PAID PILOT OR SCALE**

The next responsible step is to improve and validate with real creator participants, richer audience/fit logic, privacy controls and evidence of user value.

---

## 18. Traceability

The final prototype implements or references:

- `02_Product_Strategy.md`
- `Appendix/PRD/PRD.md`
- `04_UX_Workflow_Trust.md`
- `Appendix/Wireframes/Wireframes.md`
- `05_Data_Model_Evaluation.md`
- `Appendix/Metrics/Metrics_and_Launch_Gates.md`
- `Appendix/AI_Self_Evaluation/AI_Product_Self_Evaluation.md`
- `Appendix/Workflows/DealFit_Future_Workflow.puml`

Business viability, first-revenue logic and scaling will be documented in:

`06_Business_Economics_Scaling.md`

