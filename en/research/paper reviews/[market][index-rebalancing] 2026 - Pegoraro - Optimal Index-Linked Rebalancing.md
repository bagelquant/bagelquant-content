---
layout: content
title: Optimal Index-Linked Rebalancing with Anticipatory Trading
tags:
  - market
  - index-rebalancing
read: false
---

# Optimal Index-Linked Rebalancing with Anticipatory Trading

- DOI: 10.2139/ssrn.6772502
- Date: May 15, 2026
- Status: Working paper
- Suggested classification: `[market][index-rebalancing]`

## Author information

- Stefano Pegoraro
  - Mendoza College of Business, University of Notre Dame
  - Email: s.pegoraro@nd.edu
- Marco Sammon
  - Harvard Business School
  - Email: mcsammon@gmail.com
- John J. Shim
  - Mendoza College of Business, University of Notre Dame
  - Email: jshim2@nd.edu

## Key findings

The paper argues that anticipatory traders around index reconstitutions should not automatically be viewed as predatory front-runners. When they acquire inventory before implementation and sell it to index-tracking investors at the implementation-day closing auction, they provide intertemporal liquidity.

The relevant comparison is therefore not between index funds trading with and without anticipatory price movements. It is between:

- a market in which speculators prepare inventory in advance; and
- a market in which index funds must execute a large, inelastic order without such intermediation.

Under the paper's model, speculators reduce index investors' execution costs relative to the no-speculator counterfactual, even though speculators earn trading profits.

The main results are:

- Index trackers can rationally concentrate their entire rebalance at the implementation-date close, despite predictable pre-event price movements.
- Trading before or after implementation reduces the inventory that speculators are willing to supply at implementation. The fund's off-event trading therefore crowds out intermediary liquidity.
- Credible commitment to an implementation-date schedule makes concentrated execution optimal for a wider range of tracking-error preferences.
- As competition among speculators increases, their rents decline and implementation-date liquidity improves.
- With full commitment and sufficiently intense speculator competition, even investors with very weak tracking-error concerns optimally trade at implementation.
- Greater competition shifts price adjustment from the implementation date into the pre-event period. This explains why enormous implementation-day volume can coexist with little contemporaneous return.
- Post-implementation price reversal is proposed as the measure of the temporary and avoidable component of index-rebalancing cost.
- Fast-track additions shortly after an IPO are costly for index investors when the stock is illiquid and difficult to short, but beneficial to issuers and initial shareholders.
- Competitive intermediation creates a liquidity complementarity: loose benchmark trackers become more willing to trade alongside large passive orders when those orders attract sufficiently deep speculative liquidity.

The paper is more useful as a framework for understanding execution costs, auction liquidity, crowding and event conditioning than as a standalone recommendation to buy additions and short deletions.

## Research question

The paper starts from two apparently contradictory facts.

First, index trackers frequently trade extraordinary quantities at the closing auction on the exact implementation date. For S&P 500 additions and deletions, implementation-day volume can amount to roughly 20% or more of shares outstanding.

Second, implementation-day abnormal returns are now small. For S&P 500 direct additions during 2010–2024, the average implementation-day abnormal return is reported as approximately $-9$ basis points, despite volume of roughly 20–25 times normal daily volume.

This creates three questions:

- Why is implementation-day price impact so small?
- Why do flexible benchmark trackers trade at the same time as strict index funds?
- Do anticipatory traders impose costs on index investors, or do they provide valuable liquidity?

The paper answers these questions with a strategic execution model supported by event-study, holdings and securities-lending evidence.

References: Introduction; Section 3; Figure 1.

## Institutional setting

Strict index funds and ETFs aim to minimize tracking error and therefore prefer to transact at the official closing price used by the index.

Other investors also track benchmarks less explicitly:

- enhanced index funds;
- direct-indexing portfolios;
- benchmark-constrained active funds;
- institutional mandates;
- closet indexers.

These investors have more flexibility but still often participate in the implementation-day auction.

Index changes differ in predictability:

- S&P changes involve committee decisions and are normally announced before implementation.
- Russell membership is largely determined by transparent market-capitalization rankings.
- Fast-track IPO additions provide very little time for intermediaries to prepare inventory.

This variation in predictability, timing and short-sale feasibility is central to the paper's predictions.

References: Section 3.1.

## Data and sample construction

The empirical analysis separates index events into distinct groups:

- S&P 500 direct additions and deletions;
- migrations between the S&P 500 and the S&P 400 or S&P 600;
- Russell 1000 and Russell 2000 direct additions and deletions;
- migrations between the Russell 1000 and Russell 2000.

The main data sources include:

- index-provider constituent and reconstitution files;
- CRSP daily stock data;
- Datastream index returns;
- CRSP mutual-fund classifications and holdings;
- holdings-based shadow-indexing estimates;
- Markit short-interest, lendable-quantity and borrowing-fee data.

The baseline security-level event panel requires observations from 120 trading days before to 20 trading days after implementation. This excludes some recent listings, spinoffs and corporate-event cases without sufficient trading history.

The authors separately align announcement, rank and implementation dates to valid CRSP trading days. Non-trading event dates are moved to the next trading day.

Scaled volume is defined as:

$$
\text{Scaled Volume}_{i,t}
=
\frac{\text{Shares Traded}_{i,t}}
{\text{Shares Outstanding}_{i,t}}.
$$

Cumulative abnormal returns are calculated by compounding the stock and benchmark returns separately and subtracting afterward:

$$
CAR(\tau)
=
\prod_{s=0}^{\tau}(1+r^{stock}_s)
-
\prod_{s=0}^{\tau}(1+r^{benchmark}_s).
$$

Outcome variables are winsorized within event time and decade using one-sided winsorization at the 99th percentile.

References: Section 2.

## Motivating empirical facts

### Trading is concentrated at implementation

Figure 1 shows a dramatic implementation-day volume spike across S&P and Russell events.

For S&P events, approximately 18%–26% of shares outstanding may trade on implementation day. Russell migrations produce a smaller but still clearly abnormal spike.

The concentration cannot be explained solely by strict index funds. Existing evidence cited by the authors indicates that closing-auction activity is approximately twice the quantity expected from identified strict trackers.

References: Section 3.2, Fact 1; Figure 1.

### Implementation-day returns are small

Despite the quantity traded, modern implementation-day returns are modest:

- S&P 500 direct additions: approximately $-0.09\%$;
- S&P 500 migration additions: approximately $-0.24\%$;
- Russell 1000 to Russell 2000 migrations: approximately $0.10\%$;
- Russell 2000 to Russell 1000 migrations: approximately $0.11\%$.

Prices can move substantially before implementation. The important fact is that the date with the largest benchmark-linked quantity is no longer necessarily the date with the largest return.

The paper interprets this separation between price timing and quantity timing as evidence that intermediaries accumulate inventory before implementation and deliver it at the close.

References: Section 3.2, Fact 2; Figure 1.

## Model setup

The baseline model contains five periods:

- Period 0: index change is announced.
- Period 1: pre-implementation trading.
- Period 2: index implementation.
- Period 3: post-implementation trading.
- Period 4: terminal fundamental payoff.

The index fund must sell $Q$ shares of the outgoing constituent and purchase $Q$ shares of the incoming constituent. It may divide the order between periods 1, 2 and 3:

$$
x_1+x_2+x_3=Q.
$$

There are $L$ strategic speculators. Each speculator may build inventory before implementation, sell against the fund's demand at implementation, and close any remaining position afterward.

Transaction prices follow a linear permanent-and-temporary impact model:

$$
\hat P_{J,t}
=
\bar v
+
\lambda_J Z_{J,t-1}
+
\mu_J z_{J,t}
+
M_{J,t},
$$

where:

$$
\mu_J=\frac{\lambda_J}{2}+\eta_J.
$$

Here:

- $\lambda_J$ represents persistent price impact;
- $\eta_J$ represents temporary price impact;
- $z_{J,t}$ is current net order flow;
- $Z_{J,t-1}$ is cumulative prior order flow;
- $M_{J,t}$ is the fundamental martingale component.

The fund minimizes implementation shortfall plus tracking-error cost:

$$
C^F
=
IS^F+\kappa\nu(x_1+x_3).
$$

The tracking-error term penalizes trading outside period 2. The parameter $\kappa$ measures the importance of benchmark tracking, while $\nu$ scales the expected return difference between the incoming and outgoing securities.

Speculators maximize trading profit net of execution, financing, margin and inventory costs. They must close their positions by the terminal trading period.

References: Section 4.1.

## Commitment structures

The paper considers two equilibrium concepts.

### No commitment

The fund and speculators choose mutually optimal strategies. When selecting its schedule, the fund treats speculator positions as given.

The fund does not internalize how trading outside implementation causes speculators to reduce their implementation-date liquidity provision.

### Full commitment

The fund publicly commits to its complete execution schedule before speculators choose their positions.

The fund therefore anticipates how its schedule affects speculative inventory and internalizes the liquidity lost through off-implementation trading.

The authors argue that repeated index events, disclosure requirements and execution reputation can make this commitment credible even without a formal contract.

References: Sections 4.1 and 4.2.4.

## Main theoretical results

### Off-event fund trading crowds out speculative liquidity

When the fund trades before or after implementation, the potential profit available to speculators declines. Speculators respond by reducing both their pre-positioning and their post-event covering trades.

Consequently, implementation-date speculative liquidity is strictly decreasing in $x_1$ and $x_3$.

This is the model's central strategic mechanism. A fund that tries to avoid speculators by trading early also eliminates part of the liquidity that those speculators would otherwise have supplied at implementation.

Reference: Proposition 1.

### Speculators reduce the fund's cost

For a fund that executes completely at implementation, the model compares execution with and without speculators.

Under the maintained condition that temporary impact is sufficiently important, speculative inventory lowers the fund's implementation shortfall relative to trading alone.

The speculators still earn profits, but those profits are less than the execution-cost savings they create for the fund in the no-speculator counterfactual.

The paper therefore distinguishes public-information anticipatory trading from predatory trading against a distressed or forced liquidator.

Reference: Proposition 2; Figure 2.

### No-commitment equilibrium

There are three tracking-error regimes.

When $\kappa$ is high:

$$
x_1^*=x_3^*=0,\qquad x_2^*=Q.
$$

The fund executes entirely at implementation.

At intermediate tracking-error penalties, the fund trades at implementation and afterward, but not before:

$$
x_1^*=0,\qquad x_3^*>0.
$$

At low tracking-error penalties, the fund spreads execution across all periods:

$$
x_1^*>0,\qquad x_3^*>x_1^*.
$$

The schedule is back-loaded because a pre-implementation purchase permanently raises the price paid on the remaining implementation block, whereas a post-implementation purchase does not.

References: Proposition 3; Figures 3 and 7.

### Full-commitment equilibrium

The implementation-only threshold satisfies:

$$
0<\kappa^*_{FC}\leq\kappa^*_{NC}.
$$

Commitment makes concentrated execution optimal at a lower tracking-error penalty because the fund recognizes that off-event trading would destroy implementation-date liquidity.

Below the full-commitment threshold, the optimal schedule is symmetric:

$$
x_1^*=x_3^*>0.
$$

This differs from the back-loaded no-commitment schedule.

References: Proposition 4; Figure 4.

### Competitive limit

As the number of speculators increases:

$$
\kappa^*_{FC}(L)\rightarrow 0.
$$

Thus, with full commitment and sufficiently intense competition, implementation-date execution becomes optimal for any positive tracking-error concern.

Under no commitment, the threshold remains positive:

$$
\kappa^*_{NC}(\infty)
=
\frac{(\mu_N+\mu_O)Q}{\nu}>0.
$$

Competition eliminates speculative rents but cannot eliminate the fund's incentive to reduce temporary impact on its entire remaining implementation block.

References: Proposition 5; Figure 5.

### Price and volume measures of competition

The authors define the post-implementation reversal as:

$$
\Gamma(L)
=
\frac{
\mathbb E[\bar P_N-\hat P_{N,2}]
}{
\hat P_{N,0}Q
}.
$$

For an addition, $\Gamma(L)$ is negative because the implementation price is above the subsequent post-trading price.

As competition increases, $\Gamma(L)$ becomes less negative and approaches zero. A smaller absolute reversal therefore indicates more efficient intermediation.

The fraction of demand intermediated by speculators is:

$$
V(L)
=
\frac{S_1(L)+R(L)}{Q}.
$$

This quantity increases with the number of speculators, although it remains below one because temporary price-impact costs prevent complete intermediation.

References: Propositions 6 and 7.

## Generalized multi-period model

The model is extended to an arbitrary number of periods before and after implementation.

The main conclusions remain:

- sufficiently high tracking-error costs lead to complete implementation-date execution;
- commitment lowers the threshold for concentrated execution;
- no-commitment schedules are tilted toward post-event trading;
- full-commitment schedules are symmetric around implementation;
- the economically relevant deviations are usually the periods immediately adjacent to implementation.

Adding more distant trading periods has limited influence because tracking-error costs accumulate with distance while the marginal execution benefit from trading farther away declines.

References: Section 5.1; Figures 6–8.

## Fast-track IPO additions

Fast-track additions combine several adverse conditions:

- little time between listing and implementation;
- high temporary price impact;
- limited lendable supply;
- expensive or infeasible short selling.

When short selling is available, speculators can sell borrowed shares at implementation and cover afterward. The post-event period effectively extends the intermediation window.

When short selling is constrained, speculators must acquire most inventory before implementation. With a short pre-event window, this generates larger implementation prices and larger subsequent reversals.

The welfare effects differ across groups:

- index investors bear higher temporary execution costs;
- issuers and initial shareholders receive higher IPO or early-trading prices;
- competitive speculators transfer more of the index-inclusion value to issuers because they bid aggressively for inventory.

The model predicts that fast tracking is particularly costly when the stock is both illiquid and hard to short. A surprise addition of an established, liquid and borrowable company need not have the same cost.

References: Section 5.2; Figures 9–11.

## Liquidity complementarity

A weak tracker with low tracking-error concerns may initially prefer to trade away from a large passive block.

In a thin market, the passive implementation order creates a large price spike, so the weak tracker avoids the close.

In a deep market, the same predictable passive order attracts speculative capital. Intermediaries accumulate inventory in advance, reducing the incremental implementation-day price concession.

The weak tracker may then optimally join the passive block.

The implication is that strict and loose tracker orders can become complements rather than substitutes. A larger passive order can make implementation-date execution more attractive to other benchmarked investors when intermediation is competitive.

This mechanism provides an explanation for implementation-day volume exceeding the demand of identifiable index funds.

References: Section 5.3; Figures 12–14.

## Empirical evidence

### Benchmark-linked demand does not explain all implementation turnover

For S&P 500 direct additions, implementation-day turnover commonly exceeds 15%–20% of shares outstanding.

Estimated demand from strict index funds plus identified shadow indexers is generally below 10% of shares outstanding. The ratio of estimated index-plus-shadow demand to total implementation turnover is approximately $0.4$ in the later sample.

The authors interpret the unexplained volume as evidence that additional benchmarked investors coordinate at implementation.

This interpretation is plausible but not definitive: turnover measures both sides of a trade and may also include arbitrageurs, dealers, discretionary investors and closing-price-linked executions.

Reference: Section 6.1; Figure 15.

### Post-implementation reversals have declined

S&P 500 direct additions in the 1990s show a clear price run-up followed by reversal.

The reversal becomes smaller in the 2000s and is close to zero in the post-2010 sample, despite substantially larger index-linked demand.

The decline is stronger when reversal is divided by the estimated demand shock. The paper interprets this demand-normalized reversal as the empirical analogue of avoidable temporary impact per unit of index demand.

The result supports the view that the market has become more effective at intermediating predictable index orders.

References: Section 6.2; Figures 16 and 17.

### Short-interest dynamics support post-event intermediation

For S&P 500 direct additions:

- short interest rises near implementation;
- borrow fees increase;
- lendable supply increases after inclusion;
- short interest subsequently declines as positions are covered.

Russell migrations provide a signed test.

Stocks moving from the Russell 1000 to the Russell 2000 generally experience positive benchmark-linked demand. Their short interest rises around implementation.

Stocks moving from the Russell 2000 to the Russell 1000 generally experience negative demand. Their short interest falls around implementation.

The sign reversal makes it less likely that the result is a generic mechanical response to any reconstitution.

References: Section 6.3; Figures 18–20.

### Less predictable events require last-minute intermediation

The authors compare Russell migration candidates near the rank cutoff with more obvious “slam-dunk” switchers.

Close-call stocks that ultimately switch indexes have significantly more turnover between rank and implementation and more abnormal turnover afterward.

Implementation-day turnover is similar across switchers, consistent with benchmark demand being determined by the eventual index assignment rather than how early the assignment was known.

Close-call stocks that do not switch have much lower turnover throughout the event window because no benchmark demand shock materializes.

References: Section 6.4; Table 1.

### Estimated avoidable cost is small relative to trade size

The paper estimates avoidable cost as:

$$
\text{Avoidable Cost}_e
\approx
\text{Benchmark-Linked Dollars Traded}_e
\times
\text{Post-Event Reversal}_e.
$$

This is not total implementation shortfall. It measures the component associated with temporary price pressure that subsequently reverses.

Although index-linked demand has increased dramatically, the estimated avoidable cost has not increased proportionally. In the recent sample, it is approximately 1% of the benchmark-linked trade.

The authors emphasize that this is small relative to the quantity executed. S&P additions can involve benchmark demand exceeding 2,000%–2,500% of normal daily volume.

References: Section 6.5; Figure 21.

## Implications for index design

Predictability has both benefits and costs.

Greater transparency gives intermediaries time to:

- accumulate inventory;
- arrange stock borrowing;
- spread transactions across multiple dates;
- supply liquidity in the implementation auction.

A longer gap between announcement or ranking and implementation can therefore reduce temporary impact.

Predictability is less beneficial when:

- the preparation window remains too short;
- the incoming security is highly illiquid;
- short selling is constrained;
- uncertainty about inclusion persists until shortly before implementation.

The paper supports pre-announcement and sufficiently long implementation windows, but it does not imply that every predictable index rule is costless.

References: Section 6.6.

## Critical assessment

### Strengths

The paper explains several facts within one coherent framework:

- concentrated implementation-day volume;
- small contemporaneous returns;
- earlier price adjustment;
- declining post-event reversals;
- short selling at additions;
- synchronized trading by strict and loose trackers.

The distinction between total price pressure and avoidable temporary impact is particularly useful. Permanent price adjustment caused by a lasting demand shock should not automatically be classified as an execution failure.

The comparison with a no-speculator counterfactual also corrects the common assumption that every anticipatory price movement is evidence of harm to passive investors.

Using both S&P and Russell events gives the analysis variation in predictability, event design and the sign of benchmark demand.

The signed short-interest test for Russell migrations is a strong piece of supporting evidence because the predicted direction changes with the demand shock.

### Limitations

The paper does not directly identify the investors it calls speculators. Short interest and event-time volume are consistent with intermediation, but they do not reveal complete position histories or account-level profits.

The decline in reversals is interpreted as increasing speculator competition, but other developments may contribute:

- improvements in closing-auction design;
- greater electronic liquidity;
- lower commissions and spreads;
- changes in index announcement policies;
- improved stock-lending markets;
- broader changes in the liquidity of index constituents.

The paper does not structurally estimate the number of intermediaries, their inventory costs or the model's impact parameters. Competition is inferred through comparative patterns rather than directly measured.

Using post-event reversal as avoidable cost assumes that the reversal mainly reflects temporary price pressure. News, fundamental information and endogenous S&P selection may also affect post-event returns.

The full-commitment assumption is economically intuitive for strict index funds but is not literal in most settings. Funds generally do not announce their complete schedules to speculators. The effective commitment comes from mandates, repeated behavior and predictable aggregate demand.

The model assumes:

- linear price impact;
- identical Cournot speculators;
- a fixed and known demand quantity;
- martingale fundamentals;
- two securities traded in lockstep;
- a linear tracking-error penalty;
- no strategic behavior by index providers or corporate issuers.

Real portfolios rebalance many securities simultaneously and may face cross-impact, auction imbalance constraints, cash flows, futures overlays and risk-model limits.

The proofs are placed in an Internet Appendix that is not included in the uploaded PDF. This makes it difficult to audit the algebra and sufficient parameter conditions from the main document alone.

The estimated recent cost of roughly 1% is an event-level back-of-the-envelope estimate, not an annual drag for an index investor. It should not be interpreted as a general expense ratio or as the full cost of passive investing.

## Suggestion on how to use the paper

### Primary use

Use the paper as a framework for modeling index-reconstitution liquidity and execution costs rather than as a simple index-addition alpha signal.

The central research object should be the interaction:

$$
\text{Expected Demand}
\times
\text{Predictability}
\times
\text{Liquidity Constraints}
\times
\text{Intermediary Competition}.
$$

A large expected demand shock does not necessarily imply a large implementation-day return. When competition is strong, price adjustment may occur earlier and the closing auction may be extremely deep.

### Candidate features

For each index event, construct:

- expected index demand as a percentage of shares outstanding;
- expected demand divided by ADV;
- days from announcement or rank date to implementation;
- probability of inclusion or deletion;
- distance from the Russell rank cutoff;
- free float and index-eligible shares;
- historical spread, Amihud illiquidity and market impact;
- closing-auction volume and imbalance;
- borrow fee, lendable quantity and utilization;
- IPO age and lock-up status;
- direct addition versus index migration;
- estimated strict and shadow-index ownership;
- historical post-event reversal for similar events;
- demand-normalized reversal as a market-efficiency proxy.

### Alpha hypotheses

A post-implementation reversal strategy should be strongest when:

- the event is discovered late;
- the security is illiquid;
- expected benchmark demand is large;
- the stock is difficult to borrow;
- the pre-positioning window is short;
- closing-auction liquidity is weak;
- historical demand-normalized reversals indicate limited competition.

Pre-implementation drift should occur earlier for highly predictable events with competitive intermediation. Therefore, trading only after the formal announcement may be too late for transparent Russell events.

Fast-track IPO inclusions are a distinct event class. They should not be pooled mechanically with established-company additions because their liquidity, borrow availability and event horizon differ materially.

### Execution applications

For a portfolio that must follow an index, the paper suggests comparing:

- expected auction impact;
- tracking-error cost from early execution;
- the liquidity lost by deviating from the common implementation date.

A naïve execution model may recommend gradual pre-trading because it ignores the endogenous response of intermediaries. The paper implies that early trading can crowd out auction liquidity and may not reduce total cost as much as a static impact model predicts.

The implementation-date close may be optimal when:

- the benchmark uses the official close;
- aggregate index demand is highly predictable;
- the event attracts many intermediaries;
- borrow markets are deep;
- post-event reversals have historically been small.

### Backtest design

A realistic backtest should:

- use only announcement and rank information available at the time;
- distinguish announcement, rank and implementation dates;
- separate direct additions, direct deletions and migrations;
- hedge returns with the relevant source or destination index;
- exclude or flag mergers, delistings and unusual corporate events;
- model closing-auction fills rather than daily VWAP fills;
- include borrow availability and borrow fees;
- control for event overlap and common implementation dates;
- measure capacity relative to auction volume, not only normal ADV;
- test both raw and demand-normalized returns;
- examine pre-event, implementation and post-event windows separately.

### Portfolio interpretation

The paper argues against treating predictable passive demand as automatically exploitable alpha.

In competitive modern markets:

- implementation-day price impact may already be close to zero;
- the pre-event signal may be incorporated before a public announcement;
- most gross profit may compensate inventory, borrow and execution risk;
- alpha can disappear as intermediary participation increases.

The more durable application is likely a conditional execution-cost model or event-risk overlay that identifies where the intermediation mechanism is likely to fail.

## Bottom line

Anticipatory trading around index changes can look like front-running because speculators buy before index funds and sell to them at implementation.

The paper's key insight is that timing alone does not establish harm. Speculators also warehouse inventory and supply immediacy when benchmark investors value it most.

When the intermediation market is competitive, index investors can combine near-zero tracking error with surprisingly low temporary price impact. The largest opportunities and costs should therefore arise not from predictable index demand by itself, but from situations where predictability, liquidity provision or short-selling capacity breaks down.