# TEAM008
DealFit — An AI-Powered Brand Partnership Screener for Independent Creators 

Team Name
Team 008

Team Members
● Arunachala Gnana Ramanan - 2025MB26107
● Boggavarapu Jagannath - 2025MB26076
● Alamelu G - 2025MB26016
● Abdurrahman Lal Sudhesh - 2025MB26034
● Poojagiri V - 2025MB26084

Working Title
DealFit — An AI-Powered Brand Partnership Screener for Independent Creators

Industry / Function
Creator economy / Influencer marketing operations

Target User
Mid-tier independent creators (10K–200K followers) who manage their own brand partnerships without an agent or agency — and the small creator-management teams (1–2 people) who screen deals on their behalf.

Current Workflow Problem
Creators receive a growing volume of inbound sponsorship offers and DMs (via email, Instagram DMs, and marketplace platforms). Each pitch must be manually checked against: audience fit, pay-per-reach reasonableness, brand reputation/values alignment, and past experience with that brand or similar brands. This is slow, inconsistent, and easy to get wrong when under time pressure — leading creators to either waste time on bad-fit deals or miss good ones buried in the inbox.
Why This Matters
Bad brand-fit decisions cost creators real money (undervalued deals), audience trust (misaligned sponsorships causing follower drop-off or backlash), and time (hours per week screening pitches manually). For creators without agents, this is a persistent, repeated, high-stakes decision with no good tool support today.

Proposed AI Role
Classification + ranking + recommendation: given an inbound brand pitch (brand, offer terms, campaign brief) and the creator's profile (niche, audience demographics, past deal history, stated values/exclusions), the system scores the pitch on fit, flags risk factors, and recommends Accept / Negotiate / Decline — with a stated confidence level.

Why AI Instead of a Simpler Alternative
A static checklist or rules engine can catch simple mismatches (e.g., "brand category creator has excluded") but cannot weigh multiple soft factors together (audience overlap likelihood, pay reasonableness given market rates, brand reputation nuance, tone/values alignment) or learn from a creator's own accept/decline history over time. Search or a dashboard would still require the creator to do the judgment work manually — the value here is in synthesizing many weak signals into one ranked recommendation.

Human-in-the-Loop Design
The AI never auto-accepts or auto-declines a deal. Every recommendation requires creator (or manager) review. Low-confidence or high-risk pitches (e.g., unusually high pay for low effort, brand controversy signals, contract red flags) are explicitly flagged for manual escalation rather than a normal recommendation.

Smallest Credible MVP
A no-code tool where a creator profile (niche, audience stats, past deals, exclusion list) is entered once, and each new pitch is scored against it — producing a fit score, key risk flags, and an Accept/Negotiate/Decline recommendation with reasoning. Tested against 5–10 real or realistic sample pitches for one creator persona.

Build vs Buy vs API View
API-first / no-code orchestration for MVP: use an LLM API (or manual ChatGPT/Claude runs as Wizard-of-Oz) for the scoring/reasoning step, a spreadsheet or no-code app (Glide/Airtable/Google Sheets) as the interface and data store. No custom model training needed at MVP stage — differentiation is in the scoring logic and workflow fit, not the model.

Main Risks
● Risk 1: AI over-trusts a well-written but low-quality brand pitch (surface polish vs actual fit).
● Risk 2: Bias toward brands that "look" reputable (large, well-known) over smaller but better-fit brands.
● Risk 3: Creator over-relies on the score and skips their own judgment, missing context the tool can't see (e.g., personal relationship with a brand contact).

Success Evidence
● Creators report the tool reduces screening time per pitch.
● Creators agree with (or make an informed override of) the tool's recommendation in a majority of test cases.
● Flagged high-risk deals match what an experienced creator/manager would independently flag.
