\# A/B Test: PDP Redesign for Improved View-to-Cart Conversion



**Author**: Anushka Sharma

**Context**: Cosmetics E-Commerce Funnel Analysis

**Date**: 20 May 2026



\---



\## 🎯 The Business Problem



Based on my earlier funnel analysis of 4M+ user events from a cosmetics e-commerce store,

I found that the View → Cart conversion rate is \~5% — meaning 95% of users who view a

product never add it to cart. This drop-off is 3x larger than the Cart → Purchase drop-off.



The product team typically focuses on checkout optimization, but the data suggests the

real leak is on the Product Detail Page (PDP). Before making a major redesign decision,

I'd propose A/B testing a targeted PDP intervention to validate the assumption that

PDP improvements move the needle on conversion.







\## 💡 The Hypothesis



**Null Hypothesis (H₀):**

Adding a Customer Reviews widget and a "X people viewing this now" social proof element

to the PDP will have NO impact on the View → Cart conversion rate.



**Alternative Hypothesis (H₁):**

The new PDP design will increase View → Cart conversion rate by at least 5% (relative)

— from the current 5.0% baseline to 5.25% or higher.



\---



\## Metrics



\### Primary Metric

\- **View-to-Cart Conversion Rate** = (Users who add to cart) / (Users who view a product)



\### Secondary Metrics

\- **Cart-to-Purchase Conversion Rate-** checks for downstream impact (we don't want users

&#x20; adding to cart but never buying because reviews convinced them to compare elsewhere)

\- **Average Order Value (AOV)- did we attract bargain hunters or genuinely high-intent buyers?**

\- **Time on PDP**— engagement signal; reviews should increase dwell time



\### Guardrail Metrics (these should NOT degrade)

\- **Bounce Rate from PDP** — if our new widget slows the page, users may leave faster

\- **Page Load Time** — additional UI elements may add load latency (target: <200ms increase)

\- **Mobile vs Desktop CTR ratio** — the design should work on both viewports



\---



\## Sample Size \& Test Duration



\### Baseline Numbers (from my funnel analysis):

\- Current View → Cart conversion rate: \~5%

\- Minimum Detectable Effect (MDE): 5% relative improvement (i.e., move from 5% to 5.25%)

\- Significance level (α): 0.05

\- Statistical power: 80%



\### Sample Size Calculation:

Using a standard sample size formula for two-proportion z-test, we need approximately

**60,000 users per arm** (\~120,000 total) to detect a 5% relative lift with 80% power

at the 5% significance level.



\### Test Duration:

With \~40,000 daily PDP viewers in the dataset, and a 50/50 split between control and

treatment, we'd need approximately **3-4 days** to reach the sample size.



To account for day-of-week effects and noise, I'd run the test for a **full 14 days**.



\---



\## Randomization



\- **Unit of randomization**: User ID (NOT session)

\- **Why user-level?** Users see the same variant across visits — prevents the same

&#x20; user toggling between designs and biasing engagement metrics.

\- **Split**: 50/50 between Control (existing PDP) and Treatment (new PDP)

\- **Eligibility**: All users visiting any PDP during the test period



\---



\## Implementation



\- Control: Existing PDP (no changes)

\- Treatment: PDP with two additions —

&#x20; 1. Customer Reviews widget below product title (showing star rating + top 3 reviews)

&#x20; 2. "X people viewing this product right now" social proof below the price



\---



\## Decision Criteria



| Outcome | Action |

|---|---|

| Treatment beats Control by ≥5% relative, p < 0.05, guardrails OK | **Ship to 100%** |

| Treatment beats Control but <5%, p < 0.05 | **Discuss with team** — is it worth the engineering cost? |

| No significant difference (p ≥ 0.05) | **Roll back** — design didn't move the needle |

| Treatment underperforms or hurts guardrails | **Roll back immediately** |



\---



\## ⚠️ Pitfalls I'd Watch For



1\. **Peeking**: I will NOT check results before the planned 14-day window ends.

&#x20;  Peeking + early stopping inflates Type I error rates.



2\. **Novelty effect**: New designs sometimes get a temporary lift just because

&#x20;  they're new. The 14-day window gives time for this to settle.



3\. **Sample Ratio Mismatch (SRM)**: If the actual traffic split is not 50/50

&#x20;  (e.g., 60/40), there's a bug in randomization. I'd check this on Day 1.



4\. **Segment heterogeneity**: A win overall might hide a loss for one segment

&#x20;  (e.g., mobile users may lose if the widget slows the page). I'd segment by

&#x20;  device, traffic source, and new vs returning users.



5\. **Multiple testing**: If we look at 10 secondary metrics, by chance some will

&#x20;  show "significance." I'd apply Bonferroni correction for secondary metrics.



\---



\## 🎯 What I'd Recommend If This Won



If the test wins:

1\. **Ship to 100%** of users

2\. **Iterate** — test additional PDP elements (FAQs, related products, size guides)

3\. **Segment analysis** — was the lift larger for high-consideration categories?



If it loses:

1\. **Roll back**

2\. **Re-test** the hypothesis with different design execution

3\. **Investigate** — was the metric definition right? Were users actually seeing the widget?



\---



\## What I Learned



This exercise taught me:

\- A/B test design is more about clear hypothesis framing and metric selection than fancy statistics

\- The hardest part is choosing the right MDE — too small = expensive test, too large = miss real wins

\- Guardrails matter as much as the primary metric — winning the wrong way is still losing

\- Documenting decisions upfront prevents motivated reasoning when results come in

\- The test design itself reveals product knowledge: WHY this hypothesis, WHY this metric,

&#x20; WHY this MDE — these are the questions a Product Analyst should answer before touching code





\## Related Work



This A/B test design builds directly on my earlier funnel and cohort analysis:

\[ecommerce-funnel-analysis](https://github.com/anushkashh/ecommerce-funnel-analysis)

