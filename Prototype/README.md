# DealFit Prototype

## Overview

DealFit is an AI-assisted brand partnership screening prototype for independent creators and small creator-management teams.

The prototype evaluates an inbound sponsorship pitch against a creator profile and returns:

- DealFit score;
- Accept / Negotiate / Decline / Manual Review / Need More Information recommendation;
- confidence level;
- provided facts;
- AI-style inferences;
- risk flags;
- missing information;
- external-verification requirements;
- recommended next action.

> **AI recommends. The creator decides.**

---

## Prototype File

Open:

`DealFit_Prototype.html`

No installation, server, account or API key is required.

Recommended browsers:

- Microsoft Edge
- Google Chrome

---

## How to Run

1. Download or clone the repository.
2. Open the `Prototype` folder.
3. Double-click `DealFit_Prototype.html`.
4. Review or edit the default Maya creator profile.
5. Select **Save Creator Profile**.
6. Select a synthetic scenario or enter a new fictional deal.
7. Select **Load Scenario** when using S01-S12.
8. Select **Analyze with DealFit**.
9. Review the recommendation, confidence, facts, inferences, risks, missing information and verification requirements.
10. Continue to the creator-decision screen.
11. Record a final decision or override DealFit.

---

## Prototype Workflow

```text
Creator Profile
      |
      v
New Partnership / Pitch Input
      |
      v
DealFit Analysis
      |
      v
Creator Decision / Override
      |
      v
Session Decision History
```

The prototype never contacts a brand or executes an external action.

---

## Important Technical Note

The classroom prototype uses:

- local HTML;
- CSS;
- JavaScript rules;
- configurable creator inputs;
- hard-coded prototype scoring and confidence logic;
- local AI-style assessment behavior.

The prototype does **not** use:

- a live LLM API;
- live web search;
- live brand-reputation data;
- a market-rate database;
- legal-analysis services;
- production authentication or cloud storage.

Creator and deal information remains within the active browser session for this prototype.

---

## Synthetic Scenarios

The prototype contains 12 fictional scenarios:

| ID | Scenario | Intended Test |
|---|---|---|
| S01 | Strong fit, complete terms | Accept path |
| S02 | Strong fit, low compensation | Negotiate |
| S03 | Excluded category | Hard creator boundary |
| S04 | Compensation missing | Critical missing information |
| S05 | Broad paid-media rights | Usage-rights risk |
| S06 | Unclear exclusivity | Clarification / Manual Review |
| S07 | Weak niche and audience fit | Decline |
| S08 | High pay, incomplete terms | Avoid over-trusting compensation |
| S09 | Existing partnership conflict | Explicit conflict handling |
| S10 | Creator-only context | Human override |
| S11 | Ambiguous values alignment | Values-risk escalation |
| S12 | Contradictory terms | Low-confidence review |

All brands, pitches and deal terms are synthetic.

---

## Human Override

The creator can select:

- Accept;
- Negotiate;
- Decline;
- Need More Information;
- Manual Review.

When the creator decision differs from DealFit:

- an override warning is displayed;
- an optional reason can be selected;
- additional notes can be entered;
- the final decision is stored in the session Decision History;
- no external action is executed.

---

## Trust and Safety Design

The prototype includes:

- creator-defined excluded categories;
- critical missing-information escalation;
- explicit risk flags;
- confidence labels;
- score-not-probability disclaimer;
- separation of provided facts and AI-style inferences;
- external-verification warnings;
- required creator review;
- human override;
- no automatic brand communication or financial/contract action.

The analysis explicitly states:

- Brand reputation not verified
- Market-rate comparison unavailable
- Contract enforceability not assessed

---

## Evaluation Summary

### Version 1

- 12/12 synthetic scenarios executed
- 8/12 primary expected behaviors passed
- Six product-logic limitations documented

### Version 2

Targeted regression scenarios:

- S01
- S03
- S04
- S06
- S07
- S09
- S11

Result:

**7/7 targeted regression behaviors passed.**

S10 separately demonstrated an informed human override.

Detailed evidence:

- `../Appendix/Metrics/Metrics_and_Launch_Gates.md`
- `../Appendix/AI_Self_Evaluation/AI_Product_Self_Evaluation.md`
- `../09_Prototype_MVP.md`

---

## Known Limitations

- Audience relevance uses a simplified hard-coded heuristic.
- Screening weights are prototype assumptions.
- Confidence is rule-based, not probability calibrated.
- Values-sensitive terms use a small keyword set.
- Only one design persona was used for most testing.
- Evidence is synthetic rather than real-user validation.
- No live LLM, retrieval, brand reputation, legal, or market-rate source is connected.
- Session data is not persisted after the browser session.
- The prototype is not production-secure.

---

## Screenshot Folder

Final screenshots should be stored under:

`screenshots/`

Recommended files:

1. `01_Creator_Profile.png`
2. `02_New_Deal.png`
3. `03_Analysis_Negotiate.png`
4. `04_Decision_Override.png`
5. `05_Missing_Information.png`
6. `06_Hard_Conflict.png`
7. `07_Weak_Fit_Decline.png` - optional
8. `08_Values_Manual_Review.png` - optional

Use final Version 2 screenshots for any state corrected during the V1-to-V2 revision.

---

## Product Disclaimer

DealFit provides AI-assisted screening and does not provide legal, financial, contractual, market-rate, or reputation-verification services.

Creators remain responsible for:

- reviewing the source information;
- correcting inaccurate inputs;
- considering relationship and audience context;
- seeking professional advice where required;
- making the final sponsorship decision.

---

## Final Status

### Classroom Prototype

**PASS FOR DEMONSTRATION**

### Commercial / Paid Pilot

**IMPROVE AND VALIDATE FIRST**

The next responsible step is a controlled, consent-based validation stage with real creators, secure data handling, improved audience/fit logic, and measured evidence of workflow value.

