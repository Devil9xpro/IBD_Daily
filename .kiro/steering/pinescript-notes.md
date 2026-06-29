---
inclusion: auto
---

# PineScript v6 — Ghi chú quan trọng

## Các lỗi thường gặp (PHẢI NHỚ)

### 1. `plotbar()` và `plotcandle()` KHÔNG có `linewidth`
- Không có cách nào tăng độ dày thanh bar từ code PineScript
- Muốn bar dày hơn → đổi chart type sang "Bars" trong TradingView → Chart Settings → Symbol → tăng Thickness
- Dùng `barcolor()` để tô màu cho chart bars mặc định

### 2. Text formatting constants (v6)
- ✅ Đúng: `text.format_bold`, `text.format_italic`
- ❌ Sai: `text.formatting_bold`, `text.formatting_italic`
- Kết hợp: `text.format_bold + text.format_italic`
- Dùng trong: `label.new()`, `box.new()`, `table.cell()` → tham số `text_formatting`

### 3. Plot linestyle (v6 mới)
- `plot.linestyle_solid` (mặc định)
- `plot.linestyle_dashed`
- `plot.linestyle_dotted`
- Chỉ hoạt động với: `plot.style_line`, `plot.style_linebr`, `plot.style_stepline`, `plot.style_area`

### 4. `line.new()` có `width` parameter
- Dùng khi cần vẽ custom bars với độ dày tùy chỉnh
- Giới hạn: `max_lines_count` tối đa 500 (mặc định) → chỉ hiện ~250 bars gần nhất

### 5. Giới hạn TradingView Free
- Tối đa 2 indicators/chart
- 1 active alert
- `request.security()` giới hạn calls
- Không có multi-timeframe analysis nâng cao

## API Reference nhanh

### label.new() parameters (v6)
```
label.new(x, y, text, xloc, yloc, color, style, textcolor, size, textalign, tooltip, text_formatting)
```
- `text_formatting`: `text.format_bold`, `text.format_italic`, hoặc cộng cả hai

### plotbar() parameters (v6)
```
plotbar(open, high, low, close, title, color, editable, show_last, display, force_overlay)
```
- KHÔNG có: linewidth, width, bordercolor, wickcolor

### plotcandle() parameters (v6)
```
plotcandle(open, high, low, close, title, color, wickcolor, editable, show_last, bordercolor, display)
```
- KHÔNG có: linewidth, width

### Pivot detection
```
ta.pivothigh(source, leftbars, rightbars) → series float (or na)
ta.pivotlow(source, leftbars, rightbars) → series float (or na)
```
- Kết quả trả về offset `rightbars` bars về trước → dùng `bar_index - rightbars` khi vẽ label

## Nguyên tắc làm việc
1. LUÔN verify API trên TradingView docs trước khi dùng parameter/constant mới
2. Nếu không chắc → search web trước, không đoán
3. Tài liệu trong `/PineGenius/data/Data.txt` là v5 — v6 có thêm nhiều features mới
