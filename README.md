# Foldable HID Controller

Ứng dụng biến điện thoại gập (Foldable) hoặc điện thoại Android thông thường thành **bàn phím đầy đủ + trackpad đa điểm** điều khiển máy tính Windows qua **Bluetooth HID**, **Bluetooth SPP**, **Wi-Fi LAN** hoặc **USB Tethering**.

*(Turn your foldable or Android phone into a full keyboard + precision multi-touch trackpad for Windows via Bluetooth HID, Bluetooth SPP, Wi-Fi LAN, or USB Tethering.)*

---

## Tính năng chính / Key Features

- **Tối ưu cho điện thoại gập (Foldable-aware)**:
  - **Màn hình ngoài (gập)**: Tự xoay ngang, chia đôi Bàn phím / Trackpad trái-phải.
  - **Màn hình trong (mở)**: Chia đôi Trên / Dưới hoặc phóng to toàn màn hình riêng từng phần (**KB Full** / **Pad Full**).
- **4 chế độ kết nối linh hoạt**:
  1. **Bluetooth SPP** (`bt:spp` + `FoldableHidReceiver.exe`): Kết nối dễ dàng chỉ cần pair Bluetooth bình thường trong Windows.
  2. **Wi-Fi LAN** (`FoldableHidReceiver.exe`): Tự động dò tìm điện thoại trong cùng mạng Wi-Fi (UDP broadcast port `29786` -> TCP `29785`).
  3. **USB Tethering / ADB Forward** (`FoldableHidReceiver.exe`): Độ trễ cực thấp qua cáp USB.
  4. **Bluetooth HID thuần** (`BluetoothHidDevice`): Không cần chạy app trên Windows.
- **Bàn phím đầy đủ 6 hàng (Full 6-row Keyboard)**: Có `Esc`, `F1`–`F12`, `PrtSc`, `Ins`, `Del`, `Home`, `PgUp`, `PgDn`, `End`, cụm mũi tên, phím modifier hỗ trợ giữ/latch (`Ctrl`, `Shift`, `Alt`, `Win`), phân biệt màu sắc rõ ràng theo 5 nhóm phím (phím chức năng nền đen, phím chữ & số sáng, phím dấu, phím Space, cụm mũi tên, phím Enter chữ & viền cam).
- **Trackpad đa điểm & chỉnh độ nhạy**: Thanh trượt chỉnh tốc độ con trỏ (`0.4x`–`3.0x`, tự động lưu), hỗ trợ chạm/kéo 1–3 ngón.
- **Chống lưu ảnh OLED (Burn-in Protection)**: Nền đen thuần (`#000000`), dịch chuyển điểm ảnh định kỳ (`Pixel Shift`), và tự làm dịu màn hình khi không thao tác (`Auto-Dim`).

---

## 1. Cài đặt / Installation

Tải các file phát hành mới nhất từ mục **Releases**:
- **Android**: Tải file `.apk` (`app-release.apk`) và cài đặt lên điện thoại Android (Android 9 / API 28 trở lên).
- **Windows**: Tải file `FoldableHidReceiver.exe` (chạy trực tiếp trên Windows 10/11, không cần cài đặt).

---

## 2. Hướng dẫn kết nối / Connection Guide

### Cách 1: Bluetooth SPP — Dễ nhất cho không dây (khuyên dùng với `FoldableHidReceiver.exe`)
1. Pair Bluetooth giữa điện thoại và máy tính trong **Windows Settings** như bình thường.
2. Mở `FoldableHidReceiver.exe` trên Windows (biểu tượng ở khay hệ thống).
3. Trên điện thoại: chọn tab **BT** -> bấm vào chip trạng thái kết nối -> chọn **Bluetooth SPP (PC Receiver)**.
4. Windows sẽ tự động kết nối tới điện thoại (`Connected (BT: ...)`).

### Cách 2: Wi-Fi LAN — Tự động tìm nhau không cần dây
1. Đảm bảo điện thoại và Windows kết nối **cùng một mạng Wi-Fi**.
2. Mở `FoldableHidReceiver.exe` trên Windows.
3. Trên điện thoại: chọn tab **USB** -> bấm chip trạng thái -> chọn **USB Tethering (Port 29785)**.
4. `FoldableHidReceiver.exe` sẽ tự động tìm thấy điện thoại qua mạng LAN và kết nối.

### Cách 3: USB Tethering hoặc ADB Forward — Độ trễ thấp nhất
- **Dùng USB Tethering**:
  1. Cắm cáp USB truyền dữ liệu -> bật **USB Tethering** trên điện thoại.
  2. Mở `FoldableHidReceiver.exe` trên Windows.
  3. Trên điện thoại: chọn tab **USB** -> bấm chip trạng thái -> chọn **USB Tethering (Port 29785)**.
- **Dùng ADB Forward** (nếu bật USB Debugging):
  - Chạy lệnh `adb forward tcp:29785 tcp:29785` trên Windows, `FoldableHidReceiver.exe` sẽ tự kết nối qua `127.0.0.1:29785`.

### Cách 4: Bluetooth HID thuần (không cần `FoldableHidReceiver.exe`)
1. Nếu đã từng pair trước đó, hãy **Unpair / Quên thiết bị** trên cả Windows và điện thoại.
2. Mở app **Foldable HID** -> tab **BT** -> bấm chip trạng thái -> chờ báo `HID profile ready` -> bấm **Make Discoverable**.
3. Trên Windows: vào **Add device -> Bluetooth** để pair lại trong lúc app vẫn đang mở, sau đó chọn tên máy tính trên app để kết nối.

---

## 3. Hướng dẫn sử dụng / Usage

### Thanh công cụ trên cùng
- **BT / USB**: Chuyển đổi chế độ kết nối Bluetooth hoặc USB/Wi-Fi.
- **Chip trạng thái**: Xem trạng thái hiện tại và bấm để mở hộp thoại chọn thiết bị / ngắt kết nối.
- **Tune (`1.4x`)**: Mở thanh trượt chỉnh độ nhạy Trackpad (`0.4x` – `3.0x`) + nút **Reset**.
- **Middle**: Nhấn/giữ chuột giữa.
- **Swap**: Đảo vị trí Trackpad và Bàn phím (Trái ↔ Phải hoặc Trên ↔ Dưới).
- **KB Full / Pad Full / Exit Full**: Phóng to riêng Bàn phím hoặc Trackpad toàn màn hình.
- **`(i)`**: Xem thông tin ứng dụng, phiên bản, tác giả và đổi ngôn ngữ thông tin (Tiếng Việt / English).

### Cử chỉ Trackpad
- **Kéo 1 ngón**: Di chuyển con trỏ chuột.
- **Chạm 1 ngón**: Click chuột trái.
- **Chạm 2 ngón**: Click chuột phải.
- **Kéo 2 ngón**: Cuộn trang dọc và ngang.
- **Chạm 3 ngón**: Click chuột giữa.

### Menu chuột phải của `FoldableHidReceiver.exe` (System Tray)
- **Reconnect**: Kết nối lại ngay lập tức.
- **Set IP...**: Nhập IP thủ công (để trống để tự động dò).
- **Diagnostics...**: Xem danh sách adapter mạng, IP và lỗi kết nối chi tiết.
- **Start with Windows**: Tự khởi động cùng Windows.

---

```
(Yêu cầu .NET Framework 4.x có sẵn trên Windows).
