# VP Finance Strategy Report

> **Date**: March 7, 2026
> **Period**: February 22 -- March 7, 2026
> **Author**: VP Finance Agent (Claude Opus 4.6)
> **Status**: Initial report -- based on VP Engineering strategy context and portfolio analysis
> **Revision**: R1 -- corrected to include full portfolio cost allocation and revenue analysis

---

## Executive Summary

Enkai is a pre-revenue bootstrapped company with minimal burn, no debt, and two founders employed full-time elsewhere. This is an unusually strong financial position for a startup -- the founders can afford to be patient. But patience is not a strategy. The company needs to close its first paid deal to validate the business model, not just to generate revenue.

The financial picture is more complex than "AWS costs ~$2K/month" suggests -- the company maintains **30+ repositories** across a portfolio of products, each consuming infrastructure resources. Understanding cost allocation per product is essential for pricing decisions.

```
 FINANCIAL SNAPSHOT                         KEY NUMBERS
 ──────────────────────────                 ─────────────────────
 Revenue (lifetime) ........ $0             Monthly burn: ~$2,000-2,400
 Cash reserves ............. Unknown         Runway: Indefinite (employed founders)
 Monthly burn (AWS) ........ ~$2,000         Break-even: 1 Pilot customer ($5K)
 Claude subscriptions ...... 2x Max 20x     Target: $20K/month by month 3-6
 Products in portfolio ..... 30+ repos       Cost allocation unknown
 Debt ...................... $0              Equity given: 50% of clearbreak
 External funding .......... $0
 Founder salaries .......... $0 from Enkai
```

**Core insight**: The financial risk isn't running out of money -- it's running out of motivation. Two employed founders working evenings and weekends need to see revenue to sustain the effort. First deal matters more for morale than for cash flow.

---

## 1. Current Financial State

### 1.1 Cost Structure

| Category | Monthly Cost | Annual Cost | Notes |
|----------|:-----------:|:----------:|-------|
| **AWS Infrastructure** | ~$2,000 | ~$24,000 | ECS Fargate, S3, DynamoDB, Route53, CDK stacks |
| **Claude Max 20x** (x2) | ~$400 | ~$4,800 | Two subscriptions for AI agent work |
| **Domain (enkai.ca)** | ~$3 | ~$35 | Annual registration |
| **GitHub** | $0 | $0 | Free tier (public repos) or included |
| **Total Monthly Burn** | **~$2,400** | **~$28,800** | |

### 1.2 AWS Cost Allocation by Product (Estimated)

This is the critical view that was missing. The $2,000/month AWS bill supports the entire portfolio:

| Product/Service | Est. Monthly AWS Cost | Resources Used | Can Be Reduced? |
|----------------|:--------------------:|---------------|:---------------:|
| **enkai platform** | ~$600 | ECS (builder, issue-manager), SQS, DynamoDB | Partially -- issue-manager already disabled |
| **enkai-infra** | ~$300 | CDK/CloudFormation overhead (30 stacks), IAM, Secrets Manager | Yes -- consolidate unused stacks |
| **frank** | ~$400 | ECS Fargate containers (rightsized to 2vCPU/4GB) | Already optimized |
| **enkai-qualify** | ~$200 | ECS, S3, Cognito, health endpoints | Minimal |
| **clearbreak** | ~$150 | ECS, RDS/Prisma, auth | Scale with usage |
| **Shared infrastructure** | ~$250 | VPC, NAT Gateway, Route53, CloudFront, logging | NAT Gateway + logging have savings potential |
| **Other portfolio** | ~$100 | bankan, ja9, mockery (if hosted) | Review if any are running idle |
| **Total** | **~$2,000** | | |

**Key finding**: The enkai platform core (enkai + frank) accounts for ~$1,000/month -- half the total AWS bill. This is the cost of goods sold (COGS) for the managed AI development service. Everything else is either product development cost or can be attributed to specific portfolio products.

**Action**: Request detailed AWS Cost Explorer export with resource tagging to validate these estimates. Consider implementing AWS cost allocation tags by product.

### 1.3 Hidden Costs

| Item | Est. Monthly | Notes |
|------|:-----------:|-------|
| Founder time (opportunity cost) | $15-25K each | Both employed full-time; Enkai is evenings/weekends |
| MacBook runner (electricity) | ~$20 | Negligible |
| Potential API costs (future) | $500-2,000 | When Claude subscriptions hit limits |
| Portfolio maintenance overhead | Unmeasured | 30+ repos consume AI agent time even when "idle" |

---

## 2. Revenue Model Analysis

### 2.1 Stream A: Managed AI Development (Primary)

Powered by the enkai platform (enkai-builder + frank + pedro):

| Metric | Pilot | Growth | Scale |
|--------|:-----:|:------:|:-----:|
| **Monthly price** | $5,000 | $10,000 | $20,000+ |
| **Founding discount** | $3,500 | $7,000 | Custom |
| **COGS per customer** | ~$400 | ~$600 | ~$1,000 |
| **Gross margin** | **89%** | **91%** | **95%** |
| **Min commitment** | 3 months | 3 months | Annual |
| **Contract value (min)** | $10,500 | $21,000 | $240,000+ |

**COGS breakdown per enterprise customer:**

| Component | Cost | Notes |
|-----------|:----:|-------|
| frank container time | $150-300 | Dedicated ECS Fargate capacity |
| Claude API usage (future) | $100-300 | Currently covered by subscription |
| S3/DynamoDB (artifacts, state) | $10-20 | Minimal |
| SQS (issue dispatch) | $5-10 | Minimal |
| Data transfer | $20-50 | Depends on repo size |
| **Total COGS per customer** | **$285-680** | |

**Margin analysis**: The managed AI development service has extraordinary gross margins because the "labor" is AI agents running on existing infrastructure. The marginal cost of serving a customer is primarily incremental frank container time and Claude API usage.

### 2.2 Stream B: enkai-qualify (Secondary)

| Metric | Free | Builder | Pro | Team |
|--------|:----:|:-------:|:---:|:----:|
| **Monthly price** | $0 | $29 | $79 | $199 |
| **COGS per user** | ~$2 | ~$5 | ~$10 | ~$15 |
| **Gross margin** | N/A | **83%** | **87%** | **92%** |

**Infrastructure cost**: qualify runs on ~$200/month AWS regardless of user count (up to ~100 users). Beyond that, scaling costs are primarily Claude API for research generation.

**Revenue significance**: At 50 paid subscribers averaging $40/month, qualify generates $2,000/month with ~$500 COGS = $1,500 gross profit. Material revenue requires 200+ subscribers.

### 2.3 Stream C: clearbreak (Partner)

| Item | Value |
|------|-------|
| Equity split | 50% Enkai / 50% Andy |
| Revenue model | TBD (subscription likely) |
| Enkai's role | Development + hosting |
| Hosting cost to Enkai | ~$150/month (ECS + RDS) |
| Revenue potential | Unknown -- needs market validation |

**Concern**: 50% equity for a project where Enkai does 100% of the development is generous. This is acceptable for customer #1 (case study value) but should not be the template for future partnerships.

### 2.4 Stream D: Portfolio Products (Future Potential)

Products built by the platform that could generate revenue in the future:

| Product | Revenue Model Options | Current Cost | Revenue Potential |
|---------|----------------------|:----------:|:-----------------:|
| **bankan** | Freemium SaaS kanban | ~$50/month | Low-medium (crowded market) |
| **ja9** | Premium journal app | ~$30/month | Low (crowded market) |
| **mockery** | Design tool subscription | ~$30/month | Medium (niche) |
| **brandassador** | Brand management SaaS | ~$30/month | Medium (niche, 18 features planned) |

**Recommendation**: These are not revenue priorities. Their value is as platform proof points and internal tools. Don't invest in monetization until core revenue is established.

---

## 3. Financial Projections

### 3.1 Conservative Scenario (Most Likely)

```
                          Month 1   Month 2   Month 3   Month 4   Month 5   Month 6
 ─────────────────────────────────────────────────────────────────────────────────────
 REVENUE
 Managed Dev (Stream A)    $0      $3,500    $3,500    $7,000   $10,500   $10,500
   Pilot customer #1        -      $3,500    $3,500    $3,500    $3,500    $3,500
   Growth customer #1       -         -         -      $3,500    $7,000    $7,000
 Qualify (Stream B)         $0        $0       $200      $400      $800    $1,200
 Clearbreak                 $0        $0        $0        $0       $500      $500
 ─────────────────────────────────────────────────────────────────────────────────────
 TOTAL REVENUE              $0     $3,500    $3,700    $7,400   $11,800   $12,200

 COSTS
 Platform (enkai+frank)  $1,000    $1,200    $1,400    $1,600    $1,800    $2,000
 Portfolio products        $500      $500      $500      $500      $500      $500
 Shared infra              $500      $500      $500      $500      $500      $500
 Claude (subs -> API)      $400      $400      $400      $600      $800    $1,000
 Stripe fees (2.9%+30c)     $0       $105      $110      $220      $350      $360
 Domain + misc              $10       $10       $10       $10       $10       $10
 ─────────────────────────────────────────────────────────────────────────────────────
 TOTAL COSTS             $2,410    $2,715    $2,920    $3,430    $3,960    $4,370

 NET INCOME             -$2,410      $785      $780    $3,970    $7,840    $7,830
 CUMULATIVE             -$2,410   -$1,625     -$845    $3,125   $10,965   $18,795
```

### 3.2 Optimistic Scenario

```
                          Month 1   Month 2   Month 3   Month 4   Month 5   Month 6
 ─────────────────────────────────────────────────────────────────────────────────────
 REVENUE
 Managed Dev (Stream A)  $3,500    $7,000   $10,500   $14,000   $17,500   $20,000
 Qualify (Stream B)         $0       $500    $1,000    $1,500    $2,000    $3,000
 Clearbreak                 $0        $0       $500      $500    $1,000    $1,000
 ─────────────────────────────────────────────────────────────────────────────────────
 TOTAL REVENUE           $3,500    $7,500   $12,000   $16,000   $20,500   $24,000

 TOTAL COSTS             $2,600    $3,000    $3,500    $4,000    $4,500    $5,000
 NET INCOME                $900    $4,500    $8,500   $12,000   $16,000   $19,000
```

### 3.3 Pessimistic Scenario

```
                          Month 1   Month 2   Month 3   Month 4   Month 5   Month 6
 ─────────────────────────────────────────────────────────────────────────────────────
 REVENUE                    $0        $0        $0     $3,500    $3,500    $3,500
 TOTAL COSTS             $2,410    $2,410    $2,410    $2,600    $2,600    $2,600
 NET INCOME             -$2,410   -$2,410   -$2,410      $900      $900      $900
 CUMULATIVE             -$2,410   -$4,820   -$7,230   -$6,330   -$5,430   -$4,530
```

Even the pessimistic scenario is survivable because founders have day jobs. But 6 months of $0 revenue would likely kill motivation.

---

## 4. Pricing Analysis

### 4.1 Managed AI Development Pricing

**Is $5K/month (or $3,500 founding) too low?**

| Comparison | Cost | Notes |
|------------|:----:|-------|
| Junior developer (US) | $5-8K/month | Salary + benefits + overhead |
| Senior developer (US) | $12-18K/month | Salary + benefits + overhead |
| Dev agency (20 features) | $20-40K/month | At $1-2K per feature |
| Enkai Pilot (20 issues) | $3,500-5K/month | 89%+ gross margin |

**Verdict**: The pricing is appropriate for a founding pilot. It's cheap enough to be a no-brainer for prospects ("less than a junior dev") while maintaining excellent margins. The founding discount creates urgency.

**However**: The Pilot tier at $3,500 (with founding discount) only covers costs + modest profit. The real business begins at Growth tier ($7-10K). Ensure the pilot-to-growth upgrade path is clear in contracts.

### 4.2 Qualify Pricing

**Concern**: $29-199/month is standard SaaS pricing but requires significant volume to be meaningful revenue.

**Recommendation**: Don't optimize qualify pricing yet. Keep it simple, keep the free tier generous, and focus on whether the qualify-to-managed-dev funnel converts. Qualify's strategic value as a lead funnel may exceed its direct subscription revenue.

### 4.3 Portfolio Product Monetization

Not recommended at this stage. The portfolio products (bankan, ja9, mockery, brandassador) serve as:
1. Proof of platform capability (marketing value)
2. Internal productivity tools
3. Test beds for the enkai platform

Monetization would distract from the core enterprise revenue motion.

### 4.4 Contract Terms

| Term | Recommendation | Rationale |
|------|---------------|-----------|
| Payment terms | Net 15, due monthly | Standard SaaS |
| Minimum commitment | 3 months (Pilot/Growth) | Enough time to demonstrate value |
| Auto-renewal | Month-to-month after initial term | Reduces friction |
| Termination | 30 days written notice | Standard |
| Annual discount | 2 months free (17% off) | Incentivize predictable revenue |
| Pre-payment | 10% discount for quarterly pre-pay | Improve cash flow |

---

## 5. Financial Controls

### 5.1 Accounting Setup (Needed)

| Item | Status | Action |
|------|--------|--------|
| Business bank account | Unknown | Confirm exists and is separate from personal |
| Accounting software | Unknown | QuickBooks or Wave (free) recommended |
| Stripe account | Not set up | Required before first invoice |
| HST/GST registration | Unknown | Required in Canada if revenue >$30K/year |
| Corporate tax filing | Unknown | Confirm fiscal year and filing status |
| Invoicing process | None | Stripe auto-invoicing recommended |
| AWS cost allocation tags | Not set up | Tag resources by product for cost tracking |

### 5.2 Expense Tracking

At current scale, expense tracking is simple but should be organized by product:

| Category | How to Track | Allocation |
|----------|-------------|-----------|
| AWS | Monthly bill with cost allocation tags | By product |
| Claude | Subscription receipts | Shared across platform |
| Domain | Annual receipt | Corporate |
| Everything else | Founders to submit receipts monthly | Corporate |

**Recommendation**: Set up AWS cost allocation tags NOW. Tag resources with `product: enkai`, `product: qualify`, `product: clearbreak`, `product: bankan`, etc. This will give accurate per-product cost data within 30 days.

### 5.3 Tax Considerations (Canada)

| Item | Notes |
|------|-------|
| **HST/GST** | Must register once revenue exceeds $30K in 4 consecutive quarters. Register proactively if expecting enterprise deals. |
| **SR&ED** | Scientific Research & Experimental Development tax credits. AI agent development likely qualifies. Could recover 35-65% of eligible R&D expenses. Requires documentation. |
| **CCPC benefits** | Canadian-Controlled Private Corporation: small business deduction on first $500K of active business income (9% federal rate vs. 15%). |
| **Founder compensation** | When revenue supports it, salary vs. dividend optimization. Consult accountant. |

**SR&ED is significant**: If Enkai qualifies, the R&D tax credit could recover $10-20K+ in AWS and development costs retroactively. The entire portfolio of 30+ repos built by AI agents is potentially eligible R&D activity. This should be explored with an SR&ED specialist.

---

## 6. AWS Cost Optimization

### 6.1 Portfolio-Level Optimization

| Opportunity | Est. Monthly Savings | Effort | Products Affected |
|-------------|:-------------------:|:------:|-------------------|
| Terminate unused CDK stacks from 30-stack set | $100-300 | Medium | enkai-infra |
| Stop hosting idle portfolio products | $50-150 | Low | bankan, ja9, mockery (if running) |
| Reserved Instances for stable workloads | $200-400 | Low | frank, enkai platform |
| S3 lifecycle policies | $20-50 | Low | All products |
| NAT Gateway -> VPC endpoints | $50-100 | Medium | Shared infra |
| Consolidate logging (30-day retention) | $30-50 | Low | All products |
| **Total potential savings** | **$450-1,050** | | |

### 6.2 Scaling Costs per Enterprise Customer

| Per Customer Component | Monthly Cost | Platform Component |
|-----------------------|:-----------:|-------------------|
| frank container time | $150-300 | ECS Fargate |
| Claude API (post-migration) | $100-300 | API billing |
| enkai-builder compute | $50-100 | ECS + SQS |
| S3 storage (repos, artifacts) | $10-20 | S3 |
| Data transfer | $20-50 | EC2/ECS |
| **Total per customer** | **$330-770** | |

At $5,000/month per Pilot customer, COGS of $330-770 = **85-93% gross margin**.

### 6.3 Claude Subscription vs. API Migration

| | 2 Subscriptions | API Billing |
|---|:-:|:-:|
| Monthly cost | ~$400 | Variable ($500-2,000+) |
| Capacity | Limited (rate limits) | Unlimited |
| Scalability | Ceiling at ~3 customers | Scales with revenue |
| Portfolio support | Covers all 30+ repos | Per-token across all repos |
| Break-even point | N/A | ~3 concurrent enterprise customers |

**Recommendation**: Stay on subscriptions until revenue from 3+ enterprise customers funds the API migration. The subscriptions currently support the entire 30+ repo portfolio -- API migration must account for ALL portfolio usage, not just enterprise customer work.

---

## 7. Funding Strategy

### 7.1 Current Position: Bootstrap

**Advantages**:
- 100% equity retained (except 50% of clearbreak)
- No board obligations
- No growth pressure from investors
- Founders maintain full control
- Portfolio proves capability without external validation

**Disadvantages**:
- Growth limited by founder time
- No cash cushion for aggressive hiring
- Can't invest heavily in sales/marketing
- 30+ repo portfolio is high maintenance for 2 people

### 7.2 Should You Raise?

**Not yet.** The business model hasn't been validated with paying customers. Raising now would mean:
- Selling equity at low valuation (no revenue, no traction)
- Taking on growth obligations that conflict with day jobs
- Adding overhead (board, reporting) to a 2-person team

**When to reconsider**:
- 3+ paying enterprise customers (validates demand)
- $15K+ MRR sustained for 3 months (validates unit economics)
- Clear growth bottleneck that only capital solves (e.g., need to hire full-time)

### 7.3 Alternative Funding

| Source | Amount | Fit |
|--------|--------|-----|
| **SR&ED tax credits** | $10-20K retroactive | Excellent -- 30+ repos of AI R&D is strong evidence |
| **IRAP (NRC)** | Up to $50K | Good -- non-repayable for Canadian tech SMEs |
| **BDC loans** | $50-250K | Moderate -- low interest but still debt |
| **Angel investors** | $50-200K | Only if validated (see above) |
| **Revenue-based financing** | Based on MRR | Only at $10K+ MRR |

**Priority**: Apply for SR&ED and explore IRAP. Both are non-dilutive. The 30+ repo portfolio with 500+ weekly commits is compelling evidence for SR&ED eligibility.

---

## 8. Financial Milestones

```
 MILESTONE                              TARGET           SIGNIFICANCE
 ─────────────────────────────────────────────────────────────────────────
 First dollar of revenue                Month 1-2        Business validation
 Monthly revenue > monthly costs        Month 2-3        Operational break-even
 $10K MRR                               Month 4-5        Sustainable business signal
 $20K MRR                               Month 5-7        Founder income potential
 $30K MRR                               Month 8-12       Consider: quit day jobs?
 $50K MRR                               Month 12-18      First hire possible
```

### Key Decision Points

| MRR | Decision to Make |
|:---:|-----------------|
| $5K | Set up AWS cost allocation tags. Start per-product cost tracking. |
| $10K | Register for HST/GST. Set up proper accounting. Review portfolio: which products earn their hosting costs? |
| $15K | Start founder compensation (modest). Engage accountant. SR&ED filing. |
| $20K | Evaluate: quit one day job? Hire contractor? Review portfolio pruning. |
| $30K | Evaluate: both founders full-time? First employee? |
| $50K | Evaluate: raise growth capital? Or stay bootstrapped? |

---

## 9. Risk Assessment

| Risk | L | I | Mitigation |
|------|:-:|:-:|------------|
| No revenue in 90 days | M | H | Jordan sends proposals THIS WEEK. Founding discount creates urgency. |
| AWS costs spike with enterprise customers | M | M | Set billing alerts at $3K and $5K. Cost allocation tags to identify source. |
| Portfolio hosting costs grow unchecked | M | M | Review per-product costs monthly. Shut down idle products. |
| Enterprise customer doesn't pay on time | M | M | Net 15 terms. Stripe auto-billing. Follow up immediately. |
| Claude pricing changes | M | M | Budget for API transition. API costs must cover full portfolio usage. |
| Tax compliance issues | L | M | Engage accountant before first invoice. Register HST proactively. |
| 50% clearbreak equity sets bad precedent | M | M | Document this as founding-partner exception. Future deals: 80/20 or fee-based. |
| Founders burn out before revenue | M | H | First deal is a motivation milestone. Celebrate it. |
| SR&ED claim rejected | L | L | Low risk -- 30+ repos of AI development clearly qualifies. Keep documentation. |
| 30 CDK stacks create unexpected costs | M | M | Audit and consolidate. Terminate unused stacks. |

---

## 10. Open Questions for Founders

| # | Question | Why It Matters |
|:-:|----------|---------------|
| 1 | Is there a separate business bank account? | Required for clean accounting |
| 2 | What accounting software (if any) is in use? | Need to set up before first invoice |
| 3 | What is the corporate fiscal year end? | Tax planning |
| 4 | Have you explored SR&ED tax credits? | 30+ repos of AI R&D could recover $10-20K+ |
| 5 | What are each founder's runway expectations? | Determines urgency of revenue |
| 6 | At what MRR would you consider going full-time? | Determines financial targets |
| 7 | Is the founding discount (30%) approved by both founders? | Affects first-deal economics |
| 8 | How is the 50/50 clearbreak equity documented? | Needs formal agreement |
| 9 | What are the actual AWS costs? (Need Cost Explorer export) | My per-product estimates need validation |
| 10 | Are any portfolio products running idle but costing money? | Quick savings opportunity |
| 11 | Which of the 30 CDK stacks are actually in use? | Consolidation savings |

---

## 11. What I Need From You

```
 1. Actual AWS bill for the last 3 months
    -> My estimates need validation. Cost Explorer CSV preferred.
    -> Ideally with resource-level breakdown for cost allocation.

 2. Set up AWS cost allocation tags by product
    -> Tag: product=enkai, product=qualify, product=clearbreak, etc.
    -> This gives accurate per-product costs within 30 days.

 3. Confirm business bank account exists
    -> If not, set one up before first invoice

 4. Confirm: is an accountant engaged?
    -> If not, find one who knows SR&ED. Budget $2-3K/year.
    -> 30+ repos of AI development is a strong SR&ED case.

 5. Each founder's "magic number" -- what MRR makes this feel real?
    -> Financial planning needs emotional targets, not just math

 6. List which portfolio products are currently hosted (costing money)
    -> Quick win: shut down anything not being used or demo'd
```

---

<sub>Report generated by VP Finance Agent (Claude Opus 4.6) | Session: vpfinance-20260307 | R1</sub>
