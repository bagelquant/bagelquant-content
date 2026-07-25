---
layout: content
read: true
---
# The Effect of Analyst Forecasts during Earnings Announcements on Investor Responses to Reported Earnings

- PDF filename: `[alpha][analyst-revisions] 2017 - Lobo - Analyst Forecasts During Earnings Announcements.pdf`
- DOI: `10.2308/accr-51556`
- Journal: *The Accounting Review*, Volume 92, Issue 3, pages 239–263
- Publication date: May 2017
- Submitted: May 2014
- Accepted: August 2016

## Author information

- Gerald J. Lobo
  - University of Houston
- Minsup Song
  - Sogang University
- Mary Harris Stanford
  - Texas Christian University

## Key findings

- The market response to an earnings surprise depends strongly on whether analyst forecast revisions issued during the earnings announcement reinforce or contradict that surprise.

- A forecast revision is reinforcing when the direction of the revision agrees with the direction of unexpected earnings:
  - Positive earnings surprise with upward revisions
  - Negative earnings surprise with downward revisions

- A forecast revision is contradicting when the revision moves in the opposite direction:
  - Positive earnings surprise with downward revisions
  - Negative earnings surprise with upward revisions

- Earnings response coefficients are significantly larger when analyst revisions reinforce the earnings surprise and significantly smaller when revisions contradict it.

- In the full-sample regression, the incremental earnings response coefficient is:
  - $+0.2512$ for reinforcing revisions
  - $-0.2906$ for contradicting revisions
  - The difference is $0.5417$, with a $t$-statistic of $6.55$

- Among announcements that have concurrent analyst revisions, the estimated earnings response coefficient is:
  - $1.4898$ for reinforcing revisions
  - $0.9222$ for contradicting revisions

- The reinforcing-versus-contradicting distinction remains significant when comparing different announcements for the same firms, indicating that the result is not simply driven by persistent firm characteristics.

- Analyst forecast consensus strengthens the effect:
  - Both reinforcing and contradicting signals have greater price impact when pre-announcement forecast dispersion is low.
  - Investors place more weight on a revision signal when analysts broadly agree.

- Earnings persistence changes how investors interpret conflicting information:
  - High persistence strengthens the effect of reinforcing revisions.
  - High persistence reduces the negative effect of contradicting revisions.
  - Investors appear less willing to abandon a strong, persistent earnings signal because of a contradictory analyst revision.

- Analyst forecast revisions and management guidance provide complementary information.
  - The strongest market response occurs when both analysts and management reinforce the earnings surprise.
  - The market response becomes weaker when either source contradicts the earnings surprise.
  - It becomes weakest when both sources contradict it.

- The frequency of concurrent analyst revisions increased substantially over the sample:
  - 53% of earnings announcements had concurrent revisions in 1994.
  - 93% had concurrent revisions in 2014.

- The evidence supports the interpretation role of analysts rather than the pure piggyback hypothesis.
  - Analysts do not merely repeat information already contained in the earnings release.
  - Their immediate revisions help investors assess whether current earnings news is likely to persist into future earnings.

## Detail notes

### Research question

The paper asks whether analyst forecast revisions issued during an earnings announcement help investors interpret reported earnings.

The central question is not whether analyst revisions independently move prices. Instead, it is whether the stock-market response to unexpected earnings changes depending on the information contained in concurrent analyst revisions.

The paper therefore studies the interaction between:

- The current earnings surprise
- Revisions to forecasts of next year's earnings
- Management guidance issued at the same time

This differs from studies that treat an analyst revision as an independent information event.

### Economic intuition

An earnings surprise describes how current earnings differ from prior expectations, but it does not reveal whether the surprise is temporary or persistent.

Analysts can interpret the earnings release using:

- Segment information
- Management commentary
- Margins and cost developments
- Accrual composition
- Forward-looking disclosures
- Industry knowledge
- Private analytical models

An upward revision following positive unexpected earnings suggests that analysts believe the good news will persist.

A downward revision following positive unexpected earnings suggests that analysts interpret the surprise as temporary, low quality, or offset by negative forward-looking information.

The interaction between the two signals therefore contains information about expected earnings persistence.

### Unexpected earnings

Unexpected earnings are defined as:

$$
UE_{i,t}
=
\frac{
EPS^{Actual}_{i,t}
-
EPS^{PreAnnouncement}_{i,t}
}{
Price_{i,t}
}
$$

The pre-announcement expectation is the most recent analyst forecast for current-year EPS issued before the earnings announcement.

The measure is scaled by fiscal-year-end stock price.

See pages 243–244 and Appendix A.

### Analyst forecast revision

The analyst forecast revision measures the change in expected earnings for the following fiscal year:

$$
AFR_{i,t}
=
\overline{Forecast}^{[0,+1]}_{i,t+1}
-
\overline{Forecast}^{PreAnnouncement}_{i,t+1}
$$

where:

- $\overline{Forecast}^{[0,+1]}_{i,t+1}$ is the mean forecast for year $t+1$ issued on earnings-announcement day 0 or day $+1$.
- $\overline{Forecast}^{PreAnnouncement}_{i,t+1}$ is the mean year-$t+1$ forecast issued within the 30 days before the announcement.

See pages 243–244 and Appendix A.

### Reinforcing and contradicting classifications

A compact representation is:

$$
Consistency_{i,t}
=
\operatorname{sign}(UE_{i,t})
\times
\operatorname{sign}(AFR_{i,t})
$$

The revision is:

- Reinforcing when $Consistency_{i,t}>0$
- Contradicting when $Consistency_{i,t}<0$

The reference category in the main regression consists of earnings announcements without concurrent analyst forecast revisions.

### Return measure

The dependent variable is size-adjusted cumulative abnormal return over the four-day earnings-announcement window:

$$
CAR_{[-1,+2]}
$$

The window captures both:

- The earnings announcement on day 0
- Analyst revisions released on day 0 or day $+1$

The conclusions are similar using a three-day window ending on day $+1$.

See pages 244, 251, and the robustness discussion.

### Main regression

The primary specification is conceptually:

$$
CAR
=
\alpha
+
\beta_1 UE
+
\beta_2 ReinforcingAFR
+
\beta_3 ContradictingAFR
+
\beta_4 UE\times ReinforcingAFR
+
\beta_5 UE\times ContradictingAFR
+
Controls
+
\varepsilon
$$

The key coefficients are:

- $\beta_4>0$: reinforcing revisions increase the market response to unexpected earnings.
- $\beta_5<0$: contradicting revisions reduce the market response to unexpected earnings.

The model also interacts unexpected earnings with the control variables, allowing the earnings response coefficient to vary with firm and earnings characteristics.

Year fixed effects are included, and standard errors are clustered by firm.

See pages 244–245 and Table 3.

### Sample

The primary sample covers January 1994 through December 2014.

Data sources include:

- I/B/E/S detail data for analyst forecasts
- Compustat for earnings announcements and financial statement variables
- CRSP for stock returns
- First Call Company Issued Guidelines for management forecasts

The full sample contains 36,803 firm-year earnings announcements.

Sample composition:

- No concurrent analyst revision: 7,522 observations, or 20.4%
- Reinforcing revision: 16,830 observations, or 45.7%
- Contradicting revision: 12,451 observations, or 33.8%

Among observations with concurrent revisions, approximately 57% are reinforcing.

See pages 246–250 and Tables 1–2.

### Asymmetry by earnings-surprise direction

Approximately 65% of observations have positive unexpected earnings.

For positive surprises:

- 42% have reinforcing revisions.
- 39% have contradicting revisions.
- 19% have no concurrent revision.

For negative surprises:

- 54% have reinforcing revisions.
- 24% have contradicting revisions.
- 23% have no concurrent revision.

Analysts are therefore particularly likely to reinforce negative earnings surprises by revising future earnings downward.

See Tables 1 and 2.

### Main empirical results

In the full sample, the base earnings response coefficient for announcements without concurrent analyst revisions is $0.9936$.

Relative to that base:

$$
UE\times ReinforcingAFR=0.2512
$$

with a $t$-statistic of $3.09$.

For contradicting revisions:

$$
UE\times ContradictingAFR=-0.2906
$$

with a $t$-statistic of $-3.02$.

The difference between the reinforcing and contradicting coefficients is:

$$
0.2512-(-0.2906)=0.5417
$$

with a $t$-statistic of $6.55$.

See Table 3, Model 1.

### Within-firm evidence

The authors restrict the sample to firms that experience at least one reinforcing revision and one contradicting revision during the sample period.

The results remain similar:

- Reinforcing interaction: $0.2990$
- Contradicting interaction: $-0.2706$
- Difference: $0.5696$
- Difference $t$-statistic: $6.67$

This test is important because it compares different earnings announcements for the same broad set of firms.

The classification therefore reflects announcement-specific information rather than a permanent type of company.

See Table 3, Model 2.

### Announcements with analyst revisions only

The authors also exclude observations without analyst forecast revisions.

The estimated earnings response coefficients are:

$$
ERC^{Reinforcing}=1.4898
$$

and:

$$
ERC^{Contradicting}=0.9222
$$

The difference is $0.5676$, with a $t$-statistic of $6.51$.

This comparison reduces concern that the result is caused only by analysts choosing which earnings announcements deserve an immediate revision.

See Table 3, Model 3.

### Interpretation of the main result

The return response to an earnings surprise cannot be understood solely from the surprise itself.

A positive earnings surprise accompanied by downward forward-earnings revisions is materially weaker information than an identical positive surprise accompanied by upward revisions.

Similarly, a negative surprise accompanied by upward revisions is less damaging than a negative surprise followed by additional downward revisions.

The revision direction functions as an interpretation of the persistence and future implications of current earnings.

### Analyst forecast dispersion

Forecast dispersion is measured as the standard deviation of current-year analyst forecasts issued within 30 days before the earnings announcement, scaled by stock price.

The sample is divided each year into high- and low-dispersion groups.

For reinforcing revisions:

- Low-dispersion coefficient: $0.8403$
- High-dispersion coefficient: $0.2235$
- Difference: $0.6169$
- Difference $t$-statistic: $3.93$

For contradicting revisions:

- Low-dispersion coefficient: $-0.7581$
- High-dispersion coefficient: $-0.2250$
- Difference in magnitude: $0.5330$
- Difference $t$-statistic: $2.76$

Both confirming and conflicting revision signals matter more when analysts have greater consensus.

See pages 256–257 and Table 5, Panel A.

### Earnings persistence

Earnings persistence is estimated using:

$$
E_{j,t+1}
=
c_0
+
c_1E_{j,t}
+
\varepsilon_{j,t+1}
$$

The regression is estimated using up to five preceding years, with at least three observations required.

For reinforcing revisions:

- Low-persistence coefficient: $0.1586$
- High-persistence coefficient: $0.4288$
- Difference: $0.2703$
- Difference $t$-statistic: $4.18$

For contradicting revisions:

- Low-persistence coefficient: $-0.3601$
- High-persistence coefficient: $-0.1404$
- Difference: $0.2197$
- Difference $t$-statistic: $2.57$

When historical earnings are persistent, investors respond more strongly to confirming analyst revisions.

However, they respond less negatively to contradicting revisions, potentially because a single contradictory revision is less credible against a strong history of persistent earnings.

See pages 256–257 and Table 5, Panel B.

### Management forecasts

Management forecasts are classified using the same reinforcing-versus-contradicting framework.

A management forecast is reinforcing when its direction relative to pre-announcement analyst expectations agrees with the sign of unexpected earnings.

It is contradicting when the directions disagree.

The management forecast analysis uses data from 1996 through 2010.

For the point-estimate management-guidance sample, there are 4,762 observations.

Approximately:

- 43.6% have reinforcing management forecasts and reinforcing analyst revisions.
- 12.0% have reinforcing management forecasts and contradicting analyst revisions.
- 11.3% have contradicting management forecasts and reinforcing analyst revisions.
- 33.0% have contradicting management forecasts and contradicting analyst revisions.

Analyst and management signals agree in approximately 77% of the observations.

See Table 2, Panel E.

### Complementarity of analysts and management

The earnings response coefficient is highest when both analyst revisions and management forecasts reinforce unexpected earnings.

Using this group as the reference case, the incremental effects are:

- Reinforcing management forecast with contradicting analyst revision: $-1.6446$
- Contradicting management forecast with reinforcing analyst revision: $-0.9903$
- Both management and analysts contradicting: $-1.8914$

The results indicate that neither source completely replaces the other.

Analysts appear to contribute interpretation beyond management guidance, while management guidance provides information beyond analyst revisions.

See pages 253–255 and Table 4, Panel B.

### Trading volume and information content

Earnings announcements accompanied by analyst revisions have higher announcement-period trading volume than announcements without revisions.

The increase in trading volume over time is also stronger for announcements with concurrent revisions.

The paper interprets this as evidence that part of the historical increase in earnings-announcement information content may be associated with the increasing frequency of immediate analyst interpretation.

See pages 246–250 and Table 1.

### Relation to the piggyback hypothesis

The piggyback hypothesis argues that analysts merely repeat or repackage public corporate news without adding useful information.

Under a strict piggyback interpretation, the earnings response coefficient should not systematically differ between reinforcing and contradicting revisions.

The observed differences imply that the content of the analyst revision affects how investors price the earnings surprise.

The paper therefore concludes that analysts perform a valuable interpretation role even when the revision follows immediately after a public disclosure.

### Robustness tests

The main conclusions remain under several alternative specifications.

#### Alternative return windows

Results are similar using:

- Four-day abnormal returns from day $-1$ through day $+2$
- Three-day abnormal returns from day $-1$ through day $+1$

#### Continuous revision measures

The results are similar when continuous analyst forecast revisions are used instead of reinforcing and contradicting indicator variables.

#### Same-firm sample

The conclusions remain when the sample is restricted to firms that experience both reinforcing and contradicting revisions.

#### Positive and negative earnings surprises

The reinforcing-versus-contradicting difference remains for both positive and negative unexpected earnings.

#### Forecast-timestamp errors

Because some I/B/E/S forecast dates may be delayed or inaccurate, the authors repeat the analysis over 2003–2014, when timestamp errors are considered less severe.

The conclusions remain unchanged.

#### Falsification test

The authors construct a forecast measure using information available before the earnings announcement.

Because this measure cannot incorporate interpretation of the newly released earnings, it should not produce the same reinforcing-versus-contradicting result.

The falsification measure does not generate a significant difference between reinforcing and contradicting groups.

This supports the interpretation that the main result comes from information incorporated during the announcement period.

#### Unexpected-earnings measurement error

The authors add pre-announcement stock returns and alternative controls to test whether measurement error in unexpected earnings explains the interaction effects.

The reinforcing and contradicting coefficients remain stable.

#### Self-selection

Analyst and management decisions to issue concurrent forecasts may not be random.

The paper addresses this using:

- Heckman two-stage selection models
- Propensity-score matching
- Samples restricted to announcements with analyst revisions
- Within-firm comparisons

The primary conclusions remain.

See pages 257–259.

## Strengths

- The paper focuses on the interaction between two information signals rather than treating analyst revisions as isolated events.

- The reinforcing-versus-contradicting classification has a clear economic interpretation related to earnings persistence.

- The large sample covers more than two decades and contains over 36,000 earnings announcements.

- The analysis includes same-firm comparisons, reducing concern that reinforcing and contradicting observations represent fundamentally different types of companies.

- Results are robust to several treatments of selection, measurement error, timestamp problems, and return-window definitions.

- The management-guidance analysis shows that analyst information is incremental to a major competing source of forward-looking information.

- The dispersion and persistence results provide economically meaningful conditioning variables rather than merely documenting an average effect.

## Limitations

- The paper studies market reactions around the announcement rather than directly testing a tradable long-horizon return strategy.

- Analyst revisions are included inside the return measurement window, so the design does not cleanly separate the price response to reported earnings from the later response to the analyst revision.

- The primary classification uses the sign of the consensus revision and discards much of the information in revision magnitude.

- Averaging analyst forecasts can conceal disagreement across individual analysts.

- The sample uses annual earnings announcements and annual EPS forecasts. Results may differ for quarterly forecasts, shorter forecast horizons, or non-EPS measures.

- The sample ends in 2014. Analyst behavior, disclosure practices, machine-readable earnings releases, and market reaction speeds may have changed since then.

- The management-guidance sample ends in 2010 and requires sufficiently precise guidance to classify the direction of the management signal.

- The use of the most recent pre-announcement analyst forecast as the earnings expectation may introduce staleness or analyst-specific measurement error.

- Forecast dispersion is based on forecast levels before the announcement. It does not directly measure agreement in the announcement-period revision directions.

- The paper demonstrates information content but does not establish that investors could trade on the analyst revisions before the documented price response is completed.

## Suggestion on how to use the paper

### Core alpha interpretation

The paper suggests that earnings surprise and analyst revision direction should not be modeled as independent additive signals.

The economically relevant feature is their interaction:

$$
Reinforcement_{i,t}
=
\operatorname{sign}(EarningsSurprise_{i,t})
\times
RevisionSignal_{i,t}
$$

A positive value indicates that revisions confirm the earnings news.

A negative value indicates that revisions contradict it.

This interaction can distinguish four economically different states:

| Earnings surprise | Analyst revisions | Interpretation |
|---|---|---|
| Positive | Upward | Strong positive continuation signal |
| Positive | Downward | Positive current news but weak future implications |
| Negative | Downward | Strong negative continuation signal |
| Negative | Upward | Negative current news but possible temporary weakness |

The paper is therefore most useful as support for a conditional earnings-revision alpha rather than a standalone earnings-surprise or revision-count factor.

### Count-based construction

When only analyst revision counts are available, define:

$$
NetRevisionCount_{i,t}
=
\frac{
N^{Up}_{i,t}-N^{Down}_{i,t}
}{
N^{Up}_{i,t}+N^{Down}_{i,t}
}
$$

Then construct:

$$
ReinforcementScore_{i,t}
=
\operatorname{sign}(EarningsSurprise_{i,t})
\times
NetRevisionCount_{i,t}
$$

Interpretation:

- Large positive values indicate broad analyst confirmation of the earnings surprise.
- Values near zero indicate weak or divided analyst interpretation.
- Large negative values indicate broad contradiction of the earnings surprise.

A signed directional alpha can retain the direction of the earnings news:

$$
ConditionalEarningsAlpha_{i,t}
=
\operatorname{sign}(EarningsSurprise_{i,t})
\times
f(ReinforcementScore_{i,t})
$$

where $f(\cdot)$ increases the signal magnitude when reinforcement is strong and shrinks it when analysts contradict the announcement.

### Consensus adjustment

The dispersion result suggests separating revision direction from confidence.

Using revision counts, define revision agreement as:

$$
RevisionAgreement_{i,t}
=
\frac{
\left|N^{Up}_{i,t}-N^{Down}_{i,t}\right|
}{
N^{Up}_{i,t}+N^{Down}_{i,t}
}
$$

Then:

$$
ConsensusAdjustedReinforcement_{i,t}
=
ReinforcementScore_{i,t}
\times
RevisionAgreement_{i,t}
$$

This gives more weight to cases in which analysts broadly agree and less weight to mixed revision waves.

Another useful representation is:

$$
DirectionalBreadth_{i,t}
=
\frac{N^{Up}_{i,t}-N^{Down}_{i,t}}
{\max(1,N^{Total}_{i,t})}
$$

This retains information about both direction and the breadth of participation.

### Revision activity

The paper requires an announcement-period revision to exist, but revision activity itself may contain information.

A count-based signal can distinguish:

- No revision response
- Low analyst participation
- Broad analyst participation
- Broad and directionally consistent participation

A possible interaction is:

$$
Alpha_{i,t}
=
EarningsDirection_{i,t}
\times
ReinforcementStrength_{i,t}
\times
g(RevisionCount_{i,t})
$$

where $g(\cdot)$ increases slowly with the number of analysts revising, rather than allowing a few revisions to receive the same confidence as a broad revision wave.

### Persistence conditioning

The earnings-persistence result suggests conditioning the interaction on an estimate of earnings quality.

Possible persistence proxies include:

- Historical EPS autocorrelation
- Stability of operating margins
- Fraction of earnings attributable to recurring operations
- Accrual intensity
- Frequency of special items
- Historical relationship between earnings surprises and subsequent revisions
- Agreement between FY1 and FY2 revision directions

For persistent firms, a reinforcing revision can receive greater weight.

A contradicting revision should not necessarily fully reverse the earnings signal when the firm's historical earnings process is highly persistent.

### Management-guidance interaction

When management guidance is available, construct a second consistency signal:

$$
ManagementConsistency_{i,t}
=
\operatorname{sign}(EarningsSurprise_{i,t})
\times
\operatorname{sign}(GuidanceRevision_{i,t})
$$

The strongest signal should occur when:

$$
AnalystConsistency_{i,t}>0
$$

and:

$$
ManagementConsistency_{i,t}>0
$$

Mixed analyst-management signals represent uncertainty rather than a clean directional state.

A useful categorical feature is:

- Both reinforce
- Analysts reinforce, management contradicts
- Management reinforces, analysts contradict
- Both contradict

### Forecast-horizon variants

The paper uses revisions to year-$t+1$ annual earnings, which are explicitly forward-looking.

Related variants include:

- Current fiscal-year surprise versus FY1 revisions
- Current fiscal-year surprise versus FY2 revisions
- FY1 and FY2 revisions in the same direction
- FY1 revision reinforced by a change in long-term growth forecasts
- Near-term reinforcement but long-term contradiction
- Long-term reinforcement despite a temporary current-period miss

The disagreement between revision horizons may identify whether analysts view the earnings news as temporary or structural.

### Magnitude and breadth decomposition

When both forecast values and revision counts are available, separate:

$$
RevisionMagnitude
$$

from:

$$
RevisionBreadth
$$

A large consensus revision supported by many analysts is economically different from a large revision driven by one analyst.

Potential components are:

- Mean or median revision magnitude
- Net revision count
- Fraction of analysts revising
- Cross-analyst revision dispersion
- Concentration of revisions among historically accurate analysts
- Agreement across forecast horizons

### Most useful takeaway

The paper's most important alpha insight is:

> An earnings surprise should be interpreted jointly with the direction and consensus of subsequent analyst revisions.

A positive surprise is not uniformly positive, and a negative surprise is not uniformly negative.

The expected persistence of the news is better captured by whether analysts revise future earnings in the same direction, how broadly they agree, and whether management guidance provides the same forward-looking message.