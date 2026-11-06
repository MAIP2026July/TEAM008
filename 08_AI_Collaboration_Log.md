# DealFit - AI Collaboration Log

## 1. Purpose

This log documents how generative AI was used as a product-development collaborator for DealFit, where AI output was useful, where it was weak or ambiguous, what human judgement changed, and how the final product differed from the first AI-generated implementation.

The log is intentionally transparent. AI output was not treated as automatically correct.

> **Collaboration principle: AI accelerates the work; humans remain accountable for product decisions.**

---

## 2. Collaboration Scope

AI was used to support:

- product-strategy structuring;
- persona and JTBD drafting;
- PRD development;
- user-story and MoSCoW formulation;
- current/future workflow design;
- UX and trust requirements;
- wireframe specification;
- data/model/evaluation design;
- synthetic scenario design;
- functional prototype generation;
- scenario-result interpretation;
- defect and ambiguity analysis;
- Version 2 logic revision;
- economics/roadmap structuring;
- governance/risk structuring;
- artifact consistency review.

Human judgement remained responsible for:

- approving scope;
- deciding product boundaries;
- running the prototype;
- providing observed screenshots/results;
- determining whether behavior was acceptable;
- choosing which weaknesses required correction;
- retaining limitations rather than hiding them;
- deciding final readiness claims.

---

## 3. AI Collaboration Summary

| Stage | AI Contribution | Human Contribution | Outcome |
|---|---|---|---|
| Topic refinement | Structured approved topic into a narrow product wedge | Approved scope remained source of truth | DealFit kept focused on inbound partnership screening |
| Product strategy | Drafted vision, persona, JTBD, alternatives and AI role | Reviewed language and scope | `02_Product_Strategy.md` |
| PRD | Drafted requirements, AI/trust requirements and acceptance criteria | Reviewed constraints and consistency | `Appendix/PRD/PRD.md` |
| Workflow | Produced current/future PlantUML swimlanes | Reviewed logic and wording | Two `.puml` workflows |
| UX / Wireframes | Drafted screen states and trust patterns | Confirmed human-control model | UX and wireframe artifacts |
| Evaluation design | Proposed rules, scoring dimensions, test scenarios and gates | Required evidence integrity / no fabricated results | Evaluation + metrics artifacts |
| Prototype V1 | Generated self-contained browser MVP | Ran scenarios and supplied observed results | Functional V1 |
| V1 testing | Helped interpret outputs | Human actually executed S01-S12 | 8/12 primary behaviors passed |
| Defect analysis | Identified likely implementation causes | Human accepted/rejected severity and required changes | L1-L6 documented |
| Prototype V2 | Generated revised logic | Human reran targeted regression | 7/7 targeted regressions passed |
| Governance | Structured risk/accountability framework | Kept claims bounded to evidence | Governance + risk register |
| Business case | Structured staged monetization/economics | Kept prices and costs hypothetical | Roadmap + economics artifacts |

---

## 4. Representative AI Prompts / Instructions

The exact conversation contained iterative requests rather than one single master prompt. The following captures the substance of the key instructions used.

### Prompt A - Build the Product Strategy

> Use the approved DealFit topic as the source of truth. Create a product strategy for independent creators screening inbound brand partnerships. Keep the first wedge narrow. Clearly separate what AI should do, what deterministic rules should do, and what must remain human-controlled. Do not invent customer interviews or validation evidence.

### Prompt B - Build the PRD

> Convert the locked DealFit strategy into a buildable MVP PRD with goals, non-goals, user stories, functional requirements, AI requirements, trust requirements, acceptance criteria, prioritization and explicit human override. Preserve the principle that AI recommends and the creator decides.

### Prompt C - Build the Functional MVP

> Using the DealFit Product Strategy, PRD, workflows, UX/trust specification, wireframes, data/model strategy and evaluation framework as the source of truth, build a functional browser MVP. Implement the Must Have requirements, keep final sponsorship decisions human-controlled, use synthetic scenarios for demonstration, and do not silently invent external reputation or market-rate facts.

### Prompt D - Evaluate the Product

> Compare the observed scenario output with the expected behavior in the PM artifacts. Identify whether the scenario passes, what failed, why the behavior may have occurred, and whether the issue is a safety defect, product-logic defect, UX ambiguity or known prototype limitation. Do not hide failed cases.

### Prompt E - Revise the Product

> Update the tested Version 1 prototype to correct the observed issues without weakening existing guardrails. Preserve the successful Accept, Negotiate, hard-exclusion, missing-information, contradiction and human-override paths. Produce a Version 2 suitable for targeted regression testing.

### Prompt F - Self-Evaluate

> Critically evaluate the DealFit product generated from the PM artifacts. Identify ambiguities, assumptions, hard-coded logic, configurable logic, UX weaknesses, technical limitations, safety/trust concerns and changes required before a real pilot. Use the actual V1 and V2 test evidence rather than generic AI-risk statements.

---

## 5. AI Contribution That Was Useful

### 5.1 Fast Artifact Structuring

AI converted the approved topic into a connected set of PM artifacts quickly while maintaining a common product narrative.

### 5.2 Scope Discipline

The collaboration repeatedly reinforced that DealFit should remain a **sponsorship screener**, not become a full creator CRM, autonomous negotiation agent, payment system or contract-execution tool.

### 5.3 Hybrid AI Design

AI helped separate:

- deterministic creator rules;
- AI-style interpretation;
- confidence/missing-information logic;
- final human decision.

This made the product safer and easier to test.

### 5.4 Test Scenario Generation

The S01-S12 synthetic pack covered:

- strong fit;
- low compensation;
- category exclusion;
- missing compensation;
- broad usage rights;
- unclear exclusivity;
- poor fit;
- incomplete high-pay offer;
- existing conflict;
- human override;
- values ambiguity;
- contradictory terms.

### 5.5 Prototype Generation

AI created a working browser MVP containing the core PM requirements, enabling product behavior to be tested instead of remaining theoretical.

### 5.6 Failure Explanation

After screenshots were provided, AI helped trace failures to specific hard-coded logic rather than treating incorrect recommendations as mysterious model behavior.

---

## 6. Where AI Output Was Weak or Wrong

The first build was functional but not product-correct in every case.

### L1 - Audience-Relevance Heuristic Too Crude

Aligned scenarios received unexpectedly low audience scores because the scoring used simplified matching.

**Human decision:** Treat as a known limitation and improve directionally without claiming semantic accuracy.

### L2 - Confidence Semantics Were Wrong

A High-risk deterministic exclusion caused Low confidence even though the exclusion itself was certain.

**Human correction:** Confidence should describe evidence quality, not risk severity.

### L3 - Missing Compensation Had Insufficient Precedence

S04 returned Negotiate / Medium even though compensation was absent.

**Human correction:** Critical missing information must force guarded review behavior.

### L4 - Partnership Conflict Logic Was Over-Broad

S06 falsely inferred an existing partnership conflict.

**Human correction:** Strong conflict flags require explicit evidence rather than loose category matching.

### L5 - Niche Matching Was Fooled by Incidental Language

S07 incorrectly recommended Accept for an enterprise-software campaign because the pitch contained wording referring to a lifestyle creator.

**Human correction:** Compare campaign category/target audience with creator domains, not incidental pitch wording.

### L6 - Values Misalignment Was Hidden in a Score

S11 produced a low values score without surfacing the problem as a visible risk or lowering confidence.

**Human correction:** Material low-dimension findings must propagate into actionable UX when they affect the recommendation.

---

## 7. Version 1 Evidence

The human tester executed all 12 synthetic scenarios in the first prototype.

### V1 Result

- Scenarios executed: **12 / 12**
- Primary expected behaviors passed: **8 / 12 (66.7%)**
- Primary failures: **S04, S06, S07, S11**

The purpose of retaining this evidence is to show that AI-generated software output required product evaluation and human correction.

---

## 8. Human Review and Version 2 Changes

Human-directed revisions required the second prototype to:

1. separate confidence from risk severity;
2. define critical missing fields;
3. strengthen missing-information precedence;
4. require explicit partnership-conflict evidence;
5. improve niche/domain comparison;
6. surface values concerns as risk;
7. preserve creator exclusions;
8. preserve fact/inference/verification separation;
9. preserve creator override;
10. preserve no-automatic-action behavior.

AI then produced the revised Version 2 implementation.

---

## 9. Version 2 Regression Evidence

The human tester reran the changed paths plus one regression path.

| Scenario | V2 Result | Outcome |
|---|---|---|
| S01 | Accept / High / 74 | Accept path preserved |
| S03 | Decline / High / 48 | Confidence semantics corrected |
| S04 | Manual Review / Low / 58 | Critical missing information corrected |
| S06 | Manual Review / Medium / 74 | False partnership conflict removed |
| S07 | Decline / High / 55 | Poor-fit logic corrected |
| S09 | Decline / High / 74 | Genuine partnership conflict retained |
| S11 | Manual Review / Medium / 70 | Values concern propagated |

**Targeted V2 regression result: 7 / 7 passed.**

---

## 10. Human Override Evidence

S10 was used to test whether human judgement could legitimately differ from DealFit.

### DealFit

- Recommendation: Accept
- Confidence: High
- Score: 75

### Human

- Final decision: Negotiate
- Override: Yes
- Reason: Personal relationship or context
- Note: `Creator has additional context unavailable to DealFit.`

The product recorded the override and performed no external action.

### Learning

Human disagreement should not automatically be classified as AI failure. A creator may possess relationship or contextual information outside the system.

---

## 11. What AI Was Not Allowed to Decide Independently

Throughout the project, AI was not treated as the final authority for:

- product-scope approval;
- final sponsorship decisions;
- legal interpretation;
- verified brand reputation;
- real market-rate claims;
- real pricing willingness;
- real customer-value claims;
- final risk acceptance;
- readiness for a paid pilot;
- team contribution claims.

---

## 12. Hard-Coded and Configurable Learning

The build made the distinction visible.

### Configurable in MVP

- creator profile;
- preferred/excluded categories;
- minimum compensation;
- deal inputs;
- final creator decision.

### Hard-Coded in MVP

- six screening dimensions;
- scoring weights;
- critical-field definition;
- recommendation precedence;
- confidence rules;
- risk severity;
- domain mapping;
- values-sensitive keywords;
- synthetic scenarios.

### Human Product Decision

Hard-coded safety logic is acceptable for a classroom MVP when documented and tested. Personalization assumptions such as audience weighting and values policies should become more configurable before real-world use.

---

## 13. AI-Human Collaboration Pattern

The project ultimately followed this operating model:

```text
Human-approved scope
        |
        v
AI drafts product artifact
        |
        v
Human reviews scope / evidence / wording
        |
        v
AI builds functional implementation
        |
        v
Human runs real tests
        |
        v
AI helps diagnose observed failures
        |
        v
Human decides required correction
        |
        v
AI revises implementation
        |
        v
Human runs regression tests
        |
        v
Final evidence documented transparently
```

This was more reliable than treating either AI output or human intuition alone as sufficient.

---

## 14. Remaining AI Collaboration Limitations

Even after Version 2:

- audience relevance remains simplified;
- scoring weights remain unvalidated;
- confidence remains rule-based;
- values logic remains keyword-based;
- no live LLM/API was tested;
- no real creator dataset was used;
- no real-user productivity/willingness-to-pay evidence exists.

AI assistance cannot substitute for those future validation steps.

---

## 15. Academic Integrity / Evidence Note

The project distinguishes:

- **approved topic information** from later AI-generated product artifacts;
- **design personas** from real interview participants;
- **synthetic scenarios** from real creator data;
- **planning assumptions** from measured evidence;
- **hypothetical pricing** from willingness-to-pay validation;
- **V1 evidence** from **V2 regression evidence**.

No interviews, timings, satisfaction scores, revenue, willingness-to-pay results or production-model metrics are invented.

---

## 16. Final AI Collaboration Assessment

AI materially accelerated the creation of connected PM artifacts and a functional prototype. The most valuable use of AI, however, was not generating the first answer. It was enabling an iterative product loop where assumptions could be made visible and tested.

The Version 1 failures demonstrate why AI-generated implementation still requires structured human review. The Version 2 regression demonstrates the value of converting observed failures into explicit product requirements and retesting them.

The final collaboration conclusion is:

> **AI was effective as a rapid product-development collaborator, but human judgement remained necessary for scope, evidence quality, safety boundaries, defect severity, correction priorities and the final readiness decision.**

---

## 17. Traceability

This collaboration log is supported by:

- `02_Product_Strategy.md`
- `03_PM_Artifact_Pack.md`
- `Appendix/PRD/PRD.md`
- `04_UX_Workflow_Trust.md`
- `05_Data_Model_Evaluation.md`
- `Appendix/Metrics/Metrics_and_Launch_Gates.md`
- `Prototype/DealFit_Prototype.html`
- `09_Prototype_MVP.md`
- `Appendix/AI_Self_Evaluation/AI_Product_Self_Evaluation.md`
- `Appendix/Roadmap/Roadmap.md`
- `06_Business_Economics_Scaling.md`
- `07_Ethics_Governance_Risk.md`

