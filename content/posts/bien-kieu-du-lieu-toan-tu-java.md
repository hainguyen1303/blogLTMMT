---
title: "Biến, kiểu dữ liệu và toán tử trong Java"
date: 2025-10-16
draft: false
tags: ["Java", "Lập trình"]
categories: ["Lập trình"]
description: "Tìm hiểu cách khai báo biến, lựa chọn kiểu dữ liệu và sử dụng toán tử cơ bản trong Java."
image: "/images/posts/bien-kieu-du-lieu-toan-tu-java.jpg"
---

Khi mới chạm vào Java, nhiều bạn dễ bị choáng ngợp bởi số lượng khái niệm cần ghi nhớ. Tuy nhiên, nếu hiểu rõ biến, kiểu dữ liệu và toán tử, bạn sẽ nắm được “ngữ pháp” cốt lõi để diễn đạt mọi ý tưởng. Bài viết này giúp bạn có cái nhìn hệ thống, đi kèm ví dụ thực tế để thực hành ngay.

## Biến trong Java là gì?

Biến (variable) giống như chiếc hộp để lưu trữ thông tin tạm thời trong bộ nhớ. Mỗi biến có tên, kiểu dữ liệu và giá trị. Java là ngôn ngữ kiểu tĩnh, nghĩa là bạn phải khai báo kiểu dữ liệu ngay khi tạo biến, giúp chương trình an toàn và dễ kiểm soát hơn.

### Quy tắc đặt tên biến

- Sử dụng chữ cái, số, ký tự gạch dưới hoặc `$`, nhưng không bắt đầu bằng số.  
- Dùng phong cách `camelCase`, ví dụ `soSinhVien`, `tenSanPham`.  
- Tránh trùng với từ khóa (`class`, `int`, `switch`, ...).

## Kiểu dữ liệu cơ bản

Java cung cấp 8 kiểu nguyên thủy và nhiều kiểu tham chiếu:

- **Nguyên thủy**: `byte`, `short`, `int`, `long`, `float`, `double`, `char`, `boolean`.  
- **Tham chiếu**: `String`, `BigDecimal`, `LocalDate`, hoặc bất kỳ lớp do bạn tự tạo.  
- **Mảng và Collection**: dùng khi cần lưu trữ nhiều giá trị cùng kiểu.

### Lựa chọn kiểu dữ liệu

- Số nguyên nhỏ dùng `int`, số lớn dùng `long`.  
- Số thực đơn giản dùng `double`, tính toán tài chính nên chọn `BigDecimal`.  
- Dữ liệu dạng văn bản dùng `String`.  
- Đúng/Sai dùng `boolean`.  

## Toán tử trong Java

Toán tử cho phép bạn thao tác trên biến và giá trị. Có bốn nhóm chính:

1. **Toán tử số học**: `+`, `-`, `*`, `/`, `%`.  
2. **Toán tử gán**: `=`, `+=`, `-=`, `*=`, `/=`.  
3. **Toán tử so sánh**: `==`, `!=`, `>`, `<`, `>=`, `<=`.  
4. **Toán tử logic**: `&&`, `||`, `!` dùng trong điều kiện.

### Ví dụ minh họa

```java
public class BienVaToanTu {
    public static void main(String[] args) {
        int soHocVien = 20;
        double diemTrungBinh = 8.35;
        boolean daTotNghiep = diemTrungBinh >= 5.0;

        System.out.println("Số học viên: " + soHocVien);
        System.out.println("Điểm trung bình: " + diemTrungBinh);
        System.out.println("Đã tốt nghiệp? " + daTotNghiep);

        soHocVien += 5; // tăng sĩ số
        double tongDiem = diemTrungBinh * soHocVien;
        System.out.println("Tổng điểm của lớp: " + tongDiem);
    }
}
```

Đoạn code cho thấy cách kết hợp biến với toán tử gán, toán tử số học và toán tử so sánh để suy luận trạng thái. Khi chạy chương trình, bạn sẽ thấy số học viên được cập nhật và điều kiện tốt nghiệp được kiểm tra ngay lập tức.

## Lời khuyên thực hành

Hãy luyện tập bằng cách giải các bài toán nhỏ:

- Viết chương trình tính chỉ số BMI.  
- Tạo ứng dụng hỏi đáp trắc nghiệm, sử dụng `boolean` để lưu đáp án đúng.  
- Viết bộ chuyển đổi nhiệt độ từ Celsius sang Fahrenheit.  

Qua từng bài tập, bạn sẽ quen tay và hiểu rõ hơn cách Java xử lý dữ liệu. Khi nền tảng đã vững, những chủ đề tiếp theo như cấu trúc điều khiển hay lập trình hướng đối tượng sẽ trở nên dễ tiếp thu hơn rất nhiều.
