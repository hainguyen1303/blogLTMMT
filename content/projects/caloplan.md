---
title: "Calo Plan – Ứng dụng quản lý dinh dưỡng và theo dõi sức khỏe cá nhân"
date: 2025-07-31
summary: 
---

## Thông tin nhóm thực hiện

**Tên đề tài:** Ứng dụng Quản lý Dinh dưỡng – *Calo Plan*  
**Lớp học phần:** Lập trình thiết bị di động  

**Thành viên nhóm:**
1. **Nguyễn Văn Hải**  
2. **Triệu Xuân Dũng**  
3. **Vũ Nguyễn Khánh Dương**  
4. **Tiết Thanh Minh Hiếu** – Leader  

---

## Giới thiệu

Trong bối cảnh con người ngày càng quan tâm đến **dinh dưỡng và sức khỏe**, việc kiểm soát lượng **calo nạp vào và tiêu thụ mỗi ngày** trở nên vô cùng quan trọng.  
Đồ án **“Ứng dụng Quản lý Dinh dưỡng – Calo Plan”** được phát triển nhằm hỗ trợ người dùng **theo dõi thói quen ăn uống, kiểm soát cân nặng, và duy trì lối sống lành mạnh** thông qua nền tảng di động trực quan và dễ sử dụng.

---

## 1. Mục tiêu đề tài

Ứng dụng **Calo Plan** được thiết kế với mục tiêu:

- Hỗ trợ người dùng **quản lý khẩu phần ăn và lượng calo** hàng ngày.  
- Cung cấp các chỉ số **BMI, BMR** và lượng **calo cần nạp/ngày** dựa trên thông tin cá nhân.  
- Gợi ý món ăn phù hợp với **mục tiêu dinh dưỡng cá nhân** (giảm cân, tăng cân, duy trì).  
- Cung cấp **thống kê và biểu đồ** trực quan giúp người dùng dễ dàng theo dõi tiến trình sức khỏe.  

---

## 2. Đối tượng và phạm vi ứng dụng

- **Đối tượng sử dụng:**  
  Người dùng cá nhân, đặc biệt là sinh viên, người tập thể hình hoặc người đang muốn kiểm soát cân nặng.

- **Phạm vi:**  
  Ứng dụng được phát triển trên nền tảng **Flutter (cross-platform)**, có thể chạy trên **Android** và **iOS**.  
  Dữ liệu được lưu trữ và đồng bộ thông qua **Firebase Realtime Database**.

---

## 3. Kiến trúc và công nghệ sử dụng

| Thành phần | Công nghệ sử dụng |
|-------------|------------------|
| Giao diện người dùng | Flutter, Dart |
| Cơ sở dữ liệu | Firebase Realtime Database |
| Xác thực người dùng | Firebase Authentication |
| Lưu trữ hình ảnh | Firebase Storage |
| Phân tích dữ liệu | Chart.js / Flutter Charts |
| Thiết kế UI | Material 3 & Cupertino Style |


---

## 4. Chức năng chính

### 🏠 Màn hình Trang chủ
Hiển thị tổng quan tình trạng trong ngày:
- Lượng **calo nạp / mục tiêu** (`2244 / 2326 kcal`)  
- Các **chỉ số dinh dưỡng chính** (Protein, Carbs, Fat)  
- Lượng **nước đã uống** và công cụ điều chỉnh nhanh.  
- Nút **“+ Thêm món”** để thêm món ăn nhanh chóng.

<div align="center">
  <img src="/images/caloplan/home.jpg" alt="Màn hình chính Calo Plan – Theo dõi lượng calo và macros"
       style="width:45%; min-width:280px; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15); margin:10px 0;">
  <p><i>Hình 1: Giao diện chính – Theo dõi năng lượng và dinh dưỡng trong ngày</i></p>
</div>

---

### 🍽️ Danh sách món ăn
- Gồm hàng trăm món ăn phổ biến (ví dụ: **Bánh cuốn, Chuối, Cơm trắng…**)  
- Thông tin **kcal/100g** được hiển thị rõ ràng.  
- Người dùng có thể **đánh dấu yêu thích** hoặc **tạo món cá nhân**.  
- Tính năng **tìm kiếm nhanh** giúp thao tác mượt mà.

<div align="center">
  <img src="/images/caloplan/foods.jpg" alt="Danh sách món ăn Calo Plan"
       style="width:45%; min-width:280px; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15); margin:10px 0;">
  <p><i>Hình 2: Giao diện danh sách món ăn – chi tiết năng lượng và thông tin dinh dưỡng</i></p>
</div>

---

### 📊 Thống kê và phân tích
- Biểu đồ trực quan thể hiện:
  - **Thống kê calo nạp theo ngày**
  - **Biểu đồ cân nặng theo thời gian**
  - **Tỷ lệ dinh dưỡng (Protein, Carbs, Fat)**
  - **Món ăn được dùng nhiều nhất**

<div align="center">
  <img src="/images/caloplan/statistics.jpg" alt="Biểu đồ thống kê sức khỏe trong Calo Plan"
       style="width:45%; min-width:280px; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15); margin:10px 0;">
  <p><i>Hình 3: Thống kê tổng hợp về năng lượng và tỷ lệ dinh dưỡng</i></p>
</div>

---

### 👤 Hồ sơ cá nhân
Người dùng có thể nhập và theo dõi thông tin thể trạng:

- **Tên:** Nguyễn Văn Hải  
- **Chiều cao:** 180 cm  
- **Cân nặng:** 59 kg  
- **BMI:** 18.2 (*Gầy*)  
- **BMR:** 1615 kcal  
- **Calo cần nạp/ngày:** 2326 kcal  

Ứng dụng tự động tính toán chỉ số **BMI** và **BMR**, đồng thời đưa ra lượng calo khuyến nghị phù hợp.

<div align="center">
  <img src="/images/caloplan/profile.jpg" alt="Hồ sơ cá nhân trong Calo Plan"
       style="width:45%; min-width:280px; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.15); margin:10px 0;">
  <p><i>Hình 4: Hồ sơ cá nhân – chỉ số BMI, BMR và lượng calo cần thiết</i></p>
</div>

---

## 5. Giao diện tổng thể

Bố cục ứng dụng được chia thành 4 tab chính:

| Tab | Chức năng |
|------|------------|
| **Trang chủ** | Hiển thị tổng quan calo và nước uống |
| **Món ăn** | Quản lý và thêm món ăn |
| **Thống kê** | Biểu đồ theo dõi tiến trình |
| **Cá nhân** | Cập nhật thông tin và chỉ số cơ thể |

Giao diện được thiết kế theo phong cách **Material Design**, màu sắc dịu nhẹ, phù hợp với thị giác và trải nghiệm người dùng hiện đại.

---

## 6. Kết quả và đánh giá

**Kết quả đạt được:**
- Hoàn thiện ứng dụng cơ bản gồm các chức năng chính.  
- Giao diện thân thiện, dễ thao tác, tương thích đa nền tảng.  
- Dữ liệu đồng bộ ổn định với Firebase.  

**Hạn chế:**
- Chưa tích hợp API tự động tra cứu món ăn từ bên ngoài.  
- Còn thiếu tính năng theo dõi hoạt động thể chất (calo tiêu thụ).  

**Hướng phát triển:**
- Bổ sung tính năng **AI gợi ý thực đơn thông minh**.  
- Hỗ trợ **đồng bộ thiết bị đeo tay / smartwatch**.  
- Cho phép **chia sẻ tiến trình và mục tiêu với bạn bè**.

---

## 7. Kết luận

Ứng dụng **Calo Plan** là một bước tiến nhỏ nhưng đầy tiềm năng trong việc **ứng dụng công nghệ vào quản lý dinh dưỡng và sức khỏe cá nhân**.  
Sản phẩm không chỉ giúp người dùng **nhận thức rõ hơn về thói quen ăn uống**, mà còn hướng tới **lối sống cân bằng, khoa học và bền vững**.

> 💬 “Sức khỏe không đến từ may mắn, mà từ thói quen mỗi ngày.” – *Calo Plan Team*

---

<div align="center" style="margin-top:40px;">
  <a href="/about" style="text-decoration:none; background:#007bff; color:white; padding:10px 18px; border-radius:8px; font-weight:500; box-shadow:0 2px 5px rgba(0,0,0,0.2);">
    ⬅ Quay lại Trang giới thiệu
  </a>
</div>
