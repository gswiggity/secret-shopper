# Secret Shopper — Feature Priority Matrix

> Impact vs. Effort scoring for all features, mapped to release phases.
> **Impact**: How much value this delivers to users and the business (1-5).
> **Effort**: Engineering and operational complexity (1-5, where 5 = hardest).
> **Priority Score**: Impact / Effort (higher = do first).

---

## MVP Features (Months 1-3)

Ship these first. They prove the core value proposition and drive waitlist-to-active conversion.

| Feature | Impact | Effort | Score | Notes |
|---------|--------|--------|-------|-------|
| **Email OAuth + historical parse** | 5 | 3 | 1.67 | The activation moment. User connects email, instantly sees purchase history. Gmail + Outlook cover ~80% of users. |
| **Purchase timeline view** | 5 | 2 | 2.50 | Core dashboard. List of all purchases extracted from email, searchable, browsable. |
| **Shipping tracker aggregation** | 4 | 2 | 2.00 | High daily utility. Parse tracking numbers from emails, show delivery status. Use carrier APIs or scraping. |
| **Promo code extraction (email)** | 5 | 2 | 2.50 | Scan email for promo codes, surface unexpired codes per retailer. Immediate tangible value. |
| **Return window tracking** | 4 | 2 | 2.00 | Parse return policies from order confirmations, countdown to deadline, push notification alerts. |
| **Basic browser extension** | 4 | 3 | 1.33 | Chrome Manifest V3. Detect checkout pages, capture cart contents, surface known promo codes. |
| **Promo code database (public)** | 3 | 2 | 1.50 | Scrape public promo aggregators. Supplement email-found codes. |
| **Basic spend analytics** | 3 | 1 | 3.00 | "You spent $X at Amazon this month." Simple aggregation from parsed purchases. |
| **Onboarding flow** | 4 | 2 | 2.00 | Email connect → initial parse → "Here's what we found" moment. Needs to feel magical. |
| **Waitlist landing page** | 3 | 1 | 3.00 | Pre-launch acquisition. Email capture, value prop, maybe a "scan your email" teaser. |

**MVP Definition of Done:** A user can connect their email, see their purchase history, get shipping updates, find promo codes, and track return windows — all in one place.

---

## V2 Features (Months 4-7)

These deepen engagement and unlock premium revenue. Ship after MVP is validated with beta users.

| Feature | Impact | Effort | Score | Notes |
|---------|--------|--------|-------|-------|
| **Email alias generation** | 5 | 4 | 1.25 | Core privacy feature. Requires email infrastructure (MX, relay, spam filtering). High value but operationally complex. |
| **Alias management dashboard** | 4 | 2 | 2.00 | Per-retailer alias view, forwarding rules, spam stats, one-tap revocation. |
| **Universal cart monitor** | 4 | 3 | 1.33 | Track carts across retailers via extension. Requires broad retailer compatibility. |
| **Abandoned cart strategy ("Cold Cases")** | 5 | 3 | 1.67 | The "aha" feature. "You abandoned this cart 3 days ago — wait 2 more days for a likely promo." Needs prediction model. |
| **AI promo timing predictions** | 5 | 4 | 1.25 | "78% chance of 15% off in 2 days." Requires training on behavioral data. High impact but needs data volume. |
| **Historical price tracking** | 4 | 3 | 1.33 | Price charts per product. Requires persistent price monitoring infrastructure. |
| **Price drop alerts** | 4 | 2 | 2.00 | Notify user when tracked product drops below threshold. Straightforward once price tracking exists. |
| **Buy now vs. wait recommendation** | 4 | 3 | 1.33 | AI recommendation combining price history, seasonal patterns, promo predictions. |
| **Continuous email monitoring** | 4 | 3 | 1.33 | Real-time processing of new emails (not just historical scan). Webhook or polling infrastructure. |
| **Smart email filtering** | 3 | 3 | 1.00 | Suppress marketing, surface actionable only. Nice-to-have, not critical path. |
| **Full browser extension** | 4 | 3 | 1.33 | Auto-apply codes, price history overlay, cross-retailer comparison. Firefox + Safari support. |
| **Premium tier + billing** | 5 | 3 | 1.67 | Stripe integration, tier management, feature gating. Required for revenue. |
| **Cross-device sync** | 3 | 3 | 1.00 | Cloud sync for purchase data and settings. Users expect this but local-first is the differentiator. |
| **Warranty/receipt storage** | 3 | 2 | 1.50 | Document upload and storage per purchase. Low effort, moderate value. |

**V2 Definition of Done:** Premium tier is live and generating revenue. Users have full proxy email system, cart monitoring with AI predictions, and price intelligence.

---

## V3 Features (Months 8-12)

These expand the platform into new value areas and unlock B2B revenue streams.

| Feature | Impact | Effort | Score | Notes |
|---------|--------|--------|-------|-------|
| **Retailer Shield Score** | 4 | 4 | 1.00 | Trust scoring per retailer (spam, dark patterns, data sharing). Requires significant data + editorial framework. |
| **Crowdsourced behavior patterns** | 5 | 4 | 1.25 | Aggregated community intelligence on retailer behavior. Needs opt-in framework + anonymization pipeline. |
| **Independent brand evaluation program** | 4 | 5 | 0.80 | B2B revenue stream. High operational complexity (hiring evaluators, building methodology, partner relationships). |
| **Social media brand extraction** | 3 | 3 | 1.00 | Read Instagram/TikTok/Pinterest follows. API access varies; some platforms make this hard. |
| **Conscious shopping alternatives** | 4 | 4 | 1.00 | Product alternatives by values (sustainability, local, small biz). Needs product database + certification data. |
| **Greenwashing detection** | 3 | 4 | 0.75 | Cross-reference marketing claims vs. certifications. High editorial/research effort. |
| **Consumer org partnerships** | 4 | 3 | 1.33 | Integrate Consumer Reports-type data. Revenue sharing. Primarily a business development effort. |
| **In-app browser** | 3 | 4 | 0.75 | Full browsing within Secret Shopper. High effort, moderate incremental value over extension. |
| **B2B data insights product** | 3 | 4 | 0.75 | Anonymized aggregate data for market researchers. Needs sales team + data pipeline + compliance. |
| **Family/household plan** | 3 | 3 | 1.00 | Shared intelligence, individual privacy. Billing + multi-profile architecture. |

**V3 Definition of Done:** Brand evaluation program generating B2B revenue. Full conscious shopping experience live. Crowdsourced intelligence powering predictions at scale.

---

## Feature Dependencies

```
Email OAuth (MVP)
  └─→ Purchase Dashboard (MVP)
  └─→ Promo Code Extraction (MVP)
  └─→ Shipping Tracking (MVP)
  └─→ Return Window Tracking (MVP)
  └─→ Continuous Email Monitoring (V2)
       └─→ Smart Email Filtering (V2)

Browser Extension - Basic (MVP)
  └─→ Cart Capture (V2)
       └─→ Universal Cart Monitor (V2)
       └─→ Abandoned Cart Strategy (V2)
  └─→ Full Extension (V2)
       └─→ Auto-apply Codes (V2)
       └─→ Price History Overlay (V2)

Email Infrastructure (V2) ← new dependency
  └─→ Email Alias Generation (V2)
  └─→ Alias Management (V2)
       └─→ Alias Analytics (V3)

Price Monitoring Infrastructure (V2)
  └─→ Historical Price Tracking (V2)
  └─→ Price Drop Alerts (V2)
  └─→ Buy Now vs. Wait (V2)

Behavioral Data Collection (V2)
  └─→ AI Promo Predictions (V2)
  └─→ Crowdsourced Patterns (V3)
  └─→ Retailer Shield Score (V3)

Opt-in Anonymization Pipeline (V2)
  └─→ Community Intelligence (V3)
  └─→ B2B Data Insights (V3)

Brand Evaluation Framework (V3)
  └─→ Shield Scores (V3)
  └─→ Conscious Shopping (V3)
  └─→ Greenwashing Detection (V3)
  └─→ Consumer Org Partnerships (V3)
```

---

## What to Build First (Sprint Plan Sketch)

### Sprint 1-2 (Weeks 1-4): Foundation
- Email OAuth integration (Gmail + Outlook)
- Email parser: order confirmations, tracking numbers, promo codes
- Core data model: purchases, retailers, products, promos
- Basic purchase timeline UI

### Sprint 3-4 (Weeks 5-8): Core Dashboard
- Shipping tracking aggregation (carrier API integration)
- Return window extraction and countdown alerts
- Promo code surfacing per retailer
- Search across purchases
- Basic spend analytics

### Sprint 5-6 (Weeks 9-12): Extension + Polish
- Chrome extension: checkout detection, cart capture, promo overlay
- Onboarding flow optimization
- Notification system (return reminders, shipping updates)
- Beta launch preparation
- Waitlist landing page

### Beta Launch: Week 12-13
- Invite first cohort from waitlist
- Measure activation, retention, engagement
- Iterate based on feedback
