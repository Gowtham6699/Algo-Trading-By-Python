# Algo-Trading-By-Python
This project would not provide you with real world profitable trading signals but this would be really helpful to understand how you should be writing down your ideas into code and test them just using Python

And fun part is this was my first project after which I started trying out newer and newer ideas to obtain some good Alphas! So, let’s get started with…

Now, before starting you should be familiar with Pandas, MatPlotLib, Datetime libraries. A standard plotting style used in Quant Industry is ‘fivethirtyeight’

we shall use pandas_datareader library to import data from Yahoo Finance. It takes stock ticker from data source(like MSFT for Microsoft, SBIN.NS for State Bank of India), data_source(stooqin our case) and start(start_date in our case)

Here I would show a Simple Moving Average(SMA) Crossover Strategy to get familiar with framework of Systematic Strategy testing:
Buy a stock when its 20-Day SMA crosses 50-Day SMA from below and square off position when 20-Day SMA crosses 50-Day SMA from above.

Following lines of code would create 20 & 50 SMA of Close prices.
(We generally use ‘Adj. Close Prices’ when we want to test a long term strategy. For short term strategies we prefer ‘Close Prices’.)

Finally, let’s create a new DataFrame containing all relevant info that could be fed into a function to provide Buy-Sell signals.
(funds column with initial capital of 1 Lac is created so that as we do buy-sell transactions in the next section we could make appropriate changes)

This is most important part of project i.e. Strategy

We set flag = 0 when we are not long or don’t have any open position. So when upward crossover happens i.e. SMA20 > SMA50 along with flag = 0 we go “long”.
Position is squared off when downward crossover happens i.e. SMA20 < SMA50 along with flag = 1.

All these things are for long-only context. Similarly we could consider case of long-short case.

Its important to keep a track of your open_position i.e. last_funds/Price and update last_funds on each day when your position is open i.e. last_funds = Price * open_position.
Finally, we could see results of our strategy by plotting funds.
