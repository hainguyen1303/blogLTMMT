---
title: "Lập trình hướng đối tượng trong Java – Hiểu rõ Class và Object"
date: 2025-10-16
draft: false
tags: ["Java", "Lập trình"]
categories: ["Lập trình"]
description: "Tìm hiểu khái niệm class, object và bốn đặc tính hướng đối tượng quan trọng trong Java."
image: "/images/posts/lap-trinh-huong-doi-tuong-java.jpg"
---

Lập trình hướng đối tượng (OOP) là trái tim của Java. Nhờ mô hình này, chúng ta có thể mô tả thế giới thực một cách trực quan thông qua các lớp (class) và đối tượng (object). Trong bài viết này, tôi sẽ cùng bạn đi qua những khái niệm nền tảng, minh họa bằng code và chia sẻ một số kinh nghiệm giúp bạn áp dụng OOP hiệu quả khi xây dựng ứng dụng thực tế.

## Class và Object là gì?

- **Class**: Bản thiết kế mô tả thuộc tính và hành vi.  
- **Object**: Thể hiện cụ thể của class với giá trị riêng cho từng thuộc tính.  

Ví dụ, class `HocVien` miêu tả mọi học viên, còn object là từng bạn học viên cụ thể đang tham gia khóa học Java.

### Bốn đặc tính của OOP

1. **Đóng gói (Encapsulation)**: Bảo vệ dữ liệu bằng cách giới hạn quyền truy cập.  
2. **Kế thừa (Inheritance)**: Cho phép lớp con tái sử dụng và mở rộng lớp cha.  
3. **Đa hình (Polymorphism)**: Một hành vi có thể thể hiện khác nhau tùy ngữ cảnh.  
4. **Trừu tượng (Abstraction)**: Che giấu chi tiết phức tạp, chỉ lộ ra các chức năng quan trọng.

## Ví dụ thực hành

```java
class HocVien {
    private final String hoTen;
    private int soBuoiHoc;

    public HocVien(String hoTen) {
        this.hoTen = hoTen;
        this.soBuoiHoc = 0;
    }

    public void diemDanh() {
        soBuoiHoc++;
        System.out.printf("%s đã điểm danh. Tổng số buổi: %d%n", hoTen, soBuoiHoc);
    }
}

class HocVienOnline extends HocVien {
    private final String khuVuc;

    public HocVienOnline(String hoTen, String khuVuc) {
        super(hoTen);
        this.khuVuc = khuVuc;
    }

    @Override
    public void diemDanh() {
        super.diemDanh();
        System.out.println("Kết nối từ: " + khuVuc);
    }
}

public class LopJavaCoBan {
    public static void main(String[] args) {
        HocVien lan = new HocVien("Lan");
        HocVienOnline tung = new HocVienOnline("Tùng", "TP.HCM");

        lan.diemDanh();
        tung.diemDanh();
    }
}
```

Đoạn code trên minh họa cả bốn đặc tính: `HocVien` đóng gói dữ liệu bằng `private`, `HocVienOnline` kế thừa `HocVien`, trong khi phương thức `diemDanh` thể hiện đa hình thông qua `@Override`. Việc tạo constructor giúp đơn giản hóa thao tác khởi tạo đối tượng.

## Khi nào nên dùng OOP?

OOP phù hợp khi bạn cần:

- Mô tả các thực thể phức tạp như người dùng, sản phẩm, đơn hàng.  
- Xây dựng ứng dụng lớn cần khả năng mở rộng và bảo trì lâu dài.  
- Tổ chức code thành các module độc lập, dễ kiểm thử.

Ngược lại, với các script nhỏ, bạn có thể cân nhắc dạng lập trình hàm hoặc thủ tục để tránh tạo quá nhiều lớp rườm rà. Quan trọng là linh hoạt lựa chọn phong cách phù hợp với mục tiêu dự án.

## Mẹo học hiệu quả

1. Vẽ sơ đồ lớp trước khi viết code, giúp bạn hình dung mối quan hệ rõ ràng.  
2. Bắt đầu từ trường hợp đơn giản, sau đó thêm tính năng kế thừa, đa hình từng bước.  
3. Đọc mã nguồn framework như Spring để quan sát cách họ tổ chức class thực tế.  

Khi đã hiểu vững OOP, bạn sẽ thấy Java trở nên dễ chịu hơn nhiều. Từ đây, việc tiếp cận các công nghệ nâng cao như Spring Boot, Hibernate cũng sẽ “mượt” hơn vì chúng đều dựa trên các khái niệm quen thuộc của lập trình hướng đối tượng.
