## Đặt bài toán 

- Phần cứng: Chỉ có một nút bấm nhả (push button) và một đèn LED hiển thị tích hợp sẵn trên các dev board điển hình
- Yêu cầu Viết chương trình có chức năng sau:
    + bấm nút một lần (single click) để bật/tắt LED (đảo trạng thái). 
    + nhấn giữ >2s (hold) thì LED sẽ chuyển sang trạng thái nhấp nháy liên tục (blink 200ms một lần)
    + nếu tiếp tục nhấn single click thì LED lại chuyển trạng thái bật/tắt 
    + Lưu ý: khử rung phím bấm 

## Mục đích DEMO

Project này sử dụng thư viện mã mở nổi tiếng gần đây là OneButton và thư viện LED tự viết:
- `OneButton` tác giả Matthias Hertel: https://github.com/mathertel/OneButton 
- `LED.h` Cung cấp API sáng sủa để khởi tạo và điều khiển LED (đảo trạng thái - flip, và nháy - blink)
- Việc gom các chức năng đọc phím bấm và điều khiển LED như trên vào các thư viện để có thể tái sử dụng, và giúp mã sáng sủa hơn. Các chức năng như trong yêu cầu xuất hiện rất phổ biến ở hầu hết tất cả các project vi điều khiển. 

Project này cũng minh họa điểm mạnh của PIO là có thể dùng chung mã nguồn cho nhiều nền tảng phần cứng khác nhau, ở đây:
- Chip ESP32 kiến trúc xtensa lõi kép
- Chip ESP32-C3 kiến trúc RISC-V lõi đơn 
