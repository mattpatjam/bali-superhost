# CRM Selection Report: BSH Brokerage

*Prepared for inclusion in the BSH brokerage business plan*
*Date: 12 October 2026*
*Prepared by: Matthieu Jammers, Director of Business Development*

---

## 1. Executive Summary

The BSH brokerage launches without a CRM, without a listing website, and without a property database. BSH Management runs HubSpot. This report evaluates whether the brokerage should join HubSpot or run its own system, and which system that should be.

**Recommendation: keep HubSpot for management, and run Zoho CRM Professional for the brokerage, synced to HubSpot on contacts and deals.**

Cost: $184 per month at 8 users, or $296 per month on Zoho One if BSH licenses company-wide. Both sit well inside a $500 monthly budget.

Three findings drive the recommendation:

**HubSpot cannot hold a property record at a price BSH should pay.** Custom objects are gated to HubSpot's Enterprise tier. Professional offers only contacts, companies, deals and tickets, and a villa is none of those. Putting the brokerage on HubSpot means roughly $1,200 per month at 8 seats plus a required onboarding fee, to obtain an object that alternatives include as standard. This is a cost argument, not a preference.

**Most real estate CRMs on the market do not work in Indonesia.** Follow Up Boss, BoldTrail, Lofty, Top Producer and similar platforms are built around MLS and IDX feeds, which do not exist here. Their principal value does not transfer, while their pricing does.

**The strongest product fit carries a governance problem BSH should decline.** Closio Estate matches the brokerage's requirements more closely than any other candidate reviewed. It is owned by Bali Exception, a direct competitor. Section 9 covers this in full, and recommends against adoption on those grounds alone.

---

## 2. What the Brokerage Actually Needs

Requirements were set before any vendor was reviewed, to avoid selecting on demonstration quality rather than fit.

**Must have:**

- Properties as first-class records, with Indonesian title types (SHM, HGB, Hak Pakai, leasehold with years remaining), dual IDR and USD pricing, and land measurement in are and square metres
- Buyer criteria matched against live inventory, with alerts when a new listing fits
- The CRM as the single source of truth for listings, with the website reading from it so nothing is entered twice
- Commission handling for co-broke splits, agent commission, the 20 percent brokerage profit share and the 15 percent property acquisition overriding commission
- WhatsApp as a first-class channel, since the large majority of client contact happens there
- Two-way synchronisation with HubSpot on contacts and deals, because managed villas get listed for sale and management clients become brokerage clients

**Constraints:**

- Fewer than 10 users in year one, scaling toward 25
- Under $500 per month, all inclusive
- Operational for the brokerage's first working day
- Buy rather than build. BSH has a development team, but an in-house CRM at a previous employer took years and remains underused. Developers are better spent on integration and the website.

---

## 3. Price Comparison

All figures verified against vendor pricing pages in October 2026. Annual billing where available.

| | Zoho CRM Pro | Zoho One | GoHighLevel | Closio | Apimo |
|---|---|---|---|---|---|
| Model | Per seat | Per employee | Flat | Tiered plus usage | Flat |
| Headline | $23/seat/mo | $37/user/mo | $297/mo | $189/mo to 5 users | €139/mo |
| Cost at 8 users | $184/mo | $296/mo | $307/mo | $393 to $592/mo | ~$150/mo |
| Cost at 25 users | $575/mo | $925/mo | $307/mo | ~$1,167/mo | ~$150/mo |
| 3-year cost at 8 users | $6,624 | $10,656 | $11,052 | ~$13,608 | $5,400 |
| WhatsApp cost | Included in plan | Included | $10/mo add-on | AI packs, see below | Unverified |
| Onboarding fee | None | None | None | Included | Not published |
| Annual discount | 20% | 20% | Yes | 20% | Not published |
| Meta message fees | On top, all vendors | | | | |

**Closio figures: source and status.** Closio does not publish CRM or AI pricing. Its public pricing page offers a custom quote only. The figures above come from a Closio internal sales reference dated October 2026, which I retained from go-to-market work I did for the product while at Bali Exception (see Section 9). They are accurate as at that date but are not public, not quoted to BSH, and should be treated as indicative. Any real number would come from a quote.

Closio's structure, for completeness:

- CRM Starter $99/mo up to 3 users. CRM Pro $189/mo up to 5 users. Additional users $25/mo each on both. Enterprise is quote only.
- The AI agent is a separate module priced by conversation volume, where one conversation means one buyer thread in a month regardless of message count: 200 threads $129, 500 threads $249, 900 threads $399, 1,500 threads $599, or $0.75 per thread with no commitment. Overage above a pack bills at the per-thread rate.
- Closio Sites, a website synced to the CRM, $79/mo with no setup fee.
- 20% discount on annual billing across all three lines.

At 8 users BSH would need CRM Pro at $189 plus three additional seats at $25, so $264, plus an AI pack sized to roughly 200 leads per month at $129 to $249, plus Sites at $79 if used. That is $393 to $592 monthly, or $314 to $474 on annual billing.

Notes that matter for budgeting:

- **Zoho One is cheaper than Zoho CRM Professional plus SalesIQ bought separately** ($296 against $344) and includes roughly 45 additional applications. The constraint is that Zoho One is licensed per employee, so every BSH employee would need a seat. Worth checking before assuming the saving.
- **GoHighLevel's flat rate becomes compelling above about 13 users** and never increases. Its disqualification is functional, not financial.
- **Closio costs roughly two to two and a half times the recommended option** and reaches the $500 ceiling once the AI pack is sized for real volume. It also scales poorly, because every user above five adds $25, putting a 25-agent team near $1,167 per month.
- **Closio's per-thread AI pricing compares well on its own terms.** Packs work out at $0.40 to $0.65 per buyer thread against Meta's per-message billing elsewhere. Whether Meta's pass-through fees sit on top of Closio's packs is not stated and would need confirming.
- **Meta's WhatsApp message fees apply on top of every option.** See Section 8.

---

## 4. Integrations

| Capability | Zoho | GoHighLevel | Closio |
|---|---|---|---|
| HubSpot two-way sync | Yes, via Zoho Flow, Whalesync or Stacksync | Zapier or Make only | Not offered |
| Slack | Native | Zapier | Not offered |
| Google Drive | Native, including file attachment to custom records | Zapier | Documents module, own storage |
| Gmail and Google Calendar | Native two-way | Native | Not specified |
| Claude and AI assistants | Official MCP server with published Claude setup guide | No MCP server | No MCP server |
| Open REST API | Full, with webhooks | API v2, Unlimited tier only | Not publicly documented |
| Scripting and custom code | Deluge, can call any external API | Limited | Not offered |
| Mobile apps | iOS and Android | iOS and Android | iOS and Android |

Zoho is the only candidate that answers the AI requirement through a documented, supported route. BSH's working practice already runs through Claude, so an assistant that can read and write CRM records directly is worth more here than it would be at most brokerages.

The absence of a public API specification for Closio is a procurement concern independent of ownership. A website integration, a HubSpot sync and any future automation all depend on one.

---

## 5. Automations

| | Zoho | GoHighLevel | Closio |
|---|---|---|---|
| Trigger-based rules | Workflow Rules, 50 per module on Professional | Workflow builder | Automatic lead routing by language and listing type |
| Follow-up sequences | Cadences, including WhatsApp template steps | Campaigns across channels | Automatic email broadcasts to segments |
| Process enforcement | Blueprint, stage by stage, Professional tier | Pipeline stages | Pipeline |
| Custom code | Deluge functions, Professional tier | Limited | None exposed |
| AI assistance | Zia, Enterprise tier only | Included, deeply integrated | AI agent included, core to the product |

Zoho Professional at $23 unlocks both Blueprint and Deluge, which are the two capabilities that matter for enforcing a sales process and for reaching anything the native integrations miss. Zia, Zoho's own AI layer, sits on Enterprise at $40 and is not required, because Claude covers that ground through the MCP server.

Closio's automation is narrower but aimed precisely at this industry. Routing leads by spoken language and listing type is a real brokerage problem that generic platforms leave to configuration.

---

## 6. Workflow Setup

The practical question is how much work stands between signing and agents using the system.

**Zoho: two to four weeks of configuration.** The property module, matching logic and commission calculations are all buildable and none exist on day one. This is known, bounded work for the development team. The risk is that a poorly designed layout kills agent adoption, so the configuration should be judged on how fast an agent can enter a villa, not on how complete the field list looks.

**GoHighLevel: fast to stand up, wrong shape underneath.** Reviews consistently describe a difficult first month because the platform exposes everything at once without a guided order. The deeper issue is that no amount of configuration produces a property object.

**Closio: fastest by a wide margin.** The vendor states the AI agent is live roughly 24 hours after the WhatsApp number is connected, and most agencies are fully operational within seven days, with onboarding, data import and training included in the price. For a brokerage opening in weeks, that is a material advantage.

---

## 7. Listing Website Integration

This matters more than usual because the brokerage website does not exist yet. BSH can design the site around whichever CRM it picks, rather than forcing a CRM to fit an existing site.

**Zoho.** No website product. The site gets built by the development team against Zoho's REST API, with webhooks triggering an update when a property record changes. Most control, most work, no lock-in. The property schema should be designed first and the site built around it.

**GoHighLevel.** Website and funnel builder included. Good for landing pages and lead capture, poor as a property catalogue, because the underlying records are contacts and opportunities rather than listings.

**Closio.** Connects to an existing website and syncs listings automatically, with publish, update and remove driven from the CRM. A website is explicitly not included, though the vendor will build one as a separately quoted project.

All three put the CRM in charge of listings. The difference is how much BSH builds and how much it rents.

---

## 8. WhatsApp and Agent Follow-Up

WhatsApp deserves its own section because it does not behave like email, and because Meta changed the economics on 1 October 2026.

**The three rules:**

- A client message opens a 24-hour window. Inside it, any message can be sent, including AI-generated replies. Each new client message resets the clock.
- Outside that window, only templates approved in advance by Meta may be sent, and only to clients who have explicitly opted in.
- Message quality is rated, and numbers that behave like spam get restricted. A restricted brokerage number during launch month would be severe.

**What changed on 1 October 2026:** free-form replies inside the 24-hour window are now billed per message, where previously they were free. AI-generated messages are billed as a separate and more expensive category, estimated by one provider at $0.04 to $0.05 each. Most published guidance still describes the old model and should be disregarded.

**The offset:** advertisements that click through to WhatsApp open a 72-hour free entry point, on a separate timer. For a brokerage advertising on Meta, which is the expected primary lead source, those conversations carry no message cost for three days.

**Cost model for AI qualification:** a ten-message qualifying exchange costs roughly $0.40 to $0.50. At 200 inbound leads per month, that is $80 to $100. Set against agent hours spent asking the same five qualifying questions repeatedly, the economics are favourable.

**Agent follow-up, by vendor:**

| | Zoho | GoHighLevel | Closio |
|---|---|---|---|
| Official WhatsApp Cloud API | Included in paid plans | $10/mo add-on | Included |
| Template sequences | Cadences support WhatsApp follow-up steps | Campaigns | Not specified |
| AI qualification bot | SalesIQ Zobot, $20/operator | Included | Core product feature, 30+ languages |
| Multi-agent assignment | Yes | Yes | Yes, routed by language and listing type |
| Billing model | Meta rates | Prepaid wallet | Within quoted conversation volume |

Two practical cautions:

**Agents keeping their own WhatsApp numbers** is possible through Meta's Coexistence feature, which runs the Business app and the Cloud API on one number simultaneously without losing history. Availability depends on country, provider and the individual number, so it must be confirmed for Indonesian numbers before anything is promised to agents. Unofficial QR-code bridging tools carry a genuine risk of the number being banned and should not be used.

**GoHighLevel bills usage from a prepaid wallet, and a negative balance halts service.** For a brokerage whose WhatsApp line is its primary channel, that is an operational risk rather than an accounting detail.

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

### Zoho CRM Professional

**Advantages**

- Custom modules model Indonesian property precisely: title types, lease years remaining, dual-currency pricing, local land measurement. Nothing is forced into a foreign market's conventions.
- Official WhatsApp Cloud API included in the plan rather than sold as an add-on.
- Official MCP server with published Claude setup, the only candidate answering the AI requirement through a supported route.
- Native Slack, Gmail, Google Calendar and Google Drive integration.
- Full REST API, webhooks and Deluge scripting, so the development team can reach anything the native integrations miss, including Meta's Conversions API.
- Blueprint enforces the sales process stage by stage, which matters when onboarding new agents.
- Cadences support WhatsApp follow-up steps alongside email.
- Zoho has been independent and profitable for over 25 years. No funding or acquisition risk.
- At $184 per month, over $300 of the monthly budget remains for messaging and synchronisation tooling.

**Disadvantages**

- Nothing is configured on day one. Two to four weeks of development work precede agent use.
- Buyer-to-listing matching is built with workflow rules rather than supplied.
- The administrative interface is dated and extensive. Adoption depends on layout design quality.
- Professional caps custom modules and fields per module, which must be checked against the property schema.
- Listing photograph handling at 25 to 40 images per villa is unproven and may require WorkDrive alongside.
- Zia AI sits on the Enterprise tier.
- No Indonesian data centre. Australia or India must be chosen deliberately.
- Per-seat pricing rises with headcount, reaching $575 per month at 25 agents.

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

## 11. Recommendation and Rollout

**Select Zoho CRM Professional.** Confirm whether Zoho One at $296 per month is viable given its per-employee licensing, since it is cheaper than buying CRM and SalesIQ separately and includes considerably more.

**Hold Apimo as the alternative.** A French platform built for international non-MLS markets at €139 per month flat, with native property matching, multi-currency handling, commission tracking and its own website product. It scored level with Zoho. Zoho was preferred because its weakness is configuration work with a deadline, while Apimo's weakness is an absent integration surface that cannot be built on the vendor's behalf.

**Phase 1, weeks 1 to 4.** Property module, contact model, pipeline, permissions. Brokerage WhatsApp number onto the Cloud API. Agents logging every deal from the first working day. That is the only success measure that matters at this stage.

**Phase 2, weeks 4 to 10.** Brand and website built against the CRM API, with listings published from the CRM.

**Phase 3, months 3 to 4.** HubSpot two-way synchronisation on contacts and deals. Claude workflows through the MCP server. Commission module with confirmed formulas.

**Phase 4, as required.** Agent WhatsApp Coexistence subject to eligibility. Portal feeds once partnerships are in place. Meta Conversions API so advertising optimises toward closed deals rather than form submissions.

**Success measures.** At 30 days, every agent logs every deal in the CRM and nothing is tracked in spreadsheets. At 90 days, website listings match CRM listings without manual intervention and no follow-up sits untouched beyond seven days. At 180 days, commissions calculate in the system and management sees brokerage pipeline without asking.

---

## 12. Risks and Open Items

| Risk | Consequence | Mitigation |
|---|---|---|
| Zoho workflow rules may not trigger WhatsApp sends reliably | The follow-up automation case collapses | Test explicitly during trial. Documentation and user reports conflict. Fallback is a dedicated platform at about $199/mo |
| Indonesian WhatsApp rates unknown after the 1 October change | Bot running costs unbudgeted | Obtain written rates from the provider before signing |
| Property schema may exceed Professional tier limits | Forced upgrade to Enterprise at $40/seat | Verify field and module caps against the schema first |
| Agent adoption fails | The system becomes a second place to type things | Time the villa-entry workflow during trial. Beyond 10 minutes, redesign |
| No named administrator | The tool goes unused | Assign to the planned Admin and Listings Coordinator role |
| HubSpot record ownership undefined | The two systems overwrite each other | Agree ownership rules with management before enabling synchronisation |
| Commission formulas not documented | The commission module cannot be built | Document co-broke, profit share and overriding commission formulas |

**Before signing, confirm:** Zoho Professional module and field limits against the property schema; listing photograph handling; Coexistence eligibility for Indonesian numbers; data centre selection; IDR formatting at nine figures; Zoho One licensing viability; and whether Meta Conversions API work belongs at launch or in Phase 3.

**Trial plan.** Two weeks, Zoho and Apimo in parallel, using ten real listings with photographs and twenty real leads. Six scenarios: enter a villa and time it; match a buyer against inventory; change a price and confirm it reaches the website; log a WhatsApp conversation end to end; calculate a commission on a co-broked deal; and fire an automation into WhatsApp. Submit a support ticket to each vendor and time the reply. Obtain one reference from a customer the vendor did not nominate.

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
