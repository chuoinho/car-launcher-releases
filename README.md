# CarLauncher OTA Releases

Kho lưu trữ bản cài đặt công khai (OTA) cho **CarLauncher** (`com.car.launcher`).

## Phiên bản hiện tại: `v1.0.11` (`versionCode: 10011`)

- **Tải APK trực tiếp**: [`dist/car-launcher-debug.apk`](https://raw.githubusercontent.com/chuoinho/car-launcher-releases/main/dist/car-launcher-debug.apk)
- **OTA Manifest**: [`dist/version.json`](https://raw.githubusercontent.com/chuoinho/car-launcher-releases/main/dist/version.json)
- **SHA-256 (APK)**: `62266c789d661352fb22af65a6c9bc2c7d9ffdfd176cca3e09c5eabd8499a1bd`
- **Chứng chỉ ký APK (SHA-256)**: `AD:A8:1F:91:3F:11:3A:56:E7:B3:4B:4F:7B:DB:45:33:FF:CA:68:47:24:5D:86:CD:E9:C9:78:68:66:6B:63:5B`

### Thay đổi trong v1.0.11
- **Sửa triệt để lỗi `<-> Đổi chỗ` (`CarDisplayServerImpl` & `CarRuntime`)**:
  - Thêm khoảng trễ `130ms` (`SWAP_REBIND_GAP_MS`) sau khi detach cả hai surface rồi resize trước khi gắn lại vào `VirtualDisplay` đích, loại bỏ xung đột `BufferQueueProducer` khiến khung hình bị đen hoặc treo sau nhiều lần đảo khe.
  - Thêm khóa nguyên tử `swapInFlight` + chống dội `650ms` và fallback dọn sạch slot nếu một trong hai khe chưa gắn xong.
- **Sửa nút `C Tải lại` không có tác dụng (`reloadSlot`)**: force-stop toàn bộ task đang kẹt trong khe, detach/reattach lại surface (`bounceSlotSurface`) và mở lại với `FLAG_ACTIVITY_CLEAR_TASK`.
- **Sửa nút `<- Lùi` treo màn đen khi thoát root Activity (`backInSlot`)**: đồng bộ thứ tự bấm Back trên `slotOps`, sau `420ms` kiểm tra `getTopPackageSlot` — nếu khe trống hoàn toàn thì tự trả khe về giao diện chọn app (`EmptySlotPicker`) thay vì kẹt màn hình đen.
- **Khắc phục app tự reload khi đổi tỉ lệ / mở YouTube Dark Mode (`SlotBlackWatchdog`)**: không restart watchdog theo `surfaceVersion`, hạ ngưỡng pure-black xuống `luma <= 2` và kiểm tra `getTopPackageSlot` trước khi cho phép relaunch.
- **Ổn định bố cục `SlotMiniBar` & Drawer (`CarHomeTwoSlot`, `ScalableAppDrawer`)**: giữ cố định vị trí `Đổi chỗ` (làm mờ khi Fullscreen) và `70/30` (bấm khi Fullscreen sẽ thoát về split), tách `X Đóng` sau divider tránh bấm nhầm khi gõ đúp `Toàn màn`, ẩn nút focus rotary `[OpenInNew]` ở chế độ cảm ứng, thu gọn chip vừa khít cả ở chế độ `50/50` và mở rộng vùng bấm pill kéo mở lại (`104×30dp`).

### Thay đổi trong v1.0.10
- **Gỡ bỏ hoàn toàn cầu chì Safe Mode (`StartupGuard`)**: tắt vĩnh viễn cảnh báo và màn hình khóa khe trên cả điện thoại lẫn màn xe (`isSafeMode()` luôn trả `false` và tự xóa cờ cũ nếu từng bị kích hoạt).
- **Sửa lỗi lệch cảm ứng trên xe (`TouchMapper` & `:carapps`)**:
  - Nhận diện màn có margin báo tọa độ theo full codec frame (ví dụ `1024×600` trong `1280×720`, hoặc `1920×720` trong `1920×1080`) để map 1:1 thay vì vừa thu nhỏ vừa cộng dồn margin hai lần; tự chuyển chế độ tại runtime nếu phát hiện đầu xe gửi gốc `(0, 0)` hoặc scale toàn panel.
  - Sửa lỗi màn `1080p` chỉ mở luồng `720p` không margin bị hiểu nhầm thành visible-pixels gây lệch chạm 1.5x, và khử mô tả ADC ảo `4095×4095`.
  - Đồng bộ chính xác kích thước `TextureView` buffer 1:1 (bỏ ngưỡng trễ 16px) và thêm `SlotTouchTransform` để ánh xạ lại tọa độ khi app bị letterbox / xoay dọc trong `VirtualDisplay`.
- **Mở đúng app đã chọn trong khe (`Hidden.movePackageTasksToDisplay` + `launchSlot`)**: tự động di chuyển task của ứng dụng đang mở trên màn điện thoại (`display 0`) sang đúng `VirtualDisplay` đích khi chọn app trong launcher để không bị hiển thị nhầm app cũ.

### Thay đổi trong v1.0.9
- **Thanh Dock tự co giãn thông minh (`Adaptive Rail`)**: tự động thu nhỏ kích thước nút & khoảng đệm trên màn hình thấp/hẹp (`800×480`, `1024×600`, `1280×500`, `720p@220-240dpi`, dọc `480×853dp`) để **luôn hiển thị nút `Back` và `Gọi rảnh tay`**; thêm cử chỉ **vuốt 3 ngón** chỉnh nhanh âm lượng xe (`CarVolumeHud`) hoặc về Trang chủ.
- **Thanh điều khiển `SlotMiniBar` tự ẩn sau 4 giây & Bố cục 3 cột Ultrawide**: thay cụm nút nổi cố định bằng thanh mini trên đỉnh từng khe tự thu gọn thành vạch mảnh (`0%` che khuất YouTube/Maps), tích hợp **Lùi, Đổi app, Tải lại, Đổi chỗ, Tỷ lệ đang bật (`70/30` | `50/50`), Toàn màn hình, Đóng hẳn app**; mở đồng thời **Khe chính + Khe phụ + Cột Thông tin** trên màn Ultrawide (`1920×720+`).
- **Kho ứng dụng & Quản lý tiến trình trên xe**: hỗ trợ **tìm kiếm tiếng Việt không dấu** (`foldVietnameseSearch`), bảng **`Đang chạy / Đóng tất cả`**, phân biệt app trùng tên, ưu tiên gợi ý app Dẫn đường & Nhạc/Video và thiết kế lại tab **App trên xe** 3 trạng thái trên điện thoại (đồng bộ sao lưu `pinned_car_apps`).
- **Đồng bộ Ban đêm `VirtualDisplay` & Hoàn thiện vận hành**: đồng bộ `uimode night` vào khung ứng dụng nhúng theo đèn xe (tự khôi phục khi rời xe), không vô hiệu hóa `VirtualDevice` khi gặp app `FLAG_SECURE`, khóa focus hộp thoại Rotary/Touchpad, khôi phục âm thanh `PhoneMute`, bong bóng tốc độ kéo thả tự xóa biển cũ và đồng bộ ngôn ngữ `CarLauncher`.
