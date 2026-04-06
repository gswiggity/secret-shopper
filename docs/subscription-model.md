# Secret Shopper — Subscription Model Analysis

> What to charge, how to tier it, and what it takes to sustain the business at every stage.

---

## The Core Constraint

Your costs break into two buckets with very different dynamics:

| Cost Type | At 10K Users | At 100K Users | Scales With |
|-----------|-------------|---------------|-------------|
| **Infrastructure** | $1,155-$4,480/mo | $4,875-$19,000/mo | Users (roughly linear) |
| **People** | $45,000-$100,000/mo | $45,000-$100,000/mo | Team size (step function) |

Infrastructure is cheap and scales predictably. **People costs are 90%+ of your burn at every stage under 500K users.** This means your pricing doesn't need to cover infrastructure — it needs to cover salaries. That changes the math significantly.

---

## What Comparables Charge

| Product | Price | What You Get | Model |
|---------|-------|-------------|-------|
| Cloaked | $10/mo or $96/yr | Unlimited identities, email/phone masking, password management | Freemium subscription |
| DeleteMe (Abine) | $10.75/mo ($129/yr) | Data broker removal, privacy monitoring | Subscription only |
| SimpleLogin (now Proton) | $4/mo or $30/yr | Unlimited email aliases, custom domains | Freemium subscription |
| Honey | Free | Coupon codes, price tracking | Affiliate revenue (no subscription) |
| Capital One Shopping | Free | Price comparison, coupons | Tied to Capital One ecosystem |
| RetailMeNot | Free | Coupon codes, cashback | Advertising + affiliate |

**The pattern:** Pure shopping tools (Honey, RetailMeNot) are free and monetize via affiliate/advertising. Privacy tools (Cloaked, DeleteMe, SimpleLogin) charge $4-11/month. **Secret Shopper straddles both categories** — this is both an opportunity and a pricing challenge.

---

## Recommended Tier Structure

### Free Tier — "The Hook"

The free tier must be genuinely useful on its own. It's your acquisition engine.

| Feature | Included |
|---------|----------|
| Purchase dashboard (full email parse, complete history) | Yes |
| Shipping tracking (all retailers) | Yes |
| Return window alerts | Yes |
| Basic promo code surfacing (codes found in your email) | Yes |
| Browser extension (manual code lookup at checkout) | Yes |
| Limited retailer aliases | 3 aliases |
| Basic spend analytics | Yes |

**Why this works:** The purchase dashboard is the "aha" moment — connect your email, instantly see everything you've bought. This alone is valuable enough to keep users engaged and talking about the product. It also trains them to trust Secret Shopper with their email, which is the conversion lever for premium.

### Premium Tier — "Secret Shopper Pro"

**Recommended price: $9.99/month or $79.99/year ($6.67/month)**

The annual plan is critical — it improves retention, cash flow, and LTV.

| Feature | Free | Pro |
|---------|------|-----|
| Purchase dashboard | Full | Full |
| Shipping tracking | All retailers | All retailers |
| Return window alerts | Yes | Yes + smart reminders |
| Promo code surfacing | Email-found only | Email + site-scraped + crowdsourced |
| AI promo timing predictions | No | Yes ("Wait 2 days — 78% chance of 15% off") |
| Price history charts | No | Yes (full historical tracking) |
| Price drop alerts | No | Yes |
| "Buy now vs. wait" recommendations | No | Yes |
| Cart monitoring (Cold Cases) | No | Yes (unlimited carts) |
| Strategic abandonment coaching | No | Yes |
| Email aliases | 3 | Unlimited |
| Alias management (forwarding, blocking) | Basic | Full control |
| Retailer Shield Scores | Summary only | Full breakdown |
| Savings reports | No | Monthly report ("You saved $X") |
| Conscious shopping features | No | Full (alternatives, sustainability scores) |
| Browser extension | Manual lookup | Auto-apply + price overlay |
| Priority support | No | Yes |

### Why $9.99/month

| Factor | Analysis |
|--------|----------|
| **Comparable pricing** | Cloaked is $10/mo, DeleteMe is $10.75/mo. Secret Shopper offers more utility (shopping intelligence + privacy). $10 is the established price point for consumer privacy tools. |
| **Psychological threshold** | $9.99 stays under the $10 mental barrier. It's "about the cost of one streaming service." |
| **Savings justification** | If the product saves users even one missed return ($30+) or one good promo ($15+) per month, it pays for itself many times over. The "Secret Shopper saved you $X this month" metric in the app makes this tangible. |
| **After app store cut** | At $9.99, you net $8.49 (15% commission under Small Business Program). At scale past $1M revenue, you net $6.99 (30% commission), unless users subscribe via web. |
| **Annual option** | $79.99/year ($6.67/month) gives a 33% discount, locks in retention, and improves cash flow. Industry data shows annual subscribers retain 2-3x longer. |

### Family Plan — "Secret Shopper Household"

**Recommended price: $14.99/month or $119.99/year**

- Up to 5 family members
- Shared intelligence (combined data improves predictions for everyone)
- Individual privacy (members don't see each other's purchases)
- Single billing

**Why this matters:** Household plans increase ARPU by 50% while reducing per-user cost to acquire. A family of 3 paying $14.99 = $5/person, cheaper than individual plans, but more revenue per account.

---

## Revenue Math by Stage

### Net Revenue Per Paying User

| Channel | Monthly Price | Commission | Net Revenue |
|---------|-------------|------------|-------------|
| App Store (monthly, <$1M rev) | $9.99 | 15% | $8.49 |
| App Store (monthly, >$1M rev) | $9.99 | 30% | $6.99 |
| App Store (annual, <$1M rev) | $6.67 effective | 15% | $5.67 |
| Web (Stripe, monthly) | $9.99 | 2.9% + $0.30 | $9.40 |
| Web (Stripe, annual) | $6.67 effective | 2.9% + $0.30 | $6.27 |

**Key insight:** Push users to subscribe via the web whenever possible. The difference between 15% (app store) and 2.9% (Stripe) is massive at scale. At 10,000 paying users, that's **$18,000/month** in saved commissions.

### Blended Revenue Assumptions

Assuming a mix of monthly/annual and app store/web subscribers:
- **Average net revenue per paying user: ~$7.50/month**
- This accounts for ~60% monthly / 40% annual split, ~50% app store / 50% web

### Revenue at Each User Scale

| Active Users | Conversion Rate | Paying Users | Monthly Net Revenue | Annual Net Revenue |
|-------------|----------------|-------------|--------------------|--------------------|
| 5,000 | 4% | 200 | $1,500 | $18,000 |
| 10,000 | 4% | 400 | $3,000 | $36,000 |
| 25,000 | 4% | 1,000 | $7,500 | $90,000 |
| 50,000 | 5% | 2,500 | $18,750 | $225,000 |
| 100,000 | 5% | 5,000 | $37,500 | $450,000 |
| 250,000 | 5% | 12,500 | $93,750 | $1,125,000 |
| 500,000 | 6% | 30,000 | $225,000 | $2,700,000 |
| 1,000,000 | 6% | 60,000 | $450,000 | $5,400,000 |

Note: Conversion rate improves with scale because (a) the AI predictions get better with more data, making premium more valuable, and (b) the product has more time to demonstrate value via the "savings" metric.

---

## Break-Even Scenarios at $9.99/month

### Bootstrap Phase (2 founders, $15K/month burn)

| | Calculation | Result |
|-|------------|--------|
| Paying users needed | $15,000 / $7.50 net | **2,000 paying users** |
| Active users needed (4% conv) | 2,000 / 0.04 | **50,000 active users** |
| Timeline to reach (optimistic) | ~12-18 months | |

### Post-Seed Phase (3-person team, $55K/month burn)

| | Calculation | Result |
|-|------------|--------|
| Paying users needed | $55,000 / $7.50 net | **7,333 paying users** |
| Active users needed (5% conv) | 7,333 / 0.05 | **146,667 active users** |
| Timeline to reach | ~18-30 months | |

### Growth Phase (5-person team, $90K/month burn)

| | Calculation | Result |
|-|------------|--------|
| Paying users needed | $90,000 / $7.50 net | **12,000 paying users** |
| Active users needed (5% conv) | 12,000 / 0.05 | **240,000 active users** |
| Timeline to reach | ~24-36 months | |

---

## The Conversion Lever: "Savings Dashboard"

The single most important feature for conversion is the **savings dashboard** — showing users exactly how much money Secret Shopper has saved (or could have saved) them.

**Free users see:**
> "Secret Shopper found 3 promo codes you missed this month worth an estimated **$47.50**. Upgrade to Pro to auto-apply codes and get AI-powered timing predictions."

**Premium users see:**
> "This month: **$127.40 saved** — $47.50 from promo codes, $32.00 from price drop alerts, $47.90 from strategic cart timing. Your Pro subscription has paid for itself **12.7x** this month."

This is the Cloaked playbook — they show users exactly how many data points were blocked, creating tangible value justification. For Secret Shopper, dollar savings are even more compelling than abstract privacy metrics.

**Target:** Premium needs to demonstrably save users **$30+/month** on average to justify $9.99/month. Based on the research:
- Average US household spends ~$6,000+/year online
- 5-15% savings on even a portion of that = $25-75/month
- This is achievable with promo codes + price drop timing alone

---

## Pricing Experiments to Run in Beta

Don't lock in pricing permanently. Run these tests:

### Test 1: Price Point
- A/B test $7.99 vs. $9.99 vs. $12.99
- Measure: conversion rate, revenue per user, LTV
- The optimal price is whichever maximizes **revenue per active user** (price x conversion rate)

| Price | If Conv. = 5% | If Conv. = 4% | If Conv. = 3% | Rev/Active User |
|-------|---------------|---------------|---------------|-----------------|
| $7.99 | $0.40 | $0.32 | $0.24 | Higher conv likely |
| $9.99 | $0.50 | $0.40 | $0.30 | Middle ground |
| $12.99 | $0.65 | $0.52 | $0.39 | Higher if conv holds |

### Test 2: Annual Discount Depth
- 20% off ($95.88/yr) vs. 33% off ($79.99/yr) vs. 40% off ($71.88/yr)
- Measure: annual adoption rate, 12-month retention, total LTV
- Deeper discounts drive more annual signups but reduce per-user revenue

### Test 3: Free Trial vs. Freemium
- Option A: Freemium (permanent free tier, as designed)
- Option B: 14-day full-feature trial, then free tier or premium
- Option C: 30-day full-feature trial, then free tier or premium
- Trials typically convert at 10-25% vs. freemium at 3-5%, but trials also have higher churn post-conversion

### Test 4: Savings Guarantee
- "If Secret Shopper Pro doesn't save you more than the subscription cost in your first month, we'll refund you."
- This is a confidence signal that dramatically reduces purchase friction
- Only works if the product actually delivers savings reliably

---

## When to Introduce Each Revenue Stream

| Revenue Stream | When | Expected Contribution |
|---------------|------|----------------------|
| **Premium subscription** | Day 1 of public launch | 80%+ of revenue for first 2 years |
| **Annual plans** | Day 1 (offer alongside monthly) | 30-40% of subscription revenue |
| **Family/household plan** | Month 3-6 post-launch | 10-15% of subscription revenue |
| **Web-direct billing** | Day 1 (avoid app store commission) | Cost savings, not new revenue |
| **Brand evaluation program** | Month 12+ (need credibility first) | 10-20% of revenue at maturity |
| **B2B data insights** | Month 18+ (need data volume) | 5-10% of revenue at maturity |
| **Industry partnerships** | Month 12+ (need brand recognition) | 5-10% of revenue at maturity |

---

## Summary: The Recommended Model

| Element | Recommendation |
|---------|---------------|
| **Free tier** | Purchase dashboard + basic promos + 3 aliases. Genuinely useful, drives word-of-mouth. |
| **Premium price** | $9.99/month or $79.99/year |
| **Family plan** | $14.99/month or $119.99/year (up to 5 members) |
| **Conversion target** | 4-5% free-to-paid |
| **Key conversion lever** | Savings dashboard showing dollar value of premium features |
| **App store strategy** | Push web-direct billing to save 12-27% in commissions |
| **Break-even (bootstrap)** | ~50K active users / 2,000 paying |
| **Break-even (3-person team)** | ~147K active users / 7,333 paying |
| **Annual revenue at 100K users** | ~$450,000 |
| **Annual revenue at 500K users** | ~$2,700,000 |
