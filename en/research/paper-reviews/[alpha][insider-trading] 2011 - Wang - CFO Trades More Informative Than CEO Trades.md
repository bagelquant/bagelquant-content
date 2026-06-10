---
read: true
layout: content
---

# Are CFOs’ Trades More Informative than CEOs’ Trades?

Authors:
- Weimin Wang — Saint Louis University
- Yong-Chul Shin — University of Massachusetts Boston
- Bill B. Francis — Rensselaer Polytechnic Institute

## Key findings

This paper studies whether trades by CFOs contain more information about future stock returns than trades by CEOs.

Main result:

CFO stock purchases are significantly more informative than CEO purchases.

Key numbers:

- After open-market purchases:
    - CEO 12-month abnormal return: +2.41%
    - CFO 12-month abnormal return: +7.41%
    - Difference: +5.00%

- Most excess return occurs:
    - Month 1–3: +2.58%
    - Month 4–6: +1.17%
    - Month 7–9: +1.02%

- Even after public disclosure:
    - CFO still earns +6.19%
    - CEO only +1.57%
    - Spread remains +4.62%

- CFO purchases predict stronger future earnings surprises:
    - CFO EA CAR: +0.430%
    - CEO EA CAR: +0.216%

Interpretation:

CFOs appear to possess and/or exploit more valuable information than CEOs when purchasing company stock.

## Detailed notes

### Research question

Traditional insider trading literature treats insiders as one homogeneous group.

This paper asks:

Do different executives possess different information advantages?

Focus specifically on:

- CEO
- CFO

Information quality is inferred through post-trade abnormal returns.

### Economic intuition

Two mechanisms:

1. Information advantage

CFO responsibilities:
- financial reporting
- budgeting
- financing
- capital allocation
- cost control

Therefore CFOs may observe:

- earnings quality
- operating conditions
- financial stress
- accounting adjustments

earlier and more precisely.

2. Incentive difference

Even if CEOs know the same information:

- CEOs face more scrutiny
- greater legal exposure
- higher compensation outside trading
- ownership guideline constraints

Therefore CEOs may trade less aggressively on private information.

### Data

Sample:
- Thomson Financial insider trading database
- Jan 1992 – Jul 2002
- Pre-SOX period

Final sample:

- CEO purchases: 12,936
- CFO purchases: 7,049
- CEO sales: 24,527
- CFO sales: 13,909

Filters:
- stock price > $2
- sufficient CRSP coverage
- combine same insider same-day transactions

### Methodology

Measure:

Post-trade cumulative abnormal return (CAR)

Benchmark:

- Fama–French size × book-to-market portfolios (10×10)

Important technical contribution:

The paper avoids standard equal-weight bias.

Uses:

Return-weighted adjustment
(Asparouhova et al., 2010)

Idea:

weight each return by:

$$
1+r_{t-1}
$$

to reduce microstructure bias.

Additional robustness:

Factor regressions:

- CAPM
- FF3
- FF4 (momentum)

### Core empirical results

#### Purchases dominate sales

Purchases:
- strong alpha

Sales:
- weak and mostly disappear after factor adjustment

Interpretation:

Selling is contaminated by:
- liquidity
- diversification
- compensation liquidation

Buying is more information driven.

#### CFO advantage strongest in small firms

12M abnormal return:

Size Q1:
- CFO − CEO = +5.83%

Size Q2:
- +6.06%

Size Q3:
- +5.48%

Large firms:
- no meaningful advantage

Interpretation:

Information asymmetry is larger in smaller firms.

#### Market does not immediately absorb insider information

Even after SEC disclosure:

CFO purchases continue generating alpha.

Filing-day reaction:

- CEO: +0.022%
- CFO: +0.232%

Small relative to long-run returns.

Implication:

Market underreacts to insider signals.

#### Earnings explain only part of the effect

Earnings announcement CAR:

- CFO purchase: +0.430%
- benchmark: +0.150%

But:

earnings explain only a small fraction of total +7% return.

Meaning:

CFOs likely trade using broader information:

- future cash flow
- financing events
- business conditions
- strategic developments

## Strengths

- Clean executive-level decomposition of insider information
- Strong economic magnitude
- Multiple robustness checks
- Links insider trading to future fundamentals

## Weaknesses / limitations

1. Pre-SOX sample only
    - disclosure rules changed materially after 2002

2. Observational
    - cannot separate information access from incentive differences

3. Long-horizon CAR methodology
    - sensitive to specification

4. Alpha implementation ignores:
    - transaction costs
    - replication delay
    - modern disclosure latency

## Suggestion on how to use the paper

Tag area:
[alpha]-[insider-trading]

This paper is highly actionable for alpha research.

Ideas:

### Insider hierarchy signal

Instead of:

$$
\text{Net Insider Buy}
$$

construct:

$$
\text{Weighted Insider Buy}
=
w_{CEO} \cdot CEO
+
w_{CFO} \cdot CFO
+
w_{Other} \cdot Other
$$

with:

$$
w_{CFO}>w_{CEO}
$$

### CFO purchase intensity

Features:

- purchase amount / market cap
- recent purchase count
- clustered purchases
- CFO − CEO net activity

### Combine with earnings revision

Since earnings only partially explains returns:

combine:

- insider purchase
- analyst revision
- earnings momentum
- accrual quality
- quality factors

### Event-driven implementation

Signal:

Recent CFO purchase

Holding:

3–9 months

Universe:

Small–mid cap

Controls:

- size
- momentum
- liquidity
- sector

Expected use:

medium-frequency equity alpha rather than HFT.

## My takeaway

This paper is one of the cleaner examples showing:

not all insiders are equal.

For equity alpha research, executive identity itself can be treated as an information layer rather than using aggregate insider activity.