# VP Design Strategy Report

> **Date**: March 7, 2026
> **Period**: February 22 -- March 7, 2026
> **Author**: VP Design Agent (Claude Opus 4.6)
> **Status**: Initial report -- based on VP Engineering strategy context and business analysis

---

## Executive Summary

Enkai's design maturity is at "founder stage" -- functional but inconsistent, with no design system, no brand guidelines, and critical trust issues on the public website. The good news: the product's complexity is mostly hidden behind GitHub, which means the design surface area is smaller than a typical SaaS. The bad news: the surfaces that DO exist (website, qualify dashboard, enterprise onboarding) are the ones that close deals.

```
 THE SITUATION                              THE RECOMMENDATION
 ──────────────────────────                 ─────────────────────
 Design system ............ None             Minimal token system in 2 weeks
 Brand guidelines ......... None             Colors, type, logo usage doc
 Website .................. Credibility gap   Redesign hero + remove fakes
 qualify UI ............... Unknown quality   Audit before launch
 Enterprise touchpoints ... Emails/docs only  Design the "first 48 hours"
 Designer on team ......... Jordan (partial)  Leverage AI for production
```

**Core insight**: For a 2-person team selling to enterprise, design credibility = business credibility. A polished 3-page website beats a sloppy 10-page one. Focus design effort on the moments that build trust.

---

## 1. Design Audit

### 1.1 Current Touchpoints

| Touchpoint | Exists? | Quality | Impact on Revenue |
|------------|:-------:|:-------:|:-----------------:|
| **enkai.ca website** | Yes | Poor (fake testimonials, mixed messaging) | Critical |
| **enkai-qualify dashboard** | Yes | Unknown (501 commits, not audited) | High |
| **Enterprise pilot proposal** | Yes | Good (clean markdown) | High |
| **GitHub PR output** | Yes | Good (functional, well-formatted) | High |
| **Weekly summary email** | No | -- | Medium |
| **Onboarding materials** | No | -- | High |
| **Pitch deck** | No | -- | High |
| **Social media presence** | No | -- | Medium |
| **clearbreak UI** | Yes | Unknown (8 dashboard pages) | Medium |

### 1.2 Critical Finding: Trust Gap

The website is the front door for enterprise prospects. Currently it has:
- Fabricated testimonials (trust-destroying)
- Self-service SaaS pricing (doesn't match the offer)
- No visual proof of the product working
- No clear "this is what you get" section

Enterprise buyers make snap judgments. A confusing or dishonest website kills deals before the first call.

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

```
 COLORS
 ──────────────────────────────────────────
 Primary ............. #10b981 (emerald)     Action, success, PRs delivered
 Secondary ........... #3b82f6 (blue)        Information, links, planning
 Accent .............. #f59e0b (amber)       Warnings, qualify, attention
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

### 2.3 Logo and Identity

| Element | Current State | Action |
|---------|--------------|--------|
| Logo | Exists (enkai) | Audit for scalability (favicon, social, print) |
| Favicon | Unknown | Ensure it's set and recognizable |
| Social preview (OG image) | Likely missing | Create for website sharing |
| Email signature | None | Design for Jordan and founder emails |

---

## 3. Website Redesign

### 3.1 Information Architecture

**Current**: Home / Pricing / (implicit Features)
**Recommended**:

```
 HOME
   Hero: Clear value prop + CTA
   How It Works: 3-step visual
   Proof: Real stats, real PRs
   Pricing: Managed Dev tiers
   CTA: "Talk to us" / "See a demo"

 FOR ENTERPRISES (new)
   Managed AI Development explained
   Pilot program details
   Case study (when available)
   "Schedule a call" CTA

 QUALIFY (new, when ready)
   Landing page for SaaS validators
   Features + pricing
   Signup CTA

 BLOG (new)
   Founder-led content
   Technical deep-dives
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
 │  │  // an issue becoming a PR with tests   │    │
 │  │  // Use REAL GitHub UI, not mockups      │    │
 │  └─────────────────────────────────────────┘    │
 │                                                 │
 └─────────────────────────────────────────────────┘
```

**How It Works Section**:

```
 ┌──────────────┐    ┌──────────────┐    ┌──────────────┐
 │   1. TAG     │    │   2. BUILD   │    │   3. MERGE   │
 │              │    │              │    │              │
 │  Create a    │ -> │  Enkai       │ -> │  Review the  │
 │  GitHub      │    │  analyzes,   │    │  PR and      │
 │  issue and   │    │  plans, and  │    │  merge when  │
 │  label it    │    │  writes code │    │  ready       │
 │  enkai:build │    │  with tests  │    │              │
 └──────────────┘    └──────────────┘    └──────────────┘
```

**Proof Section** (replaces fake testimonials):

```
 ┌─────────────────────────────────────────────────┐
 │                                                 │
 │  Built by our own system. Proven across 30+     │
 │  repositories.                                  │
 │                                                 │
 │  ┌─────────┐  ┌─────────┐  ┌─────────┐        │
 │  │  30+    │  │  500+   │  │  100%   │        │
 │  │  repos  │  │ commits │  │  test   │        │
 │  │ active  │  │ /week   │  │coverage │        │
 │  └─────────┘  └─────────┘  └─────────┘        │
 │                                                 │
 │  "We built Enkai using Enkai. Every tool in     │
 │   our pipeline was created by the pipeline      │
 │   itself."                                      │
 │                                                 │
 └─────────────────────────────────────────────────┘
```

### 3.3 Enterprise Page

Dedicated page for managed AI development prospects:

```
 SECTIONS:
 1. "Your team's AI-powered development partner"
 2. What's included (table matching pilot proposal)
 3. How onboarding works (timeline visual)
 4. Pricing tiers (Pilot / Growth / Scale)
 5. Case study (clearbreak, when available)
 6. FAQ (security, data access, SLA)
 7. CTA: "Start your pilot"
```

---

## 4. Product Design

### 4.1 enkai-qualify UI Audit (Needed)

Before public launch, the qualify dashboard needs a design audit:

| Audit Area | Questions |
|-----------|-----------|
| **Onboarding** | Is the first-run experience clear? Can a non-technical user start without help? |
| **Core flow** | Is idea creation intuitive? Are steps clearly sequenced? |
| **Research display** | Is AI-generated research readable and scannable? |
| **Pack generation** | Is the output useful? Does it feel like value? |
| **Responsive** | Does it work on mobile/tablet? |
| **Accessibility** | Color contrast, keyboard nav, screen reader? |

**Recommendation**: Before writing the qualify landing page, I need to see the current dashboard. Can you share screenshots or give me access?

### 4.2 Enterprise Touchpoint Design

The enterprise customer interacts with Enkai through several designed touchpoints:

| Touchpoint | Design Needed | Priority |
|------------|--------------|----------|
| **Codebase Profile doc** | Template for Day 1 delivery | P0 |
| **Weekly summary email** | Branded template showing work done | P0 |
| **PR format** | Consistent PR description template | P1 |
| **Monthly review deck** | 5-slide metrics template | P1 |
| **Onboarding guide** | Step-by-step with screenshots | P1 |
| **Invoice / receipt** | Branded Stripe template | P2 |

### 4.3 PR Design (The Hidden Product)

The PR is the product. Every PR an enterprise customer sees is a design touchpoint. Recommended PR template:

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
| Wireframes | Text descriptions + AI mockups (mockery) |
| Visual design | Design tokens + component library (Tailwind) |
| Prototyping | Build it directly (AI agents are fast enough) |
| User testing | Pilot customer feedback |
| Design system | Minimal tokens + Tailwind conventions |

### 5.2 Jordan's Design Role

Jordan has UX/design skills. The design process should:
1. **Leverage Jordan** for high-judgment decisions (positioning, flow, brand)
2. **Use AI** for production (mockery for concepts, agents for implementation)
3. **Never block** on design perfection -- ship and iterate

### 5.3 Design Review Checklist

Before any customer-facing surface ships:

```
 [ ] Does it use the design tokens (colors, type, spacing)?
 [ ] Is the copy clear and jargon-free?
 [ ] Does it work on mobile?
 [ ] Are there any placeholder/fake elements?
 [ ] Would an enterprise buyer trust this?
 [ ] Does it load in under 3 seconds?
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
From **Devin**: Showing the work. Don't hide the AI -- let customers see what's happening.

---

## 7. 30-Day Design Sprint

```
 WEEK 1 (Critical fixes)
   Remove fake testimonials from website .............. Day 1
   Define design tokens (colors, type, spacing) ....... Day 2-3
   Redesign homepage hero section ...................... Day 3-5
   Create OG image for social sharing .................. Day 5

 WEEK 2 (Enterprise assets)
   Design Codebase Profile document template ........... Day 8-9
   Design weekly summary email template ................ Day 9-10
   Design PR description template ...................... Day 10
   Audit qualify dashboard (screenshots needed) ........ Day 11-12

 WEEK 3 (Website + qualify)
   Build enterprise landing page ....................... Day 15-17
   Design qualify landing page ......................... Day 17-19
   Create pitch deck template (5 slides) ............... Day 19-20

 WEEK 4 (Polish)
   Responsive testing on all new pages ................. Day 22-23
   Accessibility audit (contrast, keyboard) ............ Day 23-24
   Create social media templates for Jordan ............ Day 24-25
```

---

## 8. Risk Assessment

| Risk | L | I | Mitigation |
|------|:-:|:-:|------------|
| Fake testimonials destroy enterprise trust | L* | **C** | Remove TODAY |
| No design consistency across products | H | M | Design tokens + checklist enforced on all new work |
| Qualify UI not ready for public users | M | H | Audit before launch. Budget 1 week for fixes. |
| Jordan too busy for design review | H | M | AI drafts, Jordan approves. Limit review to 30 min/week. |
| Website looks "AI-generated" (generic) | M | M | Use real screenshots, real data, no stock art |
| Accessibility issues block enterprise deals | L | M | Basic audit in Week 4. Full WCAG later. |

---

## 9. Open Questions for Founders

| # | Question | Why It Matters |
|:-:|----------|---------------|
| 1 | Can I see the current enkai-qualify dashboard? | Need to audit before designing landing page |
| 2 | What's the enkai.ca tech stack? (Next.js? Tailwind?) | Determines how fast we can implement changes |
| 3 | Does Jordan have preferred design tools? (Figma? Direct code?) | Determines design workflow |
| 4 | Are there existing brand assets (logo files, color values)? | Need for design tokens |
| 5 | Do enterprise prospects use dark mode or light mode? | Determines default theme |
| 6 | Should clearbreak have its own visual identity or inherit Enkai's? | Determines brand architecture |
| 7 | How does Jordan want to review design work? (Async? Live?) | Sets the collaboration model |

---

## 10. What I Need From You

```
 1. Screenshots of the qualify dashboard
    -> I can't audit what I can't see

 2. Access to enkai.ca source code
    -> To assess implementation effort for redesign

 3. Logo files and any existing brand assets
    -> Foundation for design tokens

 4. Approve the design tokens above (colors, type, spacing)
    -> Everything else builds on this

 5. Confirm: Are you OK shipping a "proof of work" section
    instead of testimonials?
    -> This is the replacement strategy for the fake quotes
```

---

<sub>Report generated by VP Design Agent (Claude Opus 4.6) | Session: vpdesign-20260307</sub>
