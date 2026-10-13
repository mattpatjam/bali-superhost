# BSH Brokerage CRM Evaluation

*Created: 2026-10-11*
*Revised: 2026-10-13 (existing BSH tool stack disclosed, Odoo added as a finalist, recommendation downgraded to provisional)*
*Status: discussion document. Research complete, trials not started, no decision made and none to be made alone.*
*Owner: Matthieu*

> **Read this first.** The 2026-10-11 version of this document assumed the brokerage was starting from close to nothing, with HubSpot as the only incumbent system. That was wrong. BSH already runs five tools (Section 1.1), two of which overlap directly with what a CRM was being asked to do. The finalist set has changed, the recommendation is no longer a recommendation, and the remaining decision belongs to a group, not to one person. Section 8.1 sets out who needs to answer what.

---

## 1. Need Brief

**The problem:** the BSH brokerage is a new brand launching in weeks. It has no CRM, no website, and no listing database. It does, however, sit inside an existing BSH tool stack that was not accounted for in the first draft. See Section 1.1.

**What success looks like at 6 months:**
- Every lead, listing, and viewing lives in one system that agents actually use
- Changing a price or status in the CRM changes it on the website, with no double entry
- No follow-up gets missed because the system surfaces who is owed contact
- Management can see brokerage pipeline without the brokerage working inside HubSpot

**What success looks like at 2 years:**
- The system scales from under 10 users to 25 plus without a replatform
- Commission splits (brokerage profit share, PA overriding commission, co-broke) are calculated in the system, not in spreadsheets
- Listings syndicate to partner portals when partnerships land

**Hard constraints:**
- Under 10 users in year one
- Under $500 per month all in
- Live for day one of the brokerage, weeks away
- Indonesia has no MLS, so IDX-dependent products are disqualified
- Buy, do not build. Bali Exception proved an in-house CRM is a multi-year time sink. The dev team is for integration glue, not for building the core product.

**Required integrations:** revised 2026-10-13, see Section 1.1 and Section 7.
- Listing website (does not exist yet, so it gets built against whichever CRM wins)
- respond.io, inbound: new conversations and qualified leads become CRM records
- Odoo, outbound: closed deals and commission lines become invoices and journal entries
- HubSpot, two-way on contacts and deals, **if HubSpot survives the consolidation question in Section 7**
- Guesty, read-only: ADR and occupancy on managed villas, for buyer-facing ROI
- Slack, email, Google Drive
- Claude, via API or MCP, for follow-up drafting and task triage

**No longer a CRM requirement:** WhatsApp Cloud API on the brokerage number. respond.io already holds it. See Section 1.1 and Section 7.

**Stakeholders:** Matthieu (champion, not sole decision maker), BSH management (owns the existing stack and the budget, must approve any sixth tool), BSH finance (owns Odoo, and Odoo is now a candidate), BSH dev team (builds the glue and the website), the reservation and concierge team (owns respond.io day to day, and their inbox is the brokerage's lead capture point), 4 to 6 brokerage agents (the actual users, and the ones who decide whether this succeeds).

---

## 1.1 The Existing BSH Tool Stack

Disclosed 2026-10-13, after the first draft was written. This section exists because the original analysis was built on an incomplete picture and anyone reading the earlier conclusions needs to know what moved.

| Tool | What it does today | What it means for this decision |
|---|---|---|
| **respond.io** | Omnichannel inbox for the reservation and concierge team. WhatsApp, Facebook, Instagram, TikTok. Handles guest inquiries **and inbound property acquisition inquiries** | Removes WhatsApp from the CRM requirement entirely. Becomes the lead capture layer. Was the largest single input to Zoho's score |
| **HubSpot Starter, $15/seat/mo** | Pipeline tracking | Confirms the HubSpot elimination (Starter has no custom objects). Also makes HubSpot small enough to absorb rather than integrate with. See Section 7 |
| **Slack** | Internal communication | Unchanged. Native in Zoho, HubSpot and Odoo |
| **Guesty** | PMS for the managed portfolio | Not a CRM candidate. Is a data source worth connecting, see Section 7 |
| **Odoo** | Finance | **New finalist.** Odoo includes a CRM, and Odoo Custom includes Studio for custom models. See Section 4 and 5.1 |

**The three consequences:**

1. **WhatsApp is solved, and that was half of Zoho's winning margin.** The 2026-10-11 scorecard gave Zoho credit for including official WhatsApp Cloud API in the plan at no extra cost, and reserved budget headroom for a BSP. A phone number can only be registered to one WhatsApp Business Account at a time, so the same number cannot sit on both respond.io and a CRM. Either respond.io keeps the conversation layer, or the brokerage runs a separate second number. Keeping respond.io is obviously correct: it is already paid for, already staffed, and already receiving acquisition inquiries. Zoho's WhatsApp advantage is therefore no longer an advantage over anything, and Sections 7.1 and 7.2 are largely out of scope.

2. **Odoo should have been on the longlist and was not.** It is the only candidate that could calculate a commission and book the revenue in the same database. Section 5.1 covers it properly.

3. **Adding a sixth tool now needs a stronger case than adding a second one did.** The original framing was "keep HubSpot for management, add a brokerage CRM." The real framing is "BSH runs five systems, and the proposal is a sixth." That objection is legitimate and should be answered in writing before anything is proposed.

**respond.io cost note.** Pricing is per plan plus monthly active contacts: Starter $79/mo for 5 users with unlimited contacts, Growth $159/mo for 10 users and 1,000 monthly active contacts, extra users $12 to $20 each, higher contact tiers priced upward from there. Adding 4 to 6 brokerage agents is a real line item against the $500 ceiling, and it also mixes brokerage buyer threads into the same contact pool as guest inquiries. Verify which plan BSH holds, how many monthly active contacts it currently uses, and whether the brokerage should sit in a separate workspace rather than a shared one.

---

## 2. Build vs Buy

**Decision: buy.**

Rationale:
- A brokerage CRM is table stakes, not a differentiator. BSH wins on inventory access and agent quality, not on owning CRM code.
- Bali Exception's in-house CRM is the direct precedent. It took a very long time and is still underused.
- The brokerage opens in weeks. A build cannot be ready.
- The genuine custom need is the property data model, and that is configurable inside two of the three finalists without writing an application.

**What does get built in-house:**
- The listing website, consuming the CRM's API
- The HubSpot sync rules, if the off-the-shelf connector is not enough
- WhatsApp routing beyond what the CRM provides natively

---

## 3. Why Most "Real Estate CRMs" Are Disqualified

Two findings that eliminate most of the obvious candidates.

**Finding 1: the US real estate CRM category does not apply here.**

Follow Up Boss ($69/user), BoldTrail, Lofty, Sierra, BoomTown, Top Producer ($179/user), CINC, Real Geeks, iHomefinder and Wise Agent are all built around MLS and IDX feeds. Their core value is ingesting a regional MLS, running IDX search on your site, and routing Zillow and Realtor.com leads. Indonesia has none of that. Strip the IDX layer out and what remains is a generic pipeline CRM with weaker APIs and worse integrations than tools costing a third as much. Several of them also refuse to publish pricing, which means a quote cycle the launch timeline cannot absorb.

Rex Software deserves a note as the closest near-miss. It is built for Australia, New Zealand and the UK, which are non-MLS markets, so the property model is right and it has a public API. It is quote-only, its portal integrations are AU-specific, and its support timezone is a plus for Bali. Worth a quote if the three finalists disappoint, not worth blocking the decision on.

**Finding 2: HubSpot structurally cannot hold a property record at a price BSH will pay.**

*Clarified 2026-10-13. BSH holds HubSpot Starter at $15/seat/mo, roughly $120/mo at 8 seats. The figures below describe the tiers that do have custom objects, not what BSH currently pays. Stating this plainly matters: anyone at BSH who knows their own bill will read an unqualified "$1,200/mo" as an error and discount the rest of this document.*

HubSpot's custom objects are Enterprise only, confirmed on HubSpot's own knowledge base and still true as of April 2026. Every tier below it, Starter and Professional included, is limited to the four standard objects: contacts, companies, deals, tickets. There is no property object, and a villa is not a company or a deal. **BSH's Starter tier therefore cannot hold a property record, and neither could an upgrade to Professional.**

The workarounds are both bad:
- Model each villa as a Company record. Breaks reporting, breaks buyer matching, and corrupts management's own company data in the shared portal.
- Upgrade to Sales Hub Enterprise. Roughly $150 per seat per month, so about $1,200 per month at 8 seats, plus a required one-time onboarding fee. That is more than twice the entire CRM budget, to get an object the €139 per month option has natively.

**The argument to take to management.** It is not a preference or a taste question. The only HubSpot tier that can hold a villa costs roughly ten times what BSH pays today, and purpose-built alternatives include the object natively. So HubSpot is out as the brokerage system of record on structural grounds, at any tier BSH would realistically buy.

**What the Starter tier does change.** The first draft treated HubSpot as an entrenched platform the brokerage had to integrate with. At $15/seat it is a lightweight pipeline tracker holding contacts and deals, with no custom objects to migrate. That makes retiring it genuinely cheaper than syncing to it. See Section 7, where this is now an open recommendation rather than an assumption.

**Finding 3: Closio is disqualified because a direct competitor owns it.**

Closio Estate is owned by Bali Exception, Matthieu's former employer and a direct BSH competitor in the same geography, for the same villas, the same sellers, and the same buyers.

Adopting it would put BSH's entire brokerage book inside a database that a competitor owns and whose backend their staff administers: every lead, every listing, every seller contact, every negotiated price, every commission split, every agent's activity. No contractual confidentiality clause resolves this. It asks a competitor to hold your book and promise not to read it.

That alone ends it. Three secondary issues reinforce it:

- **Procurement conflict.** Matthieu did go-to-market work for Closio through `Bali Exception/crm-sales`. Any residual revenue share, referral arrangement, equity, or unfinished engagement makes him a buyer with a financial interest in the vendor he is selecting.
- **Non-compete entanglement.** Non-solicit and non-compete status with Bali Exception is already an open blocking item for BSH hiring. Becoming a paying customer of BE's product while recruiting from Bali agencies and competing for their listings hands BE a commercial lever at the worst possible moment.
- **It may not be available anyway.** The `crm-sales` disqualifier list excludes Bali, Lombok, Sumbawa and the Gilis from Closio's target market for competitive protection. BSH's geography may already be off-limits.

**Action: rule it out, and disclose it proactively to BSH management** rather than waiting to be asked. State that Closio exists, that BE owns it, that there is a prior commercial relationship, and that it was excluded for those reasons. The cost of exclusion is near zero because two viable alternatives exist. The cost of being wrong is leaking competitive intelligence to a rival, which is not reversible.

The only conditions under which this would be worth reopening: BE's ownership is genuinely passive and arm's length, Matthieu holds zero financial interest, and BSH management approves in writing. Even then the competitive data exposure remains and the upside over Zoho is marginal.

---

## 4. Shortlist

Longlist considered: HubSpot (Pro and Enterprise), Attio, Pipedrive, Zoho CRM, Zoho One, GoHighLevel, Apimo, Rex Software, Propertybase/Lone Wolf, Closio Estate, Follow Up Boss, BoldTrail, Lofty, Top Producer, Wise Agent, Real Geeks, EspoCRM.

**Eliminated, with reasons:**

| Tool | Why out |
|---|---|
| HubSpot Starter (what BSH holds), Pro, Enterprise | No custom objects below Enterprise, so no property record at Starter or Pro. Enterprise is about $1,200/mo at 8 seats plus onboarding. See Section 3, Finding 2. |
| Attio | Custom objects are Pro and Enterprise only, per Attio's own docs. Pro is $79/seat annual, so about $632/mo at 8 seats. Plus is capped at 5 total objects anyway, including the standard three. Excellent MCP server and API, genuinely good product, simply over budget for the object model needed. Revisit if the team stays at 4 seats. |
| Pipedrive | Cheapest credible option at $14 to $49/seat, but it supports fewer record types than HubSpot or Attio. No real property object. Lead capture and web tracking are priced as separate add-ons. Pipeline tool, not a property system. |
| Follow Up Boss, BoldTrail, Lofty, Top Producer, CINC, Real Geeks, iHomefinder, Wise Agent | MLS and IDX dependent. See Section 3, Finding 1. |
| Propertybase / Lone Wolf | Salesforce-based, enterprise pricing and implementation cycle. Wrong scale and wrong timeline. |
| Rex Software | Right market model (non-MLS), public API, quote-only pricing, AU-specific portals. Hold as backup. |
| Closio Estate | **Ruled out on competitive exposure. See Section 3, Finding 3.** |

**Finalists, revised 2026-10-13:**

1. **Zoho CRM Professional** ($23/seat/mo annual, about $184/mo at 8 seats), the flexible CRM shaped into a real estate system
2. **Apimo CRM AI+** (€139/mo flat, about $150/mo), the opinionated real estate product built for international non-MLS markets
3. **Odoo CRM, Custom plan** (Indonesia tier, roughly $15/user/mo, about $120/mo at 8 seats), **added 2026-10-13**, the incumbent finance platform extended into brokerage
4. **GoHighLevel Unlimited** ($297/mo flat), retained for the record only, see the verdict in Section 5

**Why Odoo is now on the list.** BSH already runs Odoo for finance. Odoo's subscription includes every app, so CRM, Sales, Documents and Accounting sit in one database, and the Custom plan includes Odoo Studio for building custom models, which is how the property object would be created. Indonesia tier pricing is roughly $15/user/mo on Custom (around Rp255,000), so eight seats is near $120/mo, and existing finance users are already licensed. Most importantly, it is the only candidate that can calculate a commission split and book the resulting invoice in the same system, which is the stated 180-day success criterion.

**Why GoHighLevel is now redundant as well as unsuitable.** Its strongest feature was the conversations and nurture layer. respond.io already does that across more channels and is already staffed. GHL was eliminated as a system of record on 2026-10-11, and the existing stack removes its consolation prize too.

---

## 5. Scorecard

Weights adjusted from the standard rubric for this situation. Technical fit is raised to 25% because the website does not exist yet and will be built against the CRM's API, making API quality a launch dependency rather than a nice-to-have. Security is lowered to 5% because no regulated or health data is involved.

**Rescored 2026-10-13.** WhatsApp has been removed from the technical fit criterion, because respond.io now provides it for every candidate equally. That drops Zoho from 5.0 to 4.5 on technical fit, raises Apimo from 3.0 to 3.25, and lowers GoHighLevel from 3.5 to 3.25. Odoo is scored for the first time. The original scores are kept in brackets where they changed.

| Dimension | Weight | Zoho CRM Pro | Apimo CRM AI+ | Odoo Custom | GoHighLevel |
|---|---|---|---|---|---|
| Functional fit (property model, matching, commissions) | 35% | 3.5 | 5.0 | 4.0 | 2.0 |
| Technical fit (API, website, Claude, Slack, Drive) | 25% | 4.5 *(was 5.0)* | 3.25 *(was 3.0)* | 4.0 | 3.25 *(was 3.5)* |
| Operational fit (time to launch, admin burden) | 10% | 3.0 | 4.5 | 2.5 | 3.5 |
| Cost at 8 seats | 10% | 5.0 | 5.0 | 5.0 | 4.0 |
| Vendor health | 8% | 5.0 | 4.0 | 4.5 | 3.5 |
| Lock-in risk / data portability | 7% | 4.0 | 3.0 | 4.5 | 2.0 |
| Security and compliance | 5% | 4.0 | 3.5 | 4.0 | 3.0 |
| **Weighted total** | **100%** | **4.03** *(was 4.16)* | **4.22** *(was 4.16)* | **4.03** | **2.83** *(was 2.90)* |

**The result is now a three-way near-tie, and that is the honest finding.** Apimo 4.22, Zoho 4.03, Odoo 4.03. A 0.19 spread across three candidates is noise, not a ranking. Anyone presenting this as "the numbers chose X" is misreading it.

**Two caveats on the numbers themselves, both of which matter more than the totals:**

- **The scorecard understates Odoo.** Commission calculation is one component of a 35% functional-fit score, sitting alongside the property model and buyer matching where Odoo is average. It does not capture that Odoo is the only candidate where a commission calculation and the invoice that follows it live in the same database, with no sync to build or maintain. If commission accuracy is weighted as its own dimension, Odoo leads.
- **The scorecard understates Apimo's integration risk.** Apimo scores well on functional fit because the property model is native. But its connector gaps are now gaps against respond.io and Odoo rather than against WhatsApp and HubSpot, and those are the two systems the brokerage would actually depend on daily. The 3.25 may still be generous.

GoHighLevel loses on the thing a brokerage needs most and is no longer a serious entry. It is retained below for the record.

### Per-finalist detail

**Zoho CRM Professional, $23/seat/mo annual ($184/mo at 8 seats)**

Strengths:
- Custom modules let the dev team model Properties, Viewings, and Commission Splits exactly as Bali works: SHM, HGB, Hak Pakai, leasehold with years remaining, IDR and USD dual pricing, land size in are and sqm. Nothing has to be bent to fit a US convention.
- ~~Official WhatsApp Cloud API support is built into the paid plans, not an add-on. Cheapest full CRM with official API messaging included.~~ *Struck 2026-10-13: respond.io holds the WhatsApp numbers, so this is no longer a differentiator. It would only matter if the brokerage ran a separate second number outside respond.io, which is not the proposal.*
- Official Zoho MCP server with a published Claude setup guide. This is the single clearest differentiator for the AI requirement. Claude can read and write CRM records directly rather than through a brittle middle layer.
- Native Slack integration and native Google Drive integration, including attaching Drive files to custom module records.
- Full REST API, webhooks, and Zoho Flow for the HubSpot sync.
- Zoho has been profitable and independent for over 25 years. No funding-runway risk.

Weaknesses:
- Everything above is a capability, not a configuration. Someone has to build the property module, the matching logic, and the commission calculations. Estimate 2 to 4 weeks of focused work.
- Buyer-to-listing matching is not native. It gets built with workflow rules and custom functions.
- The admin surface is dated and sprawling. Agent adoption depends on how well the layouts are designed.
- Professional caps custom modules and custom fields per module. Needs verification against the planned property schema (Section 8).
- No Indonesian data center. Pick Australia or India.

**Apimo CRM AI+, €139/mo flat (about $150/mo, any team size)**

Strengths:
- Purpose-built for international real estate agencies, and explicitly multilingual, multi-currency, and adapted to local market regulations. Built for exactly the non-MLS, cross-border, foreign-buyer situation Bali is.
- Property and client matching is native, not built. So is commission tracking, document storage with e-signature, a client portal, lead capture and distribution, and listing management.
- Flat rate regardless of seat count. Going from 6 agents to 20 costs nothing extra, which is unusual and valuable.
- Has its own website product, SEO-oriented, with the CRM as the listing source of truth. Solves the website requirement in one purchase instead of a custom build.
- Public API and claims 500 plus partner integrations.

Weaknesses:
- No HubSpot connector found. The sync would be custom work against both APIs, or a middleware layer like Whalesync or Make.
- No MCP server and no published Claude path. The AI requirement would run through the API with custom work, or through the "AI" features Apimo markets, which were not verifiable from public material.
- WhatsApp and Slack support both unverified. Treat as absent until a demo proves otherwise.
- French company, European timezone. Support responsiveness from Bali is unknown.
- Little public evidence of Asian clients. Needs a reference call in or near the region.
- Using Apimo's website product is the fastest path and also the deepest lock-in. The listings and the site live together.

**GoHighLevel Unlimited, $297/mo flat plus $10/mo WhatsApp add-on (about $307/mo)**

Strengths:
- Unlimited users and unlimited contacts at a flat rate. At 8 seats that is already cheaper per head than most per-seat options, and it never gets worse.
- Website and funnel builder, two-way messaging, booking calendar, pipeline, and automation all in one subscription. For lead nurture and speed-to-first-response it is genuinely strong.
- AI features are deeply integrated rather than bolted on.
- API access, needed for the website integration, is on the Unlimited tier. Starter at $97 does not include it, so Starter is not an option here.

Weaknesses:
- No real property object. Everything is a contact and an opportunity. Buyer-to-listing matching, title types, and dual-currency pricing have nowhere natural to live.
- No commission split tracking.
- Data export is the known weak point of the platform. Snapshots are proprietary. If this fails in year two, migration is painful.
- Built for US local service businesses and marketing agencies. Reviews consistently describe a difficult first month because the dashboard exposes everything at once with no guided order.
- Usage runs off a prepaid wallet, and a negative balance halts services. That is an operational risk for a brokerage whose WhatsApp line is its lifeline.

**Verdict:** GoHighLevel is the wrong shape. It is a lead-nurture machine being asked to be a property database. Keep it in mind as a possible marketing layer later if lead generation becomes the bottleneck, but it is not the brokerage's system of record.

---

## 5.1 Pros and Cons Against BSH's Actual Requirements

Scored against what BSH specifically needs, not against generic CRM criteria. Apimo is included because it is the recommended backup and a decision table that omits the number two option is misleading.

### Zoho CRM Professional ($184/mo at 8 seats)

| Pros | Cons |
|---|---|
| Custom modules model the property exactly as Bali works: SHM, HGB, Hak Pakai, leasehold with years remaining, IDR and USD dual pricing, land in are and sqm | None of that exists on day one. It has to be built. Estimate 2 to 4 weeks of dev work before agents can use it |
| ~~Official WhatsApp Cloud API included in the plan~~ *(struck 2026-10-13, respond.io holds the numbers, no longer a differentiator)* | Buyer-to-listing matching is not native. Built with workflow rules and custom functions |
| Official MCP server with a published Claude setup guide. Claude reads and writes records directly, no brittle middle layer. The only finalist that answers the AI requirement properly | Admin interface is dated and sprawling. Agent adoption depends entirely on how well the layouts get designed |
| Native Slack and native Google Drive integrations, including attaching Drive files to custom module records | Professional caps custom modules and fields per module. Needs checking against the property schema before committing (open item 1) |
| Full REST API and webhooks, so the website can be built against it cleanly | Listing photo handling is unproven at 25 to 40 images per villa. May need WorkDrive or Drive alongside (open item 2) |
| HubSpot sync available three ways: Zoho Flow, Whalesync or Stacksync, HubSpot Operations Hub | No Indonesian data center. Australia or India has to be chosen deliberately |
| Independent and profitable for 25+ years. No funding runway risk, no acquisition risk | Configuration knowledge becomes Zoho-specific. Portable data, less portable setup |
| $184/mo leaves over $300/mo of budget free for sync tooling and reserve | Per-seat pricing, so cost scales with headcount. At 25 agents this is $575/mo |
| | **No native respond.io connector.** Zapier or Integrately only, so the lead capture handoff is glue the dev team builds and maintains (added 2026-10-13) |
| | **Commission lives in a different system from finance.** Calculating a split in Zoho and booking it in Odoo is a second integration to build (added 2026-10-13) |

### Odoo CRM, Custom plan (about $120/mo at 8 seats, Indonesia tier)

*Added 2026-10-13. Conditional on BSH running the Custom plan or self-hosted Enterprise. If BSH is on Odoo Standard, there is no Studio and no external API, and Odoo is out.*

| Pros | Cons |
|---|---|
| **Already in the stack and already paid for on the finance side.** Not a sixth tool. The only candidate that reduces tool count rather than adding to it | **Nobody has confirmed which plan BSH holds.** Standard has no Studio and no external API access, which eliminates Odoo outright. This is the single blocking question |
| **Commission and finance in one database.** Brokerage profit share at 20%, PA overriding commission at 15% and co-broke splits calculate in the same system that issues the invoice and books the revenue. No sync, no reconciliation, no spreadsheet | Property schema still has to be built in Studio. Same 2 to 4 weeks as Zoho, not less. Odoo has no native real estate object |
| Odoo Studio builds custom models no-code, so the property object can carry SHM, HGB, Hak Pakai, lease years remaining, dual IDR and USD pricing, land in are and sqm | **Highest agent adoption risk of any finalist.** Odoo's interface is built for operations and finance staff, not for salespeople working from a phone between viewings. This is the main reason it scores 2.5 on operational fit |
| Indonesia tier pricing is roughly $15/user/mo on Custom. Cheapest finalist, and finance users are already licensed | No official MCP server. Claude access would be via Odoo's JSON-RPC or XML-RPC API, or a community MCP server. Zoho keeps a real edge here |
| All apps included in one subscription: CRM, Sales, Documents, Accounting, Website, Sign. The listing site could be built in Odoo Website or against the API | Buyer-to-listing matching is not native and would be built, same as Zoho |
| Full external API on Custom, plus webhooks, so the listing website can be built against it cleanly | Multi-company configuration needs care if brokerage and management are separate legal entities. Available on Custom, but it is setup work and a permissions question |
| Open source core, so data and schema portability are the best of any finalist. Lowest lock-in risk scored | No native respond.io connector. Zapier or Integrately only, same glue problem as Zoho |
| Management already knows the tool, so there is no second vendor relationship, no second contract, no second security review | Per-seat pricing, so cost scales with headcount, though from a much lower base than Zoho |

### GoHighLevel Unlimited ($307/mo including WhatsApp add-on)

| Pros | Cons |
|---|---|
| Flat rate with unlimited users and unlimited contacts. Going from 8 agents to 25 costs nothing extra | **No property object.** Everything is a contact and an opportunity. Villas, title types and dual-currency pricing have nowhere natural to live. This is disqualifying for a brokerage |
| Website and funnel builder included, so the site requirement is partly solved in the same subscription | No commission split tracking. Profit share, PA overriding commission and co-broke would stay in spreadsheets |
| Strongest of the three on lead nurture and speed-to-first-response. Missed-call text-back, booking calendar, automated reminders | No buyer-to-listing matching, because there are no listings to match against |
| AI features are deeply integrated rather than bolted on | No official MCP server. Claude integration would be custom work against API v2 |
| Two-way messaging, pipeline, booking and automation all in one place | Data export is the platform's known weak point. Snapshots are proprietary. Painful to leave in year two |
| API access on the Unlimited tier supports a custom website build | Usage runs off a prepaid wallet and a negative balance halts services. For a brokerage whose WhatsApp line is its lifeline, that is an operational risk |
| 14-day free trial on every plan | Built for US local service businesses and marketing agencies. Reviews consistently describe a hard first month |
| | HubSpot sync only via Zapier or Make, no native connector |

**Verdict:** wrong shape. A lead-nurture machine being asked to be a property database. Worth revisiting later as a marketing layer on top of a real CRM if lead generation becomes the bottleneck, never as the system of record.

### Closio Estate (ruled out, see Section 3 Finding 3)

Listed honestly, because the pros are real and the rejection should survive them.

**Pricing obtained 2026-10-12.** From `Closio-Pricing-Internal-EN.pdf`, the vendor's internal sales reference dated Oct 2026 ("quote calculator v3"), which Matthieu holds from the `Bali Exception/crm-sales` go-to-market work. The document is marked INTERNAL, DO NOT PUBLISH, and instructs staff never to put CRM or AI numbers in public material. Matthieu was advised of the confidentiality and disclosure risks and directed on 2026-10-12 to include the figures anyway. They appear in the BSH-facing report with their source stated, rather than as market research.

| Line | Price (monthly, USD) |
|---|---|
| CRM Starter, up to 3 users | $99 |
| CRM Pro, up to 5 users ("most agencies land here") | $189 |
| CRM Enterprise, unlimited, multi-branch, SLA | Quote only, never public |
| Additional user, Starter or Pro | $25 each |
| AI agent, 200 conversations | $129 ($0.645 per thread) |
| AI agent, 500 conversations | $249 ($0.498) |
| AI agent, 900 conversations | $399 ($0.443) |
| AI agent, 1,500 conversations | $599 ($0.399) |
| AI agent, pay as you go | $0.75 per conversation |
| Closio Sites (website synced to CRM, WhatsApp button, no setup fee) | $79 |
| Annual billing | 20% off every recurring line |

A conversation means one buyer thread in a month regardless of message count. Overage above a pack bills at the PAYG rate. Grid is USD base global; IDR quotes are USD times a default rate of 16,500, with Indonesian agencies quoted off a separate IDR grid. Sites is the only price Closio publishes openly.

**BSH scenario at 8 users:** CRM Pro $189 plus 3 extra seats at $25 is $264. AI pack at roughly 200 leads/month is $129 (no headroom) or $249 (safe). Sites $79 if used.

| Configuration | Monthly | Annual billing |
|---|---|---|
| Pro + AI 200, no Sites | $393 | $314 |
| Pro + AI 200 + Sites | $472 | $378 |
| Pro + AI 500 + Sites | $592 | $474 |
| At 25 users (Pro + 20 extra + AI 900 + Sites) | $1,167 | $934 |

**Conclusion: the pricing strengthens the existing rejection and changes nothing.** Closio runs 2 to 2.5x Zoho ($184) and hits the $500 ceiling once the AI pack is sized honestly. It also scales badly, since every seat above five adds $25, against GoHighLevel's flat $307 at any headcount. The one genuinely favourable element is the per-thread AI model at $0.40 to $0.65 per buyer thread, which compares well with Meta's per-message billing, though whether Meta pass-through sits on top of Closio's packs is unstated.

| Pros | Cons |
|---|---|
| Built for Southeast Asia, with a stated Bali presence. The only candidate not designed around a Western market | **Owned by Bali Exception, a direct BSH competitor.** BSH's entire book would sit in a competitor-administered database. Not fixable by contract. Disqualifying on its own |
| Per-thread AI pricing ($0.40 to $0.65) is a cleaner model than per-message billing, and bundles the AI agent rather than charging a platform fee for it | 2 to 2.5x the cost of Zoho, at the $500 ceiling once the AI pack is realistic, and $1,167/mo at 25 agents |
| Native WhatsApp, Instagram and portal inquiry handling, which is exactly how leads arrive in Bali | Procurement conflict. Matthieu did go-to-market work for the product and may hold a residual financial interest |
| Likely handles IDR and Indonesian title types natively, without configuration | Entangles the open non-solicit and non-compete question with Bali Exception at the worst moment |
| Local timezone support, unlike Apimo (Europe) or Zoho (India and Australia) | BSH's geography may already be excluded from Closio's target market for competitive protection. Possibly moot |
| Matthieu already knows the product and the team, so evaluation would be fast | Exit risk. If the BE relationship sours, the system of record is controlled by someone with reason to make it difficult |
| ICP of 5 to 50 agent agencies matches BSH's shape | No public pricing, no public API documentation, no published property schema. Depth unverified |
| | Small vendor. Thin public evidence of customers, financial health, or security posture |
| | No MCP server, so the Claude requirement would be custom work |

**Verdict:** the product fit may well be good. It does not matter. The competitive exposure is structural, severe, and not reversible, and two alternatives exist that carry none of it.

### Apimo CRM AI+ (€139/mo flat, recommended backup)

| Pros | Cons |
|---|---|
| Purpose-built for international non-MLS real estate. Multilingual, multi-currency, adapted to local market regulations. Exactly the cross-border foreign-buyer situation Bali is | No HubSpot connector found. The sync would be custom work against both APIs or a middleware layer |
| Property and client matching is native, not built. So is commission tracking, e-signature, client portal, lead capture and distribution | No MCP server and no published Claude path. The AI requirement would be custom work |
| Flat rate at any seat count. 8 agents or 25 costs the same | WhatsApp and Slack support both unverified. Treat as absent until a demo proves otherwise |
| Its own SEO-oriented website product with the CRM as listing source of truth. Solves the site requirement without a custom build | Using their website product is the fastest path and also the deepest lock-in. Listings and site live together |
| Fastest of the four to a working system. Little configuration needed | French company, European timezone. Support responsiveness from Bali unknown |
| Public API and 500+ claimed partner integrations | Little public evidence of Asian clients. Needs a reference call in or near the region |

---

## 6. Position, Not Recommendation

*Rewritten 2026-10-13. The previous version recommended Zoho with Apimo as backup. That recommendation rested on two things the existing stack has removed: Zoho's included WhatsApp Cloud API, and the assumption that HubSpot was the only incumbent. It is withdrawn, not reversed. There is no recommendation in this document until Section 8.1 is answered.*

**Where it actually stands: three candidates, a 0.19 scorecard spread, and one blocking unknown.**

Each finalist now wins on a different axis, and which axis matters most is a judgement call that belongs to the group, not to one person reading vendor pages.

| Candidate | Wins on | Loses on | Pick it if |
|---|---|---|---|
| **Odoo Custom** | Commission and finance in one database. No sixth tool. Cheapest. Best data portability | Agent adoption risk. No MCP. Property model has to be built | The group's priority is one fewer system and commissions that reconcile themselves, and agents will be trained properly |
| **Apimo CRM AI+** | Property model and buyer matching native on day one. Fastest to a working system. Flat rate at any headcount | Thinnest integration surface, now against respond.io and Odoo. Lock-in if the website product is used. No Asian reference clients found | The group's priority is launching in weeks with no build, and accepting glue work later |
| **Zoho CRM Pro** | Best integration surface. Only candidate with an official MCP server and documented Claude setup. Deluge as an escape hatch | Property model has to be built. Commission sits apart from finance. Dated admin UI | The group's priority is the Claude workflows and long-term flexibility, and the dev team has capacity |

**The honest summary for the discussion:** Apimo is the fastest to working, Odoo is the cleanest architecture and the cheapest, Zoho is the most flexible and the best Claude story. Nothing in the research separates them decisively, so the decision should turn on what BSH actually values most, which is a conversation that has not happened yet.

**What should not be reopened.** The eliminations in Sections 3 and 4 are structural, not preference-based, and the new information does not touch them: no MLS in Indonesia, no custom objects below HubSpot Enterprise, and Closio sits inside a direct competitor. Those stay closed.

**Budget position.** All three finalists sit well inside the $500/mo ceiling: Odoo about $120, Apimo about $150, Zoho about $184. The ceiling is no longer a constraint on the CRM choice. It does now need to absorb incremental respond.io seats and contact tiers, which the first draft did not account for.

---

## 7. Integration Architecture

*Rewritten 2026-10-13. The previous version assumed the CRM would own WhatsApp and sync to HubSpot. Both assumptions are gone.*

**The shape of it: each system keeps the job it already does well, and the CRM is given exactly one job.**

```
respond.io          →   CRM            →   Odoo (finance)
(conversations)         (records)          (invoice, revenue)
WA/FB/IG/TikTok         property           commission booked
guest + acquisition     deal, viewing
                        commission calc
                            ↓        ↑
                        website    Guesty
                        (listings) (ADR, occupancy)
                            ↓
                        Slack, Drive, Claude
```

**respond.io, the conversation layer and the capture point**
- respond.io keeps every channel and every number. The CRM never touches WhatsApp. This is the single biggest change from the first draft.
- A phone number can only be registered to one WhatsApp Business Account at a time, so this is not a preference, it is a constraint. The same number cannot be on respond.io and a CRM simultaneously.
- The handoff to build: when a conversation is qualified as a brokerage lead, it becomes a CRM contact and deal, with the respond.io thread link stored on the record. Direction is respond.io to CRM for creation, CRM to respond.io for context (budget, area, stage) so whoever picks up the chat can see it.
- **None of the three finalists has a native respond.io connector.** HubSpot does, which is worth noting honestly, but HubSpot cannot hold a property. For Zoho, Apimo and Odoo the path is respond.io webhooks plus the CRM's API, or Zapier or Integrately as an interim. Budget dev time for this in Phase 1, not Phase 3. It is the lead capture path, so it cannot be late.
- **Open question for the reservation team, not for IT:** brokerage buyer threads and guest inquiries currently share one inbox and one contact pool. Decide whether the brokerage gets its own workspace, its own channels, or just its own tags. This affects respond.io's monthly active contact tier and therefore the bill.

**Odoo, the finance endpoint**
- Closed deal produces a commission calculation, which produces an invoice and a journal entry. If Odoo wins the CRM decision, this is internal and free. If Zoho or Apimo wins, this is a second integration to build and maintain.
- That asymmetry is the strongest single argument for Odoo and it is not fully reflected in the scorecard. Section 5 says so explicitly.

**HubSpot, and whether it survives**
- *Changed 2026-10-13. Previously framed as a required two-way sync. It is now an open recommendation to retire it.*
- **Option A, consolidate.** Migrate management's pipeline into the chosen CRM and drop HubSpot. At Starter tier, with no custom objects and only contacts and deals to move, this is a small migration. It deletes the two-way sync build, the $45/mo sync tooling, and the record-ownership rules below, which were going to be a standing source of conflict between two systems fighting over the same phone number as a key.
- **Option B, keep it.** Two honest arguments: it is management's tool and the politics of removing it may cost more than the sync does, and respond.io's native HubSpot connector already works today whereas the respond.io to Zoho/Apimo/Odoo path has to be built.
- **Suggested position:** propose Option A, but do not make it a condition of the CRM decision. Decide the CRM on the property and commission model, prove the new system in Phase 1, then propose consolidation separately. Trying to take HubSpot off management in week two is how the whole thing loses approval.
- If Option B is chosen, the ownership rule still has to be agreed before the sync is switched on: management owns the record for management clients, the brokerage owns it for brokerage-sourced leads, matched on phone number, owning side wins on conflict.

**Guesty, read-only, new in this draft**
- Not a CRM candidate, but an asset the first draft missed. Guesty's Open API exposes listings, reservations and journal entries.
- Use case: pull real ADR and occupancy from the managed portfolio into buyer-facing ROI numbers. A brokerage selling income-producing villas that can show actual performance data from its own management arm, rather than projections, has something most Bali agencies cannot produce.
- Low priority for launch, high value once listings are selling on investment returns. Phase 3 or later.

**Website (the listing site)**
- Unchanged. The CRM is the single source of truth for listings. Nothing is ever entered on the website.
- Built after the CRM is chosen, reading from the CRM API, with webhooks triggering a rebuild or cache invalidation when a property record changes.
- Design the property schema first, then the site around it. Not the reverse.

**Claude**
- Zoho is the only finalist with an official MCP server and a published Claude setup guide. Odoo would run through JSON-RPC or a community MCP server. Apimo has no published path.
- First use cases regardless of which CRM wins: a daily "who is owed a follow-up" brief, drafting follow-ups from record history for a human to send through respond.io, and triaging new inbound leads against live inventory.
- Note the draft-and-review rule applies: Claude drafts the follow-up, a person sends it. Nothing goes to a lead automatically.

**Slack and Google Drive**
- Slack is native in all three finalists. Deal and listing alerts into a channel.
- Drive for mandates, title documents and photos attached to property records. Check whether listing photos belong in Drive or in the CRM's own file store. 20 to 40 photos per villa is a volume problem most CRMs handle badly.

---

## 7.1 WhatsApp Messaging Economics (changed 1 October 2026)

> **Scope changed 2026-10-13.** This section was written on the assumption that the CRM would hold the WhatsApp numbers. respond.io holds them, so none of this is a CRM selection criterion any more. **It is still live and still matters**, because Meta's per-message charges are passed through by every BSP including respond.io, and the cost of an AI qualifying bot is unchanged by which inbox sends it. Read this as respond.io operating economics, not as CRM evaluation. The questions move from "which CRM" to the reservation team and whoever administers respond.io.

Meta changed WhatsApp pricing eleven days before this was written. Most vendor pages and blog posts still describe the old model. Anything online saying "service replies are free" is now wrong.

**The three rules that govern everything:**

- **24-hour customer service window.** A client message opens a 24-hour timer and each new client message resets it. Inside the window, free-form messages of any kind, including AI-generated replies. Outside it, only pre-approved templates.
- **Templates require Meta approval and explicit opt-in.** You cannot write a drip sequence and schedule it. Every business-initiated message is reviewed before it can send. "They gave us their number once" is not opt-in.
- **Quality rating throttles sending.** Spam-shaped sequences drop the rating and Meta restricts the number. A restricted brokerage number in launch month would be severe.

**What changed on 1 October 2026:**

- Free-form replies inside the 24-hour window are now **billed per message**. They were free until 30 September.
- Utility templates inside the window are now billed per message too.
- **AI-generated messages are billed as a separate and more expensive category**, Meta Business Agent messages, explicitly excluded from the free entry point. One BSP estimates roughly $0.04 to $0.05 per message.
- Marketing templates remain the most expensive category with no volume discount, as before.

**The offset:** Click-to-WhatsApp ads open a **72-hour free entry point window**, which runs on a separate timer from the 24-hour service window. For a brokerage running Meta ads into WhatsApp, which is the likely primary lead source, those conversations are free for 72 hours. This materially changes lead-gen economics in BSH's favour.

**Cost model for an AI qualifying bot:** a 10-message qualifying conversation costs roughly $0.40 to $0.50. At 200 inbound leads per month that is $80 to $100. Against agent time spent asking the same five qualifying questions two hundred times, that is cheap. Design implication: keep bot replies short. Long multi-turn flows now cost real money per turn.

**Verify Indonesian rates with the BSP before committing.** Rates vary by market and these are days old.

---

## 7.2 Zoho Automation, and What Actually Reaches WhatsApp

> **Largely superseded 2026-10-13.** The central risk in this section, whether Zoho workflow rules can reliably trigger WhatsApp sends, no longer decides anything: respond.io owns WhatsApp sending and has its own native automation and sequence builder. Open item 11 below is downgraded from blocking to irrelevant for the CRM choice. What survives and still matters: the Zoho plan gating table (Blueprint and Deluge need Professional, Zia needs Enterprise), the Meta Lead Ads capture path, and the Conversions API gap, which applies whichever CRM wins. Kept in full because the plan gating feeds the cost case.

Zoho's automation is four separate layers, and the plan gating matters for the cost case.

| Layer | What it does | Plan required |
|---|---|---|
| Workflow Rules | Trigger on record create, edit or field update. Actions: email, task, field update, webhook, custom function | Standard. 50 per module, 200 on Enterprise |
| Cadences | Multi-step sequential follow-up, the closest thing to an email sequence | Standard, up to 70 active per module with add-ons |
| Blueprint | Enforces a process stage by stage so agents cannot skip steps | **Professional** |
| Custom Functions (Deluge) | Zoho's scripting language. Can call any REST API, including Meta's Graph API directly | **Professional** |

Professional at $23/seat is the tier that unlocks Blueprint and Deluge. That is the recommended tier anyway, so no cost change. Note that **Zia AI suggestions are Enterprise only** ($40/seat), which is worth knowing before anyone assumes Zia is included.

**Cadences support WhatsApp follow-ups.** Confirmed on Zoho's own help documentation and release notes. This is the sequence capability, and it works the way WhatsApp requires: pre-approved templates only, and only if WhatsApp Business is enabled on the account. So a follow-up cadence can be built, but every step is a template that Meta approved and every send is billed.

**Meta Lead Ads reach the CRM through Zoho Social**, not Zoho CRM directly. The integration captures leads in real time and maps up to 20 Lead Ad form fields to CRM fields. Fine for inbound.

**Known gap worth planning around:** the native integration captures leads into the CRM but does not reliably send conversion events back to Meta. That means Meta's ad algorithm cannot optimise toward closed deals, only toward form fills. For a brokerage where a lead is worth very different amounts depending on budget, that is a real limitation. The fix is Meta's Conversions API, which Deluge can call directly. Build it in Phase 3, not at launch.

**Open conflict to resolve in trial:** Zoho's documentation indicates workflow rules can trigger WhatsApp messages, but there are user reports on Zoho's own community forum complaining that the WhatsApp integration lacks workflow support. These may be different features or different vintages. **Do not assume this works. Test it explicitly.** It is exactly the kind of thing that reads fine on a feature page and breaks in practice, and the whole follow-up automation case depends on it.

**Deluge is the escape hatch.** Anything the native integrations do not cover, custom functions can reach by calling the Meta Graph API directly. That is the reason the dev team matters, and it is a capability Apimo and GoHighLevel do not match.

---

## 8. Open Items to Verify Before Signing

Nothing here should be assumed. Each of these could change the decision.

| # | Item | Why it matters | Who |
|---|---|---|---|
| 1 | Zoho Professional custom module and custom field limits against the planned property schema | If Properties needs more fields than Professional allows, the price jumps to Enterprise at $40/seat and the cost case changes | Dev team |
| 2 | How Zoho handles listing photo volume (CRM attachments vs WorkDrive vs Drive) | A brokerage listing has 20 to 40 photos. If this is awkward, it is a daily friction point for agents | Dev team |
| 3 | WhatsApp Coexistence eligibility for Indonesian numbers, via the chosen BSP | Determines whether agents keep their own WhatsApp. Do not promise it to agents until confirmed | Matthieu + BSP |
| 4 | Zoho data center choice (AU vs IN) and whether BSH has any data residency position | No Indonesian DC exists. Pick deliberately rather than by default | Matthieu + BSH |
| 5 | IDR as a first-class currency in both finalists, with correct formatting at billions | Prices are quoted in IDR and USD. Currency handling that breaks at 9 digits is a real risk | Trial |
| 6 | Apimo: is €139 genuinely flat and seat-unlimited, what does the website product cost separately, are there any Asian clients | Decides whether the backup is real | Matthieu |
| 7 | Apimo: HubSpot, Slack, and WhatsApp support, confirmed in a demo not a brochure | Three stated requirements, all unverified | Demo |
| 8 | HubSpot record ownership rules with management | The sync cannot be switched on without this agreed | Matthieu + management |
| 9 | Commission model: exact formulas for brokerage profit share, PA overriding commission, and co-broke splits | Needed before anyone builds the commission module | Matthieu |
| 10 | Who administers the CRM day to day | A tool with no owner sits unused. Likely the Admin & Listings Coordinator role already planned in `Hiring/` | Matthieu |
| 11 | ~~Can Zoho workflow rules actually trigger WhatsApp sends~~ | **Closed 2026-10-13, no longer relevant.** respond.io owns WhatsApp sending and has native automation. Does not affect the CRM choice | Closed |
| 12 | Indonesian WhatsApp message rates post 1 Oct 2026 | Pricing changed and varies by market. Still live, but now a respond.io operating cost question, not a CRM question | Reservation team + respond.io |
| 13 | Zoho One ($37/user, so $296/mo at 8) vs CRM Pro + SalesIQ Enterprise ($344/mo) | Zoho One is cheaper and includes ~45 more apps, but is licensed per employee so everyone at BSH would need a seat. Check whether that is viable before assuming the saving | Matthieu + BSH |
| 14 | Whether Meta Conversions API work is needed at launch or Phase 3 | Native Lead Ads integration captures leads but does not send conversion events back to Meta, so ads optimise toward form fills rather than closed deals. Build work whichever CRM wins | Dev team |

**Added 2026-10-13, after the existing stack was disclosed:**

| # | Item | Why it matters | Who |
|---|---|---|---|
| 15 | **Which Odoo plan and edition does BSH run: Standard, Custom, or self-hosted Community?** | **Blocking.** Standard has no Studio and no external API, which eliminates Odoo outright. Custom or Community with dev resource makes it the favourite on the finance and commission criterion. Nothing about Odoo can be concluded until this is answered | BSH finance + IT |
| 16 | Which respond.io plan BSH holds, current monthly active contact usage, and seat count | Determines the cost of adding 4 to 6 brokerage agents, and whether the brokerage needs its own workspace. The first draft budgeted nothing for this | Reservation team |
| 17 | Whether brokerage conversations should sit in a separate respond.io workspace or share the guest inbox | Affects the contact tier, the bill, agent permissions, and whether a buyer thread is visible to concierge staff | Reservation team + Matthieu |
| 18 | Does management agree to retire HubSpot Starter, or does it stay? | Decides whether a two-way sync gets built at all. See Section 7, Options A and B | Matthieu + management |
| 19 | respond.io to CRM handoff: webhook plus API, Zapier, or Integrately, and who owns it | No finalist has a native connector. This is the lead capture path, so it is Phase 1 work, not Phase 3 | Dev team |
| 20 | Are brokerage and management separate legal entities? | Decides whether multi-company configuration is needed, which is a Custom-plan feature in Odoo and affects permissions in all three finalists | Matthieu + BSH |
| 21 | Guesty API access and whether ADR/occupancy data can be used in buyer-facing material | Compliance and owner-consent question before performance data from managed villas appears in a listing presentation | Matthieu + management |

---

## 8.1 What Needs Discussing, and With Whom

Added 2026-10-13. The research is as far as research can take this. What is left is not findable on a vendor page.

**Four conversations, in this order:**

**1. BSH finance and IT, one question.** Which Odoo plan and edition? Standard eliminates Odoo. Custom or Community makes it the leading candidate. Nothing else in the decision can be sequenced until this is known, so ask this first and ask it alone. Also worth asking in the same conversation: who administers Odoo today, and would they take on a brokerage module.

**2. The reservation and concierge team.** They own respond.io and their inbox is where brokerage leads already arrive. Three things to establish: which plan and contact tier BSH is on, whether brokerage conversations get their own workspace or share theirs, and what the handoff looks like in practice when an acquisition inquiry lands. This team can block adoption more easily than anyone realises, because if the handoff is awkward they will simply keep handling brokerage inquiries themselves and the CRM will stay empty.

**3. BSH management, the budget and stack conversation.** Frame it as what it is: BSH runs five systems and the brokerage needs a property database none of them can hold. Lead with the HubSpot structural point from Section 3 Finding 2, because it is the one argument that is not a matter of taste. Then put the consolidation option on the table (Section 7, Option A) so the proposal is "replace a tool" rather than only "add a tool."

**4. The dev team.** Two estimates needed: the property schema build in whichever platform is chosen, and the respond.io handoff. Both are Phase 1. Also get their read on Odoo, because if they already maintain it their opinion on Studio is worth more than any external analysis.

**What Matthieu should decide alone:** nothing in this document. What he should own is the property schema definition (what fields a Bali villa record actually needs), the commission formulas, and who administers the CRM day to day. Those are domain questions nobody else at BSH can answer, and all three are prerequisites regardless of which platform wins.

**The trap to avoid.** The temptation is to arrive with a recommendation and defend it. Do not. Arrive with the three-way table from Section 6 and the question "which of these three things matters most to us," and let the group pick the axis. A CRM chosen by the people who have to feed it gets fed. One chosen for them does not, and the day-30 success criterion is agents logging every deal.

---

## 9. Trial Plan

*Revised 2026-10-13: three finalists, not two, and only once open item 15 confirms whether Odoo is eligible. Scenarios 4 and 6 are rewritten, because WhatsApp sending is no longer the CRM's job.*

Two weeks, finalists in parallel, real data not sample data.

Load into each: 10 real listings with real photos and real IDR prices, and 20 real leads with real history.

Then run these five scenarios in both, and time them:

1. **Intake a listing.** Full villa record with title type, lease years remaining, dual-currency price, land and building size, 25 photos, owner contact, mandate document. Time it. If it takes an agent more than 10 minutes, adoption will fail.
2. **Match a buyer.** A buyer wants leasehold, under $400K, Canggu or Berawa, sea view. How many clicks to get the matching inventory, and can it fire automatically when a new listing lands?
3. **Publish a price change.** Change a listing price and confirm it reaches the website, or in the trial, confirm the API exposes the change and a webhook fires.
4. **Capture a lead from respond.io.** *Rewritten 2026-10-13.* Take a real acquisition inquiry sitting in respond.io and get it into the CRM as a contact and a deal, with the thread link on the record. Use whatever path is realistic: webhook, Zapier, or Integrately. This is now the highest-risk integration in the stack, because it is the lead capture path and no finalist has a native connector. If it is ugly in a trial it will be worse in production.
5. **Calculate a commission.** One closed deal with a co-broke split, agent commission, and BSH profit share. Does the system produce the numbers, or does it still need a spreadsheet? For Odoo, carry it one step further: does the invoice and the journal entry follow without a second system?
6. **Hand a drafted follow-up back to respond.io.** *Rewritten 2026-10-13.* The CRM identifies who is owed contact and drafts the message from record history. A person sends it from respond.io. Test the full loop, including whether the sent message lands back on the CRM record. Automation that bypasses human approval is out of scope by policy, so the test is the handoff, not the send.

Also, during the trial window:
- Submit a real support ticket to each vendor and time the response. This is the cheapest vendor-health signal available.
- Get one reference call per finalist, from a customer the vendor did not suggest. For Apimo specifically, try to find one in Asia.
- **Put two agents in front of each candidate for thirty minutes and watch them intake a listing unassisted.** Added 2026-10-13, mainly because Odoo's adoption risk is the only thing that could sink the cheapest and architecturally cleanest option, and it cannot be assessed from a feature page.

---

## 10. Rollout Plan

Phased, because the website and the HubSpot sync do not have to block launch.

**Phase 0, now to 2 weeks: decide**
- Run the trials and the five scenarios
- Close out the open items in Section 8
- Score with the dev team and whoever will administer it, not alone. The scoring argument is more useful than the number.
- Negotiate before committing verbally. Ask for terms, not just price: annual discount, free onboarding or migration help, and a monthly-to-annual escape in the first 90 days. Keep the second finalist warm until terms are settled.

**Phase 1, weeks 2 to 4: CRM live for day one**
- Property module, contact model, deal pipeline, user accounts and permissions
- Brokerage WhatsApp number onto the Cloud API
- Agents logging deals from the first working day. This is the only Phase 1 success criterion that matters.

**Phase 2, weeks 4 to 10: website**
- Brand and site built against the CRM API
- Listings publish from the CRM, no double entry, ever

**Phase 3, months 3 to 4: connect the rest**
- HubSpot two-way sync on contacts and deals
- Claude via MCP: the follow-up brief and the draft-reply workflows
- Commission module with the real formulas

**Phase 4, when needed**
- Agent WhatsApp Coexistence, if eligible
- Portal feeds, when partnerships land

**Success criteria:**
- Day 30: every agent logs every deal in the CRM, zero deals tracked in WhatsApp or spreadsheets
- Day 90: website listings match CRM listings with no manual sync, no follow-up older than 7 days sitting untouched
- Day 180: commission calculations run in the system, HubSpot sync stable, management can see brokerage pipeline without asking for it

---

## 11. Decision Log

| Date | Decision | Rationale |
|---|---|---|
| 2026-10-11 | Buy, do not build | Bali Exception precedent, launch timeline |
| 2026-10-11 | US MLS-based real estate CRMs ruled out | No MLS in Indonesia, their core value does not transfer |
| 2026-10-11 | HubSpot ruled out for brokerage | Custom objects are Enterprise only, about $1,200/mo at 8 seats |
| 2026-10-11 | Attio ruled out | Custom objects are Pro only, about $632/mo at 8 seats, over budget |
| 2026-10-11 | GoHighLevel ruled out as system of record | No property object, no commission tracking, poor data portability |
| 2026-10-11 | Zoho CRM recommended, Apimo backup | Tied on score, Zoho's weakness is fixable in weeks and Apimo's is not |
| 2026-10-12 | Closio internal pricing added to both docs | Matthieu supplied `Closio-Pricing-Internal-EN.pdf`, marked INTERNAL / DO NOT PUBLISH. Confidentiality and disclosure risks raised (it undercuts the Section 9 conflict disclosure, and his non-compete position with Bali Exception is unresolved). He directed inclusion anyway. Figures carry their source in the BSH-facing report rather than appearing as market research. Analytically the numbers reinforce the rejection: Closio is 2 to 2.5x Zoho and scales worse |
| 2026-10-12 | Closio ruled out, framing hardened | Originally logged as a personal conflict of interest. Corrected: the disqualifying issue is structural, Bali Exception owns the product and is a direct BSH competitor in the same geography. Adopting it puts BSH's entire book in a competitor-administered database. Disclose to BSH management proactively rather than on request |
| | Final selection | Pending trials |

**Renewal tracking:** set once a contract is signed. Note the notice period and put the renewal date minus 60 days in the calendar, with an owner.

---

## Sources

All figures verified against vendor pricing pages and vendor documentation, October 2026. Pricing changes often, so re-check on the day of purchase.

- Attio pricing and custom object plan gating: attio.com/pricing and Attio Help Center, "Create and manage custom objects"
- HubSpot custom objects tier: HubSpot Knowledge Base, "Create and edit custom objects"; confirmed Enterprise-only as of April 2026
- Zoho CRM pricing and editions: zoho.com/crm/zohocrm-pricing.html
- Zoho MCP and Claude setup: zoho.com/mcp and zoho.com/crm/developer/docs/mcp/setup/claude.html
- Apimo packages and positioning: apimo.com/en, Capterra and Software Advice product profiles
- GoHighLevel pricing and add-ons: gohighlevel.com/pricing
- WhatsApp multi-agent limits and Coexistence: WhatsApp Help Center "About multi-agent", Meta for Developers "Onboard WhatsApp Business app users"
