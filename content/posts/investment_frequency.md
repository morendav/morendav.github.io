---
title: "Does Investment Frequency Matter?"
date: 2025-01-04T20:34:48-08:00
draft: false # until false then posted to production
author: "D.Moreno"
description: "This blog post explores whether investment frequency (yearly, monthly, etc) has any effect on portfolio performance."
tags: [
  "Finance",
  "Case Study",
]
ShowToc: true
ShowBreadCrumbs: true
math : true


## including a cover image
# cover:
#   image: "<image path/url>"   # as static content
#   image: https://i.ibb.co/K0HVPBd/paper-mod-profilemode.png  # as a url
#   alt: "<alt text>"
#   caption: "<text>"
---


Given two investors: one investing all of their annual target investment in January, and the other investing at some subannual frequency (e.g. monthly, quarterly, etc), which one wins at the end of the investments’ time-horizon?

<!--more-->



# :pushpin: TL;DR

When it comes to investing either all upfront (front-loading) or distributing across the year (monthly, quarterly, biannually), historical data suggests that front-loading is the winning strategy.
- This is true for market indexes (e.g. SP500)
- This is also true for high volatility assets (e.g. High Beta indexes and Bitcoin)


## Lessons / Key takeaways

<table>
  <tr>
   <td>
<strong>Front-loading beats more frequent investing </strong>
   </td>
   <td>
<ul>

<li>Historically, frontloading investments is most likely to beat all other subannual investment frequencies (i.e. investing monthly, quarterly, biannually)</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Investment time-horizon matters</strong>
   </td>
   <td>
<ul>

<li>Comparing Yearly (front-loading) vs frequent investing (e.g. monthly, etc) - Short-term investing results in a wider range of possible outcomes</li>

<li>Yearly (front-loading) is still the most likely to be the winning strategy in short-term time horizons</li>

<li>All assets converge on yearly (front-loading) investing being the winning strategy  in longer time-horizons</li>

<li>High-Beta assets have a wider range of possible outcomes in short-term time horizons</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Capital Asset Pricing Model</strong>
   </td>
   <td>
<ul>

<li>Canonical financial model that describes the relationship between asset risk (market volatility correlation) and asset price, asserting investors demand returns commensurate to assumed risk</li>

<li>Key assumptions of the model are efficient markets, and accessibility of risk-free assets to market participants</li>

<li>Data suggests front-loading strategy outperforms in near and long term for Beta >= 1 assets (negative and &lt;1 beta assets are not explored)</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>The “best” strategy is the one that gets investors participating</strong>
   </td>
   <td>
<ul>

<li>Front-loading is the most likely strategy to lead to higher returns over all timeframes explored, despite this, it may not be for everyone</li>

<li>The “best” strategy is the one that meets the investor’s risk tolerance</li>

<li>Frequent distributions may shelter a portfolio from market volatility, which could appeal to some investors who are sensitive to loses</li>
</ul>
   </td>
  </tr>
</table>



# Intro

> Disclaimer: Not financial advice. Previous performance does not translate to future returns. This blog post ignores all other considerations (e.g. tax implications, etc),  etc.

The inspiration for this blog post comes from a debate I had with a colleague, credit due to you (you know who you are)... I'll admit it... you were right.

The debate was quite simple: If you plan to invest $X in a year, is it better to front-load your investment at the beginning of the year or spread it out throughout the entire year? For example, many employers offer 401k matching - is it better to attempt to draw from this match earlier in the year or does that not matter at all?

Initially, my intuition was to stick to distributed investments: after all this shields your investment from market risk and volatility. Basically, my intuition was that claiming that it was better to frontload was to say "I can time the market". My wise colleague corrected the claim, it wasn't about market timing, instead it was ‘time in market’ that mattered. They were right.


## Comparing strategies

The question we're trying to answer here is which investor's portfolio has greater value over some time period T: 

1. An investor that always invests on the first trading day of the year

2. An investor that spreads their yearly investment across the first trading day of every month, every year

Holding constant:

* The number of years both investors invest

* The total yearly investment amount (so that the yearly and monthly investors both invest $X per year)

For simplicity we will make a few assumptions, at least initially:

1. The investors are investing in a broad basket index fund

2. The investors aren't using a sophisticated strategy (they are not a hedge fund, they are a "set it and forget it" investor)

3. Long timeline investors (e.g. those investing for retirement)

4. The investors ignore all macro-economic trends, meaning neither is trying to time entry/exit

5. All investors aren't counting on withdrawing any money from their investments until the term of their investment time-horizon


## Time in market >> derisking volatility

The canonical broad basket index, the SP500, has had positive yearly returns for between 70-75% of years in the last 100 years, depending on the specific data source and time period analyzed. Given this, early entrance is likely to have an annual payout roughly 7 out of every 10 years the investor invests in the first month.

Over the lifetime of an investment, the arithmetic on the gains vs loses work out to a question of how:

A. Gains made on the winning years (7 out of 10 odds that any given year is a winner), are balanced against

B. Losses realized on losing years (3 out of 10 odds that any given year is a losing year)

What this means is that our _Invest in January_ investor's entry in that first month of the year is likely (70%+) to be a winning strategy on a yearly basis.

The math is complicated by compounding growth, both because some broad basket indexes pay dividends, which may be reinvested, but also by capital appreciation overtime. For example, compounding growth over 7 years would need to be wiped out in the following 3 years in a toy example of a 10 year investment period where the first 7 years were bull markets followed by 3 years of bear markets. It's also complicated by some evidence that macro-trends may [influence the frequency and duration of bull and bear markets](https://www.schwab.com/learn/story/is-two-year-old-bull-market-2-legit-2-quit).


## What about riskier assets?

Given all of this, it seems that the portfolio shock insulation that monthly investing provides may not outperform the 'time in market' strategy. Perhaps the former outshines when we compare portfolios that hold assets with more volatility?

A key assumption for our investors here is that they are trading in a broad basket index, the SP500, which is a proxy for the market as a whole. Formally, we would say the SP500 and the market exhibit _perfect positive correlation_, and this formulation leads us to the canonical model for asset price and risk relationship.

This equation should provide us the criteria to select assets that do not conform to assumption 1: "investors invest in broad basket index"


# Capital Asset Pricing Model (CAPM) & Asset Volatility

American Economists William Sharpe, John Lintner, and Jan Mossin are credited for building the Capital Asset Pricing Model (CAPM), building upon earlier work of Harry Markowitz on portfolio optimization.

CAPM is based on the idea that investors demand a premium for bearing risk, and that this premium should be proportional to the amount of risk taken. It provides a simple way to estimate the expected return for an asset based on its risk relative to the overall market.   

CAPM Formula:

$E(R_i) = R_f + \beta_i (E(R_m) - R_f) + \alpha_i$

Where:

- $E(R_i)$ is the expected return on asset i
- $R_f$ is the risk-free rate of return
- $β_i$ is the beta of asset i, a measure of its volatility relative to the market  
- $E(R_m)$ is the expected return on the market portfolio
- $\alpha_i$ is an "error term"

In practice, the risk-free rate is often estimated using the yield on long-term government bonds, while the expected market return is typically based on historical averages or analyst forecasts. The beta of an asset can be calculated using statistical methods to measure its historical volatility relative to a broad market index, here is where our S&P500 index comes in.   

It's worth calling out here that CAPM relies on several simplifying assumptions, remarkably:

- Existence of a perfectly efficient market

- The ability of investors to borrow and lend at a risk-free rate

In reality, these assumptions may not always hold true, particularly in unregulated markets. Additionally, the CAPM may not be as accurate in predicting the returns for certain types of assets, such as those with high idiosyncratic risk (diversifiable risk) or those that are not publicly traded.

The error term, alpha, may represent inefficiencies in the market. It is also the object of exploitation by hedge funds and sophisticated investors who 'seek alpha'.


## CAPM For Assumption #1

Assumption 1 restated with CAPM terms is that we want to initially test with an asset whose $\beta_i = 1$.

This is achieved by using SP500 index. 

Then, what we want to test is whether the 'insulate portfolio' strategy (i.e. monthly investing) might be better for 'riskier' assets, meaning we will want to analyze historical data for high- beta assets, $\beta_i >> 1$.


# Case Study

This case study is hosted on [GitHub](https://github.com/morendav/investing_frequency_simulations/tree/main), and has a [companion notebook](https://colab.research.google.com/drive/1P9ZRZBKjLKQl9oPPqi5ifP9EJa6jw9F4?usp=sharing) you can play with here.


Summary of observations:

- For the SP500

   - The investor that invests in January outperforms the monthly, quarterly, and biannual investor over the long term (30yr term)

   - Short-term investing produces a wider range of outcomes (yearly vs sub-annual investing), but the data suggests that January Investing is still more likely to outperform sub-annual investing

   - The data suggests that of the sub-annual investing strategies: Monthly outperforms Quarterly, and Quarterly outperforms biannual investing.

       - This is likely an outcome of the case study’s implementation because the quarterly investor starts on month 3, biannual on month 6, and monthly on month 1.

       - In other words, quarterly misses investing in months [1, 2]. This supports the hypothesis that time in the market is a source of investment performance.

- For high Beta assets

   - We see the same outcomes as the SP500 (yearly > monthly > quarterly > biannual performance)

   - There is a wider range of observed outcomes when we look at short-term investing

- For Bitcoin

   - We see the same outcomes as the SP500


## Methods

The case study is written in Python, and makes use of the Yahoo Finance api to fetch historical asset prices over a date range. For the purposes of this case study we're only going to look at the opening price, and ignore intraday fluctuations.

The case study seeks to answer the question of which investor's portfolio has greater value over some shared investment time window. This will be calculated as a the ratio of portfolio values:

$Ratio = Portfolio(yearly) / Portfolio(subannual)$


Such that a ratio of >1 indicates that the yearly investor has beat the sub-annual investor. The portfolios will differ on their investment frequencies:

- Yearly investors will always invest the whole amount on the first trading day of the year, approximately Jan 2nd of every year because markets are closed on New Years every year.

- Subannual is any frequency that doesn't leave remaining months without investing, in other words: 12 % N == 0

   - This may be monthly, (N=12)

   - Quarterly, where (N=4)

   - Biannually, where (N=6)

   - The implementation works out such that the quarterly investor begins investing in March (month = 3), and the Biannual investor always starts investing in June (month = 6)

   - All subannual investors invest on the first trading day of each month in which they invest, skipping holidays and weekends.


## Results


### SP500, 30 year term

The first experiment compares two investors (yearly and monthly investing frequency) over a 30 year time horizon. 

Result: Yearly investor beats monthly investor.

30 year investing, comparison:

"""

Total shares held by yearly investor:  851.9668172216104

Total shares held by monthly investor:  803.6001892839496

Portfolio Values Ratio (yearly/monthly):  1.0601874272587692

"""


{{< figure
  src="https://raw.githubusercontent.com/morendav/investing_frequency_simulations/refs/heads/main/sp500_yearly_monthly_portfolio_values.png"
  title="Investors' Portfolio Values Over Time"
  link="https://github.com/morendav/investing_frequency_simulations/blob/main/sp500_yearly_monthly_portfolio_values.png"
  target="_blank"
  class="align-center"
>}}


As a follow up, I was curious how these results compare for different subannual frequencies (Monthly vs Quarterly vs Biannually) and how different time horizons might change the distribution of outcomes.


### SP500, Monte Carlo Simulations

In order to test the time horizons effect on expected outcomes, the case study runs a monte carlo simulation where each iteration randomly selects a time period within the range of available data (1983 - 2025). Each iteration calculates the portfolio ratio (Ratio = Portfolio Value Yearly Investors / Portfolio Value Subannual Investor), a separate monte carlo simulation is run for the three different subannual frequencies (Monthly, Quarterly, Biannually), each over 1000 random time windows within the available data.

The simulations suggest that the annual (Invest in January) investor _outperforms_ compared to every other subannual frequency. Additionally, it suggests that the most frequent investor (monthly) outperforms all lower frequency investors (quarterly, biannual). This last observation is likely a consequence of the implementation: Quarterly investors start investing in month 3, and biannual investors in month 6, meaning they both miss out on the first months of the year. This supports the hypothesis that time in the market is what most drives portfolio performance.


{{< figure
  src="https://raw.githubusercontent.com/morendav/investing_frequency_simulations/refs/heads/main/sp500_monteCarlo.png"
  title="Monte Carlo Simulations: SP500 Portfolio Ratios"
  link="https://github.com/morendav/investing_frequency_simulations/blob/main/sp500_monteCarlo.png"
  target="_blank"
  class="align-center"
>}}

### High Beta, Monte Carlo Simulations

We might expect highly volatile assets to offer a better outcome for a strategy that aims to shelter the portfolio against market downturns - to test this we look at a couple of high beta indexes:

- QQQ (a high beta index fund)
- Bitcoin

For these tests only monthly subannual investing was analyzed.

The data for high-volatility assets tested also converge over a longer time horizon investing on the yearly investor topping the monthly investor. In shorter time-horizons the high-beta assets demonstrate a wider range of outcomes than the SP500.


{{< figure
  src="https://raw.githubusercontent.com/morendav/investing_frequency_simulations/refs/heads/main/highBeta_monteCarlo_yearly_monthly_ratio.png"
  title="Monte Carlo Simulations: SP500 Portfolio Ratios"
  link="https://github.com/morendav/investing_frequency_simulations/blob/main/highBeta_monteCarlo_yearly_monthly_ratio.png"
  target="_blank"
  class="align-center"
>}}


These simulations had the following 9-10 year investment outcomes:


```
SP500 Investor started investing in ...... 2014
QQQ Investor started investing in ........ 2014
BTC Investor started investing in ........ 2015

Investor ratios = total portfolio value of yearly / monthly
SP500 investor ratio ............ 1.0417459886451395
QQQ investor ratio .............. 1.174122960008631
BTC investor ratio .............. 1.0408948892014118
```



## Conclusions: Which strategy is better?

Historical data suggests that over long timeframes, investing early (i.e. front-loading whatever you plan to invest in the year) is objectively the best from the perspective of maximizing portfolio value (note assumptions at the beginning of post).

Even in the short-term, front-loading may be the best bet for maximizing returns especially if investing in diversified, market-matched volatility assets (e.g. SP500).

Both of these strategies require determination, and a high tolerance for day to day fluctuations. In truth, the best strategy is _some_ exposure to the market - so the best _subjective_ strategy is the one that meets the investors risk tolerance. Subannual investing helps shelter a portfolio from losses by spreading distributions across months thereby mitigating down-turn risk. While historically this strategy has underperformed relative to early-year investing, if this more frequent distribution strategy better meets the investor's risk tolerance than it is the better strategy for that individual.



---------






---------


### Sidenote

Hello blog followers, it's been a while.

Let's not forget, I only committed to posting more frequently than once every 10<sup>10</sup> years but... still... I had intended to post more frequently.

I've been staying busy: working on some other side projects, doing a part-time grad school program, and so on - lamentably my goal to write more has taken a bit of a backseat. 

Regardless, it’s good to make some time to post again - I hope you liked this installment of idea sharing :)