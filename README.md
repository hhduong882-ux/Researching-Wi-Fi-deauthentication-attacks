# Nghiên cứu tấn công Deauthentication trên mạng không dây

Đề tài nghiên cứu học thuật về tấn công hủy xác thực (**Deauthentication Attack**) trên mạng Wi-Fi (IEEE 802.11): phân tích cơ chế kỹ thuật, lỗ hổng liên quan trong chuẩn 802.11, và thực nghiệm minh họa bằng các công cụ mã nguồn mở trong môi trường phòng thí nghiệm khép kín.

## Thông tin đề tài

- **Đơn vị:** Học viện Kỹ thuật Mật mã – Khoa An toàn thông tin
- **Năm:** 2026
- **Sinh viên thực hiện:**
  - Hoàng Hải Dương – AT200415
  - Đỗ Mạnh Cường – AT200408
  - Nguyễn Hoàng Long – AT200236
  - Lê Như Tuấn Kiệt – AT200233
  - Nguyễn Văn Khánh – AT200430

Báo cáo đầy đủ: [`docs/Bao_cao_Deauthentication.docx`](./docs/Bao_cao_Deauthentication.docx)

## Tóm tắt nội dung

Mạng không dây truyền dữ liệu qua sóng vô tuyến trong không gian mở, nên bất kỳ thiết bị nào trong vùng phủ sóng cũng có thể thu nhận hoặc can thiệp vào luồng dữ liệu. Đề tài tập trung vào **Deauthentication Attack** — kỹ thuật khai thác điểm yếu trong thiết kế khung tin quản lý của chuẩn IEEE 802.11 (không được xác thực nguồn gốc, không mã hóa ở các phiên bản ban đầu), cho phép kẻ tấn công giả mạo địa chỉ MAC của Access Point để ép thiết bị khách ngắt kết nối hàng loạt.

Tấn công này thường không trực tiếp đánh cắp dữ liệu, nhưng là **bước đệm** cho các kịch bản tấn công phức hợp: bắt gói tin bắt tay 4 bước để dò mật khẩu ngoại tuyến, hoặc ép nạn nhân chuyển sang điểm truy cập giả mạo (Evil Twin) / tấn công xen giữa (MitM).

### Chương 1 — Tổng quan về mạng không dây
Khái niệm, lịch sử phát triển, phân loại (WPAN/WLAN/WMAN/WWAN/WRAN), kiến trúc và nguyên lý hoạt động (STA, AP, DS, BSS/ESS), các chuẩn 802.11, và các kiểu tấn công phổ biến trên mạng không dây: Eavesdropping/Packet Sniffing, Man-in-the-Middle, Rogue/Fake AP, Deauthentication, Replay, DDoS.

### Chương 2 — Phân tích tấn công Deauthentication
- Cơ chế quản lý kết nối và lỗ hổng trong thiết kế khung tin quản lý 802.11.
- Kỹ thuật giả mạo địa chỉ MAC và phân tích gói tin; các hình thức tấn công (cơ bản, quảng bá, có chủ đích).
- Vai trò của Deauthentication làm tiền đề cho Handshake Capture và Evil Twin/MitM.
- Giải pháp phát hiện & phòng chống: **IEEE 802.11w (PMF – Protected Management Frames)**, **WIDS/WIPS**, và các biện pháp cấu hình/vận hành.

### Chương 3 — Thực nghiệm

**3.1. Deauthentication Flood (mô phỏng bằng Scapy)**

| Thành phần | Công cụ |
| --- | --- |
| Máy tấn công | Kali Linux (VMware Workstation 17) |
| Máy lab | Windows 10 |
| Tạo dữ liệu | Scapy |
| Phân tích | Wireshark (PCAP) |

Quy trình: cài Scapy trên Kali → viết script tạo 500 frame Deauthentication (RadioTap + Dot11 + Dot11Deauth, Reason Code = 7) → xuất file `deauth_simulation.pcap` → chuyển sang Windows qua Shared Folders/HTTP server → mở bằng Wireshark với display filter `wlan.fc.type_subtype == 0x0c` → phân tích bằng I/O Graphs.

**Kết quả:** 500/500 frame được Wireshark nhận diện đúng là Deauthentication, địa chỉ MAC và Reason Code khớp với dữ liệu đã tạo. *Hạn chế:* đây là mô phỏng ngoại tuyến (offline) — frame chỉ tồn tại trong file PCAP, không phát trực tiếp qua card Wi-Fi, nên chưa đánh giá được tác động thực tế lên một mạng đang hoạt động.

**3.2. Evil Twin / Captive-portal phishing bằng Wifiphisher**

| Thiết bị | Vai trò |
| --- | --- |
| Kali Linux | Attacker — cài Wifiphisher, card `wlan0` hỗ trợ Monitor/AP mode |
| AP thật (SSID "LAB WIFI", mạng mở) | Mục tiêu trong lab |
| Windows XP | Victim — đã kết nối sẵn vào "LAB WIFI" |

Quy trình: Wifiphisher dò quét AP trong phạm vi → chọn mục tiêu là mạng mở → dựng Fake AP cùng SSID/kênh, đồng thời gửi liên tục gói Deauth/Disassociation tới AP thật và client → thiết bị victim bị ngắt kết nối, tự động dò lại mạng đã lưu và kết nối nhầm vào Fake AP (tín hiệu giả thường mạnh hơn, không cần xác thực) → mọi request HTTP của victim bị điều hướng tới trang captive-portal giả theo kịch bản có sẵn của Wifiphisher ("firmware-upgrade") → dữ liệu victim nhập vào được gửi về HTTP server cục bộ trên máy Attacker.

**Kết quả:** chuỗi tấn công Evil Twin + captive-portal phishing thực thi thành công trọn vẹn: dò đúng mục tiêu → ngắt kết nối bằng Deauth (khai thác việc thiếu Management Frame Protection) → lừa thiết bị tự động kết nối vào AP giả (khai thác cơ chế auto-connect chỉ dựa vào SSID) → thu thập thông tin do nạn nhân tự nhập. *Nhận định:* hiệu quả tấn công đến từ sự kết hợp giữa điểm yếu giao thức (deauth không xác thực) và yếu tố con người (người dùng không kiểm tra trang trước khi nhập thông tin), không phải một lỗ hổng kỹ thuật phức tạp.

**Tổng hợp rủi ro & biện pháp phòng chống:**

| Rủi ro | Biện pháp phòng chống |
| --- | --- |
| Lộ mật khẩu Wi-Fi / thông tin đăng nhập qua trang giả mạo | Không nhập thông tin nhạy cảm vào trang yêu cầu bất thường; kiểm tra kỹ URL trước khi nhập dữ liệu |
| Bị ngắt kết nối khỏi AP thật do Deauthentication | Bật chuẩn **802.11w (PMF)** để chống giả mạo khung quản lý |
| Tự động kết nối vào AP giả trùng tên (Evil Twin) | Tắt tự kết nối Wi-Fi đã lưu; dùng VPN trên Wi-Fi công cộng; triển khai **WIDS/WIPS** |
| Captive portal giả danh thông báo hệ thống | Đào tạo nhận thức an toàn thông tin; dùng WPA2/WPA3 thay vì mạng mở |

### Kết luận chung
Kết quả thực nghiệm khớp với phân tích lý thuyết ở Chương 2: khi không có PMF, thiết bị khách chấp nhận khung Deauthentication giả mạo và ngắt kết nối; khi bật PMF (802.11w), khung tin giả mạo bị từ chối nhờ mã toàn vẹn thông điệp (MIC) và cuộc tấn công thất bại. WIDS/WIPS hỗ trợ ghi nhận hành vi bất thường để phát hiện sớm. Hạn chế chung của đề tài: phạm vi thực nghiệm còn hẹp, chưa đánh giá đầy đủ ảnh hưởng của các yếu tố môi trường mạng thực tế.

## Công cụ sử dụng trong thực nghiệm

| Thư mục | Mô tả |
| --- | --- |
| [`wifiphisher/`](./wifiphisher) | Mã nguồn công cụ Wifiphisher — dựng kịch bản Evil Twin / captive-portal phishing trong thực nghiệm 3.2 |
| [`roguehostapd/`](./roguehostapd) | Dependency của Wifiphisher, dùng để dựng Access Point giả (rogue AP) |

Hai thư mục trên là mã nguồn mở, clone nguyên bản từ:
- https://github.com/wifiphisher/wifiphisher
- https://github.com/wifiphisher/roguehostapd

được đưa vào repo để tái lập môi trường thực nghiệm đã dùng, **không phải sản phẩm do nhóm tự phát triển**.

## Mục đích & phạm vi

Nội dung được thực hiện **trong môi trường phòng thí nghiệm khép kín, chỉ nhằm mục đích học thuật/nghiên cứu**, phục vụ việc tìm hiểu cơ chế tấn công để từ đó đề xuất biện pháp phòng chống (PMF, WIDS/WIPS, cấu hình vận hành). Không khuyến khích và không chịu trách nhiệm cho việc sử dụng các kỹ thuật/công cụ nêu trong tài liệu để tấn công hệ thống mạng khi chưa có sự cho phép hợp pháp của chủ sở hữu.

## Tài liệu tham khảo

1. DataReportal, "Digital 2026: Vietnam," 2025.
2. Q&Me, "Vietnam Mobile App Usage Trends 2026," 2026.
3. J. Bellardo and S. Savage, "802.11 Denial-of-Service Attacks: Real Vulnerabilities and Practical Solutions," USENIX Association, 2003.
4. I. Martinovic, F. A. Zdarsky and J. B. Schmitt, "On the Way to IEEE 802.11 DoS Resilience," University of Kaiserslautern, 2006.
5. R. Hešík, "Impact of Denial of Service Attacks on the Public Wi-Fi Networks," VŠB – Technical University of Ostrava, 2013.
6. A. G. Gaikwad and B. Patil, "Securing the Airwaves: A Survey on De-authentication Attacks and Mitigation Strategies," *International Journal of Computing and Digital Systems*, vol. 16, no. 1, pp. 1307-1316, 2024.

Danh mục đầy đủ (từ viết tắt, hình ảnh, bảng biểu): xem trong [báo cáo Word](./docs/Bao_cao_Deauthentication.docx).

## Cấu trúc repo

```
.
├── README.md                          # Mô tả dự án (file này)
├── docs/
│   └── Bao_cao_Deauthentication.docx  # Báo cáo đầy đủ (Word)
├── wifiphisher/                       # Source code công cụ Wifiphisher
└── roguehostapd/                      # Source code dependency roguehostapd
```
