# DealFit - Low-Fidelity Wireframes

## 1. Purpose

This artifact translates the requirements in `Appendix/PRD/PRD.md` and `04_UX_Workflow_Trust.md` into low-fidelity screen specifications for the DealFit MVP.

The wireframes are intentionally functional rather than visually polished. They define:

- the information shown on each screen;
- the order of user actions;
- the placement of trust and uncertainty signals;
- the human-review and override workflow;
- the states that the prototype must demonstrate.

> **Product principle: AI recommends. The creator decides.**

---

## 2. Navigation Model

The MVP uses a four-step workflow:

```text
1. Creator Profile  -->  2. New Deal  -->  3. DealFit Analysis  -->  4. Creator Decision
```

Optional navigation items:

- Decision History
- About the Prototype
- Load Synthetic Scenario

For the first prototype, the four steps may be implemented as sections within a single responsive page.

---

## 3. Wireframe 1 - Creator Profile

### Objective

Capture reusable creator context, preferences, exclusions, and commercial boundaries before a pitch is analysed.

```text
+--------------------------------------------------------------------------------+
| DealFit                                              [Profile] [New Deal] [Help]|
+--------------------------------------------------------------------------------+
| CREATOR PROFILE                                                               |
| Tell DealFit how partnership opportunities should be screened.                |
| Sensitive commercial preferences are used only for this prototype workflow.   |
+--------------------------------------------------------------------------------+
| Profile Name*                     | Follower Range                             |
| [ Maya - Lifestyle Creator     ] | [ 50K-100K                         v ]      |
|                                   |                                            |
| Primary Niche*                    | Typical Content Formats                    |
| [ Lifestyle & Wellness         ] | [x] Short video  [x] Stories  [ ] Blog     |
|                                   |                                            |
| Content Themes                    | Audience Characteristics                   |
| [ Wellness, routines, travel   ] | [ Urban, 18-34, wellness interested     ]  |
|                                   |                                            |
| Preferred Categories              | Excluded Categories                        |
| [ Wellness, travel, beauty     ] | [ Gambling, tobacco, payday loans       ]  |
|                                   |                                            |
| Creator Values / Boundaries       | Minimum Compensation (optional)            |
| [ No misleading health claims  ] | [ INR 25,000                           ]    |
| [ No unrealistic body claims   ] |                                            |
|                                   |                                            |
| Previous Partnership Notes (optional)                                         |
| [ Existing 3-month exclusivity with a skincare brand                    ]     |
+--------------------------------------------------------------------------------+
| [Reset to Demo Persona]                              [Save Creator Profile]    |
+--------------------------------------------------------------------------------+
| Why this information is collected: DealFit uses supplied profile information  |
| to apply creator-defined rules and generate screening recommendations.          |
+--------------------------------------------------------------------------------+
```

### Required Behaviours

- Validate primary niche before saving.
- Reject negative compensation values.
- Warn if the same category appears under both Preferred and Excluded.
- Allow optional fields to remain blank.
- Clearly label commercial preferences and prior-deal notes as sensitive.
- Allow profile editing before every pitch analysis.

### PRD Traceability

- FR-01
- AC-01
- TSR-05

---

## 4. Wireframe 2 - New Partnership / Pitch Input

### Objective

Capture the original sponsorship pitch and known structured terms without forcing the creator to invent missing information.

```text
+--------------------------------------------------------------------------------+
| DealFit                                   Profile Saved: Maya     Step 2 of 4   |
+--------------------------------------------------------------------------------+
| NEW PARTNERSHIP                                                               |
| Paste the original pitch and confirm any known deal terms.                    |
+--------------------------------------------------------------------------------+
| Synthetic Demo Scenario [ Select scenario...                           v ]     |
| [Load Scenario]                                                                |
+--------------------------------------------------------------------------------+
| Brand Name*                       | Brand Category                              |
| [ WellSpring Nutrition         ] | [ Wellness                           v ]     |
|                                   |                                            |
| Proposed Compensation             | Campaign Timeline                           |
| [ INR 35,000                   ] | [ 3 weeks                                ]   |
|                                   |                                            |
| Deliverables                                                                    |
| [ 2 short videos + 3 stories                                          ]       |
|                                                                                |
| Usage Rights                      | Exclusivity Terms                           |
| [ 6 months + paid media        ] | [ Not Provided                          ]   |
|                                   |                                            |
| Target Audience                   | Payment Terms                               |
| [ Urban wellness audience      ] | [ Not Provided                          ]   |
|                                                                                |
| Original Pitch / Campaign Brief*                                               |
| +----------------------------------------------------------------------------+ |
| | Hi Maya, we would like to partner with you for our upcoming...             | |
| |                                                                            | |
| +----------------------------------------------------------------------------+ |
|                                                                                |
| Additional Notes                                                               |
| [ Existing relationship with the brand contact                          ]     |
+--------------------------------------------------------------------------------+
| [Clear Pitch]                                      [Analyze with DealFit]      |
+--------------------------------------------------------------------------------+
| Unknown information should be marked “Not Provided.” Do not guess deal terms.  |
+--------------------------------------------------------------------------------+
```

### Required Behaviours

- Require Brand Name and Pitch Text for the normal analysis flow.
- Preserve the original pitch text.
- Accept `Not Provided` as a valid state for uncertain terms.
- Flag missing compensation, deliverables, usage rights, exclusivity, or payment terms.
- Trigger a hard-conflict path when the brand category matches an exclusion.
- Support loading clearly labelled synthetic test scenarios.

### PRD Traceability

- FR-02 to FR-05
- AC-02 and AC-03

---

## 5. Wireframe 3 - DealFit Analysis

### Objective

Present a concise, explainable screening result while keeping uncertainty, missing information, and external-verification limits visible.

```text
+--------------------------------------------------------------------------------+
| DealFit                                              Analysis Complete          |
+--------------------------------------------------------------------------------+
| CREATOR REVIEW REQUIRED                                                       |
|                                                                                |
| DealFit Score          Recommendation              Confidence                 |
|      72 / 100          [ NEGOTIATE ]               [ MEDIUM ]                 |
|                                                                                |
| The DealFit score is a structured screening indicator. It is not a probability|
| of campaign success.                                                          |
+--------------------------------------------------------------------------------+
| RECOMMENDED NEXT ACTION                                                        |
| Negotiate compensation and narrow paid-media usage rights. Request payment    |
| terms and exclusivity duration before deciding.                               |
+--------------------------------------------------------------------------------+
| PROVIDED FACTS                         | AI INFERENCES                          |
| - Category: Wellness                   | - Broad niche alignment               |
| - Compensation: INR 35,000             | - Deliverable burden may be high      |
| - Deliverables: 2 videos + 3 stories   | - Partnership may be worth negotiating|
| - Usage rights: 6 months + paid media  |                                       |
+--------------------------------------------------------------------------------+
| RISK FLAGS                                                                    |
| [MEDIUM] Broad paid-media usage rights                                        |
| [MEDIUM] Deliverable burden may be high                                       |
| [LOW]    Payment schedule unavailable                                         |
+--------------------------------------------------------------------------------+
| MISSING INFORMATION                    | EXTERNAL VERIFICATION REQUIRED         |
| - Payment terms                        | - Brand reputation not verified        |
| - Exclusivity duration                 | - Market-rate comparison unavailable   |
| - Content approval process             | - Contract enforceability not assessed |
+--------------------------------------------------------------------------------+
| DIMENSION DETAILS [Expand]                                                     |
| Creator fit 82 | Audience 78 | Commercial 62 | Feasibility 68 | Risk 55        |
+--------------------------------------------------------------------------------+
| DealFit provides decision support, not legal, financial, contractual, or      |
| reputation-verification services.                                              |
+--------------------------------------------------------------------------------+
| [Edit Facts and Rerun]                           [Continue to Creator Decision] |
+--------------------------------------------------------------------------------+
```

### Required Behaviours

- Display Recommendation, Score, and Confidence together.
- Label the result `Creator Review Required`.
- Separate Provided Facts, AI Inferences, Rule Triggers, and External Verification.
- Show the reason for Medium or Low confidence.
- Do not imply brand research was performed when no source is connected.
- Do not expose hidden chain-of-thought.
- Allow the creator to edit extracted facts and rerun the analysis.

### PRD Traceability

- FR-06 to FR-11
- AIR-01 to AIR-07
- AC-04, AC-05, AC-07, and AC-08

---

## 6. Wireframe 4 - Creator Decision and Override

### Objective

Capture the final human decision and preserve the ability to disagree with DealFit.

```text
+--------------------------------------------------------------------------------+
| DealFit                                                   Step 4 of 4          |
+--------------------------------------------------------------------------------+
| CREATOR DECISION                                                               |
| DealFit recommended: NEGOTIATE | Confidence: MEDIUM | Score: 72                |
+--------------------------------------------------------------------------------+
| What is the creator's final decision?                                          |
|                                                                                |
| [ Accept ] [ Negotiate ] [ Decline ] [ Need More Information ] [ Manual Review]|
|                                                                                |
| Selected: DECLINE                                                              |
+--------------------------------------------------------------------------------+
| OVERRIDE NOTICE                                                                |
| The selected creator decision differs from the DealFit recommendation.          |
|                                                                                |
| Override Reason (optional) [ Select...                                  v ]    |
| - Personal relationship or context                                             |
| - Existing partnership conflict                                                |
| - Commercial context unavailable to DealFit                                    |
| - Audience context unavailable to DealFit                                      |
| - Contract concern                                                             |
| - Known brand information                                                      |
| - Recommendation reasoning was not persuasive                                  |
| - Other                                                                        |
|                                                                                |
| Additional Notes                                                               |
| [ Existing exclusivity makes this partnership unsuitable.                ]    |
+--------------------------------------------------------------------------------+
| [Back to Analysis]                                    [Record Final Decision]  |
+--------------------------------------------------------------------------------+
| No brand message, contract action, acceptance, or rejection will be executed   |
| automatically.                                                                 |
+--------------------------------------------------------------------------------+
```

### Confirmation State

```text
+--------------------------------------------------------------------------------+
| Decision Recorded                                                              |
| Final creator decision: DECLINE                                                 |
| DealFit recommendation: NEGOTIATE                                               |
| Override recorded: Yes                                                         |
|                                                                                |
| DealFit has not contacted the brand or executed any external action.            |
|                                                [Screen Another Partnership]     |
+--------------------------------------------------------------------------------+
```

### Required Behaviours

- Keep `Need More Information` and `Manual Review` as separate creator actions.
- Detect when the final creator decision differs from DealFit.
- Allow, but do not force, an override reason.
- Store recommendation, confidence, final decision, and override feedback.
- Never execute an external action.

### PRD Traceability

- FR-12 to FR-14
- AC-06 and AC-09
- TSR-01 and TSR-06

---

## 7. Wireframe 5 - Missing Information / Low Confidence

### Objective

Demonstrate safe degradation when the provided pitch is incomplete.

```text
+--------------------------------------------------------------------------------+
| DealFit                                              Analysis Incomplete        |
+--------------------------------------------------------------------------------+
| Recommendation: NEED MORE INFORMATION / MANUAL REVIEW                           |
| Confidence: LOW                         DealFit Score: Not emphasized           |
+--------------------------------------------------------------------------------+
| WHY CONFIDENCE IS LOW                                                         |
| Material deal information is unavailable. DealFit cannot evaluate the          |
| commercial and contractual trade-offs reliably.                               |
+--------------------------------------------------------------------------------+
| MISSING INFORMATION                                                            |
| [!] Proposed compensation                                                      |
| [!] Usage rights                                                               |
| [!] Exclusivity duration                                                       |
| [!] Payment terms                                                              |
+--------------------------------------------------------------------------------+
| SUGGESTED QUESTIONS FOR THE BRAND                                               |
| 1. What is the proposed compensation and payment schedule?                     |
| 2. Will the brand use the content in paid advertising?                         |
| 3. Is category exclusivity required, and for how long?                         |
+--------------------------------------------------------------------------------+
| External verification was not performed.                                       |
+--------------------------------------------------------------------------------+
| [Edit Pitch Details] [Record Need More Information] [Choose Manual Review]     |
+--------------------------------------------------------------------------------+
```

### Required Behaviours

- Do not show an unqualified Accept recommendation.
- Explain the cause of Low confidence.
- List specific missing fields.
- Offer practical questions for the brand.
- Keep `Need More Information` and `Manual Review` separate.

### PRD Traceability

- FR-04 and FR-09
- AIR-04
- AC-03 and AC-08

---

## 8. Wireframe 6 - Hard Conflict

### Objective

Show that creator-defined exclusions override positive AI reasoning.

```text
+--------------------------------------------------------------------------------+
| DealFit                                                  HARD CONFLICT          |
+--------------------------------------------------------------------------------+
| Recommendation: DECLINE / MANUAL REVIEW                                        |
| Confidence: HIGH for rule detection                                             |
+--------------------------------------------------------------------------------+
| RULE TRIGGER                                                                   |
| Brand category: Gambling                                                       |
| Creator exclusion: Gambling and betting partnerships                           |
|                                                                                |
| This creator-defined exclusion was triggered before AI fit assessment.          |
+--------------------------------------------------------------------------------+
| PROVIDED FACTS                                                                 |
| - Brand category was entered as Gambling                                       |
| - Compensation was provided                                                    |
| - Deliverables were provided                                                   |
+--------------------------------------------------------------------------------+
| AI ASSESSMENT LIMIT                                                            |
| DealFit will not use persuasive AI reasoning to override a creator-defined     |
| hard exclusion.                                                                |
+--------------------------------------------------------------------------------+
| [Correct Brand Category] [Record Decline] [Choose Manual Review]               |
+--------------------------------------------------------------------------------+
```

### Required Behaviours

- Identify the precise creator rule triggered.
- Do not generate an unqualified Accept result.
- Allow category correction if the input was wrong.
- Permit Manual Review when the creator chooses to investigate further.
- Preserve the creator's final authority without weakening the warning.

### PRD Traceability

- FR-05
- TSR-03
- AC-02

---

## 9. Optional Wireframe - Decision History

Decision History is a **Should Have** MVP feature.

```text
+--------------------------------------------------------------------------------+
| DECISION HISTORY                                                               |
+--------------------------------------------------------------------------------+
| Brand          DealFit       Confidence   Creator Decision   Override           |
| WellSpring     Negotiate     Medium       Decline            Yes                |
| TrailGo        Accept        High         Accept             No                 |
| BetQuick       Decline       High         Decline            No                 |
| NovaSkin       Manual Review Low          Need Information   Yes                |
+--------------------------------------------------------------------------------+
| [Open Record] [Filter by Decision] [Screen New Partnership]                    |
+--------------------------------------------------------------------------------+
```

The history view must not imply that previous creator choices are automatically correct training labels.

---

## 10. Responsive Behaviour

### Desktop

- Use two-column presentation for profile and pitch fields.
- Keep Recommendation, Score, and Confidence visible at the top of Analysis.
- Use paired evidence blocks for Facts / Inference and Missing / Verification.

### Mobile

- Convert all content to a single column.
- Place Recommendation, Confidence, and major Risk Flags before detailed evidence.
- Stack decision buttons vertically if horizontal space is insufficient.
- Avoid horizontal scrolling and wide data tables.

---

## 11. Accessibility Notes

- Every form field requires a visible label.
- Recommendation states require text in addition to color.
- Risk severity requires text labels such as High, Medium, or Low.
- Focus indicators should remain visible during keyboard navigation.
- Error messages should appear next to the affected field.
- Buttons should use action-specific text such as `Analyze with DealFit` rather than `Submit`.
- Headings should follow a logical order.
- Minimum target size should support touch interaction.

---

## 12. Prototype Build Mapping

| Wireframe | Prototype Component |
|---|---|
| Creator Profile | Profile form and demo-persona loader |
| New Partnership | Pitch form and synthetic-scenario selector |
| DealFit Analysis | Recommendation card and evidence sections |
| Creator Decision | Five human decision buttons and override form |
| Missing Information | Low-confidence guarded result state |
| Hard Conflict | Deterministic rule-trigger state |
| Decision History | Optional local decision log |

---

## 13. Prototype Screenshots Required

When the MVP is built, save screenshots under:

`Prototype/screenshots/`

Required screenshots:

1. `01_Creator_Profile.png`
2. `02_New_Deal.png`
3. `03_Analysis_Negotiate.png`
4. `04_Decision_Override.png`
5. `05_Missing_Information.png`
6. `06_Hard_Conflict.png`

Optional:

7. `07_Decision_History.png`
8. `08_Mobile_View.png`

---

## 14. Traceability

This wireframe artifact implements:

- `02_Product_Strategy.md`
- `Appendix/PRD/PRD.md`
- `04_UX_Workflow_Trust.md`
- `Appendix/Workflows/Current_State_Workflow.puml`
- `Appendix/Workflows/DealFit_Future_Workflow.puml`

Prototype deviations, assumptions, hard-coded elements, and configurable elements must be documented in:

- `09_Prototype_MVP.md`
- `Appendix/AI_Self_Evaluation/AI_Product_Self_Evaluation.md`
