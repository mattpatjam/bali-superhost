# Bali Superhost — Project Tracker

*Last updated: 2026-10-13 (existing BSH tool stack disclosed, both CRM docs revised, Zoho recommendation withdrawn)*

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
- `Context/README.md` + 2 files — interview context. Read-only copies of `bsh-brokerage-strategy-overview.html` (the "Building the Brokerage" strategy pitched to BSH, 7 Jul 2026) and `bsh-terms-recap.md` (terms as of 7 Aug 2026, pre-signature). Originals stay in `Personal/Career/BSH-Kozystay/` and remain source of truth. README flags the two deltas vs. the signed offer (title is Director of Business Development, ramp settled at 1.0x/2.0x/3.0x)
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

### 2026-10-12 (latest)
- **Closio pricing obtained and integrated into both docs.** Matthieu supplied `Closio-Pricing-Internal-EN.pdf`, Closio's internal sales reference (Oct 2026, "quote calculator v3"), held from the `Bali Exception/crm-sales` work. Grid: CRM Starter $99 (3 users), Pro $189 (5 users), +$25/extra user, Enterprise quote-only; AI agent priced by conversation pack ($129/200, $249/500, $399/900, $599/1,500, or $0.75 PAYG, where a conversation is one buyer thread per month regardless of message count); Closio Sites $79; 20% off annual.
- **BSH at 8 users works out to $393 to $592/mo ($314 to $474 annual), against Zoho at $184.** So 2 to 2.5x, hitting the $500 ceiling once the AI pack is sized honestly, and ~$1,167/mo at 25 agents since every seat above five adds $25. The pricing reinforces the existing rejection rather than changing it.
- **Confidentiality flagged, Matthieu directed inclusion anyway.** The PDF is marked INTERNAL / DO NOT PUBLISH and tells staff never to put CRM or AI numbers in public material. Raised three concerns: it is a confidentiality problem, it undercuts the Section 9 conflict disclosure that makes his procurement judgment credible, and he is the obvious source if a board document leaks. His non-compete position with Bali Exception is still unresolved. He said to proceed. Figures are in the BSH-facing report with their source stated, not presented as market research. Decision and reasoning logged in `crm-evaluation.md` decision log.
- One genuinely favourable finding: Closio's per-thread AI model ($0.40 to $0.65 per buyer thread) is a cleaner structure than Meta's per-message billing. Unstated whether Meta pass-through sits on top.

### 2026-10-12 (later)
- Wrote `Systems/crm-comparison-report.md`, the management-facing version for the BSH business plan. Separate file from the internal evaluation, because the audience is different: BSH management rather than Matthieu. Humanizer applied per CLAUDE.md.
- **Scraped closioestate.com and got real data for the first time.** Previous sessions had nothing verifiable. Findings: custom quote only (priced on team size + monthly AI conversation volume + onboarding), AI agent live ~24h after the WhatsApp number connects, most agencies running in under 7 days with onboarding included, modules cover leads/pipeline/contacts/owner listing requests/properties/calendar/messages/email broadcasts/documents/calculators/reports, AI agent qualifies on budget-purpose-timeline in 30+ languages and books viewings, lead capture across WhatsApp/Instagram/Facebook/portals/website/email with auto source-tagging and routing by language, iOS and Android apps, no website included (connects to an existing one). **Bali Exception is the first client logo on Closio's homepage**, so the relationship is publicly verifiable.
- **This makes Closio the closest functional fit of anything reviewed, and the report says so.** Stacking the deck against it would have made the rejection easy to attack. The rejection stands on governance alone, and is stronger for conceding the product quality.
- Closio gaps that are independent of the ownership issue: no published pricing (an unquantified line in a business plan), no public API docs (affects website sync, HubSpot sync, any future automation), no HubSpot/Slack/MCP, 5 client logos and 3 public reviews, and commission *calculators* which are not commission split *tracking*.
- Conflict disclosure rewritten into first person on the humanizer pass. Third person ("the author of this report") read as distancing on a page that names Matthieu at the top, which is the opposite of what a disclosure should do.
- Note: Matthieu wrote "Closeio" in the request. Assumed Closio Estate, consistent with the whole thread. Close.com is a different, unrelated US sales CRM if he actually meant that.

### 2026-10-12
- **Closio ruled out, and the earlier framing was wrong.** Yesterday's version logged it as a personal conflict of interest (Matthieu's prior go-to-market work on the product). Matthieu pointed out that Bali Exception owns Closio. That changes the category of problem entirely: the disqualifying issue is structural, not personal. BSH's entire brokerage book (leads, listings, seller contacts, negotiated prices, commission splits, agent activity) would sit in a database owned and administered by a direct competitor in the same geography, competing for the same villas and buyers. No confidentiality clause resolves that. Rewritten as `Systems/crm-evaluation.md` Section 3 Finding 3.
- Secondary reinforcing issues logged: procurement conflict if any residual financial interest exists, entanglement with the already-blocking non-compete question, and the possibility that BSH's geography is excluded from Closio's target market anyway per the `crm-sales` disqualifier list.
- **Action added:** disclose Closio to BSH management proactively rather than on request. Cost of exclusion is near zero (two viable alternatives), cost of a later discovery is a trust problem in a new role.
- Added `Systems/crm-evaluation.md` Section 5.1: pros and cons tables for Zoho, GoHighLevel and Closio against BSH's actual requirements, plus Apimo (requested three, added the fourth because omitting the recommended backup from a decision table would mislead). Closio's pros listed honestly rather than stacked, so the rejection survives them.
- Checked a Google CRM roundup Matthieu sent. Zoho was in it. Apimo was not, because these roundups are US-audience affiliate content and Zapier-sourced, and Apimo is a French vendor with no US affiliate program. Nothing in it changed the recommendation.
- Confirmed prior session's work was committed and pushed via workspace auto-sync (`8a82c44`). `Bali Superhost/` is not its own git repo, unlike Scale-Rise, olc-method and Bali Exception. Flagged as a deliberate choice to make before the folder fills with hiring and comp-adjacent material.

### 2026-10-12 (last)
- Added `Context/` with reference copies of two BSH-Kozystay files, per Matthieu's request: `bsh-brokerage-strategy-overview.html` and `bsh-terms-recap.md`. `Context/README.md` indexes them and marks them read-only snapshots.
- Partial exception to the CLAUDE.md scope note (negotiation record stays in `Personal/Career/`). The exception is written into both CLAUDE.md and the README, scoped to these two files only, with the originals named as source of truth. `bsh-terms-recap.md` is comp/ESOP material, so it now exists in two places.
- **Two stale facts found, not fixed:** `CLAUDE.md` line 3 and this tracker's Overview both say start date October 1, 2026 and title "Head of Brokerage (50%) & Head of Property Acquisition (50%)". Per `current-priorities.md` item 7 the actual start was October 5 and the signed title is Director of Business Development. Flagged for Matthieu rather than edited.

### 2026-10-08
- Started applying Roberge's *Sales Acceleration Formula* to BSH hiring. Wrote `Hiring/adaptation-notes.md`.
- **Process failure worth recording:** built a duplicate reference file at `.claude/knowledge/books/hr/sales-acceleration-formula-reference.md` from dictated notes over two sessions, while the full 21,500-word reference already existed at `.claude/knowledge/books/sales/sales-acceleration-formula-reference.md`. Cause: checked the knowledge base before Matthieu finished adding the book, then never re-checked across a week. The `sales/` shelf and the `ask-the-books` shelf table were both already correct. Duplicate deleted, adaptation notes rewritten against the real text, and three claims that were my own inference rather than the book's content were corrected (aggressiveness as a negative predictor: not in the book; prior sales experience as non-predictive: the real finding is context mismatch; step 4 needing n>5: the book says two or three hires is already enough for the judgment version).
- **Blocker raised:** non-solicit / non-compete status is undefined and Roberge's highest-yield sourcing tactic is relationship-based poaching of exactly the agencies Matthieu came from. Must be resolved before any outreach.
- Open: D2 (is Bali villa brokerage a commoditized or complex buyer context) determines whether work ethic or intelligence gets the heavier weight, and may split by role.

### 2026-09-09
- Folder created (`Strategy/`, `Hiring/`, `Training/`, `Systems/`, this tracker, `CLAUDE.md`). Kept separate from `Personal/Career/BSH-Kozystay/` (negotiation record stays there).
