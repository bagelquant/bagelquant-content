---
read: true
layout: content
---

# Smart Money, Dumb Money, and Capital Market Anomalies

- DOI: 10.1016/j.jfineco.2015.07.003
- Authors: Ferhat Akbas, Will J. Armstrong, Sorin Sorescu, Avanidhar Subrahmanyam

## Key finds

- Aggregate mutual fund flows (“dumb money”) exacerbate cross-sectional mispricing in US equities, especially in growth, momentum, and accrual anomalies.
- Hedge fund flows (“smart money”) attenuate mispricing, primarily through short positions in overvalued stocks.
- Mispricing exacerbation by mutual funds occurs mainly via new investments rather than redemptions.
- Effects are stronger when mutual/hedge funds have larger market shares.
- Retail investor flows are the primary source of dumb money.
- Economic conditions (e.g., Internet bubble run-up) amplify the effects of mutual fund flows on mispricing.
- Hedge fund flows act intentionally and correct mispricing but do not reverse afterward; mutual fund-induced mispricing tends to revert in 1–3 months.
- De-trended and orthogonalized analyses confirm robustness; unexpected fund flows drive effects rather than predictable components.

## Detail notes

- **Measurement**:
  - Mispricing proxy: long–short portfolios based on 11 anomalies from Stambaugh, Yu, and Yuan (2012).
  - Mutual fund flows: CRSP Survivor-Bias-Free US Mutual Fund Database.
  - Hedge fund flows: Lipper TASS database (US equity-focused).
  - Controls: liquidity (AGGILLIQ, AGGTURN), Fama-French three factors (RMRF, HML, SMB), market trends, sentiment, VIX.
- **Methodology**:
  - Time-series regressions of long-short returns on fund flows with controls.
  - Decomposition of mutual fund flows into new investment, reinvestment, other inflows, redemptions using SEC N-SAR data.
  - Composite mispricing measures by grouping anomalies (growth/momentum/accrual vs. real investment; old vs. new).
  - Orthogonalization and de-trending to handle trends and autocorrelations.
- **Empirical insights**:
  - Mutual fund inflows disproportionately target overvalued growth/accrual stocks (short leg), causing mispricing.
  - Hedge funds exploit these temporary mispricing opportunities, predominantly via short positions in overvalued stocks.
  - Flows to real investment anomalies are largely unaffected.
  - Residual fund flows (unexpected deviations) have stronger effects than predicted flows.
  - Interaction with market share shows larger effect sizes when fund industry share is higher.

## Suggestion on how to use the paper (based on the tag area)

- **[alpha][flow]**: Use the results to identify periods when “dumb money” inflows likely distort cross-sectional returns, creating arbitrage opportunities for systematic alpha strategies.
- Incorporate hedge fund flow proxies as potential indicators of mispricing correction for timing short positions in overvalued stocks.
- For factor research, consider separating growth/accrual vs. real investment anomalies when assessing the impact of aggregate flows.
- Useful for building predictive signals in equity alpha models that exploit temporary price pressure from mutual fund flows.
- The methodology provides a template for quantifying smart vs. dumb money impact in other markets or asset classes.