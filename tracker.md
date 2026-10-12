# Bali Superhost — Project Tracker

*Last updated: 2026-10-12 (Closio ruled out, pros/cons tables, WhatsApp economics + Zoho automation researched)*

---

## Overview

Head of Brokerage (50%) & Head of Property Acquisition (50%) at Bali Superhost (Kozystay Group). Start date: **October 1, 2026**. Building the brokerage from scratch.

Negotiation and comp/ESOP terms are tracked separately at `Personal/Career/BSH-Kozystay/` — this tracker covers the operational build only.

## File Index

- `Strategy/` — empty, next: extract Sections 1-10 of `Personal/Career/BSH-Kozystay/bsh-tuesday-meeting-draft.md` into a clean operating plan (positioning, competitive landscape, GTM channels, 90-day roadmap), stripped of negotiation framing
- `Hiring/adaptation-notes.md` — how Roberge's Sales Acceleration Formula hiring framework adapts to BSH. 6 open decisions, 6 direct transfers, 4 substitutions, scorecard mechanics. Raw capture, not the methodology. Next: resolve D1 (blocker) and D2, then write `hiring-methodology.md`
- `Hiring/` — job descriptions still to come: 2x Senior Brokerage Agent, Villa Sourcer, Property Acquisition Sourcer, Admin & Listings Coordinator. These come out of the methodology, not before it
- `Training/` — empty, next: adapt `Bali Exception/Training/` (7 files, deal-lifecycle sales training) for BSH's comp structure, listings, and team
- `Systems/crm-comparison-report.md` — **management-facing** CRM report, written for inclusion in the BSH brokerage business plan. 12 sections: price comparison, integrations, automations, workflow setup, website sync, email, Meta, WhatsApp and agent follow-up, real-estate-specific needs, full pros/cons for Zoho / GoHighLevel / Closio, recommendation with phased rollout, risks table. Contains the written Closio conflict disclosure in first person. Humanizer applied
- `Systems/crm-evaluation.md` — **internal** working evaluation, more detail and franker than the report above. Need brief, build-vs-buy, longlist of 17 with elimination reasons, 3 scored finalists, integration architecture, 10 open verification items, trial plan, phased rollout. Recommendation: Zoho CRM Professional ($184/mo at 8 seats), backup Apimo CRM AI+ (€139/mo flat). No decision made, trials not started
- `Systems/` — next: brokerage-website requirements spec, written against whichever CRM wins (the site reads listings from the CRM API, so the CRM decision comes first)

## Active Follow-ups

| Item | Status | Next step |
|---|---|---|
| **Non-solicit / non-compete status** | **BLOCKING hiring outreach** | Get BE contract reviewed and BSH non-compete pinned down in writing. Roberge's best sourcing tactic is relationship-based poaching of Bali agency brokers, and the signed BSH letter never mentions a non-compete (see `current-priorities.md` item 7) |
| Strategy doc extraction | Not started | Pull from `bsh-tuesday-meeting-draft.md` Sections 1-10. Note: Roberge's talent-pool protocol (`Hiring/adaptation-notes.md` T6) produces competitor comp and team intel as a by-product, feed it in here |
| Hiring — methodology | In progress | Resolve D1 and D2 in `Hiring/adaptation-notes.md`, then write `hiring-methodology.md` (trait sheets per role, assessment method per trait, interview sequence, scorecard, decision rule) |
| Hiring — job descriptions | Not started | Draft 4 JDs once the methodology defines the trait sheets |
| Training program adaptation | Not started | Resume `Bali Exception/Training/`, adapt to BSH |
| CRM selection | Research complete, decision pending | Run 2-week parallel trials of Zoho CRM Pro and Apimo on real data (5 scenarios in `Systems/crm-evaluation.md` Section 9). Close the 10 open items in Section 8 first, items 1, 3 and 9 are the ones that could change the decision |
| CRM — management approval | Not started | Pitch keeping HubSpot for management and adding a brokerage CRM. The argument is cost, not preference: HubSpot gates custom objects (so, property records) behind Enterprise, about $1,200/mo at 8 seats vs $184/mo for Zoho. See `Systems/crm-evaluation.md` Section 3 |
| CRM — Closio disclosure to BSH | Not started | Proactively tell BSH management that Closio exists, that Bali Exception owns it, that Matthieu has a prior commercial relationship with it, and that it was excluded for those reasons. Raise it before anyone asks. Reads badly if it surfaces later, buys credibility if disclosed first |
| CRM — commission formulas | Not started | Matthieu to write out exact formulas for brokerage profit share (20%), PA overriding commission (15%), and co-broke splits. Blocks building the commission module in any CRM |
| CRM — WhatsApp Coexistence check | Not started | Verify with a BSP whether Meta's Coexistence feature is available for Indonesian numbers. Determines whether agents keep their own WhatsApp linked to the CRM. Do not promise it to agents before this is confirmed |
| Brokerage website spec | Blocked on CRM choice | Site reads listings from the CRM API, so design the property schema first, then the site around it |

## Session Log

### 2026-10-11
- Researched the brokerage CRM. Output: `Systems/crm-evaluation.md`.
- Requirements gathered from Matthieu: keep HubSpot for management and run a brokerage CRM alongside with two-way sync on contacts and properties (managed villas get listed for sale, management clients become brokerage clients), buy not build (dev team is for glue, Bali Exception's in-house CRM is the counter-example), under 10 users and under $500/mo, live for day one, website and brand do not exist yet so the site gets built against the chosen CRM's API.
- **Two findings that did most of the elimination work.** First, the US real estate CRM category does not transfer: Follow Up Boss, BoldTrail, Lofty, Sierra, BoomTown, Top Producer and the rest are built on MLS and IDX feeds, which Indonesia does not have. Second, HubSpot's custom objects are Enterprise only (confirmed on HubSpot's own KB, still true April 2026), so a villa has no object to live in without roughly $1,200/mo at 8 seats plus onboarding. That is the argument for management, and it is a cost argument rather than a taste one.
- Attio ruled out on the same mechanism: custom objects are Pro only at $79/seat annual, about $632/mo at 8 seats. Good product, genuinely best-in-class MCP server, simply over budget for the object model needed. Would be viable at 4 seats.
- Finalists scored one per category as requested. Zoho CRM Professional and Apimo CRM AI+ **tied at 4.16**, GoHighLevel scored 2.90 (no property object, no commission tracking, poor data export, prepaid wallet halts service when negative).
- Tiebreak reasoning, worth keeping: Apimo wins the property model outright (purpose-built for international non-MLS markets, native matching, multi-currency, commission tracking, own website product, €139/mo flat at any seat count). Zoho wins the integration surface outright (official WhatsApp Cloud API included, official MCP server with a published Claude setup guide, native Slack and Google Drive, full REST API). Recommended Zoho because configuration work has a deadline and missing integration surface does not: Apimo had no HubSpot connector, no MCP, and unverified Slack and WhatsApp support, which is custom integration work against a smaller vendor's API for every stated requirement.
- **WhatsApp answer to the "each agent uses their own number" question:** Meta now has an official feature called Coexistence that runs the Business app and the Cloud API on the same number simultaneously with real-time mirroring and no loss of chat history. Rolling out gradually, eligibility depends on country, BSP and the number, so it needs verifying for Indonesian numbers before promising it to agents. Unofficial QR-bridge tools are the real ban risk and are ruled out.
- Closio Estate noted and set aside rather than scored: its ICP (Jakarta agencies, 5 to 50 agents) fits BSH's shape, but Matthieu has a commercial relationship with the product and that project's own disqualifier list excludes Bali and Lombok for competitive protection. Flagged for the conflict, raise separately if worth revisiting.
- Nothing bought, no trial started, no vendor contacted.

### 2026-10-12
- **Closio ruled out, and the earlier framing was wrong.** Yesterday's version logged it as a personal conflict of interest (Matthieu's prior go-to-market work on the product). Matthieu pointed out that Bali Exception owns Closio. That changes the category of problem entirely: the disqualifying issue is structural, not personal. BSH's entire brokerage book (leads, listings, seller contacts, negotiated prices, commission splits, agent activity) would sit in a database owned and administered by a direct competitor in the same geography, competing for the same villas and buyers. No confidentiality clause resolves that. Rewritten as `Systems/crm-evaluation.md` Section 3 Finding 3.
- Secondary reinforcing issues logged: procurement conflict if any residual financial interest exists, entanglement with the already-blocking non-compete question, and the possibility that BSH's geography is excluded from Closio's target market anyway per the `crm-sales` disqualifier list.
- **Action added:** disclose Closio to BSH management proactively rather than on request. Cost of exclusion is near zero (two viable alternatives), cost of a later discovery is a trust problem in a new role.
- Added `Systems/crm-evaluation.md` Section 5.1: pros and cons tables for Zoho, GoHighLevel and Closio against BSH's actual requirements, plus Apimo (requested three, added the fourth because omitting the recommended backup from a decision table would mislead). Closio's pros listed honestly rather than stacked, so the rejection survives them.
- Checked a Google CRM roundup Matthieu sent. Zoho was in it. Apimo was not, because these roundups are US-audience affiliate content and Zapier-sourced, and Apimo is a French vendor with no US affiliate program. Nothing in it changed the recommendation.
- Confirmed prior session's work was committed and pushed via workspace auto-sync (`8a82c44`). `Bali Superhost/` is not its own git repo, unlike Scale-Rise, olc-method and Bali Exception. Flagged as a deliberate choice to make before the folder fills with hiring and comp-adjacent material.

### 2026-10-08
- Started applying Roberge's *Sales Acceleration Formula* to BSH hiring. Wrote `Hiring/adaptation-notes.md`.
- **Process failure worth recording:** built a duplicate reference file at `.claude/knowledge/books/hr/sales-acceleration-formula-reference.md` from dictated notes over two sessions, while the full 21,500-word reference already existed at `.claude/knowledge/books/sales/sales-acceleration-formula-reference.md`. Cause: checked the knowledge base before Matthieu finished adding the book, then never re-checked across a week. The `sales/` shelf and the `ask-the-books` shelf table were both already correct. Duplicate deleted, adaptation notes rewritten against the real text, and three claims that were my own inference rather than the book's content were corrected (aggressiveness as a negative predictor: not in the book; prior sales experience as non-predictive: the real finding is context mismatch; step 4 needing n>5: the book says two or three hires is already enough for the judgment version).
- **Blocker raised:** non-solicit / non-compete status is undefined and Roberge's highest-yield sourcing tactic is relationship-based poaching of exactly the agencies Matthieu came from. Must be resolved before any outreach.
- Open: D2 (is Bali villa brokerage a commoditized or complex buyer context) determines whether work ethic or intelligence gets the heavier weight, and may split by role.

### 2026-09-09
- Folder created (`Strategy/`, `Hiring/`, `Training/`, `Systems/`, this tracker, `CLAUDE.md`). Kept separate from `Personal/Career/BSH-Kozystay/` (negotiation record stays there).
