---
layout: content
read: false
---

# Capital Market Assumptions and Strategic Asset Allocation Using Multi-Asset Tradable Factors

- DOI: 10.2139/ssrn.6785958
- Authors:
  - Artur Sepp, Global Head of Quantitative Analytics, LGT Bank, Switzerland
  - Emilie H. Hansen, Investment Solutions Quantitative Group, LGT Bank
  - Mika A. Kastenholz, Global Head of Investment Solutions, LGT Bank
- Version: May 17, 2026
- Publication type: SSRN working paper
- Tag: `[model][asset-allocation]`

## Key finds

- The paper proposes the Multi-Asset Tradable Factors Capital Market Assumptions framework, abbreviated MATF-CMA, for generating long-horizon expected returns used in strategic asset allocation.

- Its central design principle is that expected returns and the covariance model should be constructed from the same factor loading matrix:

$$
\boldsymbol{\mu}-r_f\mathbf{1}
=
\hat{\boldsymbol{\beta}}\boldsymbol{\lambda}
$$

$$
\boldsymbol{\Sigma}
=
\hat{\boldsymbol{\beta}}
\boldsymbol{\Sigma}_F
\hat{\boldsymbol{\beta}}^\top
+
\mathbf{D}
$$

  Here, $\hat{\boldsymbol{\beta}}$ contains asset-factor loadings, $\boldsymbol{\lambda}$ contains expected factor risk premia, $\boldsymbol{\Sigma}_F$ is the factor covariance matrix, and $\mathbf{D}$ contains residual variances.

- Because the same $\hat{\boldsymbol{\beta}}$ is used in both equations, the expected excess return vector lies inside the span of the risk model by construction. The authors call this alpha-beta consistency.

- The factor model contains nine tradable factors:
  - Equity
  - Rates
  - Credit
  - Currency carry
  - Inflation
  - Commodities
  - Private equity
  - Rates volatility
  - FX

- Equity, Rates, and Credit premia are estimated from market-observable valuation or yield decompositions. Carry, Inflation, Commodities, Private Equity, and Rates Volatility use assumed long-run equilibrium Sharpe ratios. FX is included as a risk-only factor with zero expected premium.

- Asset loadings are estimated using Hierarchical Clustering Group Lasso, or HCGL, augmented with:
  - economically motivated sign constraints;
  - asset-cluster group penalties;
  - nonzero prior loadings for exposures that are difficult to identify statistically because of factor collinearity.

- The authors introduce a general consistency diagnostic:

$$
\boldsymbol{\Delta}
=
\left[
\mathbf{I}
-
\boldsymbol{\beta}
\left(
\boldsymbol{\beta}^\top\boldsymbol{\beta}
\right)^{-1}
\boldsymbol{\beta}^\top
\right]
\left(
\boldsymbol{\mu}-r_f\mathbf{1}
\right)
$$

  $\boldsymbol{\Delta}$ is the component of expected excess returns that cannot be represented by the factor model. The diagnostic can be applied to any expected-return vector and any factor risk model, not only MATF-CMA.

- In the paper's 17-asset example, conventional per-asset expected-return estimates generate typical consistency residuals of approximately 20 to 85 basis points per asset. The cross-asset $L_2$ norm has a median of approximately 2.8% and a 95th percentile of approximately 4.8%. MATF-CMA has zero residual when no explicit alphas are admitted.

- The bootstrap analysis reports that MATF-CMA reduces the width of the efficient-frontier confidence band by approximately two times relative to per-asset sample-mean estimation. The authors interpret this as information equivalent to approximately four times the historical sample length.

- This uncertainty reduction is not free. It comes mainly from imposing a relatively tight structural prior on factor Sharpe ratios. The sensitivity analysis on page 38 shows that the reduction falls from 3.69 times under an aggressive prior to only 1.10 times when prior uncertainty is comparable to historical sampling uncertainty.

- The framework changes investment-committee governance from setting dozens of correlated asset-level forecasts to setting a smaller number of factor premia, loading constraints, alpha-admission weights, and scenario shocks.

- For practical use, the strongest contribution is the architecture and consistency diagnostic. The specific factor-premium numbers should be treated as illustrative calibrations rather than universal expected-return estimates.

## Detail notes

### Research motivation

Capital market assumptions are long-term forecasts of expected returns, risks, and correlations for asset classes. They are direct inputs to strategic asset allocation and mean-variance optimization.

The paper identifies two weaknesses in common institutional CMA processes.

The first is structural inconsistency. Expected returns are often produced through a building-block process, while the covariance matrix comes from a separate factor or statistical risk model. Nothing guarantees that the return forecasts are representable by the risks recognized by the covariance model.

The second is estimation uncertainty. Producing a separate expected return for every asset requires many noisy forecasts. When these forecasts depend on common macroeconomic assumptions, their errors are correlated and may compound rather than diversify.

The Grinold-Kroner equity decomposition is used as the main example:

$$
E[R]
=
\frac{D}{P}
+
g
+
\pi
+
\Delta(P/E)
$$

where the components are dividend yield, real earnings growth, inflation, and valuation reversion.

On page 5, the paper assumes realistic estimation errors for the four US equity components. The standard error is approximately 2.70% if component errors are independent and 3.64% if they have pairwise correlation of 0.5. This produces an extremely wide confidence interval around a 6% expected-return estimate.

This example illustrates the problem, but it is an assumed error decomposition rather than an empirical evaluation of actual institutional Grinold-Kroner forecasts.

### Core MATF-CMA architecture

For asset $i$, the arithmetic expected return is:

$$
\operatorname{CMA}_i
=
r_f^{\text{ref},3Y}
+
\hat{\boldsymbol{\beta}}_i^\top
\boldsymbol{\lambda}
$$

The factor-implied excess return is therefore:

$$
\operatorname{CMA}^{\text{factor}}_i
=
\sum_{j=1}^{M}
\hat{\beta}_{ij}\lambda_j
$$

The covariance model is:

$$
\boldsymbol{\Sigma}
=
\hat{\boldsymbol{\beta}}
\boldsymbol{\Sigma}_F
\hat{\boldsymbol{\beta}}^\top
+
\mathbf{D}
$$

The diagram on page 7 provides the clearest summary of the paper.

Under a traditional process, expected returns and covariance are estimated separately. The expected-return vector can therefore contain a component outside the column space of the factor loading matrix.

Under MATF-CMA, factor premia and the HCGL loading matrix jointly determine expected returns, while the same loading matrix determines covariance. The expected-return vector is consequently factor-spanned by construction.

This is an important system-design principle:

> A portfolio optimizer should not receive an expected-return model and a risk model that describe economically incompatible worlds.

However, consistency is defined relative to the selected factor model. A zero residual proves internal coherence, but it does not prove that the factor set is complete, that the loadings are stable, or that the factor premia are accurate.

### Relationship to Black-Litterman

The authors position MATF-CMA as an alternative architecture to Black-Litterman.

Both frameworks contain:

- a structural prior;
- a mechanism for introducing investment views;
- a covariance or risk model;
- a mapping from lower-dimensional assumptions to asset-level expected returns.

The main differences are:

- Standard Black-Litterman derives its equilibrium prior from market-capitalization weights:

$$
\boldsymbol{\Pi}
=
\delta\boldsymbol{\Sigma}\mathbf{w}_{\text{mkt}}
$$

- MATF-CMA derives its prior from factor loadings and directly calibrated factor premia:

$$
\boldsymbol{\mu}^{\text{MATF}}
-
r_f\mathbf{1}
=
\hat{\boldsymbol{\beta}}
\boldsymbol{\lambda}^{\text{MATF}}
$$

- Black-Litterman requires a view uncertainty matrix $\boldsymbol{\Omega}$ and prior-confidence parameter $\tau$.

- MATF-CMA asks the investment committee to specify factor-premium assumptions directly.

- Standard asset-space Black-Litterman does not necessarily keep expected returns inside the span of a separately selected factor loading matrix. Factor-space Black-Litterman does.

An institution could therefore use MATF-CMA factor premia as the prior for a factor-space Black-Litterman model. The two methods are complementary rather than mutually exclusive.

The comparison table on page 9 is useful for understanding the governance inputs required by each approach.

### Factor specification

The extended MATF model contains the following factors.

| Factor | Construction | Volatility target | Premium estimation |
|---|---|---:|---|
| Equity | MSCI World futures | 15% | Payout and Cyclically-Adjusted Earnings Yield |
| Rates | G10 10-year government bond futures | 6% | OIS-implied term premium plus roll-down |
| Credit | 66% CDX IG and 34% CDX HY QIS | 5% | Credit spread less expected loss |
| Carry | Long high-yielding currencies and short low-yielding currencies | 5% | Equilibrium Sharpe ratio |
| Inflation | US five-year breakeven QIS | 5% | Equilibrium Sharpe ratio |
| Commodities | Bloomberg Commodity Index futures | 15% | Equilibrium Sharpe ratio |
| Private Equity | Synthetic equity-credit replication portfolio | 7% | Equilibrium Sharpe ratio |
| Rates Volatility | Long swaption-volatility QIS | 5% | Equilibrium Sharpe ratio |
| FX | ICE Dollar Index futures | 7% | Zero expected premium |

The illustrative factor premia as of March 31, 2026 are approximately:

| Factor | Expected excess return |
|---|---:|
| Equity | 2.53% |
| Rates | 0.58% |
| Credit | 1.60% |
| Carry | 1.50% |
| Inflation | 0.50% |
| Commodities | 1.50% |
| Private Equity | 3.50% |
| Rates Volatility | 1.50% |
| FX | 0.00% |

Only the Equity, Rates, and Credit premia are derived principally from current valuation or yield data. The remaining positive premia depend on equilibrium Sharpe-ratio assumptions.

The distinction matters because the paper sometimes describes the framework broadly as market-implied, while a substantial part of the expected-return vector remains judgmentally calibrated.

### Equity factor premium

The Equity factor premium uses the Payout and Cyclically-Adjusted Earnings Yield methodology.

Standard cyclically adjusted earnings are:

$$
\operatorname{CAE}_t
=
\frac{1}{K}
\sum_{k=0}^{K-1}
\tilde{E}_{t-k}
$$

$$
\operatorname{CAEY}_t
=
\frac{\operatorname{CAE}_t}{P_t}
$$

P-CAEY modifies historical earnings for retained earnings that were reinvested rather than distributed:

$$
E_s^{\text{P-adj}}
=
d_s\tilde{E}_s
+
(1-d_s)\tilde{E}_s
\left(
1+\operatorname{CAEY}_s
\right)^{t-s}
$$

The regional equity premium is then:

$$
\lambda_{\text{Equity},r}
=
\operatorname{P\text{-}CAEY}_r
-
r_{f,r}^{\text{real}}
$$

The global Equity premium is a market-cap-weighted aggregation of regional premia.

Regional indices are not priced solely with their regional equity premium. The paper combines:

- exposure to the global Equity factor;
- a regional equity valuation adjustment;
- contributions from Rates, Credit, Carry, Commodities, and other factors.

For region $r$:

$$
\operatorname{CMA}^{\text{excess}}_r
=
\hat{\beta}^{\text{eq}}_r
\lambda_{\text{Equity}}^{\text{Global}}
+
\left(
1-\hat{\beta}^{\text{eq}}_r
\right)
\lambda_{\text{Equity},r}
+
\sum_{j\neq\text{eq}}
\hat{\beta}_{r,j}\lambda_j
$$

This is intuitive as a global-plus-regional decomposition, but the use of $1-\hat{\beta}^{\text{eq}}_r$ as the regional loading is partly a modeling convention rather than a result derived directly from the return regression.

### Rates factor premium

The Rates factor premium has two components:

$$
\lambda_{\text{Rates},c}
=
TP_{10,c}
+
RD_{10,c}
$$

The term premium is approximated by:

$$
TP_{10,c}
=
y_{10,c}
-
\operatorname{OIS}_{5Y5Y,c}
$$

The roll-down return is approximated by:

$$
RD_{10,c}
=
\frac{
\left(
y_{10,c}-y_{7,c}
\right)D_{10}
}{
T_{\text{roll}}
}
$$

The global Rates premium is a liquidity-weighted average across government bond futures from the US, Germany, UK, Japan, Canada, and Australia.

This is transparent and observable, although $y_{10}-\operatorname{OIS}_{5Y5Y}$ is only an approximation to the term premium. It does not fully account for maturity mismatch, convexity, forward-rate risk, or differences between government and swap curves.

### Credit factor premium

Credit spread is decomposed as:

$$
s
=
PD\times LGD
+
CRP
+
\ell
$$

For liquid CDS indices, the paper assumes the liquidity component $\ell$ is small and estimates:

$$
CRP
\approx
s-PD\times LGD
$$

The current and historical credit-risk premia are blended equally:

$$
CRP_k^{\text{blend}}
=
0.5
\left(
s_k^{\text{current}}-EL_k
\right)
+
0.5
\left(
s_k^{\text{historical}}-EL_k
\right)
$$

The final factor premium is:

$$
\lambda_{\text{Credit}}
=
0.66CRP_{\text{IG}}^{\text{blend}}
+
0.34CRP_{\text{HY}}^{\text{blend}}
$$

The construction is implementable, but the fixed 50% blending weight, through-the-cycle default rates, and constant recovery assumptions are judgmental. The approach also abstracts from variation in liquidity, downgrade risk, spread duration, and risk-premium cyclicality.

### Structural factor premia

For Carry, Inflation, Commodities, Private Equity, and Rates Volatility:

$$
\lambda_k
=
SR_k^{LR}\sigma_k^*
$$

The long-run Sharpe-ratio assumptions are:

| Factor | Assumed Sharpe ratio |
|---|---:|
| Carry | 0.30 |
| Inflation | 0.10 |
| Commodities | 0.10 |
| Private Equity | 0.50 |
| Rates Volatility | 0.30 |

These assumptions provide strong shrinkage and make the framework operational, but they are among its most important subjective inputs.

The Private Equity factor is particularly model-dependent. It is a synthetic replication based on Nasdaq, Russell 2000, high-yield credit, and global equity exposures. This may capture systematic risk in private equity, but it cannot fully represent illiquidity, stale pricing, leverage, vintage effects, manager selection, and cash-flow timing.

### Rates-volatility factor

The Rates Volatility factor is intended to capture the negative exposure of corporate assets to increases in long-term interest-rate volatility.

The factor is a long swaption-volatility QIS strategy with an assumed positive premium of 1.5%. Most conventional assets are estimated to have negative betas to this factor.

Consequently, the contribution to an asset CMA is often negative:

$$
\hat{\beta}_{i,\text{RatesVol}}
\lambda_{\text{RatesVol}}
<
0
$$

The factor is economically interesting because it identifies short-volatility exposure that may not be visible in conventional Equity-Rates-Credit decompositions.

Its reliability will depend heavily on the construction and history of the QIS index. Backfilled QIS data, transaction costs, dealer methodology changes, and investability should be examined before production use.

### FX factor

The FX factor is constructed from ICE Dollar Index futures and assigned:

$$
\lambda_{\text{FX}}=0
$$

It contributes to covariance but not expected return.

This allows the risk model to explain currency-driven co-movements without assigning a structural premium to directional dollar exposure. Currency carry remains a separate compensated factor.

This distinction between a risk-only factor and a priced factor is useful and could be applied elsewhere. Not every important covariance driver must receive a positive expected return.

### Multi-currency estimation

The framework estimates currency-specific loadings while keeping factor premia common across currencies.

For unhedged equities and alternatives, the reference-currency regression target is:

$$
Y_t^{(\text{ref})}
=
\left(
Y_t^{\text{local}}
-
r_t^{\text{local}}
\right)
+
\Delta S_t^{\text{local/ref}}
$$

For hedged fixed income:

$$
Y_t^{(\text{ref})}
=
Y_t^{\text{local}}
-
r_t^{\text{ref}}
$$

Under long-horizon uncovered interest-rate parity:

$$
E[
\Delta S_t^{\text{local/ref}}
]
=
r_t^{\text{local}}
-
r_t^{\text{ref}}
$$

The expected values of the hedged and unhedged targets therefore coincide under the assumption.

The Swiss equity example on page 23 shows that the USD and CHF excess CMAs differ by only approximately 20 basis points, while total CMAs differ by more than three percentage points because of the different risk-free anchors.

The multi-currency construction is operationally appealing, but currency invariance is approximate. Uncovered interest-rate parity can fail over practical horizons, and actual hedged returns also depend on cross-currency basis, transaction costs, contract tenor, and hedge-rebalancing policy.

### HCGL factor loading estimation

The authors use Hierarchical Clustering Group Lasso to estimate asset-factor loadings.

Assets are first grouped using hierarchical clustering. Group Lasso regularization then encourages economically similar assets to retain or discard factor exposures together.

The paper adds sign constraints:

- Equity, Rates, Credit, and Carry loadings are generally constrained to be non-negative for long-only traditional assets.
- Rates Volatility loadings are constrained to be non-positive.
- Private Equity exposure is forced to zero for traditional assets.
- Inflation, Commodities, and FX are generally unconstrained.
- Hedge funds and real assets receive fewer restrictions.

The sign constraints improve interpretability and prevent economically implausible estimates, but they also make the results conditional on the researcher's prior economic classification.

### Prior-centered regularization

Credit and Equity factor returns have a correlation of approximately 0.9 in the paper's recent sample. Under ordinary sparse regression, the Equity factor can absorb most of the Credit exposure, causing estimated Credit betas to shrink to zero.

The authors therefore modify the HCGL penalty to shrink toward nonzero prior loadings:

$$
\min_{\boldsymbol{\beta}}
\left\{
\frac{1}{t}
\sum_{t'=1}^{t}
w_{t',t}
\left\|
\mathbf{Y}_{t'}
-
\boldsymbol{\beta}\mathbf{X}_{t'}
\right\|_2^2
+
\lambda
\sum_{g=1}^{G}
\sqrt{s_g}
\left\|
\boldsymbol{\beta}_{I_g}
-
\boldsymbol{\beta}^{0}_{I_g}
\right\|_2
\right\}
$$

The principal nonzero priors are:

- Credit beta of 0.2 for investment-grade instruments.
- Credit beta of 0.4 for sub-investment-grade and hybrid instruments.
- Inflation beta of 0.2 for inflation-linked bonds.

This solves an attribution problem but not an identification problem. When factors are highly collinear, the data cannot reliably distinguish their separate effects. The prior determines which economically preferred decomposition is selected.

The paper reports modest improvements in $R^2$ after introducing the priors. A stronger validation would compare rolling out-of-sample forecast errors, covariance forecasts, and portfolio outcomes with and without the prior-centered penalty.

### Explicit residual alpha

The factor-implied excess CMA may be augmented with historical residual alpha:

$$
\operatorname{CMA}^{\text{excess}}_i
=
\hat{\boldsymbol{\beta}}_i^\top
\boldsymbol{\lambda}
+
w_i\alpha_i
$$

where:

$$
\alpha_i
=
\bar{Y}_i
-
\hat{\boldsymbol{\beta}}_i^\top
\bar{\mathbf{X}}
$$

The inclusion weight $w_i\in[0,1]$ controls how much residual alpha is admitted.

The proposed policy is:

- $w_i=0$ for traditional equity and bond indices;
- positive $w_i$ for selected low-$R^2$ alternatives where residual return may represent manager skill, illiquidity compensation, or another economically meaningful source.

This is a good governance feature because it separates systematic factor premia from explicitly declared alpha.

However, historical residual alpha is one of the noisiest inputs in the model. For private and alternative assets, it may also contain return smoothing, stale valuations, selection effects, survivorship bias, or omitted systematic factors.

### Alpha-beta consistency diagnostic

Define the projection onto the factor-loading space as:

$$
\mathbf{P}_{\beta}
=
\boldsymbol{\beta}
\left(
\boldsymbol{\beta}^\top
\boldsymbol{\beta}
\right)^{-1}
\boldsymbol{\beta}^\top
$$

The orthogonal-complement projection is:

$$
\mathbf{M}_{\beta}
=
\mathbf{I}
-
\mathbf{P}_{\beta}
$$

For a candidate CMA vector:

$$
\boldsymbol{\Delta}
=
\mathbf{M}_{\beta}
\left(
\boldsymbol{\mu}-r_f\mathbf{1}
\right)
$$

Under MATF-CMA:

$$
\boldsymbol{\mu}-r_f\mathbf{1}
=
\boldsymbol{\beta}\boldsymbol{\lambda}
$$

and therefore:

$$
\boldsymbol{\Delta}
=
\mathbf{M}_{\beta}
\boldsymbol{\beta}\boldsymbol{\lambda}
=
\mathbf{0}
$$

If explicit alphas are included:

$$
\boldsymbol{\mu}-r_f\mathbf{1}
=
\boldsymbol{\beta}\boldsymbol{\lambda}
+
\mathbf{W}\boldsymbol{\alpha}
$$

then:

$$
\boldsymbol{\Delta}
=
\mathbf{M}_{\beta}
\mathbf{W}\boldsymbol{\alpha}
$$

This diagnostic is one of the paper's most reusable contributions.

Important interpretation:

- $\boldsymbol{\Delta}=0$ means that expected returns are fully representable by the selected factor model.
- It does not mean that expected returns are correct.
- $\boldsymbol{\Delta}\neq0$ can represent an unintended model artifact, but it can also represent genuine alpha, omitted factors, asset characteristics, or misspecification of the risk model.

The paper reports the $L_2$ norm $\|\boldsymbol{\Delta}\|_2$ as a portfolio-level violation. Strictly speaking, this is a Euclidean cross-asset norm, not a return on a particular portfolio. It does not account for portfolio weights, asset volatility, residual risk, or the optimizer's sensitivity to each component.

A covariance-weighted or residual-risk-weighted version may be more decision-relevant.

### Diagnostic without a named factor model

When only a covariance matrix is available, the paper proposes extracting principal-component loadings:

$$
\boldsymbol{\Sigma}
=
\mathbf{U}
\boldsymbol{\Lambda}
\mathbf{U}^\top
$$

$$
\hat{\boldsymbol{\beta}}_{\text{PCA}}
=
\mathbf{U}_M
\boldsymbol{\Lambda}_M^{1/2}
$$

The same projection diagnostic can then be applied to the principal-component factor space.

This extension is useful when using a commercial covariance model whose internal factors are unavailable.

The result depends on the selected number of components $M$. Choosing $M$ based on an explained-variance threshold introduces another modeling decision.

### Scenario construction

Historical factor returns are converted into five-year CMA shocks by dividing annual returns by the horizon:

$$
\Delta f_k^{5Y}
=
\frac{1}{5}
f_k^{\text{annual, scenario}}
$$

The scenario CMA is:

$$
\operatorname{CMA}^{\text{scenario}}_i
=
r_f
+
\hat{\boldsymbol{\beta}}_i^\top
\boldsymbol{\lambda}
+
\hat{\boldsymbol{\beta}}_i^\top
\Delta\mathbf{f}^{5Y}
$$

The paper uses:

- 2022 as a stress scenario;
- 2023 as an upside scenario.

The main advantage is coherent propagation. A single factor shock automatically generates scenario returns for every asset.

The main limitation is that dividing a one-year return by five is a simple linear annualization assumption. It does not model persistence, mean reversion, compounding, changing betas, nonlinear payoffs, or scenario-dependent covariance.

### Strategic asset allocation optimization

The paper maximizes expected portfolio return:

$$
\max_{\mathbf{w}^{\text{SAA}}}
\boldsymbol{\mu}^\top
\mathbf{w}^{\text{SAA}}
$$

subject to benchmark-relative tracking error:

$$
\left(
\mathbf{w}^{\text{bm}}
-
\mathbf{w}^{\text{SAA}}
\right)^\top
\boldsymbol{\Sigma}
\left(
\mathbf{w}^{\text{bm}}
-
\mathbf{w}^{\text{SAA}}
\right)
\leq
\sigma_{\text{target}}^2
$$

The illustration uses:

- 17 assets;
- four risk profiles;
- versions with and without alternatives;
- a 1.5% annual tracking-error limit;
- asset weights constrained to within plus or minus 50% of benchmark weights.

The optimized Balanced portfolio without alternatives increases expected return from approximately 5.6% to 6.0%.

The Balanced portfolio with alternatives increases expected return from approximately 6.4% to 7.1%.

The optimizer tends to overweight:

- high-yield and emerging-market hard-currency bonds;
- Private Equity;
- Real Assets.

It underweights:

- government bonds;
- lower-CMA alternatives such as Hedge Funds.

These outcomes are mechanically linked to the assumed factor premia. In particular, the high Private Equity allocation is supported by a 3.5% Private Equity factor premium and admitted residual alpha.

The results demonstrate internal functionality, but they do not constitute out-of-sample evidence that the optimized allocations will outperform.

### Factor concentration in multi-asset portfolios

The portfolio risk decomposition on page 29 shows that the Equity factor remains dominant across most portfolios.

Even an income portfolio with no direct equity allocation receives approximately 22% of its risk from the Equity factor through credit and emerging-market debt.

For equity-heavy portfolios, the Equity factor contributes approximately 70% to 85% of total risk.

Introducing alternatives reduces the Growth portfolio's Equity risk contribution from approximately 86% to 77%, but does not eliminate the concentration.

This is an important practical result:

> Diversification across asset-class labels does not necessarily produce diversification across economic risk factors.

### Bootstrap design

The paper compares:

- a raw asset-level sample-mean and sample-covariance estimator;
- the MATF factor-structured estimator.

The bootstrap uses:

- 300 months from April 2001 to March 2026;
- 500 stationary block-bootstrap draws;
- mean block length of 12 months;
- minimum block length of three months;
- 14 monthly assets and three quarterly alternative assets.

The MATF bootstrap draws factor Sharpe ratios from:

$$
\mathbf{SR}^{(b)}
\sim
N
\left(
\mathbf{m}_{SR},
\boldsymbol{\Sigma}_{SR}
\right)
$$

The baseline prior standard deviation is:

$$
\sigma_{SR}=0.10
$$

The authors compare this with an estimated historical Sharpe-ratio standard error of approximately:

$$
\frac{1}{\sqrt{T_{\text{eff}}}}
\approx
0.20
$$

The prior is therefore approximately twice as precise as the historical data.

For US equities, the reported standard errors are:

| Estimator | Standard error |
|---|---:|
| Sample mean | 3.32% |
| Grinold-Kroner illustration | 3.64% |
| MATF-CMA | 1.60% |

The 90% efficient-frontier bandwidth is approximately:

- 3% to 8% for the asset-level estimator;
- 1.4% to 3.2% for MATF-CMA.

### Interpreting the uncertainty reduction

The two-times reduction should primarily be interpreted as the benefit of dimensionality reduction and prior shrinkage.

The sensitivity table on page 38 reports:

| Sharpe-ratio prior uncertainty | Frontier-band reduction |
|---:|---:|
| 0.050 | 3.69 times |
| 0.075 | 2.69 times |
| 0.100 | 2.07 times |
| 0.125 | 1.69 times |
| 0.150 | 1.44 times |
| 0.200 | 1.10 times |

When the prior becomes as uncertain as the historical data, nearly all of the claimed advantage disappears.

The result is therefore not that factor models automatically create four times more information. It is that an economically structured and sufficiently informative prior can materially reduce posterior uncertainty.

That may be desirable, but the prior must be defensible.

### Important sources of uncertainty omitted or simplified

The reported analytical standard error treats factor loadings and factor volatilities as fixed:

$$
SE
\left(
\hat{R}^{\text{MATF}}_i
\right)
\approx
\left|
\hat{\beta}_{i,f^*}
\right|
\sigma_{SR}
\sigma_{F,f^*}
$$

This omits uncertainty from:

- estimating factor loadings;
- selecting asset clusters;
- selecting the regularization parameter;
- imposing sign constraints;
- setting prior betas;
- choosing the factor universe;
- estimating factor covariance;
- defining QIS factor histories;
- changing factor relationships across regimes.

The bootstrap also uses a common estimated loading structure rather than re-estimating the complete HCGL model-selection pipeline in every draw.

As a result, the uncertainty bands likely understate total model uncertainty.

### Strengths

- Expected returns and risk are integrated through a common factor architecture.

- The methodology is transparent enough to support institutional governance and scenario discussion.

- The factors are designed to be tradable rather than abstract macroeconomic variables.

- The framework distinguishes priced factors, risk-only factors, and explicitly admitted alpha.

- The consistency diagnostic is simple, general, and easy to implement.

- The multi-currency pipeline provides a unified process for producing parallel CMA panels.

- The prior-centered HCGL modification addresses a real attribution problem caused by highly correlated factors.

- Factor-level scenarios propagate consistently across asset classes.

- The paper includes detailed implementation equations and references reproducible code.

- The portfolio risk decomposition demonstrates that apparent asset-class diversification can conceal strong factor concentration.

### Limitations and critical assessment

- Alpha-beta consistency is guaranteed algebraically because expected returns are constructed as $\boldsymbol{\beta}\boldsymbol{\lambda}$. This is useful internal discipline but not empirical validation.

- The factor-spanning requirement is a modeling choice. An expected-return component outside the risk-model span is not necessarily erroneous; it may represent genuine alpha or an omitted factor.

- The diagnostic depends on the selected factor model. A misspecified or incomplete factor model can report perfect internal consistency while producing economically poor forecasts.

- The paper compares MATF primarily with sample means and an illustrative Grinold-Kroner error calculation. It does not provide a full empirical comparison with:
  - Bayesian asset-level shrinkage;
  - James-Stein expected returns;
  - resampled optimization;
  - robust optimization;
  - standard and factor Black-Litterman;
  - alternative factor models;
  - equal-weight or risk-based allocations.

- The sample mean is used as a proxy for per-asset Grinold-Kroner forecasts in the bootstrap. This is convenient but does not directly measure the behavior of actual forward-looking building-block forecasts.

- The claimed two-times uncertainty reduction is strongly determined by the assumed Sharpe-ratio prior dispersion.

- Loading uncertainty and factor-model-selection uncertainty are not fully propagated through the bootstrap.

- Equity and Credit factors are extremely correlated. Their separate loadings and premium contributions are consequently weakly identified and materially determined by priors.

- Several factor premia are judgmental equilibrium assumptions rather than independently market-implied quantities.

- Private Equity and alternative-asset returns are difficult to model using liquid-market proxies because reported returns contain smoothing, leverage, cash-flow timing, and manager-selection effects.

- Adding historical residual alpha for low-$R^2$ alternatives can reintroduce severe expected-return estimation error.

- The Euclidean consistency norm does not account for risk, portfolio weights, or economic materiality.

- The use of a three-year government yield as the risk-free anchor introduces some duration and term-premium exposure despite being described as a cash-like reference.

- The multi-currency derivation relies on long-horizon uncovered interest-rate parity and abstracts from important hedging implementation effects.

- The scenario framework is linear and based on only two selected years. It is not a full macroeconomic scenario model.

- The optimization examples evaluate expected outcomes generated by the same model used to construct expected returns and covariance. There is no realized out-of-sample allocation performance.

- The high expected benefit from alternatives is partly driven by favorable Private Equity and residual-alpha assumptions. It should be tested against unsmoothed risk estimates and conservative alpha haircuts.

## Suggestion on how to use the paper (based on the tag area)

### Use it as a portfolio-model architecture

The most valuable idea is not the exact March 2026 factor-premium calibration. It is the architecture:

$$
\text{factor premia}
+
\text{asset loadings}
\rightarrow
\text{expected returns}
$$

$$
\text{factor covariance}
+
\text{same asset loadings}
\rightarrow
\text{asset covariance}
$$

This creates a single coherent source for:

- expected returns;
- covariance;
- factor attribution;
- scenario analysis;
- portfolio risk decomposition.

For a quantitative research platform, these should be separate reusable components rather than one monolithic model.

### Implement the consistency diagnostic independently

Given a forecast vector $\hat{\boldsymbol{\mu}}$ and risk loading matrix $\mathbf{B}$, calculate:

$$
\hat{\boldsymbol{\mu}}_{\parallel}
=
\mathbf{P}_B
\hat{\boldsymbol{\mu}}
$$

$$
\hat{\boldsymbol{\mu}}_{\perp}
=
\left(
\mathbf{I}-\mathbf{P}_B
\right)
\hat{\boldsymbol{\mu}}
$$

where:

$$
\mathbf{P}_B
=
\mathbf{B}
\left(
\mathbf{B}^\top\mathbf{B}
\right)^{-1}
\mathbf{B}^\top
$$

Interpret the components as:

- $\hat{\boldsymbol{\mu}}_{\parallel}$: expected returns attributable to recognized risk factors;
- $\hat{\boldsymbol{\mu}}_{\perp}$: residual alpha, omitted-factor exposure, or model inconsistency.

Do not automatically force $\hat{\boldsymbol{\mu}}_{\perp}$ to zero. Require that it be explicitly labeled, justified, sized, and risk-managed.

### Adapt the diagnostic for equity alpha research

For stock-selection models, residual alpha is usually the desired output rather than an error.

The paper's diagnostic can be inverted into an alpha-governance process:

- Start with raw stock forecasts.
- Project the forecasts onto the risk-factor loading space.
- Identify the factor-timing component.
- Remove or constrain unwanted factor components.
- Retain the orthogonal residual as stock-selection alpha.
- Record intentional factor views separately.

For a stock-level signal:

$$
\boldsymbol{\alpha}^{\text{raw}}
=
\boldsymbol{\alpha}^{\text{factor}}
+
\boldsymbol{\alpha}^{\text{residual}}
$$

with:

$$
\boldsymbol{\alpha}^{\text{factor}}
=
\mathbf{P}_B
\boldsymbol{\alpha}^{\text{raw}}
$$

$$
\boldsymbol{\alpha}^{\text{residual}}
=
\left(
\mathbf{I}-\mathbf{P}_B
\right)
\boldsymbol{\alpha}^{\text{raw}}
$$

This makes it possible to distinguish:

- stock-selection alpha;
- industry exposure;
- style-factor exposure;
- market beta;
- country and currency exposure;
- deliberate factor timing.

### Use a risk-weighted projection

The paper uses ordinary Euclidean projection. For portfolio construction, consider a weighted projection:

$$
\mathbf{P}_{B,W}
=
\mathbf{B}
\left(
\mathbf{B}^\top
\mathbf{W}
\mathbf{B}
\right)^{-1}
\mathbf{B}^\top
\mathbf{W}
$$

Possible choices include:

$$
\mathbf{W}
=
\boldsymbol{\Sigma}^{-1}
$$

or:

$$
\mathbf{W}
=
\mathbf{D}^{-1}
$$

This gives more weight to economically important or precisely estimated assets and less weight to noisy alternatives.

Compare at least:

- unweighted residual norm;
- residual-risk-weighted norm;
- portfolio-weighted residual;
- optimizer-induced exposure caused by the residual.

### Separate the useful architecture from the uncertain calibrations

A practical implementation can adopt:

- the common beta matrix;
- factor-based covariance;
- factor-level scenarios;
- explicit alpha admission;
- consistency diagnostics;

without adopting the paper's exact:

- Sharpe-ratio assumptions;
- Private Equity factor;
- three-year risk-free anchor;
- P-CAEY calibration;
- Rates term-premium approximation;
- Credit blending weights.

Each factor premium should remain replaceable.

### Recommended validation design

Before using MATF-CMA in production, run a rolling out-of-sample comparison against:

- historical means;
- Bayesian shrinkage of asset means;
- Black-Litterman;
- factor Black-Litterman;
- equal risk contribution;
- minimum variance;
- benchmark-only allocation;
- robust mean-variance optimization.

For every model, evaluate:

- expected-return forecast errors;
- covariance forecast errors;
- allocation turnover;
- stability of factor loadings;
- stability of optimal weights;
- realized tracking error;
- realized factor exposures;
- realized performance relative to the policy benchmark;
- sensitivity to prior assumptions;
- sensitivity to the factor universe;
- sensitivity to the estimation window.

The entire HCGL procedure should be repeated inside each bootstrap or rolling window so that uncertainty from loading estimation and model selection is included.

### Suggested research-system components

A modular implementation could contain:

- `FactorReturnPanel`
  - Stores tradable factor returns.

- `FactorPremiumModel`
  - Produces $\boldsymbol{\lambda}$ from valuation models, yield decompositions, or equilibrium priors.

- `HCGLLoadingEstimator`
  - Estimates $\hat{\boldsymbol{\beta}}$ using clusters, sign constraints, and prior-centered penalties.

- `FactorCovarianceModel`
  - Estimates $\boldsymbol{\Sigma}_F$.

- `AssetCovarianceComposer`
  - Produces $\hat{\boldsymbol{\beta}}\boldsymbol{\Sigma}_F\hat{\boldsymbol{\beta}}^\top+\mathbf{D}$.

- `CMAComposer`
  - Produces $r_f\mathbf{1}+\hat{\boldsymbol{\beta}}\boldsymbol{\lambda}+\mathbf{W}\boldsymbol{\alpha}$.

- `ConsistencyDiagnostic`
  - Computes factor-spanned and residual expected-return components.

- `ScenarioShockOperator`
  - Maps factor shocks into asset-level return scenarios.

- `PortfolioOptimizer`
  - Solves benchmark-relative allocation under tracking-error, exposure, turnover, and weight constraints.

This paper is particularly useful as a design reference for connecting expected-return models, risk models, and portfolio construction in a unified graph.

### Bottom line

The paper provides a strong framework for making strategic expected returns internally coherent with a factor risk model.

Its most durable contributions are:

- the shared-loading architecture;
- the explicit separation of factor premia and residual alpha;
- the alpha-beta consistency diagnostic;
- factor-level scenario propagation;
- the governance reduction from many asset assumptions to fewer factor assumptions.

The empirical claim of approximately two-times lower uncertainty should be interpreted cautiously because it is largely generated by a tight factor Sharpe-ratio prior and does not include all sources of model uncertainty.

Use MATF-CMA as an architecture and diagnostic framework. Re-estimate, challenge, and stress-test the factor-premium calibrations before using them as investment views.