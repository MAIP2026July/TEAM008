# DealFit - PM Artifact Pack

## 1. Purpose

This artifact provides a management-friendly summary and index of the Product Management work completed for DealFit. Detailed product requirements, workflows, wireframes, evaluation criteria, roadmap and risk controls are maintained in the linked repository artifacts rather than duplicated here.

> **Product principle: AI recommends. The creator decides.**

---

## 2. Product at a Glance

| Item | DealFit Position |
|---|---|
| Product | AI-assisted brand partnership screener |
| Primary user | Independent mid-tier creators managing sponsorships without a full-service agent |
| Initial segment | Approximately 10K-200K followers |
| First wedge | Screen one inbound sponsorship pitch against one persistent creator profile |
| Core output | Accept / Negotiate / Decline / Manual Review / Need More Information |
| AI role | Extract, interpret, synthesize, explain |
| Rule role | Enforce explicit creator constraints and critical information checks |
| Human role | Make the final partnership decision |
| MVP status | Pass for classroom demonstration |
| Commercial status | Not yet validated for paid pilot or scale |

---

## 3. Product Vision

> **Help independent creators evaluate inbound brand partnerships quickly, consistently and confidently while keeping the creator in control of the final decision.**

DealFit converts fragmented sponsorship information into a structured first-pass assessment containing:

- DealFit score;
- recommendation;
- confidence;
- supporting reasons;
- risks;
- missing information;
- external-verification requirements;
- recommended next action.

Detailed strategy:

`02_Product_Strategy.md`

---

## 4. Problem Statement

Independent creators frequently evaluate sponsorship opportunities through fragmented channels such as email, direct messages and creator marketplaces. Each opportunity may require manual assessment of creator-brand fit, audience relevance, compensation, deliverables, usage rights, exclusivity, creator values, existing conflicts and missing information.

The process is repetitive and context-heavy. DealFit addresses the first-pass screening decision rather than attempting to manage the entire creator-brand partnership lifecycle.

---

## 5. Primary Persona

### Maya - Independent Lifestyle Creator

Design profile:

- approximately 75,000 followers;
- lifestyle and wellness niche;
- manages sponsorships independently;
- receives multiple inbound partnership enquiries;
- uses email, DMs, spreadsheets and personal notes;
- has no dedicated agent.

Primary need:

> A fast first-pass assessment that identifies important deal information, flags concerns, explains reasoning and preserves final creator control.

Maya is a design persona, not a claimed interview participant.

---

## 6. Jobs to Be Done

### Functional JTBD

> When I receive a sponsorship pitch, help me determine whether it deserves acceptance, negotiation, rejection or additional review without rebuilding the evaluation from scratch.

### Trust JTBD

> Show why the recommendation was produced, what is missing and where human judgement is still required.

### Business JTBD

> Help me focus time on commercially relevant opportunities and reduce effort spent on unsuitable or incomplete pitches.

---

## 7. MVP Scope

### In Scope

- creator-profile creation and editing;
- preferred and excluded categories;
- creator minimum-compensation preference;
- manual pitch input / copy-paste;
- structured deal fields;
- missing-information detection;
- deterministic hard-rule checks;
- creator/campaign fit assessment;
- 0-100 screening score;
- recommendation;
- confidence;
- reasons;
- risk flags;
- external-verification labels;
- human decision;
- override and optional reason capture;
- synthetic evaluation scenarios;
- local Decision History.

### Out of Scope

- automatic acceptance or rejection;
- autonomous negotiation;
- contract execution;
- payment processing;
- legal advice;
- live brand-reputation claims;
- live market-rate benchmarking;
- full creator CRM;
- sponsor discovery;
- proprietary foundation-model training.

Detailed requirements:

`Appendix/PRD/PRD.md`

---

## 8. Core User Stories

| ID | User Story | Priority |
|---|---|---|
| US-01 | Create a reusable creator profile for screening | Must |
| US-02 | Paste an inbound brand pitch for analysis | Must |
| US-03 | Identify missing information | Must |
| US-04 | Enforce creator-excluded categories | Must |
| US-05 | Receive a score and recommendation | Must |
| US-06 | Understand reasons and risk flags | Must |
| US-07 | See recommendation confidence | Must |
| US-08 | Override DealFit using creator context | Must |
| US-09 | Distinguish facts from AI inference | Must |
| US-10 | Receive a suggested next action | Should |
| US-11 | Retain basic decision/override history | Should |
| US-12 | Configure scoring priorities | Could |

---

## 9. MoSCoW Prioritization

### Must Have

- creator profile;
- pitch input;
- mandatory-field checks;
- creator exclusions;
- fit assessment;
- score;
- recommendation;
- confidence;
- explanation;
- risk flags;
- missing information;
- human decision and override;
- decision-support disclaimer.

### Should Have

- basic decision history;
- suggested next action;
- configurable minimum compensation;
- override-reason capture;
- synthetic-scenario loader.

### Could Have

- configurable scoring weights;
- duplicate-pitch detection;
- personalization from reviewed override history;
- negotiation-draft support requiring approval;
- exportable deal summary.

### Won't Have in MVP

- live inbox integration;
- automated brand communication;
- contract signing;
- payment processing;
- live brand-reputation scraping;
- full market-rate database;
- custom model training;
- full creator CRM.

---

## 10. Decision Framework

```text
Creator Profile + Sponsorship Pitch
                |
                v
       Validate Critical Information
                |
                v
       Apply Deterministic Rules
                |
                v
      Assess Softer Fit Signals
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
 Final Decision / Override / More Information
```

Recommendation precedence:

1. Hard creator conflict: Decline or Manual Review.
2. Critical information missing / contradictory: Manual Review / Need More Information.
3. Strong fit + acceptable terms + no material concern: Accept.
4. Good potential + improvable terms: Negotiate.
5. Weak fit with no credible improvement path: Decline.

---

## 11. Current vs Future Workflow

### Current State

The creator manually reads the pitch, extracts terms, checks fit, researches context, compares prior experience and decides what to do.

Artifact:

`Appendix/Workflows/Current_State_Workflow.puml`

### Future State

DealFit structures information, checks hard constraints, assesses softer fit, presents confidence/risk/missing information, and returns a recommendation for creator review.

Artifact:

`Appendix/Workflows/DealFit_Future_Workflow.puml`

No external action is executed automatically.

---

## 12. UX and Trust Model

The product experience is organized around four core screens:

1. Creator Profile
2. New Partnership / Pitch Input
3. DealFit Analysis
4. Creator Decision / Override

Critical UX states include:

- Missing Information;
- Hard Conflict;
- Low Confidence;
- No External Verification;
- Error / fallback;
- Override.

Trust labels distinguish:

- **Provided Fact**
- **AI Inference**
- **Rule Trigger**
- **External Verification Required**

Detailed UX:

`04_UX_Workflow_Trust.md`

Wireframes:

`Appendix/Wireframes/Wireframes.md`

---

## 13. Data and AI Product Design

### Inputs

- creator profile;
- creator rules/preferences;
- sponsorship pitch;
- structured deal fields;
- creator-provided contextual notes.

### Hybrid Logic

**Deterministic rules** handle:

- excluded categories;
- critical missing information;
- minimum compensation preference;
- usage-rights concerns;
- exclusivity concerns;
- explicit partnership conflicts.

**AI-style assessment** handles:

- creator/campaign fit;
- audience relevance;
- values alignment;
- brief clarity;
- ambiguity;
- explanation and next action.

### Human Role

The human owns the final decision and may override DealFit.

Detailed strategy:

`05_Data_Model_Evaluation.md`

---

## 14. Evaluation and Launch Gates

### V1 Evaluation

- 12/12 synthetic scenarios executed;
- 8/12 primary behaviors passed;
- four primary behavior failures identified;
- six design/implementation limitations documented.

### V2 Regression

Targeted checks:

- S01 Accept path;
- S03 creator exclusion;
- S04 critical missing compensation;
- S06 unclear exclusivity;
- S07 weak niche fit;
- S09 explicit partnership conflict;
- S11 values ambiguity.

**Result: 7/7 targeted regression behaviors passed.**

### Final Classroom Gate

**PASS FOR DEMONSTRATION**

### Paid-Pilot Gate

**IMPROVE AND VALIDATE FIRST**

Detailed scorecard:

`Appendix/Metrics/Metrics_and_Launch_Gates.md`

---

## 15. Prototype Status

Final implementation:

`Prototype/DealFit_Prototype.html`

The browser MVP implements:

- profile configuration;
- 12 synthetic scenarios;
- screening logic;
- recommendation/confidence;
- evidence and risk sections;
- manual review states;
- human override;
- session decision history.

The classroom prototype uses local JavaScript logic and **does not call a live LLM API**.

Prototype documentation:

`09_Prototype_MVP.md`

---

## 16. AI Build and Self-Evaluation

The PM artifacts were used to direct AI to build the functional prototype.

Structured V1 testing identified:

- L1 audience heuristic weakness;
- L2 confidence semantics issue;
- L3 critical missing-field precedence issue;
- L4 over-broad partnership conflict detection;
- L5 incidental-keyword niche error;
- L6 values-risk propagation issue.

Human review directed Version 2 corrections and targeted regression testing.

Detailed evaluation:

`Appendix/AI_Self_Evaluation/AI_Product_Self_Evaluation.md`

---

## 17. Roadmap

DealFit's planned evidence stages are:

```text
Classroom Prototype
        ->
Private Alpha
        ->
Creator Beta
        ->
First Paid Pilot
        ->
Creator Pro
        ->
Small Creator Teams
```

### First-Money Milestone

Proposed paid-pilot hypothesis:

**INR 499/month per creator**

This price is for willingness-to-pay testing and is not validated market pricing.

Detailed roadmap:

`Appendix/Roadmap/Roadmap.md`

---

## 18. Business and Scaling Position

The current recommendation is:

> **Fund/support a small validation stage, not scale.**

DealFit currently has no measured evidence for:

- willingness to pay;
- customer acquisition cost;
- retention;
- lifetime value;
- real screening-time saving;
- production API cost;
- real support cost;
- creator satisfaction / NPS.

Detailed economics:

`06_Business_Economics_Scaling.md`

---

## 19. Responsible AI and Governance

Key product controls include:

- human final authority;
- facts vs inference separation;
- external-verification labels;
- no automatic external action;
- explicit creator exclusions;
- conservative handling of missing/contradictory information;
- privacy/data minimization;
- monitoring and incident response;
- launch-blocking safety conditions.

Governance:

`07_Ethics_Governance_Risk.md`

Detailed risk register:

`Appendix/Risk_Note/Risk_Note.md`

---

## 20. Key Open Questions

Before a real pilot the product still needs to answer:

1. How should audience relevance be evaluated beyond the simplified prototype heuristic?
2. Which scoring weights should become creator-configurable?
3. What definition of confidence is most understandable to creators?
4. Which fields are critical for different deal types?
5. How should override history be used without reinforcing one-off decisions?
6. Does DealFit materially reduce screening time?
7. Will creators repeatedly use the workflow?
8. What price, if any, will real creators pay?
9. What LLM/API architecture offers acceptable privacy, reliability and cost if introduced?
10. Do small creator-management teams offer stronger economics than individual creators?

---

## 21. PM Artifact Index

| PM Artifact | Repository Location |
|---|---|
| Product Strategy | `02_Product_Strategy.md` |
| PM Artifact Pack | `03_PM_Artifact_Pack.md` |
| PRD | `Appendix/PRD/PRD.md` |
| Current Workflow | `Appendix/Workflows/Current_State_Workflow.puml` |
| Future Workflow | `Appendix/Workflows/DealFit_Future_Workflow.puml` |
| UX / Trust Design | `04_UX_Workflow_Trust.md` |
| Wireframes | `Appendix/Wireframes/Wireframes.md` |
| Data / Model / Evaluation | `05_Data_Model_Evaluation.md` |
| Metrics / Launch Gates | `Appendix/Metrics/Metrics_and_Launch_Gates.md` |
| Prototype | `Prototype/DealFit_Prototype.html` |
| Prototype Documentation | `09_Prototype_MVP.md` |
| AI Self-Evaluation | `Appendix/AI_Self_Evaluation/AI_Product_Self_Evaluation.md` |
| Roadmap | `Appendix/Roadmap/Roadmap.md` |
| Business / Economics / Scaling | `06_Business_Economics_Scaling.md` |
| Ethics / Governance / Risk | `07_Ethics_Governance_Risk.md` |
| Detailed Risk Register | `Appendix/Risk_Note/Risk_Note.md` |

---

## 22. PM Recommendation

The PM artifact set supports the following product decision:

> **DealFit has progressed far enough to justify controlled real-user validation, but not enough to justify autonomous execution, production-scale investment, or commercial-impact claims.**

The next product-management objective is therefore not feature expansion. It is to validate:

- repeated problem frequency;
- real workflow value;
- trust;
- screening-time improvement;
- willingness to pay;
- serving economics.

