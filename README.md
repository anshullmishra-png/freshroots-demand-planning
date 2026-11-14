# Freshroots Demand Planning

**Demand planning for a 200-person snacks and staples distributor: rules flag what to reorder, AI explains why, and the planner approves.**

[![tests](https://github.com/anshullmishra-png/freshroots-demand-planning/actions/workflows/tests.yml/badge.svg)](https://github.com/anshullmishra-png/freshroots-demand-planning/actions/workflows/tests.yml) [![licence: MIT](https://img.shields.io/badge/licence-MIT-blue)](LICENSE)

[Live demo](https://freshroots-demand-planning-demo.vercel.app) · Built for Mesa School of Business. Freshroots and its people (Raghav, Priya, Deepa) are a fictional case brief, and the data is seeded.

## The problem

Freshroots loses ₹28–34 lakh a quarter: ₹18–22 lakh in stockouts and ₹10–12 lakh in overstock write-offs, mostly perishables. Its demand planner spends about two working days a month pulling SAP data into Excel, so the forecast is 3–4 weeks old by the time procurement acts, and festival periods and competitor schemes get missed.

## What I decided

- **Success is measured in rupees, not in flags produced.** If the quarterly loss doesn't fall below the ₹28–34 lakh baseline, the system has failed, however busy it looks.
- **The planner's rules decide; the AI explains.** His documented rules cover about 80–85% of monthly recommendations. The cases rules can't cover (launches, one-off events) are surfaced to him, not decided for him.
- **Two kill switches.** If the planner reverses 10% or more of the AI's decisions, the automation stops and the old process returns.
- **Twice a week instead of monthly,** with the planner as reviewer instead of calculator. Every rejection is logged with a reason.

[Why it works this way: the decision record](docs/12-OPEN-QUESTIONS.md) · [Project brief](docs/00-PROJECT-BRIEF.md) · [Kill switches](docs/06-KILL-SWITCHES.md)

## Did it work?

832 tests run on every push. A separate check covers accessibility (WCAG 2.2 AA) at desktop and phone width. Not measured yet: the rupee outcome, which needs a real quarter of use.

## What it doesn't solve

It reads SAP data from exported files, not a live connection, and it is not a chatbot: there is no free-text AI interface. The 15–20% of cases outside the rules still need the planner's judgement.

## Try it in 60 seconds

The live demo signs you in with a test account; no password needed.

1. Open the [live demo](https://freshroots-demand-planning-demo.vercel.app). You land on **Review** as Raghav, the demand planner.
2. Look at a flagged SKU: the rule that fired, the AI's explanation, and what accepting would do to stock cover and loss exposure.
3. **Accept** or **Reject** it. Every rejection is logged with a reason.
4. Press **Switch role** to see the same week as procurement, the dashboard owner or the kill-switch owner.

---

## How it's built

The full specification this app was built from, written before any code, is in [`docs/`](docs/): brief, component map, business rules, data spec, AI spec, guardrails, kill switches, screens, design system, measurement plan, test plan, deployment and build plan. [`docs/BUILD-PACK.md`](docs/BUILD-PACK.md) lists every file and how the pack was handed to the coding agent.
