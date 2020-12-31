# Stock Price Prediction
Name | StudentID
--- | ---
Nguyễn Văn Hoài Nam | 1712607
Phan Thanh Quan | 1712686
## Our question:
Can a neural network perporm good forecasts for stock price?

## Insight:
Stock Price Prediction is a interesting subject but there are few public models can give decent results. High accuracy prediction gain profits in term of making money, building buy/sell signal bot,...

## How we collect data:
We crawl from this site [investing](https://www.investing.com). The Volume can be extracted from source code and other fields (Date, Close, Open, High, Low, Change_%) can be easily taken from text data.

## About the data:
stock_price.csv: 5000 rows, 7 columns like data from [investing IBM URL](https://www.investing.com/equities/ibm-historical-data) between Feb 15, 2001 to Dec 30, 2020

stock_price_with_indicators_nan.csv: 5000 rows, 16 columns. stock_price.csv with indicators calculated from Close column (Closing price - giá chốt phiên)

stock_price_with_indicators.csv: 4967 rows, 16 columns. stock_price_with_indicators_nan.csv but drop NaN

The columns use for prediction is Close

## Ý nghĩa của cột dữ liệu
Columns|Type|Meaning
---|---|---
Date|string|Day month year
Close|float|Closing price at the end of a day
Open|float|Opening price at the beginning of a day
High|float|Higest price in that day
Low|float|Lowest price in that day
Vol|int|Volume: amount of money transacted in that day
Change_%|float|Closing price compare to yesterday in percentage
SMA_20|float|Simple moving average of 20 before
EMA_20|float|Exponential moving average of 20 before (like SMA but with exponential weighted)
BB_upper_20, BB_lower_20|float|Bollinger Bands
OBV|float|On-Balance Volume
MACD_12_26, MACDsign_12_26, MACDdiff_12_26|float|Moving average convergence divergence (một loại indicator phát hiện đổi chiều trend theo nhóm hiểu, được nhiều người đánh giá là lagging indicator, mọi indicator đều là lagging indicator nhưng MACD có vẻ là lag nhất, cũng hợp lý vì đảo cả trend thì trend đó có thể sẽ diễn ra rất lâu)
RSI_14|float|Relative strength index (tạm dịch chỉ số sức mạnh tương đối, có thể đây là một trong những indicator được sử dụng nhiều nhất, có thể dự đoán trend, dự đoán giá đảo chiều dựa vào convergence và divergence gần giống như MACD,...)

## Self-assessment
Overall, Model gets a decent job in trend prediction but the accuracy of forecasted closing price not quite high, details in StockPredictModel.ipynb notebook

## Work
Nguyễn Văn Hoài Nam: Crawl data, calculate indicator, preprocess and visualization

Phan Thanh Quan: Build and validate model

## Running instruction
- StockPredictModelJupyterLab.ipynb: On Jupyter Notebook or Jupyter Lab, Click Restart & Run All

  Lưu ý: Comment cell code đầu tiên của mục 3 **Đánh giá model** (có chú thích trong cell code) nếu không chạy đánh giá trung bình 20 lần chạy (khá tốn thời gian ~20 phút, em đã comment lại và để kết quả chạy trước ở dưới cell đó), tất cả các cell còn lại chạy tương đối nhanh.
  
## Disclaimer:
This project is for study/research purpose. We don't take any responsibility with your investment. Please read and use our result considerably **This is not a financial advice!**
