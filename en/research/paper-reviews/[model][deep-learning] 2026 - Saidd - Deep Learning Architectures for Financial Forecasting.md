---
read: false
---
# A Controlled Comparison of Deep Learning Architectures for Multi-Horizon Financial Forecasting: Evidence from 918 Experiments

- Document type: arXiv preprint
- Version: arXiv v1, dated February 27, 2026
- arXiv identifier: 2603.16886
- JEL classification: C45, C52, C53, G17
- Primary topic: Controlled comparison of deep-learning architectures for hourly financial price forecasting

## Author information

- Author: Nabeel Ahmad Saidd
- Affiliation: Dr. A.P.J. Abdul Kalam Technical University, AKTU
- Email: nabeelahmadsaidd@gmail.com
- Author structure: Single-author paper
- Code and data: The paper states that code, data, model checkpoints, HPO logs, configurations, and evaluation outputs are released in a public repository. Repository information appears in Appendix B.4, page 60.

## Key findings

- ModernTCN is the strongest model under the paper's experimental protocol:
  - Mean rank: 1.333
  - Median rank: 1
  - First-place finishes: 18 of 24 asset-horizon evaluation points
  - Win rate: 75%

- PatchTST is the most consistent alternative:
  - Mean rank: 2.000
  - First-place finishes: 3 of 24
  - It stays close to ModernTCN across cryptocurrency, forex, and equity-index categories.

- The global ranking has three broad tiers:
  - Top tier: ModernTCN, PatchTST
  - Middle tier: iTransformer, TimeXer, DLinear, N-HiTS
  - Bottom tier: TimesNet, Autoformer, LSTM

- Architecture-specific inductive bias appears more important than parameter count:
  - DLinear uses approximately 1,000 parameters but outperforms several substantially larger models.
  - Autoformer and LSTM have much larger parameter counts but occupy the bottom tier.
  - ModernTCN and PatchTST provide the best accuracy with moderate rather than maximal capacity.

- Rankings remain relatively stable between the 4-hour and 24-hour forecasting tasks:
  - All models experience materially higher absolute errors at the longer horizon.
  - ModernTCN and PatchTST generally remain in the top two positions.
  - Spearman rank correlations between the two horizons range from approximately 0.68 to 1.00 across assets.

- Final-training random seeds contribute very little measured variance:
  - Raw decomposition: architecture 99.90%, seed 0.01%
  - Within-slot z-normalisation, all models: architecture 48.32%, seed 0.04%
  - Within-slot z-normalisation, excluding LSTM: architecture 68.33%, seed 0.02%
  - The more defensible result is the modern-model, z-normalised panel rather than the headline 99.90% figure.

- Directional accuracy is effectively random:
  - Average directional accuracy across all 54 model-category-horizon combinations is 50.08%.
  - No architecture demonstrates economically meaningful hourly directional forecasting ability.
  - This is the paper's most important result for alpha research: low price-level RMSE does not imply return or direction predictability.

- N-HiTS has some asset-specific strength:
  - It wins on ETH/USDT at both horizons.
  - It wins on ADA/USDT at the 4-hour horizon.
  - The author interprets this as evidence that multi-rate pooling may suit highly volatile, multi-scale cryptocurrency dynamics.

- DLinear is an attractive computational baseline:
  - It ranks around the middle of the model set despite extremely low complexity.
  - It should be treated as a required baseline for future deep-learning time-series experiments.

## Detail notes

### Research question

The paper asks which modern deep-learning architecture performs best for multi-horizon financial forecasting when the models are evaluated under a common experimental protocol.

The comparison includes nine models from four broad families:

- Transformer:
  - Autoformer
  - PatchTST
  - iTransformer
  - TimeXer

- Convolutional:
  - ModernTCN
  - TimesNet

- MLP or linear:
  - DLinear
  - N-HiTS

- Recurrent:
  - LSTM

The intended contribution is not a new forecasting architecture. It is a controlled architecture benchmark.

### Forecasting task

For each timestamp, the model receives an OHLCV input matrix and predicts a vector of future closing prices:

$$
\hat{\mathbf{y}}_{t+1:t+h}
=
f_\theta(\mathbf{X}_t)
$$

where:

- $\mathbf{X}_t$ contains Open, High, Low, Close, and Volume.
- The forecast target is future Close price.
- $h \in \{4,24\}$ hours.
- All future values are produced in one forward pass.
- The loss function is mean squared error.

The two task configurations are:

- 4-hour forecast:
  - 24-hour lookback
  - 4 future closing prices predicted

- 24-hour forecast:
  - 96-hour lookback
  - 24 future closing prices predicted

The paper calls this “direct multi-step forecasting.” More precisely, because the entire output vector is produced jointly, this is closer to a multi-output or MIMO forecasting setup than to the classical direct strategy in which separate models are fitted for each horizon.

### Asset universe

The study uses twelve instruments:

- Cryptocurrency:
  - BTC/USDT
  - ETH/USDT
  - BNB/USDT
  - ADA/USDT

- Forex:
  - EUR/USD
  - USD/JPY
  - GBP/USD
  - AUD/USD

- Equity indices:
  - Dow Jones
  - S&P 500
  - NASDAQ 100
  - DAX

All series are represented at hourly frequency.

The most recent 30,000 observations or windowed samples are retained for each asset. The effective calendar spans differ substantially because cryptocurrency trades continuously, forex pauses over weekends, and equity indices trade only during exchange sessions.

### Data processing

The preprocessing steps are:

- Retain the latest 30,000 samples.
- Fit z-score normalisation on the training partition only.
- Apply the training scaler to validation and test data.
- Construct rolling input and target windows.
- Split chronologically:
  - 70% training
  - 15% validation
  - 15% test
- Do not shuffle the observations.
- Inverse-transform forecasts before computing RMSE and MAE.

Training-only normalisation and chronological ordering are appropriate design choices.

However, the paper does not clearly state whether a purge or embargo is inserted between partitions. Because adjacent rolling samples have heavily overlapping inputs and targets, a sample-level split without purging can cause the same target timestamps to appear in windows on both sides of a train-validation or validation-test boundary.

This does not necessarily mean there is conventional future leakage into model inputs, but it does reduce the independence of the partitions and can make validation and test statistics more optimistic.

### Hyperparameter optimisation protocol

The paper uses a five-stage pipeline.

#### Hyperparameter optimisation

- Optuna TPE sampler
- Fixed HPO seed: 42
- Five trials per model-category-horizon combination
- Fifty training epochs per trial
- Validation MSE as the objective
- One representative asset per category:
  - BTC/USDT for cryptocurrency
  - EUR/USD for forex
  - Dow Jones for equity indices

#### Configuration freezing

The selected configuration for each model-category-horizon combination is frozen and then applied to all four assets in that category.

This reduces asset-level tuning and limits computational cost.

However, an equal number of Optuna trials is not necessarily an equal optimisation budget:

- Search-space dimensionality differs across architectures.
- Some models have more sensitive hyperparameters than others.
- Five trials are too few to explore most of the reported spaces.
- A model with a compact or forgiving search space receives an implicit advantage over a model with a large or irregular space.

Therefore, the study controls the number of trials, but it does not fully control the probability that each architecture is tuned near its attainable optimum.

#### Final training

- Seeds: 123, 456, 789
- Maximum epochs: 100
- Adam optimiser
- Weight decay: $10^{-4}$
- ReduceLROnPlateau scheduler
- Early-stopping patience: 15
- Gradient clipping at norm 1.0
- Best checkpoint selected by validation loss

The total reported experiment count is:

- 270 HPO trials
- 648 final training runs
- 918 runs in total

### Evaluation metrics

The study reports:

- RMSE
- MAE
- Directional accuracy

RMSE is the primary ranking metric.

The reported directional-accuracy definition compares the sign of adjacent movements within the predicted path against adjacent movements within the realised path:

$$
\operatorname{sign}(\hat y_i-\hat y_{i-1})
\quad\text{versus}\quad
\operatorname{sign}(y_i-y_{i-1})
$$

This is not necessarily the most useful directional metric for a trading strategy. For a forecast made at time $t$, a more directly investable definition would often be:

$$
\operatorname{sign}(\hat y_{t+h}-y_t)
\quad\text{versus}\quad
\operatorname{sign}(y_{t+h}-y_t)
$$

Alternatively, one could evaluate predicted returns for each future interval or use a classification objective directly.

The paper also does not clearly explain how the first forecast step is handled in the directional-accuracy calculation, because $\hat y_0$ must refer either to the final observed price or to another convention.

### Main ranking results

The global mean-rank leaderboard on page 21 is:

- ModernTCN: 1.333
- PatchTST: 2.000
- iTransformer: 3.667
- TimeXer: 4.292
- DLinear: 4.958
- N-HiTS: 5.250
- TimesNet: 7.708
- Autoformer: 7.833
- LSTM: 7.958

ModernTCN wins every equity-index evaluation point and almost every forex evaluation point. Its performance is less dominant in cryptocurrency, where N-HiTS and PatchTST achieve several wins.

The small difference between ModernTCN and PatchTST should not always be interpreted as economically meaningful. On BTC/USDT at the 4-hour horizon, for example, PatchTST's RMSE is 731.05 and ModernTCN's is 731.63, a difference of approximately 0.08%.

### Category-level findings

The category means on page 23 show ModernTCN and PatchTST in the top two positions across all three asset classes.

However, the category-level RMSE averages are computed in raw price units. This creates an important weighting problem:

- BTC contributes much larger numerical errors than ADA or BNB.
- Dow Jones contributes much larger errors than an index with a lower numerical level.
- USD/JPY has a different numerical scale from EUR/USD.

Consequently, category-average raw RMSE is dominated by the assets with the largest price units. The rank-based leaderboard is more defensible than the raw category averages.

Better alternatives would include:

- Normalised RMSE
- RMSE divided by price level
- Error measured in returns
- Error measured in basis points
- Mean rank across assets
- MASE relative to a persistence forecast

### Cross-horizon results

Absolute RMSE generally increases by around two to two-and-a-half times between the two tasks.

ModernTCN and PatchTST retain their leading positions, while rank changes are concentrated in the middle tier.

The author interprets this as evidence of cross-horizon architecture stability.

This interpretation should be qualified because the two tasks differ in more than forecast horizon:

- Lookback changes from 24 hours to 96 hours.
- Hyperparameters are separately optimised for each horizon.
- The output dimension changes.
- Effective model complexity may change with the output dimension.
- Training sample construction changes.

Therefore, the reported degradation does not isolate the causal effect of increasing $h$ from 4 to 24. It measures the combined effect of a longer forecast, a longer lookback, separately selected configurations, and a different output structure.

The rank-stability conclusion is still useful, but the percentage degradation should not be interpreted as a pure horizon elasticity.

### Seed robustness

The final-training seed results are highly stable.

This supports the narrower statement that, conditional on:

- A fixed data split
- A fixed HPO seed
- A frozen configuration
- A fixed preprocessing pipeline
- The selected training procedure

the three final weight-initialisation seeds generate similar RMSE rankings.

It does not establish that three seeds are generally sufficient for financial forecasting research.

The paper does not vary:

- HPO seed
- HPO trial order
- Time-period split
- Market regime
- Training-window start date
- Data vendor
- Preprocessing choices

These sources of research variance may be much larger than final-network initialisation variance. The statement “three seeds suffice” should therefore be limited to this specific pipeline.

### Variance decomposition

The headline result says architecture explains 99.90% of raw RMSE variance.

The paper itself acknowledges that this value is largely driven by LSTM's extremely poor errors and by raw-scale effects.

More informative results are:

- Z-normalised, all models:
  - Architecture: 48.32%
  - Seed: 0.04%
  - Residual: 51.64%

- Z-normalised, excluding LSTM:
  - Architecture: 68.33%
  - Seed: 0.02%
  - Residual: 31.66%

The 68.33% result supports the view that architecture matters materially among modern models.

The 31.66% residual is also economically important. It implies substantial model-by-asset-horizon interaction, so the best architecture can depend on the particular market and forecasting task.

The decomposition should ideally include explicit effects for:

- Asset
- Horizon
- Architecture
- Seed
- Architecture-by-asset interaction
- Architecture-by-horizon interaction
- Asset-by-horizon interaction

A model-versus-seed decomposition alone compresses several economically distinct effects into a generic residual.

### Statistical testing

The paper conducts a broad set of tests:

- Friedman test
- Iman-Davenport correction
- Holm-corrected Wilcoxon pairwise tests
- Diebold-Mariano tests
- Spearman rank correlations
- Stouffer combined test
- Intraclass correlation
- Jonckheere-Terpstra test

The global Friedman-Iman-Davenport test strongly rejects equal model performance.

Thirty-three of thirty-six global pairwise Wilcoxon comparisons remain significant after Holm correction. The three non-significant pairs are:

- iTransformer versus TimeXer
- DLinear versus N-HiTS
- TimesNet versus Autoformer

This supports the existence of broad performance tiers.

Important qualifications:

- Only 24 asset-horizon blocks are available globally.
- Only eight blocks are available within each asset category, making category-level pairwise tests underpowered.
- Assets and horizons are not necessarily independent blocks.
- Forecast errors arise from highly overlapping windows.
- Multi-step forecast errors are serially correlated.

Diebold-Mariano inference on overlapping multi-step forecasts normally requires a suitable long-run variance or HAC adjustment. The paper does not provide enough detail to determine whether the reported extremely small Diebold-Mariano p-values adequately account for this dependence.

### Complexity-performance relationship

The paper argues that model complexity and accuracy have a non-monotonic relationship.

This descriptive conclusion is reasonable:

- DLinear is extremely small and performs competitively.
- Autoformer is much larger and performs poorly.
- ModernTCN and PatchTST achieve the best results at moderate parameter counts.

However, failure to detect a significant monotonic relationship is not proof that no relationship exists. The statistical test has only a small number of architectures and uses coarse complexity groups.

There is also an inconsistency in the hypothesis definition:

- Section 1.3 describes a null involving a perfect monotonic correlation of $\rho_S=-1$.
- Section 3.6 says Spearman correlations are tested against zero.
- Section 4.6 reports a Jonckheere-Terpstra test rather than the originally specified Spearman test.

The descriptive evidence is stronger than the formal hypothesis-testing structure.

### Directional accuracy and economic value

Directional accuracy averages 50.08%, with no meaningful deviation from chance.

This sharply limits the trading interpretation of the RMSE results.

The actual-versus-predicted charts on pages 36–38 visually show predictions tracking the realised price level closely. However, a price level is highly persistent. A model can generate a visually impressive forecast by staying close to the latest observed price while possessing no ability to forecast returns.

This explains the apparent contradiction between:

- Close visual alignment in level plots
- Low RMSE
- Directional accuracy near 50%

For financial alpha research, return forecasting, residual forecasting, or cross-sectional ranking is generally more relevant than minimising raw price-level RMSE.

### Most important missing baseline

The paper does not report a naïve persistence or random-walk forecast such as:

$$
\hat y_{t+k}=y_t
$$

This is the most serious omission.

For highly persistent price levels, the last observed price is often an extremely strong RMSE baseline. Without comparison to persistence, it is impossible to determine whether ModernTCN and PatchTST learn genuine predictive structure or merely approximate the current price efficiently.

Other useful baselines would include:

- Driftless random walk
- Random walk with drift
- Seasonal naïve forecast
- Linear autoregression
- Exponential smoothing
- DLinear
- A forecast based only on the last Close
- A model trained on returns rather than levels

The lack of a persistence baseline weakens statements about “forecasting ability,” although it does not invalidate the relative architecture comparison.

### Potential partition-overlap problem

Rolling forecasts at horizons 4 and 24 contain heavily overlapping targets.

For consecutive 24-step samples, 23 of the 24 target timestamps overlap. If sample rows are first constructed and then divided at a simple 70/15/15 index boundary, observations near the boundary can appear in the targets of both partitions.

The paper states that splits are chronological but does not document:

- Purge length
- Embargo length
- Whether windows are formed before or after splitting
- Whether overlapping target timestamps cross partition boundaries

A robust implementation should split the raw timeline first or purge at least the lookback and forecast overlap around each boundary.

### Cross-asset time representation

An “hourly” step does not represent the same amount of wall-clock time for all categories:

- Cryptocurrency is continuous.
- Forex has weekend closures.
- Equity indices have overnight and weekend gaps.
- Equity trading sessions vary by market and daylight-saving regime.

If the data simply treats consecutive available bars as consecutive hourly steps, then a 24-step forecast can represent:

- Approximately one calendar day for cryptocurrency
- More than one calendar day around a forex weekend
- Several trading sessions for an equity index

This complicates cross-category interpretation. The models may partly learn trading-session structure rather than a universal hourly process.

### OHLCV comparability

The study uses the same five feature labels for every asset class, but “Volume” is not economically equivalent across these markets:

- Cryptocurrency volume may be exchange-specific.
- Spot forex volume is often tick volume rather than consolidated traded volume.
- A cash equity index does not have directly traded volume in the same way an individual stock or futures contract does.

The paper should document the data source and precise economic definition of Volume for each instrument.

### LSTM result

LSTM errors are between approximately 7 and 33 times those of the best models.

Such a large gap may indicate a genuine architectural disadvantage, but it can also indicate:

- A poor configuration
- Inadequate optimisation
- A convergence failure
- A scaling or output-head issue
- A protocol that is especially unsuitable for recurrent models

The paper mentions convergence failures but still uses LSTM in the headline raw variance decomposition. This materially inflates the reported architecture share.

LSTM should be treated as a failed baseline implementation rather than definitive evidence that all recurrent models are intrinsically one or two orders of magnitude worse.

### Internal presentation inconsistencies

Several tables and figures appear inconsistent with their captions or surrounding discussion.

Examples include:

- Figure 13b on page 36 is described as Dow Jones, but the plot title contains `DEUIDXEUR`, which ordinarily refers to DAX.
- Figure 30 on page 55 is captioned as a percentage horizon-degradation heatmap across all assets excluding LSTM, but the visible matrix appears to show raw RMSE values for USD/JPY and includes an LSTM row.
- Figure 11 is described as global mean-rank complexity analysis, while the visible axes and titles appear to show forex mean RMSE for individual horizons.
- The EUR/USD degradation table on page 25 rounds all RMSE values to 0.00 or 0.01, making the displayed numbers practically uninformative.
- Some figure descriptions claim “directional fidelity” even though the formal directional-accuracy results are indistinguishable from 50%.

These issues do not automatically invalidate the underlying output files, but they reduce confidence in the manuscript's quality control. Results should be verified against the released CSV files before reuse.

## Overall assessment

The paper is useful as an architecture-screening study and as a template for organising a controlled machine-learning benchmark.

Its strongest contributions are:

- Comparing several important modern architectures in one pipeline
- Reporting multiple training seeds
- Freezing configurations at the category level
- Using chronological splits and training-only normalisation
- Reporting rank-based and pairwise statistical analysis
- Publishing detailed experimental artefacts
- Showing that DLinear remains competitive
- Demonstrating that ModernTCN and PatchTST are strong candidates for financial sequence modelling

Its central limitation is that it evaluates raw price-level prediction without a persistence baseline.

Because directional accuracy remains at 50%, the results should not be interpreted as evidence that ModernTCN or PatchTST produces tradable hourly alpha.

The most defensible conclusion is:

> Under this particular OHLCV price-level forecasting protocol, large-kernel temporal convolutions and patch-based Transformers minimise RMSE more reliably than the other tested architectures. The experiment does not establish economically useful return predictability.

## Suggestion on how to use the paper

### Use as an architecture shortlist

For a new financial sequence-model experiment, the paper supports the following initial shortlist:

- ModernTCN as the default nonlinear temporal model
- PatchTST as the main Transformer alternative
- DLinear as the low-complexity benchmark
- N-HiTS when multi-scale temporal behaviour is especially important

There is little reason to begin with Autoformer, TimesNet, or a conventional LSTM unless the research question specifically concerns their mechanisms.

### Use as a benchmark-design reference

The five-stage framework is useful:

- Common data preparation
- Controlled HPO budget
- Frozen configurations
- Multi-seed final training
- Rank-based statistical comparison

A stronger implementation should add:

- Persistence and random-walk baselines
- Purged chronological partitions
- Walk-forward testing
- Multiple time regimes
- Multiple HPO seeds
- Return- or residual-based targets
- Scale-free error metrics
- Economic backtests
- Transaction costs and turnover
- Proper dependence correction for overlapping forecasts

### Adapt it for equity-alpha research

For equity-alpha applications, do not directly copy the raw-price forecasting target.

More relevant targets include:

- Future excess return
- Industry-neutral residual return
- Cross-sectional return rank
- Probability of positive residual return
- Future volatility
- Future drawdown risk
- Fundamental surprise or revision response

A useful model comparison would be:

- DLinear
- ModernTCN
- PatchTST
- A simple linear factor model
- Gradient-boosted trees
- A last-value or zero-return baseline

Evaluate them using:

- Pearson IC
- Rank IC
- IC information ratio
- Top-minus-bottom portfolio return
- Turnover
- Transaction-cost-adjusted return
- Exposure neutrality
- Subperiod stability
- Incremental value beyond existing factors

### Possible BagelQuant experiment

The most directly reusable research design would be:

- Build a common sequence-model interface in `bagelquant-core`.
- Use ModernTCN, PatchTST, and DLinear as interchangeable model nodes.
- Feed each model identical lagged feature panels.
- Forecast one-month residual returns rather than raw prices.
- Freeze one hyperparameter configuration across a broad universe.
- Use purged walk-forward folds.
- Compare predictions using IC and portfolio results.
- Test whether nonlinear models add incremental information after controlling for traditional value, quality, investment, and momentum factors.

The key question should not be whether ModernTCN has lower price RMSE than PatchTST. It should be whether its signal provides stable incremental cross-sectional alpha after neutralisation and costs.

## Bottom line

This is a useful but not conclusive benchmark.

The ranking evidence is strong enough to justify testing ModernTCN and PatchTST before older recurrent or frequency-domain architectures.

The evidence is not strong enough to conclude that the models forecast economically useful hourly returns.

The paper is most valuable for model selection and experimental structure, not as direct evidence of a trading strategy.