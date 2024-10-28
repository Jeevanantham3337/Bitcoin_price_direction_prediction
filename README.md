# Bitcoin_price_direction_prediction
To predict the next day's price direction of Bitcoin (up or down) by combining historical price data with sentiment data. The goal is to develop a robust model that can accurately forecast price direction based on market sentiment and historical trends.

**BITCOIN PRICE DIRECTION PREDICTION USING RANDOM FOREST AND ENSEMBLE TECHNIQUES**

**DATA PREPARATION:**


Two types of Data:

1\.Sentiment Data – Wikipedia data

2\.Historical price Data – Yfinance data

**SENTIMENT DATA – WIKIPEDIA DATA**

Collecting the edits on bitcoin related pages in Wikipedia using mwclient and HuggingFace model is used for text classification.

This is for helpful to analysis the sentiment over bitcoin using licensed data.

There are three columns such as 

- mean of the sentiment of the day
- negative sentiment ratio over total sentiment
- edit count might be influenced on bitcoin price

Rolling the data for 30 days - Rolling mean could give your model a smoother view of the trend, helping it avoid reacting to single-day spikes or drops

**HISTORICAL PRICE DATA – YFINANCE DATA**

Download the Bitcoin historical price data up to today and predict the next day price direction,

Combining the Historical data and Sentiment data with the help of date.

Adding Target Column:

btc['target'] = (btc['tomorrow']>btc['close']).astype(int)

which helps to predict the price direction.

**BASE MODEL DEVELOPMENT:**

Random forest Classifier – which helps to predict the price direction.

model=RandomForestClassifier(n\_estimators=100, min\_samples\_split=50, random\_state=1)

Which creates 100 decision trees with minimum number of samples needed to split any internal node and assign same random number every time we run, to avoid fluctuation of the prediction of the same data.

Min\_split avoids overfitting.

**MODEL EVALUATION:**

**IMPROVE THE PERFORMANCE FOR THE DATA, SHIFTED TO ENSEMBLE MODEL SUCH AS XGBCLASSIFIER:**

model=XGBClassifier(random\_state=1, learning\_rate=0.1, n\_estimators=200)

**MODEL EVALUATION:**

Using XGBClassifier, it improves the performance of model from 0.35 to 0.5 (precision score)

Need to follow the trends for particular period which means there is some trend which might helpful to predict price direction to certain days.

So, we need to consider trend indicators such as

- Moving average
- Exponential Moving Average

Even after adding the indicators, there is no improvement in model performance.

LSTM or Arima need to be introduced.





