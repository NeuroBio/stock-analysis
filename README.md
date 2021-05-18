# VBA of Wallstreet: an analysis of the trading history of green energy stocks in 2017 and 2018

## Overview of Project
Recent finance graduate Steve is interested in picking out green energy stocks for his parents to invest in.  He is happy with the macro I built for him to analyze stock trends thus far, but he wants to extend his stock dataset to include all of the stock market.  The current analysis macro is inefficient and will not handle an expanded dataset in a timely manner.  I will refactor the existing analysis macro to only check each row in the spreadsheet once per analysis instead of once per stock in the analysis.

## Analysis
The analysis was performed on 2017-2018 stock price and trade volume data collected from 12 green energy stocks.  The total daily volume was calculated by summing all the daily trade volumes for a stock in a given year.  The return was calculated by dividing (1) the price of a stock at the closing of the stock market on the final date for the year by (2) the price of a stock at the closing of the stock market on the first date for that year and (3) subtracting 1.  Positive returns were color-coded in green, while negative returns were color coded in red.  The length of time required to run the analysis was calculated by starting a timer after the user inputs the year they would like to perform the analysis on.  After all analysis logic had been executed, the timer was stopped.  The end value minus the start value of the timer was returned in a pop up.

## Results
### Stock Values
In 2017, essentially all of the green energy stocks were showing positive returns **(Fig. 1)**.  In fact, four of the stocks, DQ, ENPH, FSLR, and SEDG had at least doubled in value.  This suggests that green energy as a sector is a growing market.  However, but 2018, nearly all of these stocks show mild to moderate losses **(Fig. 2)**.  This is unsurprising, as the global market was down in 2018, so prices had fallen for a majority of stocks (see [6 factors that fueled the stock market dive in 2018]( https://www.pbs.org/newshour/economy/making-sense/6-factors-that-fueled-the-stock-market-dive-in-2018)).  The two stocks that defied this pattern were ENPH and RUN.  Steve should look into ENPH as a momentum play as it remained strong even in the financial downturn.  However, it is also quite possible that ENPH has already achieved much of its expected growth and stock prices may remain largely static going forward.  Steve will have to research projected earnings for the company to make a decision on how much more potential ENPH has.  If Steve’s parents are interested in day trading, they should seriously consider DQ.  There seems to be a lot of volatility in the value of this stock, and it is currently at a low (see the raw values in 2017 and 2018 [Analysis of 2017 Stocks](/Challenge/VBA_Challenge.xlsm)).  Unless Steve finds a valid reason for DQ to be undervalued at the moment (such as ongoing litigation), there is a good chance that there is a play to be made in buying DQ at this low of about 23$ and selling it when it spikes back up to previous levels of 50-60$.  In general, most of the stocks look like decent buys, because they are undervalued due to the market being down rather than because the company have lost their underlying value.  The one exception to this is TERP, which was down in 2017 and 2018.  Steve should look into why this company is losing value and whether the are signs of recovery in the near future.

![Analysis of 2017 Stocks](/Challenge/Resources/VBA_Challenge_2017.png?raw=true)

**Figure 1:** Analysis of green energy stock returns in 2017.  Stocks with positive returns are marked in green, while stocks with negative returns are marked in red.  Pop-up shows the amount of time required to analyze the data using the refactored algorithm.

![Analysis of 2017 Stocks](/Challenge/Resources/VBA_Challenge_2018.png?raw=true)

**Figure 2:**  Analysis of green energy stock returns in 2018.  Markings and pop-up are the same as described in Figure 1.

### Code Speed
The original code analyzed the 2017 data in approximately 0.7 seconds **(Fig. 3)** and the 2018 data in approximately 0.8 seconds **(Fig. 4)**.  In comparison, the refactored code analyzed the 2017 data in 0.14 seconds and the 2018 data in 0.13 seconds **(Figs. 1 & 2)**.  Thus, the refactored code runs 5-6 times faster than the original code for this small dataset.  Time savings are expected to be even greater for datasets with more stock tickers, because the new algorithm decreased the time complexity for the macro from O(n^2) to O(n) where n refers to each stock ticker added to the dataset.

![Original Algorithm Speed for 2017](/Challenge/Resources/Supplemental_2017.png?raw=true)

**Figure 3:** Time to complete the analysis of green energy stock returns in 2017 using the original algorithm.

![Original Algorithm Speed for 2018](/Challenge/Resources/Supplemental_2018.png?raw=true)

**Figure 4:** Time to complete the analysis of green energy stock returns in 2018 using the original algorithm.


## Summary
### Advantages and Disadvantages of Refactoring
Refactoring code, when done well, has the capacity to increase the readability and speed and reduce the time complexity of an algorithm.  It also often increases the functionality and the number of possible applications of the code, because better code tends to cater to the most general case, while many first passes at code are unnecessarily restricted to special cases.  However, refactoring code requires time.  Time spent refactoring existing code could instead be put towards writing new functions to handle new problems.  Furthermore, because bugs can be introduced while refactoring code, code that had been thoroughly bug tested prior to refactoring will need to be retested, requiring more time.
### Advantages and Disadvantages of this Refactoring this Script
The original code already worked, and Steve found no bugs while using it.  Although I have tested my refactored script, there is still a possibility that my refactored code has a bug that will become apparent when Steve tries to apply the new macro.  However, the refactored macro runs significantly faster, because it only checks the values in each row once.  The refactored code is therefore going to be viable for use with much larger datasets that would take too long to analyze with the original code.  As it stands, both sets of code are still limited to the twelve stocks that Steve originally wanted to analyze.  Before the macro can used with any group of stocks in the stock market as Steve requested, the macro needs to be able to stocks to the dataset on the fly rather than using hardcoded stock tickers.
