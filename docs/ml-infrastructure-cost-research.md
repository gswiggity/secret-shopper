# ML Infrastructure Cost Research — Secret Shopper

> Research compiled April 2026. All figures are current as of this date unless otherwise noted.

---

## 1. ML Infrastructure Costs for a Startup

### Can This Be Done with Simpler Models Initially?

**Yes, absolutely.** For Secret Shopper's core prediction use cases (promo code timing, optimal purchase windows, price drop prediction), you do NOT need deep learning or GPUs at the start:

- **Promo timing prediction**: Historical pattern analysis (e.g., "Brand X sends 20% codes every 6 weeks") is fundamentally a time-series pattern detection problem. Simple approaches work well:
  - Rule-based heuristics (detect periodicity in email timestamps)
  - Classical time-series models (ARIMA, Prophet) — CPU-only, runs on a $5/month VM
  - Gradient-boosted trees (XGBoost/LightGBM) — CPU-only, trains in seconds on moderate data
  
- **Price drop prediction**: Historical price data + seasonal decomposition. Again, XGBoost or even simple regression models suffice initially.

- **"Best time to buy" recommendations**: Aggregated historical purchase data + seasonal patterns. This is statistics, not deep learning.

**Bottom line**: A startup can run all initial prediction models on CPU-only instances. GPUs are not needed until you're doing NLP/embedding work or have millions of users requiring real-time deep learning inference.

### Cloud Compute Costs by Scale

#### Training Costs (periodic retraining, e.g., weekly)

| Approach | Instance | Cost/Hour | Monthly (4 hrs/week training) |
|----------|----------|-----------|-------------------------------|
| Simple models (XGBoost, Prophet) on CPU | AWS ml.m5.xlarge | $0.23/hr | ~$4/month |
| Simple models on basic VM | EC2 t3.medium | $0.05/hr | ~$1/month |
| Mid-complexity (embeddings, small neural nets) | AWS ml.g5.xlarge (GPU) | $1.21/hr | ~$19/month |
| Deep learning (transformer models) | AWS ml.p4d.24xlarge | $37.69/hr | ~$603/month |

**Recommendation for Secret Shopper MVP**: Start with ml.m5.xlarge or even t3.medium. Total training cost: **$1-20/month**.

#### Inference Costs at Scale

**SageMaker Serverless Inference** (best for low/variable traffic):
- ~$0.00024 per request (500ms inference, 4GB memory)
- 1K daily predictions = ~$7/month
- 10K daily predictions = ~$72/month
- 100K daily predictions = ~$720/month

**SageMaker Real-Time Inference** (dedicated endpoint, better for steady traffic):

| Scale | Recommended Instance | Cost/Month |
|-------|---------------------|------------|
| 1K predictions/day | ml.t3.medium (CPU) | ~$37/month |
| 10K predictions/day | ml.m5.large (CPU) | ~$84/month |
| 100K predictions/day | ml.m5.xlarge (CPU) | ~$196/month |
| 1M predictions/day | 2x ml.m5.xlarge (CPU) | ~$392/month |

**GCP Vertex AI Forecast** (managed forecasting service):
- $0.20 per 1,000 data points (first 1M)
- $0.10 per 1,000 data points (1M–50M)
- $0.02 per 1,000 data points (50M+)
- For 100K daily predictions = ~$600/month at the low tier, dropping significantly at scale

**Key insight**: At Secret Shopper's initial scale, simple CPU-based models with SageMaker serverless or a single small instance can handle predictions for **under $100/month total**.

### Cloud ML Services vs. Self-Hosted GPU Instances

| Factor | SageMaker/Vertex AI | Self-Hosted EC2 GPU |
|--------|-------------------|-------------------|
| ml.g5.xlarge (GPU) | ~$1.41/hr | ~$1.01/hr (EC2 direct) |
| Management overhead | Managed (lower ops cost) | You manage everything |
| SageMaker premium | 20-40% more than raw EC2 | Baseline |
| Spot instances | Available | 60-90% savings |
| Best for | Teams <5 ML engineers | Teams with dedicated MLOps |

**Recommendation**: Use managed services (SageMaker or Vertex AI) until you have a dedicated ML engineer. The 20-40% premium is worth it for the reduced ops burden. But for Secret Shopper's use case, **you likely won't need GPUs at all for v1**.

---

## 2. LLM API Costs for Email Parsing

### Cost Per Email — LLM API Approach

A typical order confirmation email is ~500-2,000 tokens. Parsing output (structured JSON with order details, items, prices, tracking) is ~200-500 tokens. Using ~1,500 input + 300 output tokens per email:

| Model | Input Cost (per email) | Output Cost (per email) | Total per Email |
|-------|----------------------|------------------------|----------------|
| Claude Haiku 4.5 | $0.0015 | $0.0015 | **$0.003** |
| Claude Sonnet 4.6 | $0.0045 | $0.0045 | **$0.009** |
| GPT-5 nano | $0.000075 | $0.00012 | **$0.0002** |
| GPT-5 mini | $0.000375 | $0.0006 | **$0.001** |
| Claude Haiku 4.5 (Batch, 50% off) | $0.00075 | $0.00075 | **$0.0015** |

### Cost at Scale: 100 Emails/User/Month

| Model | 1K Users/mo | 10K Users/mo | 100K Users/mo | 1M Users/mo |
|-------|-------------|--------------|----------------|-------------|
| GPT-5 nano | $20 | $200 | $2,000 | $20,000 |
| GPT-5 mini | $100 | $1,000 | $10,000 | $100,000 |
| Claude Haiku 4.5 | $300 | $3,000 | $30,000 | $300,000 |
| Claude Haiku (Batch) | $150 | $1,500 | $15,000 | $150,000 |
| Claude Sonnet 4.6 | $900 | $9,000 | $90,000 | $900,000 |

### Alternative: Purpose-Built NLP Models (spaCy / Fine-Tuned BERT)

**Training costs**:
- Fine-tuning a BERT-based email parser: ~$50-200 in compute (a few hours on a single GPU)
- Labeling 1,000-2,000 example emails for training data: ~$1,000-3,000 (manual labeling) or use LLM-generated labels
- spaCy NER pipeline training: Can run on CPU, essentially free compute

**Inference costs (self-hosted)**:
- A fine-tuned BERT model runs comfortably on a single CPU instance
- EC2 t3.medium: ~$37/month — can handle thousands of emails/hour
- EC2 m5.large: ~$84/month — can handle tens of thousands of emails/hour
- At 100K users x 100 emails = 10M emails/month: 2-3 m5.xlarge instances ≈ **$400-600/month**

**Comparison Summary**:

| Approach | 10K Users | 100K Users | 1M Users | Setup Cost |
|----------|-----------|------------|----------|------------|
| GPT-5 nano API | $200/mo | $2,000/mo | $20,000/mo | ~$0 |
| Claude Haiku Batch | $1,500/mo | $15,000/mo | $150,000/mo | ~$0 |
| Fine-tuned BERT (self-hosted) | $84/mo | $400/mo | $2,000/mo | $2,000-5,000 one-time |
| spaCy NER pipeline | $37/mo | $200/mo | $1,000/mo | $3,000-8,000 one-time |

**Recommendation for Secret Shopper**:
1. **Start with GPT-5 nano or Claude Haiku Batch API** — zero setup cost, handles parsing well, and at 1K-10K users costs only $20-1,500/month
2. **At ~50K+ users, invest in a fine-tuned BERT/spaCy model** — the crossover point where self-hosted becomes dramatically cheaper
3. **Hybrid approach**: Use LLM for complex/ambiguous emails, use pattern-matching/regex for standardized retailers (Amazon, Walmart, Target have very predictable email formats)

The hybrid approach could reduce LLM calls by 60-80% since major retailers use templated emails that simple regex can parse.

---

## 3. Price Monitoring Infrastructure

### Web Scraping Infrastructure Costs

#### Proxy Services (Required for Retailer Scraping)

| Provider | Type | Price | Notes |
|----------|------|-------|-------|
| Bright Data | Residential proxy | $3.50-10.50/GB | Industry leader, largest network |
| Smartproxy | Residential proxy | $2.20/GB | Good mid-range option |
| Smartproxy | Datacenter proxy | $0.09/GB | Cheapest, but easily detected |
| Oxylabs | Residential proxy | $10/GB | Premium quality |
| SOAX | Mobile proxy | $4/GB | For mobile-only sites |
| Proxy-Cheap | Datacenter | ~$0.30/IP | Budget option |

#### Scraping API Services (Managed)

| Provider | Pricing | Best For |
|----------|---------|----------|
| Bright Data Web Scraper API | From $1/1,000 results (pay-as-go); $499/mo subscription | Pre-built scrapers for 120+ retail domains |
| ScrapingBee | ~$49/mo for 150K API credits | Headless browser rendering |
| Apify | Free tier; $49/mo for 100 actor runs | Pre-built Amazon/retail scrapers |

#### Self-Built Scraping Infrastructure

For monitoring 10,000 products across 20 retailers, checking prices daily:

| Component | Cost/Month |
|-----------|-----------|
| 2-3 EC2 instances (t3.medium) for scrapers | $75-110 |
| Residential proxy bandwidth (~50GB/month) | $175-500 |
| Database (RDS PostgreSQL, small) | $30-50 |
| Queue service (SQS) | $5-10 |
| **Total for 10K products** | **$285-670/month** |

Scaling to 100K products: multiply proxy costs by ~8-10x = **$1,500-5,000/month**.

### Existing Price Tracking Services & APIs

| Service | Pricing | Coverage |
|---------|---------|----------|
| **Keepa** | Free basic; €19/mo subscription; API from €49/mo ($53) | Amazon only (all categories, all marketplaces) |
| **Prisync** | $99/mo (100 products); $199/mo (1K products); $399/mo (5K products); $799/mo (unlimited) | Multi-retailer competitor monitoring |
| **Price2Spy** | Similar to Prisync, ~$100-500/mo | Multi-retailer |
| **Bright Data Insights** | Custom pricing (enterprise) | AI-powered ecommerce analytics |

**Important caveats**:
- Keepa only covers Amazon — not other retailers
- Prisync is designed for B2B competitor monitoring, not consumer-facing apps
- Most price tracking APIs have usage limits and terms of service that may restrict use in a consumer product
- CamelCamelCamel does not offer a public API

### How Honey / Capital One Shopping Get Price Data

Based on research, these services use a combination of methods:

1. **Browser extension data collection**: When millions of users browse shopping sites, the extension collects pricing data passively from the pages users visit. This is their primary moat — crowdsourced price data from the extension's installed base.

2. **Affiliate network integrations**: Honey/Capital One Shopping are integrated with affiliate networks (Commission Junction, AWIN, Rakuten LinkShare, ShareASale). These networks provide product feeds and pricing data as part of the affiliate relationship.

3. **Coupon scraping**: Developer notes revealed Honey scraped competitor coupon sites (RetailMeNot, CouponFollow) for codes.

4. **Retailer partnerships**: As dominant distribution channels, they negotiate direct data feeds from participating retailers.

5. **Cookie/checkout monitoring**: The extension monitors checkout pages across supported sites, building a real-time database of prices and coupon validity.

**Key takeaway for Secret Shopper**: Without a browser extension installed on millions of devices, you can't replicate this passive data collection model. You'd need to rely on active scraping + API services, which is significantly more expensive. However, Secret Shopper's email-based approach provides a different (and potentially complementary) data source — actual transaction prices rather than listed prices.

---

## 4. Comparable ML Costs from Public Startups

### Stitch Fix (SFIX)

- **Revenue (FY2025)**: $1.27 billion
- **Data science team**: 80+ data scientists (mostly PhDs)
- **Infrastructure**: Migrated from EMR on EC2 to EMR on EKS; hundreds of auto-scaling production ML services
- **Specific cloud spend**: Not broken out in 10-K filings (consolidated under "Technology and development" expenses)
- **Technology & development expense**: Approximately $200-250M/year (roughly 15-20% of revenue), though this includes all engineering, not just ML compute
- **Estimated ML infrastructure portion**: Industry benchmarks suggest ML compute is typically 15-25% of total tech spend for ML-heavy companies, suggesting **$30-60M/year** for a company of Stitch Fix's scale and ML intensity

### General Industry Benchmarks

From the research on real-world ML projects:

| Company Stage | ML Compute Budget | Notes |
|--------------|-------------------|-------|
| Pre-seed/seed startup | $500-2,000/month | Simple models, managed services |
| Series A (product-market fit) | $2,000-10,000/month | More models, more data, some GPU |
| Series B+ (scaling) | $10,000-100,000/month | Multiple model pipelines, real-time inference |
| Growth-stage ($50M+ revenue) | $100,000-500,000/month | Large-scale training, global inference |

### Bookshop.org Case Study
- Implemented an AI-powered recommendation engine
- Total investment: **$100K-$300K over 6-9 months** (includes development, not just compute)

### Hidden Cost Multipliers
- Actual ML spending ends up **40-60% higher** than initial estimates
- Total infrastructure cost often reaches **2.5-3x the raw compute investment** when you include monitoring, data pipelines, storage, and engineering time
- Ongoing maintenance: **17-30% of initial build cost per year** (retraining, monitoring, regulatory updates)

---

## Summary: Estimated Costs for Secret Shopper by Stage

### MVP (0-1K users) — Month 1-6

| Component | Monthly Cost |
|-----------|-------------|
| Email parsing (LLM API — GPT-5 nano) | $20-50 |
| Prediction models (CPU instances) | $40-100 |
| Price monitoring (limited, Keepa API + light scraping) | $50-150 |
| Database & storage | $30-50 |
| **Total ML/data infrastructure** | **$140-350/month** |

### Growth (1K-10K users) — Month 6-18

| Component | Monthly Cost |
|-----------|-------------|
| Email parsing (LLM API) | $200-1,500 |
| Prediction models (still CPU) | $100-300 |
| Price monitoring (expanded scraping) | $300-700 |
| Database & storage | $50-200 |
| **Total ML/data infrastructure** | **$650-2,700/month** |

### Scale (10K-100K users) — Month 18+

| Component | Monthly Cost |
|-----------|-------------|
| Email parsing (transition to fine-tuned BERT + LLM hybrid) | $500-3,000 |
| Prediction models (may need GPU for embeddings) | $300-2,000 |
| Price monitoring (dedicated scraping infra) | $1,500-5,000 |
| Database & storage | $200-1,000 |
| **Total ML/data infrastructure** | **$2,500-11,000/month** |

---

## Sources

- [AWS SageMaker Pricing](https://aws.amazon.com/sagemaker/pricing/)
- [SageMaker Pricing Guide — CloudZero](https://www.cloudzero.com/blog/sagemaker-pricing/)
- [SageMaker Inference Deep Dive — Zircon.tech](https://zircon.tech/blog/the-real-cost-of-running-ai-models-on-aws-sagemaker-inference-deep-dive/)
- [GCP Vertex AI Pricing](https://cloud.google.com/vertex-ai/generative-ai/pricing)
- [Vertex AI Pricing Guide — nOps](https://www.nops.io/blog/vertex-ai-pricing/)
- [Vertex AI Top 16 Services Pricing — Finout](https://www.finout.io/blog/top-16-vertex-services-in-2026)
- [Claude API Pricing — Anthropic](https://platform.claude.com/docs/en/about-claude/pricing)
- [Claude API Pricing Breakdown — MetaCTO](https://www.metacto.com/blogs/anthropic-api-pricing-a-full-breakdown-of-costs-and-integration)
- [OpenAI API Pricing](https://openai.com/api/pricing/)
- [OpenAI Pricing 2026 — Finout](https://www.finout.io/blog/openai-pricing-in-2026)
- [Keepa Pricing — RevenueGeeks](https://revenuegeeks.com/keepa-pricing/)
- [Prisync — Competitor Price Tracking](https://prisync.com/)
- [Prisync Pricing — ITQlick](https://www.itqlick.com/prisync/pricing)
- [Bright Data Web Scraper Pricing](https://brightdata.com/pricing/web-scraper)
- [Bright Data Pricing Breakdown — Firecrawl](https://www.firecrawl.dev/blog/bright-data-pricing)
- [Cheap Rotating Proxies — Scrape.do](https://scrape.do/blog/cheap-rotating-proxies/)
- [Honey Data Collection — datarequests.org](https://www.datarequests.org/blog/honey-data-collection/)
- [Honey Extension Scandal — myip.foo](https://myip.foo/blog/honey-browser-extension-scandal)
- [Stitch Fix Algorithms Tour](https://algorithms-tour.stitchfix.com/)
- [Stitch Fix ML Platform — Multithreaded](https://multithreaded.stitchfix.com/blog/2022/07/14/deployment-for-free/)
- [ML Costs: Price Factors and Estimates — ITRex](https://itrexgroup.com/blog/machine-learning-costs-price-factors-and-estimates/)
- [AI Development Cost Estimation — Coherent Solutions](https://www.coherentsolutions.com/insights/ai-development-cost-estimation-pricing-structure-roi)
- [AWS EC2 GPU Pricing — TRG Datacenters](https://www.trgdatacenters.com/resource/aws-gpu-pricing/)
- [AWS GPU Price Reductions June 2025](https://aws.amazon.com/blogs/aws/announcing-up-to-45-price-reduction-for-amazon-ec2-nvidia-gpu-accelerated-instances/)
- [LLM Alternatives: Cost-Effective AI — MetaCTO](https://www.metacto.com/blogs/beyond-the-hype-exploring-powerful-alternatives-to-llms-for-your-next-ai-project)
- [spaCy Transformers — Explosion.ai](https://explosion.ai/blog/spacy-transformers)
