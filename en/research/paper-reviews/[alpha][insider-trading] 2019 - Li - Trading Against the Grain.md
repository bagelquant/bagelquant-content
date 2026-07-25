---
read: true
layout: content
---

# Trading Against the Grain: When Insiders Buy High and Sell Low

- DOI: 10.3905/jpm.2019.46.1.139
- SSRN DOI: 10.2139/ssrn.3446396
- Publication: The Journal of Portfolio Management, 2019, Volume 46, Issue 1, pp. 139–151
- Tags: [alpha][insider-trading]
- Sample period: 1986–2017
- Market: United States
- Data: Thomson Reuters Insider Filing Data Feed and CRSP
- JEL classification: G11, G14, G15

- Authors:
  - Ruihai Li — School of Business Administration, Shanghai Lixin University of Commerce and Finance
  - Xuewu (Wesley) Wang — Department of Finance, Quinnipiac University
  - Zhipeng Yan — Martin Tuchman School of Management, New Jersey Institute of Technology in the uploaded version
  - Qunzi Zhang — School of Economics, Shandong University

Page references below use PDF page numbers. The printed page number in the paper is generally one page lower because the title page is unnumbered.

## Key findings

- Corporate insiders exhibit behavior consistent with anchoring:
  - They buy disproportionately more when the stock price is close to its 52-week low.
  - They sell disproportionately more when the stock price is close to its 52-week high.
  - This behavior remains after controlling for the well-known contrarian tendency of insiders to buy past losers and sell past winners.

- Trades made against the natural anchor are substantially more informative:
  - A high buy is an insider purchase when the stock price is far above its 52-week low.
  - A low sell is an insider sale when the stock price is far below its 52-week high.
  - The authors interpret these trades as cases in which private information is sufficiently strong to overcome the insider’s anchoring bias.

- Using decile sorts, high buys outperform low buys by:
  - 4.07% over the following 30 days using size-adjusted returns.
  - 4.59% using market-adjusted returns.
  - 3.31% using DGTW size, value, and momentum characteristic-adjusted returns.
  - See Table 8, PDF pp. 50–51.

- Low sells underperform high sells by:
  - 1.36% over the following 30 days using size-adjusted returns.
  - 1.03% using market-adjusted returns.
  - 1.20% using DGTW-adjusted returns.
  - See Table 8, PDF pp. 50–51.

- The purchase-side result is economically much stronger than the sale-side result. This is consistent with the broader insider-trading literature: purchases usually represent a more deliberate information signal, while sales can be motivated by diversification, liquidity, taxation, compensation, or scheduled disposal.

- The return differences are persistent rather than quickly reversing:
  - The high-sell minus low-sell gap widens for roughly five months and then stabilizes.
  - The high-buy minus low-buy gap continues to widen through the 12-month horizon.
  - See Figures 1 and 2, PDF pp. 56–57.

- The strongest calendar-time strategy combines the anchor signal with price momentum:
  - Long high-buy stocks that also have strong past returns.
  - Short low-sell stocks that also have weak past returns.
  - The value-weighted long-high-buy/short-low-sell portfolio earns a five-factor alpha of 2.16% per month before transaction costs.
  - Its DGTW characteristic-adjusted return is 2.75% per month with a t-statistic of 3.48.
  - The corresponding equal-weighted five-factor alpha is 3.80% per month.
  - See Table 10, PDF p. 53.

- The evidence is stronger for informationally advantaged or less routine trades:
  - High-buy effects are stronger for top executives and officers/directors than for large shareholders.
  - Opportunistic insiders produce larger high-buy versus low-buy and low-sell versus high-sell return differences than routine insiders.
  - Nevertheless, even high purchases by routine insiders remain informative.

## Detail notes

### Research question

The paper asks two related questions:

- Are corporate insiders affected by behavioral anchoring when trading their own company’s stock?
- Can the interaction between anchoring and private information identify which insider trades contain the most information?

The central insight is not simply that insider purchases predict positive returns or that insider sales predict negative returns. Instead, the authors condition the interpretation of an insider trade on where the stock price is relative to a psychologically salient reference point.

For purchases, the relevant anchor is the 52-week low. For sales, it is the 52-week high.

An insider who buys near the 52-week low may be buying because:

- the stock appears inexpensive relative to its recent range;
- the insider has positive private information;
- the insider is following a contrarian investment style;
- or some combination of these motives.

The trade direction alone therefore contains an ambiguous signal.

In contrast, an insider who buys when the price is already far above its 52-week low is trading against the natural “buy low” anchor. The paper argues that positive private information is the most plausible reason for overcoming that reluctance.

The same reasoning applies symmetrically to insider sales. Selling far below the 52-week high goes against the tendency to wait for a more attractive selling price and may reveal unusually negative information.

### Behavioral and informational framework

The paper divides insider trades into four cases.

| Trade | Price relative to anchor | Paper terminology | Interpretation |
|---|---|---|---|
| Purchase | Close to 52-week low | Low buy | Could reflect anchoring, contrarian behavior, or positive information |
| Purchase | Far above 52-week low | High buy | More likely to reflect strong positive information |
| Sale | Far below 52-week high | Low sell | More likely to reflect strong negative information |
| Sale | Close to 52-week high | High sell | Could reflect anchoring, contrarian behavior, liquidity, or negative information |

The important comparison is therefore not simply buys against sells. It is:

$$
R_{\text{High Buy}}-R_{\text{Low Buy}}>0
$$

and

$$
R_{\text{Low Sell}}-R_{\text{High Sell}}<0.
$$

High buys and low sells are the “against-the-grain” trades.

### Data construction

The sample covers U.S. insider transactions from 1986 through 2017.

Insider transactions come from the Thomson Reuters Insider Filing Data Feed. Stock prices, returns, trading volume, and firm characteristics come primarily from CRSP.

The insider universe consists of people subject to Section 16 reporting requirements:

- corporate officers;
- directors;
- and shareholders owning more than 10% of the company.

Only open-market equity transactions are retained.

The authors apply several filters:

- The transaction must match a CRSP security through CUSIP.
- The reported transaction price must fall within the CRSP daily high-low range.
- The transaction price must be at least $1.
- The transaction must contain at least 100 shares.
- Exact duplicate records are removed.
- Multiple transactions by the same insider on the same day are aggregated, with a volume-weighted transaction price.

See Section 3, PDF pp. 10–12.

The final sample contains:

- 293,988 insider purchases;
- 862,949 insider sales;
- approximately 6.57 billion shares purchased;
- approximately 25.63 billion shares sold;
- about $99.0 billion of purchases;
- about $880.9 billion of sales.

The large imbalance between purchases and sales reflects the fact that insiders often acquire shares through compensation, grants, founding ownership, or option exercise and later dispose of those shares.

See Table 1, PDF p. 43.

### Measuring distance from the anchor

For the initial combined buy-versus-sell analysis, the paper defines nearness to the 52-week high as:

$$
Near52_{i,t}
=
\frac{\overline{P}_{i,t-30:t-1}}
{High52_{i,t}},
$$

where $\overline{P}_{i,t-30:t-1}$ is the average closing price during the 30 days before the insider transaction.

A higher value means that the stock is closer to its 52-week high.

For the return analysis, the anchor depends on trade direction.

For purchases:

$$
BuyAnchorRatio_{i,t}
=
\frac{\overline{P}_{i,t-30:t-1}}
{Low52_{i,t}}.
$$

A high ratio indicates a high buy: the stock is far above its 52-week low.

For sales:

$$
SellAnchorRatio_{i,t}
=
\frac{\overline{P}_{i,t-30:t-1}}
{High52_{i,t}}.
$$

A low ratio indicates a low sell: the stock is far below its 52-week high.

The paper also uses the position of the transaction price within the previous 52-week high-low range:

$$
RangePosition_{i,t}
=
\frac{P_{i,t}-Low52_{i,t}}
{High52_{i,t}-Low52_{i,t}}.
$$

Although this normalized expression is not written directly in this form, it corresponds to the five equal price intervals used in Tables 5–7.

### Evidence of anchoring

Table 2 sorts all insider trades by proximity to the 52-week high.

Measured by number of trades, purchases represent:

- 43.04% of insider trades in the quintile farthest below the 52-week high;
- 31.30% in Quintile 2;
- 21.88% in Quintile 3;
- 15.96% in Quintile 4;
- 14.88% in the quintile closest to the 52-week high.

The almost monotonic decline is also present when activity is measured by shares or dollar volume.

See Table 2, PDF p. 44.

Table 5 examines purchases and sales separately by dividing the prior 52-week price range into five intervals.

For insider purchases:

- 39.29% occur in the interval closest to the 52-week low.
- Only 13.13% occur in the interval closest to the 52-week high.
- The bottom two intervals contain 58.62% of all purchase transactions.

For insider sales:

- 40.56% occur in the interval closest to the 52-week high.
- Only 11.08% occur in the interval closest to the 52-week low.
- The top two intervals contain 61.53% of all sale transactions.

See Table 5, PDF p. 47.

These distributions are consistent with insiders anchoring purchases to the recent low and sales to the recent high.

### Distinguishing anchoring from contrarian trading

A major identification concern is that insiders are known contrarian investors. They tend to buy stocks with poor past returns and sell stocks with strong past returns.

Since stocks close to their 52-week highs often have positive momentum, the apparent anchor effect could simply be momentum or contrarian behavior.

The authors address this with independent double sorts on:

- proximity to the 52-week high;
- and the stock’s cumulative return over the previous 12 months, excluding the most recent month.

The momentum measure is approximately the conventional 12–2 return:

$$
Momentum_{i,t}
=
\prod_{\tau=t-13m}^{t-2m}(1+r_{i,\tau})-1.
$$

Table 3 shows both effects:

- Holding anchor proximity constant, insiders buy less as past returns increase, confirming contrarian behavior.
- Holding past returns constant, insider purchases generally decline as the price approaches the 52-week high, supporting an additional anchor effect.

See Table 3, PDF p. 45.

The paper then estimates a logistic regression in which the dependent variable equals one for an insider purchase and zero for an insider sale.

Controls include:

- proximity to the 52-week high;
- top-executive status;
- officer/director status;
- interactions between role and anchor proximity;
- past 12–2 returns;
- shares traded relative to daily trading volume.

The coefficient on $Near52$ is negative and highly significant. The interaction coefficients for top executives and officers/directors are also strongly negative.

See Table 4, PDF p. 46.

This implies that insiders become less likely to buy as the price approaches the 52-week high, even after controlling for momentum and trade characteristics.

### Trades that overcome both anchoring and contrarian behavior

Tables 6 and 7 contain an especially useful result for alpha research.

Among stocks with the worst past returns, insiders sometimes sell when the stock is already near the bottom of its 52-week range. These low sells contradict both:

- the anchoring tendency to wait for a higher sale price;
- and the contrarian tendency to buy or retain recent losers.

Similarly, among stocks with the strongest past returns, insiders sometimes buy near the top of the 52-week range. These high buys contradict both:

- the anchoring tendency to avoid buying at a high price;
- and the contrarian tendency to sell or avoid recent winners.

In the strongest past-return quintile, the percentage of insider purchase transactions rises from 11.04% in the lowest price interval to 31.93% in the highest price interval.

See Table 7, PDF pp. 49–50.

In the weakest past-return quintile, 31.43% of insider sale transactions occur in the lowest price interval, compared with only 8.84% in the highest interval.

See Table 6, PDF p. 48.

These two corners motivate the combined anchor-and-momentum portfolio strategy.

### Event-time return tests

The main event study calculates abnormal returns over the 30 days after each transaction:

$$
CAAR_{i,[t+1,t+30]}
=
\sum_{\tau=t+1}^{t+30}
AR_{i,\tau}.
$$

Three abnormal-return definitions are used:

- CAAR1: stock return minus the return of a corresponding size portfolio;
- CAAR2: stock return minus the market return;
- CAAR3: stock return minus a DGTW portfolio matched on size, book-to-market, and momentum.

For sales using decile sorts:

| Group | CAAR1 | CAAR2 | CAAR3 |
|---|---:|---:|---:|
| Low sell | -1.20% | -0.73% | -1.19% |
| High sell | 0.16% | 0.30% | 0.02% |
| High sell minus low sell | 1.36% | 1.03% | 1.20% |

For purchases using decile sorts:

| Group | CAAR1 | CAAR2 | CAAR3 |
|---|---:|---:|---:|
| Low buy | 0.93% | 0.96% | 0.86% |
| High buy | 5.00% | 5.55% | 4.17% |
| High buy minus low buy | 4.07% | 4.59% | 3.31% |

See Table 8, PDF pp. 50–51.

The results show that ordinary insider purchases are still somewhat positive. The main economic gain comes from identifying the subset of purchases made far away from the buying anchor.

For sales, high sells are approximately neutral or slightly positive. The economically useful negative signal is concentrated in low sells.

### Regression return tests

Table 9 retains only the extreme high and low trade groups and regresses the subsequent 30-day abnormal return on a high-trade indicator and firm characteristics.

Controls include:

- firm size;
- book-to-market;
- previous-year return;
- previous-month return;
- calendar-month fixed effects;
- firm-clustered standard errors.

For purchases, the high-buy coefficient ranges from approximately 3.1% to 4.4%, depending on the abnormal-return model.

For sales, the high-sell coefficient is positive, generally around 0.7% to 1.0%. Because low sells form the omitted category, the positive coefficient means that low sells have lower subsequent returns.

See Table 9, PDF p. 52.

The result is therefore not explained by conventional size, value, short-term reversal, or medium-term momentum exposures.

### Persistence of the return signal

Figure 1 plots cumulative DGTW-adjusted returns for high sells and low sells over 12 months.

Low sells experience strongly negative returns during the first several months. The difference relative to high sells reaches roughly 3%–4% after around five months and does not subsequently reverse.

See Figure 1, PDF p. 56.

Figure 2 shows a larger purchase-side effect.

High buys accumulate strongly positive abnormal returns over the full year, while low buys remain approximately flat and eventually become slightly negative. The high-buy minus low-buy spread reaches approximately:

- 10%–11% using quintile sorting;
- 13%–14% using decile sorting.

See Figure 2, PDF p. 57.

The persistence is consistent with slowly incorporated information. However, persistence alone does not establish that the source is private information; it could also reflect exposure to an omitted persistent characteristic.

### Calendar-time portfolio construction

For every month, insider purchases and sales are independently sorted into deciles based on:

- distance from the relevant anchor;
- and 12–2 momentum.

The paper requires at least 200 insider trades in a month and begins the portfolio sample in December 1995.

The four relevant portfolios are:

- High buy: purchases far above the 52-week low and in high-momentum stocks.
- Low buy: purchases near the 52-week low and in low-momentum stocks.
- High sell: sales near the 52-week high and in high-momentum stocks.
- Low sell: sales far below the 52-week high and in low-momentum stocks.

Stocks are held during the following month, and portfolios are rebalanced monthly.

The principal hedge portfolio is:

$$
R^{HB-LS}_{t+1}
=
R^{HighBuy}_{t+1}
-
R^{LowSell}_{t+1}.
$$

For the value-weighted version:

- Average raw return: 2.71% per month.
- CAPM alpha: 2.04%.
- Fama–French three-factor alpha: 1.98%.
- Carhart four-factor alpha: 2.09%.
- Five-factor alpha including liquidity: 2.16%.
- DGTW-adjusted return: 2.75%.

For the equal-weighted version:

- Average raw return: 3.39% per month.
- Five-factor alpha: 3.80%.
- DGTW-adjusted return: 3.39%.

See Table 10, PDF p. 53.

The much larger equal-weighted results raise the possibility that the signal is particularly strong among smaller or less liquid firms. The persistence of value-weighted results is nevertheless important because it shows that the findings are not entirely driven by microcapitalization stocks.

### Insider information hierarchy

The authors divide insiders into:

- top executives;
- officers and directors;
- large shareholders.

For purchases, the DGTW-adjusted high-buy minus low-buy differences are:

- Top executives: 4.20%.
- Officers and directors: 4.23%.
- Large shareholders: 1.62%.

The smaller purchase effect for large shareholders is consistent with their weaker access to operating information.

For sales, the DGTW-adjusted high-sell minus low-sell differences are:

- Top executives: 1.52%.
- Officers and directors: 0.86%.
- Large shareholders: 2.86%.

The unexpectedly large sale difference for large shareholders is partly generated by positive returns after their high sells rather than exclusively by especially negative information in low sells.

See Table 11, PDF p. 54.

The information-hierarchy result is therefore clearer and more intuitive on the purchase side.

### Routine versus opportunistic insiders

Following Cohen, Malloy, and Pomorski, an insider is classified as routine when the insider trades during the same calendar month for at least three consecutive years. Other insiders in the eligible universe are classified as opportunistic.

For DGTW-adjusted returns:

- Routine high-buy minus low-buy spread: 4.33%.
- Opportunistic high-buy minus low-buy spread: 5.12%.
- Routine high-sell minus low-sell spread: 0.68%.
- Opportunistic high-sell minus low-sell spread: 1.17%.

See Table 12, PDF p. 55.

The opportunistic group produces stronger results, particularly for sales. However, high buys by routine insiders remain highly informative.

This suggests that anchor distance can recover useful information even within a group whose unconditional trades are often considered relatively uninformative.

### Interpretation

The paper’s proposed mechanism is:

$$
ObservedTrade
=
BehavioralBias
+
PrivateInformation
+
LiquidityAndOtherMotives.
$$

When the trade agrees with the behavioral bias, it is difficult to separate these components.

When the trade contradicts the bias, the behavioral component works against the observed action. The authors infer that the information component must therefore be sufficiently strong to dominate it.

This is an economically intuitive identification strategy, but it is not a formal causal identification of private information.

A more conservative interpretation is:

> Conditional on insider trade direction, distance from the appropriate 52-week anchor identifies trades with substantially stronger return predictability.

That empirical statement is well supported. The stronger statement that private information is definitively the cause remains an interpretation.

### Strengths

- The paper offers an intuitive conditioning variable that substantially improves a familiar insider-trading signal.
- It separates purchase and sale anchors rather than applying the 52-week high symmetrically to both trade directions.
- It controls explicitly for insider contrarian behavior.
- The main results are robust across:
  - quintile and decile sorts;
  - several abnormal-return benchmarks;
  - event-time and calendar-time analysis;
  - regression controls;
  - different insider roles;
  - routine and opportunistic classifications;
  - multiple holding horizons.
- Calendar-time results show that the finding can be translated into a portfolio rather than existing only as an event-study anomaly.
- Both equal- and value-weighted results are positive.
- The strategy uses observable information: transaction direction, transaction or filing date, historical prices, insider role, and past returns.

### Limitations and concerns

#### Private-information interpretation is not directly identified

Trading against an anchor may indicate unusually strong information, but other motives could also produce high buys or low sells.

Potential omitted motives include:

- portfolio rebalancing;
- tax planning;
- divorce or estate transactions;
- personal liquidity needs;
- changes in insider ownership requirements;
- stock-based compensation;
- option exercise and subsequent transactions;
- Rule 10b5-1 plans;
- signaling motives;
- participation in corporate financing;
- firm distress or pending corporate events.

The filters remove many non-open-market transactions, but open-market trades can still have non-information motives.

#### Transaction date versus public availability date

The event study is indexed to the insider transaction date. Outside investors generally learn about the trade only when the Form 4 is filed.

After the Sarbanes–Oxley Act, most trades must be reported within two business days. Before 2002, the reporting delay could be much longer.

The calendar-time strategy forms portfolios in the following month, and the paper reports a robustness test using an additional one-month delay. Nevertheless, a production replication should use the SEC filing acceptance timestamp rather than the transaction date.

Using transaction dates directly could introduce look-ahead bias.

#### Transaction costs are omitted

The reported portfolio alphas are before:

- bid-ask spreads;
- commissions;
- market impact;
- short-borrow fees;
- availability constraints;
- delay between filing and execution.

The low-sell short portfolio may contain distressed, small, volatile, or expensive-to-borrow stocks. Therefore, the 2%–4% monthly gross alpha should not be interpreted as a realistic net return.

#### Potential microcap and liquidity exposure

Equal-weighted results are considerably larger than value-weighted results.

Although the value-weighted strategy remains significant, the difference suggests that part of the strongest signal may reside in smaller securities. A modern replication should impose explicit:

- market-capacity screens;
- minimum ADV;
- maximum participation rates;
- bid-ask-spread constraints;
- borrow-availability screens.

#### Anchor measures are not fully consistent across tests

Different sections use:

- average price divided by the 52-week high;
- average price divided by the 52-week low;
- and equal intervals within the 52-week high-low range.

These measures capture related but not identical concepts.

The ratio to the 52-week low can become extreme when the historical low is unusually small. The measure may therefore load on:

- volatility;
- recent drawdown recovery;
- low-price outliers;
- jumps;
- corporate actions;
- or data-adjustment errors.

A normalized range-position measure or log-distance measure may be more stable.

#### Mechanical overlap with momentum and the 52-week-high factor

The signal is intentionally combined with momentum in the portfolio test.

A high buy tends to occur in a stock that has risen far from its past low. A low sell tends to occur in a stock that has fallen far from its past high. These classifications can be correlated with:

- 12–2 momentum;
- short-term reversal;
- distance from the 52-week high;
- drawdown;
- residual momentum;
- volatility;
- trend strength.

The paper double-sorts on momentum and uses DGTW adjustment, but a production alpha should explicitly measure incremental predictive power after neutralizing these related signals.

#### Sample ends in 2017

The institutional environment for insider trading has evolved since the sample ended, including changes in:

- electronic filing;
- information-processing speed;
- quantitative use of Form 4 data;
- Rule 10b5-1 disclosure and cooling-off requirements;
- market liquidity and shorting conditions.

The result should be re-estimated on a post-publication sample.

#### Multiple trades and overlapping returns

A firm may have multiple insiders trading close together. Event-time observations can therefore overlap and may not be independent.

Firm-clustered standard errors help, but a portfolio implementation should aggregate trades at an issuer-date or issuer-filing-event level to avoid mechanically treating a cluster of related trades as independent signals.

#### Economic magnitudes are unusually large

Monthly alphas of approximately 2%–4% are extremely large for a public-information equity strategy.

Possible explanations include:

- genuine information diffusion;
- concentration in small and illiquid stocks;
- stale filing assumptions;
- overlapping signals;
- short-sale frictions;
- extreme double-sort portfolios;
- data-mining or sample-specific effects.

Independent replication is essential before assigning a large allocation.

## Suggestion on how to use the paper

### Core alpha interpretation

The paper is most useful as a conditioning framework for an existing insider-trading alpha.

Do not treat every insider purchase as equally bullish or every insider sale as equally bearish.

Instead:

- Increase the bullish score when an insider purchases after the stock has moved far above its 52-week low.
- Increase the bearish score when an insider sells after the stock has moved far below its 52-week high.
- Reduce the importance of low buys and high sells because their motivations are more ambiguous.

The basic signed signal can be represented as:

$$
Signal_{i,t}
=
BuyIntensity_{i,t}\times BuyAgainstAnchor_{i,t}
-
SellIntensity_{i,t}\times SellAgainstAnchor_{i,t}.
$$

A stable feature definition would be:

$$
BuyAgainstAnchor_{i,t}
=
\log\left(
\frac{\overline{P}_{i,t-20:t-1}}
{Low252_{i,t}}
\right)
$$

for purchases, and

$$
SellAgainstAnchor_{i,t}
=
\log\left(
\frac{High252_{i,t}}
{\overline{P}_{i,t-20:t-1}}
\right)
$$

for sales.

Both features become larger as the insider trades further against the relevant anchor.

Alternatively, use normalized range position:

$$
RangePosition_{i,t}
=
\frac{\overline{P}_{i,t-20:t-1}-Low252_{i,t}}
{High252_{i,t}-Low252_{i,t}}.
$$

Then:

- high values are more informative for purchases;
- low values are more informative for sales.

The normalized version is likely to be more robust across stocks with different prices and volatilities.

### Recommended event construction

Build the signal using the public filing event rather than the transaction event.

For each Form 4 filing:

- Record the SEC acceptance timestamp.
- Extract all underlying transactions.
- Keep genuine open-market purchases and sales.
- Aggregate transactions to insider-stock-filing-date.
- Aggregate multiple insiders to stock-filing-date after preserving insider-role features.
- Adjust all historical prices for splits and other corporate actions.
- Begin the tradable return window after the filing becomes public.

Useful event-level fields include:

- issuer;
- filing timestamp;
- transaction date;
- reporting delay;
- insider identity;
- insider role;
- purchase or sale;
- number of shares;
- transaction value;
- change in beneficial ownership;
- trade value divided by ADV;
- trade value divided by the insider’s existing holdings;
- 10b5-1 plan indicator;
- direct versus indirect ownership;
- number of insiders trading in the same direction;
- anchor distance;
- 12–2 momentum;
- one-month return;
- volatility;
- market capitalization;
- industry.

### Purchase-side signal

The paper indicates that purchases should be the primary implementation target.

A candidate purchase score is:

$$
BuyScore_{i,t}
=
Rank(BuyDollarIntensity)
\times
Rank(BuyAgainstAnchor)
\times
Rank(Momentum_{12-2})
\times
RoleWeight.
$$

Possible role weights:

- larger weight for CEO, CFO, and other top executives;
- medium weight for officers and directors;
- smaller weight for outside large shareholders.

Additional positive filters may include:

- multiple insiders buying;
- a meaningful increase in insider ownership;
- purchase size large relative to prior holdings;
- short reporting delay;
- opportunistic rather than routine timing.

The paper’s evidence suggests that high buys can remain informative for routine insiders, so routine status should reduce rather than automatically eliminate the signal.

### Sale-side signal

Sales require stricter filtering because ordinary insider sales have many non-information motives.

A candidate sale score is:

$$
SellScore_{i,t}
=
Rank(SellDollarIntensity)
\times
Rank(SellAgainstAnchor)
\times
Rank(-Momentum_{12-2})
\times
InformationWeight.
$$

The strongest bearish case is:

- an open-market insider sale;
- price far below the 52-week high;
- weak past return;
- an opportunistic insider;
- meaningful sale size relative to holdings;
- no obvious option-exercise, tax, or scheduled-plan explanation.

Use the sale signal primarily as:

- a short-selection filter;
- a long-portfolio exclusion signal;
- or a risk-reduction overlay.

Because of borrow costs, a long-only implementation may obtain more reliable value by avoiding low-sell stocks rather than shorting all of them.

### Portfolio implementation

A direct replication would independently rank stocks on:

- anchor distance;
- and 12–2 momentum.

Possible long portfolio:

- stocks with recent insider purchases;
- top decile of purchase distance from the 52-week low;
- top decile of 12–2 momentum.

Possible short or avoidance portfolio:

- stocks with recent insider sales;
- top decile of sale distance below the 52-week high;
- bottom decile of 12–2 momentum.

Hold for one to three months and allow the position to decay gradually.

A practical decay function could be:

$$
w_{i,t+h}
=
w_{i,t}\exp(-\lambda h),
$$

where $h$ is the number of trading days since the filing.

Given the event-time results, half-lives between approximately one and three months should be tested. The persistent 12-month spread does not necessarily imply that a fixed 12-month holding period is optimal because new filings and price information arrive during the interval.

### Neutralization

The raw signal should be neutralized or evaluated against:

- market beta;
- sector and industry;
- country, where relevant;
- size;
- value;
- 12–2 momentum;
- one-month reversal;
- distance from 52-week high;
- realized volatility;
- liquidity;
- short interest;
- analyst revisions;
- earnings-announcement proximity.

The most important research question is whether anchor-conditioned insider trading adds predictive power beyond:

$$
InsiderDirection + Momentum + RangePosition.
$$

A useful horse race would compare:

- raw insider net purchases;
- insider trade size;
- anchor distance alone;
- momentum alone;
- insider direction interacted with anchor distance;
- insider direction interacted with momentum;
- the full three-way interaction.

### Robustness tests for a modern replication

A production-quality replication should include:

- Post-2002 sample only.
- Post-publication out-of-sample period.
- Signal timing based on filing acceptance timestamps.
- Explicit treatment of after-market and intraday filings.
- Separate results for 10b5-1 and non-10b5-1 trades.
- Exclusion of filings connected to option exercise.
- Exclusion or separate treatment of microcaps.
- Minimum stock-price and ADV screens.
- Equal-, value-, and liquidity-weighted portfolios.
- Net returns after spreads, impact, borrow fees, and reporting delays.
- Calendar-time inference with Newey–West or appropriate clustered errors.
- Issuer-event aggregation to address multiple overlapping insider trades.
- Purged validation where overlapping holding periods do not leak across train and test samples.
- Sector- and market-neutral portfolio construction.
- Subperiod tests around regulatory changes.
- Capacity analysis.

### Potential extensions

#### Aggregate market indicator

A handwritten annotation on PDF p. 26 suggests aggregating the measure to predict the stock market return. The paper itself does not test this extension.

A market-level indicator could be:

$$
AggregateInsiderAnchor_t
=
\frac{
\sum_i HighBuyIntensity_{i,t}
-
\sum_i LowSellIntensity_{i,t}
}{
\sum_i TotalInsiderActivity_{i,t}
}.
$$

Possible uses include predicting:

- broad-market returns;
- market volatility;
- small-cap versus large-cap returns;
- industry returns;
- business-cycle turning points.

The measure should be normalized by the number of eligible firms and by normal insider activity because aggregate filings may vary seasonally and around earnings blackout periods.

#### Industry-level information

Aggregate high buys and low sells within industries. Insider trades may contain information about:

- industry demand;
- input costs;
- regulatory developments;
- capital expenditure;
- product cycles.

An industry-neutral stock alpha and a separate industry-timing alpha could be tested independently.

#### Interaction with earnings announcements

Test whether high buys before or after earnings announcements are more informative.

Relevant distinctions include:

- pre-announcement versus post-announcement filings;
- positive versus negative earnings surprises;
- earnings drift;
- analyst-revision direction;
- distance from the next expected earnings date.

This would help determine whether the signal captures information not yet incorporated into analyst forecasts.

#### Interaction with analyst revisions

A high buy accompanied by upward analyst revisions may simply confirm public information. A high buy without revisions may contain more incremental information.

Similarly, a low sell without downward revisions may identify information that analysts have not yet incorporated.

#### Alternative anchors

The paper acknowledges that the true choice of anchor is not directly observed.

Alternative anchors worth testing include:

- 52-week high and low;
- all-time high;
- post-earnings price;
- insider’s previous purchase price;
- insider’s equity-grant price;
- moving averages;
- analyst target price;
- recent volume-weighted average price;
- acquisition or IPO price;
- maximum drawdown level.

A learned model could allow the relevant anchor to vary by investor type, trade direction, volatility regime, and firm lifecycle.

#### International replication

The framework can be tested in markets with sufficiently detailed insider-disclosure data.

However, local differences matter:

- disclosure delays;
- definition of an insider;
- blackout periods;
- enforcement quality;
- ownership concentration;
- state ownership;
- short-sale restrictions;
- prevalence of controlling shareholders.

The coefficients from the U.S. sample should not be transferred directly to another market.

### Overall assessment

The paper provides a strong and practically useful refinement to insider-trading alpha.

Its most important contribution is not the finding that insiders buy low and sell high. That behavior is largely expected. The useful insight is that trades contradicting this normal tendency contain considerably more return information.

For alpha research, the paper supports using anchor distance as an interaction variable:

$$
\text{Insider direction}
\times
\text{distance from the relevant anchor}
\times
\text{past return}.
$$

The purchase-side signal appears more robust and easier to implement than the sale-side signal.

The reported portfolio returns are too large to accept without independent replication, realistic filing timestamps, and transaction-cost modeling. Nevertheless, the conditioning logic is compelling and can be incorporated into a broader insider-trading model even if the original portfolio alpha does not survive in full.

The most promising practical use is therefore not a literal replication of the extreme long-short portfolio. It is to use high buys and low sells as high-conviction modifiers within a diversified equity-alpha model.