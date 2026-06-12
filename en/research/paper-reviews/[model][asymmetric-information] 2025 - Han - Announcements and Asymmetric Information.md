---
layout: content
title: "Announcements, Expectations, and Stock Returns with Asymmetric Information"
author: "Leyla Jianyu Han"
year: 2025
tags:
  - model
  - asymmetric-information
doi: "10.1016/j.jmoneco.2025.103751"
---

# Announcements, Expectations, and Stock Returns with Asymmetric Information

- DOI: 10.1016/j.jmoneco.2025.103751
- Working-paper DOI: 10.2139/ssrn.3499773
- Publication: Journal of Monetary Economics, Volume 151, 2025, Article 103751
- Author: Leyla Jianyu Han
- Affiliation in the uploaded version: Questrom School of Business, Boston University
- Paper version reviewed: Preprint submitted to Elsevier on February 11, 2025
- Primary classification: `[model][asymmetric-information]`
- Keywords: macroeconomic announcements, earnings announcements, expectations formation, noisy rational expectations, asymmetric information, trading volume
- JEL codes: D83, D84, G11, G12, G14

## Key findings

The paper reconciles two apparently contradictory empirical patterns within a rational-expectations model:

- Consensus forecasts underreact to information.
- Market prices overreact to information before scheduled announcements.

The distinction arises because a consensus forecast is an average of heterogeneous Bayesian beliefs, whereas the stock price is affected by both beliefs and noisy asset supply.

The main empirical findings are:

- Consensus macroeconomic forecast revisions positively predict subsequent forecast errors.
- Consensus firm-level EPS revisions also positively predict realized EPS forecast errors.
- Forecast revisions made by relatively informed forecasters predict the subsequent errors of relatively uninformed forecasters.
- The reverse relationship does not hold: uninformed forecasters’ revisions do not predict informed forecasters’ errors.
- Stock returns accumulated during forecast-revision periods negatively predict high-frequency announcement returns.
- The reversal is considerably stronger during high-volatility periods.
- During low-volatility periods, the relationship becomes weak and can reverse sign.
- Trading volume rises sharply at announcements and falls immediately afterward.

The model explains these findings through two connected mechanisms:

- Under asymmetric information, each investor is Bayesian with respect to their own information, but the average of investors’ beliefs is not itself a Bayesian belief.
- Noise accumulates in prices while uncertainty builds between announcements. When an announcement reveals fundamentals, the accumulated noise component is corrected.

The quantitative model approximately reproduces the central empirical coefficients:

- Model consensus forecast-error coefficient: $0.46$.
- Empirical consensus coefficient used for comparison: approximately $0.32$.
- Model revision-return coefficient: $-0.15$.
- Empirical pooled return coefficient: approximately $-0.16$.

## Research question

The paper asks whether predictable expectation errors and predictable announcement returns necessarily imply irrational expectations.

Under a representative-agent full-information rational-expectations model:

- Beliefs should follow a martingale.
- Forecast revisions should not predict forecast errors.
- Publicly observable returns should not predict pricing errors revealed at announcements.

The empirical evidence violates these restrictions. Existing literature commonly interprets such evidence as behavioral underreaction or overreaction.

The paper offers a different interpretation:

> Rational expectations can remain valid at the individual-investor level when investors have asymmetric information, even though consensus forecasts and equilibrium prices display apparent underreaction and overreaction.

The key departure is therefore from the representative-agent assumption rather than from rationality.

See the Introduction, pages 2–6.

## Empirical design

### Timeline

For a quantity $x_{t+1}$ announced in the next period:

- $\bar E_{t-1}(x_{t+1})$ is the previous consensus forecast.
- $\bar E_t(x_{t+1})$ is the updated consensus forecast.
- $x_{t+1}$ is the announced realization.

The consensus forecast revision is

$$
F^{rev}_t(x_{t+1})
=
\bar E_t(x_{t+1})
-
\bar E_{t-1}(x_{t+1}).
$$

The subsequent forecast error is

$$
F^{err}_{t+1}(x_{t+1})
=
x_{t+1}
-
\bar E_t(x_{t+1}).
$$

The Coibion–Gorodnichenko regression is

$$
F^{err}_{t+1}
=
\alpha
+
\beta_F F^{rev}_t
+
\epsilon_{t+1}.
$$

Under representative-agent full-information rational expectations, $\beta_F$ should equal zero. A positive coefficient is conventionally interpreted as forecast underreaction.

For prices, the revision-period return is the cumulative return between two adjacent forecast-submission dates:

$$
R^{rev}_t
=
\frac{P_t-P_{t-1}}{P_{t-1}}.
$$

The announcement return is measured over the 30-minute window surrounding the announcement:

$$
R^{err}_{t+1}
=
\frac{P_{t+1}-P^-_{t+1}}{P^-_{t+1}},
$$

where $P^-_{t+1}$ is the price 15 minutes before the announcement and $P_{t+1}$ is the price 15 minutes afterward.

The return regression is

$$
R^{err}_{t+1}
=
\alpha
+
\beta_P R^{rev}_t
+
\epsilon_{t+1}.
$$

A negative $\beta_P$ means that price movements during the revision period tend to reverse when the underlying information is publicly revealed.

See Appendix A.1, pages 36–39.

### Data

Macroeconomic forecasts:

- Survey of Professional Forecasters, 1968–2019.
- Consensus Economics, 1990–2019.
- Main forecast variables: real GDP growth and unemployment.
- Announcement dates obtained from the Bureau of Economic Analysis and Bureau of Labor Statistics.

Aggregate market returns:

- SPDR S&P 500 ETF.
- Close-to-close returns between forecast-submission dates.
- 30-minute returns from 8:15 a.m. to 8:45 a.m. around 8:30 a.m. macroeconomic announcements.
- High-frequency sample begins in 2003 because of TAQ availability.

Firm-level earnings:

- I/B/E/S analyst EPS forecasts and realized EPS.
- CRSP firm-level stock returns.
- Sample period: 1980–2019.

The use of firm-level earnings data provides substantially more statistical power and reduces concerns that aggregate return predictability is driven by changing macroeconomic risk premia.

See Appendix A.1, pages 36–40.

## Consensus forecast underreaction

Forecast revisions positively predict later forecast errors.

For macroeconomic forecasts, Table 1 reports:

- GDP consensus coefficient: $0.39$, with a $t$-statistic of $2.29$.
- Unemployment consensus coefficient: $0.24$, with a $t$-statistic of $6.84$.

A positive revision is therefore followed, on average, by a forecast error in the same direction. Forecasters update toward the realization but do not update sufficiently relative to the representative-agent benchmark.

At the firm level, the EPS result is even stronger. Table A.4 reports consensus EPS forecast-error coefficients between $0.41$ and $0.47$, depending on the revision-horizon restriction. The baseline estimate is

$$
\beta_F=0.41,
\qquad
t=11.14.
$$

The baseline panel contains approximately 490,000 observations and includes firm and quarter fixed effects.

See Section 2, pages 7–8, and Appendix A.2, pages 40–41.

## Cross-sectional information asymmetry

The paper identifies informed and uninformed forecasters using persistent historical forecast accuracy.

For forecaster $j$, the absolute forecast error is

$$
err_{j,t}
=
\left|
x_{t+1}-E_{j,t}(x_{t+1})
\right|.
$$

The paper subtracts the cross-sectional mean absolute error and scales the result by that mean:

$$
smerr_{j,t}
=
\frac{
err_{j,t}
-
\frac{1}{J}\sum_{k=1}^{J}err_{k,t}
}{
\frac{1}{J}\sum_{k=1}^{J}err_{k,t}
}.
$$

A lower historical average $smerr$ indicates greater forecast accuracy and is interpreted as higher information precision.

Each quarter:

- The top accuracy tercile is classified as informed.
- The bottom accuracy tercile is classified as uninformed.
- Classification uses only information available through the previous quarter.

Forecast accuracy remains persistent over horizons extending to approximately twenty quarters, supporting the use of historical accuracy as a forecaster characteristic.

The directional prediction tests produce:

- Informed revisions predicting uninformed GDP forecast errors: $0.63$, with $t=4.13$.
- Informed revisions predicting uninformed unemployment errors: $0.49$, with $t=3.83$.
- Uninformed revisions predicting informed GDP errors: $0.08$, statistically insignificant.
- Uninformed revisions predicting informed unemployment errors: $-0.08$, statistically insignificant.

This asymmetry is central to the paper. It is not merely evidence that forecasters possess different independent signals. The information sets are hierarchical:

$$
\mathcal F_t^u
\subset
\mathcal F_t^i.
$$

Informed investors know more than uninformed investors, while uninformed investors do not possess offsetting private information that informed investors lack.

The results are robust to:

- Lifetime forecast-accuracy measures.
- Fixed two-year rolling accuracy windows.
- Quintile classifications.
- Decile classifications.

See Table 1 on page 8 and Appendix A.3, pages 41–49.

## Price overreaction and announcement reversal

The paper’s novel price result is that revision-period returns negatively predict announcement returns.

Table 2 reports standardized revision-return coefficients:

- Consensus Economics GDP: $-0.075$, with $t=-2.21$.
- Consensus Economics unemployment: $-0.082$, with $t=-2.19$.
- SPF GDP: $-0.071$, with $t=-2.20$.
- SPF unemployment: $-0.088$, with $t=-1.44$.

For GDP, a one-standard-deviation increase in revision-period returns predicts approximately a $7.5$ basis-point lower return in the 30-minute announcement window.

The paper verifies that revision-period returns move in the same direction as forecast revisions:

- Positive GDP revisions are associated with positive revision-period market returns.
- Upward unemployment revisions are associated with negative market returns.

This supports the interpretation that prices and forecasts respond to related information during the revision period.

See Section 2, pages 9–10, and Table A.3 on page 40.

## Firm-level earnings-announcement evidence

The firm-level test regresses a stock’s earnings-announcement return on its return surrounding the most recent analyst forecast revision.

The specification includes firm, analyst, and quarter fixed effects, with standard errors clustered by firm and revision date.

Table A.6 reports negative coefficients across several matched revision and announcement windows:

- Five-day window $[-2,2]$: $-0.013$, with $t=-5.64$.
- Three-day window $[-1,1]$: $-0.014$, with $t=-5.89$.
- Window $[0,2]$: $-0.018$, with $t=-7.00$.
- Window $[0,4]$: $-0.012$, with $t=-4.92$.
- Same-day window: $-0.003$, with $t=-1.83$.

A 1% increase in the three-day return around a forecast revision is associated with approximately a 1.4 basis-point reduction in the three-day earnings-announcement return.

The firm-level design strengthens identification because:

- Analysts submit revisions on different dates.
- Revision timing is less mechanically related to aggregate macroeconomic conditions.
- Short windows better isolate the market response associated with each revision.
- Analyst-level revision returns are less likely to proxy for aggregate risk-premium variation.

The economic magnitude is small per event, but the sign is consistent across windows and is estimated with high statistical precision.

See Appendix A.4, pages 45–47.

## Volatility dependence

The reversal is strongly state dependent.

During high-volatility periods, Table 2 reports coefficients ranging from approximately $-0.10$ to $-0.18$:

- GDP: $-0.098$ and $-0.143$, depending on survey.
- Unemployment: $-0.131$ and $-0.183$.

These estimates are roughly 1.5 times the unconditional coefficients and are statistically significant.

During low-volatility periods, the coefficients are generally insignificant and positive:

- Values range from approximately $0.01$ to $0.07$.

The VIX-based robustness test produces a similar pattern.

The interpretation is:

- High uncertainty causes the effect of noise on prices to build between announcements.
- The subsequent announcement produces a large correction.
- When volatility falls unexpectedly, some accumulated noise begins to correct before the announcement.
- Revision-period corrections and announcement corrections then move in the same direction, producing positive rather than negative predictability.

A limitation is that stochastic volatility is not fully introduced as an endogenous state variable in the solved equilibrium. The low-volatility sign reversal is illustrated through an unexpected volatility transition and comparative statics. The paper explicitly leaves the complete time-varying-volatility extension for future research.

See pages 9–10 and 25–27, particularly Figure 5 and footnote 20.

## Trading volume

Trading volume spikes at macroeconomic announcements and then drops rapidly.

Figure 1 measures excess one-minute turnover for SPY around GDP and unemployment announcements. The largest increase occurs at the 8:30 a.m. release time.

The model interprets this as trading generated when public information suddenly eliminates part of the information asymmetry and changes investors’ optimal holdings.

Because portfolio holdings follow diffusion processes in the continuous-time model, ordinary turnover is not directly defined. The paper therefore introduces quadratic trading volume based on the quadratic variation of portfolio positions.

Empirically:

- Quadratic volume increases by approximately $75\%$ from the day before an announcement to the announcement day.
- It falls by approximately $43\%$ from the announcement day to the next day.

The corresponding model values are approximately:

- $31\%$ increase before the announcement.
- $36\%$ decline afterward.

The directions and broad magnitudes are consistent, although quadratic trading volume is not identical to conventional share turnover.

See Figure 1 on page 11 and pages 31–33.

## Model setup

The paper develops a continuous-time noisy rational-expectations equilibrium model based on Wang (1993), augmented with periodic announcements.

### Preferences and assets

Investors have CARA utility and trade:

- A risk-free bond with constant return $r$.
- A risky stock that pays a dividend flow.

The dividend process is

$$
dD_t
=
(x_t-D_t)dt
+
\sigma_D dB_{D,t}.
$$

The latent long-run dividend component follows

$$
dx_t
=
b(\bar x-x_t)dt
+
\sigma_x dB_{x,t}.
$$

The total risky-asset supply is noisy and mean reverting:

$$
d\theta_t
=
-a\theta_tdt
+
\sigma_\theta dB_{\theta,t}.
$$

The variable $\theta_t$ represents noise-trader supply, liquidity shocks, or other nonfundamental demand and supply disturbances.

See Section 3.1, pages 12–13.

### Information structure

There are two investor groups:

- A fraction $1-\omega$ is informed.
- A fraction $\omega$ is uninformed.

Informed investors observe a private signal:

$$
ds_t
=
x_tdt
+
\sigma_s dB_{s,t}.
$$

Uninformed investors do not observe this signal but learn indirectly from prices.

At scheduled dates $t=nT$, an announcement fully reveals the current latent state $x_t$. Immediately afterward:

$$
\hat x_{nT}
=
\tilde x_{nT}
=
x_{nT},
$$

and posterior uncertainty resets to zero.

Between announcements, the latent state evolves and uncertainty accumulates again.

See pages 13–17 and Figure 2.

### Equilibrium price

The conjectured equilibrium price is

$$
P_t
=
\phi
+
\phi_DD_t
-
\phi_\theta(t)\theta_t
+
\phi_x(t)\hat x_t
+
\phi_\Delta(t)\tilde x_t.
$$

Equivalently, from the uninformed investor’s perspective,

$$
P_t
=
\phi
+
\phi_DD_t
-
\phi_\theta(t)\tilde\theta_t
+
\bar\phi_x\tilde x_t.
$$

Important coefficients are:

- $\phi_\theta(t)$: price sensitivity to noisy asset supply.
- $\phi_x(t)$: price impact associated with informed beliefs.
- $\phi_\Delta(t)$: price impact associated with uninformed beliefs.

The model solution produces:

- $\phi_\theta(t)>0$ and increasing between announcements.
- A downward jump in $\phi_\theta(t)$ at the announcement.
- An increasing $\phi_x(t)$ as informed investors’ information advantage grows.
- A decreasing $\phi_\Delta(t)$ as uninformed investors become relatively less aggressive.

Figure 3 on page 20 illustrates these patterns.

## Why consensus beliefs underreact

Each group’s forecast is conditionally rational:

$$
\operatorname{Cov}
\left(
\hat E_t[x_T]-\hat E_0[x_T],
x_T-\hat E_t[x_T]
\right)
=
0,
$$

and

$$
\operatorname{Cov}
\left(
\tilde E_t[x_T]-\tilde E_0[x_T],
x_T-\tilde E_t[x_T]
\right)
=
0.
$$

Neither group’s forecast revision predicts its own error.

However, informed investors’ revisions contain private information absent from uninformed beliefs:

$$
\operatorname{Cov}
\left(
\hat E_t[x_T]-\hat E_0[x_T],
x_T-\tilde E_t[x_T]
\right)
>
0.
$$

The reverse covariance is zero:

$$
\operatorname{Cov}
\left(
\tilde E_t[x_T]-\tilde E_0[x_T],
x_T-\hat E_t[x_T]
\right)
=
0.
$$

The consensus forecast is

$$
\bar E_t[x_T]
=
(1-\omega)\hat E_t[x_T]
+
\omega\tilde E_t[x_T].
$$

Consequently,

$$
\operatorname{Cov}
\left(
F^{rev}_t,
F^{err}_T
\right)
>
0.
$$

The important conceptual point is that an average of Bayesian conditional expectations formed under different information sets is generally not itself the conditional expectation under a single information set.

Thus, apparent consensus underreaction does not require any individual investor to violate Bayes’ rule.

See Proposition 1, pages 18–19.

## Why prices overreact

The price is affected by both beliefs and noisy supply.

Immediately after an announcement:

- The true state is known.
- Information asymmetry is temporarily eliminated.
- The price impact of noise is relatively low.

As time passes:

- Fundamental uncertainty rises.
- Uninformed investors rely more heavily on the noisy price when learning about fundamentals.
- A price change caused by supply noise is partially interpreted as fundamental news.
- This belief response amplifies the effect of the original noise shock.
- Therefore, $\phi_\theta(t)$ increases.

The price change during a revision interval includes the term

$$
-
\left[
\phi_\theta(t+\delta)
-
\phi_\theta(t)
\right]
\tilde\theta_t.
$$

Because $\phi_\theta(t)$ rises over time, noise becomes progressively more strongly embedded in the price.

At the announcement, uncertainty falls and $\phi_\theta$ jumps downward. The announcement return contains the correction

$$
-
\left[
\phi_\theta(T)
-
\phi_\theta(T^-)
\right]
\tilde\theta^-_T.
$$

Revision-period noise accumulation and announcement-time noise correction have opposite signs. Persistent noisy supply therefore produces

$$
\operatorname{Cov}
\left(
P_{t+\delta}-P_t,
P_T-P^-_T
\right)
<
0.
$$

Proposition 2 shows that the result holds when the noise-supply effect is sufficiently strong relative to the fundamental-information component.

If $\phi_\theta(t)$ is continuous, the announcement-specific predictable component disappears. Lemma 3 establishes that standard noisy rational-expectations models with constant or continuous price coefficients cannot generate the same high-frequency announcement-return predictability.

See pages 22–25.

## Calibration and quantitative performance

The model is calibrated annually and simulated daily with quarterly announcements.

Selected parameters from Table 3 include:

- Risk-free rate: $r=0.03$.
- Time-discount parameter: $\rho=0.01$.
- Fraction uninformed: $\omega=0.35$.
- Fundamental mean reversion: $b=0.14$.
- Fundamental volatility: $\sigma_x=0.8$.
- Private-signal noise: $\sigma_s=0.4$.
- Noisy-supply volatility: $\sigma_\theta=0.58$.
- Noisy-supply mean reversion: $a=0.007$.

Calibration targets include:

- Mean, volatility, and persistence of the price-dividend ratio.
- Dividend-growth volatility.
- Aggregate return volatility.
- Persistence of VIX squared.
- Implied-variance reduction around announcements.

The model produces:

- Log price-dividend mean of $3.46$, versus $3.37$ in the data.
- Log price-dividend volatility of $0.46$, versus $0.43$.
- First-order price-dividend autocorrelation of $0.96$, versus $0.94$.
- Annual return volatility of $15.73\%$, versus $18.48\%$.
- VIX-squared autocorrelation of $0.93$, versus $0.97$.
- Announcement implied-variance reduction of $2.48$, versus $1.97$ in the data.

The model-generated forecast and return regressions are close to the target moments:

| Moment | Data | Model |
| --- | ---: | ---: |
| Consensus revision predicting consensus error | $0.32$ | $0.46$ |
| Informed revision predicting uninformed error | $0.56$ | $0.93$ |
| Uninformed revision predicting informed error | $0.00$ | $0.00$ |
| Revision-period return predicting announcement return | approximately $-0.16$ | $-0.15$ |

The informed-to-uninformed coefficient is materially larger in the model than in the data. The paper attributes this to the calibration treating institutions as informed and households as uninformed, whereas the empirical survey comparison is between relatively informed and relatively uninformed professional forecasters.

See Section 4, pages 27–33.

## Contribution relative to existing models

The paper differs from behavioral expectation models by retaining individual Bayesian rationality.

It differs from standard noisy rational-expectations models because periodic announcements create:

- Time-varying posterior uncertainty.
- Time-varying price sensitivity to noise.
- Discrete corrections when information is publicly revealed.

It differs from differential-information models in which both groups possess separate private signals. Such models generally imply symmetric cross-predictability:

- Group A’s revision predicts Group B’s error.
- Group B’s revision predicts Group A’s error.

The data instead support hierarchical information:

- Informed revisions predict uninformed errors.
- Uninformed revisions do not predict informed errors.

It also differs from finite-horizon models in which noisy supply is mechanically eliminated at a terminal date. Here, recurring announcements generate repeated cycles of uncertainty accumulation and resolution in an infinite-horizon environment.

## Strengths

- Provides one mechanism for both consensus underreaction and price overreaction.
- Preserves Bayesian rationality at the individual level.
- Produces a sharp directional prediction from hierarchical information sets.
- Tests the mechanism using both macroeconomic surveys and firm-level earnings data.
- Uses narrow announcement windows to improve identification.
- Shows that the price effect varies systematically with volatility.
- Connects beliefs, returns, uncertainty, and trading volume within one equilibrium framework.
- Quantitatively matches several important empirical coefficients rather than providing only qualitative comparative statics.
- Clearly distinguishes average beliefs from an individual conditional expectation.

## Limitations and interpretation issues

### Aggregate return sample size

The macroeconomic return tests contain only approximately 58–66 observations, depending on the series. Statistical significance is consequently moderate, and the unemployment result in one specification has a $t$-statistic of only $-1.44$.

The firm-level evidence provides much greater power, but the economic setting differs from the aggregate macroeconomic model.

### Measuring informedness

Historical forecast accuracy is an indirect proxy for information precision. It may capture:

- Forecasting skill.
- Model quality.
- Employer resources.
- Sector specialization.
- Persistent optimism or pessimism.
- Chance performance.

Persistence and robustness tests strengthen the interpretation, but the information sets remain unobserved.

### Revision-period return interpretation

Returns between survey dates contain all information arriving during the period, not only information that caused the measured forecast revision. The positive correlation between forecast revisions and returns supports the interpretation, but it does not fully isolate common news.

The firm-level short-window tests alleviate this concern.

### Full revelation assumption

Scheduled announcements are assumed to reveal the latent state perfectly. Actual GDP and earnings releases are noisy, subject to revisions, and reveal only part of the relevant long-run state.

The assumption creates a clean uncertainty reset and helps generate the discontinuity in $\phi_\theta(t)$.

### Common informed signal

All informed investors observe a common private signal. Real institutions are likely to have heterogeneous signals, models, processing abilities, and interpretations.

The common signal produces the hierarchical structure cleanly but may overstate agreement among informed investors.

### Volatility extension

The solved benchmark equilibrium has a fixed fundamental-volatility parameter. The low-volatility positive-predictability result is generated through an unexpected volatility reduction rather than through a fully solved regime-switching equilibrium.

### Trading-volume mapping

The model uses quadratic variation of portfolio holdings, while the data use squared high-frequency turnover. The comparison captures trading intensity but is less direct than the comparisons involving forecasts and returns.

### Approximate institutional interpretation

The model calibrates $35\%$ of investors as uninformed using household asset ownership. This is a coarse mapping:

- Households are not necessarily uninformed.
- Institutional investors are not uniformly informed.
- Survey forecasters are not representative of household investors.

### Table-label issue

The caption of Table 2 appears to reverse the descriptions of $\beta_H$ and $\beta_L$, stating that they correspond to below- and above-mean volatility, respectively. The surrounding text consistently interprets $\beta_H$ as the high-volatility coefficient and $\beta_L$ as the low-volatility coefficient. This appears to be a caption typo rather than a difference in the analysis.

## Suggestion on how to use the paper

### Use as a rational mechanism for expectation underreaction

The paper is useful when a positive forecast-revision coefficient is being interpreted as evidence of behavioral bias.

The result shows that

$$
\operatorname{Cov}
\left(
F^{rev},
F^{err}
\right)
>
0
$$

does not by itself reject rational expectations. The same statistic can arise because consensus averages investors with nested information sets.

When analyzing revision signals, separate:

- Whether an individual forecast is inefficient relative to its own information.
- Whether the consensus is inefficient because it aggregates heterogeneous information.
- Whether one identifiable group’s revisions predict another group’s errors.

The cross-group regressions are more informative about the mechanism than the consensus regression alone.

### Construct an analyst-information hierarchy

A direct empirical extension is to estimate analyst informedness using lagged forecast accuracy.

For analyst $j$, define a historical accuracy score such as

$$
Accuracy_{j,t}
=
-
\frac{1}{K}
\sum_{k=1}^{K}
smerr_{j,t-k}.
$$

Analyst revisions can then be weighted by estimated information quality:

$$
WeightedRevision_{i,t}
=
\sum_{j\in\mathcal A_{i,t}}
w_{j,t}\Delta EPS_{i,j,t},
$$

where $w_{j,t}$ increases with historical accuracy.

Potential variants include:

- Top-tercile analyst revisions.
- Difference between high-accuracy and low-accuracy analyst revisions.
- Revision breadth among high-accuracy analysts.
- Interaction between revision direction and analyst-information rank.
- Cases where informed analysts revise but the broader consensus has not yet followed.

The paper directly establishes this hierarchy for macro forecasters. Applying it to individual equity analysts would be a natural alpha-oriented extension rather than a result already demonstrated in the paper.

### Separate fundamental continuation from price reversal

The central insight is that forecasts and prices may react differently to the same information:

- Forecast revisions underreact and predict future fundamental surprises in the same direction.
- Revision-period price movements overreact and predict announcement returns in the opposite direction.

This suggests treating the two objects as separate signals:

$$
FundamentalNews_{i,t}
=
\Delta ConsensusEPS_{i,t},
$$

and

$$
PriceReaction_{i,t}
=
R^{revision}_{i,t}.
$$

A positive earnings revision accompanied by a strongly positive stock return can imply:

- A positive expected earnings surprise.
- A negative expected announcement-window return due to prior price overreaction.

The paper therefore warns against treating a forecast-revision signal and the contemporaneous price response as interchangeable measures of news.

### Earnings-announcement reversal signal

For each firm and upcoming earnings announcement, measure the stock return around recent analyst revision events:

$$
RevisionReturn_{i,t}
=
\sum_{\tau\in\mathcal R_{i,t}}
w_\tau R_{i,[\tau-h,\tau+h]}.
$$

The paper predicts

$$
E
\left[
R^{EA}_{i,t+1}
\mid
RevisionReturn_{i,t}
\right]
<
0
$$

for positive revision-period returns, with the sign reversed for negative returns.

Potential constructions include:

- Most recent analyst-revision return.
- Mean revision-window return across analysts.
- Median revision-window return.
- Revision-return breadth.
- Residual revision return after removing market, industry, and common-factor returns.
- Stronger weighting for revisions closer to the announcement.
- Stronger weighting for historically accurate analysts.

The reported effect is statistically reliable but economically small, so it is more naturally used as an event-timing component or as an interaction than as a standalone medium-horizon alpha.

### Condition reversal signals on uncertainty

The model predicts that the reversal should strengthen when fundamental uncertainty is high.

A simple interaction is

$$
AnnouncementReversal_{i,t}
=
-
RevisionReturn_{i,t}
\times
HighUncertainty_{i,t}.
$$

Possible uncertainty measures include:

- Implied volatility.
- Realized volatility.
- Analyst forecast dispersion.
- Earnings uncertainty.
- Firm-specific residual volatility.
- Distance from the previous information-resetting event.
- Large disagreement between informed and uninformed analyst groups.

The paper also implies that a single unconditional reversal coefficient can hide a regime change. During sufficiently low-volatility periods, the coefficient may approach zero or become positive.

### Use time since the last announcement as a state variable

Uncertainty accumulates after an announcement and is reset when new information is released.

For scheduled corporate events, potential state variables include:

- Days since the previous earnings announcement.
- Days until the next earnings announcement.
- Cumulative volatility since the previous announcement.
- Cumulative analyst revisions since the previous announcement.
- Growth in analyst disagreement during the cycle.
- Growth in implied volatility during the cycle.

A useful model-inspired state variable is

$$
AccumulatedUncertainty_{i,t}
=
\sum_{s=t_0}^{t}
\sigma^2_{i,s},
$$

where $t_0$ is the previous announcement date.

The prediction is that the price impact of nonfundamental demand should be greater when accumulated uncertainty is high.

### Distinguish informational price moves from noisy price moves

The model implies that the reversal component comes from noisy supply rather than from the rationally forecastable component of fundamentals.

An empirical signal should therefore attempt to isolate revision-window returns unexplained by observable fundamental revisions:

$$
NoiseReturn_{i,t}
=
RevisionReturn_{i,t}
-
\hat\beta^\top FundamentalRevision_{i,t}.
$$

The announcement reversal should be more closely associated with the residual return than with the component explained by fundamental news.

This provides a sharper empirical implementation of the model than using raw revision-window returns alone.

### Use trading-volume spikes as a mechanism diagnostic

The announcement-volume spike is better treated as evidence about the mechanism than as the primary alpha signal.

A candidate reversal is more consistent with the model when it is accompanied by:

- High pre-announcement uncertainty.
- A large announcement-time volume increase.
- A rapid decline in volume afterward.
- A sharp reduction in implied volatility.
- A price move opposite to the preceding revision-period return.

This combination indicates an information reset and correction of previously accumulated noise.

## Bottom line

The paper’s most important contribution is the distinction between individual rationality, consensus beliefs, and market prices.

Individual investors can update optimally while:

- Consensus forecasts appear to underreact.
- Prices appear to overreact.
- Announcement returns reverse previous price movements.

The forecast result is driven by hierarchical information sets. The return result is driven by time-varying price sensitivity to persistent noise and the discrete resolution of uncertainty at scheduled announcements.

For equity-alpha research, the most useful implications are:

- Weight analyst revisions by persistent information quality.
- Do not equate fundamental revisions with contemporaneous price reactions.
- Look for announcement reversals following large revision-window returns.
- Condition those reversals on uncertainty and volatility.
- Attempt to isolate the nonfundamental component of the revision-period price move.