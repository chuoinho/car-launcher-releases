# CarLauncher OTA Releases

Kho lưu trữ bản cài đặt công khai (OTA) cho **CarLauncher** (`com.car.launcher`).

## Phiên bản hiện tại: `v1.0.8` (`versionCode: 10008`)

- **Tải APK trực tiếp**: [`dist/car-launcher-debug.apk`](https://raw.githubusercontent.com/chuoinho/car-launcher-releases/main/dist/car-launcher-debug.apk)
- **OTA Manifest**: [`dist/version.json`](https://raw.githubusercontent.com/chuoinho/car-launcher-releases/main/dist/version.json)
- **SHA-256 (APK)**: `00a6389e4eb8e70b53e0a28dcc91e709c0675f827e3ccb7fcabefaf6f55b8433`
- **Chứng chỉ ký APK (SHA-256)**: `AD:A8:1F:91:3F:11:3A:56:E7:B3:4B:4F:7B:DB:45:33:FF:CA:68:47:24:5D:86:CD:E9:C9:78:68:66:6B:63:5B`

### Thay đổi trong v1.0.8
- Hoàn thiện chống khóa ngân hàng / VNeID (`DebugAwayController`): tự tắt cả 3 cờ (`adb_wifi_enabled`, `adb_enabled`, `development_settings_enabled`) ngay lập tức khi bật tính năng ở ngoài xe, xóa marker khôi phục Wi-Fi và giải phóng `CarDisplayClient`.
- Đếm ngược rời xe **10 giây** kèm `JobScheduler` dự phòng (`OffJob` + `runScheduledOffJob`) và 2 nút thao tác nhanh trên thông báo (**Tắt ngay** / **Giữ bật lần này**).
- Khóa kín mọi luồng nền (`blocksEnable`) trên `AdbRecoveryJob`, `CarDisplayClient`, `ServerStarter`, warmup audio/Shizuku và `PhoneCompanionScreen`, không để app tự bật lại ADB khi đang ẩn (kể cả ẩn thủ công).
- Đánh thức sớm khi kết nối Bluetooth xe (`WirelessReceiver`), bỏ qua toggle ADB giữa phiên USB nếu đang tắt, xử lý rời `CarPreviewActivity`, và thêm nút chuyển nhanh **Chế độ Ngân hàng** ↔ **Bật lại màn xe** ngay trên notification của `ProjectionService`.
- Đồng bộ trạng thái thực tế lên thẻ Trang chủ & đèn kiểm tra sẵn sàng (`CarReadinessChecks` giữ đèn `dev`/`server` xanh khi đang bảo vệ ngân hàng).
