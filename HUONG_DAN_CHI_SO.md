# Hướng dẫn đọc các chỉ số tài chính trên chart

## Bảng bên phải (Phân tích kỹ thuật)

| Chỉ số | Ý nghĩa | Xanh (tốt) | Đỏ (xấu) |
|--------|---------|-------------|-----------|
| MA 20 | Giá cách MA 20 ngày bao nhiêu % | Dương (giá trên MA) | Âm (giá dưới MA) |
| MA 50 | Giá cách MA 50 ngày bao nhiêu % | Dương | Âm |
| MA 200 | Giá cách MA 200 ngày bao nhiêu % | Dương | Âm |
| ATR(14) | Biên độ dao động trung bình 14 ngày (%) | — | — |
| Streak | Số ngày liên tiếp tăng/giảm | ▲ tăng | ▼ giảm |
| 52W High | Giá cách đỉnh 52 tuần bao nhiêu % | Gần 0% (gần đỉnh) | < -25% (xa đỉnh) |
| U/D Vol | Tỷ lệ volume ngày tăng / ngày giảm trong 50 ngày | ≥ 1.5 (tích lũy) | ≤ 0.7 (phân phối) |
| Dist Day | Số phiên phân phối trong 25 ngày (O'Neil) | 0-2 (an toàn) | ≥ 5 (nguy hiểm) |
| MF Score | Main Force Score — smart money 0-100 | ≥ 70 (mua vào) | < 40 (bán ra) |
| Vol Trend | Volume 10 ngày / Volume 50 ngày | < 0.7x (Dry-up, sẵn sàng breakout) | > 1.3x (Expand/Bùng nổ) |
| Tight | Số ngày liên tiếp biên độ < 0.5×ATR | ≥ 5 (nén mạnh, setup breakout) | — |
| RS | Performance 3 tháng so với VN-Index | Dương + ↑ (outperform, cải thiện) | Âm + ↓ (underperform, yếu đi) |

### Vol Trend (chi tiết)
- **Là gì:** So sánh volume trung bình 10 ngày với volume trung bình 50 ngày
- **Ý nghĩa:** Volume đang tăng hay giảm so với bình thường
- **Đánh giá:**
  - < 0.7x: **Dry-up** (xanh) — volume co lại, supply cạn, sẵn sàng breakout. Đây là VCP signal.
  - 0.7-1.3x: **Bình thường** (đen) — không có gì đặc biệt
  - > 1.3x: **Expand** (cam) — volume đang tăng, cần xem giá tăng hay giảm
  - > 1.5x: **Bùng nổ** (cam) — volume cực cao, có thể breakout hoặc distribution
- **Kết hợp:** Vol Trend Dry-up + Tight ≥ 5 + giá gần pivot high = setup breakout lý tưởng

### Tight Close (chi tiết)
- **Là gì:** Đếm số ngày liên tiếp biên độ thanh bar (high - low) nhỏ hơn 0.5 × ATR(14)
- **Ý nghĩa:** Stock đang nén giá — biên độ co lại bất thường, supply và demand đang cân bằng ở mức thấp. Khi 1 bên bứt phá → giá sẽ move mạnh.
- **Tại sao dùng 0.5 × ATR:** ATR là biên độ trung bình — nếu 1 ngày có range nhỏ hơn nửa mức bình thường, đó là ngày "yên bất thường". Dùng ATR thay vì % cố định để tự adapt theo từng stock.
- **Đánh giá:**
  - 0-2 ngày: **—** (đen) — bình thường, chưa có gì
  - 3-4 ngày: **Nén** (teal) — bắt đầu co lại, theo dõi
  - ≥ 5 ngày: **Nén mạnh ✓** (xanh) — setup breakout, sẵn sàng move
- **Cách dùng:**
  1. Tight ≥ 5 → stock đang nén, chờ breakout
  2. Kết hợp Vol Trend Dry-up (< 0.7x) → xác nhận supply cạn kiệt
  3. Khi breakout "B" xuất hiện SAU tight period → entry point mạnh
  4. Stoploss đặt dưới vùng tight (đáy gần nhất trong chuỗi tight)
- **Lưu ý:** Tight chỉ có ý nghĩa trong context uptrend hoặc base. Stock đang downtrend mạnh cũng có thể tight 1-2 ngày trước khi giảm tiếp — cần kết hợp với U/D Vol và MF Score.

### RS (Relative Strength vs Index)
- **Là gì:** So sánh performance 3 tháng (63 phiên) của cổ phiếu với VN-Index
- **Công thức:** RS = (% thay đổi cổ phiếu 63 ngày) - (% thay đổi VN-Index 63 ngày)
- **Ý nghĩa:** Cổ phiếu đang mạnh hơn hay yếu hơn thị trường chung
- **Đánh giá:**
  - Dương (xanh): **Outperform** — cổ phiếu mạnh hơn index. O'Neil chỉ mua stock RS dương.
  - Âm (đỏ): **Underperform** — cổ phiếu yếu hơn index. Tránh.
- **Mũi tên Trend (RS đang cải thiện hay yếu đi):**
  - ↑ : RS tăng > 2% so với 10 ngày trước — stock đang mạnh lên so với thị trường
  - → : RS ổn định (thay đổi < 2%)
  - ↓ : RS giảm > 2% so với 10 ngày trước — stock đang yếu đi
- **Cách dùng:**
  1. RS dương + ↑ = stock mạnh và đang cải thiện → ưu tiên mua
  2. RS dương + ↓ = stock vẫn outperform nhưng đang yếu dần → cẩn thận
  3. RS âm + ↑ = stock yếu nhưng đang hồi phục (có thể tạo đáy trước index) → theo dõi
  4. RS âm + ↓ = stock yếu và tiếp tục yếu → tránh hoàn toàn
- **Trường hợp đặc biệt:**
  - Stock giảm ít hơn index trong correction: RS sẽ dương dù cả hai đều giảm → institutional holding
  - Stock tạo đáy trước index: RS sẽ chuyển từ ↓ sang ↑ trước khi index phục hồi → leading signal
- **Thay đổi Index:** Vào Settings → group "RS" → đổi sang `HOSE:VN30`, `SP:SPX`, etc. tùy thị trường
- **Lưu ý:** Cần tối thiểu 73 phiên data trên chart. Stock mới niêm yết sẽ hiện "N/A".

---

## Bảng bên trái (Phân tích cơ bản / Fundamental)

### P/E (Price to Earnings)
- **Là gì:** Giá cổ phiếu chia cho lợi nhuận trên mỗi cổ phiếu (EPS)
- **Ý nghĩa:** Bạn đang trả bao nhiêu đồng cho 1 đồng lợi nhuận
- **Đánh giá:**
  - < 20: Rẻ (xanh)
  - 20-40: Hợp lý (đen)
  - > 40: Đắt (đỏ) — nhưng cổ phiếu growth có thể chấp nhận P/E cao nếu EPS tăng nhanh

### PEG (Peter Lynch)
- **Là gì:** P/E chia cho tốc độ tăng trưởng EPS (%)
- **Ý nghĩa:** So sánh giá với tốc độ tăng trưởng. P/E 30 nhưng EPS tăng 50% → PEG = 0.6 (rẻ!)
- **Đánh giá:**
  - < 1: **Undervalued** — tăng trưởng nhanh hơn giá (xanh, MUA)
  - 1-2: Hợp lý (đen)
  - > 2: **Overvalued** — giá đã chạy quá xa tăng trưởng (đỏ)
- **Lưu ý:** Chỉ có ý nghĩa khi EPS đang tăng (> 0). Nếu EPS âm → PEG = N/A

### ROE (Return on Equity)
- **Là gì:** Lợi nhuận ròng / Vốn chủ sở hữu × 100%
- **Ý nghĩa:** Công ty tạo ra bao nhiêu lợi nhuận từ mỗi đồng vốn
- **Đánh giá (Minervini):**
  - > 17%: Hiệu quả cao (xanh)
  - 10-17%: Trung bình (đen)
  - < 10%: Kém hiệu quả (đỏ)

### EPS ▲ (EPS Growth YoY)
- **Là gì:** % tăng trưởng lợi nhuận/cổ phiếu so với cùng kỳ năm trước
- **Ý nghĩa:** Công ty có đang kiếm tiền nhiều hơn không
- **Đánh giá (Minervini/O'Neil):**
  - > 25%: Tăng trưởng mạnh (xanh) — đây là tiêu chí #1 của CAN SLIM
  - 0-25%: Tăng nhẹ (đen)
  - < 0%: Lợi nhuận giảm (đỏ) — TRÁNH

### Rev ▲ (Revenue Growth YoY)
- **Là gì:** % tăng trưởng doanh thu so với cùng kỳ năm trước
- **Ý nghĩa:** Công ty có bán được nhiều hàng hơn không
- **Đánh giá (Minervini):**
  - > 25%: Tăng trưởng mạnh (xanh)
  - 0-25%: Tăng nhẹ (đen)
  - < 0%: Doanh thu giảm (đỏ)
- **Lưu ý:** EPS tăng nhưng Revenue giảm = cắt chi phí, không bền vững

### Margin (Operating Margin)
- **Là gì:** % lợi nhuận hoạt động / doanh thu
- **Ý nghĩa:** Mỗi 100 đồng doanh thu, công ty giữ lại bao nhiêu đồng lợi nhuận
- **Đánh giá (Minervini):**
  - > 15%: Biên lợi nhuận tốt (xanh) — công ty có pricing power
  - 5-15%: Trung bình (đen)
  - < 5%: Biên mỏng (đỏ) — dễ bị ảnh hưởng khi chi phí tăng

### EPS (EPS TTM)
- **Là gì:** Lợi nhuận trên mỗi cổ phiếu trong 12 tháng gần nhất
- **Đánh giá:**
  - Dương (xanh): Công ty có lãi
  - Âm (đỏ): Công ty đang lỗ — TRÁNH (trừ khi startup)

### P/B (Price to Book)
- **Là gì:** Giá cổ phiếu / giá trị sổ sách mỗi cổ phiếu
- **Ý nghĩa:** Bạn trả bao nhiêu so với tài sản thực của công ty
- **Đánh giá:**
  - < 2: Hợp lý (xanh)
  - 2-5: Trung bình (đen)
  - > 5: Đắt (đỏ) — nhưng tech/growth stocks thường P/B cao vì tài sản vô hình

---

## Cách đánh giá nhanh cổ phiếu tăng trưởng (Peter Lynch + Minervini)

### ✅ MUA khi:
1. PEG < 1 (rẻ so với tăng trưởng)
2. EPS ▲ > 25% (lợi nhuận tăng mạnh)
3. Rev ▲ > 25% (doanh thu cũng tăng, không chỉ cắt chi phí)
4. ROE > 17% (sử dụng vốn hiệu quả)
5. SEPA ≥ 5/7 (kỹ thuật confirm uptrend)

### ⚠️ CẨN THẬN khi:
- PEG > 2 (đắt)
- EPS tăng nhưng Revenue giảm (không bền)
- Margin giảm liên tục (lợi nhuận bị ăn mòn)

### ❌ TRÁNH khi:
- EPS < 0 (đang lỗ)
- SEPA 0-2/7 (downtrend)
- U/D Vol < 0.7 (phân phối, smart money đang bán)

---

## Ký hiệu trên chart

| Ký hiệu | Màu | Ý nghĩa |
|---------|------|---------|
| **B** ▲ | Xanh dương | Breakout — giá vượt đỉnh pivot (điểm mua) |
| **G** × | Xanh | Gap Up mạnh (> 2% giá) |
| **G** × | Đỏ | Gap Down mạnh |
| Label trên | Trắng/đen | Giá đỉnh pivot |
| Label dưới | Trắng/đen | Giá đáy pivot |
| Đường tím liền | — | MA 150 (30 tuần) |
| Đường tím dashed | — | 52-week High |

---

## Checklist trước khi MUA (tất cả phải align)

Dựa trên phương pháp Minervini — chờ mọi dấu hiệu đúng cùng lúc:

### Bảng kỹ thuật (phải):
- [ ] **SEPA ≥ 5/7** (tốt nhất 7/7) — uptrend xác nhận
- [ ] **U/D Vol ≥ 1.5** (Tích lũy) — smart money đang mua
- [ ] **Base lần 1-2** — breakout sớm, chưa late stage
- [ ] **Breakout "B" vừa xuất hiện** — timing entry

### Bảng cơ bản (trái):
- [ ] **PEG < 1** — giá rẻ so với tăng trưởng
- [ ] **EPS ▲ > 25%** — lợi nhuận tăng mạnh
- [ ] **Rev ▲ > 0%** — doanh thu đang tăng (không chỉ cắt chi phí)
- [ ] **Loại: 🚀 Tăng trưởng** — xác nhận growth stock

### Quy tắc vào lệnh:
1. Chờ tất cả checklist ✅ → MUA tại breakout "B"
2. Stoploss: đặt dưới đáy pivot gần nhất (7-8% max loss)
3. Nếu thiếu 1-2 điều kiện → THEO DÕI, không mua
4. Nếu SEPA < 3 hoặc U/D Vol < 0.7 → TRÁNH hoàn toàn

### Quy tắc bán:
1. Giá giảm 7-8% từ điểm mua → cắt lỗ ngay (Minervini iron rule)
2. Giá vượt fair value → cân nhắc chốt lời 1 phần
3. SEPA giảm từ 7 xuống < 4 → bán hết
4. U/D Vol chuyển sang "Phân phối" → cảnh giác bán

---

## VSA (Volume Spread Analysis) — Nhận diện nến trên chart

VSA phân tích mối quan hệ giữa **Volume** (khối lượng), **Spread** (biên độ thanh bar), và **Close Position** (vị trí đóng cửa) để phát hiện smart money đang làm gì.

### Cách đọc 3 yếu tố:
- **Volume**: so với trung bình 20 phiên (cao/thấp)
- **Spread**: biên độ high-low so với trung bình 20 phiên (rộng/hẹp)
- **Close Position**: close gần high (buyer mạnh) hay gần low (seller mạnh)

### 8 nến VSA trên chart:

#### Bullish (tín hiệu tích cực):

**SV — Stopping Volume** 🟢
- Volume cực cao (> 2x avg 20 phiên) + spread lớn + close gần high (> 50% range) + **bar giảm** (close < close trước)
- Xuất hiện khi giá đang giảm (< MA50)
- Ý nghĩa: Bar giảm nhưng smart money đang **hấp thụ** bán ra → close bật lên gần high. Đáy có thể đang hình thành.
- Hành động: Theo dõi, chờ xác nhận bằng No Supply sau đó

**NS — No Supply** 🟢
- Volume thấp (< 50% avg 20 phiên) + spread nhỏ (< 50% avg spread) + giá giảm nhẹ
- Có ý nghĩa ở vùng đáy HOẶC vùng tích lũy (không nhất thiết phải < MA50)
- Ý nghĩa: Không còn ai muốn bán nữa. Selling đã cạn kiệt.
- Hành động: Nếu xuất hiện SAU Stopping Volume hoặc trong vùng tích lũy → tín hiệu sắp breakout

**SC — Selling Climax** 🟢
- Volume cao nhất 50 ngày + giá giảm mạnh (> 3%)
- Ý nghĩa: Bán tháo hoảng loạn ở đáy. Smart money đang gom hàng từ retail sợ hãi.
- Hành động: KHÔNG mua ngay. Chờ Test hoặc No Supply xác nhận đáy.

**AB — Absorption** 🟢
- Volume cao (> 2x avg 20 phiên) + spread RẤT nhỏ + giá gần như không đổi
- Ý nghĩa: Volume lớn nhưng giá không giảm → smart money đang "nuốt" toàn bộ supply
- Hành động: Bullish ngầm. Giá sắp tăng khi supply hết.

**SOS — Sign of Strength** 🟢
- Volume cao (> 1.5x avg 20 phiên) + spread rộng (> avg) + close gần high + giá tăng mạnh (> 2%)
- Thường xuất hiện SAU Stopping Volume, Selling Climax, hoặc No Supply (context lý tưởng)
- Nhưng bất kỳ phiên tăng mạnh + vol cao breakout khỏi vùng tích lũy đều tính là SOS
- Ý nghĩa: Xác nhận smart money đã gom xong và bắt đầu đẩy giá lên. Tín hiệu chuyển từ tích lũy sang uptrend.
- Hành động: Điểm mua. Đặc biệt mạnh nếu vượt resistance/pivot.

#### Bearish (tín hiệu tiêu cực):

**UT — Upthrust** 🔴
- Volume cao (> 1.5x avg 20 phiên) + wick trên dài (> 60% spread) + close gần low
- Xuất hiện khi giá đang tăng (> MA50)
- Ý nghĩa: Smart money **trap buyers** — đẩy giá lên cao rồi xả hàng. Retail mua ở đỉnh bị kẹt.
- Hành động: Cẩn thận, có thể đảo chiều giảm

**ND — No Demand** 🔴
- Volume thấp (< 50% avg 20 phiên) + spread nhỏ + giá tăng nhẹ
- Xuất hiện khi giá trên MA50 (vùng đỉnh)
- Ý nghĩa: Giá tăng nhưng KHÔNG CÓ AI thực sự muốn mua. Tăng giả, sắp giảm.
- Hành động: KHÔNG mua. Nếu nhiều No Demand liên tiếp → chuẩn bị bán

**SOW — Sign of Weakness** 🔴
- Volume cao (> 1.5x avg 20 phiên) + spread rộng (> avg) + close gần low + giá giảm mạnh (> 2%)
- Xuất hiện SAU Upthrust hoặc No Demand liên tiếp
- Ý nghĩa: Xác nhận smart money đã bán xong, giá bắt đầu giảm thực sự. Tín hiệu chuyển từ phân phối sang downtrend.
- Hành động: BÁN. Không cố giữ.

### Cách đọc VSA kết hợp context:

**Sequence bullish điển hình (ở đáy):**
```
SC (Selling Climax) → SV (Stopping Volume) → NS (No Supply) → SOS (Sign of Strength) → Breakout ▲
```

**Sequence bearish điển hình (ở đỉnh):**
```
ND (No Demand) → ND → UT (Upthrust) → SOW (Sign of Weakness) → Breakdown ▼
```

### Quy tắc quan trọng:
1. VSA chỉ có ý nghĩa khi xét CONTEXT (vùng đỉnh hay đáy)
2. 1 nến đơn lẻ không đủ → cần sequence (2-3 nến liên tiếp xác nhận)
3. VSA bullish ở đáy + MF Score > 70 + SEPA đang cải thiện = tín hiệu mạnh nhất
