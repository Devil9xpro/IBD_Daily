# IBD Daily Chart — PineScript v6 Indicator

Indicator phân tích cổ phiếu theo phương pháp IBD (Investor's Business Daily) kết hợp Mark Minervini (SEPA) và Peter Lynch (PEG), tối ưu cho TradingView.

## Tính năng

### Trên chart
- **HLC Bars kiểu IBD** — thanh giá không có open tick, đen = tăng, đỏ = giảm
- **Đường MA 20/50/150/200** — nhận biết trend và support/resistance
- **Đường 52-week High** — đường dashed tím hiện đỉnh 252 ngày
- **Pivot đỉnh/đáy** — label hiện giá tại các đỉnh/đáy quan trọng (lookback 30 bars)
- **Gap marker ("G")** — đánh dấu gap mạnh > 2% giá
- **Breakout signal ("B")** — mũi tên khi giá vượt pivot high gần nhất

### Bảng phân tích kỹ thuật (góc phải)
| Chỉ số | Ý nghĩa |
|--------|---------|
| MA 20/50/200 | % khoảng cách giá so với MA |
| ATR(14) | Biên độ dao động trung bình (%) |
| Streak | Số ngày liên tiếp tăng/giảm |
| 52W High | % khoảng cách từ đỉnh 52 tuần |
| U/D Vol | Tỷ lệ volume tăng/giảm 50 ngày |
| SEPA | Minervini Trend Template (7 điều kiện) |
| Base | Đếm số lần breakout trong uptrend |

### Bảng phân tích cơ bản (góc trái)
| Chỉ số | Ý nghĩa |
|--------|---------|
| P/E | Giá / Lợi nhuận (rẻ < 20, đắt > 40) |
| PEG | P/E / EPS Growth — Peter Lynch (< 1 = undervalued) |
| ROE | Hiệu quả sử dụng vốn (> 17% = tốt) |
| EPS ▲ | Tăng trưởng EPS YoY (> 25% = mạnh) |
| Rev ▲ | Tăng trưởng doanh thu YoY |
| Net Margin | Biên lợi nhuận ròng (> 15% = tốt) |
| EPS | EPS TTM hiện tại |
| P/B | Giá / Giá trị sổ sách |

## Cách sử dụng

1. Mở TradingView → Pine Editor → dán code từ `IBD_Daily_Chart.pine`
2. Đổi chart type sang **"Bars"** → Chart Settings → Symbol → tăng Thickness
3. Tắt candle mặc định (indicator sẽ tô màu bars)
4. Điều chỉnh trong Settings → Inputs:
   - Group "Hiển thị": bật/tắt từng component
   - Group "Pivots": thay đổi lookback
   - Group "Gaps": thay đổi ngưỡng gap %

## Phương pháp luận

- **William O'Neil / CAN SLIM** — EPS growth > 25%, base count, pivot breakout
- **Mark Minervini / SEPA** — 7 điều kiện Trend Template, stage analysis
- **Peter Lynch** — PEG ratio để đánh giá growth stock có đang rẻ không

## Lưu ý

- **Bản Free TradingView**: bảng cơ bản (request.financial) có thể gây warning "tập lệnh nặng". Nâng lên bản Essential sẽ hết.
- **Cổ phiếu VN (HOSE)**: một số chỉ số FA có thể hiện "N/A" nếu TradingView chưa có data.
- Xem file `HUONG_DAN_CHI_SO.md` để hiểu cách đọc từng chỉ số.

## Screenshots

*(Thêm screenshot chart ở đây)*

## License

MIT
