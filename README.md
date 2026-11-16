# Nghiên cứu tấn công Deauthentication trên mạng không dây

Đề tài nghiên cứu học thuật về tấn công hủy xác thực (**Deauthentication Attack**) trên mạng Wi-Fi (IEEE 802.11): phân tích cơ chế kỹ thuật, lỗ hổng liên quan trong chuẩn 802.11, và thực nghiệm minh họa bằng các công cụ mã nguồn mở.

## Thông tin đề tài

- **Đơn vị:** Học viện Kỹ thuật Mật mã – Khoa An toàn thông tin
- **Năm:** 2026
- **Sinh viên thực hiện:**
  - Hoàng Hải Dương – AT200415
  - Đỗ Mạnh Cường – AT200408
  - Nguyễn Hoàng Long – AT200236
  - Lê Như Tuấn Kiệt – AT200233
  - Nguyễn Văn Khánh – AT200430

## Nội dung báo cáo

Báo cáo đầy đủ: [`docs/Bao_cao_Deauthentication.docx`](./docs/Bao_cao_Deauthentication.docx)

1. **Chương 1 – Tổng quan về mạng không dây:** khái niệm, kiến trúc, các chuẩn 802.11 và các kiểu tấn công phổ biến (Eavesdropping, MitM, Rogue AP, Deauthentication, Replay, DDoS).
2. **Chương 2 – Phân tích tấn công Deauthentication:** cơ chế quản lý kết nối và lỗ hổng trong khung tin quản lý 802.11, kỹ thuật thực thi tấn công, vai trò của Deauthentication trong các kịch bản tấn công phức hợp (Handshake Capture, Evil Twin/MitM), và các giải pháp phát hiện/phòng chống (802.11w – PMF, WIDS/WIPS).
3. **Chương 3 – Thực nghiệm:**
   - **3.1.** Tấn công Deauthentication Flood
   - **3.2.** Tấn công giả mạo điểm truy cập (Evil Twin) bằng [Wifiphisher](https://github.com/wifiphisher/wifiphisher)
   - **3.3.** Kết luận và đánh giá rủi ro

## Công cụ sử dụng trong thực nghiệm

| Thư mục | Mô tả |
| --- | --- |
| [`wifiphisher/`](./wifiphisher) | Mã nguồn công cụ Wifiphisher — dùng để dựng kịch bản Evil Twin / captive-portal phishing trong thực nghiệm 3.2 |
| [`roguehostapd/`](./roguehostapd) | Dependency của Wifiphisher, dùng để dựng Access Point giả (rogue AP) |

Hai thư mục trên là mã nguồn mở, được clone nguyên bản từ:
- https://github.com/wifiphisher/wifiphisher
- https://github.com/wifiphisher/roguehostapd

được đưa vào repo để tái lập môi trường thực nghiệm đã dùng, không phải sản phẩm do nhóm tự phát triển.

## Mục đích & phạm vi

Nội dung được thực hiện **trong môi trường phòng thí nghiệm khép kín, chỉ nhằm mục đích học thuật/nghiên cứu**, phục vụ việc tìm hiểu cơ chế tấn công để từ đó đề xuất các biện pháp phòng chống (PMF, WIDS/WIPS, cấu hình vận hành). Không khuyến khích và không chịu trách nhiệm cho việc sử dụng các kỹ thuật/công cụ nêu trong tài liệu để tấn công hệ thống mạng khi chưa có sự cho phép hợp pháp của chủ sở hữu.

## Cấu trúc repo

```
.
├── README.md                          # Mô tả dự án (file này)
├── docs/
│   └── Bao_cao_Deauthentication.docx  # Báo cáo đầy đủ (Word)
├── wifiphisher/                       # Source code công cụ Wifiphisher
└── roguehostapd/                      # Source code dependency roguehostapd
```
