# CarLauncher OTA Releases

Kho lưu trữ bản cài đặt công khai (OTA) cho **CarLauncher** (`com.car.launcher`).

## Phiên bản hiện tại: `v1.0.5` (`versionCode: 10005`)

- **Tải APK trực tiếp**: [`dist/car-launcher-debug.apk`](https://raw.githubusercontent.com/chuoinho/car-launcher-releases/main/dist/car-launcher-debug.apk)
- **OTA Manifest**: [`dist/version.json`](https://raw.githubusercontent.com/chuoinho/car-launcher-releases/main/dist/version.json)
- **SHA-256 (APK)**: `2a3c8a564325e7e538c6fa6f59520136c1456394deebf0a0f1fd283cf957ab67`
- **Chứng chỉ ký APK (SHA-256)**: `AD:A8:1F:91:3F:11:3A:56:E7:B3:4B:4F:7B:DB:45:33:FF:CA:68:47:24:5D:86:CD:E9:C9:78:68:66:6B:63:5B`

### Thay đổi trong v1.0.5
- Nâng cấp `AdbMdns` dùng `NsdManager.registerServiceInfoCallback` + `getHostAddresses()` và so khớp IPv4/IPv6 theo byte (bỏ qua suffix `%wlan0`) trên Android 14–17.
- Sửa `AttributionSource.Builder` (bổ sung `setPackageName`) khi `CarDisplayServer` bàn giao Binder về app, tăng timeout tìm cổng connect lên `10s`, và ghi chi tiết mã lỗi `lastFailure`.
- Bật `PhoneAppsJournal` ngay khi khởi động app, bổ sung dòng trạng thái `ADB:` trong báo cáo chẩn đoán, sửa nhãn `"Chờ kết nối xe"` gây hiểu nhầm thành `"Đang khởi động Engine…"` / `"Khởi động Engine thất bại"`, và thêm nút thử cấp lại quyền `WRITE_SECURE_SETTINGS` ngay tại thẻ Chống khóa ngân hàng.
