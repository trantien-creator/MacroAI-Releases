<div align="center">

<img src="assets/smartmacroai-logo.png" alt="SmartMacroAI" width="360">

# SmartMacroAI

**Công cụ tự động hóa Windows/ADB với trình soạn kịch bản trực quan**

[![Version](https://img.shields.io/badge/version-1.3.0%20Beta.3-0078D4?style=flat-square)](https://github.com/trantien-creator/MacroAI-Releases/releases/tag/v1.3.0-beta.3)
![Platform](https://img.shields.io/badge/platform-Windows%2010%2B-0078D4?style=flat-square&logo=windows)
![.NET](https://img.shields.io/badge/.NET-8.0-512BD4?style=flat-square&logo=dotnet)
![Language](https://img.shields.io/badge/UI-Ti%E1%BA%BFng%20Vi%E1%BB%87t%20%7C%20English-F7931E?style=flat-square)
![License](https://img.shields.io/badge/license-Proprietary-8A2BE2?style=flat-square)

Phát triển bởi **Trần Tiến**

[Website](https://smartmacroai.pages.dev/) · [Tải bản phát hành](https://github.com/trantien-creator/MacroAI-Releases/releases/tag/v1.3.0-beta.3)

</div>

SmartMacroAI là ứng dụng WPF dành cho Windows, dùng để tạo, ghi, chạy và theo dõi các kịch bản tự động hóa dạng JSON. Phiên bản hiện tại hỗ trợ hai backend thực thi: **Windows/HWND** và **ADB**. Ứng dụng kết hợp thao tác chuột/phím, nhận diện ảnh, OCR, điều kiện, vòng lặp, kịch bản con, lịch chạy, Discord Webhook và HTTP API cục bộ.

> **Lưu ý về Trợ lý AI (BYOK):** Tính năng AI assistant đang trong giai đoạn tạm khóa/không nên quảng bá là tính năng hoàn chỉnh. Trợ lý AI yêu cầu BYOK (Bring Your Own Key) và chỉ hỗ trợ phân tích thủ công; SmartMacroAI không tự áp dụng đề xuất và không tự chạy macro.

## Mục lục

- [Điểm nổi bật của v1.3.0 Beta.3](#điểm-nổi-bật-của-v130-beta3)
- [Download & Integrity](#download--integrity)
- [Backend thực thi](#backend-thực-thi)
- [Trình soạn workflow](#trình-soạn-workflow)
- [Floating Overlay và tọa độ thích ứng](#floating-overlay-và-tọa-độ-thích-ứng)
- [Hành động và điều khiển luồng](#hành-động-và-điều-khiển-luồng)
- [Nhận diện ảnh và OCR](#nhận-diện-ảnh-và-ocr)
- [Yêu cầu hệ thống](#yêu-cầu-hệ-thống)
- [Bắt đầu nhanh](#bắt-đầu-nhanh)
- [ADB và giả lập Android](#adb-và-giả-lập-android)
- [HTTP API cục bộ](#http-api-cục-bộ)
- [Discord Webhook](#discord-webhook)
- [Contact / Support](#contact--support)
- [Bảo mật và giấy phép](#bảo-mật-và-giấy-phép)

## Điểm nổi bật của v1.3.0 Beta.3

- **Floating Overlay** có thể kéo, tự hút mép, thu gọn thành pill và giảm độ mờ khi macro đang chạy.
- Marker Click/Swipe trên game/giả lập: đánh số, kéo thả, bật/tắt, ẩn/hiện, chỉnh delay riêng.
- Tọa độ **Normalized 0–100%** cho Click/Swipe — tự quy đổi theo kích thước Windows/ADB hiện tại.
- Đèn trạng thái ADB: xanh sẵn sàng, vàng đang kiểm tra, đỏ mất kết nối, xám khi dùng Windows/HWND.
- Lưu vị trí overlay và marker riêng theo cửa sổ hoặc ADB serial; tiến trình marker đổi màu theo bước.
- Backend **ADB** chụp màn hình và gửi thao tác nền tới giả lập Android mà không chiếm chuột Windows.
- HTTP API chỉ lắng nghe loopback, có token xác thực, dùng chung trạng thái chạy/dừng với giao diện.
- Nhận diện ảnh đa tỉ lệ: ưu tiên scale `1.00x`, tìm thô–tinh, xác minh màu, cache template tự làm mới.
- Click ảnh theo đúng tâm vùng khớp; xử lý template ít biến thiên để giảm false positive.
- Trình soạn kịch bản dạng sơ đồ: kéo thả, đổi thứ tự, thêm/bật/tắt bước, sao chép, dán, nhân bản.
- Debugger: breakpoint, Pause, Continue, Step, Auto-follow, thời lượng bước và lịch sử trace.
- Discord Webhook cho hành động thông báo, kết quả hoàn tất và lỗi.

> **Cảnh báo thực tế:**
> - **Raw/Hardware:** Có thể chiếm chuột hoặc đưa cửa sổ đích lên foreground. Không phù hợp nếu cần chạy nền hoàn toàn.
> - **Stealth/HWND:** Phụ thuộc việc ứng dụng đích có nhận PostMessage hay không.
> - **ADB:** Chạy nền tốt nhưng thiết bị/giả lập phải ở trạng thái `device`, không phải `offline` hoặc `unauthorized`.
> - **Driver Level (Interception):** Yêu cầu cài driver, quyền Administrator và khởi động lại Windows; mức tương thích phụ thuộc ứng dụng đích.

## Download & Integrity

Đây là bản **Pre-release** (Beta.3). Chỉ tải từ trang Releases chính thức.

**Key dùng thử Beta:** [Mở trang cấp key Community](https://cyber-bike-56a.notion.site/SmartMacroAI-License-20-Thi-t-B-30-Ng-y-3d6cdffabe278141a343ea8872c11687). Key dùng chung có giới hạn thiết bị và thời hạn hiển thị trên trang.

| Asset | Size | Link |
|---|---|---|
| `SmartMacroAI-v1.3.0-beta.3-win-x64-Setup.exe` | 518 MB | [Download](https://github.com/trantien-creator/MacroAI-Releases/releases/download/v1.3.0-beta.3/SmartMacroAI-v1.3.0-beta.3-win-x64-Setup.exe) |
| `MacroAI-v1.3.0-beta.3-win-x64.zip` | 634 MB | [Download](https://github.com/trantien-creator/MacroAI-Releases/releases/download/v1.3.0-beta.3/MacroAI-v1.3.0-beta.3-win-x64.zip) |
| `SHA256SUMS.txt` | — | [Download](https://github.com/trantien-creator/MacroAI-Releases/releases/download/v1.3.0-beta.3/SHA256SUMS.txt) |

**SHA256:**
```
042dafdc4ec3f7e186d181c2211bbb79e007fd69da9e6909a248200a9059812e  SmartMacroAI-v1.3.0-beta.3-win-x64-Setup.exe
2152d79e889d2dbaa398451d928333d675c9c465fb960f9ce10c516ac6ffc055  MacroAI-v1.3.0-beta.3-win-x64.zip
```

> Bản cài đặt Beta hiện chưa có chữ ký số nên Windows SmartScreen có thể hiện cảnh báo. Hãy tải từ release chính thức và đối chiếu SHA256 trước khi chạy.

**Xác minh checksum bằng PowerShell:**

```powershell
$hash = (Get-FileHash .\MacroAI-v1.3.0-beta.3-win-x64.zip -Algorithm SHA256).Hash
Write-Host "Hash tính toán: $hash"

# So sánh với nội dung SHA256SUMS.txt đã tải về
Get-Content .\SHA256SUMS.txt
```

Nếu hash không khớp, không giải nén và không chạy file.

## Backend thực thi

| Backend | Mục đích | Hành vi chính |
|---|---|---|
| **Windows/HWND – Stealth** | Ứng dụng desktop thông thường | Gửi thông điệp tới cửa sổ, không di chuyển con trỏ vật lý khi ứng dụng đích hỗ trợ |
| **Windows/HWND – Raw Input** | Ứng dụng cần `SendInput`/scan code | Có thể cần cửa sổ đích ở foreground và có thể ảnh hưởng chuột/phím vật lý |
| **Windows/HWND – Hardware** | Mô phỏng thao tác foreground | Di chuyển con trỏ và đưa cửa sổ đích lên trước |
| **Windows/HWND – Driver Level** | Tùy chọn dùng Interception | Cần cài driver, quyền quản trị và khởi động lại Windows |
| **ADB** | Giả lập/thiết bị Android | Chụp ảnh và gửi tap, swipe, key, text ở nền, không chiếm chuột Windows |

Backend lưu trong kịch bản là lựa chọn mặc định lâu dài. Bộ chọn backend ngoài workspace và trường `backendOverride` của API chỉ áp dụng cho lần chạy hiện tại.

## Trình soạn workflow

- Hai cách xem: danh sách tuần tự và sơ đồ node/nhánh.
- Biểu diễn được bước gốc và các nhánh lồng trong `Repeat`, `Try/Catch`, `If Variable`, `If Image` và `If Text`.
- Kéo thả hoặc dùng nút mũi tên để đổi thứ tự bước ở danh sách gốc và trong nhánh lồng phù hợp.
- Thêm bước trực tiếp từ sơ đồ; bật/tắt một bước bằng nút nguồn mà không cần xóa.
- Đổi tên từng bước; sao chép, dán và nhân bản bằng menu hoặc phím tắt `F2`, `Ctrl+C`, `Ctrl+V`, `Ctrl+D`.
- Undo/Redo bằng `Ctrl+Z` và `Ctrl+Y`.
- Mỗi bước có `StepId` ổn định, đường dẫn thực thi và log tương ứng.
- Debugger workflow có breakpoint, Pause, Continue, Step, Auto-follow, thời lượng bước và lịch sử trace gần nhất.
- Tự khóa thao tác sửa/kéo thả trong khi macro đang chạy.

## Floating Overlay và tọa độ thích ứng

- Mở bằng nút **⊙ Overlay** trên thanh công cụ của trình soạn macro sau khi chọn cửa sổ hoặc thiết bị ADB.
- Thanh nổi cung cấp Run/Pause/Resume, Stop, thêm/xóa Click, thêm Swipe, ẩn marker, cài delay/repeat, thu gọn và đóng overlay.
- Click marker để sửa delay sau bước; kéo marker để đổi tọa độ; bấm chuột phải để bật/tắt bước.
- Các action tạo từ overlay lưu cả tọa độ phần trăm và kích thước tham chiếu. Engine tính lại pixel ở thời điểm chạy theo vùng client Windows hoặc độ phân giải Android hiện tại.
- Layout được lưu nguyên tử trong `%LOCALAPPDATA%\SmartMacroAI\config\floating_overlay_profiles.json` theo từng cửa sổ/ADB serial.

## Hành động và điều khiển luồng

- Click, nhập văn bản, nhấn phím, chờ, cuộn, kéo thả và chụp màn hình.
- Điều kiện theo ảnh, văn bản OCR, biến và màu pixel; hỗ trợ nhánh Then/Else.
- Repeat, Try/Catch, dừng an toàn, biến, xóa/reset biến và ghi log biến.
- Gọi kịch bản con và tự khôi phục đường dẫn tài nguyên tương đối từ bản cài đặt cũ.
- Lặp dữ liệu CSV, ánh xạ cột thành biến và tùy chọn bỏ qua dòng lỗi.
- Ghi macro chuột/phím; ở backend ADB, thao tác ghi trên cửa sổ giả lập được ánh xạ về tọa độ Android.

## Nhận diện ảnh và OCR

### Nhận diện ảnh

- Template matching bằng Emgu CV/OpenCV, hỗ trợ nhiều tỉ lệ để thích ứng DPI và thay đổi độ phân giải.
- Có ROI để giới hạn vùng quét và danh sách nhiều template cho một điều kiện ảnh.
- Ưu tiên scale gần lần khớp trước và `1.00x`, sau đó mới mở rộng tìm kiếm.
- Dùng bước tìm thô–tinh và xác minh màu cục bộ để giảm chi phí quét toàn màn hình.
- Cache template; cache được thay thế khi kích thước hoặc thời gian sửa file thay đổi.
- Tâm click được tính theo kích thước template sau khi scale và tọa độ vùng quét.
- Template đồng màu hoặc ít chi tiết được xử lý bằng phương pháp so khớp phù hợp hơn để tránh confidence giả.

### OCR

- Windows OCR với lựa chọn `auto`, `vi-VN` hoặc `en-US`.
- Tesseract 5.2 với dữ liệu `eng` và `vie` cho các luồng nhận diện ảnh/văn bản cần Tesseract.
- Pool OCR giới hạn số tác vụ đồng thời và hỗ trợ timeout/cancellation.

## Yêu cầu hệ thống

| Thành phần | Yêu cầu |
|---|---|
| Hệ điều hành | Windows 10 build 19041 trở lên |
| Nền tảng | Bản `win-x64` là cấu hình phát hành hiện tại |
| Runtime | .NET 8; gói self-contained đã bao gồm runtime |
| ADB | Giả lập/thiết bị phải bật ADB và xuất hiện ở trạng thái `device` |
| Driver Level | Quyền Administrator khi cài/gỡ Interception và cần khởi động lại Windows |

## Bắt đầu nhanh

1. Tải `SmartMacroAI-v1.3.0-beta.3-win-x64-Setup.exe` từ [Releases](https://github.com/trantien-creator/MacroAI-Releases/releases/tag/v1.3.0-beta.3). Nếu cần bản portable, tải file ZIP.
2. Chạy installer; hoặc giải nén bản portable rồi mở `SmartMacroAI.exe`.
3. Tạo kịch bản mới hoặc mở một file trong `%LOCALAPPDATA%\SmartMacroAI\Scripts`.
4. Chọn backend:
   - **Windows/HWND:** chọn cửa sổ đích.
   - **ADB:** mở giả lập, bật ADB và chọn đúng serial thiết bị.
5. Thêm/ghi các bước, đặt tên cho những bước quan trọng và lưu kịch bản.
6. Nhấn **Chạy**, theo dõi node đang sáng hoặc bảng log; dùng breakpoint/Pause/Step khi cần rà lỗi.

## ADB và giả lập Android

ADB được đóng gói trong thư mục `adb/` của bản phát hành và hỗ trợ dò thiết bị, kết nối serial, đọc kích thước màn hình, chụp frame, tap, swipe, key event và nhập text.

Các lưu ý thực tế:

- Trạng thái hợp lệ phải là `device`; `offline`, `unauthorized` hoặc serial sai sẽ làm preflight thất bại.
- Hãy chờ Android khởi động và hiển thị nội dung thật trước khi chạy.
- MEmu HyperV có thể không trả ảnh qua `adb screencap`; SmartMacroAI có fallback chụp cửa sổ host nền khi ánh xạ được đúng cửa sổ giả lập.
- Nhập text qua lệnh ADB hiện chỉ bảo đảm ổn định với ASCII.
- Tọa độ ADB là tọa độ màn hình Android, không phải tọa độ toàn màn hình Windows.
- Hỗ trợ ADB không đồng nghĩa mọi giả lập đều có cùng cổng, quyền truy cập hoặc cơ chế render.

## HTTP API cục bộ

API mặc định chạy tại `http://127.0.0.1:5100`. Server chỉ bind loopback, không bật CORS và không mở ra LAN. Lần chạy đầu, ứng dụng tạo `ApiToken` ngẫu nhiên trong `%LOCALAPPDATA%\SmartMacroAI\app_settings.json`.

Gửi token bằng một trong hai header:

```text
X-API-Key: ***
Authorization: Bearer ***
```

`GET /health` là endpoint duy nhất không cần token.

| Method | Endpoint | Chức năng |
|---|---|---|
| `GET` | `/health` | Kiểm tra tiến trình API |
| `GET` | `/status` | Trạng thái chạy, kịch bản, backend, thời gian và lỗi gần nhất |
| `GET` | `/scripts` | Danh sách kịch bản trong `Scripts/` |
| `POST` | `/start` | Chạy kịch bản qua `MacroEngine` thật |
| `POST` | `/stop` | Yêu cầu dừng macro do UI hoặc API khởi chạy |
| `GET` | `/screenshot` | Frame mục tiêu hiện tại dạng PNG |
| `GET` | `/log?tail=200` | Lấy từ 1 đến 2000 dòng log gần nhất |

Ví dụ chạy từ PowerShell:

```powershell
$settingsPath = Join-Path $env:LOCALAPPDATA 'SmartMacroAI\app_settings.json'
$settings = Get-Content $settingsPath -Raw | ConvertFrom-Json
$headers = @{ 'X-API-Key' = $settings.ApiToken }

Invoke-RestMethod http://127.0.0.1:5100/status -Headers $headers
Invoke-RestMethod http://127.0.0.1:5100/start -Method Post -Headers $headers `
  -ContentType 'application/json' `
  -Body '{"script":"Demo ADB","backendOverride":"adb"}'
Invoke-RestMethod http://127.0.0.1:5100/stop -Method Post -Headers $headers
```

`backendOverride` nhận `script`, `windows`/`hwnd` hoặc `adb`. Giá trị này chỉ sửa bản sao thực thi trong bộ nhớ, không ghi đè file JSON.

## Discord Webhook

SmartMacroAI hỗ trợ:

- Hành động gửi tin nhắn Discord trong workflow.
- Thông báo hoàn tất thành công hoặc thất bại theo từng kịch bản.
- Ảnh chụp khi bước chạy lỗi nếu tùy chọn này được bật.
- Placeholder như `{MacroName}`, `{Duration}`, `{RowsDone}`, `{RowsTotal}`, `{ErrorMessage}` và `{MachineName}` trong mẫu thông báo.
- Kiểm tra URL, không cho phép mention ngoài ý muốn và thử lại theo rate limit của Discord.

> **Lưu ý bảo mật:** Webhook URL chứa token bí mật. Không đưa URL thật vào README, file kịch bản mẫu, log công khai hoặc issue. HTTP `429` cho biết Discord đang giới hạn tần suất; cần chờ thời gian retry, không gửi lặp liên tục.

## Contact / Support

- **Email:** hotrantentien98@gmail.com
- **Issues:** [github.com/trantien-creator/MacroAI-Releases/issues](https://github.com/trantien-creator/MacroAI-Releases/issues)
- **Releases:** [github.com/trantien-creator/MacroAI-Releases/releases](https://github.com/trantien-creator/MacroAI-Releases/releases)
- **Website:** [smartmacroai.pages.dev](https://smartmacroai.pages.dev/)

## Bảo mật và giấy phép

- API chỉ dành cho tích hợp cục bộ. Không đổi bind sang `0.0.0.0` hoặc mở port qua Internet nếu chưa có lớp xác thực và bảo vệ bổ sung.
- Không commit `app_settings.json`, `ai_credentials.dat`, API token, AI API key, Discord Webhook URL hoặc khóa ký số.
- Chỉ cài driver Interception từ gói được chủ dự án cung cấp và kiểm tra chữ ký/hash trước khi phân phối.
- SmartMacroAI là phần mềm **proprietary/confidential**, `Copyright © 2026`, **All rights reserved**. Không được sao chép, phân phối hoặc sửa đổi trái phép.
- Việc cài đặt hoặc sử dụng bản phát hành chịu điều chỉnh bởi [EULA](https://github.com/trantien-creator/MacroAI-Releases/blob/main/TERMS.md).
- Xem [PRIVACY.md](PRIVACY.md) cho chính sách bảo mật.
- Xem [TERMS.md](TERMS.md) cho điều khoản sử dụng.
- Xem [LICENSE](LICENSE) cho giấy phép proprietary.
- Xem [CHANGELOG.md](CHANGELOG.md) cho lịch sử phát hành.

---

**Repository này chỉ chứa docs và official release binaries.** Không chứa source code, credentials, API keys hay bất kỳ dữ liệu nhạy cảm nào.

---

SmartMacroAI is proprietary software developed by **Trần Tiến**. All rights reserved.
