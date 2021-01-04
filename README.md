# Stock Price Prediction
Name | StudentID
--- | ---
Nguyễn Văn Hoài Nam | 1712607
Phan Thanh Quan | 1712686
## Our question:
Can a neural network perform good forecasts for stock price?

## Insight:
Stock Price Prediction is a interesting subject but there are few public models can give decent results. High accuracy prediction gain profits in term of making money, building buy/sell signal bot,...

## How we collect data:
We crawl from this site [investing](https://www.investing.com).  
We use selenium to interact with calendar and set the start day in the past to get 5000 records.  
We use regular expression to extract Volume from source code.  
Other fields (Date, Close, Open, High, Low, Change_%) can be easily taken from text between tag using selenium methods.

## About the data:
`stock_price.csv`: 5000 rows, 7 columns like data from [Historical price of IBM quote](https://www.investing.com/equities/ibm-historical-data) between Feb 15, 2001 to Dec 30, 2020.  
`stock_price_with_indicators_nan.csv`: 5000 rows, 16 columns. stock_price.csv with indicators calculated from Close column (Closing price - giá chốt phiên).  
`stock_price_with_indicators.csv`: 4967 rows, 16 columns. stock_price_with_indicators_nan.csv but drop NaN values.  
The columns use for prediction is Close.  

## Columns description
||Columns|Type|Meaning
---|---|---|---
1|Date|string|Day month year
2|Close|float|Closing price at the end of a day
3|Open|float|Opening price at the beginning of a day
4|High|float|Higest price in that day
5|Low|float|Lowest price in that day
6|Vol|int|Volume: amount of money transacted in that day
7|Change_%|float|Closing price today compare to yesterday in percentage
8|SMA_20|float|Simple Moving Average of 20 days before. This is a type of trend indicators (lagging) which analyze whether a market is moving up, down, or sideways over time.
9|EMA_20|float|Exponential Moving Average of 20 days before (like SMA but with exponential weighted). This is also a trend indicator.
10|BB_upper_20, BB_lower_20|float|Bollinger Bands of 20 days before. This is a type of Mean Reversion Indicators (lagging) which measure how far a price swing will stretch before a counter impulse triggers a retracement.
11|OBV|float|On-Balance Volume is a type of Volume indicators (leading or lagging) which calculate trades and quantify whether bulls (rising) or bears (falling) are in control.
12|MACD_12_26, MACDsign_12_26, MACDdiff_12_26|float|Moving Average Convergence Divergence with default setting fast period=12 days, slow period=26 days and signal period=9 days. This is a type of Momentum indicators (leading) which evaluate the speed of price change over time.
13|RSI_14|float|Relative Strength Index of 14 days before. This is a type of relative strength indicators (leading) measure oscillations in buying and selling pressure. (tạm dịch chỉ số sức mạnh tương đối, có thể đây là một trong những indicator được sử dụng nhiều nhất, có thể dự đoán trend, dự đoán giá đảo chiều dựa vào convergence và divergence gần giống như MACD,...)

## Self-assessment
Overall, Model gets a decent result in trend prediction but the accuracy of forecasted closing price not quite high, details in StockPredictModel.ipynb notebook

## Work
--- | ---
Nguyễn Văn Hoài Nam | Crawl data, calculate indicator, preprocess and visualization.  
Phan Thanh Quan | Build and validate model.  

## Running instruction
`StockPredictModelJupyterLab.ipynb`: On Jupyter Notebook or Jupyter Lab, Click Restart & Run All.

Note: Comment cell code đầu tiên của mục 3 **Đánh giá model** (có chú thích trong cell code) nếu không chạy đánh giá trung bình 20 lần chạy (khá tốn thời gian ~20 phút, em đã comment lại và để kết quả chạy trước ở dưới cell đó), tất cả các cell còn lại chạy tương đối nhanh.
  
## Disclaimer:
This project is for study/research purpose. We don't take any responsibility with your investment. Please read and use our result considerably **This is not a financial advice!**
