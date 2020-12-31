# Stock Price Predict Project
Name | StudentID
--- | ---
Nguyễn Văn Hoài Nam | 1712607
Phan Thanh Quan | 1712686
## Câu hỏi đặt ra:
Liệu mô hình mạng neural có thể hoàn thành tốt việc dự đoán giá cổ phiểu hay không?
## Ý nghĩa:
Dự đoán giá cổ phiếu luôn là một vấn đề được quan tâm nhưng có rất ít model hiệu quả, việc dự đoán thành công có thể có nhiều lợi ích như xây dựng bot tín hiệu trade,...
## Cách thức thu thập dữ liệu:
## Tổng quan dữ liệu:
Số dòng: 4967, số cột: 13, cột cần dự đoán là Close (giá đóng)
## Ý nghĩa của cột dữ liệu
- Close: Giá đóng; Kiểu float
- Open: Giá mở; Kiểu float
- High: Giá cao nhất trong ngày; Kiểu float
- Low: Giá thấp nhất trong ngày; Kiểu float
- Vol: Volume (Lượng giao dịch); Kiểu int
- Change_%: Thay đổi giá Close so với ngày trước; Kiểu: float
- SMA_20: Simple moving average tính theo 20 ngày (trung bình của 20 ngày trước); Kiểu: float
- EMA_20: Exponential moving average tính theo 20 ngày (giống SMA nhưng tính theo công thức mũ); Kiểu float
- BB_upper_20, BB_lower_20: Bollinger Band; Kiểu float
- MACD_12_26, MACDsign_12_26, MACDdiff_12_26: Moving average convergence divergence (một loại indicator phát hiện đổi chiều trend theo nhóm hiểu, được nhiều người đánh giá là lagging indicator, mọi indicator đều là lagging indicator nhưng MACD có vẻ là lag nhất, cũng hợp lý vì đảo cả trend thì trend đó có thể sẽ diễn ra rất lâu); Kiểu float
- RSI_14: Relative streng index (tạm dịch chỉ số sức mạnh tương đối, có thể đây là một trong những indicator được sử dụng nhiều nhất, có thể dự đoán trend, dự đoán giá đảo chiều dựa vào convergence và divergence gần giống như MACD,...); Kiểu float
## Tự đánh giá
Model tổng quan hoạt động khá tốt trong việc dự đoán trend, còn giá dự đoán thì độ chính xác không được cao, chi tiết mô tả trong notebook StockPredictModel.ipynb
## Phân công công việc
Phan Thanh Quan: Xây dựng và đánh giá model
## Hướng dẫn chạy file notebook
- File StockPredictModel.ipynb: Chọn Restart & Run All

  Lưu ý: Comment cell code đầu tiên của mục 3 **Đánh giá model** (có chú thích trong cell code) nếu không chạy đánh giá trung bình 20 lần chạy (khá tốn thời gian ~20 phút, em đã comment lại và để kết quả chạy trước ở dưới cell đó), tất cả các cell còn lại chạy tương đối nhanh.
