# Investing Frequency

## Outline

1. Intro
    - Broad basket index fund tend to perform positively over the course of a year, 70-75% of the time [source: https://curvo.eu/backtest/en/market-index/sp-500?currency=usd]
    - Disclaimer: not financial advice
2. CAPM
    - return of Portfolio = Rf - beta(Rm - Rf) + [alpha]
    - we might expect high Beta indeces to be more sensitive to timing
3. Case Study
    - Methods
    - Results
    - Py Notebook
4. So which is better?
    - Higher risk tolerance, longer time horizon: 
        - If you're comfortable with market fluctuations and are investing for the long term (10+ years), lump-sum investing may be the better option.
    - Lower risk tolerance, shorter time horizon: 
        - If you're more risk-averse or have a shorter time horizon, dollar-cost averaging might be a more suitable strategy.


## DRAFT
===================================

# TLDR
#todo

# Intro

Disclaimer: Not financial advice. Previous performance does not translate to future returns. etc, etc.

The inspiration for this blog post comes from a debate I had with a colleague, credit due to you (you know who you are)... I'll admit it... you were right.

The debate was quite simple: If you plan to invest $X in a year, is it better do frontload your investment at the beginning of the year or spread it out throughtout the entire year? For example, many employers offer 401k matching - is it better to attempt to draw from this match earlier in the year or does that not matter at all? 

Initially, my intuition was to stick to distributed investments, afterall this shields your investment from market risk and variability. Basically, my intution was that claiming that it was better to frontload was to say "I can time the market". My wise colleague corrected the claim, it wasn't about market timing but about time in market that mattered. They were right.

## Comparing strategies

Stated simply, the question we're trying to answer here is - which investor's portoflio has greater value over some time period T:
1. An investor that always invests on the first trading day of the year, every year
2. An investor that spreads their yearly investment across the first trading days of every month, every year

Holding constant:
* The number of years both investors invest
* The total yearly investment amount

For simplicity we will make a few assumptions, at least initially:
1. The investors are investing in a broad basket index fund
2. The investors aren't using a sophisticated strategy (they are not a hedge fund, they are a "set it and forget it" investor)
3. Long timeline investors
4. The investors ignore all macro-economic trends, meaning neither is trying to time entry/exit
5. All investors aren't counting on withdrawing any money from their investments until the term of thier investment time-horizon

## Time in market >>> derisking volatility

The canonical broad basket index, the SP500, has had positive yearly returns for between 70-75% of years in the last 100 years, depending on the specific data source and time period analyzed. Given this, early entrance is likely to have an annual payout 7 out of every 10 years the investor invests in the first month.

Over the lifetime of an investment, the arithmatic on the gains vs loses work out to a question of how:
A. Gains made on the winning years (7 out of 10 odds that any given year is a winner), are balanced against
B. Losses realized on losing years (3 out of 10 odds that any given year is a losing year)

NOTE: Our _Invest in Jan_ investor's entry in Jan is likely (70%+) to be a winning strategy YoY

The arithmatic is complicated by compounding growth, both because some broad basket indexes pay dividends which may be reinvested but also by capital appreciation overtime. For example, compounding growth over 7 years would need to be wiped out in the following 3 years in a toy example of a 10 year investment period where the first 7 years were bull markets followed by 3 years of bear markets. It's also complicated by some evidence that macro-trends may influence the frequency and life of bull and bear markets, [example](https://www.schwab.com/learn/story/is-two-year-old-bull-market-2-legit-2-quit).


## What about riskier assets?

Given all of this, it seems that the portfolio shock insulation that monthly investing provides may not outperform the 'time in market' strategy. Perhaps the former outshines for portfolios with more volatility?

A key assumption for our investors here is that they are trading in a broad basket index, the SP500, which is a proxy for the market as a whole. Formally, we would say the SP500 and the market exhibit _perfect postiive correlation_, and this formalation leads us to the canonical model for asset price and risk relationship. 

This formulation should provide us the crtieria to select assets that do not conform to assumption 1: "investors invest in broad basket index"

# Capital Asset Pricing Model (CAPM) & Asset Volatility

American Economists William Sharpe, John Lintner, and Jan Mossin are credited for building Capital Asset Pricing Model (CAPM) built upon earlier work of Harry Markowitz on portfolio optimization. 

CAPM is based on the idea that investors demand a premium for bearing risk, and that this premium should be proportional to the amount of risk taken. It provides a simple yet powerful way to estimate the expected return for an asset based on its risk relative to the overall market.    

CAPM Formula:

$E(R_i) = R_f + \beta_i (E(R_m) - R_f) + alpha$

Where:
#TODO - fix thsi with latex

- E(Ri) is the expected return on asset i
- Rf  is the risk-free rate of return
- β i  is the beta of1 asset i, a measure of its volatility relative to the market   
- E(R m ) is the expected return on the market portfolio
- alpha is an "error term"

In practice, the risk-free rate is often estimated using the yield on long-term government bonds, while the expected market return is typically based on historical averages or analyst forecasts. The beta of an asset can be calculated using statistical methods to measure its historical volatility relative to a broad market index, here is where our S&P500 index comes in.    

It's worth calling out here that CAPM relies on several simplifying assumptions, remarkably:
- Existence of a perfectly efficient market
- The ability of investors to borrow and lend at a risk-free rate

In reality, these assumptions may not always hold true, particularly in less developed or less regulated markets. Additionally, the CAPM may not be as accurate in predicting the returns for certain types of assets, such as those with high idiosyncratic risk (diversifiable risk) or those that are not publicly traded.

The error term, alpha, at times represents inefficiencies in the market. It is also the object of exploitation by hedge funds an sophisticate investors who 'seek alpha'. 

## CAPM For Assumption #1

Assumption 1 restated with CAPM terms is that we want to initially test with an asset whose β = 1. #todo-Latex This is achieved by using SP500 index. Then, what we want to test that perhaps the 'insulate portoflio' strategy (i.e. monthly investing) might be better for 'riskier' assets is some asset where β >> 1. 


# Case Study

This case study is hosted on GitHub, and has a companion notebook you can play with here.
#TODO - links here, github & colab

Summary of observations:
- For the SP500
    - The investor that invests in Jan outperforms the monthly, quarterly, and biannual investor over the long term (30yr term)
    - Short-term investing produces a wider range of outcomes (yearly vs sub-annual investing), but the data suggests that Jan-Investing is still more likely to outperform sub-annual investing
    - The data suggests that of the sub-annual investing strategies: Monthly outperforms Quarterly, and Quarterly outperforms biannual investing. 
        - This is likely an outcome of implementation becasue the quarterly investing starts on month 3, biannual on month 6, and monthly on month 1. 
        - In other words, quarterly misses investing in months [1, 2]. This supports the hypothesis that time in market is source of investment performance.
- For high Beta assets
    - We see the same outcomes as the SP500 (yearly > monthly > quarterly > biannual performance)
    - There is a wider range of observed outcomes when we look at short-term investing
- For Bitcoin
    - We see the same outcoems as the SP500

## Methods

The case study is written in Python, and makes use of the Yahoo Finance api to fetch historical asset prices over a date range. For the purposes of this case study we're only going to look at the opening price, and ignore intra-day fluctuations.

The case study seeks to answer the question of which investor's portfolio has greater value over some shared investment timeframe. This will be calculated as a the ratio of portfolio values:

Ratio = Portfolio(yearly) / Portfolio(subannual)
#todo - latex equation

Such that a ratio of >1 indicates that the yearly investor has beat the sub-annual investor. The portfolios will differ on their investment frequencies:

- Yearly investors will always invest the whole amount on the first trading day of the year, approximately Jan 2nd of every year.
- Subannual is any frequency that doesn't leave remaining months without investing, in otherwords: 12 % N == 0
    - This may be monthly, (N=12)
    - Quarterly, where (N=4)
    - Biannually, where (N=6)
    - The implementation works out such that the quarterly investor begins investing in March (month = 3), and the Biannual investor always starts investing in June (month = 6)
    - All subannual investors invest on the first trading day of each month in which they invest.



## Results

### SP500, 30 year term

The first experiment compares two investors (yearly and monthly investing frequency) over a 30year time horizon. Result: Yearly investor beats monthly investor.

#TODO - insert portoflio value picture here

30 year investing, comparison: 
"""
Total shares held by yearly investor:  851.9668172216104
Total shares held by monthly investor:  803.6001892839496
Portfolio Values Ratio (yearly/monthly):  1.0601874272587692
"""

As a follow up, I was curious how these results compare for different subannual frequencies (Monthly vs Quarterly vs Biannually) and how different time horizons might change the distribution of outcomes.

### SP500, Monte Carlo Simulations

In order to test the time horizons affect on expected outcomes, the case study runs a monte carlo simulation where each iteration randomly selects a time period within the range of available data (1983 - 2025). Each iteration calculates the ratio of Portfolio Value Yearly Investors / Subannual Investor, a separate monte carlo simulation is run for the three different subannual frequencies (Monthly, Quarterly, Biannually). 

The data suggests that the annual (Invest in Jan) investor _outperforms_ compared to every other subannual frequency. Additionally, it suggests that the most frequent investor (monthly) outperforms all lower frequency investors (quarterly, biannual). This last observation is likely a consequence of the implementation: Quarterly investors start investing in month 3, and biannual investors in month 6, meaning they both miss out on the first months of the year. This supports the conclusion that time in market is what most drives portfolio performance.

#TODO - insert monte carlo


### High Beta, Monte Carlo Simluations

We might expect highly volatile assets to offer a better outcome for a strategy that aims to shelter the portfolio against market downturns - to test this we look at a couple of high beta indexes:
- QQQ (a high beta index fund)
- Bitcoin

For these tests only monthly subannual investing was tested against.

The data for high-volatility assets tested seem to also converge over longer time-horizon investing on the yearly investor topping the monthly investor. In shorter time-horizons the high-beta assets demonstrate a wider range of outcomes (ratio of yearly / monthly portfolio values) than the SP500.

#TODO - insert high beta pic here

9-10 year investment outcomes:
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

Historical data suggests that over long timeframes, investing early (i.e. front-loading whatever you plan to invest in the year) is objectively the best from the perspective of maximimizing portfolio value. 

Even in the short-term, front-loading may be the best bet for maximizing returns especially if investing in broad basket indexes (e.g. SP500).

Both of these strategies require determination, and a high tolerance for day to day fluctuations. In truth, the best strategy is _some_ exposure to the market - so the best _subjective_ strategy is the one that meets the investors risk tolerance. Subannual investing helps shelter a portfolio from loses by spreading distributions across months thereby mitigating down-turn risk. While historically this strategy has underperformed relative to early-year investing, if this more frequent distrubtion strategy better meets the investor's risk tolerance than it is the better strategy for that individual.



# Sidenote
Hello blog followers, it's been a while. 

Let's not forget, I only committed to posting more frequently then once very 10<sup>10</sup> year but... stil... I had intended to post more frequently.

I've been staying busy returning to grad school part-time and completing some other side learning and projects which I haven't posted to the blog. 

It's good to be back, I hope to post more frequently than the 'every 1.5 years' that I've done so far. 