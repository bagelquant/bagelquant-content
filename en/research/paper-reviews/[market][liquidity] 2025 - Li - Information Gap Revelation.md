---
layout: content
title: "Learning Your Neglect: Information Gap Revelation and Market Liquidity"
tags:
  - market
  - liquidity
read: false
---
# Learning Your Neglect: Information Gap Revelation and Market Liquidity

- DOI: 10.2139/ssrn.5965374
- Status: SSRN working paper
- Date written: November 30, 2025
- JEL classification: G14, G18, G41
- Primary tags: `[market][liquidity]`

## Author information

- Lu Li — Southwestern University of Finance and Economics
- Xuefeng Rong — Chinese University of Hong Kong, Shenzhen; contact author
- Yongxin Xu — Monash University
- Gaoping Zheng — RMIT University

## Key findings

The paper studies what happens when retail investors are explicitly redirected to public information that was already available but that they had previously overlooked.

The central result is counterintuitive:

> Making neglected information easier to find reduces market liquidity because investors recognize that they are informationally disadvantaged and trade less.

Following mandatory investor–firm interaction events in China:

- Trading volume decreases.
- Stock turnover decreases.
- Amihud price impact increases.
- Bid–ask spreads widen.
- Return volatility decreases.
- Retail investors execute fewer buys and sells.
- Measures of investor disagreement do not change significantly.
- Prices react again to earnings information that had been disclosed before the interaction.

The evidence is consistent with a reduction in retail noise trading rather than convergence in investors’ fundamental beliefs.

The paper therefore highlights a trade-off:

- Information-gap revelation improves price discovery.
- The same revelation reduces liquidity by discouraging uninformed trading.

The effects are substantially stronger when:

- A larger proportion of investor questions concerns information that was previously disclosed.
- Analyst coverage is low.
- Investors face higher information-awareness and information-acquisition costs.

For quantitative investment research, the paper is more directly useful for liquidity forecasting, transaction-cost modelling, retail-flow regime identification, and event-driven information-reactivation signals than as a standalone medium-horizon return alpha.

## Detail notes

### Research question

The paper distinguishes three types of information interventions:

- Providing genuinely new information.
- Helping investors understand or integrate complicated information.
- Revealing that investors failed to notice information that was already public.

The third intervention is called **information gap revelation**.

Its liquidity effect is theoretically ambiguous.

Information access could increase liquidity if it:

- Draws investor attention to trading opportunities.
- Reduces information asymmetry.
- Encourages investors to trade on a more complete information set.

Alternatively, it could reduce liquidity if investors realize that:

- They had been trading with incomplete information.
- Other market participants may be better informed.
- Their perceived trading edge was illusory.
- Continuing to trade aggressively is unlikely to be profitable.

The paper argues that the second mechanism dominates in its institutional setting.

### Institutional setting

The study uses mandatory online investor-interaction events organized by local offices of the China Securities Regulatory Commission.

The first event occurred in Ningxia in 2008. By 2018, all 36 local CSRC offices had organized an event.

Important characteristics of the setting include:

- Event timing is determined by regional CSRC offices rather than listed firms.
- Local listed firms are required to participate.
- The interaction lasts approximately two to three hours.
- Firms receive an average of 106.7 questions and provide 62 replies.
- Firms are prohibited from disclosing material information that has not already been formally announced.
- CSRC officers monitor the sessions.
- Questions and answers remain publicly available after the event.
- Institutional investors rarely participate; the events are primarily directed toward retail investors.

Because firms face many questions within a short period, their answers usually redirect investors to earlier announcements instead of providing detailed analytical explanations.

This feature helps separate information-awareness effects from new-information and information-integration effects.

### Nature of investor questions

The authors manually classify 13,093 questions, representing 10% of the complete set of 130,930 questions.

The classifications on Table 1, page 38, show:

| Question category | Percentage |
|---|---:|
| Previously disclosed but neglected information | 85.16% |
| Undisclosed information | 5.11% |
| Inappropriate investment questions | 4.78% |
| Suggestions or comments | 2.47% |
| Correcting misunderstandings | 1.66% |
| Rumor verification | 0.82% |

The most frequent subject areas are:

- Products and business operations: 46.57%
- Corporate governance: 13.28%
- Stock trading: 10.14%
- Financial reports: 7.26%
- Asset restructuring: 3.77%

The very high proportion of questions concerning existing disclosures supports the paper’s interpretation of the events as information-gap revelation.

### Data and sample

The sample covers Chinese A-share listed companies.

The authors exclude:

- Financial companies.
- Special Treatment companies.
- Particular Transfer companies.

Data sources include:

- CSMAR for accounting information, returns, analyst coverage, and market data.
- CNRDS for media coverage and investor-forum discussions.
- Web-crawled investor questions and company responses.
- Account-level trading records from one retail brokerage for an additional Beijing-event test.

Continuous variables are winsorized at the 1st and 99th percentiles.

The full stacked sample contains:

- 1,252 unique treatment firms.
- 2,537 unique potential control firms.

After propensity-score matching, the principal sample contains:

- 1,133 treatment firms.
- 1,133 matched control firms.

### Treatment and control construction

The paper uses only the first mandatory interaction event in each region.

For each regional event:

- Treatment firms are listed firms located in the region organizing the event.
- Control firms are located in regions without an interaction event during the six months before or after the treatment event.

The authors conduct one-to-one nearest-neighbour propensity-score matching without replacement.

Matching variables include:

- Market capitalization.
- Book-to-market ratio.
- Asset growth.
- Return on assets.
- Earnings and material-event disclosures.
- Analyst coverage.
- Media coverage.
- Firm age.
- Return volatility.
- Historical ROA volatility.
- Institutional ownership.

The paper also estimates a regional Weibull hazard model. The tested firm-fundamental and information-environment variables do not significantly predict when a region initiates its first interaction event.

### Baseline empirical model

The principal specification is a stacked difference-in-differences model:

$$
Y_{itg}
=
\alpha_{ig}
+
\lambda_{tg}
+
\beta
\left(
TREAT_{ig}
\times
AFTER_{tg}
\right)
+
\Gamma^{\prime}X_{itg}
+
\varepsilon_{itg}
$$

where:

- $i$ identifies a firm.
- $t$ identifies a month.
- $g$ identifies a regional interaction event.
- $\alpha_{ig}$ is an event-by-firm fixed effect.
- $\lambda_{tg}$ is an event-by-month fixed effect.
- $TREAT$ identifies firms in the interaction region.
- $AFTER$ identifies post-event observations.

The main event window covers:

- Three months before the interaction.
- The interaction month.
- Three months after the interaction.

Standard errors are two-way clustered by event–firm and event–time.

The four principal liquidity outcomes are:

- `VOLUME`: logarithm of monthly RMB trading volume.
- `TURNOVER`: monthly shares traded divided by shares outstanding.
- `AMIHUD`: absolute return divided by trading volume.
- `BAS`: time-weighted bid–ask spread.

### Main liquidity results

Table 3, pages 40–41, reports the following controlled estimates:

| Outcome | $TREAT \times AFTER$ | Interpretation |
|---|---:|---|
| Log trading volume | -0.057 | Lower trading activity |
| Turnover | -0.041 | Lower share turnover |
| Amihud illiquidity | +0.003 | Greater price impact |
| Bid–ask spread | +0.003 | Wider spreads |

The log-volume coefficient corresponds to approximately:

$$
e^{-0.057}-1 \approx -5.5\%
$$

Therefore, the treatment is associated with roughly 5.5% lower trading volume.

The turnover coefficient of $-0.041$ is:

- Approximately 8.2% of the sample mean turnover of 0.499.
- Approximately 8.8% of the turnover standard deviation of 0.466.

The Amihud increase is approximately 4.8% of its sample mean, while the spread increase is approximately 1.7% of its sample mean.

The paper describes the volume and turnover effects as 5.27% and 8.80% relative to their respective standard deviations. These figures should not be confused with percentage changes in the original variables.

### Dynamic effects

The event-time results in Table 4, page 42, show:

- No statistically significant treatment–control differences during the two months immediately before the event.
- Liquidity deterioration begins during or after the interaction.
- The strongest and most consistent effects occur approximately one to two months after the event.
- Some effects remain detectable in the third post-event month.

For trading volume:

- Month 1: -0.053
- Month 2: -0.068
- Month 3: -0.050

For turnover:

- Month 1: -0.029
- Month 2: -0.049
- Month 3: -0.037

The absence of visible pre-trends supports the causal interpretation, although it does not eliminate all possible region-level confounding.

### Heterogeneity by neglected-information questions

The authors train a FinBERT classifier using the manually labelled questions and apply it to the remaining questions.

For each firm, they calculate:

$$
GapScore_i
=
\frac{\text{questions about neglected disclosed information}}
{\text{all investor questions}}
$$

Table 5, Panel A, pages 43–44, compares firms with high and low values of this measure.

For firms with high neglected-information question ratios:

- Volume coefficient: -0.088
- Turnover coefficient: -0.054
- Amihud coefficient: +0.007
- Bid–ask spread coefficient: +0.005

For firms with low ratios:

- Volume coefficient: -0.020 and insignificant.
- Turnover coefficient: -0.026 and insignificant.
- Amihud and spread effects are approximately zero.

This cross-sectional pattern is one of the paper’s strongest pieces of evidence for the proposed mechanism.

### Heterogeneity by analyst coverage

Table 5, Panel B, divides firms according to analyst coverage.

For low-coverage firms:

- Volume coefficient: -0.112
- Turnover coefficient: -0.065
- Amihud coefficient: +0.009
- Bid–ask spread coefficient: +0.005

For high-coverage firms, the estimates are small and statistically insignificant.

This indicates that information-gap revelation matters most when investors previously had fewer intermediaries helping them discover and process corporate information.

### Noise-trading channel

The paper uses two measures of return volatility:

- `VOL1`: standard deviation of daily stock returns.
- `VOL2`: standard deviation of residual returns from a daily Fama–French three-factor regression.

Table 6, page 45, finds lower volatility after the events.

Without controls:

- `VOL1`: -0.063, significant at the 5% level.
- `VOL2`: -0.057, significant at the 5% level.

With controls:

- `VOL1`: -0.053, significant only at the 10% level.
- `VOL2`: -0.049, significant only at the 10% level.

The volatility evidence is therefore supportive but weaker than the principal liquidity results.

The decline is stronger for:

- Firms with more neglected-information questions.
- Firms with lower analyst coverage.

The interpretation follows the Kyle framework: noise traders provide order flow that allows informed traders to trade without immediately revealing their information. When noise trading falls, market depth declines and price impact rises.

### Investor-disagreement channel

The paper examines four disagreement measures:

- Dispersion in bullish and bearish social-media posts.
- Dispersion in analyst earnings forecasts.
- Range of analyst earnings forecasts.
- Abnormal short interest.

Table 7, page 46, finds no statistically significant treatment effect for any measure.

The authors conclude that investors do not necessarily converge toward the same valuation.

Instead, investors may continue to disagree while becoming less confident that their own information is sufficient to trade profitably.

This distinction is important:

- Belief dispersion remains.
- Trading confidence falls.
- Trading activity consequently declines.

### Account-level retail trading

The authors obtain retail brokerage records surrounding the 2018 Beijing interaction event.

The account-level sample covers March to July 2018.

Table 8, page 47, reports:

| Retail activity measure | Post-event coefficient |
|---|---:|
| Number of buys | -0.133 |
| Number of sells | -0.104 |
| Total number of trades | -0.171 |
| Buy ratio | -0.014 |
| Sell ratio | -0.034 |
| Total trade ratio | -0.023 |

The total-trade coefficient implies an approximate log-to-level change of:

$$
e^{-0.171}-1 \approx -15.7\%
$$

The paper interprets it as a 17.1% decline by treating the log coefficient as a direct percentage effect.

Although this evidence comes from only one brokerage and one regional event, it directly supports the proposition that retail investors reduce trading after learning that they had overlooked relevant information.

### Firm-disclosure alternative

A potential alternative explanation is that firms respond to investor questions by changing their subsequent disclosure behaviour.

The paper tests:

- Number of corporate announcements.
- Total PDF file size of corporate announcements.

Appendix Table A7 finds no statistically significant post-event change in either measure.

The liquidity result therefore does not appear to be caused by firms issuing more disclosures after the interaction.

### Price discovery and earnings surprises

The paper tests whether interaction events cause prices to react to earnings information that had already been announced.

The test focuses on firms with an earnings announcement during the month before the interaction.

The dependent variable is daily market-adjusted return over a five-day window surrounding the interaction event.

The main specification includes:

$$
TREAT
\times
I\_DAY
\times
SUE
$$

where:

- $I\_DAY$ identifies the interaction day.
- $SUE$ is standardized unexpected earnings.

Table 9, pages 48–49, finds a positive triple-interaction coefficient of approximately 0.185.

This means that, relative to control firms, treatment firms’ event-day returns become more positively related to the sign and magnitude of their earlier earnings surprise.

Using the sample standard deviation of $SUE$, which is approximately 0.014, the estimate implies an event-day return difference of roughly:

$$
0.185 \times 0.014 \approx 0.0026
$$

or approximately 0.26 percentage points for a one-standard-deviation earnings surprise.

The result suggests that the interaction reactivates previously neglected earnings information.

This is potentially the most directly usable return-alpha implication of the paper.

### Interpretation

The paper presents liquidity and price efficiency as distinct market-quality dimensions.

Information-gap revelation can produce:

- Lower trading volume.
- Wider spreads.
- Greater price impact.
- Lower return noise.
- Faster incorporation of previously neglected information.

Thus, lower liquidity does not necessarily imply lower informational efficiency.

In this setting, some pre-event liquidity appears to be generated by uninformed or overconfident retail trading. Removing that trading reduces liquidity while making prices more responsive to fundamentals.

### Identification strengths

The paper has several notable strengths.

#### Institutionally constrained information content

Firms are prohibited from releasing new information during the events, helping isolate the effect of redirecting attention to existing disclosures.

#### Externally determined event timing

Regional CSRC offices, rather than listed firms, determine event timing.

This reduces concerns that firms strategically choose events immediately before expected changes in liquidity.

#### Stacked difference-in-differences design

The stacked design avoids some negative-weight and treatment-heterogeneity problems associated with conventional two-way fixed-effect staggered DID estimators.

#### Multiple liquidity measures

The result appears in:

- Trading volume.
- Turnover.
- Amihud price impact.
- Bid–ask spreads.

This reduces dependence on one imperfect liquidity proxy.

#### Mechanism triangulation

The paper combines:

- Question text.
- Analyst coverage.
- Return volatility.
- Social-media disagreement.
- Analyst disagreement.
- Retail brokerage records.
- Corporate disclosure data.
- Earnings-response tests.

The consistency of these separate analyses makes the central economic narrative plausible.

## Concerns and limitations

### Treatment is assigned at the regional level

The regulatory event occurs at the CSRC-region level, while the regression is performed at the firm-month level.

Firms within a treated region may share:

- Local economic shocks.
- Regional regulatory initiatives.
- Investor-education campaigns.
- Media coverage.
- Brokerage composition.
- Retail-investor behaviour.

The reported standard errors are clustered by event–firm and event–time, not explicitly by treatment region.

Because there are only 36 regions, inference could be sensitive to region-level dependence and a small number of treatment clusters.

A stronger design would report:

- Region-level clustering.
- Randomization inference at the regional-event level.
- Wild-cluster bootstrap p-values.
- Leave-one-region-out estimates.

### Event timing may coincide with broader regulatory activity

Although firms do not choose the event date, local regulators may schedule interaction events alongside other investor-protection or market-supervision initiatives.

The hazard model shows that selected observable variables do not predict event timing, but it cannot exclude unobserved regional policy shocks.

### FinBERT evaluation is not sufficiently informative

The model reports an out-of-sample accuracy of 85.7%.

However, 85.16% of manually classified questions already belong to the neglected-information category.

A classifier that labels every question as neglected information would therefore achieve approximately 85.16% accuracy.

The reported accuracy is only slightly above this majority-class benchmark.

The paper should additionally report:

- Precision.
- Recall.
- F1 score.
- Area under the ROC curve.
- Confusion matrix.
- Performance by class.
- Results using manually labelled firms only.

Without these statistics, the text-based heterogeneity measure is less convincing than the headline accuracy suggests.

### Return volatility is not a unique proxy for noise trading

Lower volatility can result from:

- Less noise trading.
- Resolution of uncertainty.
- Lower arrival of private information.
- Reduced investor attention.
- Changes in systematic risk.
- Temporary reductions in participation.

The cross-sectional and account-level evidence strengthens the noise-trading interpretation, but volatility alone does not identify the mechanism.

### Account-level specification requires clarification

The account-level regression is described as including:

- An `AFTER` indicator.
- Account fixed effects.
- Month fixed effects.

Because all observations cover the same five calendar months, `AFTER` is a deterministic function of calendar month.

With a complete set of month fixed effects, the `AFTER` coefficient should be perfectly collinear and therefore unidentified.

The paper should clarify whether:

- The reported time controls are not full calendar-month fixed effects.
- There is an omitted treatment–control interaction.
- The regression is actually estimated at an account–stock–month level.
- Some other source of cross-sectional variation identifies the coefficient.

Until clarified, Table 8 should be interpreted cautiously.

### Account-level evidence has limited external validity

The brokerage analysis covers:

- One brokerage.
- One regional event.
- Five months.

The investors may not be representative of the complete retail-investor population.

### Potential spillovers

The interaction questions and responses are public.

Investors in control regions may also view the events or alter their behaviour after observing a nearby regional event.

Such spillovers would violate strict no-interference assumptions and would probably attenuate the estimated treatment effects.

### Short post-event horizon

The main analysis ends three months after the event.

The paper does not establish whether:

- Liquidity eventually returns to its previous level.
- Investors permanently reduce trading.
- Investors improve their information-processing ability.
- Trading migrates toward other stocks.
- The welfare consequences persist.

### Price-discovery regression deserves further validation

Table 9 has very low adjusted $R^2$, around 1%.

Low explanatory power is common in daily-return regressions, but several reported coefficients appear large relative to the sample’s daily-return dispersion.

The result would benefit from:

- Portfolio-sorted event returns.
- Graphical cumulative abnormal returns.
- Alternative earnings-surprise definitions.
- Exclusion of firms with contemporaneous announcements.
- More conservative event- or region-level clustering.
- Placebo interaction dates.
- Intraday evidence showing when the prior information is incorporated.

### External validity

The Chinese market during the sample period had:

- Very high retail participation.
- Strong short-sale constraints.
- Distinctive disclosure institutions.
- Regionally administered securities regulation.

The direction of the effect may generalize to other retail-dominated markets, but the magnitude may be smaller in markets with greater analyst coverage and institutional participation.

## Suggestion on how to use the paper

### Liquidity and transaction-cost forecasting

The most immediate application is to treat information-gap-revelation events as negative liquidity shocks.

Construct an event score such as:

$$
IGR_{i,t}
=
Event_{i,t}
\times
GapScore_i
\times
LowCoverage_i
$$

where:

- `Event` identifies a mandatory or highly publicized investor-interaction event.
- `GapScore` measures how often responses redirect investors to prior disclosures.
- `LowCoverage` is high when analyst coverage is low.

Expected post-event effects are:

- Lower volume.
- Lower turnover.
- Wider spreads.
- Higher price impact.
- Lower retail order frequency.

Possible portfolio-construction uses include:

- Increase expected transaction-cost estimates for one to three months.
- Reduce position sizes in high-`IGR` stocks.
- Slow execution schedules.
- Increase rebalance thresholds.
- Avoid concentrating liquidity-demanding trades immediately after the event.
- Apply stronger liquidity constraints to low-coverage stocks.

The paper should not be used to infer that an event automatically produces a negative return. Its principal result concerns trading activity and market depth, not return direction.

### Event-driven earnings-reactivation alpha

The price-discovery result suggests a short-horizon signal based on the interaction between prior earnings surprise and information-gap revelation:

$$
Alpha_{i,t}
=
I(EventDay_{i,t})
\times
SUE_i
\times
GapScore_i
$$

Potential implementation:

- Long firms with positive recent earnings surprises on the interaction day.
- Short firms with negative recent earnings surprises.
- Scale exposure by the proportion of questions that redirect investors to neglected disclosures.
- Give greater weight to low-analyst-coverage and retail-dominated stocks.
- Hold for the interaction day or a very short post-event window.

The critical test is whether the interaction event produces incremental returns beyond ordinary post-earnings-announcement drift.

The backtest should control for:

- Earnings-announcement age.
- Standard PEAD factors.
- Momentum.
- Size.
- Turnover.
- Analyst coverage.
- Other event-day announcements.
- Daily limit moves.
- Trading suspensions.
- Realistic intraday availability of Q&A text.

### Text-based neglected-information signal

A practical NLP pipeline could classify each investor question and company response into:

- New information request.
- Reference to an existing disclosure.
- Request for interpretation.
- Rumor verification.
- Corporate-governance concern.
- Product or operational question.
- Investment recommendation request.

A stronger measure than the paper’s simple question ratio would compare the response with the complete historical disclosure archive.

For example:

$$
NeglectScore_{q}
=
Similarity(Response_q, PriorDisclosures)
\times
Age(PriorDisclosure_q)
\times
Materiality(PriorDisclosure_q)
$$

Firm-level scores could aggregate:

- Number of neglected-information questions.
- Materiality of the referenced information.
- Age of the information.
- Investor engagement with each question.
- Whether the neglected information concerns earnings, guidance, restructuring, or governance.
- Whether prices had previously underreacted to the information.

This may identify both:

- Future liquidity reductions.
- Short-horizon reactivation of stale fundamental information.

### Retail-noise regime filter

The paper implies that retail participation can be endogenous to investors’ perception of their informational competence.

After a strong information-gap event, signals that depend on retail noise may weaken.

Examples include:

- Lottery-demand signals.
- Attention-driven buying.
- Retail order-imbalance continuation.
- High-turnover reversals.
- Social-media sentiment.
- Abnormal small-trade activity.

An `IGR` score could be used as a regime interaction:

$$
ExpectedAlpha_{i,t}
=
BaseRetailAlpha_{i,t}
\times
\left(1-\gamma IGR_{i,t}\right)
$$

The hypothesis is that a retail-flow alpha has lower strength after investors recognize their information disadvantage.

### Volatility forecasting

The results suggest a short-run reduction in realized and idiosyncratic volatility following high-gap events.

The event score could be added to a volatility forecast:

$$
\widehat{\sigma}_{i,t+1}
=
f(
\sigma_{i,t},
Volume_{i,t},
Spread_{i,t},
RetailFlow_{i,t},
IGR_{i,t}
)
$$

Because volatility is only an indirect noise-trading measure, this application should be validated using:

- Intraday variance.
- Realized volatility.
- Jump variation.
- Retail trade imbalance.
- Order cancellation rates.
- Quote depth.
- Price impact by trade size.

### Improved replication design

A robust replication should:

- Use exact event timestamps.
- Separate firms that answered many questions from firms with little participation.
- Identify the particular prior disclosure referenced in each response.
- Measure whether the referenced information was already incorporated into prices.
- Cluster inference at the CSRC-region or event level.
- Use randomization inference across regional event dates.
- Test for spillovers to firms in nearby regions.
- Examine one-, three-, six-, and twelve-month liquidity effects.
- Use intraday transaction and order-book data.
- Compare retail and institutional order flow.
- Exclude contemporaneous firm announcements.
- Report precision, recall, and F1 for the text classifier.
- Validate the account-level regression with a clear treatment–control interaction.

### Data requirements

A practical implementation would require:

- Investor Q&A text and timestamps.
- Company responses.
- Historical corporate disclosures.
- Earnings-announcement dates and earnings surprises.
- Analyst coverage.
- Media coverage.
- Retail ownership or small-trade proxies.
- Daily or intraday turnover.
- Bid–ask spreads.
- Order-book depth.
- Price impact.
- Trading suspensions and price-limit information.

### Overall research value

The paper provides a valuable distinction between:

- Improving access to information.
- Improving understanding of information.
- Revealing that an investor had previously missed information.

The first two can encourage participation or reduce information asymmetry. The third can reduce confidence and deter trading.

For quantitative research, its main value is the proposition that investor-information interventions can forecast changes in market participation and execution conditions.

The return-alpha implication is narrower but potentially interesting: previously disclosed fundamental information may become price-relevant again when an event explicitly directs investor attention back to it.

The main liquidity result is credible and economically coherent. The proposed noise-trading mechanism is plausible but not fully identified, particularly because of the weak classifier evaluation, regional treatment assignment, and the apparent fixed-effect collinearity in the account-level analysis.