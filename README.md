# Data wrangling with Stock market's data

## Data Wrangling - Stock market's data analysis using APIs

I work in finance industry and I’m interested in analyzing financial data of all kinds. That’s why I chose this topic for my Term project. I had to search and read through a lot of APIs before using this one.

## Objective
I want to fetch NASDAQ’s stock markets data for a few tickers via API and clean up the data to a usable format. 
When it comes to predictive analytics using machine learning, everybody thinks of coming up with an ML algorithm to predict stock prices and make money!!! Well its complicated. A lot of other factors apart from the historical numbers affect stock prices, so it’s a vast subject. I will stick to extracting dataset from the API and formatting it to usable data in this project.
### APIs used
I used two APIs for my project. 
First one fetches the list of stock tickers (e.g. AAPL, FB etc.,)
Second one gets the stock data in real-time for the given list of tickers.

Sample output of Tickers API:
```python
Symbol,Company Name
AAIT,iShares MSCI All Country Asia Information Technology Index Fund
AAL,"American Airlines Group, Inc."
AAME,Atlantic American Corporation
```

I’m only interested in fetching the Symbol and pass it on to the next API for its stock data.
Stocks data API
API link: https://financialmodelingprep.com/api/v3/quote/
Example call: https://financialmodelingprep.com/api/v3/quote/AAPL

```
[ 
    {
      "symbol" : "AAPL",
      "price" : 318.73000000,
      "changesPercentage" : 1.11000000,
      "change" : 3.49000000,
      "dayLow" : 315.06000000,
      "dayHigh" : 318.74000000,
      "yearHigh" : 318.74000000,
      "yearLow" : 151.70000000,
      "marketCap" : 1397322022912.00000000,
      "priceAvg50" : 315.24000000,
      "priceAvg200" : 239.89417000,
      "volume" : 34454117,
      "avgVolume" : 26878815,
      "exhange" : "NASDAQ"
    } 
]

```
API documentation: https://financialmodelingprep.com/developer/docs/
This API is well built, has clear documentation and no subscription or private key is needed to fetch data. I’m going to use it outside of this project as well for machine learning modeling for other use cases that I have in my mind.

Steps
1.	Load the libraries required to do the data import and data preparation.
2.	Configure the logging to log API connectivity and data fetch results.
3.	The method “getListofTickers” takes REST API url and returns the list of tickers. API get the data in CSV output and this method convert it to list of tickers.
4.	This method “getStocksList “takes REST API url and tickers list as input and establishes connection. Fetches response data and processes JSON data into Python dictionary and return the response.
5.	Then I called the above 2 methods and stored the output to variables. I used json_normalize to normalize the json output.
6.	Renamed certain columns in the dataset to more meaningful names.
7.	Dropped the null values. Not all tickers have stock data in the APIs, so some of them are NULLs/NaNs – I got rid of such rows.
8.	Converted the object types to date type and other formatting of columns
9.	Displayed the final dataset

