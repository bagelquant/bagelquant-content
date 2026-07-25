---
layout: content
read: false
---
# Analyst Underreaction and the Post-Forecast Revision Drift

- **DOI:** 10.1111/jbfa.12491
- **Journal:** Journal of Business Finance & Accounting
- **Year:** 2020
- **Authors:**
  - Po-Chang Chen — Farmer School of Business, Miami University
  - Ganapathi S. Narayanamoorthy — A.B. Freeman School of Business, Tulane University
  - Theodore Sougiannis — Gies College of Business, University of Illinois at Urbana-Champaign
  - Hui Zhou — Graduate School of Management, University of Auckland
- **Corresponding author:** Po-Chang Chen
- **Sample period:** 1983–2013
- **Primary data:** I/B/E/S Detail, CRSP, and Compustat
- **Tag:** `[alpha][analyst-revisions]`

## Key findings

- Individual analysts tend to revise their forecasts repeatedly in the same direction for the same annual earnings target. The estimated first-order revision autocorrelation is approximately $0.20$–$0.30$, depending on the specification.

- This persistence is not merely consensus-level revision momentum. It exists within the forecasting history of the same analyst for the same firm and earnings target.

- The market does not fully account for the predictability of future analyst revisions. In the Mishkin test, the actual revision-persistence coefficients are approximately $0.262$ and $0.265$, while the corresponding market-implied coefficients are only $0.076$ and $0.020$ for the three- and six-month return windows.

- The estimates imply that investors underestimate analyst revision persistence by approximately:
  - $71\%$ over three months
  - $92\%$ over six months

- Firms receiving upward revisions subsequently outperform firms receiving downward revisions. The baseline high-minus-low revision-decile return is approximately:
  - $1.8\%$ over three months
  - $2.2\%$ over six months

- Portfolio tests produce larger raw factor-adjusted spreads:
  - Three-month high-minus-low alpha: $3.0\%$ under FF3 and $2.0\%$ under Carhart four-factor
  - Six-month high-minus-low alpha: $4.1\%$ under FF3 and $2.2\%$ under Carhart four-factor

- An analyst-specific revision-momentum coefficient significantly strengthens the relationship between the current revision and future returns. At the average level of analyst underreaction, revision momentum increases the estimated post-revision drift by:
  - Approximately $15\%$ over three months
  - Approximately $28\%$ over six months

- Revision persistence and subsequent price drift are highly asymmetric:
  - Downward revisions exhibit stronger continuation.
  - Upward revisions exhibit considerably less continuation and, in the interaction specification, evidence closer to overreaction or reversal.

- Both revision momentum and price drift are stronger:
  - Before Regulation Fair Disclosure
  - Among firms with lower analyst coverage
  - Following bad-news revisions

- Revision momentum remains present throughout the sample, but the return predictability associated with revisions declines substantially over time.

## Research question

The conventional explanation for post-forecast revision drift, or PFRD, is that investors react too slowly to the information contained in analyst forecast revisions.

The paper asks whether this explanation starts one step too late.

An analyst revision may itself be an incomplete response to the underlying information. When an analyst underreacts, the analyst will subsequently issue additional revisions in the same direction. Investors who value the company using the current, incomplete forecast will therefore also react incompletely, even when they respond efficiently to the forecast number as reported.

The paper separates two potential sources of delayed price discovery:

1. Analysts underreact while producing their forecasts.
2. Investors fail to correct for the analyst’s predictable underreaction.

The central argument is that PFRD reflects the interaction of both effects rather than investor underreaction alone.

## Economic mechanism

Suppose an analyst receives negative information about a company but incorporates only part of its earnings implication into the current forecast.

The current downward revision is therefore followed by:

- Additional downward revisions from the same analyst
- Potentially similar revisions from other analysts
- Further negative price reactions as the omitted information is gradually incorporated

The current revision consequently predicts future returns because it predicts future information releases through the analyst forecast process.

In stylized form:

$$
\text{Current information}
\rightarrow
\text{Incomplete analyst revision}
\rightarrow
\text{Future same-direction revisions}
\rightarrow
\text{Continued price adjustment}
$$

The paper calls the positive serial dependence in revisions **revision momentum**.

This mechanism differs from a pure investor-underreaction explanation. Under the paper’s interpretation, part of the future return is caused by information that is not yet present in the published forecast but is predictable from the analyst’s historical revision behavior.

## Data and sample construction

The study uses individual analyst forecasts from the I/B/E/S Detail File between 1983 and 2013.

The main sample includes:

- $510{,}704$ observations for the three-month return analysis
- $489{,}072$ observations for the six-month return analysis

The authors retain annual earnings forecasts with forecast horizons of up to 13 months.

For each revision pair:

- Both forecasts must come from the same analyst.
- Both forecasts must refer to the same firm.
- Both forecasts must refer to the same annual earnings target.
- The interval between consecutive forecasts must not exceed four months.

This construction is important because it isolates persistence within an individual analyst’s own forecast-updating process. It avoids treating revisions by two different analysts responding to the same event as evidence of individual underreaction.

The analysis uses the I/B/E/S activation or confirmation date as the forecast date. Results remain similar when the announcement date is used instead.

Return data come from CRSP, while accounting controls come from Compustat.

See Section 3 and pages 7–10.

## Signal and variable construction

### Individual analyst forecast revision

The continuous revision measure is:

$$
\text{I\_REV\_PCT}_{i,t}
=
\frac{
\text{Forecast}_{i,t}
-
\text{Forecast}_{i,t-1}
}{
\text{Beginning-of-month stock price}_{t}
}
$$

The forecasts must be consecutive forecasts from analyst $i$ for the same annual earnings target.

Scaling by price makes forecast changes more comparable across firms with different earnings and price levels.

The authors also rank the revision measure into ten cross-sectional groups within each year-month:

$$
\text{I\_REV\_DEC}_{i,t}
=
\operatorname{DecileRank}
\left(
\text{I\_REV\_PCT}_{i,t}
\right)
$$

The scaled rank ranges from $0$ for the lowest revision decile to $1$ for the highest revision decile.

See Section 3 and Appendix A.

### Analyst deviation from consensus

To control for analyst herding, the paper measures the difference between the individual analyst forecast and the consensus forecast excluding that analyst:

$$
\text{I\_DEV}_{i,t}
=
\frac{
\text{Forecast}_{i,t}
-
\text{Consensus excluding analyst }i
}{
\text{Beginning-of-month stock price}_{t}
}
$$

A corresponding decile-ranked variable, $\text{I\_DEV\_DEC}$, is included in the regressions.

This distinction matters because a forecast that is far from consensus may subsequently move toward consensus even without underreaction to new fundamental information.

### Analyst-specific revision momentum coefficient

The paper constructs a direct measure of an individual analyst’s tendency to make same-direction revisions.

For each analyst, the following regression is estimated using a rolling 12-month history:

$$
\text{I\_REV\_PCT}_{m+1}
=
\text{RMC}_{i,q}
\text{I\_REV\_PCT}_{m}
+
\epsilon_m
$$

where:

- $\text{RMC}_{i,q}$ is the analyst-specific Revision Momentum Coefficient.
- The regression does not include an intercept.
- At least 15 observations are required.
- The regression is estimated at each calendar quarter-end.
- The resulting coefficient is applied to that analyst’s revisions during the following quarter.

For example, an RMC estimated from April 2010 through March 2011 is applied to revisions made from April through June 2011.

The paper obtains $107{,}734$ analyst-quarter RMC estimates.

The distribution has:

- Mean RMC: $0.247$
- Median RMC: $0.220$

A larger positive RMC indicates that the analyst has historically tended to follow an initial revision with another revision in the same direction.

See Section 4.4, pages 17–20.

## Empirical design

### Baseline post-forecast revision drift

Future three- and six-month returns are regressed on the current revision rank and a broad set of return predictors:

$$
\begin{aligned}
\text{FRET}_{t+1}
=&\ \alpha
+\beta_1\text{I\_REV\_DEC}_{t}
+\beta_2\text{I\_DEV\_DEC}_{t} \\
&+\text{risk, momentum, accounting, and earnings controls}
+\epsilon_{t+1}
\end{aligned}
$$

The controls include:

- Market beta
- Book-to-market
- Market capitalization
- Past six-month returns
- Past 36-month returns
- Asset growth
- Net operating assets
- Accruals
- R&D intensity
- Standardized unexpected earnings

The authors use monthly Fama–MacBeth regressions, industry fixed effects, and Newey–West standard errors.

Portfolio returns are also evaluated using Fama–French three-factor and Carhart four-factor models.

### Revision-momentum test

To determine whether current revisions predict subsequent revisions by the same analyst, the paper estimates:

$$
\text{I\_REV\_DEC}_{t+1}
=
\alpha
+\beta_1\text{I\_REV\_DEC}_{t}
+\beta_2\text{I\_DEV\_DEC}_{t}
+\beta_3\text{LOGMV}_{t}
+\beta_4\text{SUE}_{t}
+\epsilon_{t+1}
$$

A positive $\beta_1$ indicates that analysts tend to continue revising in the same direction.

### Mishkin market-efficiency test

The Mishkin test compares:

- The actual predictability of future analyst revisions
- The degree of predictability reflected in current market prices

Let $\beta$ represent the actual revision-persistence coefficient and $\beta^*$ the persistence coefficient implied by returns.

The relevant possibilities are:

- $\beta^*=\beta$: investors fully recognize analyst underreaction.
- $0<\beta^*<\beta$: investors recognize some persistence but underestimate it.
- $\beta^*=0$: investors ignore revision persistence.
- $\beta^*<0$: prices behave as though revisions should reverse.

The paper finds $\beta^*$ to be positive but far below $\beta$.

### Direct RMC return test

The direct test adds the analyst-specific RMC and its interaction with the current revision:

$$
\begin{aligned}
\text{FRET}_{t+1}
=&\ \alpha
+\beta_1\text{I\_REV\_DEC}_{t}
+\beta_2\text{RMC}_{t} \\
&+\beta_3
\left(
\text{I\_REV\_DEC}_{t}
\times
\text{RMC}_{t}
\right)
+\text{controls}
+\epsilon_{t+1}
\end{aligned}
$$

The interaction coefficient $\beta_3$ measures whether a revision from an analyst with historically persistent revisions predicts a larger subsequent return.

## Detailed results

### Baseline PFRD

The current revision rank significantly predicts future returns after controlling for return momentum, earnings surprise, valuation, size, asset growth, accruals, net operating assets, and R&D intensity.

The regression coefficients on the revision rank are:

| Future-return window | Revision coefficient |
|---|---:|
| Three months | $0.018$ |
| Six months | $0.022$ |

Because the revision rank ranges from $0$ to $1$, these coefficients represent the approximate return difference between the highest and lowest revision groups.

Portfolio tests produce the following high-minus-low factor-adjusted returns:

| Model | Three months | Six months |
|---|---:|---:|
| Fama–French three-factor | $3.0\%$ | $4.1\%$ |
| Carhart four-factor | $2.0\%$ | $2.2\%$ |

The result remains after controlling for standardized unexpected earnings and past returns, supporting the interpretation that PFRD is distinct from post-earnings-announcement drift and conventional price momentum.

See Table 2, pages 11–14.

### Revision momentum

In the decile specification, the coefficient relating the current revision to the next revision is:

| Specification | Revision coefficient |
|---|---:|
| Analyst variables only | $0.253$ |
| Full controls | $0.200$ |

In the continuous percentage-revision specification:

| Specification | Revision coefficient |
|---|---:|
| Analyst variables only | $0.300$ |
| Full controls | $0.222$ |

All coefficients are statistically significant at the $1\%$ level.

The positive association remains after controlling for:

- Deviation from consensus
- Firm size
- Standardized unexpected earnings
- Industry effects

The result supports the hypothesis that analysts do not immediately incorporate all relevant information into a single forecast revision.

See Table 3, pages 14–15.

### Market understanding of revision persistence

The Mishkin test produces:

| Return window | Actual persistence $\beta$ | Market-implied persistence $\beta^*$ |
|---|---:|---:|
| Three months | $0.262$ | $0.076$ |
| Six months | $0.265$ | $0.020$ |

The restrictions $\beta=\beta^*$ are strongly rejected.

Relative to actual persistence, the market recognizes only:

$$
\frac{0.076}{0.262}
\approx 29\%
$$

over three months, and:

$$
\frac{0.020}{0.265}
\approx 8\%
$$

over six months.

The paper therefore interprets the market as underestimating revision persistence by approximately $71\%$ and $92\%$, respectively.

See Table 4, pages 16–18.

### Direct pricing effect of analyst RMC

The interaction between the current revision and analyst-specific RMC is positive:

| Return window | $\text{Revision}\times\text{RMC}$ coefficient |
|---|---:|
| Three months | $0.009$ |
| Six months | $0.017$ |

At the average RMC of $0.247$, the additional three-month drift is approximately:

$$
0.009\times0.247
=
0.0022
$$

Relative to the baseline revision coefficient of $0.015$, this represents:

$$
\frac{0.0022}{0.015}
\approx 14.7\%
$$

For the six-month window, the corresponding increase is approximately $28\%$.

This is the paper’s most directly usable alpha result: the historical updating behavior of the analyst issuing a forecast contains incremental information beyond the direction of the current revision.

See Table 5, pages 19–20.

### Good-news and bad-news asymmetry

The paper defines GOODNEWS as one for positive forecast revisions and zero for negative revisions.

For revision momentum, the interaction between revision rank and GOODNEWS is:

- $-0.499$ without the full controls
- $-0.400$ with the full controls

The bad-news revision slope in the controlled model is $0.282$, while the corresponding good-news slope is:

$$
0.282-0.400=-0.118
$$

This means the paper finds:

- Underreaction and continuation following bad news
- Overreaction or reversal following good news

The future-return regressions exhibit a similar asymmetry.

For three-month returns:

$$
0.033-0.070=-0.037
$$

For six-month returns:

$$
0.067-0.164=-0.097
$$

Thus, a symmetric treatment of upward and downward revisions discards an important part of the result. The strongest continuation effect is concentrated in downward revisions.

See Table 6, pages 21–22.

### Regulation Fair Disclosure

Revision momentum is lower after Regulation Fair Disclosure.

The interaction between the revision rank and the post-Reg-FD indicator is approximately $-0.154$ in the controlled revision-momentum model.

PFRD also declines after Reg FD:

| Return window | Revision $\times$ Reg FD |
|---|---:|
| Three months | $-0.040$ |
| Six months | $-0.050$ |

Both revision momentum and return drift remain positive after Reg FD, but their magnitudes are lower.

The result supports the mechanism that improved public information availability reduces the extent to which analysts update their forecasts gradually.

See Table 7, pages 23–24.

### Analyst coverage

Higher analyst coverage is associated with weaker revision continuation and weaker PFRD.

The controlled interaction between revision rank and analyst coverage is:

- $-0.056$ for future revisions
- $-0.022$ for three-month returns
- $-0.037$ for six-month returns

The results suggest that greater competition and a richer information environment cause information to be incorporated into forecasts and prices more rapidly.

However, the effect remains present even among high-coverage firms.

See Table 7, pages 23–24.

### Earnings-announcement months

The authors test whether limited analyst attention during traditional earnings-announcement months increases underreaction.

The interaction coefficients are positive but statistically insignificant for both revision momentum and PFRD.

The paper therefore does not find evidence that the main result is driven by analysts being temporarily distracted by a concentration of earnings announcements.

See Section 5.4, pages 26–27.

### Time variation

Revision momentum remains significant in each subperiod:

| Period | Revision-momentum coefficient |
|---|---:|
| 1983–1992 | $0.178$ |
| 1993–2002 | $0.273$ |
| 2003–2013 | $0.153$ |

Revision underreaction peaks during 1993–2002 and subsequently declines.

The three-month return coefficient declines more consistently:

| Period | Three-month PFRD coefficient |
|---|---:|
| 1983–1992 | $0.031$ |
| 1993–2002 | $0.013$ |
| 2003–2013 | $0.009$ |

The six-month coefficient declines from $0.044$ to $0.012$ and then $0.008$. The final-period six-month estimate is not statistically significant.

Revision persistence therefore survives more strongly than its return predictability. Markets appear to become better at processing the information even though analysts continue to revise gradually.

See Table 8, pages 25–27.

### Robustness checks

The main findings remain similar when the authors:

- Extend the forecast horizon from 13 to 16 months
- Scale revisions by the absolute value of prior-year earnings instead of stock price
- Use size-adjusted returns rather than raw returns
- Examine consensus forecast revisions

The consensus-revision autoregressive coefficient is approximately $0.272$.

See Section 5.6, pages 27–28.

## Economic interpretation

The paper changes the interpretation of a revision signal.

A forecast revision is not necessarily a complete summary of an analyst’s information. It may instead represent one point along a gradual adjustment path.

Consequently, the predictive content of a revision has at least two components:

$$
\text{Revision alpha}
=
\text{information in the current revision}
+
\text{predictable future revision continuation}
$$

The second component depends on who issued the revision and how that analyst historically updates forecasts.

This suggests that analysts should not be treated as interchangeable observations. Two identical revisions may have different implications when:

- One comes from an analyst who normally updates forecasts in a single large step.
- The other comes from an analyst who usually makes a sequence of same-direction revisions.

The latter revision should contain more information about future revision flow and, according to the paper, a larger subsequent price drift.

## Critical assessment

### Strengths

- The paper uses individual analyst histories rather than relying only on consensus changes.
- Revisions are matched within the same analyst, firm, and annual earnings target.
- The sample is large and covers more than three decades.
- The mechanism is examined through both indirect and direct tests.
- The analyst-specific RMC is estimated before the revisions to which it is applied.
- The paper documents consistent variation across news type, analyst coverage, and regulatory regime.
- The findings remain robust under alternative revision scalers and return definitions.

### Limitations

- The sample ends in 2013. The paper itself shows that PFRD weakened significantly during the later part of the sample, so the historical return magnitudes should not be treated as current expected returns.

- The study covers US annual earnings forecasts. The magnitude may differ for quarterly forecasts, target prices, recommendations, non-US markets, or alternative analyst datasets.

- The RMC measure requires at least 15 revision pairs in a 12-month window. This favors active analysts and firms with sufficient forecast activity.

- A positive revision autocorrelation is consistent with behavioral underreaction, but it is not definitive proof of irrationality. The authors acknowledge that asymmetric analyst loss functions or strategic forecasting incentives could generate similar patterns.

- The paper documents a relationship between analyst RMC and future returns but does not fully identify whether RMC represents:
  - Stable analyst behavior
  - Broker-level practices
  - The type of firms followed
  - Differences in information arrival
  - Strategic forecast walk-down behavior

- The good-news results are not a simple weaker version of the bad-news effect. The estimated good-news slopes become negative in the interaction models, suggesting that upward and downward revisions may represent different processes.

- The primary result is based on revisions to forecast levels. A signal constructed only from revision counts is related to, but not identical to, the paper’s signal.

## Suggestion on how to use the paper

### Core alpha implication

The paper supports separating two characteristics of analyst revisions:

1. **Revision direction and magnitude**
2. **Expected continuation of the revision process**

A natural alpha representation is:

$$
\alpha_{i,t}
=
\text{CurrentRevision}_{i,t}
\times
\text{ExpectedRevisionPersistence}_{i,t}
$$

The persistence component can be estimated from the historical behavior of:

- The individual analyst
- The broker
- The analyst-firm pair
- The firm’s aggregate revision series

The paper provides the clearest evidence for individual-analyst persistence.

### Analyst-level construction

When individual forecast levels and analyst identifiers are available, a paper-aligned signal is:

$$
\text{RevisionSignal}_{j,t}
=
\operatorname{Rank}_{cs}
\left(
\frac{
F_{j,t}-F_{j,t-1}
}{
P_{t-1}
}
\right)
$$

Estimate each analyst’s historical persistence:

$$
\text{RMC}_{j,t}
=
\frac{
\sum_m
\text{Revision}_{j,m}
\text{Revision}_{j,m+1}
}{
\sum_m
\text{Revision}_{j,m}^{2}
}
$$

This is the no-intercept OLS coefficient used by the paper.

A persistence-enhanced revision signal can then be formed as:

$$
\alpha_{j,t}^{\text{RMC}}
=
\text{RevisionSignal}_{j,t}
\times
\text{RMC}_{j,t}
$$

When several analysts revise the same firm, analyst-level signals can be aggregated into a firm-level signal. Possible aggregation methods include:

- Equal-weighted average
- Revision-magnitude-weighted average
- Recency-weighted average
- Weighting by the precision or stability of the analyst’s RMC estimate

The paper does not directly compare these aggregation rules.

### Construction using revision counts only

When forecast levels are unavailable and only upward and downward revision counts are observed, the paper’s RMC cannot be replicated exactly.

A count-based approximation should capture repeated same-direction revision flow.

Define the signed net revision count:

$$
\text{NetCount}_{i,t}
=
\frac{
N^\uparrow_{i,t}
-
N^\downarrow_{i,t}
}{
N^\uparrow_{i,t}
+
N^\downarrow_{i,t}
}
$$

A rolling revision trend can be constructed as:

$$
\text{CountTrend}_{i,t}
=
\sum_{k=0}^{K}
w_k
\text{NetCount}_{i,t-k}
$$

where the weights decline with the age of the revision window.

A measure of directional agreement is:

$$
\text{Consistency}_{i,t}
=
\frac{
\left|
N^\uparrow_{i,t}
-
N^\downarrow_{i,t}
\right|
}{
N^\uparrow_{i,t}
+
N^\downarrow_{i,t}
}
$$

A count-based persistence signal is then:

$$
\alpha_{i,t}^{\text{count}}
=
\text{CountTrend}_{i,t}
\times
\text{Consistency}_{i,t}
$$

This construction gives the strongest signal to firms where:

- Revisions have repeatedly occurred in the same direction.
- Analysts currently exhibit broad agreement.
- The direction of the current revision wave agrees with the recent history.

Another direct continuation measure is:

$$
\text{Continuation}_{i,t}
=
\text{NetCount}_{i,t}
\mathbf{1}
\left[
\text{NetCount}_{i,t}
\text{NetCount}_{i,t-1}>0
\right]
\left|
\text{NetCount}_{i,t-1}
\right|
$$

This retains the sign of the current revision while increasing its magnitude when the previous window had a strong revision wave in the same direction.

### Treat positive and negative revisions separately

The paper strongly argues against imposing symmetry between upward and downward revisions.

Define separate positive and negative revision trends:

$$
\text{UpTrend}_{i,t}
=
\sum_{k=0}^{K}
w_k
\frac{
N^\uparrow_{i,t-k}
}{
N^\uparrow_{i,t-k}+N^\downarrow_{i,t-k}
}
$$

$$
\text{DownTrend}_{i,t}
=
\sum_{k=0}^{K}
w_k
\frac{
N^\downarrow_{i,t-k}
}{
N^\uparrow_{i,t-k}+N^\downarrow_{i,t-k}
}
$$

The combined signal can be written as:

$$
\alpha_{i,t}
=
\beta_{\text{up}}
\text{UpTrend}_{i,t}
-
\beta_{\text{down}}
\text{DownTrend}_{i,t}
$$

The paper’s evidence implies:

$$
\beta_{\text{down}}
>
\beta_{\text{up}}
$$

It may also justify modeling the positive and negative sides as separate alphas rather than combining them with fixed symmetric coefficients.

### Coverage interaction

The paper suggests that revision persistence is more informative among firms with lower analyst coverage.

A possible interaction is:

$$
\alpha_{i,t}^{\text{coverage}}
=
\alpha_{i,t}^{\text{revision}}
\left[
1+
\lambda
\left(
1-\text{CoverageRank}_{i,t}
\right)
\right]
$$

The economic intuition is that fewer competing analysts and a weaker information environment allow both forecasts and prices to adjust more gradually.

This is likely to alter the signal’s exposure toward smaller and less liquid firms, so it should be viewed as a distinct alpha variant rather than an unconditional improvement.

### Revision acceleration

The underreaction mechanism also motivates measuring whether the revision wave is intensifying:

$$
\text{RevisionAcceleration}_{i,t}
=
\text{NetCount}_{i,t}
-
\text{NetCount}_{i,t-1}
$$

A strong current revision combined with an already persistent historical trend may indicate continuing information incorporation.

Potential variants include:

$$
\alpha_{i,t}
=
\text{NetCount}_{i,t}
+
\gamma_1\text{CountTrend}_{i,t-1}
+
\gamma_2\text{RevisionAcceleration}_{i,t}
$$

The paper does not test revision acceleration directly, but it follows naturally from the gradual-information-incorporation mechanism.

### Analyst disagreement

The paper controls for deviation from consensus but does not position forecast dispersion as its primary signal.

A useful extension is to distinguish between:

- Persistent revisions accompanied by broad analyst agreement
- Persistent revisions concentrated in one or two analysts
- Persistent revisions accompanied by high disagreement

The first case is more consistent with a widespread information-adjustment process. The second may depend more heavily on the historical reliability and RMC of the specific analyst.

### Appropriate interpretation

The most useful contribution of this paper is not the historical magnitude of the reported long-short return.

Its main contribution is the signal-design principle:

> A forecast revision should be interpreted as part of a dynamic analyst-updating process rather than as an isolated event.

The paper supports using revision history, analyst identity, directional asymmetry, and the information environment to condition a basic analyst-revision alpha.