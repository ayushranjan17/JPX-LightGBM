# JPX-lgbm
## AIM ##
  The project aims to predict target(daily returns) for 2000 stocks listed in JPX(Japan Exchange) and rank them, the projct was built under a Kaggle hackathon organised by JPX itself.
## Feature extraction ##
  Features are selected from three files available in competition dataset i.e. stock_prices, financials ans stock list 
  1. stock_list.csv contains nature of company ,sector and several general information about company.
  2. financials.csv contains fundamentals of each stock
  3. stock_prices.csv contains daily open,close,low,high adjusted by date
We have extracted these technical indicators along with fundamental data from financials.csv
  1. Simple Moving Avergae(5,10,20,30 days period)
  2. Exponential Weighted Moving Average(5,10,20,30 days period)
  3. RSI(Relative strength of index)(14 days period)
  4. Bias(5 days period)
  5. Daily returns(not Target column)
  6. Volatility(50 days period)
  7. AMV(aggregate market value, i.e. the total share outstanding at given time,regular)
  8. CMO(Chande Momentum Osciallor , 14 days period)
  9. Bollinger Bands ( lower, mid, upper)
  10. ADX(Average directional Movement index, 14 days period)
  11. Rate of change of closeing prices over periods and standard deviation of change.
#### All the technical indicators are calculated using rolling window technique ####

## Model Selection and Tuning ##
LightGBM regression model is used in the project to predict labels and rank them.Cross validation used is TimeSeriesSplit.

## Challenges Faced ##
1. Since the dataset was very large to handle, which nor kaggle notebook wasn't able to handle and neither my local machine.
2. AdjustmentFactor column is dropped because it is having values as large as 20 for several securities, which was leading to unexpected Target predicted by the model trained on AdjustedClose(Though the code is in the notebook and can be tested for the Target predictions)
3. I tried to train model on XGBoost but due to its more memory consumption, I had to drop that algorithm and selected lgbm.
