Analysis of 6 NIGERIAN STOCKS from JAN 2023-OCT 2026 showing returns , risks , correlation and portfolio optimism in python

QUESTION:
I wanted to find out how risky each stock was, how the stocks moved together, and what mix of them would have given the best return for the risk taken.

DATA
Daily closing prices were downloaded from investing.com for 3 January 2023 to 19 October 2026.

STOCKS USED 
Seplat Energy (oil and gas)
Nestle Nigeria (consumer goods)
GTCO (banking)
Zenith Bank (banking)
MTN Nigeria (telecoms)
Dangote Cement (industrial)


NOTES ON THE DATA
Some Nigerian stocks do not trade every day, so days with a missing price were filled with the last known price, for up to 5 days in a row.
Returns are calculated from closing prices only. They do not include dividends, so they understate what an investor would have earned in total.
The raw CSV files are not in this repo. To rerun the notebook, download daily historical data for each stock from investing.com (from 1 January 2023) and save the files in a data/ folder.


METHOD 
Cleaned the price data and filled short gaps (up to 5 days).
Calculated daily returns, the percentage change in price each day.
Calculated annualised volatility for each stock, which measures how much its returns swing around in a year.
Plotted the growth of ₦1 invested in each stock over the period.
Calculated the correlation of daily returns between every pair of stocks, then repeated it with weekly returns to test the effect of stocks that do not trade every day.
Simulated about 18,000 random portfolios of the six stocks, with no stock allowed more than 30% of the portfolio.
Calculated the yearly return and risk of each portfolio.
Ranked the portfolios by Sharpe ratio, using a 17% risk-free rate based on the 364-day Nigerian Treasury bill yield (October 2026).

FINDINGS
Zenith Bank was the riskiest stock (about 39% annual volatility) and Nestle Nigeria the calmest (about 28%).
GTCO and Zenith Bank moved together the most (correlation of 0.59), which makes sense as both are banks.
Seplat grew the most: ₦1 invested became about ₦15.3 by October 2026.
Weekly correlations were higher than daily ones for several pairs, which suggests that thin trading hides how stocks really move together. This was not true for every pair.
The best portfolio (max 30% per stock) had a return of about 53.4% and risk of about 17.3%, with a Sharpe ratio of 2.10. Seplat was its biggest holding, at about 30%, right at the cap.


LIMITATIONS
The period 2023 to 2026 was a strong one for these stocks, so the returns and the high Sharpe ratio (2.10) are unlikely to repeat. Past performance does not predict future results.
Some of these stocks do not trade every day, so their risk and correlations are probably understated. The weekly correlations were higher than the daily ones for several pairs, which points to this.
The portfolio weights come from a random search of about 18,000 portfolios, so they are approximate. They are not exact optimal weights.
Returns are price-only and exclude dividends.
The Sharpe ratio depends on the 17% risk-free rate I assumed.
Only six stocks were used, so this is not a view of the whole market.
This is a learning project, not investment advice. Further analysis would be needed before relying on any of these results.

TOOLS
Python, pandas, NumPy, matplotlib. The analysis is in notebooks/01_data.ipynb.