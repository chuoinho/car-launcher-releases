# CarLauncher OTA Releases

Kho lưu trữ bản cài đặt công khai (OTA) cho **CarLauncher** (`com.car.launcher`).

## Phiên bản hiện tại: `v1.0.9` (`versionCode: 10009`)

- **Tải APK trực tiếp**: [`dist/car-launcher-debug.apk`](https://raw.githubusercontent.com/chuoinho/car-launcher-releases/main/dist/car-launcher-debug.apk)
- **OTA Manifest**: [`dist/version.json`](https://raw.githubusercontent.com/chuoinho/car-launcher-releases/main/dist/version.json)
- **SHA-256 (APK)**: `2108bc3ed75fff544a0ffcc7f5f9f22351f9f84234bfbb8e1c976ed27da5b2b2`
- **Chứng chỉ ký APK (SHA-256)**: `AD:A8:1F:91:3F:11:3A:56:E7:B3:4B:4F:7B:DB:45:33:FF:CA:68:47:24:5D:86:CD:E9:C9:78:68:66:6B:63:5B`

### Thay đổi trong v1.0.9
- **Thanh Dock tự co giãn thông minh (`Adaptive Rail`)**: tự động thu nhỏ kích thước nút & khoảng đệm trên màn hình thấp/hẹp (`800×480`, `1024×600`, `1280×500`, `720p@220-240dpi`, dọc `480×853dp`) để **luôn hiển thị nút `Back` và `Gọi rảnh tay`**; thêm cử chỉ **vuốt 3 ngón** chỉnh nhanh âm lượng xe (`CarVolumeHud`) hoặc về Trang chủ.
- **Thanh điều khiển `SlotMiniBar` tự ẩn sau 4 giây & Bố cục 3 cột Ultrawide**: thay cụm nút nổi cố định bằng thanh mini trên đỉnh từng khe tự thu gọn thành vạch mảnh (`0%` che khuất YouTube/Maps), tích hợp **Lùi, Đổi app, Tải lại, Đổi chỗ, Tỷ lệ đang bật (`70/30` | `50/50`), Toàn màn hình, Đóng hẳn app**; mở đồng thời **Khe chính + Khe phụ + Cột Thông tin** trên màn Ultrawide (`1920×720+`).
- **Kho ứng dụng & Quản lý tiến trình trên xe**: hỗ trợ **tìm kiếm tiếng Việt không dấu** (`foldVietnameseSearch`), bảng **`Đang chạy / Đóng tất cả`**, phân biệt app trùng tên, ưu tiên gợi ý app Dẫn đường & Nhạc/Video và thiết kế lại tab **App trên xe** 3 trạng thái trên điện thoại (đồng bộ sao lưu `pinned_car_apps`).
- **Đồng bộ Ban đêm `VirtualDisplay` & Hoàn thiện vận hành**: đồng bộ `uimode night` vào khung ứng dụng nhúng theo đèn xe (tự khôi phục khi rời xe), không vô hiệu hóa `VirtualDevice` khi gặp app `FLAG_SECURE`, khóa focus hộp thoại Rotary/Touchpad, khôi phục âm thanh `PhoneMute`, bong bóng tốc độ kéo thả tự xóa biển cũ và đồng bộ ngôn ngữ `CarLauncher`.
