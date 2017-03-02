#Equity Index Backtest

#Architecture

This class based backtest program pulls pricing data from Yahoo finance for equity indexes around the globe and GDP data from Quandl for those countries. The script contains five classes:

1. backtester - handles initiating the other classes and running the program by iterating through the data range for which we have pricing.
2. marketData - pulls in pricing and GDP data. Pricing data is generated for the tickers listed in country_indicies.csv.
3. model - handles generating the trade signal by running a model on the pricing and GDP data. In this specific program, trade signals are generated for the 3 markets with the cheapest price to GDP ratio.
4. trader - handles trades signals generated from model by closing exisiting positions and initiating the new positions.
5. portfolio - handles tracking daily portfolio, account equity, and positions profit and loss.

#Testing Data

To test other methodologies, users can change the following to test their own strategies on equity data:

1. Open country_indicies.csv and update the columns for the tickers you wish to test
2. Edit the model class to run the strategy you wish to test. The model class needs to output a list of tickers you wish to trade, which will be traded by the trader class on the next business day.
3. In backtester.startBacktest(), the last if statement determines when to run the model, generating new trades. If no trades are generated, the positions continue into perpetuity. The current script triggers the model at the beginning of each month.

#Output

The output of the analysis will be a pyplot graph and an Excel spreadsheet. The Excel spreadsheet will contain all data to help you judge the viability of the trading strategy. It will contain an account equity graph over time, a tab with all trades, and a tab with daily profit and losses. The Excel spreadsheet will output to the same file, and will be labeled backtestIshares.xlsx.