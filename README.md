# ESP32 OneButton LED Control

## Giới thiệu dự án
Đây là bài tập thực hành tuần 3 ứng dụng IoT nhằm điều khiển trạng thái của đèn LED ngoài thông qua các sự kiện nút nhấn nâng cao. Dự án sử dụng bo mạch ESP32 và thư viện `OneButton` để xử lý các thao tác nhấn không bị dội phím và không cần dùng hàm `delay()`, giúp hệ thống phản hồi mượt mà hơn.

**Tác giả:** Nguyễn Trọng Tùng - Sinh viên K68 Kỹ thuật Điện tử và Tin học (Trường Đại học Khoa học Tự nhiên, ĐHQGHN).

## Tính năng cốt lõi
Dự án được lập trình để nhận diện 2 thao tác điều khiển độc lập trên cùng một nút nhấn (sử dụng nút BOOT có sẵn trên mạch):
* **Single Click (Nhấn một lần):** Đảo trạng thái đèn LED (Bật thành Tắt, Tắt thành Bật).
* **Double Click (Nhấn đúp hai lần):** Chuyển đèn LED sang chế độ nhấp nháy liên tục (Blink) với chu kỳ 200ms.

## Yêu cầu phần cứng
* 1x Bo mạch phát triển **ESP32 Devkit V1**.
* 1x Đèn LED (Màu sắc tùy ý).
* 1x Điện trở hạn dòng (220Ω).
* 2 dây cắm và Breadboard.

### Sơ đồ đấu nối
| Linh kiện | Chân trên ESP32 | Hướng dẫn kết nối |
| :--- | :--- | :--- |
| **Đèn LED (Cực dương - Chân dài)** | `D18` (GPIO 18) | Cắm tín hiệu điều khiển trực tiếp vào chân D18. |
| **Đèn LED (Cực âm - Chân ngắn)** | `GND` | Nối tiếp qua con điện trở 220Ω rồi cắm về chân GND để hạn dòng, tránh cháy LED. |
| **Nút nhấn (Nút BOOT có sẵn)** | `D0` (GPIO 0) | Nút nhấn đã được tích hợp sẵn trên mạch Devkit V1, không cần nối thêm dây. |

## Yêu cầu phần mềm & Môi trường phát triển
* IDE: **Visual Studio Code**.
* Công cụ biên dịch: **PlatformIO IDE**.
* Framework: Arduino.
* Thư viện phụ thuộc: `mathertel/OneButton @ ^2.6.1`.

## Hướng dẫn cài đặt và Nạp code
1. **Clone dự án:** Tải hoặc dùng lệnh `git clone` để đưa toàn bộ mã nguồn này về máy tính.
2. **Mở bằng VS Code:** Mở thư mục gốc của dự án (nơi chứa file `platformio.ini`) bằng Visual Studio Code.
3. **Kết nối phần cứng:** Dùng cáp Micro-USB / Type-C (loại có khả năng truyền dữ liệu) kết nối bo mạch ESP32 Devkit V1 với máy tính.
4. **Biên dịch & Tải thư viện:** Nhấn nút **Build (biểu tượng dấu ✓)** ở thanh trạng thái dưới cùng của PlatformIO. Hệ thống sẽ tự động tải thư viện `OneButton` và framework Arduino về máy.
5. **Nạp code (Upload):** Nhấn nút **Upload (biểu tượng mũi tên →)** ở thanh trạng thái để đẩy mã nguồn xuống vi điều khiển. Đợi Terminal báo `[SUCCESS]` là hoàn thành.

## Cấu hình `platformio.ini`
Dự án sử dụng file cấu hình sau để định nghĩa các tham số biên dịch và thay đổi chân cắm (LED_PIN = 18) trực tiếp qua `build_flags` mà không cần can thiệp vào file `main.cpp`:

	'-D BTN_ACT=LOW'
	'-D LED_PIN=18U'
	'-D LED_ACT=HIGH'
