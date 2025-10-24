---
title: "Triển khai hệ thống Sophos Firewall trong hạ tầng mạng"
date: 2025-09-29
summary: "Đồ án Chuyên Ngành – Xây dựng và triển khai hệ thống bảo mật mạng doanh nghiệp sử dụng Sophos XG Firewall"
---

## Giới thiệu

Đồ án **“Triển khai hệ thống Sophos Firewall trong hạ tầng mạng”** được thực hiện trong khuôn khổ học phần **Đồ án Chuyên Ngành** của chuyên ngành **Mạng Máy Tính – K22, Trường Đại học Công Nghệ TP.HCM (HUTECH)**.  
Thời gian thực hiện: **29/09 – 07/12/2025**  
Giảng viên hướng dẫn: **ThS. Nguyễn Văn Cẩn**

---

## 1. Mục tiêu đồ án

Mục tiêu của đồ án là **xây dựng một hệ thống mạng doanh nghiệp hoàn chỉnh** với mô hình triển khai **Sophos XG Firewall** nhằm:
- Quản lý và phân tách các VLAN nội bộ (phòng ban khác nhau).  
- Thiết lập các **chính sách Firewall, NAT, Web Filtering** và **VPN Site-to-Site**.  
- Đảm bảo **bảo mật, hiệu suất và khả năng mở rộng** trong môi trường mạng mô phỏng.  
- Kết hợp nhiều công cụ hỗ trợ để mô phỏng, giám sát và quản trị toàn bộ hệ thống.

---

## 2. Công cụ và phần mềm sử dụng

| Công cụ | Mục đích sử dụng |
|----------|------------------|
| **EVE-NG Community** | Mô phỏng toàn bộ hệ thống mạng, bao gồm router, switch và firewall |
| **Sophos XG Firewall (ISO)** | Thiết lập tường lửa trung tâm, quản lý chính sách bảo mật |
| **VMware Workstation Pro 17.5** | Chạy các máy ảo Windows, Server và Sophos Firewall |
| **MobaXterm** | SSH / Telnet để truy cập và cấu hình router, switch, firewall |
| **FileZilla** | Truyền file cấu hình và file log giữa các thiết bị ảo |
| **UltraVNC** | Điều khiển máy ảo và giao diện WebAdmin từ xa |

---

## 3. Mô hình mạng dự kiến

<div class="figure" align="center">
  <img src="/images/dacn/mohinh.jpg" alt="Sơ đồ mạng đồ án chuyên ngành Sophos XG trên EVE-NG">
  <p><i>Hình 1: Mô hình mạng doanh nghiệp mô phỏng sử dụng Sophos XG trên EVE-NG</i></p>
</div>

### Cấu trúc tổng quan

Hệ thống được triển khai mô phỏng trên **EVE-NG**, với thành phần chính:

- **Sophos XG Firewall**: Đóng vai trò tường lửa trung tâm, kết nối các vùng mạng (DMZ, LAN, Server, WAN).  
- **Router R13, R18, R16**: Mô phỏng tuyến kết nối liên vùng và WAN.  
- **Switch Layer 2 (R7, R8)**: Phân phối lưu lượng nội bộ và VLAN giữa các nhóm người dùng.  
- **Windows Server**: Cung cấp dịch vụ **AD, DNS và DHCP** cho mạng nội bộ.  
- **Các máy trạm (Win)**: Mô phỏng người dùng ở từng VLAN, truy cập qua Firewall và được áp chính sách kiểm soát.

---

## 4. Phân hoạch mạng dự kiến

| Vùng mạng | Mô tả | IP dự kiến | Ghi chú |
|------------|--------|------------|---------|
| **WAN** | Kết nối Internet ảo qua router R13/R18 | 203.0.113.0/30 | Giao tiếp ra ngoài |
| **LAN nội bộ** | Người dùng nội bộ (HR, IT, ADMIN) | 192.168.10.0/24 | Quản lý & truy cập nội bộ |
| **DMZ** | Khu vực máy chủ (AD, DNS, Web) | 192.168.20.0/24 | Cung cấp dịch vụ nội bộ |
| **VPN Site-to-Site** | Kết nối chi nhánh qua IPsec | 10.10.10.0/24 | Bảo mật và định tuyến VPN |

---

## 5. Kế hoạch thực hiện

| Giai đoạn | Nội dung công việc | Thời gian dự kiến |
|------------|--------------------|-------------------|
| 1 | Xây dựng mô hình trên EVE-NG, kiểm tra kết nối | 29/09 – 10/10 |
| 2 | Cài đặt Sophos XG và cấu hình IP cơ bản | 11/10 – 20/10 |
| 3 | Thiết lập chính sách Firewall, NAT, VLAN | 21/10 – 05/11 |
| 4 | Cấu hình VPN Site-to-Site và Web Filtering | 06/11 – 20/11 |
| 5 | Kiểm thử và hoàn thiện báo cáo | 21/11 – 07/12 |

---

## 6. Tiến độ hiện tại

- Đã hoàn tất **mô hình mô phỏng EVE-NG** với đầy đủ router, switch và firewall.  
- Đang trong giai đoạn **cấu hình cơ bản Sophos XG Firewall** và kiểm tra kết nối VLAN.  
- Chuẩn bị triển khai **VPN Site-to-Site** và thử nghiệm lọc web nâng cao.  

---

## 7. Hình ảnh minh chứng (đang cập nhật)

---

## 8. Kỳ vọng kết quả

Sau khi hoàn thiện, hệ thống sẽ đạt được:
- Quản lý và bảo mật hiệu quả giữa các VLAN.  
- Cấu hình **NAT, Firewall, VPN, Web Filtering** hoạt động ổn định.  
- Mô phỏng hoạt động doanh nghiệp thực tế trên nền tảng ảo hóa.  
- Cung cấp báo cáo phân tích **hiệu suất, bảo mật và tính sẵn sàng** của hệ thống.

---

> 🧠 Ghi chú: Đồ án đang trong quá trình hoàn thiện,  
> phần báo cáo chi tiết và kết quả kiểm thử sẽ được cập nhật trong giai đoạn cuối (tháng 12/2025).

---

[⬅ Quay lại trang About](/about)
