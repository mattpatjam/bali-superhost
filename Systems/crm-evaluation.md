# BSH Brokerage CRM Evaluation

*Created: 2026-10-11*
*Status: research complete, trials not started, no decision made*
*Owner: Matthieu*

---

## 1. Need Brief

**The problem:** the BSH brokerage is a new brand launching in weeks. It has no CRM, no website, and no listing database. BSH Management runs HubSpot for its own pipeline. HubSpot is a competent B2B CRM and a poor fit for brokerage work, for one specific structural reason covered in Section 3.

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

**Required integrations:**
- Listing website (does not exist yet, so it gets built against whichever CRM wins)
- HubSpot, two-way, on contacts and deals
- WhatsApp, official Cloud API on the brokerage number
- Slack, email, Google Drive
- Claude, via API or MCP, for follow-up drafting and task triage

**Stakeholders:** Matthieu (owner and champion), BSH management (holds HubSpot, needs to approve a second system), BSH dev team (builds the glue and the website), 4 to 6 brokerage agents (the actual users, and the ones who decide whether this succeeds).

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

HubSpot's custom objects are Enterprise only, confirmed on HubSpot's own knowledge base and still true as of April 2026. Professional is limited to the four standard objects: contacts, companies, deals, tickets. There is no property object, and a villa is not a company or a deal.

The workarounds are both bad:
- Model each villa as a Company record. Breaks reporting, breaks buyer matching, and corrupts management's own company data in the shared portal.
- Upgrade to Sales Hub Enterprise. Roughly $150 per seat per month, so about $1,200 per month at 8 seats, plus a required one-time onboarding fee. That is more than twice the entire CRM budget, to get an object the €139 per month option has natively.

**This is the argument to take to management.** It is not a preference or a taste question. HubSpot charges Enterprise prices for the one capability a brokerage cannot operate without, and a purpose-built alternative includes it at a tenth of the cost. Keeping HubSpot for management and adding a brokerage CRM is the cheaper option, not the indulgent one.

---

## 4. Shortlist

Longlist considered: HubSpot (Pro and Enterprise), Attio, Pipedrive, Zoho CRM, Zoho One, GoHighLevel, Apimo, Rex Software, Propertybase/Lone Wolf, Closio Estate, Follow Up Boss, BoldTrail, Lofty, Top Producer, Wise Agent, Real Geeks, EspoCRM.

**Eliminated, with reasons:**

| Tool | Why out |
|---|---|
| HubSpot Pro/Enterprise | Custom objects are Enterprise only. About $1,200/mo at 8 seats plus onboarding. See Section 3. |
| Attio | Custom objects are Pro and Enterprise only, per Attio's own docs. Pro is $79/seat annual, so about $632/mo at 8 seats. Plus is capped at 5 total objects anyway, including the standard three. Excellent MCP server and API, genuinely good product, simply over budget for the object model needed. Revisit if the team stays at 4 seats. |
| Pipedrive | Cheapest credible option at $14 to $49/seat, but it supports fewer record types than HubSpot or Attio. No real property object. Lead capture and web tracking are priced as separate add-ons. Pipeline tool, not a property system. |
| Follow Up Boss, BoldTrail, Lofty, Top Producer, CINC, Real Geeks, iHomefinder, Wise Agent | MLS and IDX dependent. See Section 3, Finding 1. |
| Propertybase / Lone Wolf | Salesforce-based, enterprise pricing and implementation cycle. Wrong scale and wrong timeline. |
| Rex Software | Right market model (non-MLS), public API, quote-only pricing, AU-specific portals. Hold as backup. |
| Closio Estate | **Ruled out on competitive exposure. See Section 3, Finding 3.** |

**Three finalists, one per category, as requested:**

1. **Zoho CRM Professional** ($23/seat/mo annual) — the flexible CRM shaped into a real estate system
2. **Apimo CRM AI+** (€139/mo flat) — the opinionated real estate product built for international non-MLS markets
3. **GoHighLevel Unlimited** ($297/mo flat) — the marketing-led all-in-one

---

## 5. Scorecard

Weights adjusted from the standard rubric for this situation. Technical fit is raised to 25% because the website does not exist yet and will be built against the CRM's API, making API quality a launch dependency rather than a nice-to-have. Security is lowered to 5% because no regulated or health data is involved.

| Dimension | Weight | Zoho CRM Pro | Apimo CRM AI+ | GoHighLevel |
|---|---|---|---|---|
| Functional fit (property model, matching, commissions) | 35% | 3.5 | 5.0 | 2.0 |
| Technical fit (API, website, HubSpot, Claude, Slack, Drive) | 25% | 5.0 | 3.0 | 3.5 |
| Operational fit (time to launch, admin burden) | 10% | 3.0 | 4.5 | 3.5 |
| Cost at 8 seats | 10% | 5.0 | 5.0 | 4.0 |
| Vendor health | 8% | 5.0 | 4.0 | 3.5 |
| Lock-in risk / data portability | 7% | 4.0 | 3.0 | 2.0 |
| Security and compliance | 5% | 4.0 | 3.5 | 3.0 |
| **Weighted total** | **100%** | **4.16** | **4.16** | **2.90** |

**Zoho and Apimo tie, and the tie is the real finding.** Apimo wins the property model outright. Zoho wins the integration surface outright. GoHighLevel loses on the thing a brokerage needs most.

### Per-finalist detail

**Zoho CRM Professional, $23/seat/mo annual ($184/mo at 8 seats)**

Strengths:
- Custom modules let the dev team model Properties, Viewings, and Commission Splits exactly as Bali works: SHM, HGB, Hak Pakai, leasehold with years remaining, IDR and USD dual pricing, land size in are and sqm. Nothing has to be bent to fit a US convention.
- Official WhatsApp Cloud API support is built into the paid plans, not an add-on. Cheapest full CRM with official API messaging included.
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

## 6. Recommendation

**Primary: Zoho CRM Professional. Backup: Apimo CRM AI+.**

The two tie on score, so the tiebreaker is which weakness is fixable.

- Zoho's weakness is that the property model has to be configured. That is 2 to 4 weeks of dev work, it is a known quantity, and the dev team already exists.
- Apimo's weakness is that the integration surface is missing. HubSpot, Slack, WhatsApp and Claude are either absent or unverified. That is not configuration work, it is custom integration against a smaller vendor's API for every single one of the stated requirements.

Configuration work has a deadline. Missing integration surface does not.

Zoho also happens to be the only finalist that answers the Claude requirement properly, with an official MCP server and documented Claude setup. Given how much of BSH's intended workflow runs through Claude, that is not a minor line item.

**Choose Apimo instead if, during trials, either of these turns out true:**
- The property schema cannot be built cleanly inside Zoho Professional's custom module and field limits
- The team has no appetite for configuration work and needs something that works on day one with no build

**Budget headroom:** at $184/mo, Zoho leaves over $300/mo of the budget free. Spend some of it on a WhatsApp BSP and the HubSpot sync tool, and keep the rest as reserve. Do not spend it on seats.

---

## 7. Integration Architecture

How the pieces actually connect, assuming Zoho.

**Website (the listing site)**
- The CRM is the single source of truth for listings. Nothing is ever entered on the website.
- The site is built after the CRM is chosen, reading from the Zoho CRM API, with webhooks triggering a rebuild or cache invalidation when a property record changes.
- Since the brand does not exist yet, this is the easy case. Design the property schema first, then design the site around it. Not the reverse.

**HubSpot, two-way**
- Sync contacts and deals only. Properties stay brokerage-side, because HubSpot cannot hold them without Enterprise.
- Options: Zoho Flow (cheapest, already in the Zoho ecosystem), Whalesync or Stacksync (purpose-built two-way sync, visual setup, no code), or HubSpot Operations Hub Starter at $45/mo.
- Ownership rules have to be decided before switching the sync on, or the two systems will fight. Proposal: management owns the record for management clients, the brokerage owns it for brokerage-sourced leads, matched on phone number as the shared key, with the owning side winning on conflict. Confirm with management.

**WhatsApp**
- Brokerage main number: onto the official Cloud API, inside the CRM, with per-conversation assignment to an agent. This is the standard supported pattern and it gives ownership, routing, and an audit trail.
- Agents' own numbers: there is now an official Meta feature called **Coexistence** that lets the WhatsApp Business app and the Cloud API run on the same number simultaneously, mirroring messages in real time, without losing chat history. That is exactly what you asked for. Two caveats: it is rolling out gradually and eligibility depends on country, BSP, and the number itself, so it has to be verified for Indonesian numbers with the chosen BSP before anything is promised to agents. Also, onboarding an existing Business app number to the Cloud API unlinks its companion devices.
- **Do not use QR-code or unofficial WhatsApp bridges.** They are the actual ban risk, as opposed to multi-agent access done officially, which is fine. A banned brokerage number in week three would be a disaster.
- Without Coexistence, the fallback is the standard pattern: one official company number as the inbound and automation channel, agents keep personal numbers in the app, and personal threads are not logged. Acceptable to launch on, worth fixing later.

**Claude**
- Zoho MCP server, with the official Claude setup guide. Lets Claude query pipeline, draft follow-ups, and write records directly.
- First use cases worth building: a daily "who is owed a follow-up" brief, drafting WhatsApp and email follow-ups from the record history, and triaging new inbound leads against live inventory.

**Slack and Google Drive**
- Both native Zoho CRM integrations. Slack for deal and listing alerts into a channel. Drive for attaching mandates, title documents, and photos to property records.
- Check whether listing photos belong in Drive or in Zoho WorkDrive. Photos are a volume problem the CRM may not handle well.

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

---

## 9. Trial Plan

Two weeks, both finalists in parallel, real data not sample data.

Load into each: 10 real listings with real photos and real IDR prices, and 20 real leads with real history.

Then run these five scenarios in both, and time them:

1. **Intake a listing.** Full villa record with title type, lease years remaining, dual-currency price, land and building size, 25 photos, owner contact, mandate document. Time it. If it takes an agent more than 10 minutes, adoption will fail.
2. **Match a buyer.** A buyer wants leasehold, under $400K, Canggu or Berawa, sea view. How many clicks to get the matching inventory, and can it fire automatically when a new listing lands?
3. **Publish a price change.** Change a listing price and confirm it reaches the website, or in the trial, confirm the API exposes the change and a webhook fires.
4. **Log a WhatsApp conversation.** Inbound message to the brokerage number, assigned to an agent, replied to, and visible on the contact record afterwards.
5. **Calculate a commission.** One closed deal with a co-broke split, agent commission, and BSH profit share. Does the system produce the numbers, or does it still need a spreadsheet?

Also, during the trial window:
- Submit a real support ticket to each vendor and time the response. This is the cheapest vendor-health signal available.
- Get one reference call per finalist, from a customer the vendor did not suggest. For Apimo specifically, try to find one in Asia.

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
