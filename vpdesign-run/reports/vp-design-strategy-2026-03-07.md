# VP Design Strategy Report

> **Date**: March 7, 2026
> **Period**: February 22 -- March 7, 2026
> **Author**: VP Design Agent (Claude Opus 4.6)
> **Status**: Initial report -- based on VP Engineering strategy context and portfolio analysis
> **Revision**: R1 -- corrected to cover full product portfolio design surfaces

---

## Executive Summary

Enkai's design maturity is at "founder stage" -- functional but inconsistent, with no design system, no brand guidelines, and critical trust issues on the public website. The portfolio has **far more design surfaces than initially assessed**: the enkai planning UI, frank web UI, bankan kanban board, mockery design tool, ja9 journal app, qualify dashboard, clearbreak mortgage calculator, and enkai-monitor dashboard. Each was built independently by AI agents with no shared design system.

```
 THE SITUATION                              THE RECOMMENDATION
 ──────────────────────────                 ─────────────────────
 Design system ............ None             Minimal token system in 2 weeks
 Brand guidelines ......... None             Colors, type, logo usage doc
 Website .................. Credibility gap   Redesign hero + remove fakes
 Portfolio UIs ............ 6+ independent   Audit all, unify with tokens
 Enterprise touchpoints ... Emails/docs only  Design the "first 48 hours"
 Designer on team ......... Jordan (partial)  Leverage AI for production
```

**Core insight**: For a 2-person team selling to enterprise, design credibility = business credibility. But with 6+ user-facing products built independently, the biggest design risk is **inconsistency**. A shared design token system applied across the portfolio prevents the "obviously different teams built these" impression.

---

## 1. Design Audit

### 1.1 Complete Design Surface Inventory

#### Core Platform Surfaces

| Surface | Type | Quality | Audience | Revenue Impact |
|---------|------|:-------:|----------|:--------------:|
| **enkai.ca website** | Marketing | Poor (fake testimonials, mixed messaging) | Prospects | Critical |
| **enkai planning UI** | Product | Unknown (double diamond, feature planning) | Founders, future customers | High |
| **enkai CLI output** | Developer tool | Unknown (terminal formatting) | Developers | Medium |
| **enkai-monitor dashboard** | Product | Unknown (stale since Jan 30) | Internal, future customers | Medium |
| **frank web UI** | Product | Unknown (container management, worktree view) | Internal | Low |

#### Portfolio Product Surfaces

| Surface | Type | Quality | Audience | Demo Value |
|---------|------|:-------:|----------|:----------:|
| **enkai-qualify dashboard** | Product | Unknown (501 commits) | Public users | High |
| **clearbreak** | Product | Unknown (8 dashboard pages, auth) | End users | High |
| **bankan** | Product | Unknown (kanban, teams, consolidated view) | Internal + demo | High |
| **ja9** | Product | Unknown (entry management, mobile layout) | Internal + demo | Medium |
| **mockery** | Product | Unknown (6 page mockups) | Internal + demo | Medium |
| **brandassador** | Product | Unknown (brand management) | Internal | Low |

#### Generated Output Surfaces

| Surface | Type | Quality | Audience | Revenue Impact |
|---------|------|:-------:|----------|:--------------:|
| **GitHub PR output** | Product output | Good (functional, well-formatted) | Enterprise customers | Critical |
| **Weekly summary email** | Communication | Does not exist | Enterprise customers | High |
| **Codebase Profile doc** | Sales asset | Does not exist | Enterprise customers | High |
| **Enterprise pilot proposal** | Sales asset | Good (clean markdown) | Prospects | High |

### 1.2 Critical Finding: Portfolio Inconsistency

Every product in the portfolio was built by AI agents working independently. This means:
- No shared color palette across products
- No shared typography
- No shared component patterns
- No shared layout conventions

For internal use, this is fine. For demos to enterprise prospects ("here's bankan, here's clearbreak, here's the planning UI"), inconsistency signals "cobbled together" rather than "professional platform."

### 1.3 Critical Finding: Trust Gap

The website is the front door for enterprise prospects. Currently it has:
- Fabricated testimonials (trust-destroying)
- Self-service SaaS pricing (doesn't match the offer)
- No visual proof of the platform working
- No clear "this is what you get" section

---

## 2. Brand Foundation

### 2.1 Brand Attributes

Based on the company's actual values and positioning:

| Attribute | Expression |
|-----------|-----------|
| **Reliable** | Clean, structured layouts. No decorative clutter. |
| **Technical** | Monospace accents. Code-inspired elements. Dark mode option. |
| **Fast** | Minimal animation. Quick load times. Direct copy. |
| **Transparent** | Real data shown. No stock photos. Actual screenshots. |
| **Enterprise-grade** | Professional typography. Consistent spacing. Accessibility. |

### 2.2 Design Tokens (Minimum Viable Design System)

These tokens should be adopted across ALL portfolio products over time:

```
 COLORS
 ──────────────────────────────────────────
 Primary ............. #10b981 (emerald)     Action, success, PRs delivered
 Secondary ........... #3b82f6 (blue)        Information, links, planning
 Accent .............. #f59e0b (amber)       Warnings, attention, qualify
 Neutral ............. #1f2937 (gray-800)    Text, backgrounds
 Surface ............. #f9fafb (gray-50)     Cards, sections
 Error ............... #ef4444 (red)         Errors, critical

 TYPOGRAPHY
 ──────────────────────────────────────────
 Headings ............ Inter (700, 600)
 Body ................ Inter (400)
 Code/Data ........... JetBrains Mono (400)
 Scale ............... 14 / 16 / 20 / 24 / 32 / 48

 SPACING
 ──────────────────────────────────────────
 Base unit ........... 4px
 Component padding ... 16px (4 units)
 Section spacing ..... 64px (16 units)
 Max content width ... 1200px

 RADIUS
 ──────────────────────────────────────────
 Small ............... 4px (buttons, inputs)
 Medium .............. 8px (cards)
 Large ............... 12px (modals, panels)
```

### 2.3 Token Adoption Priority

Not every product needs the tokens immediately. Prioritize by external visibility:

| Priority | Products | Rationale |
|----------|----------|-----------|
| P0 (now) | enkai.ca website | Enterprise prospects see this first |
| P0 (now) | Generated PR output, email templates | Enterprise customers receive these |
| P1 (before demos) | bankan, clearbreak | Will be shown in demos to prospects |
| P1 (before launch) | enkai-qualify | Public-facing SaaS product |
| P2 (later) | enkai planning UI, frank UI | Internal use, customer access in Growth tier |
| P3 (optional) | ja9, mockery, brandassador | Internal only |

### 2.4 Logo and Identity

| Element | Current State | Action |
|---------|--------------|--------|
| Logo | Exists (enkai) | Audit for scalability (favicon, social, print) |
| Favicon | Unknown | Ensure it's set and recognizable |
| Social preview (OG image) | Likely missing | Create for website sharing |
| Email signature | None | Design for Jordan and founder emails |
| Sub-brand treatment | None | Define how portfolio products relate to Enkai brand |

---

## 3. Website Redesign

### 3.1 Information Architecture

**Current**: Home / Pricing / (implicit Features)
**Recommended**:

```
 HOME
   Hero: Clear value prop + CTA
   How It Works: 3-step pipeline visual (issue-manager -> builder -> PR)
   Portfolio: "30+ products built by our platform" showcase
   Proof: Real stats (commits, repos, PRs)
   Pricing: Managed Dev tiers
   CTA: "Talk to us" / "See a demo"

 FOR ENTERPRISES (new)
   Managed AI Development explained
   The enkai platform pipeline (architecture diagram)
   Pilot program details
   Case study (clearbreak, when available)
   Portfolio showcase (bankan, ja9 as proof)
   "Schedule a call" CTA

 QUALIFY (new, when ready)
   Landing page for SaaS validators
   Features + pricing
   Signup CTA

 BLOG (new)
   Founder-led content
   Technical deep-dives about the platform
```

### 3.2 Homepage Redesign

**Hero Section** (above the fold):

```
 ┌─────────────────────────────────────────────────┐
 │                                                 │
 │  GitHub issues in.                              │
 │  Production PRs out.                            │
 │                                                 │
 │  Enkai turns your team's GitHub issues into     │
 │  tested, production-ready pull requests --      │
 │  automatically.                                 │
 │                                                 │
 │  [See How It Works]  [Talk to Us]               │
 │                                                 │
 │  ┌─────────────────────────────────────────┐    │
 │  │  // Animated or static visual showing   │    │
 │  │  // the pipeline: issue -> analysis ->  │    │
 │  │  // code gen -> PR with tests           │    │
 │  │  // Use REAL GitHub UI, not mockups      │    │
 │  └─────────────────────────────────────────┘    │
 │                                                 │
 └─────────────────────────────────────────────────┘
```

**Portfolio Proof Section** (replaces fake testimonials):

```
 ┌─────────────────────────────────────────────────┐
 │                                                 │
 │  Built by our own platform.                     │
 │  Proven across 30+ repositories.                │
 │                                                 │
 │  ┌─────────┐  ┌─────────┐  ┌─────────┐        │
 │  │  30+    │  │  500+   │  │  6+     │        │
 │  │  repos  │  │ commits │  │products │        │
 │  │ active  │  │ /week   │  │ live    │        │
 │  └─────────┘  └─────────┘  └─────────┘        │
 │                                                 │
 │  ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐          │
 │  │bankan│ │clear-│ │  ja9 │ │quali-│          │
 │  │      │ │break │ │      │ │  fy  │          │
 │  │[img] │ │[img] │ │[img] │ │[img] │          │
 │  └──────┘ └──────┘ └──────┘ └──────┘          │
 │                                                 │
 │  "We built Enkai using Enkai. Every product     │
 │   above was created and is maintained by the    │
 │   same pipeline we offer to your team."         │
 │                                                 │
 └─────────────────────────────────────────────────┘
```

### 3.3 Enterprise Page

Dedicated page for managed AI development prospects:

```
 SECTIONS:
 1. "Your team's AI-powered development partner"
 2. The pipeline: How enkai-issue-manager, enkai-builder, and frank work together
 3. What's included (table matching pilot proposal)
 4. How onboarding works (timeline visual)
 5. Portfolio showcase: "Products we've built with this platform"
 6. Pricing tiers (Pilot / Growth / Scale)
 7. FAQ (security, data access, SLA, frank container isolation)
 8. CTA: "Start your pilot"
```

---

## 4. Product Design Across the Portfolio

### 4.1 Portfolio UI Audit (Needed)

Before using any portfolio product in demos or launching publicly, each needs a design audit:

| Product | Audit Questions | Priority |
|---------|----------------|----------|
| **enkai planning UI** | Is the double diamond flow clear? Is Feature Atlas presentation useful? Can a customer navigate it? | P0 (enterprise demo asset) |
| **bankan** | Is the kanban board functional and clean? Does the consolidated view make sense? | P1 (demo asset) |
| **clearbreak** | Are 8 dashboard pages consistent? Does auth flow work? Is it mobile-responsive? | P1 (case study + demo) |
| **enkai-qualify** | Is onboarding clear for non-technical users? Is research display scannable? Does pack generation feel valuable? | P1 (public launch) |
| **frank web UI** | Is the container management view clear? Worktree view useful? | P2 (internal) |
| **ja9** | Does mobile layout work well? Entry management intuitive? | P2 (demo asset) |
| **mockery** | Are 6 page mockups coherent? Useful for design workflow? | P3 (internal) |
| **enkai-monitor** | Is the dashboard functional at all? (Stale since Jan 30) | P2 (assess first) |

### 4.2 Enterprise Touchpoint Design

The enterprise customer interacts with the enkai platform through several designed touchpoints:

| Touchpoint | Design Needed | Priority |
|------------|--------------|----------|
| **Codebase Profile doc** | Template for Day 1 delivery (Feature Atlas output) | P0 |
| **Weekly summary email** | Branded template showing enkai-builder work done | P0 |
| **PR format** | Consistent PR description template (enkai-builder output) | P0 |
| **Monthly review deck** | 5-slide metrics template | P1 |
| **Onboarding guide** | Step-by-step: GitHub App -> frank container -> first PR | P1 |
| **Invoice / receipt** | Branded Stripe template | P2 |
| **enkai-monitor customer view** | Dashboard for Growth tier customers | P2 |

### 4.3 PR Design (The Hidden Product)

The PR is the product. Every PR an enterprise customer sees is a design touchpoint. This is the output of enkai-builder and should be consistent:

```markdown
## Summary
[1-2 sentence description]

## Changes
- [Bullet list of what changed]

## Testing
- [ ] Unit tests added/updated
- [ ] Integration tests pass
- [ ] Manual testing notes

## Quality Gates
| Gate | Status |
|------|--------|
| Lint | Passed |
| Type Check | Passed |
| Tests | 14/14 passed |
| Coverage | 87% (+2%) |

## Context
- Issue: #123
- Feature Atlas: [link]
- Architecture impact: None / Minor / Major

---
Built by Enkai | enkai.ca
```

---

## 5. Design Process

### 5.1 How Design Works at a 2-Person + AI Company

Traditional design process doesn't apply. Here's what does:

| Traditional | Enkai Equivalent |
|-------------|-----------------|
| User research | Conversation notes from Jordan's enterprise calls |
| Wireframes | Text descriptions + AI mockups (mockery tool) |
| Visual design | Design tokens + component library (Tailwind) |
| Prototyping | Build it directly via enkai-builder (AI agents are fast enough) |
| User testing | Pilot customer feedback |
| Design system | Minimal tokens + Tailwind conventions shared across portfolio |

### 5.2 Jordan's Design Role

Jordan has UX/design skills. The design process should:
1. **Leverage Jordan** for high-judgment decisions (positioning, flow, brand)
2. **Use AI** for production (mockery for concepts, enkai-builder for implementation)
3. **Never block** on design perfection -- ship and iterate
4. **Focus on the 3-4 products** that enterprise prospects will see

### 5.3 Design Review Checklist

Before any customer-facing surface ships:

```
 [ ] Does it use the design tokens (colors, type, spacing)?
 [ ] Is the copy clear and jargon-free?
 [ ] Does it work on mobile?
 [ ] Are there any placeholder/fake elements?
 [ ] Would an enterprise buyer trust this?
 [ ] Does it load in under 3 seconds?
 [ ] Is it consistent with other portfolio products being shown?
```

---

## 6. Competitive Design Analysis

### 6.1 Visual Benchmarks

| Competitor | Design Quality | What We Can Learn |
|------------|:-------------:|------------------|
| **Linear** | Excellent | Clean, fast, developer-focused aesthetic |
| **Vercel** | Excellent | Dark mode, code-inspired, enterprise-ready |
| **Devin** | Good | Transparency -- shows the AI working |
| **Cursor** | Good | Developer-native feel |
| **Lovable** | Good | Friendly onboarding for non-technical users |

### 6.2 Design Principles to Steal

From **Linear**: Speed as a design principle. Every interaction should feel instant.
From **Vercel**: Dark mode as default for developer tools. Monospace typography for code elements.
From **Devin**: Showing the work. Don't hide the AI -- let customers see what's happening in the pipeline.

---

## 7. 30-Day Design Sprint

```
 WEEK 1 (Critical fixes)
   Remove fake testimonials from website .............. Day 1
   Define design tokens (colors, type, spacing) ....... Day 2-3
   Redesign homepage hero section ...................... Day 3-5
   Create OG image for social sharing .................. Day 5

 WEEK 2 (Enterprise touchpoints + portfolio audit)
   Design Codebase Profile document template ........... Day 8-9
   Design weekly summary email template ................ Day 9-10
   Design PR description template (enkai-builder) ...... Day 10
   Audit enkai planning UI (screenshots needed) ........ Day 11
   Audit bankan + clearbreak for demo readiness ........ Day 12

 WEEK 3 (Website + key product surfaces)
   Build enterprise landing page with pipeline visual .. Day 15-17
   Apply design tokens to bankan (if demo-ready) ....... Day 17-18
   Design qualify landing page ......................... Day 18-19
   Create pitch deck template (5 slides) ............... Day 19-20

 WEEK 4 (Polish + consistency)
   Responsive testing on all new pages ................. Day 22-23
   Accessibility audit (contrast, keyboard) ............ Day 23-24
   Create social media templates for Jordan ............ Day 24-25
   Document design token adoption status per product ... Day 25
```

---

## 8. Risk Assessment

| Risk | L | I | Mitigation |
|------|:-:|:-:|------------|
| Fake testimonials destroy enterprise trust | L* | **C** | Remove TODAY |
| Portfolio products look inconsistent in demos | H | H | Apply tokens to top 3-4 demo products. Don't show the rest. |
| enkai planning UI not polished enough for demos | M | H | Audit first. If not ready, demo via GitHub + CLI instead. |
| No design consistency across 30+ repos | H | M | Design tokens + checklist enforced on all new work. Retrofit selectively. |
| Qualify UI not ready for public users | M | H | Audit before launch. Budget 1 week for fixes. |
| Jordan too busy for design review | H | M | AI drafts, Jordan approves. Limit review to 30 min/week. |
| Website looks "AI-generated" (generic) | M | M | Use real screenshots from portfolio products, not stock art |
| enkai-monitor dashboard abandoned | M | M | Assess: restart, replace, or defer |
| Accessibility issues block enterprise deals | L | M | Basic audit in Week 4. Full WCAG later. |

---

## 9. Open Questions for Founders

| # | Question | Why It Matters |
|:-:|----------|---------------|
| 1 | Can I see the enkai planning UI? | Need to audit for enterprise demo readiness |
| 2 | Can I see the frank web UI? | Need to understand internal design baseline |
| 3 | Can I see bankan, ja9, mockery, clearbreak? | Need to audit for demo readiness and consistency |
| 4 | Can I see the enkai-qualify dashboard? | Need to audit before designing landing page |
| 5 | What's the enkai.ca tech stack? (Next.js? Tailwind?) | Determines how fast we can implement changes |
| 6 | Does Jordan have preferred design tools? (Figma? Direct code?) | Determines design workflow |
| 7 | Are there existing brand assets (logo files, color values)? | Need for design tokens |
| 8 | Should portfolio products share one visual identity or have sub-brands? | Determines brand architecture |
| 9 | Which 3-4 products will be shown in enterprise demos? | Focus design effort there first |
| 10 | How does Jordan want to review design work? (Async? Live?) | Sets the collaboration model |

---

## 10. What I Need From You

```
 1. Screenshots or access to all portfolio UIs
    -> enkai planning UI, frank UI, bankan, clearbreak, ja9,
       qualify, mockery, enkai-monitor
    -> I need to audit the full design surface area

 2. Access to enkai.ca source code
    -> To assess implementation effort for redesign

 3. Logo files and any existing brand assets
    -> Foundation for design tokens

 4. Which 3-4 products will be demo'd to enterprise prospects?
    -> Those get design tokens first

 5. Approve the design tokens above (colors, type, spacing)
    -> Everything else builds on this

 6. Confirm: Are you OK shipping a portfolio proof section
    instead of testimonials?
    -> This is the replacement strategy for the fake quotes
```

---

<sub>Report generated by VP Design Agent (Claude Opus 4.6) | Session: vpdesign-20260307 | R1</sub>
