# Maximisor 

## In this project I am trying to maximize growth of the portfolio by entering and exiting 7 different JPMorgan mutual funds. I used 7 JPMorgan funds to cover wide variety of investments. 
1. US Large cap fund:OLGCX
2. US Mid Cap fund: OMGCX
3. US Small cap fund: OSGCX
4. Global fund: GAOCX
5. Emerging Markets fund: JEMCX
6. US Income fund: OINCX
7. Mortgage backed fund: OBBCX
I chose all funds from same family fund so there will be not exchange fee by entering and exiting the positions. I will start the portfolio by investing $10000 in each fund and keep $20000 as portfolio cash portion. Historical closing price for each fund will be downloaded as API from Yahoo Finance from 03-01-2020 to 07-10-2023. I will use Algorithmic Trading technique to find Entry and Exit signals to rebalance the Portfolio during economic and market cycles. With each Entry signal I will buy 100 share of that mutual fund if the portfolio cash is less than $20000 and 300 shares if the cash balance is more than $20000. With each Exit signal I will sell all of that fund shares. portfolio balance will be recalculated after each entry and exit position. 

## Methode:

I used shore and long SMA to to find entry exit signals. 

## Technology:
### Import the required libraries and dependencies
This project leverages Python 3.7 (Jupyter Lab) and utilizes %matplotlib inline as well as the Pandas and NumPy  requests, json, datetime, prophet, yfinance, matplotlib.pyplot, seaborn, holoviews, hvplot.pandas libraries.


## Installation Guide
Import pandas and numpy from the Python library
Initiate Jupyter lab from the Gitbash Terminal

## Data:
Historical closing price for each mutual fund will be downloded from Yahoo Finance using API between 03-01-2020 to 07-10-2023. 

## Steps:

On the first step created a portfolio by investing $10000 in each mutual fund baised on the closing Price of 07-10-2013. In the first senerio the portfolio will keep all the positions and no trade will be made. This portfolio values will be used to predict the portfolio value in the next 60 days.

### Import the required libraries and dependencies
### Get fund ticker information
### Merge all closing data in one data frame
![MutualFundsClose](MutualFundsClose.png)
### I will built portfolio investing $10,000 in each mutual fund to start investement. 
### calculating number of the shares for each fund baised on 203/7/10 prices
### defining the portfolio
![PortfolioBalanceOverTime](PortfolioBalanceOverTime.png)

### Reset the index of the DataFrame
### Review the first and last five rows of the DataFrame
### Prepare the training data to be read into a prophet model
### Rename the columns to names that Prophet recognizes
### Removing the timezone from the 'ds' column
### Displaying the modified data frame
### Call the Prophet function and store as an object
### Fit the time series model
### Create a future DataFrame to hold predictions
### Make the prediction go out as far as 720 hours (30 days)
### Review the first and last 10 rows of the DataFrame
### Make a forecast based on the future DataFrame
### Plot the forecast using the model’s plot function
![sixtydayperediction](sixtydayperediction.png) 

### Review the first five rows of the forecast DataFrame
#### Display the underlying forecast dataframe 
### Reset the index to this datetime column so that our plot looks nice
### Display the DataFrame
### Holoviews extension to render hvPlots in Colab
### Plot predictions for our forecast period
![YhatYhatLowerYhatuper](YhatYhatLowerYhatuper.png)
### Reset "ds" from the datetime index back to a column
### Plot the individual time series components of the model
![ComponentsForcastDay](ComponentsForcastDay.png)
![ComponentsForcastweekly](ComponentsForcastweekly.png)
![ComoinenetForcatsYearly](ComoinenetForcatsYearly.png)


In the second senerio I will use Algoritmic Trading SMA shot and Long to find entery and exit times to exacute the buy or sell order. 
Here are the steps and screen shots: 
### Import the required libraries and dependencies
### Get fund ticker information
### Merge all closing data in one data frame
### calculating number of the shares for each fund baised on 03-01-2020 prices
### Set the variables for short window and long window periods
### Loop through the columns of the DataFrame and calculate short and long SMA
### Generate the short and long window simple moving averages (50 and 100 days, respectively)
### Generate the trading signal 0 or 1,
#### where 1 is the short-window (SMA50) greater than the long-window (SMA100)
#### and 0 is when the condition is not met
#### Calculate the points in time when the Signal value changes
#### Identify trade entry (1) and exit (-1) points
![entrExitSignal](Screenshot 2023-07-24 203011.png)
#### Visualize exit/enter position relative to close price
![GAOCXEnterExit](GAOCXEnterExit.png)
![JEMCXEnterExit](JEMCXEnterExit.png)
![OBBCXEnterExit](OBBCXEnterExit.png)
![OINCXEnterExit](OINCXEnterExit.png)
![OLGCXEnterExit](OLGCXEnterExit.png)
![OMGCXEnterExit](OMGCXEnterExit.png)
![OSGCXEnterExit](OSGCXEnterExit.png)

### Loop trough the data frame and find the entry and exit signals and exacute the trade
#### FUND
![Trade](trade.png)
##### buy 100 shares,
##### calculate 100 share cost and deduct it from cas
##### current number of shares + 100
##### cost * num of shares
##### update cash value of the portfolio
![NumberShareofFund](NumberShareofFund.png)
![CashValue](CashValue.png)
![PortfolioBanaceandCashValue](PortfolioCashandValue.png)
![PortfolioValue](PortfolioValue.png)

After exacuting all the trades Back testing performed to evaluate the starategy: 

## Backtest 
### Create a list for the column name
### Create a list holding the names of the new evaluation metrics
### Initialize the DataFrame with index set to the evaluation metrics and the column
### Review the DataFrame
### Calculate annualized return
### Calculate cumulative return
### Calculate annual volatility
### Calculate Sharpe ratio
### Calculate downside return values
### Create a DataFrame that contains the Portfolio Daily Returns column
### Create a column to hold downside return values
### Find Portfolio Daily Returns values less than 0,
### square those values, and add them to the Downside Returns column
### Review the DataFrame
![Sortino_Ratio](Sortino_Ratio.png)
![PortfolioEvaluation](PortfolioEvaluation.png)
