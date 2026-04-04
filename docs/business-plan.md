# Secret Shopper — Business Plan

---

## Revenue Model

Secret Shopper generates revenue through four streams, ordered by expected contribution timeline.

### Stream 1: Freemium Subscription (Primary — from launch)

The core business model. Free tier drives adoption; premium tier drives revenue.

**Free Tier:**
- Purchase dashboard with email parsing (full purchase history, shipping tracking)
- Basic promo code surfacing (codes found in your email)
- Limited retailer aliases (3-5 retailers)
- Basic return window tracking
- Browser extension with manual code lookup

**Premium Tier (price TBD — exploring $5-7, $10-15, and $15-25 ranges):**
- Unlimited email aliases (full proxy identity system)
- AI promo timing predictions ("Wait 2 days — 78% chance of 15% off")
- Advanced price monitoring with historical charts
- Strategic cart abandonment coaching
- Full cart monitoring across all retailers
- Conscious shopping features (sustainability scoring, alternatives, greenwashing detection)
- Priority support
- Advanced analytics (spend trends, savings reports, retailer behavior insights)

**Family/Household Plan:**
- Shared intelligence (combined behavioral data improves predictions for all members)
- Individual privacy (family members don't see each other's purchases or browsing)
- Single billing, multiple profiles

**Pricing Strategy:**
Pricing is undecided. The approach is to launch premium at one price point during beta, measure conversion and churn, then optimize. Key considerations:
- $5-7/mo: Accessible, high-volume play. Risk: perceived as "just another subscription"
- $10-15/mo: Premium positioning. Comparable to other productivity tools. Sweet spot if retention is strong.
- $15-25/mo: Premium-premium. Only viable if the savings demonstrably exceed the cost (need "Secret Shopper saved you $X this month" to exceed subscription price)
- Annual discount (e.g., 2 months free) to improve retention and cash flow

### Stream 2: Independent Brand Evaluation (B2B — from V3)

The unique differentiator. Secret Shopper becomes a trusted authority on brand behavior.

**How it works:**
1. Brands pay Secret Shopper to undergo an independent evaluation of their practices
2. Evaluation covers: pricing transparency, email practices, return policies, data handling, sustainability claims, customer service quality
3. Results are published transparently — **brands cannot influence the outcome**
4. Brands that meet standards receive a "Evaluated by Secret Shopper" certification badge
5. Revenue comes from the evaluation fee, not from favorable results

**Who evaluates:**
- **In-house team:** Core evaluation framework, methodology, and quality control
- **Partner organizations:** Consumer Reports-type orgs per industry vertical (electronics, fashion, beauty, home goods, etc.)
- **Community + editorial:** User-contributed data (anonymized behavioral signals) with editorial oversight from Secret Shopper's team

**Why brands pay:**
- Consumer trust is increasingly valuable and hard to earn
- "Evaluated by Secret Shopper" becomes a trust signal that drives purchase decisions
- Brands get actionable feedback on how to improve (whether they pass or not)
- As Secret Shopper's user base grows, the certification carries more weight

**Revenue mechanics:**
- Evaluation fee: per-evaluation or annual certification renewal
- Tiered pricing based on brand size/revenue
- Premium listing in Secret Shopper's "Trusted Retailers" section (but never paid placement in search/recommendations)

### Stream 3: Aggregated Intelligence (B2B — from scale)

Anonymized, aggregated consumer behavior data — the exhaust of the platform becomes valuable.

**What we sell:**
- Shopping behavior trends (cart abandonment rates by category, price sensitivity curves)
- Brand loyalty and switching patterns (anonymized)
- Promo effectiveness data (which discount types drive conversion, optimal timing)
- Seasonal shopping pattern reports
- E-commerce industry benchmarks

**Who buys:**
- Market research firms
- Brands seeking honest competitive intelligence
- Investment firms analyzing e-commerce trends
- Industry publications

**Strict anonymization:**
- No individual user data ever sold
- Minimum aggregation thresholds (no data point represents fewer than N users)
- Users can opt out of contributing to aggregated data entirely
- Regular third-party audits of anonymization practices

### Stream 4: Industry Partnerships (B2B — from V3)

Secret Shopper as the aggregation and distribution layer for independent consumer intelligence.

**Model:**
- Partner with existing trusted organizations (Consumer Reports, Wirecutter-type publications, industry-specific reviewers)
- Secret Shopper surfaces partner ratings/reviews within the app alongside its own data
- Revenue sharing on premium content and ratings
- Co-branded evaluation programs per vertical
- Specific research engagements leveraging Secret Shopper's behavioral data

---

## Competitive Positioning

### The Closed Loop Advantage

```
Competitors:
  Honey          → Coupons only
  Privacy.com    → Cards only
  Shop App       → Tracking only
  Capital One    → Price alerts only (ecosystem-locked)

Secret Shopper:
  Email Intelligence → Promo Prediction → Cart Strategy →
  Purchase Tracking → Return Management → Brand Intelligence
  ─── all connected, all in one place ───
```

### Head-to-Head

| Dimension | Honey | Privacy.com | Shop App | Cap One Shopping | Secret Shopper |
|-----------|-------|------------|----------|-----------------|----------------|
| Promo codes | Strong | None | None | Moderate | Strong + AI timing |
| Email protection | None | None | None | None | Full proxy system |
| Purchase tracking | None | None | Strong (Shopify only) | None | Universal |
| Price intelligence | None | None | None | Good | Good + predictions |
| Cart strategy | None | None | None | None | Unique |
| Privacy posture | Weak (PayPal) | Strong | Weak (Shopify) | Weak (bank) | Strong (local-first) |
| Business model conflict | Affiliate commissions | Subscription | Shopify ecosystem | Credit card cross-sell | User-aligned subscription |

### Defensible Moat

The moat is not any single feature — it's the **behavioral prediction dataset** that compounds over time:
- Every cart abandonment teaches the system about retailer promo timing
- Every promo code validates or updates the prediction model
- Every purchase enriches price history and seasonal pattern data
- Every user who opts in to anonymized sharing makes the intelligence better for everyone

This dataset is proprietary, grows with the user base, and creates a flywheel: better predictions → more users → more data → better predictions.

---

## Go-to-Market Strategy

### Phase 1: Waitlist Beta (Months 1-3)

**Build:**
- MVP: Purchase Dashboard + Promo Intelligence + basic browser extension
- Landing page with waitlist signup
- Target: 1,000-5,000 waitlist signups before beta launch

**Acquire waitlist signups via:**
- Content marketing: "How much are you really spending at Amazon?" calculator/tool
- Reddit communities: r/frugal, r/deals, r/privacy, r/personalfinance
- Twitter/X threads on retailer dark patterns and shopping intelligence
- Product Hunt launch for the browser extension (free tier)

### Phase 2: Invite-Only Beta (Month 3-4)

**Goals:**
- Validate core value prop (do users come back after connecting email?)
- Measure: email permission grant rate, daily active usage, feature engagement
- Identify: which persona type activates fastest, what's the "aha moment"
- Iterate rapidly based on user feedback

**Key metrics to track:**
- Email OAuth completion rate (% of signups who actually connect email)
- Day 1, Day 7, Day 30 retention
- Feature engagement (which modules get used most)
- NPS / qualitative feedback
- Promo codes found per user per month (tangible value metric)
- Time saved per user (self-reported or estimated)

### Phase 3: Public Launch (Month 4-6)

**Expand:**
- Open signups
- Launch premium tier
- Expand browser extension to Firefox/Safari
- Begin content marketing at scale

**Acquisition channels:**
- Browser extension as top-of-funnel (free email parsing gets users in the door)
- Word of mouth from beta users
- Content marketing: retailer transparency reports, shopping intelligence blog
- Influencer partnerships (personal finance, frugal living, privacy-focused creators)
- App Store / Play Store optimization

### Phase 4: Growth (Month 6+)

- Launch V2 features (proxy aliases, cart monitoring, price tracking)
- Begin brand evaluation program (Stream 2 revenue)
- Explore partnerships with consumer organizations
- International expansion considerations

---

## Funding Strategy

### Bootstrap Phase (Months 1-4)

- Self-funded prototype and MVP development
- Minimal team: founder(s) + contractor development support
- Infrastructure costs kept low (local-first architecture = less server spend)
- Target: working MVP with beta traction data

### Seed Raise (Month 4+)

**When to raise:** Once beta data shows strong signal on:
- Email permission grant rate > 60%
- Day 30 retention > 30%
- Premium conversion > 5% (of beta users offered premium)
- Qualitative evidence of "can't live without it" engagement

**What to raise for:**
- Engineering team (2-3 full-time engineers for V2 features)
- Email proxy infrastructure (V2 alias system)
- AI/ML development for prediction models
- Partnership development (Consumer Reports-type orgs)
- Marketing for public launch

**Pitch angles:**
- Proven demand via beta metrics
- Existing browser extension and virtual card products (from collaborator) prove execution ability
- Unique revenue model (evaluation revenue) beyond just subscription
- Compounding data moat
- $900M-$2.4B TAM for subscription alone (see competitive landscape doc)

---

## Cost Structure

### MVP Phase (Low)
- Cross-platform app development (contractor or founder-built)
- Email parsing API costs (Gmail/Outlook API — free tier covers early users)
- Basic cloud infrastructure (auth, account management, sync)
- Browser extension hosting (Chrome Web Store — minimal cost)
- Domain and email infrastructure for aliases (minimal at low volume)

### Growth Phase (Moderate)
- Email proxy infrastructure (MX records, relay servers, spam filtering)
- AI/ML compute for prediction models
- Engineering salaries (2-3 FTE)
- App store fees (Apple 15-30%, Google 15%)
- Customer support
- Marketing spend

### Scale Phase (Higher)
- Dedicated ML/data team for prediction model improvement
- Evaluation team for brand assessment program
- Partnership development team
- International infrastructure
- Compliance and security (SOC 2, privacy audits)

---

## Key Metrics

### North Star Metric
**Monthly savings per user** — the dollar amount Secret Shopper demonstrably saves each user through promo codes, price drop alerts, and timing optimization. This is the metric that drives retention, premium conversion, word of mouth, and ultimately revenue.

### Supporting Metrics

| Category | Metric | Target (Beta) |
|----------|--------|---------------|
| Acquisition | Waitlist signup rate | 1,000+ pre-launch |
| Activation | Email OAuth completion | > 60% of signups |
| Engagement | Weekly active users | > 50% of activated |
| Retention | Day 30 retention | > 30% |
| Revenue | Premium conversion | > 5% of active users |
| Value | Promos found / user / month | > 3 |
| Value | Monthly savings / user | > subscription cost |
| Community | Data opt-in rate | > 40% |
| Growth | Organic referral rate | > 10% of new users |

---

## Risk Factors

| Risk | Severity | Mitigation |
|------|----------|------------|
| Email API access revoked (Gmail tightens OAuth) | High | Diversify email access methods; build direct IMAP support as backup |
| Retailers block alias emails | Medium | Rotate alias patterns; use custom domains; offer workarounds |
| User trust barrier (connecting email feels invasive) | High | Transparency-first messaging; local-first architecture; gradual permission model |
| Prediction accuracy disappoints early users | Medium | Set expectations; show confidence levels; improve with more data |
| Competitor copies closed-loop approach | Medium | Data moat compounds over time; first-mover advantage on behavioral dataset |
| Browser extension policy changes (Manifest V3 restrictions) | Medium | Maintain minimal required permissions; diversify capture methods |
| Regulatory risk on email proxy / data aggregation | Low-Medium | Legal review of email proxy model; strict anonymization; regular audits |

---

## Open Questions

These decisions can be deferred but should be resolved before public launch:

1. **Exact pricing tiers** — Run pricing experiments during beta
2. **Technology stack** — React Native vs. Flutter; backend language/framework
3. **Email infrastructure provider** — Build vs. buy for alias system (Mailgun, SendGrid, custom)
4. **AI/ML approach** — Cloud models vs. on-device inference for predictions
5. **International timeline** — US-first or multi-market from day one?
6. **Compliance requirements** — CCPA, GDPR implications of email parsing and data aggregation
7. **Collaborator integration** — How existing Chrome extension and virtual card products merge into Secret Shopper
