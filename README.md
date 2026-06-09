# GobotEA FREE v6.6.2

**Expert Advisor đa chiến lược cho MetaTrader 5**

> Phiên bản FREE hoàn toàn miễn phí, không giới hạn thời gian, không cần đăng ký.  
> Nâng cấp lên **PRO** để mở khóa 8 chiến lược + BB Sideway + Hedge tại [gobotfx.com](https://gobotfx.com)

---

## Mục lục

- [Tính năng](#tính-năng)
- [Yêu cầu hệ thống](#yêu-cầu-hệ-thống)
- [Cài đặt](#cài-đặt)
- [Cấu hình tham số](#cấu-hình-tham-số)
- [Hướng dẫn sử dụng Panel](#hướng-dẫn-sử-dụng-panel)
- [Chiến lược Grid Total TP](#chiến-lược-grid-total-tp)
- [Ví dụ cấu hình](#ví-dụ-cấu-hình)
- [Lưu ý quan trọng](#lưu-ý-quan-trọng)
- [So sánh FREE vs PRO](#so-sánh-free-vs-pro)
- [Hỗ trợ](#hỗ-trợ)

---

## Tính năng

- **2 slot độc lập** — chạy 2 chiến lược khác nhau cùng lúc trên cùng một biểu đồ
- **Grid Total TP BUY** — lưới lệnh mua, chốt lời tổng
- **Grid Total TP SELL** — lưới lệnh bán, chốt lời tổng
- **Range filter** — giới hạn vùng giá hoạt động
- **Lot multiplier** — tăng lot theo cấp số nhân
- **Panel giao diện** — hiển thị thông tin real-time, có nút Start/Stop/Close từng slot
- **Toggle collapse** — thu gọn panel khi cần không gian biểu đồ
- **Không cần licence** — dùng ngay, không cần đăng ký

---

## Yêu cầu hệ thống

| Yêu cầu | Chi tiết |
|---|---|
| Nền tảng | MetaTrader 5 (MT5) |
| Loại tài khoản | Hedge account (cho phép cả BUY và SELL cùng lúc) |
| Symbol | Tất cả cặp tiền, vàng, chỉ số, crypto |
| Timeframe | Bất kỳ (EA chạy theo tick, không phụ thuộc TF) |

---

## Cài đặt

### Bước 1 — Tải file

Download file `GobotEA_v662_FREE.ex5` từ trang [Releases](../../releases).

### Bước 2 — Copy vào thư mục MT5

Mở MT5 → menu **File** → **Open Data Folder** → vào thư mục:

```
MQL5 > Experts
```

Copy file `.ex5` vào đây.

### Bước 3 — Gắn vào biểu đồ

1. Mở **Navigator** (Ctrl+N)
2. Tìm `GobotEA_v662_FREE` trong mục **Expert Advisors**
3. Kéo thả vào biểu đồ bất kỳ
4. Tick vào **Allow algo trading** → nhấn **OK**

### Bước 4 — Bật Auto Trading

Nhấn nút **Algo Trading** trên toolbar MT5 (hoặc Ctrl+E) để bật.

---

## Cấu hình tham số

### SLOT 1 / SLOT 2

Mỗi slot có bộ tham số riêng hoàn toàn độc lập.

| Tham số | Mô tả | Mặc định |
|---|---|---|
| `Strategy` | Chọn chiến lược: OFF / Grid Total BUY / Grid Total SELL | Grid Total BUY |
| `Lot` | Lot size lệnh đầu tiên | 0.01 |
| `Multi` | Hệ số nhân lot mỗi lần thêm lệnh (1.0 = không nhân) | 1.0 |
| `Spacing` | Khoảng cách tối thiểu (tính theo giá) giữa 2 lệnh liên tiếp | 5.0 |
| `MaxOrders` | Số lệnh tối đa của slot này | 5 |
| `TP` | Khoảng cách chốt lời (tính theo giá) tính từ giá trung bình | 3.0 |
| `Magic` | Magic number để phân biệt lệnh của từng slot | 88001 / 88002 |
| `RangeLow` | Giới hạn dưới vùng hoạt động (0 = không giới hạn) | 0.0 |
| `RangeHigh` | Giới hạn trên vùng hoạt động (0 = không giới hạn) | 0.0 |

### SETTINGS

| Tham số | Mô tả | Mặc định |
|---|---|---|
| `Slippage` | Slippage tối đa cho phép (tính theo point) | 200 |

---

## Hướng dẫn sử dụng Panel

Panel hiển thị góc trên bên trái biểu đồ. Nhấn nút **`-`** / **`+`** trên title bar để thu gọn hoặc mở rộng.

```
┌─────────────────────────────────────────┐
│ GobotEA v6.6.2 gobotfx.com [FREE]  [-]  │  ← Title bar + Toggle
├─────────────────────────────────────────┤
│ FREE VERSION - Upgrade to PRO at ...    │  ← Watermark
│ ACCOUNT    1234567                      │
│ BALANCE    $1,000.00                    │
│ TOTAL P&L  $+12.50                      │  ← Tổng P&L toàn EA
│ ─────────────────────────────────────── │
│ S1  Total TP [BUY]              $+8.20  │  ← Tên strategy + P&L slot
│ lot=0.01  sp=5.0  max=5  tp=3.0  m88001 │  ← Cấu hình
│ Range: ALL (no limit)                   │  ← Trạng thái range
│ BUY 3  |  SELL 0          RUN           │  ← Số lệnh + trạng thái
│ [  START  ] [  STOP  ] [ CLOSE(3) ]     │  ← Nút điều khiển
│ ─────────────────────────────────────── │
│ S2  OFF                                 │
│ ─────────────────────────────────────── │
│   RUNNING                               │  ← Trạng thái tổng
│ [  START  ] [   STOP   ]                │  ← Nút tổng
└─────────────────────────────────────────┘
```

### Các nút điều khiển

| Nút | Chức năng |
|---|---|
| **START** (tổng) | Bật tất cả slot đang active cùng lúc |
| **STOP** (tổng) | Dừng tất cả slot, giữ nguyên lệnh đang mở |
| **START** (từng slot) | Bật riêng slot đó |
| **STOP** (từng slot) | Dừng riêng slot đó, giữ nguyên lệnh |
| **CLOSE(n)** | Đóng toàn bộ lệnh của slot đó (có xác nhận) |

### Trạng thái slot

| Trạng thái | Màu | Ý nghĩa |
|---|---|---|
| `RUN` | Xanh lá | Slot đang hoạt động bình thường |
| `STOP` | Đỏ mờ | Slot đang dừng |

---

## Chiến lược Grid Total TP

### Grid Total TP BUY

Chiến lược mở lưới lệnh BUY và chốt lời tổng khi giá phục hồi.

**Nguyên lý hoạt động:**

```
Giá thị trường
     │
     ▼
Lệnh BUY #1 @ 1.0900  (lot = 0.01)
     │ (giá giảm thêm Spacing)
     ▼
Lệnh BUY #2 @ 1.0895  (lot = 0.01 × Multi)
     │ (giá giảm thêm Spacing)
     ▼
Lệnh BUY #3 @ 1.0890  ...
     │
     ▼ (giá tăng trở lại)
Giá trung bình (avg) + TP → ĐÓNG TẤT CẢ
```

**Ví dụ cụ thể** (Spacing=5, TP=3, Lot=0.01, Multi=1.0):

| Lệnh | Giá vào | Lot |
|---|---|---|
| BUY #1 | 1.09000 | 0.01 |
| BUY #2 | 1.08995 | 0.01 |
| BUY #3 | 1.08990 | 0.01 |
| Giá TB | 1.08995 | — |
| **TP tại** | **1.08998** | Đóng tất cả |

### Grid Total TP SELL

Hoạt động ngược chiều với BUY — mở lưới SELL khi giá tăng, chốt lời khi giá quay đầu xuống.

### Range Filter

Khi set `RangeLow` và `RangeHigh`:
- EA chỉ mở lệnh mới khi giá **nằm trong** vùng `[RangeLow, RangeHigh]`
- Khi giá ra ngoài vùng → **không làm gì cả** (không mở lệnh, không TP)
- Để tắt range filter: đặt cả 2 về `0.0`

> **Lưu ý v6.6.1+:** Khi giá ngoài range, EA hoàn toàn dừng kể cả TP. Lệnh cũ được giữ nguyên cho đến khi giá quay vào vùng.

### Lot Multiplier

Khi `Multi > 1.0`, lot size sẽ tăng theo cấp số nhân:

```
Level 0 (lệnh 1): Lot × Multi^0 = Lot
Level 1 (lệnh 2): Lot × Multi^1
Level 2 (lệnh 3): Lot × Multi^2
...
```

**Ví dụ** (Lot=0.01, Multi=1.5):

| Lệnh | Lot |
|---|---|
| #1 | 0.01 |
| #2 | 0.02 |
| #3 | 0.02 |
| #4 | 0.03 |
| #5 | 0.05 |

> ⚠️ **Cảnh báo:** Multi > 1.5 kết hợp MaxOrders lớn có thể tạo ra lot rất cao. Tính toán kỹ trước khi dùng trên tài khoản thật.

---

## Ví dụ cấu hình

### Cấu hình 1: Grid BUY đơn giản

Phù hợp cho người mới, rủi ro thấp.

```
Strategy  = Grid Total TP [BUY]
Lot       = 0.01
Multi     = 1.0
Spacing   = 10.0
MaxOrders = 5
TP        = 5.0
Magic     = 88001
RangeLow  = 0.0
RangeHigh = 0.0
```

### Cấu hình 2: Grid BUY + SELL đồng thời (2 slot)

Slot 1 chạy BUY, Slot 2 chạy SELL — hai chiều cùng lúc.

```
--- SLOT 1 ---
Strategy  = Grid Total TP [BUY]
Lot       = 0.01
Spacing   = 8.0
MaxOrders = 5
TP        = 4.0
Magic     = 88001

--- SLOT 2 ---
Strategy  = Grid Total TP [SELL]
Lot       = 0.01
Spacing   = 8.0
MaxOrders = 5
TP        = 4.0
Magic     = 88002
```

> ⚠️ **Lưu ý:** Mỗi slot phải có Magic number khác nhau. EA sẽ báo lỗi nếu trùng Magic.

### Cấu hình 3: Grid BUY trong vùng range

Chỉ hoạt động khi giá XAUUSD trong vùng 2300–2350.

```
Strategy  = Grid Total TP [BUY]
Lot       = 0.01
Spacing   = 5.0
MaxOrders = 5
TP        = 3.0
Magic     = 88001
RangeLow  = 2300.0
RangeHigh = 2350.0
```

---

## Lưu ý quan trọng

### Rủi ro

- Grid trading là chiến lược **martingale/averaging** — rủi ro drawdown cao nếu thị trường đi một chiều dài
- Luôn test trên **Demo account** trước khi dùng tài khoản thật
- Không dùng toàn bộ balance, chỉ dùng phần vốn chấp nhận được rủi ro

### Magic Number

- Mỗi slot **bắt buộc** phải có Magic number khác nhau
- Không trùng với Magic của EA khác đang chạy trên cùng tài khoản
- Magic mặc định: Slot 1 = 88001, Slot 2 = 88002

### Spacing và TP

- `Spacing` và `TP` tính theo **đơn vị giá** (price), không phải pip hay point
- Ví dụ EURUSD: Spacing=5 tương đương 5 pip (0.00050)
- Ví dụ XAUUSD: Spacing=5 tương đương $5

### Tài khoản Hedge

- EA yêu cầu tài khoản **Hedge** (cho phép giữ BUY và SELL cùng lúc)
- Tài khoản **Netting** không tương thích khi dùng 2 slot cùng chiều

---

## So sánh FREE vs PRO

| Tính năng | FREE | PRO |
|---|:---:|:---:|
| Số slot | 2 | 3 |
| Grid Total TP BUY | ✅ | ✅ |
| Grid Total TP SELL | ✅ | ✅ |
| Grid Individual TP | ❌ | ✅ |
| Grid Hedge Dual | ❌ | ✅ |
| Sideway Dual | ❌ | ✅ |
| BB Sideway Auto Range | ❌ | ✅ |
| BB Buy/Sell Mean Reversion | ❌ | ✅ |
| BB Auto-Close | ❌ | ✅ |
| Auto Start/Stop theo range | ❌ | ✅ |
| Spacing riêng BUY/SELL | ❌ | ✅ |
| Licence bảo mật | Không cần | ✅ |
| Giá | **Miễn phí** | **$49/năm** |

👉 Nâng cấp PRO tại [gobotfx.com](https://gobotfx.com)

---

## Hỗ trợ

- 🌐 Website: [gobotfx.com](https://gobotfx.com)
- 💬 Support: [gobotfx.com/support](https://gobotfx.com/support)
- 📊 Dashboard: [gobotfx.com/dashboard](https://gobotfx.com/dashboard)

---

## Changelog

### v6.6.2
- Tách bản FREE và PRO riêng biệt
- Thêm nút toggle +/- thu gọn/mở rộng panel
- Hiển thị tổng P&L toàn EA ở header
- Bỏ icon emoji ở nút START/STOP/CLOSE
- Fix hiển thị title bar trên MT5

### v6.6.1
- Khi giá ngoài range → không làm gì cả (không TP, không mở lệnh mới)

### v6.6.0
- Phiên bản đầu tiên phát hành công khai

---

*GobotEA FREE © 2024 [GobotFX](https://gobotfx.com). All rights reserved.*
