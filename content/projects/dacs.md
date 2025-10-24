---
title: "Triển khai hệ thống mạng với Sophos Firewall"
date: 2025-03-10
summary: 
---

## Giới thiệu

Đồ án **“Triển khai hệ thống mạng với Sophos Firewall”** được thực hiện trong khuôn khổ học phần **Đồ án Cơ Sở** của chuyên ngành **Mạng Máy Tính – K22, Trường Đại học Công Nghệ TP.HCM (HUTECH)**.  
Thời gian thực hiện: **10/03 – 25/05/2025**  
Giảng viên hướng dẫn: **ThS. Nguyễn Văn Cẩn**  
Kết quả: **Top 1 nhóm chuyên ngành (8.5/10)**

Mục tiêu của đồ án là xây dựng một hệ thống mạng mô phỏng doanh nghiệp nhỏ, có khả năng **bảo mật, quản lý lưu lượng và truy cập từ xa an toàn** dựa trên giải pháp **Sophos UTM 9.7**.

---

## 1. Môi trường và mô hình thực nghiệm

### 1.1 Môi trường thực nghiệm
Môi trường triển khai bao gồm:

- 01 laptop chạy **Windows 11**, sử dụng làm **WebAdmin Sophos UTM 9.7**.  
- 01 máy ảo chạy file ISO `asg-9.720-5.1.iso` để cài đặt **Sophos UTM 9.7**.  
- 01 máy ảo **Windows Server 2019** làm **Domain Controller** và máy kiểm thử.  

**Phần mềm sử dụng:**  
`VMware Workstation Pro 17.5`, `Sophos Firewall UTM 9.7`.

### 1.2 Các kịch bản thử nghiệm
1. **Kịch bản 1:** Kiểm tra khả năng lọc web.  
2. **Kịch bản 2:** Thử nghiệm DNAT RDP.  
3. **Kịch bản 3:** Thử nghiệm Remote Access VPN.

---

## 2. Quy trình triển khai

### 2.1 Cài đặt Sophos Firewall trên VMware

1. **Cài đặt VMware Workstation Pro 17.5**  
   Truy cập trang chủ VMware: [https://www.vmware.com/](https://www.vmware.com/) để tải và cài đặt.  

<div align="center">
  <img src="/images/dacs/hinh1.png" alt="Hình 3.1: Cài đặt VMware Workstation Pro" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.1: Cài đặt VMware Workstation Pro</i></p>
</div>

2. **Tải ISO Sophos UTM**  
   Tải file ISO từ trang chủ Sophos tại:  
   [https://download.sophos.com/network/utm/installers/hardware/ssi-9.719-3.1.iso](https://download.sophos.com/network/utm/installers/hardware/ssi-9.719-3.1.iso)  

<div align="center">
  <img src="/images/dacs/hinh2.png" alt="Hình 3.2: Link tải file ISO của Sophos UTM" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.2: Link tải file ISO của Sophos UTM</i></p>
</div>

3. **Tạo máy ảo mới trong VMware và mount ISO**  

<div align="center">
  <img src="/images/dacs/hinh3.png" alt="Hình 3.3: Khởi tạo máy ảo Sophos UTM qua file ISO" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.3: Khởi tạo máy ảo Sophos UTM qua file ISO</i></p>
</div>

4. **Cấu hình máy ảo (RAM, CPU, card mạng, ổ đĩa ảo)**  

<div align="center">
  <img src="/images/dacs/hinh4.png" alt="Hình 3.4: Cấu hình thiết bị cơ bản cho máy ảo Sophos UTM" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.4: Cấu hình thiết bị cơ bản cho máy ảo Sophos UTM</i></p>
</div>

5. **Khởi động và cài đặt Sophos UTM 9.7**  

<div align="center">
  <img src="/images/dacs/hinh5.png" alt="Hình 3.5: Khởi chạy máy ảo trên VMware Workstation" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.5: Khởi chạy máy ảo trên VMware Workstation</i></p>
</div>

6. **Chọn interface cho WebAdmin (eth0 – NAT)**  

<div align="center">
  <img src="/images/dacs/hinh6.png" alt="Hình 3.6: Chọn cổng interface cho WebAdmin" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.6: Chọn cổng interface cho WebAdmin</i></p>
</div>

7. **Thiết lập địa chỉ IP và Subnet mask**  
   `192.168.137.253 / 255.255.255.0`  

<div align="center">
  <img src="/images/dacs/hinh7.png" alt="Hình 3.7: Thiết lập Network Configuration cho WebAdmin" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.7: Thiết lập Network Configuration cho WebAdmin</i></p>
</div>

8. **Cài đặt Kernel Support và Enterprise Toolkit**  

<div align="center">
  <img src="/images/dacs/hinh8.png" alt="Hình 3.8: Cài đặt 64-bit Kernel Support và Enterprise Toolkit" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.8: Cài đặt 64-bit Kernel Support và Enterprise Toolkit</i></p>
</div>

9. **Khởi động lại máy ảo**  

<div align="center">
  <img src="/images/dacs/hinh9.png" alt="Hình 3.9: Khởi động lại Sophos UTM trên VMware Workstation" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.9: Khởi động lại Sophos UTM trên VMware Workstation</i></p>
</div>

10. **Truy cập WebAdmin tại** `https://192.168.137.253:4444/`  

<div align="center">
  <img src="/images/dacs/hinh10.png" alt="Hình 3.10: Màn hình đăng nhập Sophos UTM trên Portal" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.10: Màn hình đăng nhập Sophos UTM trên Portal</i></p>
</div>

11. **Đăng nhập vào WebAdmin và kiểm tra giao diện chính**  

<div align="center">
  <img src="/images/dacs/hinh11.png" alt="Hình 3.11: Giao diện chính của Sophos UTM" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.11: Giao diện chính của Sophos UTM</i></p>
</div>

---

### 2.2 Mô tả sơ đồ mạng

<div align="center">
  <img src="/images/dacs/hinh12.png" alt="Hình 3.12: Sơ đồ mạng thực nghiệm" style="width:75%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.12: Sơ đồ mạng thực nghiệm</i></p>
</div>

**Cấu hình mạng:**
- **Sophos UTM:**
  - `eth0 (Management)` – NAT (IP: `192.168.137.253`)
  - `eth1 (INSIDE)` – LAN nội bộ (IP: `192.168.10.254`)
  - `eth2 (External)` – Bridged, kết nối Internet.
- **Windows Server 2019:**
  - Kết nối vào mạng `INSIDE (192.168.10.10/24)`
  - Cấu hình Domain Controller với 3 tài khoản: `Administrator`, `User01`, `User02`.

---

### 2.3 Luồng kết nối chính
- WebAdmin được truy cập từ mạng NAT (192.168.137.253).  
- UTM định tuyến giữa mạng **INSIDE (LAN)** và **External (WAN)**.  
- Windows Server kết nối Internet qua UTM.  
- Các máy nội bộ dùng `192.168.10.254` làm **gateway** ra ngoài.

---

### 2.4 Cấu hình trên WebAdmin

**Interfaces**  

<div align="center">
  <img src="/images/dacs/hinh13.png" alt="Hình 3.13: Các interface trên WebAdmin" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.13: Các interface trên WebAdmin</i></p>
</div>

**DHCP Server**  

<div align="center">
  <img src="/images/dacs/hinh14.png" alt="Hình 3.14: Thiết lập DHCP cho INSIDE và Management" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.14: Thiết lập DHCP cho INSIDE và Management</i></p>
</div>

**Firewall Rules**  
- `192.168.10.0 → Any` : INSIDE ra Internet.  
- `192.168.10.0 → 192.168.10.0` : LAN nội bộ kết nối nội bộ.  

<div align="center">
  <img src="/images/dacs/hinh15.png" alt="Hình 3.15: Firewall Rules" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.15: Firewall Rules</i></p>
</div>

**NAT Configuration**  

<div align="center">
  <img src="/images/dacs/hinh16.png" alt="Hình 3.16: NAT Rules – Phân luồng lưu lượng" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.16: NAT Rules – Phân luồng lưu lượng</i></p>
</div>

---

## 3. Cấu hình tính năng nâng cao

### 3.1 Web Filtering

<div align="center">
  <img src="/images/dacs/hinh17.png" alt="Hình 3.17: Cấu hình Web Filtering" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.17: Cấu hình Web Filtering</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh18.png" alt="Hình 3.18: Một vài Filter Actions" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.18: Một vài Filter Actions</i></p>
</div>

### 3.2 Remote Access VPN

<div align="center">
  <img src="/images/dacs/hinh19.png" alt="Hình 3.19: Cấu hình SSL VPN" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.19: Cấu hình SSL VPN</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh20.png" alt="Hình 3.20: Thiết lập Virtual IP Pool" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.20: Thiết lập Virtual IP Pool</i></p>
</div>

### 3.3 NAT – DNAT

<div align="center">
  <img src="/images/dacs/hinh21.png" alt="Hình 3.21: DNAT Rule cho RDP" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.21: DNAT Rule cho RDP</i></p>
</div>
---

## 4. Kiểm thử và đánh giá

### 4.1 Phương pháp kiểm thử

<div align="center">
  <img src="/images/dacs/hinh22.png" alt="Hình 3.22: Ping thử từ máy nội bộ đến Sophos UTM" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.22: Ping thử từ máy nội bộ đến Sophos UTM</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh23.png" alt="Hình 3.23: Truy cập internet từ máy nội bộ" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.23: Truy cập internet từ máy nội bộ</i></p>
</div>

### 4.2 Kết quả kiểm thử

<div align="center">
  <img src="/images/dacs/hinh24.png" alt="Hình 3.24: Trước khi bật Web Filtering" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.24: Trước khi bật Web Filtering</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh25.png" alt="Hình 3.25: Sau khi bật Web Filtering" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.25: Sau khi bật Web Filtering</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh26.png" alt="Hình 3.26: Pool Network VPN" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.26: Pool Network VPN</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh27.png" alt="Hình 3.27: Tạo user VPN vpn_user2" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.27: Tạo user VPN vpn_user2</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh28.png" alt="Hình 3.28: Kích hoạt user portal" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.28: Kích hoạt user portal</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh29.png" alt="Hình 3.29: Giao diện portal người dùng Sophos" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.29: Giao diện portal người dùng Sophos</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh30.png" alt="Hình 3.30: Download Sophos Connect client" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.30: Download Sophos Connect client</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh31.png" alt="Hình 3.31: Download file vpn_user2@192.168.137.253.ovpn" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.31: Download file vpn_user2@192.168.137.253.ovpn</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh32.png" alt="Hình 3.32: Kết nối thành công qua Sophos Connect" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.32: Kết nối thành công qua Sophos Connect</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh33.png" alt="Hình 3.33: Kiểm tra kết nối VPN thành công" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.33: Kiểm tra kết nối VPN thành công</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh34.png" alt="Hình 3.34: NAT rule cho phép RDP" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.34: NAT rule cho phép RDP</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh35.png" alt="Hình 3.35: NAT External → AD Server RDP" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.35: NAT External → AD Server RDP</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh36.png" alt="Hình 3.36: Remote Desktop Connection" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.36: Remote Desktop Connection</i></p>
</div>

<div align="center">
  <img src="/images/dacs/hinh37.png" alt="Hình 3.37: Join thành công vào máy nội bộ" style="width:70%; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15);">
  <p><i>Hình 3.37: Join thành công vào máy nội bộ</i></p>
</div>

---

## 5. Đánh giá tổng quan

Sau khi triển khai, **Sophos UTM 9.7** thể hiện hiệu quả rõ rệt trong việc:
- Lọc web thông minh và an toàn.  
- Cung cấp VPN truy cập từ xa bảo mật.  
- Phân luồng NAT, firewall rõ ràng, đảm bảo tính toàn vẹn mạng.  

Giao diện WebAdmin trực quan, cấu hình dễ dàng.  
Hạn chế nhỏ: độ trễ nhẹ khi dùng VPN, cần tinh chỉnh rule để tối ưu hiệu suất.

---

## 6. Kết luận

Dự án chứng minh rằng **Sophos UTM 9.7** là giải pháp tường lửa phù hợp cho doanh nghiệp vừa và nhỏ – cung cấp **bảo mật, quản lý và khả năng mở rộng tốt**.  

---

<div align="center" style="margin-top:40px;">
  <a href="/about" style="text-decoration:none; background:#007bff; color:white; padding:10px 18px; border-radius:8px; font-weight:500; box-shadow:0 2px 5px rgba(0,0,0,0.2);">
    ⬅ Quay lại Trang giới thiệu
  </a>
</div>
