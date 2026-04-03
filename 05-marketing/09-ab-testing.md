# A/B Testing Plan

## Overview

Systematic A/B testing ensures that every brand touchpoint is optimized for engagement and conversion. This plan covers headline variations, CTA copy, email subject lines, and landing page elements with clear hypotheses and success metrics.

---

## 1. Headline Variations Matrix

### Website Hero Headlines

| ID | Headline | Hypothesis | Pillar |
|----|----------|-----------|--------|
| H1-A | "Software Engineering, Crafted." | Brevity + craft positioning resonates with design-savvy audience | Technical Excellence |
| H1-B | "Code That Feels Right." | Emotional appeal differentiates from technical-only engineers | Design-Informed |
| H1-C | "I Build Digital Products That Last." | Direct, outcome-focused — speaks to business value | Trusted Partnership |
| H1-D | "Engineering with the precision of a craftsperson and the empathy of a designer." | Full value proposition in one line — tests long vs. short | All three pillars |
| H1-E | "Your Next Engineer Should Understand Design. I Do." | Confrontational/direct — tests bold positioning | Design-Informed |

### Test Plan
- **Method**: Split test on homepage, 50/50 traffic allocation
- **Metric**: Scroll depth (>50%), time on page, CTA click-through rate
- **Duration**: 2 weeks minimum or 500 visitors per variant
- **Statistical significance**: 95% confidence level

---

### Portfolio Section Headlines

| ID | Headline | Hypothesis |
|----|----------|-----------|
| P1-A | "Selected Work" | Clean, industry-standard — no friction |
| P1-B | "Built with Intention" | Differentiating — reinforces brand values |
| P1-C | "See What Craft Looks Like" | Bold, invites exploration |

---

### About Page Headlines

| ID | Headline | Hypothesis |
|----|----------|-----------|
| A1-A | "About" | Conventional — zero cognitive load |
| A1-B | "The Person Behind the Code" | Humanizing — builds connection |
| A1-C | "Engineering + Design. One Person." | Differentiating — reinforces unique positioning |

---

## 2. CTA Button Copy Variations

### Primary CTA (Contact/Hire)

| ID | Copy | Hypothesis |
|----|------|-----------|
| CTA1-A | "Let's Build Something Great" | Collaborative, aspirational — appeals to builders |
| CTA1-B | "Start a Conversation" | Low-pressure — reduces commitment anxiety |
| CTA1-C | "Get in Touch" | Simple, conventional — no interpretation needed |
| CTA1-D | "Hire Flavio" | Direct, transactional — appeals to decisive buyers |
| CTA1-E | "See If We're a Fit" | Mutual evaluation framing — appeals to partnership mindset |

### Secondary CTA (Portfolio)

| ID | Copy | Hypothesis |
|----|------|-----------|
| CTA2-A | "See the Work" | Direct, action-oriented |
| CTA2-B | "Explore Projects" | Invitational, exploratory |
| CTA2-C | "View Case Studies" | Professional, detailed — signals depth |

### Test Plan
- **Method**: Button click-through rate (CTR)
- **Metric**: Click rate, form submission rate (full funnel)
- **Duration**: 2 weeks or 200 clicks per variant minimum
- **Note**: Test CTA copy separately from headline — isolate variables

---

## 3. Email Subject Line Testing

### Welcome Email (First Touchpoint)

| ID | Subject Line | Preview Text | Hypothesis |
|----|-------------|--------------|-----------|
| E1-A | "Welcome — here's what to expect" | "A quick note about what's coming your way." | Conventional, sets expectations |
| E1-B | "Thanks for reaching out" | "I'll get back to you within 24 hours." | Personal, warm, immediate |
| E1-C | "Got your message — here's what happens next" | "A brief overview of my process." | Process-oriented, reduces uncertainty |

### Newsletter Subject Lines

| ID | Subject Line | Hypothesis |
|----|-------------|-----------|
| N1-A | "3 things I learned building [project type] this month" | Specificity + number = higher open rate |
| N1-B | "Monthly dispatch: [topic]" | Branded, consistent — builds habit |
| N1-C | "[Article title] — plus what I'm working on" | Content-forward — value proposition upfront |
| N1-D | "The one thing I'd do differently on [project]" | Vulnerability + learning = high engagement |

### Re-Engagement Subject Lines

| ID | Subject Line | Hypothesis |
|----|-------------|-----------|
| R1-A | "Still interested? Here's what's new." | Direct, no games |
| R1-B | "I've shipped some new work — take a look" | Content-driven re-engagement |
| R1-C | "It's been a while — want to stay subscribed?" | Honest, respects autonomy |

### Test Plan
- **Method**: A/B split within email platform
- **Metric**: Open rate (subject line), click rate (content), unsubscribe rate
- **Sample size**: Full list per variant (email lists are typically too small to segment)
- **Duration**: 48 hours for open rate results

---

## 4. Landing Page Element Tests

### Hero Section

| Element | Variant A | Variant B | Metric |
|---------|-----------|-----------|--------|
| **Hero layout** | Text left, image right | Centered text, no image | Scroll depth, CTA clicks |
| **Social proof placement** | Below hero | Within hero section | Trust indicators: time-on-page, CTA clicks |
| **CTA count** | Single CTA | Dual CTA (primary + secondary) | Click distribution, overall CTR |

### Portfolio Section

| Element | Variant A | Variant B | Metric |
|---------|-----------|-----------|--------|
| **Project display** | Grid (3 columns) | Single featured + list | Project page visits |
| **Project cards** | Image + title + tags | Image + title + description | Click-through to project |
| **Number of projects** | 3 featured | 6 in grid | Engagement depth, scroll |

### Trust Elements

| Element | Variant A | Variant B | Metric |
|---------|-----------|-----------|--------|
| **Testimonials** | Static quotes | Carousel | Read-through, time on section |
| **Client logos** | Logo bar | No logos | CTA conversion rate |
| **GitHub stats** | Show contribution graph | Don't show | Inquiry quality |

### Contact Section

| Element | Variant A | Variant B | Metric |
|---------|-----------|-----------|--------|
| **Form fields** | Name, email, message | Name, email, project type, budget, message | Completion rate, inquiry quality |
| **Form layout** | Single column | Two column | Completion rate |
| **Submit button** | "Send Message" | "Let's Talk" | Click rate |

---

## 5. Testing Methodology

### Statistical Requirements

| Requirement | Standard |
|-------------|----------|
| Confidence level | 95% (p < 0.05) |
| Minimum sample per variant | 200 conversions (for conversion tests) or 500 visitors (for engagement tests) |
| Test duration | Minimum 2 full weeks (capture weekday/weekend variance) |
| Maximum concurrent tests | 2 (to avoid interaction effects) |

### Testing Priority Framework

Prioritize tests using ICE scoring:

| Test | Impact (1-10) | Confidence (1-10) | Ease (1-10) | Score |
|------|--------------|-------------------|-------------|-------|
| Hero headline | 9 | 7 | 9 | 25 |
| Primary CTA copy | 8 | 8 | 10 | 26 |
| Contact form fields | 7 | 6 | 8 | 21 |
| Email subject lines | 6 | 8 | 10 | 24 |
| Portfolio layout | 7 | 5 | 7 | 19 |
| Hero layout | 8 | 5 | 5 | 18 |

**Recommended test order:**
1. Primary CTA copy (highest score, easiest to implement)
2. Hero headline (highest impact)
3. Email subject lines (high ease, independent of website)
4. Contact form fields
5. Portfolio layout
6. Hero layout

### Testing Rules

1. **Isolate variables**: Only test one element at a time per page section
2. **Don't peek**: Don't check results before the planned end date
3. **Document everything**: Record the hypothesis, variant details, results, and learnings
4. **Winner takes all**: Implement the winning variant before starting the next test
5. **Negative results are results**: A test that shows no difference is still valuable data
6. **Re-test annually**: User behavior shifts — last year's winner may not hold

---

## 6. Results Documentation Template

For each completed test:

```markdown
## Test: [Test Name]
**Date**: [Start] – [End]
**Element**: [What was tested]
**Page**: [URL]

### Hypothesis
[What we expected and why]

### Variants
- **Control (A)**: [Description]
- **Variant (B)**: [Description]

### Results
| Metric | Control | Variant | Difference | Significance |
|--------|---------|---------|------------|-------------|
| [Metric] | [Value] | [Value] | [+/- %] | [p-value] |

### Winner
[A or B]

### Learnings
[What we learned and how it informs future tests]

### Action
[What changed as a result]
```

---

## 7. Tools

| Tool | Purpose | Cost |
|------|---------|------|
| Google Optimize (sunset → use alternatives) | Website A/B testing | Free tier available |
| Posthog | Feature flags + A/B testing | Free up to 1M events |
| Vercel Edge Config | A/B testing at the edge | Included with Vercel |
| Mailchimp / ConvertKit | Email A/B testing | Free tier available |
| Google Analytics 4 | Results measurement | Free |
| Hotjar / Microsoft Clarity | Heatmaps, session recordings | Free tier available |
