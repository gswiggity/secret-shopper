# Secret Shopper — Product Definition

> Your AI shopping agent. One place for every purchase, every promo, every retailer — with your privacy intact.

---

## Product Pillars

### 1. Ease
One place for your entire shopping life. No more digging through emails, juggling tabs, or losing track of returns. Secret Shopper consolidates everything into a single intelligent dashboard.

### 2. Transparency
See how retailers really behave. Know when they spam, when they inflate prices, when they use dark patterns. Make informed choices backed by real data, not marketing.

### 3. Privacy
Your data stays yours. Aliases shield your real identity. Local-first architecture keeps your information on your device. You choose what (if anything) gets shared — and it's always anonymized.

---

## Core Product Modules

### A. Purchase Dashboard (MVP)

The lead hook. Connect your email and instantly see your complete shopping life in one place.

**Features:**
- Auto-parse email history to build a complete purchase timeline across all retailers
- Shipping tracking aggregation — every package from every retailer in one view
- Return window tracking with countdown alerts ("3 days left to return Nike order")
- Warranty tracking with document storage (receipts, warranty cards, manuals)
- Rich search across all purchases by product name, brand, date, price range, or category
- Centralized order details with receipt archival
- Quick-glance stats: total spend by retailer, by category, by time period

**Why it's the lead feature:** Everyone shops online. Everyone loses track of purchases, misses return windows, and can't find order confirmations. This solves a universal pain point on day one — no behavioral change required beyond connecting your email.

---

### B. Promo Intelligence Engine (MVP)

Never miss a deal. Never overpay. The agent finds, validates, and times promo codes so you don't have to.

**Features:**
- Deep email scraping for promo codes — historical inbox scan + real-time monitoring
- Site-level promo code discovery and validation (scrape public code databases, test codes)
- Timing optimization: "Best time to buy" predictions per brand and product category
- Seasonal purchase calendar (Black Friday patterns, end-of-season sales, Prime Day cycles)
- Code stacking analysis — which codes combine for maximum discount
- Crowdsourced code database from anonymized, opted-in user data
- Promo expiration tracking with alerts

**Intelligence layer:** Over time, the system learns patterns. "Amazon sends 10-15% off after 5 days of cart abandonment." "Nike runs 25% off every 6 weeks." "Best Buy drops prices on last-gen products when new models launch." This intelligence compounds with every user.

---

### C. Email Intelligence Layer (MVP — basic; V2 — full)

Your email is the richest source of shopping data. Secret Shopper reads it so you don't have to.

**MVP Features:**
- Parse order confirmations to extract: retailer, products, prices, order numbers
- Detect tracking numbers and identify carriers automatically
- Extract promo codes from marketing emails
- Surface return/exchange deadlines from confirmation emails

**V2 Features:**
- Continuous real-time email monitoring (not just historical scan)
- Smart filtering: surface only actionable emails (shipping updates, promos, return reminders, price drops)
- Suppress marketing noise — track what's blocked per retailer
- Company/brand extraction and intelligent tagging from email patterns
- "47 marketing emails blocked this month" dashboard stat

---

### D. Browser Extension (MVP — basic; V2 — full)

The bridge between your browsing and your agent. Lightweight, non-intrusive, always working.

**MVP Features:**
- Detect when you're on a retailer checkout page
- Capture cart contents for dashboard tracking
- Surface known promo codes at checkout
- "Extension connected" status indicator

**V2 Features:**
- Auto-apply best available promo code at checkout
- Price history overlay on product pages ("This was $20 cheaper 2 weeks ago")
- Cart capture across all retailer sites for universal cart monitoring
- Cross-device sync of browsing activity (opt-in)
- In-page alerts: "Secret Shopper found a better price at [retailer]"

---

### E. Full Proxy Identity System (V2)

Your real email never touches a retailer again. Every store gets a unique alias managed entirely by Secret Shopper.

**Features:**
- Generate unique email addresses per retailer (e.g., `nike-7x3k@secretshopper.io`)
- All retailer communications routed through Secret Shopper's proxy
- User's real email never exposed to any retailer
- Per-alias controls: forwarding rules, spam filtering, unsubscribe management
- Privacy dashboard showing data exposure per retailer
- One-tap alias revocation — cut off a retailer completely if they misbehave
- Alias analytics: which retailers sell/share your email (detected by cross-retailer spam patterns)

**Why V2:** Requires building and operating email infrastructure (MX records, relay servers, spam filtering). MVP validates demand using read-only email access first.

---

### F. Universal Cart Monitor (V2)

Track every cart across every retailer. Turn "I'll buy it later" into a strategy.

**Features:**
- Track active carts across retailers (via browser extension + in-app browser)
- Abandoned cart tracking — "Cold Cases" with strategic timing intelligence
- Price change alerts on carted items (price went up, price dropped)
- Stock level monitoring (low stock warnings, back-in-stock alerts)
- Cross-device cart sync
- Cart value trends: "Your average cart sits for 4.2 days before purchase"
- Strategic abandonment coaching: "Wait 3 more days — 72% chance of a promo code"

---

### G. Cart & Price Monitoring (V2)

Historical price intelligence for smarter purchase timing.

**Features:**
- Historical price tracking per product (chart view, like CamelCamelCamel but universal)
- Price drop alerts with purchase recommendation
- Price comparison across retailers for same/similar products
- "Buy now vs. wait" AI recommendation based on price trends and upcoming sale patterns
- Price volatility scoring per product/category
- Integration with Promo Intelligence for combined savings estimates

---

### H. Brand Behavior Intelligence (V3)

Crowdsourced truth about how retailers actually treat their customers.

**Features:**
- Aggregated behavioral patterns: "Brand X sends 15% code ~5 days after cart abandonment"
- Retailer trust scoring — the "Shield Score":
  - Email spam frequency
  - Dark pattern usage (fake urgency, hidden fees, confusing unsubscribe)
  - Data sharing practices (detected via alias cross-correlation)
  - Return friendliness (policy clarity, actual approval rates from user reports)
  - Price manipulation (inflating before sales, dynamic pricing patterns)
- Community-contributed behavioral data (opt-in, fully anonymized)
- Confidence scores on predictions: "78% chance of promo in next 48 hours"
- Brand behavior trends over time (is this retailer getting better or worse?)

---

### I. Product Discovery & Social Integration (V3)

Turn casual browsing and social media into actionable shopping intelligence.

**Features:**
- Extract followed/liked brands from social media (Instagram, TikTok, Pinterest)
- Capture product interest from browser activity (non-disruptive, permission-based)
- In-app browser for shopping with full agent integration
- Convert social media ad interactions into tracked product interests
- "You showed interest in this 3 weeks ago — it's now 20% off"
- Wishlist aggregation across platforms
- Brand follow recommendations based on purchase patterns

---

### J. Conscious Shopping Assistant (V3)

Shop according to your values. See past the marketing.

**Features:**
- Product alternatives based on user-defined values:
  - Sustainability / environmental impact
  - Made in USA / local manufacturing
  - Small business / independent brands
  - Certifications (Fair Trade, B Corp, organic, cruelty-free)
  - Demographic support (women-owned, minority-owned, veteran-owned)
- Greenwashing detection: cross-reference marketing claims against certifications and third-party data
- Partnership with Consumer Reports-type organizations per industry vertical
- Independent product evaluations (brands pay for evaluation, not placement — see Business Plan)
- Sourcing transparency scores
- "This product claims to be sustainable but has no third-party certification" alerts

---

## Platform Strategy

### Day One: Cross-Platform

| Platform | Technology | Priority |
|----------|-----------|----------|
| iOS | React Native or Flutter | Primary |
| Android | React Native or Flutter (shared codebase) | Primary |
| Web | Responsive web app, PWA-capable | Primary |
| Chrome Extension | Manifest V3 | Primary |
| Firefox Extension | WebExtension API | Secondary |
| Safari Extension | Safari Web Extension | Secondary |

**Rationale:** The product requires presence across devices (mobile for dashboard, browser for shopping intelligence). Cross-platform framework maximizes coverage with minimal team. Browser extension is the top-of-funnel acquisition tool.

---

## Permission Model

Secret Shopper is permission-based. The app requests access incrementally as the user engages with features:

| Permission | What We Access | When Requested | Required For |
|-----------|---------------|----------------|-------------|
| Email (OAuth) | Read inbox, monitor new mail | Onboarding | Purchase Dashboard, Promo Intelligence, Email Intelligence |
| Browser Extension | Page URLs, cart contents, product data | When user installs extension | Cart Monitor, Price Tracking, Checkout Promos |
| Social Media | Read-only: follows, likes, saved items | When user enables Social Discovery | Product Discovery |
| In-App Browser | Full browsing activity within SS browser | When user uses in-app browser | Full agent integration |
| Notifications | Push/local notifications | After first value moment | Return alerts, price drops, promo timing |

**What we never access without explicit consent:** Contacts, photos, location, microphone, camera, non-shopping email content.

---

## Data Architecture

### Local-First Philosophy

```
┌──────────────────────────────────────────────┐
│                User's Device                  │
│                                               │
│  ┌─────────────┐  ┌──────────────────────┐   │
│  │ Email Parser │  │ Local Database        │   │
│  │ (on-device)  │──│ - Purchase history    │   │
│  └─────────────┘  │ - Cart snapshots      │   │
│                    │ - Promo codes         │   │
│  ┌─────────────┐  │ - Price history       │   │
│  │ Extension    │──│ - Browsing signals    │   │
│  │ Data Sync   │  │ - Email content       │   │
│  └─────────────┘  └──────────┬───────────┘   │
│                               │               │
│                    ┌──────────▼───────────┐   │
│                    │ Anonymization Engine  │   │
│                    │ (strips all PII)      │   │
│                    └──────────┬───────────┘   │
└───────────────────────────────┼───────────────┘
                                │ (opt-in only)
                     ┌──────────▼───────────┐
                     │ Secret Shopper Cloud  │
                     │ - Aggregated signals  │
                     │ - Prediction models   │
                     │ - Community intel     │
                     └──────────────────────┘
```

### What stays on device (always)
- Raw email content
- Personal details (name, address, payment info)
- Full browsing history
- Cart contents
- Individual purchase details

### What syncs to cloud (for cross-device)
- Account settings and preferences
- Alias configurations (if using proxy system)
- Aggregated purchase stats (not raw details)
- Notification preferences

### What gets shared (opt-in, anonymized)
- "Promo received: yes/no"
- "Days after cart abandon: X"
- "Discount percentage: Y"
- "Retailer spam frequency: Z emails/month"
- Never: email content, product names, purchase amounts, personal details

---

## User Personas

### The Deal Hunter
- Shops at 10+ retailers, spends $300+/month online
- Currently uses Honey, checks RetailMeNot manually, follows deal subreddits
- **Hook:** Promo Intelligence finds codes they'd never find manually. Purchase Dashboard saves them hours.
- **Upgrade trigger:** AI timing predictions ("wait 2 days for 15% off") are the premium unlock.

### The Privacy Pragmatist
- Tired of spam, wary of data sharing, uses throwaway emails manually
- Might already use Privacy.com for cards
- **Hook:** Email alias system replaces their manual workarounds. Shield Scores validate their instincts.
- **Upgrade trigger:** Full proxy system with per-retailer controls.

### The Organized Shopper
- Tracks purchases in spreadsheets, sets calendar reminders for returns
- Frustrated by fragmented information across email, apps, and retailer sites
- **Hook:** Purchase Dashboard replaces all their manual tracking instantly.
- **Upgrade trigger:** Return window alerts and warranty tracking save them from missed deadlines.

### The Conscious Consumer
- Cares about sustainability, small business, ethical sourcing
- Skeptical of greenwashing, wants data not marketing
- **Hook:** Conscious Shopping Assistant surfaces alternatives aligned with their values.
- **Upgrade trigger:** Independent brand evaluations and sourcing transparency.
