# Secret Shopper — Funding & Costs Analysis

> Comprehensive cost modeling and funding strategy based on market research conducted April 2026.

---

## Executive Summary

Secret Shopper can reach MVP with **$28K-$60K** if built by founders, or **$195K-$295K** with a small funded team over 3-4 months. Monthly infrastructure costs start at **~$400-$900/month** at launch and scale to **$4K-$17K/month** at 100K users. The dominant cost at every stage is **people, not infrastructure**.

The recommended seed raise is **$1.5M-$3M**, targeting 30+ months of runway at a lean burn rate. This is well-supported by comparable raises in the space — Cloaked raised $4M seed (2022) and Privacy.com raised ~$8M pre-Series A. The "shopping intelligence + consumer privacy" intersection is a compelling narrative, sitting between Honey's $4B exit and Cloaked's $375M Series B.

---

## Part 1: Detailed Cost Breakdown

### A. Development Costs (One-Time, MVP Phase)

#### Scenario 1: Founder-Built (Recommended for Bootstrap Phase)

| Category | Cost |
|----------|------|
| Founder salaries (modest, 4 months) | $20,000-$40,000 |
| Freelance UI/UX design (15-25 screens + design system) | $5,000-$12,000 |
| Infrastructure (4 months) | $200-$600 |
| Legal basics (incorporation, ToS, privacy policy) | $2,000-$5,000 |
| App store fees | $125 |
| Tools & subscriptions | $500-$1,000 |
| **Total** | **$28,000-$59,000** |

#### Scenario 2: Small Funded Team (3 people, 4 months)

| Category | Cost |
|----------|------|
| Salaries (fully loaded, 4 months) | $180,000-$260,000 |
| Infrastructure | $500-$2,000 |
| Legal | $5,000-$10,000 |
| Design | $8,000-$20,000 |
| App store fees | $125 |
| Tools & misc | $1,000-$3,000 |
| **Total** | **$195,000-$295,000** |

#### Scenario 3: Agency-Built

| Category | Cost |
|----------|------|
| US-based agency (mobile + web + extension) | $180,000-$350,000 |
| Offshore agency (Eastern Europe) | $60,000-$120,000 |
| Infrastructure | $500-$2,000 |
| Legal | $5,000-$10,000 |
| **Total** | **$66,000-$362,000** |

### B. Monthly Infrastructure Costs by Scale

#### Email Infrastructure (Alias/Proxy System — V2)

| Component | 10K Users | 100K Users | 1M Users |
|-----------|-----------|------------|----------|
| Email forwarding (AWS SES) | $60/mo | $600/mo | $6,000/mo |
| Dedicated IPs | $25/mo | $50-75/mo | $250/mo |
| Spam filtering (self-hosted Rspamd) | $50/mo | $100-200/mo | $500-1,000/mo |
| Database | $50/mo | $200-500/mo | $1,000-3,000/mo |
| Application servers | $50/mo | $200-500/mo | $1,000-5,000/mo |
| **Subtotal** | **$235/mo** | **$1,200-1,900/mo** | **$9,000-15,000/mo** |
| **Per-user cost** | **$0.024** | **$0.012-0.019** | **$0.009-0.015** |

Key insight: Raw email forwarding is cheap (~$0.006/alias/month via SES). The real costs are engineering and deliverability management.

One-time gate: Google's CASA Tier 2 security assessment for Gmail OAuth costs **$15,000-$75,000**. Microsoft Graph API is free with no paid assessment required.

#### AI/ML & Data Infrastructure

| Component | 1K Users | 10K Users | 100K Users |
|-----------|----------|-----------|------------|
| Email parsing (LLM API) | $20-50/mo | $200-1,500/mo | $500-3,000/mo |
| Prediction models (CPU) | $40-100/mo | $100-300/mo | $300-2,000/mo |
| Price monitoring | $50-150/mo | $300-700/mo | $1,500-5,000/mo |
| **Subtotal** | **$140-350/mo** | **$650-2,700/mo** | **$2,500-11,000/mo** |

Key insights:
- **No GPUs needed initially.** Promo timing and price predictions are time-series problems solvable with XGBoost/Prophet on CPU ($1-20/month training).
- **Email parsing hybrid approach**: Use regex for templated retailer emails (Amazon, Walmart, Target), LLM only for ambiguous ones. Cuts API calls by 60-80%.
- **At ~50K users, switch from LLM API to fine-tuned BERT** for email parsing — crossover point where self-hosted ($84-400/mo) beats API ($2,000-15,000/mo).
- **Price monitoring is the most expensive AI component** due to proxy bandwidth costs ($2-10/GB for residential proxies).

#### Core App Infrastructure

| Component | 1K Users | 10K Users | 100K Users |
|-----------|----------|-----------|------------|
| Compute (API servers) | $50-150/mo | $200-600/mo | $1,000-5,000/mo |
| Database | $25-70/mo | $40-100/mo | $75-500/mo |
| Auth (Supabase/Firebase) | $0 | $0 | $0-100/mo |
| Push notifications (FCM) | $0 | $0 | $0 |
| CDN & storage | $10-20/mo | $30-80/mo | $100-500/mo |
| **Subtotal** | **$85-240/mo** | **$270-780/mo** | **$1,175-6,100/mo** |

#### Total Monthly Infrastructure

| Scale | Low Estimate | High Estimate |
|-------|-------------|---------------|
| **1K users (MVP)** | **$225/mo** | **$590/mo** |
| **10K users** | **$1,155/mo** | **$4,480/mo** |
| **100K users** | **$4,875/mo** | **$19,000/mo** |

Note: Email alias system (V2) adds $235-$1,900/month at 10K-100K users. These numbers include V2 costs for the higher-scale tiers.

### C. Ongoing Operational Costs (Monthly)

| Category | Bootstrap Phase | Post-Seed Phase |
|----------|----------------|-----------------|
| Team salaries (fully loaded) | $0-$15K (founders, deferred) | $45K-$100K (3-5 people) |
| Infrastructure | $225-$590 | $1,155-$4,480 |
| Legal retainer | $0-$500 | $500-$2,000 |
| Accounting/bookkeeping | $200-$500 | $200-$500 |
| Design (part-time) | $0-$2,000 | $2,000-$6,000 |
| Browser extension maintenance | $0 (built by founders) | $1,000-$3,000 |
| Insurance | $150-$300 | $350-$800 |
| Tools & subscriptions | $200-$500 | $500-$1,500 |
| **Total monthly burn** | **$800-$19,000** | **$50,000-$118,000** |

### D. Hidden / Easy-to-Miss Costs

| Cost | Amount | Notes |
|------|--------|-------|
| Apple/Google commission on subscriptions | 15-30% of revenue | 15% under Small Business Program (<$1M rev). At $10/mo subscription, you net $7-8.50 |
| Google Gmail security assessment | $15,000-$75,000 one-time | Required for apps that read Gmail. Non-negotiable. |
| Browser extension maintenance | $1K-$3K/month | Chrome updates Manifest V3 frequently. Safari is worst. |
| ML cost overruns | +40-60% above estimates | Industry standard — budget for it |
| ML maintenance (retraining) | 17-30% of initial build cost/year | Models degrade without fresh data |

---

## Part 2: Revenue Modeling

### Subscription Revenue Scenarios

Assuming 3-5% free-to-paid conversion (industry standard for freemium):

| Active Users | Paying Users (4%) | Monthly Revenue (@$10/mo) | After App Store Cut (15%) | Annual Revenue |
|-------------|-------------------|--------------------------|--------------------------|---------------|
| 10,000 | 400 | $4,000 | $3,400 | $40,800 |
| 50,000 | 2,000 | $20,000 | $17,000 | $204,000 |
| 100,000 | 4,000 | $40,000 | $34,000 | $408,000 |
| 500,000 | 20,000 | $200,000 | $170,000 | $2,040,000 |
| 1,000,000 | 40,000 | $400,000 | $340,000 | $4,080,000 |

### Revenue per User Economics

At $10/month premium subscription with 4% conversion:
- **Revenue per active user**: $0.40/month ($4.80/year)
- **Infrastructure cost per active user**: $0.02-0.05/month at 100K scale
- **Gross margin on infrastructure**: ~88-95%
- **After app store commission**: ~75-80% gross margin

The unit economics are strong. The challenge is reaching scale — people costs dominate until ~$2M+ ARR.

### Break-Even Analysis

| Team Size | Monthly Burn | Paying Users Needed (@$10/mo, after commission) | Active Users Needed (4% conversion) |
|-----------|-------------|------------------------------------------------|--------------------------------------|
| Solo founder | $5,000 | 588 | 14,700 |
| 2 founders | $15,000 | 1,765 | 44,100 |
| 3-person team | $55,000 | 6,471 | 161,800 |
| 5-person team | $90,000 | 10,588 | 264,700 |

---

## Part 3: Funding Strategy

### Comparable Raises in the Space

| Company | Stage | Amount | Year | Outcome |
|---------|-------|--------|------|---------|
| Honey | Seed | $1.8M | 2014 | → $4B acquisition (PayPal, 2020) |
| Honey | Series B | $26M | 2017 | 10M users at time of raise |
| Privacy.com | Pre-Series A | ~$8M | Pre-2020 | → Rebranded Lithic |
| Privacy.com | Series A | $10.2M | 2020 | Index Ventures led |
| Privacy.com | Series B | $43M | 2021 | Bessemer led |
| Cloaked | Seed | $4M | Jan 2022 | Consumer privacy product |
| Cloaked | Series A | $25M | Mar 2022 | Lux Capital, Human Capital |
| Cloaked | Series B | $375M | Mar 2026 | 350K paying customers, 10x YoY growth |
| SimpleLogin | Bootstrapped | $0 | 2019-2022 | → Acquired by Proton (2022) |
| Abine (Blur/DeleteMe) | Series A | $6.47M | 2011 | Profitable on minimal capital for 13+ years |
| Rakuten (Ebates) | Various | Minimal | 1999-2014 | → $1B acquisition |
| RetailMeNot | Multiple rounds | $315M total | 2009-2013 | → $1.5B IPO (2013) |

### Key Funding Insight

**Two capital-efficient paths are validated in this space:**

1. **Honey model**: Raise minimal capital ($49M total over entire lifecycle), grow organically via browser extension virality, reach profitability early, exit at massive multiple. Required ~17M MAU.

2. **SimpleLogin/Abine model**: Bootstrap entirely (or near-entirely), build a sustainable profitable business, get acquired by a larger privacy player. Doesn't require venture scale.

**One venture-scale path is validated:**

3. **Cloaked model**: Raise aggressively into the consumer privacy thesis ($404M total), grow fast (10x YoY), aim for very large outcomes. Requires demonstrating strong retention and paid conversion.

### Recommended Funding Plan

#### Phase 0: Bootstrap (Months 1-4) — $30K-$60K

- Founders build the MVP
- Source: Personal savings, credit cards, friends & family
- Goal: Working product with 500-1,000 beta users
- Key proof points: email OAuth completion rate, D7 retention, qualitative feedback

#### Phase 1: Seed Round (Month 4-6) — Target $1.5M-$3M

| Parameter | Target |
|-----------|--------|
| Round size | $1.5M-$3M |
| Valuation (pre-money) | $8M-$15M |
| Dilution | 15-25% |
| Investors | Angels + small consumer/privacy-focused funds |
| Runway at $50K/mo burn | 30-60 months |

**Metrics needed to raise:**
- 1,000+ beta users with email connected
- D30 retention > 30%
- Email OAuth grant rate > 60%
- Early signal on willingness to pay (survey or pre-launch premium signup)
- Demonstrable savings per user (tangible value metric)

**Use of funds:**
| Category | Allocation |
|----------|-----------|
| Engineering (2-3 hires) | 50-60% |
| Gmail security assessment | 3-5% |
| Infrastructure | 5-10% |
| Design & product | 10-15% |
| Legal & compliance | 5% |
| Marketing (content, community) | 10-15% |

#### Phase 2: Series A (Month 18-24) — Target $8M-$15M

Only pursue if metrics support venture-scale growth:

**Metrics expected by Series A investors:**
| Metric | Target |
|--------|--------|
| MAU | 100K-500K |
| D30 retention | 30%+ sustained |
| Premium conversion | 5%+ |
| MRR | $15K-$50K+ |
| Monthly growth rate | 15-20% |
| LTV:CAC | 3:1+ |

**Use of funds:**
- Scale engineering team (5-8 total)
- Build V2 features (alias system, cart monitoring, AI predictions)
- Launch brand evaluation program (B2B revenue stream)
- Marketing for public launch
- Partnership development

### Alternative Path: Stay Lean

If venture scale isn't the goal, the numbers support a sustainable business at smaller scale:

- 50K active users with 4% conversion = 2,000 paying users
- At $10/month = $20K/month revenue ($17K after app store cut)
- Infrastructure at 50K users: ~$2,500/month
- Could sustain 1-2 founders + a contractor
- No VC needed — the SimpleLogin playbook

---

## Part 4: Market Context

### Market Sizing (from competitive landscape research)

- **US e-commerce**: ~$1.1T annually (2025)
- **Digital coupon users**: ~145M Americans
- **Target wedge**: Power online shoppers (5+ retailers, $200+/mo spend, privacy-aware)
- **Serviceable addressable market**: 15-20M users
- **SAM at $5-10/month**: $900M-$2.4B for subscription alone

### Competitive Landscape Signals

- **Honey** proved 17M+ MAU is achievable with a free browser extension
- **Cloaked** proved consumers will pay for identity privacy ($375M Series B, 350K paying customers)
- **Nobody combines both** — shopping intelligence + consumer privacy in one product
- **Cart abandonment is massive**: ~70% of online shopping carts are abandoned, representing billions in unrealized purchases. Secret Shopper's "Cold Cases" feature turns this pain point into a strategic advantage.

### Investor Appetite (April 2026)

- Consumer seed rounds have compressed (median $700K in Q1 2025) but **privacy is a clear exception** — Cloaked's $375M raise signals strong appetite
- Seed-to-Series A conversion: only ~15-20% of consumer seed startups raise Series A
- Median time from seed to Series A: **3 full years** (extended significantly from 1.7 years in 2024)
- Investors expect **24-30 months of runway** at funding

---

## Part 5: Risk-Adjusted Scenarios

### Optimistic Scenario (Honey-like trajectory)
- Browser extension goes viral, 100K users in 6 months
- 5% premium conversion = 5,000 paying users = $50K MRR by month 12
- Raise Series A at $10M+ on strong metrics
- Infrastructure costs well within revenue

### Base Scenario (Steady growth)
- 10K users in 6 months, 50K by month 18
- 3% premium conversion = 1,500 paying users = $15K MRR by month 18
- Seed runway supports reaching profitability or Series A metrics
- May need to optimize burn carefully

### Conservative Scenario (Slow adoption)
- 3K users in 6 months, 15K by month 18
- 2% premium conversion = 300 paying users = $3K MRR by month 18
- Need to find product-market fit before running out of seed runway
- Consider pivoting to B2B data play earlier

### Worst Case (Pivot required)
- Email OAuth grant rate below 30% (users don't trust the product enough)
- D30 retention below 15%
- Signal: the privacy positioning is creating friction, not value
- Mitigation: Pivot to extension-only approach (no email access needed) like Honey

---

## Appendix: Key Assumptions

| Assumption | Value | Source |
|-----------|-------|--------|
| Free-to-paid conversion | 3-5% | Industry benchmark for freemium consumer apps |
| D30 retention (target) | 30%+ | a16z consumer app benchmarks |
| Email OAuth grant rate | 60%+ | Needed to validate core value prop |
| Emails per user per month | 100 | Average for active online shoppers |
| App store commission | 15% | Under Small Business Program (<$1M revenue) |
| Monthly infrastructure per user (at scale) | $0.02-$0.05 | Based on detailed infrastructure modeling |
| Fully loaded engineer cost (US) | $15K-$23K/month | Market rate for senior engineers |
| Seed round dilution | 15-25% | Industry standard |

---

## Sources

- AWS SES, SageMaker, EC2 pricing (aws.amazon.com)
- Mailgun, SendGrid, Postmark published pricing
- Nylas API pricing (v3 consumption model)
- Google CASA assessment requirements
- Anthropic Claude API and OpenAI API pricing
- Keepa, Prisync, Bright Data pricing
- Crunchbase, PitchBook, TechCrunch for funding data
- Carta Consumer Q1 2025 report
- a16z consumer app benchmarks
- SimpleLogin, AnonAddy open-source repositories
- Stitch Fix public filings (SEC EDGAR)
- Cloaked Series B announcement (March 2026)
