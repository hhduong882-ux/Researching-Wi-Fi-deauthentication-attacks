| HỌC VIỆN KỸ THUẬT MẬT MÃ **KHOA AN TOÀN THÔNG TIN** **Đề tài:** **TÌM HIỂU VỀ TẤN CÔNG DEAUTHENTICATION TRÊN MẠNG KHÔNG DÂY** ***Sinh viên thực hiện:*** **Hoàng Hải Dương – AT200415** **Đỗ Mạnh Cường – AT200408** **Nguyễn Hoàng Long – AT200236** **Lê Như Tuấn Kiệt – AT200233** **Nguyễn Văn Khánh – AT200430** ***Hà Nội - 2026*** |
| --- |

# MỤC LỤC

	MỤC LỤC	ii

	DANH MỤC TỪ VIẾT TẮT	iv

	DANH MỤC HÌNH ẢNH	vi

	DANH MỤC BẢNG BIỂU	vii

	LỜI NÓI ĐẦU	1

	CHƯƠNG 1. TỔNG QUAN VỀ MẠNG KHÔNG DÂY	2

	1.1. Khái niệm và các đặc trưng của mạng không dây	2

	1.1.1. Định nghĩa mạng không dây	2

	1.1.2. Lịch sử phát triển của mạng không dây	2

	1.1.3. Phân loại mạng không dây	2

	1.2. Kiến trúc và nguyên lí hoạt động của mạng không dây	4

	1.2.1. Các thành phần cơ bản của mạng không dây	4

	1.2.2. Các mô hình của mạng không dây	5

	1.2.3. Các chuẩn mạng không dây	8

	1.2.4. Nguyên lý hoạt động của mạng không dây	9

	1.3. Ưu và nhược điểm của mạng không dây	10

	1.4. Tính phổ biến của mạng không dây	11

	1.5. Các kiểu tấn công trong mạng không dây	12

	1.5.1. Tấn công nghe lén và bắt gói tin (Eavesdropping / Packet Sniffing)	12

	1.5.2. Tấn công xen giữa (Man-in-the-Middle - MitM)	12

	1.5.3. Tấn công bằng điểm truy cập giả mạo (Rogue / Fake Access Point)	13

	1.5.4. Tấn công huỷ xác thực (Deauthentication Attack)	14

	1.5.5. Tấn công phát lại (Replay Attack)	15

	1.5.6. Tấn công từ chối dịch vụ phân tán (DDoS)	16

	CHƯƠNG 2. PHÂN TÍCH TẤN CÔNG DEAUTHENTICATION TRÊN MẠNG KHÔNG DÂY	17

	2.1. Cơ chế quản lý kết nối và lỗ hổng bảo mật của chuẩn 802.11	17

	2.1.1. Quá trình thiết lập và duy trì kết nối	17

	2.1.2. Lỗ hổng trong thiết kế khung tin quản lý	19

	2.2. Cơ chế kỹ thuật và phương thức thực thi tấn công	21

	2.2.1. Kỹ thuật giả mạo và phân tích gói tin	21

	2.2.2. Các hình thức thực thi tấn công Deauthentication	23

	2.3. Vai trò của Deauthentication trong các kịch bản tấn công phức hợp	26

	2.3.1. Tiền đề cho tấn công dò mật khẩu (Handshake Capture)	27

	2.3.2. Tiền đề cho tấn công Evil Twin / Man-in-the-Middle	29

	2.4. Các giải pháp phát hiện và phòng chống	29

	2.4.1. Tiêu chuẩn bảo vệ khung tin quản lý (IEEE 802.11w - PMF)	29

	2.4.2. Hệ thống phát hiện xâm nhập (WIDS/WIPS)	31

	2.4.3. Các biện pháp cấu hình và vận hành	32

	CHƯƠNG 3. THỰC NGHIỆM	35

	3.1. Tấn công Deauthenticaotion Flood	35

	3.1.1. Mô hình thực nghiệm	35

	3.1.2. Quy trình thực nghiệm	35

	3.1.3. Kết quả thực nghiệm:	39

	3.2. Tấn công giả mạo điểm truy cập (Evil Twin) bằng Wifiphisher	40

	3.2.1. Mô hình thực nghiệm	40

	3.2.2. Quy trình thực nghiệm	41

	3.2.3. Kết quả thực nghiệm	45

	3.3. Kết luận	45

	TỔNG KẾT	47

	TÀI LIỆU THAM KHẢO	48

# DANH MỤC TỪ VIẾT TẮT

| **STT** | **Từ viết tắt** | **Tên đầy đủ** | **Ý nghĩa** |
| --- | --- | --- | --- |
|  | AP | Access Point | Điểm truy cập |
|  | BSS | Basic Service Set | Không gian dịch vụ cơ bản |
|  | BSSID | Basic Service Set Identifier | Định danh không gian dịch vụ cơ bản |
|  | CSMA/CA | Carrier Sense Multiple Access with Collision Avoidance | Đa truy cập nhận sóng mang tránh xung đột |
|  | DDoS | Distributed Denial of Service | Tấn công từ chối dịch vụ phân tán |
|  | Dos | Denial of Service | Tấn công từ chối dịch vụ |
|  | DS | Distribution System | Hệ thống phân phối |
|  | ESS | Extended Service Set | Không gian dịch vụ mở rộng |
|  | IBSS | Independent Basic Service Set | Không gian dịch vụ cơ bản độc lập |
|  | IoT | Internet of Things | Internet vạn vật |
|  | MAC | Media Access Control | Điều khiển truy cập mội trường |
|  | MFP | Management Frame Protection | Bảo vệ khung quản lý |
|  | MIC | Message Integrity Code | Mã toàn vẹn thông điệp |
|  | MIMO | Multiple Input Multiple Output | Công nghệ ăng-ten |
|  | MitM | Man-in-the-Middle | Tấn công xen giữa |
|  | NOS | Network Operation System | Hệ điều hành mạng |
|  | PMF | Protected Management Frames | Khung tin quản lý được bảo vệ |
|  | PSK | Pre-Shared Key | Khoá chia sẻ trước |
|  | PTK | Pairwise Transient Key | Khoá phiên tạm thời |
|  | RSSI | Received Signal Strength Indicator | Chỉ số cường độ tín hiệu nhận được |
|  | SSID | Service Set Indentifier | Định danh tập dịch vụ |
|  | STA | Station | Trạm không dây |
|  | WEP | Wired Equivalent Privacy | Giao thức bảo mật mạng không dây |
|  | WIDS | Wireless Intrustion Detection System | Hệ thống phát hiện xâm nhập mạng không dây |
|  | WIPS | Wireless Intrustion Prevention System | Hệ thống ngăn chặn xâm nhập mạng không dây |
|  | WLAN | Wireless Local Area Network | Mạng cục bộ không dây |
|  | WPA | Wi-Fi Protected Access | Truy cập Wi-Fi được bảo vệ |
|  | WPA2 | Wi-Fi Protected Access 2 | Pheien bản 2 của WPA |
|  | WPA3 | Wi-Fi Protected Access 3 | Pheien bản 3 của WPA |
|  | WPAN | Wireless Personal Area Network | Mạng cá nhân không dây |
|  | WMAN | Wireless Metropolitan Area Network | Mạng đô thị không dây |
|  | WWAN | Wireless Wide Area Network | Mạng diện rộng không dây |
|  | WRAN | Wireless Regional Area Netowork | Mạng khu vực không dây |

# DANH MỤC HÌNH ẢNH

	Hình 1.1. Mô hình mạng Ad-hoc	6

	Hình 1.2. Mô hình mạng cơ sở	7

	Hình 1.3. Mô hình mạng mở rộng	8

	Hình 1.4. Sơ đồ tấn công nghe lén và bắt gói tin	12

	Hình 1.5. Sơ đồ tấn công xen giữa (Man-in-the-Middle - MitM)	13

	Hình 1.6. Sơ đồ tấn công điểm truy cập giả mảo	14

	Hình 1.7. Sơ đồ tấn công huỷ xác thực (Deauthentication Attack)	15

	Hình 1.8. Sơ đồ tấn công phát lại (ReplayAttack)	16

	Hình 1.9. Sơ đồ tấn công từ chối dịch vụ phân tán (DDoS)	16

	Hình 2.1**. **Biểu đồ tuần tự tấn công Deauthentication	18

	Hình 2.2. Máy trạng thái kết nối trong chuẩn IEEE 802.11	20

	Hình 2.3. Sơ đồ tấn công Deauthentication cơ bản	24

	Hình 2.4. Sơ đồ tấn công Deauthentication quảng bá	25

	Hình 2.5. Sơ đồ tấn công Deauthentication có chủ đích	25

	Hình 2.6. Quy trình bắt tay 4 bước  trong WPA/WPA2	27

	Hình 2.7. Cơ chế bảo vệ khung tin quản lý của IEEE 802.11w (PMF)	30

	Hình 2.8. Kiến trúc hệ thống WIDS/WIPS	31

	Hình 3.1. Mô hình tấn công Evil Twin bằng Wifiphisher	41

DANH MỤC BẢNG BIỂU

	Bảng 1.1. So sánh các loại mạng không dây	3

	Bảng 1.2. Bảng tóm tắt các chuẩn mạng không dây IEEE 802.11	9

	Bảng 2.1. Đánh giá vai trò Deauth trong kịch bản Handshake	28

	Bảng 2.2. Đánh giá vai trò Deauth trong Evil Twin	29

	Bảng 2.3. Tổng hợp các giải pháp phòng chống Deauthentication Attack	33

	Bảng 3.1. Cấu hình thiết bị thực nghiệm tấn công Deauthentication Flood	35

	Bảng 3.2. Cấu hình thông số I/O Graphs	38

	Bảng 3.3.  Kết quả thực thi các bước thực nghiệm	39

	Bảng 3.4. Cấu hình thiết bị thực nghiệm tấn công Evil Twin	40

	Bảng 3.5. Tổng hợp rủi ro và biện pháp phòng chống	45

# LỜI NÓI ĐẦU

Sự phát triển của các chuẩn IEEE 802.11 (Wi-Fi) đã đưa mạng không dây trở thành hạ tầng thiết yếu trong đời sống hiện đại, khi phần lớn lưu lượng Internet được thực hiện qua kết nối không dây. Tuy nhiên, bản chất truyền dẫn mở bằng sóng vô tuyến cũng tạo ra những lỗ hổng bảo mật cố hữu. Khác với mạng có dây, mạng không dây cho phép bất kỳ thiết bị nào trong vùng phủ sóng cũng có thể thu nhận, phân tích hoặc can thiệp vào luồng dữ liệu, đặt ra yêu cầu cấp thiết về nghiên cứu các hình thức tấn công và cơ chế phòng chống.

Trong số các kỹ thuật tấn công phổ biến, tấn công hủy xác thực (Deauthentication Attack) khai thác trực tiếp điểm yếu trong thiết kế khung tin quản lý của chuẩn IEEE 802.11. Các khung tin này không được xác thực nguồn gốc và không được mã hóa trong các phiên bản chuẩn ban đầu, cho phép thiết bị trong vùng phủ sóng gửi khung tin giả mạo và được thiết bị đầu cuối chấp nhận. Kẻ tấn công lợi dụng điểm yếu này bằng cách giả mạo địa chỉ MAC của điểm truy cập (Access Point – AP) để gửi hàng loạt khung tin hủy xác thực đến máy khách, buộc máy khách ngắt kết nối mà không thể phân biệt lệnh hợp pháp từ AP và lệnh giả mạo.

Mặc dù không trực tiếp đánh cắp dữ liệu hay chiếm quyền điều khiển thiết bị, tấn công Deauthentication thường đóng vai trò bước đệm trong các kịch bản tấn công phức hợp. Việc ép thiết bị ngắt kết nối và tự động kết nối lại tạo điều kiện thu thập gói tin bắt tay bốn bước (four-way handshake) để thực hiện dò mật khẩu ngoại tuyến (offline brute force/dictionary attack). Bên cạnh đó, cuộc tấn công này còn là tiền đề để ép nạn nhân chuyển sang điểm truy cập giả mạo (Evil Twin) hoặc tạo điều kiện cho tấn công xen giữa (Man-in-the-Middle - MitM). Do đó, Deauthentication không chỉ là cuộc tấn công đơn lẻ mà còn là mắt xích quan trọng trong chuỗi tấn công có chủ đích, đòi hỏi hiểu biết toàn diện về cơ chế kỹ thuật và biện pháp phòng chống.

Nhận thức được tính cấp thiết của vấn đề, nhóm nghiên cứu lựa chọn đề tài **“Tìm hiểu về tấn công Deauthentication trên mạng không dây” **nhằm hệ thống hóa cơ chế kỹ thuật, phân tích lỗ hổng liên quan trong chuẩn 802.11 và đánh giá vai trò của cuộc tấn công trong các chuỗi tấn công mạng. Nội dung nghiên cứu cũng khảo sát các giải pháp phát hiện và phòng chống hiện nay, bao gồm tiêu chuẩn bảo vệ khung tin quản lý (IEEE 802.11w – Protected Management Frames – PMF), hệ thống phát hiện và ngăn chặn xâm nhập không dây (WIDS/WIPS), cùng các biện pháp cấu hình và vận hành nhằm giảm thiểu rủi ro.

# TỔNG QUAN VỀ MẠNG KHÔNG DÂY

## Khái niệm và các đặc trưng của mạng không dây

### Định nghĩa mạng không dây

Mạng không dây (Wireless Network) là một hệ thống truyền thông dữ liệu không giới hạn, dựa trên các tiêu chuẩn kỹ thuật (tiêu biểu là IEEE 802.11), sử dụng công nghệ tần số vô tuyến để giao tiếp với các thiết bị và thu thập dữ liệu. Khác với mạng truyền thống, mạng không dây giải phóng người dùng khỏi các kết nối vật lý phức tạp và cồng kềnh, cho phép các cá nhân sử dụng mạng theo những cách mới, giúp dữ liệu trở nên di động và dễ tiếp cận hơn bao giờ hết. 

### Lịch sử phát triển của mạng không dây

**- 1985:** Ủy ban liên lạc liên bang Mỹ FCC (cơ quan quản lý viễn thông của nước này), quyết định mở cửa một số băng tần của giải sóng không dây, cho phép sử dụng chúng mà không cần giấy phép của chính phủ.

**- 1988:** Công ty NCR vì muốn sử dụng dải tần không được cấp phép để liên thông các máy rút tiền qua kết nối không dây, đã gửi một yêu cầu đến Nhóm kỹ sư điện, điện tử (IEEE) thiết lập một tiểu ban mới có tên 802.11để giúp xác định một tiêu chuẩn cho công nghệ không dây.

**- 1997:** Phê chuẩn một bộ tiêu chí cơ bản, cho phép mức truyền dữ liệu 2Mbs, sử dụng một trong hai công nghệ dải tần rộng là frequency hop-ping (tránh nhiễu bằng các chuyển đổi liên tục giữa các tần số radio) hoặc direct sequence transmission (phát tín hiệu trên một dải gồm nhiều tần số).

**- 1999:** IEEE phê duyệt phiên bản tiêu chuẩn 802.11b (hoạt động trên băng tần 2.4 GHz) với tốc độ truyền dữ liệu lên tới 11 Mbps.

**- 2000:** Phiên bản chuẩn 802.11a (hoạt động trên băng tần 5,8GHz) được phê duyệt. Thống nhất tên gọi cho công nghệ mới và cuối cùng cái tên “Wifi” (Wireless fidelty) ra đời.

### Phân loại mạng không dây

**Mạng WPAN (Công nghệ Bluetooth)**: Là mạng vô tuyến cá nhân có vùng phủ nhỏ (vài mét đến hàng chục mét). Nhóm này dùng để kết nối các thiết bị ngoại vi (máy in, chuột, bàn phím, USB, đồng hồ...) với điện thoại hoặc máy tính. Các công nghệ tiêu biểu gồm Bluetooth, ZigBee, UWB, Wireless USB... Hầu hết được chuẩn hóa bởi IEEE, thuộc nhóm làm việc 802.15 (như IEEE 802.15.4).

**Mạng WLAN: **Là mạng vô tuyến cục bộ. Nhóm này bao gồm các công nghệ có vùng phủ tầm vài trăm mét. Nổi bật là công nghệ Wifi với nhiều chuẩn mở rộng khác nhau thuộc gia đình 802.11 a/b/g/h/i/... Công nghệ Wifi đã trở nên phổ biến trong những năm qua. Bên cạnh WiFi thì còn một cái tên ít nghe đến là HiperLAN và HiperLAN2, đối thủ cạnh tranh của Wifi được chuẩn hóa bởi ETSI.

**Mạng WMAN: **Đây là mạng vô tuyến đô thị. Đại diện tiêu biểu của nhóm này chính là WiMAX. Ngoài ra còn có công nghệ băng rộng BWMA 802.20. Vùng phủ sóng của nó sẽ tằm vài km (tầm 4-5km tối đa.)

**Mạng WWAN: **Mạng vô tuyến diện rộng: Nhóm này bao gồm các công nghệ mạng thông tin di động như UMTS/GSM/CDMA2000... Vùng phủ của nó cũng tầm vài km đến tầm chục km. 

**Mạng WRAN: **Mạng vô tuyến khu vực. Nhóm này đại diện là công nghệ 802.22 đang được nghiên cứu và phát triển bởi IEEE. Vùng phủ có nó sẽ lên tầm 40-100km. Mục đích là mang công nghệ truyền thông đến các vùng xa xôi hẻo lánh, khó triển khai các công nghệ khác. Nó sẽ sử dụng băng tần mà TV analog không dùng để đạt được vùng phủ rộng.

Bảng 1.1. So sánh các loại mạng không dây

| **Tiêu chí** | **WPAN** | **WLAN** | **WMAN** | **WWAN** | **WRAN** |
| --- | --- | --- | --- | --- | --- |
| **Phạm vi** | 1 - 10m | 10 – 100m | Vài km đến 50 km | Toàn quốc gia, toàn cầu | 30 - 100 km |
| **Băng tần** | 2.4 GHz, 5 GHz | 2.4 GHz, 5 GHz, 6 GHz | 2.5 GHz, 3.5 GHz, 5 GHz | 700 MHz, 800 MHz, 1.8 GHz, 2.1 GHz, 3.5 GHz | 54 - 862 MHz (Tần số TV UHF/VHF) |
| **Tốc độ** | 1 - 24Mbps | 11 Mbps - hàng Gbps | Hàng chục đến hàng trăm Mbps | Vài Mbps đến hàng trăm Mbps | 8 - 22 Mbps |
| **Công nghệ** | Bluetooth, ZigBee, UWB (IEEE 802.15) | Wi-Fi (IEEE 802.11 a/b/g/n/ac/ax) | WiMAX (IEEE 802.16), LTE | GSM, UMTS (3G), LTE (4G), 5G NR | IEEE 802.22 (Cognitive Radio) |
| **Mục đích** | Kết nối thiết bị ngoại vi, IoT cá nhân | Kết nối mạng cục bộ (nhà ở, văn phòng, trường học) | Kết nối mạng đô thị, backhaul cho WLAN | Liên lạc di động diện rộng, truy cập Internet mọi lúc mọi nơi | Cung cấp Internet cho vùng sâu vùng xa, nông thôn |

## Kiến trúc và nguyên lí hoạt động của mạng không dây

### Các thành phần cơ bản của mạng không dây

**Trạm không dây (Wireless Station ****-**** STA)****:** là các thiết bị đầu cuối (như máy tính xách tay, điện thoại thông minh, thiết bị IoT…) có trang bị bộ giao tiếp mạng không dây. Trong mô hình mạng có hạ tầng, STA đóng vai trò là các nút mạng (node) kết nối vào hệ thống. Điểm khác biệt cốt lõi so với mạng Ad-hoc (mạng ngang hàng) là các STA trong mô hình này không giao tiếp trực tiếp với nhau. Mọi luồng dữ liệu giữa các STA đều bắt buộc phải đi qua một thiết bị trung gian, đảm bảo tính kiểm soát và quản lý tập trung.

**Điểm truy cập (Access Point - AP)****:** là hạt nhân của mạng không dây có hạ tầng. Về mặt chức năng, AP đóng vai trò là một cầu nối giữa môi trường không dây và hệ thống mạng có dây. Cụ thể, AP cung cấp giao diện kết nối cho các STA vào hệ thống phân phối. Bên cạnh vai trò cầu nối, AP còn thực hiện chức năng chuyển tiếp cục bộ. Khi một STA gửi dữ liệu đến một STA khác trong cùng một vùng phủ sóng (cùng BSS), AP sẽ nhận khung tin đó và chuyển tiếp lại cho STA đích. Cơ chế này đảm bảo mọi giao tiếp trong mạng không dây đều nằm dưới sự điều phối của AP.

**Hệ thống phân phối (Distribution System - DS)**: là một hệ thống mạng dùng để liên kết các AP lại với nhau. Vai trò định tuyến của DS được thể hiện qua quá trình xử lý khung tin: Khi DS nhận được một khung dữ liệu từ một AP, nó sẽ phân tích địa chỉ đích và đưa ra quyết định định tuyến. Khung tin đó có thể được chuyển tiếp ngược lại một STA trong cùng BSS, chuyển sang một AP khác nếu đích nằm ở vùng phủ sóng khác, hoặc đẩy ra mạng có dây bên ngoài như Internet. Nhờ có DS, phạm vi kết nối của mạng không dây không còn bị giới hạn trong một vùng phủ sóng đơn lẻ.

**Không gian dịch vụ****: **Trong chuẩn IEEE 802.11, để quản lý phạm vi hoạt động và luồng dữ liệu, mạng không dây được tổ chức thành các không gian dịch vụ với hai cấp độ cơ bản:

- **Dịch vụ cơ bản** **(Basic Service Set - BSS): **Đây là đơn vị cấu trúc nhỏ nhất của mạng 802.11. Một BSS bao gồm một AP duy nhất và tập hợp các STA đang kết nối vào AP đó. Mỗi BSS được định danh bằng một mã duy nhất gọi là BSSID. BSS giới hạn phạm vi giao tiếp vật lý của các thiết bị trong cùng một vùng phủ sóng (cell), đảm bảo các thiết bị trong cùng BSS có thể trao đổi dữ liệu với nhau thông qua AP.

- **Dvụ mở rộng (Extended Service Set - ESS):** Khi nhu cầu kết nối vượt ra khỏi phạm vi của một vùng phủ sóng đơn, nhiều BSS sẽ được triển khai. Các BSS này được kết nối với nhau thông qua DS để tạo thành một ESS. ESS cho phép các STA có thể di chuyển tự do giữa các vùng phủ sóng của các AP khác nhau mà vẫn duy trì được kết nối logic liên tục tới mạng mà không bị ngắt quãng.

### Các mô hình của mạng không dây

Để xây dựng một hệ thống mạng không dây khá đơn giản. Mạng Wireless được thiết kế rất linh hoạt. Khi phát triển một hệ thống bạn có thể lựa chọn một trong nhiều kiểu mô hình đã được hoạch định sẵn. 

Mạng không dây bao gồm 3 mô hình cơ bản: mô hình mạng độc lập IBSSs (hay còn gọi là mạng Ad-hoc), mô hình mạng cơ sở (BSSs), mô hình mạng mở rộng (ESSs).

- **Mô hình mạng Ad-hoc**

Mạng IBSS (Independent Basic Service Set), hay còn gọi là mạng Ad-hoc, là cấu hình mạng không dây cơ bản nhất trong chuẩn IEEE 802.11, trong đó các trạm liên lạc trực tiếp với nhau mà không cần thông qua một Access Point (AP) trung tâm. Mỗi trạm trong mạng IBSS tự quản lý mạng, không có nút nào đóng vai trò server hay trạm chủ . Mạng IBSS thường bao gồm một số lượng nhỏ các trạm, có thời gian tồn tại ngắn và được tạo ra cho một mục đích cụ thể . 

Mô hình tối thiểu của IBSS có thể chỉ gồm hai máy client kết nối trực tiếp với nhau. Do không có AP, các trạm trong IBSS luân phiên nhau gửi khung beacon để duy trì nhận biết về sự tồn tại của mạng . Điều này khác với mạng có hạ tầng, nơi AP chịu trách nhiệm phát các khung quảng bá định kỳ . Mạng Ad-hoc thường được ứng dụng trong các văn phòng nhỏ, mạng nội bộ không cần kết nối internet, hoặc trong các tình huống quân sự và khẩn cấp - nơi không thể triển khai hạ tầng cố định. 

Hình 1.1. Mô hình mạng Ad-hoc

Về mặt bảo mật, do dữ liệu được truyền qua sóng vô tuyến trong không gian mở, mạng Ad-hoc khó kiểm soát hơn so với mạng có dây. Việc thiếu một thiết bị quản lý tập trung (AP) khiến việc triển khai các giao thức bảo mật phức tạp trở nên khó khăn hơn, và mạng dễ bị tổn thương trước các hình thức nghe lén hoặc tấn công. Nhược điểm cố hữu của mô hình này là vùng phủ sóng bị giới hạn, và trong nhiều trường hợp, các nút phải nằm trong phạm vi nghe được lẫn nhau để duy trì kết nối.

- **Mô hình mạng cơ sở**

Mô hình mạng cơ sở, hay còn gọi là Basic Service Sets (BSS), là một topology nền tảng của mạng 802.11. Trong mô hình này, các thiết bị giao tiếp tạo nên một BSS bao gồm một điểm truy cập (AP) duy nhất kết nối với một hoặc nhiều máy khách. Về bản chất, BSS bao gồm các điểm truy cập AP được gắn với mạng có dây và thực hiện giao tiếp với các thiết bị di động nằm trong vùng phủ sóng của một cell. 

Trong cấu trúc này, AP đóng vai trò là thiết bị điều khiển cell và điều khiển lưu lượng mạng. Các thiết bị di động không giao tiếp trực tiếp với nhau mà bắt buộc phải giao tiếp thông qua AP. Các cell có thể chồng lấn lên nhau khoảng 10-15% cho phép các trạm di động có thể di chuyển mà không bị mất kết nối vô tuyến, đồng thời cung cấp vùng phủ sóng với chi phí thấp nhất. 

Hình 1.2. Mô hình mạng cơ sở

Khi di chuyển, các trạm di động sẽ tự động chọn AP tốt nhất để kết nối. Một điểm truy cập nằm ở vị trí trung tâm có khả năng điều khiển và phân phối truy nhập cho các nút tranh chấp, cung cấp truy nhập phù hợp với mạng đường trục, ổn định các địa chỉ và các mức ưu tiên, giám sát lưu lượng mạng, quản lý chuyển đi các gói và duy trì theo dõi cấu hình mạng.

- **Mô hình mạng mở rộng**

Mô hình mạng mở rộng (ESS) là một kiến trúc mạng được thiết lập nhằm mở rộng phạm vi di động của mạng 802.11 ra một không gian rộng lớn hơn. Về bản chất, ESS là một tập hợp gồm nhiều mô hình mạng cơ sở (BSS) được kết nối với nhau. Trong mô hình này, các AP giao tiếp với nhau để chuyển tiếp lưu lượng từ BSS này sang BSS khác, nhờ đó các trạm di động có thể di chuyển dễ dàng giữa các vùng phủ sóng khác nhau mà vẫn duy trì kết nối. 

Để thực hiện việc kết nối và chuyển tiếp này, các AP giao tiếp với nhau thông qua một hệ thống phân phối (một hệ thống mạng trung gian, thường là mạng có dây, đóng vai trò liên kết các AP). Trong mỗi AP, hệ thống phân phối hoạt động như một lớp trung gian có nhiệm vụ xác định đích đến cho luồng lưu lượng nhận được từ một BSS. 

Hình 1.3. Mô hình mạng mở rộng

Tùy thuộc vào đích đến của luồng dữ liệu, hệ thống phân phối sẽ xử lý theo các hướng sau: truyền ngược trở lại một đích trong cùng một BSS, chuyển tiếp qua hệ thống phân phối tới một AP khác, hoặc gửi tới một mạng khác nếu đích đến nằm ngoài phạm vi ESS. Các thông tin sau khi được AP nhận từ hệ thống phân phối sẽ được truyền tới BSS và cuối cùng được trạm đích tiếp nhận.

### Các chuẩn mạng không dây

Các chuẩn mạng Wi-Fi được sử dụng hiện nay đều thuộc bộ tiêu chuẩn IEEE 802.11 đi kèm với một hoặc nhiều chữ cái phía sau. IEEE là tổ chức chịu trách nhiệm phê chuẩn cấu hình cũng như thúc đẩy sự phát triển của Wi-Fi. Từ năm 1999 đến nay, các chuẩn mạng Wi-Fi được sử dụng rộng rãi bao gồm: 

**Chuẩn 802.11a:**  Đây là chuẩn mở rộng thứ hai dựa vào 802.11 đầu tiên. Chuẩn 802.11a sử dụng tần số 5GHz với tốc độ 54Mbps. Chuẩn này áp dụng kỹ thuật trải phổ đa phân chia tần số trực giao (OFDM) - được đánh giá là kỹ thuật trội hơn so với trải phổ trực tiếp (DSSS). Do chi phí cao hơn, 802.11a thường chỉ được dùng trong các mạng doanh nghiệp, ngược lại, 802.11b thích hợp hơn cho nhu cầu gia đình. 

**Chuẩn 802.11b:** Từ tháng 6 năm 1999, IEEE mở rộng chuẩn 802.11 ban đầu và tạo ra các đặc tả kỹ thuật cho 802.11b. Chuẩn này hỗ trợ băng thông 11Mbps và sử dụng tần số 2,4 GHz. 802.11b sử dụng kỹ thuật điều chế khóa mã bù (CCK) và dùng kỹ thuật trải phổ trực tiếp giống như chuẩn 802.11 nguyên bản. Đây là chuẩn WLAN đầu tiên được chấp nhận rộng rãi trên thị trường. 

**Chuẩn 802.11g:**  Được phê chuẩn vào tháng 7 năm 2003, chuẩn 802.11g là sự kết hợp các ưu điểm của cả 802.11a và 802.11b. Chuẩn này hỗ trợ băng thông 54Mbps, sử dụng phương thức điều chế OFDM tương tự 802.11a nhưng hoạt động trên tần số 2,4GHz giống 802.11b để có phạm vi phủ sóng lớn hơn (khoảng 38-140m). Chuẩn 802.11g có khả năng tương thích ngược với chuẩn 802.11b nhưng không tương thích với chuẩn 802.11a. 

**Chuẩn 802.11n:** Đây là chuẩn được thiết kế để cải thiện tính năng của 802.11g về tổng băng thông được hỗ trợ bằng cách tận dụng nhiều tín hiệu không dây và anten (công nghệ MIMO) kết hợp với kỹ thuật ghép kênh (channel bonding). Chuẩn này hỗ trợ tốc độ lên đến 600 Mbps và cho tầm phủ sóng tốt hơn các chuẩn Wi-Fi trước đó (khoảng 70-250m) nhờ tăng cường độ tín hiệu. Các thiết bị 802.11n có khả năng tương thích ngược với 802.11g và hoạt động trên cả hai tần số 2,4GHz và 5GHz.

Bảng 1.2. Bảng tóm tắt các chuẩn mạng không dây IEEE 802.11

| **Chuẩn** | **Năm ** | **Băng tần** | **Tốc độ** | **Đặc điểm kỹ thuật** |
| --- | --- | --- | --- | --- |
| **802.11a** | 1999 | 5 GHz | 54 Mbps | Sử dụng kỹ thuật OFDM, ít bị nhiễu nhưng chi phí cao . |
| **802.11b** | 1999 | 2.4 GHz | 11 Mbps | Sử dụng CCK/DSSS, được chấp nhận rộng rãi, giá thành rẻ . |
| **802.11g** | 2003 | 2.4 GHz | 54 Mbps | Kết hợp OFDM của 802.11a và băng tần 2.4 GHz của 802.11b . |
| **802.11n** | 2009 | 2.4 GHz & 5 GHz | 600 Mbps | Sử dụng MIMO và ghép kênh (channel bonding), tầm phủ sóng trong nhà khoảng 50m . |

### Nguyên lý hoạt động của mạng không dây

Mạng WLAN sử dụng sóng điện từ (vô tuyến và tia hồng ngoại) để truyền thông tin từ điểm này sang điểm khác mà không dựa vào bất kỳ kết nối vật lý nào. Các sóng vô tuyến thường là các sóng mang vô tuyến bởi vì chúng thực hiện chức năng phân phát năng lượng đơn giản tới máy thu ở xa.

Dữ liệu truyền được chồng lên trên sóng mang vô tuyến để nó được nhận lại đúng ở máy thu. Đó là sự điều biến sóng mang theo thông tin được truyền. Một khi dữ liệu được chồng hay được điều chế lên trên sóng mang vô tuyến, thì tín hiệu vô tuyến chiếm nhiều hơn một tần số đơn, vì tần số hoặc tốc độ truyền theo bit của thông tin biến điệu được thêm vào sóng mang. Nhiều sóng mang vô tuyến tồn tại trong cùng không gian tại cùng một thời điểm mà không nhiễu với nhau nếu chúng được truyền trên các tần số vô tuyến khác nhau.

Để nhận dữ liệu, máy thu vô tuyến bắt sóng hoặc chọn một tần số vô tuyến xác định trong khi loại bỏ tất cả các tín hiệu vô tuyến khác trên các tần số khác. Trong một cấu hình mạng WLAN tiêu biểu, một thiết bị thu phát, được gọi AP, nối tới mạng nối dây từ một vị trí cố định sử dụng cáp Ethernet chuẩn. AP nhận, lưu vào bộ nhớ đệm, và truyền dữ liệu giữa mạng WLAN và cơ sở hạ tầng mạng nối dây.

Một điểm truy cập đơn hỗ trợ một nhóm nhỏ người sử dụng và vận hành bên trong một phạm vi vài mét tới hàng chục mét. Điểm truy cập (hoặc anten được gắn tới nó) thông thường được gắn trên cao nhưng thực tế được gắn bất cứ nơi đâu miễn là khoảng vô tuyến cần thu được. Các người dùng đầu cuối truy cập mạng WLAN thông qua các card giao tiếp mạng WLAN mà được thực hiện như các card PC trong các máy tính để bàn, hoặc các thiết bị tích hợp hoàn toàn bên trong các máy tính cầm tay. Các card giao tiếp mạng WLAN cung cấp một giao diện giữa hệ điều hành mạng (NOS) và sóng trời (qua một anten). Bản chất của kết nối không dây là trong suốt với NOS.

## Ưu và nhược điểm của mạng không dây

- **Ưu điểm:**

- Khả năng chia sẻ tài nguyên dữ liệu dùng chung mạnh mẽ, rất phù hợp trong môi trường kết nối mạng của các doanh nghiệp và văn phòng. 

- Người dùng có thể dễ dàng di chuyển và truy cập mạng ở bất kỳ đâu, thích ứng linh hoạt trên mọi thiết bị thông minh. 

- Mặc dù chi phí thiết bị vô tuyến ban đầu có thể cao hơn, nhưng việc loại bỏ nhu cầu thi công, lắp đặt và bảo trì hệ thống dây dẫn phức tạp giúp tiết kiệm chi phí đáng kể về lâu dài. 

- Việc thiết lập kết nối diễn ra nhanh và dễ dàng, có thể vươn tới những khu vực mà mạng có dây truyền thống không thể tiếp cận. 

- Hỗ trợ nhiều cấu hình và quy mô khác nhau, dễ dàng thay đổi để phục vụ cho tùy nhu cầu sử dụng, từ hộ gia đình đến các khu vực rộng lớn như khu dân cư hay văn phòng công sở. 

- Việc mở rộng mạng lưới trở nên dễ dàng và nhanh chóng mà không cần phải thi công thêm hệ thống dây cáp vật lý. 

- Loại bỏ sự cồng kềnh của dây cáp, giúp không gian lắp đặt gọn gàng, có tính thẩm mỹ cao và giảm thiểu rủi ro tai nạn vật.

- **Nhược điểm: **

- Do tín hiệu được truyền đi trong không gian bằng sóng vô tuyến, nguy cơ bị kẻ xấu tấn công vào mạng là rất lớn, các gói dữ liệu truyền đi có thể bị bất kỳ ai trong vùng phủ sóng chặn và giải mã. 

- Tín hiệu rất dễ bị ảnh hưởng bởi các thiết bị phát sóng khác, dẫn đến việc sóng truyền đi bị ngắt quãng hoặc giảm tốc độ truyền. 

- Tốc độ truyền của mạng không dây phụ thuộc vào băng thông và thường chậm hơn so với mạng kết nối có dây. 

- Khả năng phủ sóng bị ảnh hưởng bởi khoảng cách địa lý và các vật cản vật lý (như tường, cấu trúc tòa nhà), khiến nó chưa thể đáp ứng hoàn toàn cho các khu vực không gian quá rộng lớn nếu không có thiết bị khuếch đại. 

- Độ trễ và tính ổn định của đường truyền dễ bị biến động do môi trường và số lượng người dùng cùng lúc, gây khó khăn cho các ứng dụng yêu cầu thời gian thực. 

- Các thiết bị đầu cuối (như laptop, điện thoại) phải tiêu hao năng lượng pin nhiều hơn để duy trì kết nối vô tuyến so với khi sử dụng cáp mạng. 

- Việc quản lý, giám sát và xử lý sự cố mạng không dây thường phức tạp hơn so với việc kiểm tra kết nối vật lý trên mạng có dây.

## Tính phổ biến của mạng không dây

- Trong bối cảnh công nghệ hiện đại, các thiết bị thông minh như điện thoại, máy tính xách tay hay máy tính bảng đã trở nên phổ biến, khiến việc sử dụng mạng không dây trở thành một nhu cầu thiết yếu hàng ngày. 

- Người dùng sử dụng thiết bị di động cho mọi mục đích như liên lạc, gửi email, truy cập mạng xã hội hay giải trí; các hoạt động này đều phụ thuộc vào kết nối Internet qua mạng không dây. 

- Theo báo cáo Digital 2026: Vietnam của DataReportal, có tới 96,9% lưu lượng truy cập Internet tại Việt Nam được thực hiện qua thiết bị di động. Con số này cho thấy sự phụ thuộc gần như tuyệt đối của người dùng vào các kết nối không dây.  [1]

- Bên cạnh đó, khảo sát của Q&Me (năm 2026) cho thấy người dùng Việt Nam dành trung bình 7,1 giờ mỗi ngày cho các ứng dụng di động. Thời gian sử dụng thiết bị di động liên tục ở mức cao đã thúc đẩy mạnh mẽ việc triển khai mạng không dây tốc độ cao từ các nhà cung cấp dịch vụ.  [2]

- Hiện nay, mạng không dây đã hiện diện ở mọi không gian, từ gia đình, quán cà phê, siêu thị, ngân hàng đến các công sở, cho thấy mức độ phụ thuộc của xã hội vào hạ tầng mạng này. 

- Như vậy, những số liệu trên đã phản ánh rõ nét tầm quan trọng và tính phổ biến của mạng không dây trong đời sống hiện đại.

## Các kiểu tấn công trong mạng không dây

Mạng không dây hoạt động dựa trên môi trường truyền dẫn mở là sóng vô tuyến, do đó rất dễ bị tổn thương trước nhiều hình thức tấn công khác nhau nhằm mục đích đánh cắp dữ liệu hoặc gây gián đoạn dịch vụ. Dưới đây là phân tích chi tiết về các kiểu tấn công phổ biến.

### Tấn công nghe lén và bắt gói tin (Eavesdropping / Packet Sniffing)

Đây là hình thức tấn công thụ động (passive attack) cơ bản nhất trong môi trường không dây. Do tín hiệu Wi-Fi được truyền đi trong không gian mở bằng sóng vô tuyến, bất kỳ thiết bị nào nằm trong vùng phủ sóng cũng có thể thu được các gói tin. Kẻ tấn công lợi dụng đặc điểm này bằng cách đưa card mạng của mình vào chế độ giám sát (monitor mode) và sử dụng các phần mềm chuyên dụng để chặn, sao chép và đọc nội dung các gói dữ liệu. Vì kẻ tấn công chỉ đọc mà không can thiệp hay thay đổi luồng dữ liệu, cuộc tấn công này gần như không thể bị phát hiện bởi các hệ thống bảo mật thông thường. Nó đặc biệt nguy hiểm trên các mạng Wi-Fi công cộng không mã hóa, cho phép kẻ tấn công thu thập các thông tin nhạy cảm như tên đăng nhập, mật khẩu hoặc cookie phiên làm việc.

Hình 1.4. Sơ đồ tấn công nghe lén và bắt gói tin

### Tấn công xen giữa (Man-in-the-Middle - MitM)

Đây là hình thức tấn công chủ động (active attack), phát triển dựa trên nền tảng của việc nghe lén. Trong tấn công MitM, kẻ tấn công chèn mình vào giữa thiết bị của người dùng và Access Point (AP) hoặc máy chủ đích. Bằng cách giả mạo địa chỉ MAC hoặc sử dụng các kỹ thuật định tuyến sai lệch (như ARP Spoofing), kẻ tấn công khiến cả hai bên tin rằng chúng đang giao tiếp trực tiếp với nhau. Thực chất, mọi lưu lượng dữ liệu gửi đi và nhận về đều phải đi qua thiết bị của kẻ tấn công. Điều này không chỉ cho phép kẻ tấn công đọc trộm thông tin (như Eavesdropping) mà còn có thể chỉnh sửa nội dung giao dịch, chuyển hướng người dùng đến các trang web độc hại, hoặc chèn mã độc vào luồng dữ liệu theo thời gian thực.

Hình 1.5. Sơ đồ tấn công xen giữa (Man-in-the-Middle - MitM)

###  Tấn công bằng điểm truy cập giả mạo (Rogue / Fake Access Point)

Hình thức tấn công này xảy ra khi một Access Point (AP) được đưa vào hệ thống mạng một cách vô tình hoặc cố ý. Điểm yếu bị khai thác là sự thiếu kiểm soát chặt chẽ đối với hạ tầng vật lý của mạng. Kẻ tấn công kết nối một thiết bị phát sóng vào cổng mạng có dây của doanh nghiệp, tạo ra một kênh truy cập trái phép cho phép vượt qua các lớp bảo vệ của tường lửa. Thiết bị này sau đó phát ra một tín hiệu Wi-Fi mở (không có mật khẩu). Khi các thiết bị di động của nhân viên hoặc khách hàng tự động kết nối vào mạng mở này, mọi dữ liệu của họ sẽ đi qua AP giả mạo trước khi vào mạng chính. Một biến thể nguy hiểm hơn là Evil Twin, trong đó kẻ tấn công phát đi các gói tin quảng bá với tên mạng (SSID) giống hệt mạng hợp pháp để lừa thiết bị của nạn nhân tự động kết nối. Khi người dùng kết nối nhầm, mọi dữ liệu sẽ đi qua thiết bị của kẻ tấn công.

Hình 1.6. Sơ đồ tấn công điểm truy cập giả mảo 

### Tấn công huỷ xác thực (Deauthentication Attack)

Kiểu tấn công này khai thác một điểm yếu cố hữu trong chuẩn IEEE 802.11: các khung tin quản lý (management frames) bao gồm khung hủy xác thực, không được xác thực nguồn gốc hay mã hóa. Bất kỳ thiết bị nào trong vùng phủ sóng cũng có thể gửi các khung tin này và chúng sẽ được chấp nhận. Lợi dụng điểm yếu trên, kẻ tấn công giả mạo địa chỉ MAC của AP để gửi hàng loạt khung tin hủy xác thực đến máy khách. Máy khách không có cách nào phân biệt được đâu là lệnh ngắt kết nối thật từ AP và đâu là lệnh giả mạo, nên buộc phải ngắt kết nối. Khi người dùng cố gắng kết nối lại, kẻ tấn công tiếp tục gửi các gói tin giả mạo với tần suất dày đặc. Mục đích của cuộc tấn công này thường không phải là phá hoại đơn thuần, mà là ép thiết bị phải tự động kết nối lại nhằm thu thập gói tin bắt tay (Handshake) để dò mật khẩu, hoặc ép nạn nhân chuyển sang kết nối với mạng Evil Twin do kẻ tấn công dựng sẵn. Trong cùng nhóm tấn công ngắt kết nối còn có Disassociation Attack (sử dụng khung tin hủy liên kết để ngắt kết nối vật lý), nhưng Deauthentication là kỹ thuật phổ biến và là trọng tâm của đề tài này.

Hình 1.7. Sơ đồ tấn công huỷ xác thực (Deauthentication Attack)

### Tấn công phát lại (Replay Attack)

Đây là hình thức tấn công chủ động (active attack), trong đó kẻ tấn công chặn bắt một gói tin hoặc thông điệp hợp lệ đã được truyền đi trước đó, sau đó phát lại (replay) chính gói tin đó vào một thời điểm khác nhằm đánh lừa hệ thống. Bản chất của kỹ thuật này không nằm ở việc phá mã hóa hay dò mật khẩu, mà khai thác lỗ hổng thiếu cơ chế kiểm tra “tính tươi mới” (freshness) của dữ liệu. Trong mạng không dây, kẻ tấn công có thể ghi lại các gói tin xác thực hoặc gói tin bắt tay hợp lệ, sau đó gửi lại chúng về phía mục tiêu. Nếu hệ thống không có cơ chế phát hiện sự trùng lặp, nó sẽ xử lý gói tin phát lại như một yêu cầu hợp pháp mới. Điều này cho phép kẻ tấn công mạo danh người dùng hợp pháp hoặc thực hiện các hành vi trái phép mà không cần biết khóa bí mật. Điển hình, kỹ thuật này thường được kết hợp với tấn công xen giữa (MitM) để đánh cắp hoặc làm giả các phiên giao dịch, hoặc được sử dụng để khai thác các lỗ hổng trong quá trình bắt tay của giao thức WPA2, gây ảnh hưởng trực tiếp đến tính toàn vẹn và bảo mật của mạng không dây.

Hình 1.8. Sơ đồ tấn công phát lại (ReplayAttack)

### Tấn công từ chối dịch vụ phân tán (DDoS)

DDoS là hình thức tấn công từ chối dịch vụ nhưng sử dụng nhiều nguồn tấn công phân tán (thường là mạng lưới thiết bị bị nhiễm mã độc - botnet) đồng loạt gửi lưu lượng rác đến mục tiêu. Trong mạng không dây, DDoS thường nhắm trực tiếp vào AP nhằm làm cạn kiệt tài nguyên xử lý hoặc băng thông của thiết bị này. Một kỹ thuật điển hình là tấn công làm tràn bảng liên kết (Association Flood). Kẻ tấn công gửi hàng loạt yêu cầu xác thực giả mạo với địa chỉ MAC ngẫu nhiên. AP buộc phải cấp phát bộ nhớ để duy trì trạng thái cho các kết nối ảo này. Khi bảng trạng thái bị tràn, AP sẽ từ chối phục vụ các yêu cầu kết nối mới từ người dùng hợp pháp, khiến mạng bị mất khả năng phục vụ. DDoS tấn công vào khả năng xử lý logic của thiết bị mạng, khiến toàn bộ hệ thống bị tê liệt dù sóng vô tuyến vẫn hoạt động bình thường.

Hình 1.9. Sơ đồ tấn công từ chối dịch vụ phân tán (DDoS)

#  PHÂN TÍCH TẤN CÔNG DEAUTHENTICATION TRÊN MẠNG KHÔNG DÂY

## Cơ chế quản lý kết nối và lỗ hổng bảo mật của chuẩn 802.11

### Quá trình thiết lập và duy trì kết nối

Trong kiến trúc mạng IEEE 802.11, cơ chế thiết lập và duy trì kết nối được quy định chặt chẽ thông qua việc trao đổi các khung tin quản lý (Management Frames) tại phân lớp MAC. Về bản chất, đây là quá trình thiết lập một trạng thái logic (State) giữa trạm không dây (STA) và Điểm truy cập (AP). Để một STA có thể truyền nhận dữ liệu, nó bắt buộc phải tuần tự trải qua các trạng thái bao gồm: quét mạng để tìm kiếm AP, thực hiện xác thực (Authentication) và cuối cùng là liên kết (Association) để chính thức gia nhập vào Không gian dịch vụ cơ bản (BSS). 

Tuy nhiên, từ góc độ phân tích bảo mật, quy trình nền tảng này lại tồn tại một lỗ hổng thiết kế nghiêm trọng. Trong các phiên bản chuẩn 802.11 ban đầu, các khung tin quản lý phục vụ quá trình xác thực và liên kết không được tích hợp bất kỳ cơ chế mã hóa hay xác thực nguồn gốc nào (unauthenticated). Hệ quả là bất kỳ thiết bị nào nằm trong vùng phủ sóng cũng có thể dễ dàng thu thập các thông số định danh như địa chỉ MAC của STA và AP thông qua quá trình nghe lén. Đặc biệt, sau khi trạng thái kết nối được thiết lập, chuẩn 802.11 cho phép hủy bỏ trạng thái này thông qua khung tin Deauthentication. Đây là một tính năng hợp pháp nhằm cho phép thiết bị chủ động ngắt kết nối. Tuy nhiên, do khung tin này không được bảo vệ, thiết bị tiếp nhận hoàn toàn không có khả năng phân biệt đâu là yêu cầu ngắt kết nối thực sự từ chủ sở hữu hợp pháp và đâu là gói tin giả mạo do kẻ tấn công phát tán. [3]

Hình 2.1**. **Biểu đồ tuần tự tấn công Deauthentication

- **Giai đoạn thiết lập kết nối hợp pháp**

Tiến trình bắt đầu khi Client có nhu cầu gia nhập mạng. Trước tiên, Client khởi tạo trạng thái xác thực bằng cách gửi khung Authentication Request đến AP. AP tiếp nhận và phản hồi bằng khung Authentication Response để xác nhận chấp thuận. Ngay sau khi xác thực thành công, Client tiếp tục gửi khung Association Request nhằm yêu cầu được liên kết vào Không gian dịch vụ cơ bản (BSS). AP đáp lại bằng khung Association Response, chính thức cấp quyền cho Client tham gia vào mạng. Kể từ thời điểm này, một trạng thái kết nối logic được thiết lập giữa hai bên, cho phép Client bắt đầu truyền các gói tin dữ liệu (Data) qua AP. Trong toàn bộ giai đoạn bắt tay này, kẻ tấn công có thể lắng nghe và ghi lại các gói tin quản lý không được mã hóa để trích xuất thông số định danh (địa chỉ MAC) của cả AP và Client.

- **Giai đoạn thực thi tấn công**

Lợi dụng trạng thái kết nối đang được duy trì và các thông tin định danh đã thu thập được, kẻ tấn công tiến hành phá vỡ kết nối thông qua kỹ thuật giả mạo. Biểu đồ thể hiện hai luồng tấn công diễn ra đồng thời:

- **Hướng về phía AP:** Attacker gửi khung Deauthentication với địa chỉ MAC nguồn bị giả mạo thành địa chỉ MAC của Client. Do AP không có cơ chế xác thực nguồn gốc cho loại khung tin này, nó chấp nhận gói tin và lập tức xóa trạng thái kết nối của Client khỏi bảng quản lý.

- **Hướng về phía Client:** Đồng thời, Attacker gửi khung Deauthentication với địa chỉ MAC nguồn bị giả mạo thành địa chỉ MAC của AP. Client tiếp nhận gói tin, tin rằng AP đang chủ động ngắt kết nối với mình nên lập tức hủy bỏ trạng thái kết nối hiện tại.

Sau khi hai khung tin Deauthentication giả mạo được gửi đi, kết nối giữa Client và AP bị phá vỡ hoàn toàn từ cả hai phía. Tiến trình này không yêu cầu kẻ tấn công phải phá mã hóa hay dò tìm mật khẩu. Hậu quả trực tiếp là Client bị mất kết nối mạng và buộc phải quay lại trạng thái ban đầu (bắt đầu lại từ bước Authentication Request) nếu muốn tiếp tục truy cập. Chính khoảng thời gian gián đoạn này tạo ra điều kiện tiên quyết để kẻ tấn công triển khai các kỹ thuật tấn công phức hợp tiếp theo, chẳng hạn như bắt gói tin Handshake phục vụ dò mật khẩu hoặc lôi kéo thiết bị kết nối vào một AP giả mạo (Evil Twin).

### Lỗ hổng trong thiết kế khung tin quản lý

Cơ chế quản lý trạng thái kết nối của chuẩn IEEE 802.11 tồn tại một lỗ hổng thiết kế mang tính hệ thống: các khung tin quản lý (Management Frames), bao gồm khung Deauthentication, không được tích hợp bất kỳ cơ chế xác thực nguồn gốc nào. Điều này dẫn đến việc thiết bị tiếp nhận không có khả năng kiểm tra tính hợp lệ của nguồn gửi, từ đó tạo điều kiện cho các cuộc tấn công giả mạo. Lỗ hổng này không xuất phát từ lỗi lập trình hay cấu hình sai lệch, mà là hệ quả trực tiếp từ kiến trúc quy định phân loại khung tin của chuẩn 802.11. 

Nguyên nhân sâu xa của lỗ hổng được lý giải thông qua nghiên cứu của Martinovic và cộng sự (2006). Theo đó, chuẩn 802.11 phân chia các loại khung tin thành ba lớp (Class 1, 2 và 3) dựa trên chức năng và trạng thái kết nối. Các khung tin quản lý như Deauthentication được xếp vào nhóm Class 1. Theo quy định của máy trạng thái (State Machine), khung tin Class 1 được phép gửi và nhận ở mọi trạng thái của kết nối, kể cả trước khi thiết bị được xác thực hoặc thiết lập khóa phiên. Quy định này xuất phát từ yêu cầu cung cấp các dịch vụ cơ bản cho việc khám phá mạng và quản lý kết nối. Chính vì khung quản lý phải hoạt động độc lập trước khi quá trình bắt tay (handshake) thiết lập khóa diễn ra, chuẩn 802.11i (WPA/WPA2) đã không thể áp dụng cơ chế xác thực mật mã cho nhóm khung tin này.  [4]

Hình 2.2. Máy trạng thái kết nối trong chuẩn IEEE 802.11

Cơ chế quản lý kết nối của chuẩn IEEE 802.11 được xây dựng dựa trên một máy trạng thái (State Machine) chặt chẽ, quy định vòng đời của một trạm không dây (Client) từ khi gia nhập đến khi rời mạng. Lỗ hổng dẫn đến tấn công Deauthentication không nằm ở lỗi lập trình, mà xuất phát trực tiếp từ kiến trúc phân cấp trạng thái và phân loại khung tin của chuẩn này.  [4]

Quá trình vận hành của máy trạng thái được thể hiện cụ thể qua ba giai đoạn của vòng đời kết nối: 

- **State 1 (Chưa xác thực, chưa liên kết):** Trạng thái khởi điểm của thiết bị. Tại đây, thiết bị chỉ được phép xử lý các khung tin Class 1 (bao gồm các khung quản lý cơ bản như Beacon, Probe và Deauthentication). 

- **State 2 (Đã xác thực, chưa liên kết):** Khi quá trình xác thực thành công, thiết bị chuyển sang State 2. Lúc này, nó được phép xử lý thêm các khung tin Class 2 (phục vụ quá trình liên kết như Association Request/Response). 

- **State 3 (Đã xác thực, đã liên kết):** Sau khi liên kết thành công, thiết bị đạt đến trạng thái kết nối đầy đủ. Tại State 3, thiết bị được phép truyền nhận toàn bộ các khung tin Class 1, 2 và 3 (bao gồm cả khung dữ liệu Data). 

Tiến trình thiết lập kết nối diễn ra tuần tự từ State 1 lên State 3. Tuy nhiên, lỗ hổng thiết kế xuất hiện ở luồng chuyển trạng thái ngược, tức là quá trình ngắt kết nối. Từ trạng thái kết nối đầy đủ (State 3), thiết bị có thể bị đẩy lùi trực tiếp về State 1 thông qua khung tin Deauthentication. 

Điểm mấu chốt tạo nên lỗ hổng là việc khung Deauthentication được phân loại vào nhóm Class 1, nhóm khung tin được phép xuất hiện ở mọi trạng thái của vòng đời kết nối. Quy định này dẫn đến hệ quả tất yếu: do khung Class 1 phải hoạt động độc lập ngay từ State 1 (khi thiết bị chưa được thiết lập khóa phiên), chuẩn bảo mật 802.11i (WPA/WPA2) không thể áp dụng cơ chế xác thực mật mã cho nhóm khung tin này. Kẻ tấn công lợi dụng chính bước chuyển trạng thái từ State 3 về State 1 để gửi khung Deauthentication giả mạo với địa chỉ MAC bị làm giả, ép thiết bị nạn nhân ngắt kết nối mà không cần vượt qua bất kỳ rào cản xác thực nào.

## Cơ chế kỹ thuật và phương thức thực thi tấn công

### Kỹ thuật giả mạo và phân tích gói tin

Kỹ thuật thực thi tấn công Deauthentication không dựa trên việc phá giải các cơ chế mã hóa mật mã, mà dựa trên sự kết hợp giữa việc lợi dụng lỗ hổng định danh của giao thức và khả năng quan sát luồng truyền thông. Quá trình này bao gồm hai giai đoạn có mối quan hệ nhân quả chặt chẽ: phân tích gói tin để thu thập thông tin định danh, và giả mạo địa chỉ MAC để thực thi hành vi phá vỡ kết nối. 

Trước khi có thể giả mạo, kẻ tấn công phải xác định được các thông số định danh của mục tiêu. Trong môi trường không dây, mọi khung tin (bao gồm khung quản lý, khung điều khiển và khung dữ liệu) đều được truyền đi trong không gian mở và có thể bị thu nhận bởi bất kỳ thiết bị nào nằm trong vùng phủ sóng. Bằng cách đưa card mạng vào chế độ giám sát (monitor mode), kẻ tấn công có thể ghi lại toàn bộ các khung tin trao đổi giữa AP và Client. Các khung tin quản lý như Beacon, Probe Request/Response, Authentication và Association đều chứa địa chỉ MAC nguồn và đích ở dạng không mã hóa. Quá trình phân tích các khung tin này cho phép kẻ tấn công trích xuất chính xác địa chỉ MAC của AP (BSSID), địa chỉ MAC của Client mục tiêu, và kênh truyền sóng mà chúng đang sử dụng. Thông tin định danh này có thể bị thu thập một cách thụ động mà không cần tương tác với hệ thống, do chuẩn 802.11 không tích hợp cơ chế bảo vệ cho các khung tin quản lý ở giai đoạn này. [5] 

Sau khi đã có đầy đủ thông tin định danh, kẻ tấn công chuyển sang giai đoạn giả mạo. Bản chất của kỹ thuật này xuất phát từ việc chuẩn IEEE 802.11 dựa hoàn toàn vào địa chỉ MAC nguồn được khai báo trong header của mỗi khung tin. Đối với các khung tin thuộc nhóm Class 1 (bao gồm Deauthentication), giao thức không tích hợp bất kỳ cơ chế mật mã nào để xác minh rằng thiết bị gửi có thực sự sở hữu địa chỉ MAC đó hay không. Kỹ thuật giả mạo địa chỉ MAC xuất phát từ một đặc điểm kỹ thuật của phần cứng mạng. Mặc dù địa chỉ MAC được thiết kế như một định danh cố định và duy nhất cho mỗi card mạng, hầu hết các driver card mạng hiện đại đều cho phép ghi đè địa chỉ này thông qua phần mềm. Kỹ thuật này được gọi là MAC Spoofing, cho phép kẻ tấn công thay đổi địa chỉ MAC của card mạng tấn công thành bất kỳ giá trị nào mong muốnLợi dụng điểm yếu này, kẻ tấn công thay đổi địa chỉ MAC của card mạng tấn công thành địa chỉ MAC của AP hoặc của Client mục tiêu. Khi gửi khung Deauthentication giả mạo, thiết bị nhận sẽ kiểm tra header, thấy địa chỉ nguồn hợp lệ và lập tức chấp nhận yêu cầu ngắt kết nối mà không thể phân biệt được đâu là lệnh thật từ chủ sở hữu hợp pháp . 

Để làm rõ tính xác thực của kỹ thuật giả mạo trong thực tế, có thể phân tích cấu trúc của một khung Deauthentication được ghi lại bằng công cụ phân tích gói tin Wireshark. Trong một khung tin bị giả mạo, trường Source address (địa chỉ nguồn) sẽ hiển thị địa chỉ MAC của AP hoặc Client hợp pháp, trong khi khung tin thực chất được phát đi từ thiết bị của kẻ tấn công. Sự không khớp giữa địa chỉ MAC nguồn và nguồn gốc vật lý của tín hiệu (có thể được xác định thông qua phân tích cường độ tín hiệu RSSI) là dấu hiệu kỹ thuật để nhận diện hành vi giả mạo [5].

- **Destination address (Địa chỉ đích):** Tp-LinkT_fe:98:d2 - đây là địa chỉ MAC của AP đang nhận gói tin.

- **BSS Id (Định danh không gian dịch vụ cơ bản):** Tp-LinkT_fe:98:d2 - trùng khớp với địa chỉ của AP, xác nhận gói tin đang được gửi đến đúng mạng mục tiêu.

- **Source address (Địa chỉ nguồn):** IntelCor_26:a3:78 - đây là địa chỉ MAC của thiết bị được cho là đã gửi khung tin. Trong kịch bản tấn công, đây chính là địa chỉ MAC của Client hợp pháp đã bị kẻ tấn công thu thập và giả mạo.

Điểm mấu chốt nằm ở trường Source address. Trong giao thức 802.11, trường này được điền bởi chính thiết bị gửi khung tin, và giao thức không tích hợp bất kỳ cơ chế mật mã nào (như chữ ký số hay mã xác thực tin nhắn) để chứng minh rằng thiết bị gửi thực sự sở hữu địa chỉ MAC đó. Khi AP nhận được khung Deauthentication với trường Source address là địa chỉ của Client, AP sẽ tin rằng Client đang yêu cầu ngắt kết nối và lập tức thực thi lệnh Deauth mà không có cơ chế kiểm tra** **nguồn gốc thực sự của gói tin đến từ kẻ tấn công, có thể được xác định thông qua phân tích cường độ tín hiệu RSSI hoặc vị trí địa lý khác biệt so với Client thật.

Sự kết hợp giữa phân tích gói tin và giả mạo địa chỉ MAC cho phép kẻ tấn công thực hiện cuộc tấn công Deauthentication một cách hiệu quả với nguồn lực tối thiểu. Kẻ tấn công không cần phải thiết lập một kết nối hợp pháp với AP, không cần phải biết mật khẩu mạng, và không cần phải tương tác trực tiếp với thiết bị nạn nhân. Tất cả những gì cần thiết là khả năng thu nhận các khung tin quản lý trong không gian mở và khả năng thay đổi địa chỉ MAC của card mạng. Chính sự đơn giản về mặt kỹ thuật nhưng lại có hiệu quả phá vỡ kết nối cao đã khiến Deauthentication trở thành một trong những kỹ thuật tấn công từ chối dịch vụ phổ biến nhất trong mạng không dây.

### Các hình thức thực thi tấn công Deauthentication

Sau khi đã có thông tin định danh và làm chủ kỹ thuật giả mạo MAC, kẻ tấn công triển khai tấn công Deauthentication theo hai nhóm chính dựa trên cách thức tương tác với mạng: tấn công chủ động và tấn công thụ động:

- **Tấn công chủ động (Active De-Authentication Attacks)**

Tấn công chủ động là hình thức kẻ tấn công trực tiếp tạo ra và phát tán các khung Deauthentication giả mạo vào môi trường không dây. Đặc điểm cốt lõi của nhóm này là kẻ tấn công phải có khả năng chèn khung tin (frame injection) – tức là gửi các gói tin không có nguồn gốc hợp pháp vào mạng. Hành vi này can thiệp trực tiếp vào luồng truyền thông, tạo ra các gói tin không tồn tại trong hoạt động bình thường của mạng. Do tính chất can thiệp trực tiếp, nhóm tấn công này có thể gây ra hậu quả tức thời nhưng cũng dễ bị phát hiện hơn bởi các hệ thống giám sát do xuất hiện các khung tin bất thường về tần suất hoặc nguồn gốc. 

Nhóm tấn công chủ động được phân thành bốn hình thức với phạm vi tác động tăng dần:

**Tấn công cơ bản (Basic De-Authentication Attack):** là hình thức đơn giản nhất, trong đó kẻ tấn công gửi khung Deauth giả mạo đến một thiết bị mục tiêu duy nhất. Mục đích là buộc thiết bị đó ngắt kết nối khỏi mạng. Phương thức này thường được thực hiện bằng công cụ aireplay-ng và có hiệu quả cao khi kẻ tấn công muốn vô hiệu hóa một mục tiêu cụ thể [6].

Hình 2.3. Sơ đồ tấn công Deauthentication cơ bản

**Tấn công quảng bá (Broadcast De-Authentication Attack)**: là hình thức tấn công mở rộng phạm vi tác động bằng cách gửi khung Deauth đến địa chỉ quảng bá (broadcast address). Khi đó, mọi thiết bị trong vùng phủ sóng của kẻ tấn công đều nhận được lệnh ngắt kết nối, dẫn đến gián đoạn đồng thời trên diện rộng. Hình thức này thường được thực hiện bằng công cụ MDK3 để làm tràn ngập mạng [6].

Hình 2.4. Sơ đồ tấn công Deauthentication quảng bá

**Tấn công có chủ đích (Directed De-Authentication Attack):** thể hiện sự nhắm mục tiêu chính xác hơn. Kẻ tấn công xác định địa chỉ MAC của một thiết bị hoặc một nhóm thiết bị cụ thể và gửi khung Deauth trực tiếp đến các địa chỉ đó. Phương thức này cho phép kẻ tấn công lựa chọn chính xác nạn nhân, tương tự như tấn công cơ bản nhưng có chủ đích rõ ràng hơn [6].

Hình 2.5. Sơ đồ tấn công Deauthentication có chủ đích

**Tấn công tràn ngập (De-Authentication Flood Attack):** là hình thức có mức độ tác động mạnh nhất trong nhóm. Kẻ tấn công gửi một lượng lớn khung Deauth với tần suất cao để làm tràn ngập các kênh truyền thông, khiến toàn bộ mạng bị tê liệt và không thể hoạt động bình thường. Hình thức này thường được sử dụng trong các cuộc tấn công quy mô lớn tại các sự kiện công cộng [6].

- **Tấn công thụ động (Passive De-Authentication Attacks)**

Khác với nhóm tấn công chủ động, tấn công thụ động không chèn trực tiếp các khung Deauthentication vào mạng. Thay vào đó, kẻ tấn công lợi dụng các lỗ hổng trong quá trình xử lý khung tin của giao thức 802.11 để gây ra các đợt ngắt kết nối gián đoạn. Đặc điểm này khiến các cuộc tấn công thụ động khó bị phát hiện hơn bởi các hệ thống giám sát thông thường, do không có dấu hiệu bất thường rõ ràng về tần suất khung Deauth. Hành vi của kẻ tấn công hòa lẫn vào các hoạt động bình thường của mạng, khiến việc phân biệt giữa lưu lượng hợp pháp và lưu lượng tấn công trở nên khó khăn. 

Nhóm tấn công thụ động được phân thành ba hình thức:

**Tấn công qua khung Beacon (Beacon Frame De-Authentication Attack)****:** khai thác lỗ hổng trong quá trình xử lý khung Beacon của thiết bị. Bằng cách thao túng các khung Beacon, kẻ tấn công có thể gây ra các đợt ngắt kết nối gián đoạn mà không cần gửi khung Deauth trực tiếp, khiến thiết bị mất kết nối trong thời gian ngắn và liên tục [6].

**Tấn công qua chế độ tiết kiệm năng lượng (Power Save De-Authentication Attack)****:** lợi dụng cơ chế tiết kiệm năng lượng của thiết bị. Kẻ tấn công ép thiết bị mục tiêu vào trạng thái ngủ, làm gián đoạn liên lạc của chúng với mạng. Kết quả là thiết bị bị ngắt kết nối định kỳ, ảnh hưởng đến các ứng dụng yêu cầu kết nối liên tục như IoT hoặc giám sát từ xa  [6].

**Tấn công qua quá trình trao đổi Probe Request/Response (Probe Request Response De-Authentication Attack)****:** lợi dụng quá trình trao đổi Probe Request và Response giữa thiết bị và AP. Bằng cách thao túng hoặc chèn các yêu cầu/phản hồi Probe giả mạo, kẻ tấn công có thể phá vỡ quá trình kết nối của thiết bị, dẫn đến các đợt ngắt kết nối gián đoạn mà không cần gửi khung Deauth trực tiếp  [6].

## Vai trò của Deauthentication trong các kịch bản tấn công phức hợp

Tấn công deauthentication (deauth) về bản chất là một dạng từ chối dịch vụ nhắm vào liên kết giữa người dùng và AP Wi-Fi . Kỹ thuật này không trực tiếp đánh cắp dữ liệu hay chiếm quyền điều khiển hệ thống. Giá trị của nó nằm ở việc buộc một sự kiện mạng xảy ra theo ý kẻ tấn công: thiết bị bị ngắt kết nối rồi phải kết nối lại. Sự kiện này mở đường cho giai đoạn khai thác thực sự. Vì vậy, trong các chuỗi tấn công phức hợp, deauth nên được xem là bước chuẩn bị (staging) hơn là vũ khí chính.

Khả năng này bắt nguồn từ một điểm yếu thiết kế của chuẩn 802.11. Bellardo và Savage chỉ ra rằng các khung quản lý của giao thức không được xác thực, nên kẻ tấn công có thể giả mạo địa chỉ nguồn và gây gián đoạn dịch vụ chỉ với lượng gói tin nhỏ trên phần cứng thương mại [3]. Trong các mạng trước WPA3, khung deauth và disassociation vẫn thuộc nhóm khung quản lý không được bảo vệ, do đó việc giả mạo chúng đơn giản và ít tốn kém . Chi phí thấp này lý giải vì sao deauth xuất hiện thường xuyên trong cả hai kịch bản được phân tích dưới đây.

### Tiền đề cho tấn công dò mật khẩu (Handshake Capture)

Để tiến hành dò mật khẩu bằng phương pháp vét cạn hoặc từ điển trên mạng WPA/WPA2, kẻ tấn công trước hết phải thu được bản bắt tay bốn bước (4-way handshake). Chuỗi này có thể được kích hoạt bằng cách ép người dùng ngắt kết nối thông qua tấn công deauth [6]. Một bài tổng hợp về nghiên cứu WPA3 cũng ghi nhận rằng bước đầu tiên để bắt handshake là tấn công deauthentication.

Hình 2.6. Quy trình bắt tay 4 bước  trong WPA/WPA2

Trong mạng WPA/WPA2-PSK, khóa chủ PMK được suy ra từ passphrase và SSID. Khóa này được cả client và AP biết trước, và không bao giờ được truyền qua môi trường không dây. Khi client kết nối, hai bên thực hiện bản bắt tay bốn bước (4-way handshake) để thiết lập khóa phiên PTK. PTK được suy ra từ PMK, hai số ngẫu nhiên do mỗi bên sinh ra (ANonce và SNonce) và địa chỉ MAC của cả hai thiết bị. Để chứng minh đã sở hữu đúng PMK, client gửi kèm trong thông điệp thứ hai một mã toàn vẹn MIC được tính từ PTK.

Điểm yếu nằm ở chỗ ANonce, SNonce, địa chỉ MAC và MIC đều được truyền ở dạng không mã hóa. Kẻ tấn công thu được các giá trị này có thể thực hiện tấn công từ điển hoặc vét cạn theo quy trình sau: với mỗi passphrase ứng viên, tính PMK, rồi tính PTK, sau đó tính lại MIC và so sánh với MIC đã bắt được. Nếu hai giá trị trùng khớp, passphrase ứng viên đó chính là mật khẩu của mạng. Toàn bộ quá trình kiểm tra được thực hiện ngoại tuyến, không đòi hỏi bất kỳ tương tác nào thêm với AP, nên kẻ tấn công không bị giới hạn số lần thử và không để lại dấu vết trên mạng mục tiêu. Do đó, việc thu được handshake là điều kiện tiên quyết của tấn công, và đây chính là lý do kẻ tấn công cần đến deauth để ép handshake xuất hiện

Bảng 2.1. Đánh giá vai trò Deauth trong kịch bản Handshake

| **Tiêu chí** | **Nhận định** |
| --- | --- |
| **Vai trò** | Rút ngắn thời gian chờ đợi - thay vì chờ client tự reconnect (có thể vài giờ/ngày), kẻ tấn công chủ động ép xảy ra trong vài giây |
| **Mức độ** **quyết định** | Trung bình - handshake vẫn có thể bắt được thụ động (passive sniffing) nếu đủ kiên nhẫn, deauth chỉ tăng tốc |
| **Điểm nghẽn** **thực sự** | Nằm ở bước sau deauth: độ mạnh của passphrase. Handshake yếu (WPA3-SAE) gần như vô dụng dù có bắt được |
| **Dấu vết** **để lại** | Dễ bị phát hiện qua WIDS vì deauth burst là pattern bất thường rõ rệt |

Deauth trong kịch bản này đóng vai trò công cụ tăng tốc. Nó có giá trị chiến thuật cao vì chuyển tấn công từ thụ động sang chủ động, nhưng không quyết định kết quả cuối cùng. Yếu tố quyết định là sức mạnh của mật khẩu và chuẩn mã hóa. WPA2-PSK dễ bị tấn công từ điển ngoại tuyến hơn nhiều so với WPA3-SAE nhờ cơ chế trao đổi khóa khác biệt. Cần lưu ý rằng lợi thế của WPA3 chỉ trọn vẹn ở chế độ thuần. Ở chế độ chuyển tiếp WPA2/WPA3 (transition mode), thiết bị chỉ hỗ trợ WPA2 vẫn có thể bị lợi dụng để thu một phần handshake.

### Tiền đề cho tấn công Evil Twin / Man-in-the-Middle

Evil Twin là điểm truy cập giả mạo, sao chép SSID (thường cả BSSID tương sang AP giả này, từ đó thu thập gói tin trao đổi giữa client và mạng  [6]. Quy trình điển hình là kẻ tấn công ngắt client khỏi mạng thật, sau đó thiết bị tự động kết nối lại và rơi vào AP giả. Một số công cụ lừa đảo Wi-Fi cũng bắt đầu chuỗi tấn công bằng deauth để ngắt người dùng khỏi AP hợp pháp trước khi dựng trang giả mạo. 

Bảng 2.2. Đánh giá vai trò Deauth trong Evil Twin

| **Tiêu chí** | **Nhận định** |
| --- | --- |
| **Vai trò** | Không chỉ tăng tốc mà còn định hướng hành vi nạn nhân - ép client rời bỏ AP thật, không còn lựa chọn nào khác ngoài AP giả |
| **Mức độ** **quyết định** | Cao hơn hẳn so với kịch bản 1 - nếu không có deauth liên tục, client có thể tự quay lại AP thật bất cứ lúc nào (do tín hiệu khỏe hơn hoặc đã xác thực sẵn), phá vỡ toàn bộ kịch bản MITM |
| **Điểm nghẽn** **thực sự** | Đây là khác biệt lớn nhất: deauth trong Evil Twin thường phải chạy liên tục trong suốt phiên tấn công, không phải một lần như kịch bản bắt handshake |
| **Dấu vết** **để lại** | Cao hơn nhiều - phát sóng deauth liên tục bằng với dễ bị phát hiện bằng công cụ giám sát RF, đồng thời thời gian tấn công kéo dài tăng khả năng bị lộ |

Trong kịch bản này, deauth gần như là hạ tầng duy trì tấn công (attack enabler) chứ không chỉ là bước khởi động. Vai trò của nó quan trọng hơn so với kịch bản dò mật khẩu vì thiếu nó, cả chuỗi MITM có thể đổ vỡ giữa chừng. Đồng thời, đây cũng là điểm yếu: hiệu quả của deauth giảm mạnh khi mạng triển khai Protected Management Frames (PMF, IEEE 802.11w), vì khi đó các khung deauth giả mạo bị từ chối. Điều này khiến việc bật PMF trở thành biện pháp phòng thủ đáng ưu tiên đối với kịch bản Evil Twin.

## Các giải pháp phát hiện và phòng chống

### Tiêu chuẩn bảo vệ khung tin quản lý (IEEE 802.11w - PMF)

IEEE 802.11w được công bố năm 2009 và sau đó hợp nhất vào bản chuẩn IEEE 802.11 . Tiêu chuẩn này bổ sung cơ chế bảo vệ cho các khung quản lý dạng “robust” như Deauthentication, Disassociation và một số khung Action, áp dụng sau khi thiết bị đã hoàn tất kết nối. Trong tài liệu của Wi-Fi Alliance và các hãng thiết bị, tính năng này được gọi là Protected Management Frames (PMF) hoặc Management Frame Protection (MFP). Đây là giải pháp xử lý trực tiếp nguyên nhân gốc của tấn công, vì khung Deauthentication giả mạo không còn được AP và máy khách chấp nhận. Cơ chế bảo vệ gồm các thành phần chính:

- **Khung unicast:** khung Deauthentication/Disassociation gửi giữa AP và máy khách đã kết hợp được mã hóa và kiểm tra toàn vẹn bằng PTK sinh ra ở bước bắt tay 4 bước (4-way handshake), kèm bộ đếm chống phát lại. Kẻ tấn công không có khóa nên khung giả bị loại bỏ.

- **Khung broadcast/multicast:** được bảo vệ bằng BIP (Broadcast/Multicast Integrity Protocol) với khóa IGTK, khung mang thêm phần tử MIC quản lý (MME) để bên nhận kiểm tra tính toàn vẹn. Cơ chế này ngăn kiểu tấn công gửi khung Deauthentication quảng bá làm mọi máy khách rớt mạng cùng lúc, nhưng chỉ chống được kẻ tấn công bên ngoài, tức là không biết khóa của mạng.

Hình 2.7. Cơ chế bảo vệ khung tin quản lý của IEEE 802.11w (PMF)

- **SA Query:** khi AP nhận được yêu cầu kết hợp lại từ một máy khách đang kết nối, AP không chấp nhận ngay mà gửi khung SA Query có bảo vệ để xác nhận máy khách thật còn đang hoạt động, qua đó chặn việc giả mạo yêu cầu kết hợp để làm gián đoạn phiên.

- **Chế độ hoạt động:** được khai báo bằng các bit MFPC (Management Frame Protection Capable) và MFPR (Required) trong trường RSN Capabilities, tương ứng ba mức Disabled, Optional (Capable) và Required. WPA3 yêu cầu PMF; với WPA2, PMF là tùy chọn và cần được bật thủ công.

Khi PMF được áp dụng, các công cụ như aireplay-ng vẫn có thể phát khung Deauthentication giả nhưng máy khách bỏ qua chúng, nhờ đó kẻ tấn công không còn cách ép nạn nhân rời AP thật để thu bắt bắt tay (handshake) hoặc chuyển sang evil twin. Tuy nhiên, PMF có những giới hạn cần lưu ý. Thứ nhất, các khung trước khi khóa được thiết lập (Beacon, Probe, Authentication, Association) không được bảo vệ, nên khung Deauthentication gửi ở giai đoạn kết nối ban đầu vẫn có thể gây gián đoạn. Thứ hai, PMF không chống được nhiễu sóng vô tuyến (jamming) ở tầng vật lý. Thứ ba, thiết bị cũ hoặc IoT có thể không hỗ trợ PMF: đặt chế độ Required sẽ khiến các thiết bị này không kết nối được, còn chế độ Optional thì những máy khách không hỗ trợ PMF vẫn dễ bị tấn công.

### Hệ thống phát hiện xâm nhập (WIDS/WIPS)

Hệ thống phát hiện xâm nhập mạng không dây (WIDS) giám sát thụ động môi trường vô tuyến thông qua các cảm biến chuyên dụng hoặc AP hoạt động ở chế độ giám sát, thu và phân tích các khung 802.11 để cảnh báo hành vi bất thường. Hệ thống ngăn chặn xâm nhập (WIPS) bổ sung khả năng phản ứng tự động khi phát hiện tấn công. Khác với PMF, WIDS/WIPS không làm khung giả mất tác dụng ở phía máy khách mà giúp quản trị viên phát hiện, định vị và xử lý nguồn tấn công, kể cả trong những trường hợp PMF chưa được bật hoặc không áp dụng được.

Hình 2.8. Kiến trúc hệ thống WIDS/WIPS

Đối với tấn công Deauthentication, hệ thống thường dựa vào các dấu hiệu sau:

- **Tần suất khung:** số lượng khung Deauthentication/Disassociation trong một đơn vị thời gian vượt ngưỡng, đặc biệt là khung gửi đến địa chỉ quảng bá hoặc gửi lặp lại tới nhiều máy khách của cùng một AP trong thời gian ngắn.

- **Số thứ tự khung (sequence number):** khung do kẻ tấn công phát ra mang số thứ tự không liên tục với chuỗi của AP thật, nên có thể bị phát hiện là giả mạo.

- **Cường độ tín hiệu và vị trí:** khung mang địa chỉ nguồn của AP hợp lệ nhưng có mức thu (RSSI) hoặc vị trí ước lượng khác với AP thật; nhiều cảm biến phối hợp còn cho phép định vị gần đúng thiết bị phát.

- **Tương quan sự kiện:** đợt Deauthentication kèm theo sự xuất hiện của AP lạ có cùng SSID hoặc BSSID giả mạo, hoặc máy khách liên tục kết nối lại, là dấu hiệu của bước chuẩn bị cho tấn công thu bắt handshake hoặc Evil Twin.

Khi có cảnh báo, hệ thống gửi thông báo qua syslog, SNMP hoặc nền tảng SIEM; một số sản phẩm WIPS có thể tự động thực hiện biện pháp ngăn chặn (containment) đối với AP giả mạo. Các hệ thống mã nguồn mở như Kismet cũng hỗ trợ cảnh báo kiểu tấn công này, còn các hãng thiết bị lớn tích hợp chức năng tương tự vào bộ điều khiển không dây. Cần lưu ý ba hạn chế: WIDS chỉ cảnh báo chứ không ngăn được khung giả đến máy khách; có thể xuất hiện cảnh báo sai khi AP dùng khung Deauthentication hợp lệ (ví dụ điều hướng băng tần hoặc chuyển vùng); và biện pháp ngăn chặn thường cũng dựa trên việc gửi khung Deauthentication nên có thể ảnh hưởng đến mạng của bên khác và vi phạm quy định pháp luật về can thiệp sóng vô tuyến, do đó cần cấu hình thận trọng.

### Các biện pháp cấu hình và vận hành

Ngoài các cơ chế kỹ thuật ở trên, nhiều rủi ro có thể giảm đáng kể nhờ cấu hình đúng và vận hành có kỷ luật:

- Mã hóa và xác thực mạnh: dùng WPA3, hoặc tối thiểu WPA2 với mã hóa AES-CCMP; không dùng WEP và TKIP. Với mạng dùng khóa chia sẻ trước, đặt mật khẩu dài và ngẫu nhiên để khó bị dò ngoại tuyến từ handshake đã thu bắt; WPA3-SAE còn chống được kiểu dò mật khẩu này. Với tổ chức, nên dùng 802.1X (WPA2/WPA3-Enterprise) và cấu hình để máy khách kiểm tra chứng chỉ của máy chủ RADIUS, nhằm chống Evil Twin.

- Bật PMF theo lộ trình: đặt Required nếu toàn bộ thiết bị hỗ trợ, đặt Optional trong giai đoạn chuyển tiếp. Nên tách thiết bị cũ hoặc IoT không hỗ trợ PMF sang SSID/VLAN riêng để không phải hạ mức bảo vệ của cả mạng. Băng tần 6 GHz (Wi-Fi 6E) vốn đã yêu cầu PMF.

- Cập nhật firmware và driver: đảm bảo AP, bộ điều khiển và thiết bị đầu cuối nhận các bản vá, đồng thời hỗ trợ đầy đủ PMF và các tính năng bảo mật mới.

- Thiết kế vùng phủ: điều chỉnh công suất phát và vị trí AP để vùng phủ sóng vừa đủ, hạn chế kẻ tấn công ở ngoài khuôn viên dễ dàng thu và phát khung vào mạng.

- Giám sát và kiểm tra định kỳ: bật ghi nhật ký, bật tính năng phát hiện rogue AP, và định kỳ khảo sát hoặc kiểm thử xâm nhập có ủy quyền để đánh giá mức độ chịu đựng của mạng trước tấn công Deauthentication.

- Biện pháp ở phía người dùng: hạn chế dùng Wi-Fi công cộng không mã hóa, tắt tự động kết nối vào mạng mở, xóa các mạng đã lưu không còn dùng, và dùng VPN để dữ liệu không ở dạng văn bản gốc nếu lỡ kết nối vào evil twin. Khi bị ngắt kết nối đột ngột nhiều lần rồi xuất hiện mạng trùng tên, người dùng không nên đăng nhập hoặc nhập thông tin nhạy cảm.

Tóm lại, không có biện pháp đơn lẻ nào đủ để loại bỏ hoàn toàn tấn công Deauthentication. Cách tiếp cận hợp lý là phòng thủ nhiều lớp: PMF xử lý tận gốc việc giả mạo khung quản lý, WIDS/WIPS phát hiện và định vị phần rủi ro còn lại, còn cấu hình và vận hành đúng đắn thu hẹp bề mặt tấn công và hạn chế hậu quả nếu tấn công vẫn xảy ra.

Bảng 2.3. Tổng hợp các giải pháp phòng chống Deauthentication Attack

| **Giải pháp** | **Khả năng ngăn chặn trực tiếp** | **Khả năng phát hiện, định vị** | **Chi phí và đô phức tạp** | **Tính tương thích thiết bị** |
| --- | --- | --- | --- | --- |
| **IEEE 802.11w (PMF)** | Cao (loại bỏ khung giả mạo từ bên ngoài) | Không (chỉ âm thầm thả/bỏ gói tin) | Rất thấp (hỗ trợ sẵn trên phần sụn/AP mới) | Trung bình (các thiết bị cũ, IoT đời cũ không hỗ trợ) |
| **WIDS/WIPS** | Thấp (WIDS) / Trung bình (WIPS) | Rất cao (đo lường ngưỡng, RSSI, vị trí) | Trung bình đến Cao (cần cảm biến, máy chủ giám sát) | Cao (hoạt động độc lập, không can thiệp vào client) |
| **Cấu hình ****&**** WPA3** | Triệt để với kiểu tấn công vét cạn handshake | Không | Thấp đến Trung bình (tùy chi phí nâng cấp phần cứng) | Trung bình (cần lộ trình chuyển dịch mạng) |

	

# THỰC NGHIỆM

## Tấn công Deauthenticaotion Flood

### Mô hình thực nghiệm

Bảng 3.1. Cấu hình thiết bị thực nghiệm tấn công Deauthentication Flood

| **Thành phần** | **Công cụ / phiên bản** |
| --- | --- |
| Máy ảo thực hiện mô phỏng tấn công | Kali Linux |
| Máy ảo hỗ trợ môi trường lab | Windows 10 |
| Phần mềm ảo hóa | VMware Workstation 17 |
| Công cụ tạo dữ liệu | Scapy |
| Công cụ phân tích | Wireshark |
| Định dạng dữ liệu | PCAP |

### Quy trình thực nghiệm

- Cài đặt Scapy trên Kali Linux

| sudo apt update sudo apt install python3-scapy -y |
| --- |

- Sau khi cài đặt, kiểm tra bằng lệnh:

| python3 -c "import scapy; print('Scapy OK')" |
| --- |

- Sử dụng soạn thảo văn bản Nano để tạo file:

| nano deauth_simulation.py |
| --- |

Chương trình sử dụng Scapy để tạo 500 frame Deauthentication và ghi chúng vào file PCAP.

Các frame được xây dựng từ những thành phần:

- RadioTap: phần header hỗ trợ thông tin vô tuyến trong file bắt gói.

- Dot11: phần header IEEE 802.11.

- Dot11Deauth: phần dữ liệu Deauthentication.

- Reason Code: giá trị 7.

- Chương trình tạo dữ liệu mô phỏng và lưu vào file:

| deauth_simulation.pcap |
| --- |

- Sau khi chạy chương trình, kết quả hiển thị:

| Da tao 500 frame Deauthentication mo phong! File: deauth_simulation.pcap |
| --- |

Như vậy, file PCAP chứa 500 frame Deauthentication đã được tạo thành công.

Sau khi tạo file trên Kali Linux, sử dụng HTTP Server để hỗ trợ chuyển file sang Windows 10 VM. Tiếp theo, sử dụng tính năng Shared Folders của VMware để chia sẻ thư mục giữa máy ảo Windows 10 và máy Windows thật.File deauth_simulation.pcap được sao chép vào thư mục chia sẻ và mở trên máy Windows thật.

- Mở Wireshark trên máy Windows thật.

| Chọn File → Open. Chọn file deauth_simulation.pcap. Nhập Display Filter: wlan.fc.type_subtype == 0x0c |
| --- |

Bộ lọc trên được sử dụng để hiển thị các frame Deauthentication trong dữ liệu IEEE 802.11.Kết quả thu được:

- Tổng số packet: 500.

- Số packet hiển thị: 500.

- Tỷ lệ packet phù hợp bộ lọc: 100%.

- Protocol: IEEE 802.11.

Điều này chứng minh bộ lọc hoạt động chính xác và cả 500 frame trong file đều được Wireshark nhận diện là Deauthentication.

- Chọn một packet bất kỳ, sau đó mở rộng trường: 

| IEEE 802.11 Deauthentication |
| --- |

- Các thông tin thu được:

| **Trường thông tin** | **Giá trị** |
| --- | --- |
| Type/Subtype | Deauthentication (0x000c) |
| Receiver Address | 11:22:33:44:55:66 |
| Destination Address | 11:22:33:44:55:66 |
| Transmitter Address | aa:bb:cc:dd:ee |
| Source Address | aa:bb:cc:dd:ee |
| BSS ID | aa:bb:cc:dd:ee |
| Reason Code | 7 |

- Nhận xét:

- Frame được Wireshark nhận diện là Deauthentication.

- Địa chỉ MAC nguồn và địa chỉ MAC đích được hiển thị rõ ràng.

- Reason Code có giá trị 7, đúng với giá trị được thiết lập trong chương trình Scapy.

- Các thông tin thu được phù hợp với dữ liệu đã tạo trong quá trình mô phỏng.

- Thống kê lưu lượng bằng I/O Graphs: chọn I/O Graphs trong Statistics

Bảng 3.2. Cấu hình thông số I/O Graphs

| **Thông số** | **Giá trị** |
| --- | --- |
| Display Filter | wlan.fc.type_subtype == 0x0c |
| Interval | 1 sec (sau đó thay đổi thành 1 ms) |
| Y Axis | Packets |
| Graph | Filtered packets |

Biểu đồ thể hiện 500 packet Deauthentication trong khoảng thời gian thống kê một giây. Kết quả khi Interval = 1 ms. Biểu đồ thể hiện mật độ frame chi tiết hơn theo từng khoảng thời gian 1 mili giây. Số frame trong từng khoảng được biểu diễn bằng các điểm trên biểu đồ, với giá trị quan sát cao nhất khoảng 4 packet trong một khoảng 1 ms.

Nhận xét: Việc thay đổi Interval từ 1 giây xuống 1 mili giây giúp quan sát rõ hơn sự phân bố của các frame theo thời gian. Đây là phương pháp hữu ích để phân tích mật độ gói tin và nhận biết các khoảng thời gian có lưu lượng tăng cao.

- Sau khi hoàn thành các bước, thu được kết quả như sau:

Bảng 3.3.  Kết quả thực thi các bước thực nghiệm

| **STT** | **Nội dung kiểm tra** | **Kết quả** |
| --- | --- | --- |
| 1 | Cài đặt Scapy | Thành công |
| 2 | Tạo frame mô phỏng | 500 frame |
| 3 | Xuất file PCAP | Thành công |
| 4 | Mở file bằng Wireshark | Thành công |
| 5 | Lọc frame Deauthentication | 500/500 frame |
| 6 | Kiểm tra địa chỉ MAC | Thành công |
| 7 | Kiểm tra Reason Code | 7 |
| 8 | Thống kê bằng I/O Graphs | Thành công |

### Kết quả thực nghiệm:

- Thực nghiệm đã đạt được các mục tiêu đề ra:

- Cài đặt và sử dụng thành công Scapy trên Kali Linux.

- Tạo được 500 frame Deauthentication mô phỏng.

- Xuất dữ liệu thành file PCAP và chuyển thành công sang máy Windows thật.

- Sử dụng Wireshark để lọc và phân tích frame.

- Xác định được địa chỉ MAC nguồn, MAC đích và Reason Code.

- Sử dụng I/O Graphs để thống kê mật độ frame theo thời gian.

- Do sử dụng môi trường mô phỏng ngoại tuyến nên thực nghiệm còn một số hạn chế:

- Các frame được tạo ra chỉ tồn tại trong file PCAP, không được phát trực tiếp qua card Wi-Fi.

- Chưa kiểm tra được tác động thực tế của Deauthentication Flood lên một mạng Wi-Fi.

- Chưa đánh giá được khả năng phát hiện và ngăn chặn Deauthentication Flood của các thiết bị mạng.

- Kết quả thống kê phản ánh dữ liệu mô phỏng, không đại diện cho lưu lượng của một cuộc tấn công thực tế.

## Tấn công giả mạo điểm truy cập (Evil Twin) bằng Wifiphisher

### Mô hình thực nghiệm

Bảng 3.4. Cấu hình thiết bị thực nghiệm tấn công Evil Twin

| **Thiết bị** | **Vai trò** | **Cấu hình / ghi chú** |
| --- | --- | --- |
| Máy Kali Linux | Máy tấn công (Attacker) | Cài đặt Wifiphisher, card mạng không dây wlan0 hỗ trợ chế độ Monitor/AP |
| Access Point thật | Mục tiêu tấn công | SSID: LAB WIFI — mạng không bảo mật (Open), dùng làm mục tiêu trong môi trường lab |
| Máy Windows XP | Nạn nhân (Victim) | Kết nối tới SSID “LAB WIFI”, đóng vai trò người dùng bị tấn công |

Hình 3.1. Mô hình tấn công Evil Twin bằng Wifiphisher

-  Máy Attacker cài sẵn Kali Linux cùng mã nguồn dự án Wifiphisher :

| sudo apt update && sudo apt upgrade -y sudo apt install git -y git clone [https://github.com/wifiphisher/wifiphisher.git](https://github.com/wifiphisher/wifiphisher.git) cd wifiphisher sudo python3 setup.py install |
| --- |

- Máy nạn nhân (Windows XP) đã kết nối vào mạng “LAB WIFI” từ trước được thể hiện ở hình bên dưới.

### Quy trình thực nghiệm

- Khởi động dự án Wifiphisher trên máy Attacker

Trên máy Kali, di chuyển vào thư mục mã nguồn và khởi chạy công cụ với card mạng wlan0, sử dụng kịch bản tấn công “firmware-upgrade”:

| cd ~/wifiphisher sudo ./venv/bin/python3 bin/wifiphisher -i wlan0 -p firmware-upgrade |
| --- |

- Dò quét (recon) các mạng Wi-Fi trong phạm vi

Sau khi khởi chạy, công cụ tự động chuyển card mạng sang chế độ Monitor và liệt kê toàn bộ các access point dò được, kèm theo ESSID, BSSID, kênh (CH), cường độ tín hiệu (PWR), kiểu mã hoá (ENCR) và số thiết bị đang kết nối. Mục tiêu “LAB WIFI” được chọn làm AP cần tấn công do đang ở trạng thái mạng mở (OPEN), không có cơ chế mã hoá.

- Tạo Access Point giả và phát động tấn công Deauthentication

Sau khi chọn mục tiêu, Wifiphisher tiến hành:

- Dựng một access point giả (Fake AP) phát cùng SSID và kênh với “LAB WIFI” thật.

- Liên tục gửi các gói tin Deauthentication/Disassociation (DEAUTH/DISAS) tới các địa chỉ MAC của AP thật và các thiết bị client đang kết nối, buộc các thiết bị này bị ngắt kết nối.

- Khởi chạy máy chủ HTTP nội bộ để phục vụ trang captive-portal giả mạo khi nạn nhân kết nối trở lại.

- Giao diện điều khiển hiển thị theo thời gian thực: danh sách các gói Deauth đã gửi, kênh và tên giao diện AP đang sử dụng.

- Máy nạn nhân bị ngắt kết nối và tự động chuyển sang AP giả

Do bị dồn dập deauth khỏi AP thật, thiết bị nạn nhân mất kết nối và tự động dò tìm lại mạng đã lưu có cùng tên “LAB WIFI”. Vì tín hiệu AP giả do máy Attacker phát ra thường mạnh hơn (ở cự ly gần) và không yêu cầu mật khẩu, thiết bị nạn nhân kết nối nhầm vào AP giả này mà người dùng không hề nhận biết được sự khác biệt, do SSID hiển thị hoàn toàn giống AP thật.

Trên máy Attacker, khi phát hiện có thiết bị kết nối vào AP giả, Wifiphisher sẽ ngừng gửi gói Deauth tới thiết bị đó và hiển thị thiết bị này trong danh sách “Connected Victims” kèm địa chỉ IP được cấp phát.

- Nạn nhân bị điều hướng tới trang giả mạo và nhập thông tin

Khi máy nạn nhân (Windows XP) mở trình duyệt, mọi yêu cầu HTTP đều bị chặn và điều hướng (DNS/HTTP redirect) về trang captive-portal do Wifiphisher dựng sẵn theo kịch bản “firmware-upgrade”. Trang này giả danh thông báo “Cập nhật bảo mật quan trọng cho Windows XP”, yêu cầu người dùng nhập lại Tên mạng (SSID) và Mật khẩu mạng (WPA/WEP Key) với lý do “xác thực mạng” trước khi tải bản cập nhật.

Ngay khi nạn nhân nhấn “Kết nối & Cập nhật”, dữ liệu được gửi bằng phương thức POST về máy chủ HTTP cục bộ trên máy Attacker. Theo log ghi nhận ở Hình 6, Wifiphisher đã bắt được yêu cầu dạng:

| POST request from 10.0.0.38 with ssid=Free-WiFi-XP&password=6678676 |
| --- |

Như vậy, toàn bộ thông tin mạng mà nạn nhân tin tưởng nhập vào (được cho là để xác thực hệ thống) thực chất đã bị công cụ tấn công thu thập và hiển thị rõ ràng ở phía Attacker.

### Kết quả thực nghiệm

Qua thực nghiệm, nhóm ghi nhận công cụ Wifiphisher đã thực hiện thành công đầy đủ chuỗi tấn công Evil Twin kết hợp captive-portal phishing, cụ thể:

- Dò quét và xác định chính xác mục tiêu AP mở trong phạm vi.

- Ngắt kết nối nạn nhân khỏi AP thật bằng kỹ thuật Deauthentication - khai thác điểm yếu của chuẩn 802.11 khi không có bảo vệ khung quản lý (Management Frame Protection).

- Lừa thiết bị nạn nhân tự động kết nối vào AP giả cùng tên - khai thác cơ chế tự kết nối mạng đã lưu (auto-connect) vốn chỉ dựa vào SSID mà không xác thực AP thật hay giả.

- Thu thập thành công dữ liệu nhạy cảm (SSID/mật khẩu) do nạn nhân tự nguyện cung cấp thông qua một kịch bản tâm lý (giả danh cập nhật hệ điều hành) có tính thuyết phục cao.

Điểm mấu chốt khiến cuộc tấn công hiệu quả không nằm ở lỗ hổng kỹ thuật phức tạp, mà ở sự kết hợp giữa điểm yếu giao thức (deauth không xác thực) và yếu tố con người (người dùng không kiểm tra kỹ trang web trước khi nhập thông tin).

Bảng 3.5. Tổng hợp rủi ro và biện pháp phòng chống

| Rủi ro / hậu quả | Biện pháp phòng chống |
| --- | --- |
| Lộ mật khẩu Wi-Fi, thông tin đăng nhập do nạn nhân tự nhập vào trang giả mạo | Không nhập thông tin nhạy cảm vào các trang yêu cầu bất thường; kiểm tra kỹ địa chỉ URL trước khi nhập dữ liệu |
| Bị ngắt kết nối khỏi AP thật do tấn công Deauthentication | Sử dụng chuẩn 802.11w (Protected Management Frames) để chống giả mạo khung quản lý |
| Tự động kết nối vào AP giả mạo trùng tên (Evil Twin) do thiết bị ưu tiên mạng đã lưu | Tắt tính năng tự kết nối Wi-Fi đã lưu; dùng VPN khi dùng Wi-Fi công cộng; triển khai WIDS/WIPS để phát hiện AP giả mạo |
| Trang captive portal giả danh thông báo hệ thống đánh lừa người dùng | Đào tạo nhận thức an toàn thông tin cho người dùng; xác thực mạng bằng WPA2/WPA3 thay vì mạng mở |

## Kết luận

Thực nghiệm mô phỏng tập trung vào hai mục tiêu: kiểm chứng khả năng thực thi tấn công Deauthentication trên mạng 802.11 không có cơ chế bảo vệ khung tin quản lý và đánh giá hiệu quả của PMF trong việc ngăn chặn tấn công này. Kết quả thực nghiệm được tóm tắt theo các nội dung sau. 

Về khả năng thực thi tấn công, kết quả mô phỏng cho thấy thiết bị tấn công có thể gửi khung tin Deauthentication giả mạo đến thiết bị khách và buộc thiết bị này ngắt kết nối khỏi AP. Thiết bị khách chấp nhận khung tin giả mạo do không có cơ chế xác thực nguồn gốc đối với khung tin quản lý. Kết quả này khớp với phân tích lý thuyết về lỗ hổng trong thiết kế khung tin quản lý của chuẩn 802.11. 

Về hệ quả của tấn công, việc ngắt kết nối tạo ra hai kịch bản tấn công tiếp theo. Thứ nhất, quá trình thiết bị khách tự động kết nối lại cho phép bắt giữ gói tin bắt tay bốn bước, từ đó thực hiện dò mật khẩu ngoại tuyến. Thứ hai, trạng thái gián đoạn kết nối có thể bị lợi dụng để chuyển hướng thiết bị khách sang AP giả mạo (Evil Twin) hoặc triển khai tấn công xen giữa (MitM). Cả hai kịch bản đều đã được quan sát trong môi trường mô phỏng. 

Về hiệu quả phòng chống, khi kích hoạt PMF theo tiêu chuẩn IEEE 802.11w, các khung tin quản lý được bảo vệ bằng mã toàn vẹn thông điệp (MIC). Kết quả mô phỏng cho thấy khung tin Deauthentication giả mạo bị thiết bị khách từ chối, do đó tấn công không thành công. Ngoài ra, hệ thống WIDS/WIPS ghi nhận các hành vi bất thường trên mạng không dây, hỗ trợ phát hiện tấn công. 

Kết quả thực nghiệm phù hợp với các phân tích lý thuyết đã trình bày trong Chương 2. Hạn chế của thực nghiệm là phạm vi mô phỏng còn hẹp và chưa đánh giá đầy đủ ảnh hưởng của các yếu tố môi trường thực tế đến hiệu quả của tấn công và các biện pháp phòng chống.

# TỔNG KẾT

Báo cáo đã hệ thống hóa các vấn đề lý thuyết về mạng không dây theo chuẩn IEEE 802.11, bao gồm kiến trúc, nguyên lý hoạt động và các kiểu tấn công phổ biến. Trọng tâm của phần lý thuyết là phân tích lỗ hổng trong thiết kế khung tin quản lý của chuẩn 802.11, trong đó các khung tin này không được xác thực nguồn gốc và không được mã hóa ở các phiên bản chuẩn ban đầu. Đây là cơ sở để lý giải vì sao tấn công Deauthentication có thể được thực thi mà không cần quyền truy cập vật lý vào mạng.

Về cơ chế tấn công, báo cáo đã làm rõ kỹ thuật giả mạo địa chỉ MAC và phân tích gói tin, cùng các hình thức thực thi Deauthentication (cơ bản, quảng bá, có chủ đích). Báo cáo cũng xác định vai trò của Deauthentication như một bước đệm trong các kịch bản tấn công phức hợp, bao gồm tấn công dò mật khẩu thông qua bắt giữ gói tin bắt tay bốn bước (Handshake Capture) và tấn công Evil Twin hoặc Man-in-the-Middle.

Về phòng chống, báo cáo đã khảo sát ba nhóm giải pháp chính: tiêu chuẩn IEEE 802.11w (Protected Management Frames), hệ thống WIDS/WIPS và các biện pháp cấu hình vận hành. Các giải pháp được đánh giá dựa trên khả năng ngăn chặn, phát hiện và giảm thiểu rủi ro từ tấn công Deauthentication. Kết quả thực nghiệm mô phỏng xác nhận tính khả thi của tấn công trong điều kiện không có PMF, đồng thời kiểm chứng hiệu quả của PMF trong việc ngăn chặn khung tin giả mạo.

Các kết quả nghiên cứu có thể được sử dụng làm tài liệu tham khảo cho quản trị viên mạng trong thiết kế và vận hành hệ thống mạng không dây, đồng thời làm cơ sở cho các nghiên cứu tiếp theo về bảo mật mạng không dây. Hạn chế của báo cáo là phạm vi thực nghiệm mô phỏng còn hẹp và chưa đánh giá đầy đủ ảnh hưởng của các yếu tố môi trường thực tế đến hiệu quả của tấn công và các biện pháp phòng chống.

# TÀI LIỆU THAM KHẢO

| [1] | DataReportal, "Digital 2026: Vietnam," DataReportal, 2025. |
| --- | --- |
| [2] | Q&Me, "Vietnam Mobile App Usage Trends 2026," Q&Me, 2026. |
| [3] | J. Bellardo and S. Savage, "802.11 Denial-of-Service Attacks: Real Vulnerabilities and Practical Solutions," USENIX Association, Washington, D.C., 2003. |
| [4] | I. Martinovic, F. A. Zdarsky and J. B. Schmitt, "On the Way to IEEE 802.11 DoS Resilience," University of Kaiserslautern, Kaiserslautern, Germany, 2006. |
| [5] | R. Hešík, "Impact of Denial of Service Attacks on the Public Wi-Fi Networks," VŠB – Technical University of Ostrava, Ostrava, 2013. |
| [6] | A. G. Gaikwad and B. Patil, "Securing the Airwaves: A Survey on De-authentication Attacks and Mitigation Strategies," *International Journal of Computing and Digital Systems, *vol. 16, no. 1, pp. 1307-1316, 2024. |
| [7] | R. Hešík, "Impact of Denial of Service Attacks on the Public Wi-Fi Networks," VŠB – Technical University of Ostrava, Ostrava, 2013. |

2

2

2
