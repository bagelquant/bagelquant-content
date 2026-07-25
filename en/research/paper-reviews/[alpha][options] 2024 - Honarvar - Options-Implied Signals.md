---
read:
---
# Better Opt Out: Revisiting the Predictive Power of Options-Implied Signals

- DOI: 10.2139/ssrn.4766424
- Authors: Iman Honarvar and Clint Howard
- Affiliations stated in the paper: Robeco Quantitative Investments
- Date: September 2024
- JEL classifications: G11, G12, G14
- Keywords: options, asset pricing, implied volatility, volatility smile, skewness, replication, falsification
- Data period: January 1996 to December 2021
- Primary data sources:
  - OptionMetrics IvyDB US for daily option prices and volumes
  - CRSP for stock returns, prices, and trading volumes
  - Compustat for earnings-announcement dates
  - Kenneth French Data Library for factor returns

## Key findings

- The historically strong performance of options-implied stock-selection signals is concentrated almost entirely before March 2008.

- For the authors’ combined options signal, the value-weighted long-short portfolio Sharpe ratio falls from $1.18$ during 1996–2008 to $0.16$ during 2008–2021.

- The corresponding annualized Fama-French six-factor alpha declines from $11.40\%$ to $1.56\%$ and becomes statistically insignificant.

- A substantial part of the pre-2008 performance reflects a timestamp mismatch between stock and option prices rather than genuine forecasting power.

- Before March 2008, OptionMetrics option closing prices could be recorded several minutes after the stock market close while retaining the same trading date. The option observations could therefore contain information that was unavailable at the corresponding stock closing price.

- Lagging the option information by one trading day materially reduces the apparent predictive power:
  - Combined-signal Sharpe ratio during 1996–2008: $1.18$ without lag versus $0.69$ with lag.
  - Break-even transaction cost: $53.4$ basis points without lag versus $27.4$ basis points with lag.
  - Annualized FF6 alpha: $11.40\%$ without lag versus $5.88\%$ with lag.

- The strongest evidence of look-ahead bias appears in the first overnight return following portfolio formation. This is especially pronounced around earnings announcements made after the stock market close but before the historical option-market closing time.

- After March 2008, when OptionMetrics changed its quote-snapshot methodology to align option prices more closely with the stock market close, the difference between lagged and unlagged results becomes much smaller.

- The post-2008 deterioration remains under different portfolio weights, stock-size filters, holding periods, option-moneyness definitions, and implied-volatility aggregation methods.

- The results do not establish that option data contains no useful information. They show that commonly proposed options-implied characteristics do not provide robust standalone monthly stock-selection alpha once timestamp alignment and modern out-of-sample performance are considered.

- Options information may remain useful for:
  - Higher-frequency return forecasting
  - Volatility and risk forecasting
  - Earnings-event analysis
  - Conditional interactions with stock-market signals such as momentum
  - Market-state or informed-trading indicators

## Detail notes

### Research question

The paper tests whether options-implied characteristics robustly predict the cross-section of future stock returns.

The conventional economic argument is that informed or sophisticated investors prefer options because options provide leverage, downside protection, and more precise exposure to beliefs about the distribution of future stock returns. If informed trading reaches the options market first, option prices and volumes should lead stock prices.

The authors challenge this interpretation along two dimensions:

- Temporal robustness: do the signals continue to work after the original discovery period?
- Data-timing robustness: do the signals survive when option and stock observations are aligned to information that was genuinely available at portfolio formation?

The paper is therefore primarily a replication and falsification study rather than a proposal for a new alpha signal.

### Main look-ahead mechanism

Before March 4, 2008, the standard OptionMetrics data could report option quotes observed after the stock market’s 4:00 p.m. Eastern Time close.

Historically, some stock-option markets remained open after the underlying equity market:

- Until June 22, 1997, CBOE stock options closed at 4:10 p.m.
- Thereafter, they generally closed at 4:02 p.m.
- The OptionMetrics observations were still associated with the same calendar trading date as the stock close.

Suppose a company announces earnings immediately after 4:00 p.m.:

- The stock closing price cannot reflect the announcement.
- Option quotes observed a few minutes later can reflect it.
- An option-derived characteristic formed using those quotes is then matched to a stale stock closing price.
- The apparent prediction of the next overnight stock return partly reflects information that had already arrived when the option quote was recorded.

This is not merely a conventional execution delay. It is a violation of the information set used by the backtest.

In March 2008, OptionMetrics changed its methodology to capture option prices closer to the underlying stock-market close. This provides a natural breakpoint for studying the timestamp problem.

See the discussion in the Introduction, pages 2–6, and the economic-explanation section, pages 17–19.

### Sample construction

The investable sample contains common stocks traded on NYSE, NASDAQ, or AMEX with CRSP share codes 10 or 11.

The option sample applies the following filters:

- Positive implied volatility
- Positive best bid
- Positive open interest
- Option midpoint above $\$0.25$
- Bid-ask spread below $50\%$ of the midpoint
- Time to maturity between 10 and 91 days

The authors initially retain micro-cap stocks to reproduce the most optimistic version of the previously documented results. They subsequently impose a size filter excluding stocks below the 20th percentile of NYSE market capitalization.

After filtering, a typical stock-day-moneyness group contains a median of approximately two valid option contracts. Average availability is higher for at-the-money options than for out-of-the-money options.

Because signals relying on out-of-the-money options have substantially lower coverage, results for characteristics such as POMA, COMA, IVSKEW, and QSKEW can be especially sensitive to the option-selection methodology.

See Section 2.1 and Tables 1 and 3, pages 7–9 and 24–26.

### Options-implied signals

The paper studies signals representing several distinct parts of the option surface and trading activity.

#### Option and stock volume

- OSVOL: option volume divided by stock volume.
- $\Delta OSVOL$: change in the option-to-stock volume ratio.
- PVOL/CVOL: put-option volume divided by call-option volume.

These signals are intended to capture informed trading or differences in the intensity of bearish and bullish option demand.

#### Call-put implied-volatility differences

- CPIV: at-the-money call implied volatility minus at-the-money put implied volatility.
- $\Delta P-\Delta C$: change in put implied volatility minus change in call implied volatility.
- $\Delta C$: change in call implied volatility.
- $\Delta P$: change in put implied volatility.

These measures capture changes in relative option demand and deviations across the call and put portions of the volatility surface.

#### Volatility-smile and skew measures

- IVSKEW: out-of-the-money put IV minus at-the-money call IV.
- POMA: out-of-the-money put IV minus at-the-money put IV.
- COMA: a call-side out-minus-at volatility measure.
- QSKEW: a risk-neutral skewness proxy constructed from out-of-the-money put IV and at-the-money call and put IV.

Higher downside skew is commonly interpreted as stronger demand for crash protection or more negative information about the underlying stock.

#### Realized-versus-implied volatility

- RVIV: realized volatility minus average at-the-money implied volatility.
- $\Delta RV$: change in realized volatility.

Realized volatility is calculated from the previous 20 daily returns, requiring at least 12 observations.

#### Volatility of implied volatility

- VOLOFVOL: recent variation in implied volatility, scaled by its mean.

This variable is intended to capture uncertainty about volatility or instability in the option-implied distribution.

#### Combined signal

The COMB strategy is an equal-weighted average of signed cross-sectional percentile ranks for:

- CPIV
- $\Delta P-\Delta C$
- $\Delta OSVOL$
- RVIV
- VOLOFVOL

Each component is signed so that a higher combined value corresponds to a higher expected stock return according to the original literature.

The combination is not claimed to be optimal. It is used to show whether combining signals drawn from different dimensions of the options market produces a more robust result.

See Section 2.2 and Table 2, pages 9 and 25.

### Signal aggregation and portfolio timing

Signals are first calculated daily.

For each stock and month, the authors select the last valid daily observation available in that month. This means that the selected observation does not necessarily fall on the final trading day if no valid option observation exists on that date.

Two timing specifications are compared:

- No-lag specification: use the most recent option observation as of the portfolio-formation date.
- One-day-lag specification: require the option observation to come from at least one trading day before portfolio formation.

For example, a portfolio formed on November 30 uses option information from November 29 under the lagged specification.

The one-day lag is deliberately conservative. It addresses both the historical timestamp mismatch and the practical possibility that a researcher cannot observe, clean, aggregate, and trade on end-of-day option information instantaneously.

See Section 2.3, page 10.

### Portfolio methodology

Stocks are sorted into deciles according to each options-implied characteristic.

The primary portfolio is:

- Long the highest expected-return decile
- Short the lowest expected-return decile
- Rebalanced monthly
- Value-weighted within each decile
- Held for one month

The paper also studies:

- Equal-weighted portfolios
- Value-weighted portfolios
- Samples with and without micro-cap stocks
- Holding periods of 1, 3, 6, 9, and 12 months
- Alternative definitions of option moneyness
- Equal-weighted and volume-weighted option aggregation
- Raw traded-option IV and standardized OptionMetrics IV surfaces

Performance is evaluated using:

- Annualized Sharpe ratio
- Break-even transaction cost
- Annualized intercept from a univariate return regression
- Annualized alpha relative to the Fama-French five factors plus momentum

Newey-West standard errors with six lags are used for the monthly alpha regressions.

See Sections 2.4 and 3.2, pages 10–16.

### Baseline performance results

For the main value-weighted monthly portfolios, the combined signal produces:

#### No implementation lag

- 1996–2008:
  - Sharpe ratio: $1.18$
  - Break-even transaction cost: $53.4$ basis points
  - FF6 alpha: $11.40\%$ per year
- 2008–2021:
  - Sharpe ratio: $0.16$
  - Break-even transaction cost: $4.7$ basis points
  - FF6 alpha: $1.56\%$ per year, statistically insignificant

#### One-day implementation lag

- 1996–2008:
  - Sharpe ratio: $0.69$
  - Break-even transaction cost: $27.4$ basis points
  - FF6 alpha: $5.88\%$ per year
- 2008–2021:
  - Sharpe ratio: $0.14$
  - Break-even transaction cost: $4.2$ basis points
  - FF6 alpha: $1.44\%$ per year, statistically insignificant

Thus, the paper documents two distinct forms of decay:

- A large decrease when moving from the pre-2008 period to the post-2008 period.
- A large decrease when applying an economically reasonable information delay.

See Tables 4 and 5, pages 27–28.

### Individual-signal results

Several of the strongest historical predictors deteriorate sharply after 2008:

- $\Delta P-\Delta C$:
  - Sharpe ratio falls from $1.07$ before 2008 to $0.06$ after 2008.
- VOLOFVOL:
  - Sharpe ratio falls from $0.81$ to $-0.18$.
- QSKEW:
  - Sharpe ratio falls from $0.55$ to $-0.66$.
- IVSKEW:
  - Sharpe ratio falls from $0.28$ to $-0.32$.

CPIV retains more apparent performance than many other variables:

- No-lag post-2008 Sharpe ratio: $0.58$
- Lagged post-2008 Sharpe ratio: $0.32$

However, its performance is substantially weaker after imposing the lag, and the post-2008 risk-adjusted results are not consistently significant.

Some signals reverse sign or remain persistently weak. This highlights that the paper is not simply documenting uniform attenuation. It finds substantial instability in both signal magnitude and direction.

See Tables 4 and 5, pages 27–28.

### Concentration in the first overnight return

The daily return decomposition is one of the paper’s strongest pieces of evidence.

For the combined strategy during 1996–2008, the first day after portfolio formation contributes an unusually large return. For CPIV, the first overnight return is approximately $0.55\%$, representing a substantial portion of the entire monthly long-short return.

After 2008, this overnight contribution becomes much smaller.

This pattern is difficult to reconcile with a persistent monthly risk premium. It is more consistent with either:

- Very rapid price discovery
- Stale equity closing prices
- Look-ahead bias from option observations recorded after the stock close

Figure 2 on page 37 visually shows that the pre-2008 profitability of several signals is disproportionately concentrated in the first overnight interval.

### Earnings-announcement evidence

The authors estimate daily panel regressions separating:

- Close-to-close returns
- Close-to-open overnight returns
- Open-to-close intraday returns

The regressions interact the options characteristic with:

- A pre-March-2008 indicator
- An earnings-announcement indicator
- Their joint interaction

For CPIV, the triple interaction between CPIV, the pre-2008 indicator, and the earnings-announcement indicator is:

- Large and statistically significant for overnight returns
- Insignificant for intraday returns

The overnight coefficient is $2.24$ with significance at the $1\%$ level, while the corresponding intraday coefficient is $-0.51$ and insignificant.

OSVOL produces a similar pattern: its pre-2008 earnings-announcement interaction is concentrated in overnight rather than intraday returns.

This supports the proposed mechanism. Earnings information released after the equity close could enter option quotes before the historical option-market close and then appear mechanically to predict the stock’s overnight adjustment.

See Table 12 and the associated discussion, pages 17–19 and 35.

### Equal-weighted and micro-cap results

As expected, the most optimistic results occur in equal-weighted portfolios that include micro-cap stocks.

For the one-month equal-weighted combined strategy without a market-cap filter:

- Pre-2008 no-lag Sharpe ratio: $1.39$
- Post-2008 no-lag Sharpe ratio: $0.17$
- Pre-2008 lagged Sharpe ratio: $0.78$
- Post-2008 lagged Sharpe ratio: $0.21$

The corresponding no-lag FF6 alpha falls from $23.16\%$ before 2008 to $2.64\%$ after 2008.

The large historical alpha therefore cannot be defended as a phenomenon that remains economically meaningful merely because equal weighting or smaller stocks are used.

See Tables 8 and 9, pages 31–32.

### Holding-period robustness

Longer holding periods generally weaken the signals.

For the full-sample combined strategy:

- Three-month holding-period Sharpe ratio:
  - $0.52$ without lag
  - $0.36$ with lag
- Six-month holding-period Sharpe ratio:
  - $0.22$ without lag
  - $0.15$ with lag
- Twelve-month holding-period Sharpe ratio:
  - $0.11$ without lag
  - $0.12$ with lag

The evidence therefore does not support the interpretation that option-market information identifies a slow-moving return premium that accumulates over several months.

The strongest apparent effect is short-lived, which is consistent with fast information incorporation but also makes the result more vulnerable to timestamp and execution assumptions.

See Tables 6 and 7, pages 29–30.

### Implied-volatility construction robustness

The paper evaluates multiple methods for assigning options to at-the-money, in-the-money, and out-of-the-money groups:

- Log-moneyness based on $\log(S/K)$
- Strike-to-stock-price ratios based on $K/S$
- Equal weighting across qualifying contracts
- Option-volume weighting
- Three standardized-IV-surface specifications using maturity and delta grids

The broad deterioration after 2008 is present under all these methods.

However, the standardized IV-surface results provide an important nuance. Some post-2008 lagged specifications retain Sharpe ratios around $0.4$–$0.5$, and a few alpha estimates remain economically positive or marginally significant.

For example, the lagged post-2008 combined-signal Sharpe ratios are:

- IV Surface One: $0.48$
- IV Surface Two: $0.26$
- IV Surface Three: $0.42$

These are far below the strongest historical results but are not literally zero. The appropriate conclusion is therefore that the alpha is specification-sensitive and insufficiently robust, rather than that all options-implied information is valueless.

See Tables 10 and 11, pages 33–34, and the Internet Appendix, pages 40–51.

### Interpretation of the post-2008 break

The authors discuss three potentially overlapping explanations:

- Look-ahead bias from non-synchronous stock and option closing prices
- Reduced option-market informational advantage following post-financial-crisis market and regulatory changes
- Post-publication decay as investors learn about and trade on the signals

These explanations occur over similar periods:

- OptionMetrics changed its quote methodology in March 2008.
- Major derivative-market reforms followed the global financial crisis.
- Influential options-implied return-prediction papers were published mainly between 2005 and 2010.

The earnings-announcement and overnight-return results provide direct support for the look-ahead mechanism. Nevertheless, the paper does not fully identify how much of the broader post-2008 decay is due to timestamp correction, publication effects, changing market structure, or changes in the composition of optionable stocks.

### Strengths

- The paper examines a large collection of widely cited options-implied predictors rather than focusing on a single failed signal.

- It identifies a concrete data-construction mechanism capable of generating spurious predictability.

- The return decomposition into overnight and intraday components directly connects the empirical results to the proposed mechanism.

- Earnings-announcement interactions provide additional evidence beyond a simple pre/post comparison.

- The analysis considers both raw traded-option data and standardized implied-volatility surfaces.

- Results are tested across weighting schemes, size filters, holding periods, moneyness definitions, and aggregation methods.

- Break-even transaction costs provide more economic information than statistical significance alone.

- The paper distinguishes between the claim that option markets contain information and the stronger claim that standard option characteristics deliver implementable monthly stock-selection alpha.

### Limitations and open questions

- A full-day lag is effective at eliminating timestamp leakage, but it may be more conservative than necessary. A synchronized 4:00 p.m. option snapshot would be preferable because it preserves information genuinely available at the decision time.

- March 2008 is not a clean single-treatment event. It coincides with major changes in market structure, the financial crisis, regulation, and the publication of related research.

- Optionable-stock coverage changes materially through time. The post-2008 sample may contain a different set of firms, industries, liquidity profiles, and investor clienteles.

- The analysis is primarily monthly. It cannot determine whether properly synchronized option information has economically useful predictive power over minutes, hours, or several trading days.

- The study evaluates mostly univariate portfolio sorts and a simple equal-weighted combination. Nonlinear interactions, conditional effects, and state-dependent models may preserve information that unconditional sorts miss.

- The break-even transaction-cost measure is useful but does not fully model implementation frictions such as borrow availability, market impact, delayed signal computation, and turnover concentrated around earnings events.

- Some standardized-IV-surface specifications retain moderate post-2008 performance. These residual results deserve additional out-of-sample investigation rather than being treated as fully resolved.

- The paper ends in 2021. It does not test whether the results persist in the subsequent market environment.

## Suggestion on how to use the paper

### Use as a data-timing standard for options alpha

The paper should be treated as a mandatory implementation reference for any equity signal using options data.

Every option-derived feature should carry at least:

- The trading date
- The exact observation timestamp
- The option-exchange closing convention
- The vendor snapshot methodology
- The stock-price timestamp used for comparison
- The earliest realistic portfolio-execution timestamp

A signal should only be matched to a return when the full signal information set was observable before the beginning of that return.

The governing condition should be:

$$
t_{\text{signal available}} < t_{\text{portfolio execution}}
$$

Matching observations only by calendar date is insufficient.

### Do not use the historical pre-2008 results as the primary alpha prior

The unadjusted 1996–2008 results substantially overstate the expected return of a live monthly strategy.

For forecasting the likely performance of a modern implementation, give substantially more weight to:

- Post-March-2008 results
- Lagged results
- Synchronized-data results
- Large and liquid stock samples
- Specifications that survive alternative IV-surface construction methods

The pre-2008 sample remains useful for diagnosing data problems, but it should not drive the expected Sharpe ratio.

### Treat standalone monthly option signals as weak priors

The paper provides little support for deploying CPIV, IVSKEW, QSKEW, OSVOL, or the combined signal as standalone monthly stock-selection factors.

A reasonable research prior is:

- Low expected standalone alpha
- High sensitivity to timing and construction
- Potentially high turnover
- Limited capacity in smaller stocks
- Greater usefulness as a conditional feature than as a primary ranking signal

### Focus on conditional interactions

A more promising research direction is to interact option information with established stock signals or event conditions.

Potential interactions include:

- Price momentum × changes in option skew
- Earnings surprise × option-volume imbalance
- Short interest × put-call IV spread
- Analyst revision × option-market disagreement
- Residual volatility × volatility-of-implied-volatility
- Momentum crash-risk regime × downside IV skew
- Pre-earnings drift × abnormal option volume

The economic hypothesis should be that the option variable identifies when another equity signal is more or less credible, rather than independently predicting monthly returns.

### Separate information prediction from risk prediction

An option-derived measure may fail to predict expected returns while still forecasting:

- Future realized volatility
- Tail risk
- Earnings-gap risk
- Drawdown probability
- Cross-sectional return dispersion
- Correlation changes
- Short-horizon liquidity demand

Therefore, evaluate option variables separately as:

- Alpha features
- Risk-model features
- Portfolio-sizing inputs
- Event-risk controls
- Trading-cost or liquidity indicators

Failure as a monthly alpha signal does not imply failure as a risk input.

### Reproduce the overnight-versus-intraday decomposition

For every option-based signal, separately evaluate:

$$
r^{\text{overnight}}_{t+1}
=
\frac{Open_{t+1}}{Close_t}-1
$$

and

$$
r^{\text{intraday}}_{t+1}
=
\frac{Close_{t+1}}{Open_{t+1}}-1
$$

A signal whose performance is dominated by the first overnight return should receive additional scrutiny for:

- After-hours information contamination
- Earnings-announcement timing
- Stale closing prices
- Vendor snapshot conventions
- Unrealistic execution assumptions

This decomposition is more diagnostic than examining only monthly cumulative returns.

### Recommended research specification

For a modern replication:

- Start with post-2008 data.
- Prefer intraday or explicitly synchronized 4:00 p.m. option snapshots.
- Retain a one-day-lag specification as a conservative benchmark.
- Record the last valid option observation rather than assuming month-end availability.
- Test raw traded-option data and standardized IV surfaces separately.
- Separate earnings-announcement and non-announcement observations.
- Exclude illiquid options using bid, midpoint, spread, open-interest, and maturity filters.
- Report results with and without micro-cap stocks.
- Examine equal-weighted and value-weighted portfolios.
- Control for momentum, reversal, volatility, size, liquidity, and short interest.
- Test interactions rather than relying only on univariate sorts.
- Compare overnight, intraday, daily, weekly, and monthly horizons.
- Reserve a genuinely untouched recent period for final validation.

### Bottom line for alpha research

This paper is more valuable as a warning about false alpha than as a source of a tradable factor.

Its most important contribution is the demonstration that a small timestamp mismatch can transform information already observed in the options market into apparently strong prediction of future stock returns.

The appropriate practical conclusion is not to discard options data. It is to impose much stricter standards on:

- Point-in-time construction
- Timestamp synchronization
- Execution assumptions
- Post-publication validation
- Signal-horizon selection
- Robustness across option-surface definitions

Options-implied variables are best treated as fragile, fast-moving information features that may enhance other signals or improve risk forecasts, rather than as reliable standalone monthly equity factors.