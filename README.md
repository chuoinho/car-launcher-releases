# CarLauncher OTA Releases

Kho lưu trữ bản cài đặt công khai (OTA) cho **CarLauncher** (`com.car.launcher`).

## Phiên bản hiện tại: `v1.0.7` (`versionCode: 10007`)

- **Tải APK trực tiếp**: [`dist/car-launcher-debug.apk`](https://raw.githubusercontent.com/chuoinho/car-launcher-releases/main/dist/car-launcher-debug.apk)
- **OTA Manifest**: [`dist/version.json`](https://raw.githubusercontent.com/chuoinho/car-launcher-releases/main/dist/version.json)
- **SHA-256 (APK)**: `c60ccaa9c13b0184f70ebbfd1dbea39fed11da0ca2e9695ceeb7c01aee05b1b1`
- **Chứng chỉ ký APK (SHA-256)**: `AD:A8:1F:91:3F:11:3A:56:E7:B3:4B:4F:7B:DB:45:33:FF:CA:68:47:24:5D:86:CD:E9:C9:78:68:66:6B:63:5B`

### Thay đổi trong v1.0.7
- Mặc định tắt ghi nhật ký kết nối (`connectionLogEnabled = false`), chặn đồng bộ ghi file trên cả `DiagLog`, `PhoneAppsJournal` và `SessionAapLog.verbose`, bổ sung công tắc bật/tắt và hộp thoại xác nhận xóa log ở `LogCard`.
- Gộp luồng cập nhật OTA theo **Phương án A**: giữ mục quản lý OTA đầy đủ trong **Cài đặt → Nâng cao**, chỉ hiển thị `AppOtaBannerCard` ngữ cảnh trên **Trang chủ** khi có bản cập nhật mới, đang tải, sẵn sàng cài hoặc báo lỗi.
- Chuẩn hóa toàn diện giao diện **Material Design 3** + tương phản **WCAG AA** (Day/Night `ColorScheme`, `PhoneShapes`, `CarTypography`, dual-stroke focus highlight, vùng chạm `≥ 48dp`) trên điện thoại, máy tính bảng (`NavigationRail` + bố cục 2 cột Cài đặt), màn hình xe mọi tỷ lệ (bao gồm `800×480`, `1280×720`, `1920×720`/`2560×720` ultrawide, `1024×1024` vuông) và cụm đồng hồ (`ClusterTurnCard`).
