# CRM Selection Report: BSH Brokerage

*Prepared for inclusion in the BSH brokerage business plan*
*Date: 12 October 2026. Revised 13 October 2026.*
*Prepared by: Matthieu Jammers, Director of Business Development*
*Status: for discussion. No selection made.*

> **Revision note, 13 October 2026.** The first version of this report was written without a full picture of the systems BSH already runs. It assumed HubSpot was the only incumbent. BSH in fact operates respond.io for omnichannel messaging, HubSpot Starter for pipeline, Slack, Guesty for property management and Odoo for finance. Two of those overlap directly with what the CRM was being asked to do. The report has been revised accordingly: WhatsApp is no longer a CRM requirement, Odoo has been added as a candidate, and the recommendation has been withdrawn pending the internal questions set out in Section 11.

---

## 1. Executive Summary

The BSH brokerage launches without a CRM, without a listing website, and without a property database. It does, however, operate inside an existing stack of five systems. This report evaluates what the brokerage needs, which candidates can provide it, and what remains to be decided internally.

**There is no single recommendation at this stage, and that is a deliberate change from the 12 October draft.** Three candidates finish within 0.19 of each other on a weighted scorecard, which is not a meaningful gap. Each wins on a different axis, and which axis matters most is a decision for BSH collectively rather than a conclusion research can reach.

| Candidate | Monthly at 8 users | Strongest on | Weakest on |
|---|---|---|---|
| **Odoo CRM, Custom plan** | ~$120 | Commissions and finance in one database. Already in the stack | Agent adoption risk. Property model must be built |
| **Apimo CRM AI+** | ~$150 | Property model native on day one. Fastest to operational | Thinnest integration surface |
| **Zoho CRM Professional** | ~$184 | Integration surface. Only candidate with a supported Claude route | Property model must be built. Commissions sit apart from finance |

All three sit well inside a $500 monthly budget, so cost is not the deciding factor.

**Four findings drive the analysis:**

**HubSpot cannot hold a property record at any tier BSH would buy.** Custom objects are gated to HubSpot's Enterprise tier. Every tier below it, including the Starter plan BSH runs today at $15 per seat, offers only contacts, companies, deals and tickets, and a villa is none of those. Reaching the tier that can hold a villa means roughly $1,200 per month at 8 seats plus a required onboarding fee, against the $120 per month BSH currently pays. This is a structural argument, not a preference.

**Most real estate CRMs on the market do not work in Indonesia.** Follow Up Boss, BoldTrail, Lofty, Top Producer and similar platforms are built around MLS and IDX feeds, which do not exist here. Their principal value does not transfer, while their pricing does.

**Odoo deserves consideration precisely because BSH already runs it.** It is the only candidate that could calculate a commission split and book the resulting invoice in the same database, with no synchronisation to build or reconcile. It is also the only option that does not add a sixth system. Its viability depends on which Odoo plan BSH holds, which is the single blocking question in this report.

**The strongest product fit carries a governance problem BSH should decline.** Closio Estate matches the brokerage's requirements more closely than any other candidate reviewed. It is owned by Bali Exception, a direct competitor. Section 9 covers this in full, and recommends against adoption on those grounds alone.

---

## 2. What the Brokerage Actually Needs

Requirements were set before any vendor was reviewed, to avoid selecting on demonstration quality rather than fit.

**Must have:**

- Properties as first-class records, with Indonesian title types (SHM, HGB, Hak Pakai, leasehold with years remaining), dual IDR and USD pricing, and land measurement in are and square metres
- Buyer criteria matched against live inventory, with alerts when a new listing fits
- The CRM as the single source of truth for listings, with the website reading from it so nothing is entered twice
- Commission handling for co-broke splits, agent commission, the 20 percent brokerage profit share and the 15 percent property acquisition overriding commission
- A working handover from respond.io, so a qualified acquisition inquiry becomes a CRM record without anyone retyping it
- A route into Odoo, so a closed deal and its commission lines become an invoice and a journal entry

**Revised 13 October 2026, two requirements changed:**

- **WhatsApp as a first-class CRM channel is withdrawn as a requirement.** respond.io already holds BSH's WhatsApp, Facebook, Instagram and TikTok channels, and already receives inbound property acquisition inquiries alongside guest inquiries. A phone number can only be registered to one WhatsApp Business Account at a time, so the CRM cannot take over a number respond.io holds without BSH running a second number. Keeping respond.io as the conversation layer is the sensible course: it is already paid for, already staffed, and already working. The CRM's job is to hold records, not conversations.
- **Two-way synchronisation with HubSpot is now conditional.** It remains necessary if HubSpot stays, because managed villas get listed for sale and management clients become brokerage clients. However, at Starter tier with no custom objects and only contacts and deals held, migrating that pipeline into the chosen CRM and retiring HubSpot is a smaller exercise than building and maintaining a permanent two-way sync. Section 11 puts both options forward.

**Constraints:**

- Fewer than 10 users in year one, scaling toward 25
- Under $500 per month, all inclusive. Note that this must now also absorb any additional respond.io seats and contact-tier cost for brokerage agents, which the 12 October draft did not account for.
- Operational for the brokerage's first working day
- Buy rather than build. BSH has a development team, but an in-house CRM at a previous employer took years and remains underused. Developers are better spent on integration and the website.
- Adding a sixth system requires a stronger justification than adding a second one. Any proposal should address consolidation, not only addition.

---

## 3. Price Comparison

All figures verified against vendor pricing pages in October 2026. Annual billing where available.

| | Odoo Custom | Apimo | Zoho CRM Pro | Zoho One | GoHighLevel | Closio |
|---|---|---|---|---|---|---|
| Model | Per seat | Flat | Per seat | Per employee | Flat | Tiered plus usage |
| Headline | ~$15/user/mo | €139/mo | $23/seat/mo | $37/user/mo | $297/mo | $189/mo to 5 users |
| Cost at 8 users | ~$120/mo | ~$150/mo | $184/mo | $296/mo | $307/mo | $393 to $592/mo |
| Cost at 25 users | ~$375/mo | ~$150/mo | $575/mo | $925/mo | $307/mo | ~$1,167/mo |
| 3-year cost at 8 users | ~$4,320 | $5,400 | $6,624 | $10,656 | $11,052 | ~$13,608 |
| Incremental cost to BSH | Lower, finance seats already licensed | Full | Full | Full | Full | Full |
| Onboarding fee | None on subscription. Implementation not included | Not published | None | None | None | Included |
| Annual discount | Yes | Not published | 20% | 20% | Yes | 20% |
| WhatsApp cost | Not applicable, respond.io holds the channel for every candidate | | | | | |
| Meta message fees | Charged by respond.io on top, whichever CRM is chosen | | | | | |

**Odoo figures: source and status.** The Odoo line is indicative and must be replaced with BSH's actual contract terms before it is relied on. Odoo prices per country and raised Custom-plan prices across several currency zones in September 2026. The Indonesia Custom tier is published at roughly Rp255,000 per user per month, around $15, cross-checked against two independent pricing trackers. Two qualifications matter: the figure applies to the Custom plan, and BSH's existing finance users are already licensed, so the brokerage's incremental cost is lower than the table implies. The subscription also excludes implementation work, which for a custom property model is comparable to Zoho's two to four weeks.

**Closio figures: source and status.** Closio does not publish CRM or AI pricing. Its public pricing page offers a custom quote only. The figures above come from a Closio internal sales reference dated October 2026, which I retained from go-to-market work I did for the product while at Bali Exception (see Section 9). They are accurate as at that date but are not public, not quoted to BSH, and should be treated as indicative. Any real number would come from a quote.

Closio's structure, for completeness:

- CRM Starter $99/mo up to 3 users. CRM Pro $189/mo up to 5 users. Additional users $25/mo each on both. Enterprise is quote only.
- The AI agent is a separate module priced by conversation volume, where one conversation means one buyer thread in a month regardless of message count: 200 threads $129, 500 threads $249, 900 threads $399, 1,500 threads $599, or $0.75 per thread with no commitment. Overage above a pack bills at the per-thread rate.
- Closio Sites, a website synced to the CRM, $79/mo with no setup fee.
- 20% discount on annual billing across all three lines.

At 8 users BSH would need CRM Pro at $189 plus three additional seats at $25, so $264, plus an AI pack sized to roughly 200 leads per month at $129 to $249, plus Sites at $79 if used. That is $393 to $592 monthly, or $314 to $474 on annual billing.

Notes that matter for budgeting:

- **Odoo is the cheapest option and the only one that does not add a vendor**, a contract or a security review. Its cost advantage is understated in the table, because finance seats are already paid for. Its viability rests entirely on which plan BSH holds: the Standard plan excludes Odoo Studio and external API access, which would remove it from consideration altogether.
- **Zoho One is cheaper than Zoho CRM Professional plus SalesIQ bought separately** ($296 against $344) and includes roughly 45 additional applications. The constraint is that Zoho One is licensed per employee, so every BSH employee would need a seat. Worth checking before assuming the saving. Note that SalesIQ's role was partly messaging, which respond.io now covers, so the comparison may no longer be the relevant one.
- **GoHighLevel's flat rate becomes compelling above about 13 users** and never increases. Its disqualification is functional, not financial, and its strongest feature, the conversation and nurture layer, now duplicates respond.io.
- **Closio costs roughly two to two and a half times the recommended option** and reaches the $500 ceiling once the AI pack is sized for real volume. It also scales poorly, because every user above five adds $25, putting a 25-agent team near $1,167 per month.
- **Closio's per-thread AI pricing compares well on its own terms.** Packs work out at $0.40 to $0.65 per buyer thread against Meta's per-message billing elsewhere. Whether Meta's pass-through fees sit on top of Closio's packs is not stated and would need confirming.
- **Meta's WhatsApp message fees apply on top of every option.** See Section 8.

---

## 4. Integrations

*Revised 13 October 2026. respond.io and Odoo are now the two integrations that matter most, because they sit at either end of the brokerage workflow: leads arrive through one and money leaves through the other.*

| Capability | Odoo Custom | Apimo | Zoho | GoHighLevel | Closio |
|---|---|---|---|---|---|
| **respond.io handover** | Zapier or Integrately, or API | Zapier or API | Zapier or Integrately, or API | Zapier or Make | Not offered |
| **Odoo finance link** | **Internal, none required** | Custom work | Custom work | Custom work | Not offered |
| HubSpot two-way sync | Zapier or Integrately | No connector found | Zoho Flow, Whalesync or Stacksync | Zapier or Make only | Not offered |
| Slack | Native | Unverified | Native | Zapier | Not offered |
| Google Drive | Documents module, plus API | Own document module | Native, including file attachment to custom records | Zapier | Documents module, own storage |
| Gmail and Google Calendar | Native two-way | Native | Native two-way | Native | Not specified |
| Guesty data link | API to API | API to API | API to API | Not practical | Not offered |
| Claude and AI assistants | JSON-RPC or XML-RPC API. No official MCP server | No published route | **Official MCP server with published Claude setup guide** | No MCP server | No MCP server |
| Open REST API | Full on Custom plan, with webhooks. **Not available on Standard** | Public API claimed | Full, with webhooks | API v2, Unlimited tier only | Not publicly documented |
| Scripting and custom code | Python modules, open source core | Not offered | Deluge, can call any external API | Limited | Not offered |
| Mobile apps | iOS and Android | iOS and Android | iOS and Android | iOS and Android | iOS and Android |

**Three observations.**

**No candidate has a native respond.io connector.** HubSpot does, which is worth stating plainly, but HubSpot cannot hold a property record at a tier BSH would buy. For Odoo, Apimo and Zoho the handover is built using respond.io's webhooks and the CRM's API, or an intermediary such as Zapier or Integrately in the interim. Since this is the lead capture path, it belongs in the first phase of work rather than a later one. It is the highest-risk integration in the project and should be tested during the trial, not assumed.

**Odoo's advantage on the finance link is structural and not replicable.** A commission calculated in Odoo produces the invoice and the journal entry in the same database. A commission calculated in Zoho or Apimo has to reach Odoo by synchronisation, which is a build, then a dependency, then a reconciliation problem. If commission accuracy is a priority, this is the most important row in the table.

**Zoho's advantage on Claude is also real and also not replicable.** It is the only candidate with an official MCP server and a published Claude setup guide. Odoo can be reached through its API but without vendor support for it, and Apimo has no published route. Given that BSH's working practice already runs through Claude, this is a genuine differentiator rather than a feature-list entry.

The absence of a public API specification for Closio is a procurement concern independent of ownership. A website integration, a respond.io handover and any future automation all depend on one.

---

## 5. Automations

*Revised 13 October 2026. Messaging automation now sits in respond.io for every candidate, so what matters here is internal process automation: what the CRM does to its own records, not what it sends to a client.*

| | Odoo Custom | Apimo | Zoho | GoHighLevel | Closio |
|---|---|---|---|---|---|
| Trigger-based rules | Automated actions and server actions, Studio | Native rules | Workflow Rules, 50 per module on Professional | Workflow builder | Lead routing by language and listing type |
| Follow-up sequences | Activity scheduling and reminders | Native | Cadences | Campaigns across channels | Email broadcasts to segments |
| Process enforcement | Stages with required fields | Pipeline | Blueprint, stage by stage, Professional tier | Pipeline stages | Pipeline |
| Custom code | Python, open source core | Not offered | Deluge functions, Professional tier | Limited | None exposed |
| AI assistance | Odoo AI on Custom plan | Marketed, unverified | Zia, Enterprise tier only | Included, deeply integrated | AI agent included, core to the product |
| Client messaging automation | Handled by respond.io in every case | | | | |

Zoho Professional at $23 unlocks both Blueprint and Deluge, which matter for enforcing a sales process and for reaching anything the native integrations miss. Zia, Zoho's own AI layer, sits on Enterprise at $40 and is not required, because Claude covers that ground through the MCP server.

Odoo's automation is adequate rather than strong for sales process work, since its heritage is operations and finance rather than selling. Its open source core means anything missing can be written, which is an advantage only if BSH's developers are willing to maintain it.

Closio's automation is narrower but aimed precisely at this industry. Routing leads by spoken language and listing type is a real brokerage problem that generic platforms leave to configuration, although respond.io already performs routing of this kind across BSH's channels.

---

## 6. Workflow Setup

The practical question is how much work stands between signing and agents using the system.

**Apimo: fastest of the credible options.** The property model, matching and commission tracking are supplied rather than built, so little configuration stands between signing and use. The work moves instead to the integration side, where it is less bounded.

**Zoho: two to four weeks of configuration.** The property module, matching logic and commission calculations are all buildable and none exist on day one. This is known, bounded work for the development team. The risk is that a poorly designed layout kills agent adoption, so the configuration should be judged on how fast an agent can enter a villa, not on how complete the field list looks.

**Odoo: comparable build time to Zoho, with a higher adoption risk.** The property model is built in Odoo Studio, which is capable but is the same two to four weeks of work. The distinct concern is the interface. Odoo is designed for operations and finance staff at a desk, not for salespeople working from a phone between viewings, and it is the densest of the candidates to learn. This is the one factor that could rule out an option that is otherwise the cheapest and the cleanest architecturally, and it cannot be judged from a feature list. The trial should put two agents in front of it unassisted and watch what happens.

**GoHighLevel: fast to stand up, wrong shape underneath.** Reviews consistently describe a difficult first month because the platform exposes everything at once without a guided order. The deeper issue is that no amount of configuration produces a property object.

**Closio: fastest by a wide margin.** The vendor states the AI agent is live roughly 24 hours after the WhatsApp number is connected, and most agencies are fully operational within seven days, with onboarding, data import and training included in the price. For a brokerage opening in weeks, that is a material advantage.

---

## 7. Listing Website Integration

This matters more than usual because the brokerage website does not exist yet. BSH can design the site around whichever CRM it picks, rather than forcing a CRM to fit an existing site.

**Zoho.** No website product. The site gets built by the development team against Zoho's REST API, with webhooks triggering an update when a property record changes. Most control, most work, no lock-in. The property schema should be designed first and the site built around it.

**Odoo.** Includes a website builder in the same subscription, so the site could either be built in Odoo directly or built separately against its API. Building it in Odoo is fast and keeps listings and site in one system. Building it against the API gives design freedom, which matters for a brokerage selling on presentation quality. The second route is probably correct, but the first exists as a fallback if the launch timeline tightens.

**Apimo.** Has its own search-oriented website product with the CRM as the listing source of truth, which solves the website requirement in the same purchase. It is the fastest route and also the deepest lock-in, since listings and site then live together and leaving means rebuilding both.

**GoHighLevel.** Website and funnel builder included. Good for landing pages and lead capture, poor as a property catalogue, because the underlying records are contacts and opportunities rather than listings.

**Closio.** Connects to an existing website and syncs listings automatically, with publish, update and remove driven from the CRM. A website is explicitly not included, though the vendor will build one as a separately quoted project.

All three put the CRM in charge of listings. The difference is how much BSH builds and how much it rents.

---

## 8. WhatsApp and Agent Follow-Up

*Revised 13 October 2026. This section no longer bears on the CRM choice, because respond.io holds BSH's WhatsApp channels and will continue to. It is retained in full because the economics below are unchanged by that, and they govern what BSH pays to run brokerage conversations through respond.io. The questions move from the CRM vendors to the reservation team and to respond.io.*

WhatsApp deserves its own section because it does not behave like email, and because Meta changed the economics on 1 October 2026.

**The three rules:**

- A client message opens a 24-hour window. Inside it, any message can be sent, including AI-generated replies. Each new client message resets the clock.
- Outside that window, only templates approved in advance by Meta may be sent, and only to clients who have explicitly opted in.
- Message quality is rated, and numbers that behave like spam get restricted. A restricted brokerage number during launch month would be severe.

**What changed on 1 October 2026:** free-form replies inside the 24-hour window are now billed per message, where previously they were free. AI-generated messages are billed as a separate and more expensive category, estimated by one provider at $0.04 to $0.05 each. Most published guidance still describes the old model and should be disregarded.

**The offset:** advertisements that click through to WhatsApp open a 72-hour free entry point, on a separate timer. For a brokerage advertising on Meta, which is the expected primary lead source, those conversations carry no message cost for three days.

**Cost model for AI qualification:** a ten-message qualifying exchange costs roughly $0.40 to $0.50. At 200 inbound leads per month, that is $80 to $100. Set against agent hours spent asking the same five qualifying questions repeatedly, the economics are favourable.

**Agent follow-up, as it will actually work.** The vendor comparison that previously sat here has been removed, because the channel does not run through the CRM in any scenario. The arrangement is:

| Function | System |
|---|---|
| WhatsApp, Facebook, Instagram, TikTok channels | respond.io |
| Conversation routing and assignment | respond.io |
| AI qualification of inbound inquiries | respond.io, if BSH chooses to enable it for brokerage threads |
| Template sequences and follow-up sends | respond.io |
| Who is owed contact, and the draft of what to say | CRM, with Claude reading the record |
| Record of what was sent, against the contact | CRM, written back from respond.io |

Follow-ups are therefore drafted from the CRM and sent from respond.io by a person. Nothing is sent to a client automatically.

Three practical points:

**The brokerage's share of respond.io cost is not yet established.** Pricing runs per plan plus monthly active contacts, with Starter at $79 per month for five users and Growth at $159 per month for ten users and 1,000 monthly active contacts, additional users at $12 to $20 each. Adding four to six brokerage agents and their buyer threads has a real cost against the $500 ceiling and needs confirming with whoever administers the account.

**Brokerage threads and guest threads currently share one inbox and one contact pool.** Whether the brokerage should have a separate workspace, separate channels, or only separate tags affects the contact tier, the bill, and whether concierge staff can see buyer negotiations. This is a decision for the reservation team, and it should be made before brokerage agents are added rather than after.

**Agents keeping their own WhatsApp numbers** is possible through Meta's Coexistence feature, which runs the Business app and the Cloud API on one number simultaneously without losing history. Availability depends on country, provider and the individual number, so it must be confirmed for Indonesian numbers with respond.io before anything is promised to agents. Unofficial QR-code bridging tools carry a genuine risk of the number being banned and should not be used.

---

## 9. Closio Estate: Capability and Conflict

This section exists to disclose a conflict. It should stay in the business plan in full.

**Closio is the closest product fit of anything reviewed.** Its modules cover leads and pipeline, contacts, owner listing requests, property listings, calendar, messages, email broadcasts, documents, reporting and built-in calculators for rental yield, commission and price per square metre. Its AI agent replies to buyers in over 30 languages, qualifies on budget, purpose and timeline, scores the lead, proposes only the agency's own listings, books viewings and hands over to a named agent. Lead capture spans WhatsApp, Instagram, Facebook, portals, website and email, with each lead source-tagged and assigned automatically. It is multi-language including Bahasa Indonesia, it ships iOS and Android applications, and onboarding is included.

For a Bali brokerage selling to foreign buyers over WhatsApp, this is close to a purpose-built answer.

**Closio is owned by Bali Exception, a direct BSH competitor.** Bali Exception operates in the same geography, pursuing the same villas, the same sellers and the same buyers. Bali Exception appears as the first client logo on Closio's own homepage, so the relationship is public and verifiable.

Adopting Closio would place BSH's complete brokerage book inside a database owned and administered by that competitor: every lead, every listing, every seller contact, every negotiated price, every commission split and every agent's activity. No confidentiality clause resolves this, because it asks a competitor to hold the book and undertake not to read it.

**My own position, stated plainly.** While I was at Bali Exception I did go-to-market work for Closio. I am raising that here rather than waiting to be asked, and BSH should weigh my recommendation with it in mind. My recommendation is that we do not buy the product.

**Two secondary considerations:**

- My non-solicitation and non-competition terms with Bali Exception are not yet settled in writing. BSH becoming a paying customer of their product while we recruit in the same market would complicate that.
- Closio's published target market excludes Bali and the surrounding islands for competitive protection, so BSH may fall outside the territory it serves regardless.

**Recommendation: decline. The reason is governance, not capability.** Excluding Closio costs us little, because workable alternatives exist. Being wrong about it costs us our competitive information, permanently. If BSH wants to reopen this, the conditions would be passive arm's length ownership, no financial interest held by anyone at BSH, and written board approval. The data exposure would still be there.

---

## 10. Pros and Cons

### Odoo CRM, Custom plan

*Added 13 October 2026. Everything below assumes BSH runs the Custom plan or self-hosted Enterprise. On the Standard plan there is no Odoo Studio and no external API access, and Odoo is not a candidate at all.*

**Advantages**

- Already in the stack, already licensed on the finance side, already administered by someone at BSH. It is the only option that does not add a sixth system, a new vendor, a new contract or a new security review.
- Commission and finance in one database. Co-broke splits, the 20 percent brokerage profit share and the 15 percent property acquisition overriding commission calculate in the same system that raises the invoice and books the revenue. No synchronisation, no reconciliation, no spreadsheet at the end of a deal.
- Odoo Studio builds custom models without code, so the property record can carry Indonesian title types, lease years remaining, dual-currency pricing and local land measurement.
- Cheapest option reviewed, and cheaper still in practice because finance seats are already paid for.
- One subscription covers CRM, Sales, Documents, Accounting, Website and Sign, so the listing site and document handling need no additional purchase.
- Open source core, giving the strongest data and schema portability of any candidate and the lowest exit risk.
- Full external API with webhooks on the Custom plan, so the listing website can be built against it cleanly.

**Disadvantages**

- Which plan BSH holds has not been confirmed. The Standard plan eliminates Odoo outright. Nothing else about this option can be concluded until that is answered.
- The property model must be built, the same two to four weeks as Zoho. Odoo has no native real estate object.
- Highest agent adoption risk of any candidate. The interface is built for operations and finance staff, not for salespeople working from a phone between viewings. This is the principal reason not to choose it.
- No official MCP server, so Claude access runs through Odoo's API without vendor support for that use. Zoho is materially better here.
- Buyer-to-listing matching is built rather than supplied, the same as Zoho.
- No native respond.io connector, the same as every other candidate.
- If the brokerage and management are separate legal entities, multi-company configuration is required. It is available on the Custom plan but is additional setup and raises permission questions about who sees whose records.
- Per-seat pricing rises with headcount, though from a considerably lower base than Zoho.

### Zoho CRM Professional

**Advantages**

- Custom modules model Indonesian property precisely: title types, lease years remaining, dual-currency pricing, local land measurement. Nothing is forced into a foreign market's conventions.
- Official MCP server with published Claude setup, the only candidate answering the AI requirement through a supported route.
- Native Slack, Gmail, Google Calendar and Google Drive integration.
- Full REST API, webhooks and Deluge scripting, so the development team can reach anything the native integrations miss, including Meta's Conversions API.
- Blueprint enforces the sales process stage by stage, which matters when onboarding new agents.
- Zoho has been independent and profitable for over 25 years. No funding or acquisition risk.
- At $184 per month, over $300 of the monthly budget remains for synchronisation tooling and reserve.

**Disadvantages**

- Nothing is configured on day one. Two to four weeks of development work precede agent use.
- Buyer-to-listing matching is built with workflow rules rather than supplied.
- The administrative interface is dated and extensive. Adoption depends on layout design quality.
- Professional caps custom modules and fields per module, which must be checked against the property schema.
- Listing photograph handling at 25 to 40 images per villa is unproven and may require WorkDrive alongside.
- Zia AI sits on the Enterprise tier.
- No Indonesian data centre. Australia or India must be chosen deliberately.
- Per-seat pricing rises with headcount, reaching $575 per month at 25 agents.
- Commission calculation sits in a different system from finance, so the result has to reach Odoo by synchronisation. Added 13 October 2026.
- No native respond.io connector, so the lead capture handover is work the development team builds and maintains. Added 13 October 2026.

### GoHighLevel Unlimited

**Advantages**

- Flat rate with unlimited users and contacts. Growth from 8 to 25 agents costs nothing additional.
- Website and funnel builder included.
- Strongest of the three on lead nurture, response speed, missed-call text-back, booking and reminders.
- AI features are integrated rather than added on.
- Fourteen-day free trial on all plans.

**Disadvantages**

- No property object. Villas, title types and dual-currency pricing have no natural home. This is disqualifying for a brokerage.
- No commission tracking, so splits and profit share remain in spreadsheets.
- No buyer-to-listing matching, because there is no listing record to match against.
- No MCP server. Claude integration would be custom work.
- Data export is a known weakness and snapshots are proprietary, making a future migration difficult.
- Usage is billed from a prepaid wallet, and an empty wallet suspends service.
- Built for United States local service businesses. Reviews report a steep first month.
- HubSpot synchronisation only through Zapier or Make.

### Closio Estate

**Advantages**

- The closest functional fit reviewed. Property records, owner listing requests, matching, multi-channel capture and brokerage calculators are all supplied rather than built.
- AI agent in over 30 languages, qualifying and routing without configuration work.
- Live in roughly seven days, with onboarding, data import and training included.
- Built for Southeast Asia, with Bahasa Indonesia support and local timezone coverage.
- Lead routing by spoken language and listing type, which generic platforms leave to configuration.

**Disadvantages**

- Owned by a direct competitor. Disqualifying on its own.
- Roughly two to two and a half times the cost of the recommended option, reaching the $500 ceiling once the AI pack is sized for real lead volume.
- Scales poorly on headcount. Every user above five adds $25, so a 25-agent team approaches $1,167 per month against GoHighLevel's flat $307.
- No published pricing. Every figure in this report comes from an internal document rather than a quote, so BSH cannot verify it without engaging the vendor.
- No public API documentation, which affects website integration, HubSpot synchronisation and future automation.
- No HubSpot, Slack or MCP integration offered.
- Small vendor with five client logos and three public reviews. Limited evidence of financial stability or security posture.
- Commission calculators are not the same as commission split tracking.
- Exit risk, since the system of record would sit with a party holding reason to obstruct.

---

## 11. What Needs Deciding, and Rollout

*Rewritten 13 October 2026. The previous version selected Zoho with Apimo as the alternative. That selection rested on Zoho including WhatsApp at no extra cost and on HubSpot being the only incumbent system. Neither holds. The selection is withdrawn rather than replaced: three candidates finish within 0.19 of each other, and the deciding factor is a question of BSH's priorities rather than a research finding.*

**The choice, stated as a choice.**

| Choose | If BSH's priority is |
|---|---|
| **Odoo Custom** | One fewer system, the lowest cost, and commissions that reconcile themselves against finance without a sync. Accepting that agents need real training on a dense interface |
| **Apimo** | Launching in weeks with almost no build, accepting that integration work to respond.io and Odoo comes later and is less bounded |
| **Zoho CRM Pro** | Long-term flexibility and the Claude workflows, accepting a two to four week build and a separate commission-to-finance link |

**Five questions to settle before any trial, in this order.**

1. **Which Odoo plan and edition does BSH run?** For finance and IT. Standard removes Odoo from consideration. Custom or self-hosted makes it the leading candidate on cost and on commissions. Nothing can be sequenced before this answer.
2. **Which respond.io plan is BSH on, what is current contact usage, and what does adding brokerage agents cost?** For the reservation team. This is budget the 12 October draft did not account for.
3. **Should brokerage conversations have their own respond.io workspace, or share the guest inbox?** For the reservation team and the brokerage jointly. It affects cost, permissions, and whether concierge staff can see buyer negotiations.
4. **Does HubSpot Starter stay or get retired?** For management. Keeping it means building and maintaining a two-way sync. Retiring it means a small migration of contacts and deals, after which the sync, the tooling cost and the record-ownership rules all disappear. The recommendation is to retire it, but not until the new system is proven, and not as a condition of the CRM decision.
5. **Are the brokerage and management separate legal entities?** For management. It determines whether multi-company configuration and separated permissions are required.

**Rollout, once a decision is made.**

**Phase 1, weeks 1 to 4.** Property module, contact model, pipeline, permissions. The respond.io to CRM lead handover working, promoted into this phase because it is the lead capture path and cannot be late. Brokerage access configured in respond.io. Agents logging every deal from the first working day. That is the only success measure that matters at this stage.

**Phase 2, weeks 4 to 10.** Brand and website built against the CRM API, with listings published from the CRM.

**Phase 3, months 3 to 4.** Commission module with confirmed formulas, and the link into Odoo if the chosen CRM is not Odoo. Claude workflows. HubSpot either synchronised or retired, per question 4 above.

**Phase 4, as required.** Guesty data link so actual occupancy and average daily rate from the managed portfolio can support buyer-facing return figures. Meta Conversions API so advertising optimises toward closed deals rather than form submissions. Portal feeds once partnerships are in place.

**Success measures.** At 30 days, every agent logs every deal in the CRM, nothing is tracked in spreadsheets, and every acquisition inquiry arriving in respond.io reaches the CRM. At 90 days, website listings match CRM listings without manual intervention and no follow-up sits untouched beyond seven days. At 180 days, commissions calculate in the system and reconcile with Odoo, and management sees brokerage pipeline without asking.

---

## 12. Risks and Open Items

*Revised 13 October 2026. Two risks closed, four added.*

| Risk | Consequence | Mitigation |
|---|---|---|
| **BSH runs Odoo Standard rather than Custom** | The cheapest and architecturally cleanest option disappears, and the choice narrows to Zoho or Apimo | Confirm the plan and edition with finance and IT before anything else |
| **No candidate has a native respond.io connector** | The lead capture path is custom work, and if it is late or fragile, leads stay in respond.io and the CRM sits empty | Build and test it in Phase 1, not Phase 3. Test it during the trial with a real inquiry |
| **Odoo agent adoption fails** | A technically correct choice that salespeople will not use, which is worse than a compromise they will | Put two agents in front of it unassisted during the trial and watch, rather than judging from a demonstration |
| **Brokerage and guest conversations share a respond.io inbox** | Contact-tier costs rise unpredictably and concierge staff can see buyer negotiations | Settle the workspace question with the reservation team before adding brokerage agents |
| Property schema may exceed Zoho Professional tier limits | Forced upgrade to Enterprise at $40/seat | Verify field and module caps against the schema first |
| Agent adoption fails generally | The system becomes a second place to type things | Time the villa-entry workflow during trial. Beyond 10 minutes, redesign |
| No named administrator | The tool goes unused | Assign to the planned Admin and Listings Coordinator role |
| HubSpot record ownership undefined, if HubSpot is retained | The two systems overwrite each other | Agree ownership rules with management before enabling synchronisation, or retire HubSpot and avoid the problem |
| Commission formulas not documented | The commission module cannot be built in any candidate | Document co-broke, profit share and overriding commission formulas. This is needed regardless of which system wins |
| ~~Zoho workflow rules may not trigger WhatsApp sends reliably~~ | **Closed 13 October 2026.** respond.io owns WhatsApp sending, so this no longer affects the CRM choice | |
| ~~Indonesian WhatsApp rates unknown~~ | **Reassigned 13 October 2026.** Still live, but now a respond.io operating cost rather than a CRM selection risk | Obtain written rates from respond.io |

**Before signing, confirm:** the Odoo plan and edition; the respond.io plan, contact usage and incremental seat cost; Zoho Professional module and field limits against the property schema; listing photograph handling; data centre or hosting region selection; IDR formatting at nine figures; whether brokerage and management are separate legal entities; and whether Meta Conversions API work belongs at launch or later.

**Trial plan.** Two weeks, in parallel, across whichever candidates remain eligible after the Odoo plan question is answered. Ten real listings with photographs and twenty real leads. Six scenarios: enter a villa and time it; match a buyer against live inventory; change a price and confirm it reaches the website or that the API exposes it; take a real acquisition inquiry from respond.io through to a CRM record; calculate a commission on a co-broked deal and follow it through to an invoice; and draft a follow-up from the CRM for sending through respond.io. Alongside that: submit a support ticket to each vendor and time the reply, obtain one reference from a customer the vendor did not nominate, and put two agents in front of each candidate unassisted for thirty minutes.

---

## Sources

Verified against vendor pricing pages and documentation in October 2026. Pricing changes frequently and should be rechecked at purchase.

- HubSpot custom object tier: HubSpot Knowledge Base, confirmed Enterprise-only as of April 2026
- Zoho CRM pricing, Cadences WhatsApp support, SalesIQ pricing, MCP and Claude setup: Zoho published documentation
- GoHighLevel pricing and add-ons: gohighlevel.com/pricing
- Closio modules, pricing model, deployment timeline and client logos: closioestate.com
- Apimo packages: apimo.com
- WhatsApp window rules, October 2026 pricing change and Coexistence: Meta for Developers and WhatsApp Help Centre
- Attio custom object tier: Attio Help Centre
