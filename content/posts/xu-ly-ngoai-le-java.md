---
title: "Xử lý ngoại lệ (Exception Handling) trong Java"
date: 2025-10-16
draft: false
tags: ["Java", "JavaScript", "Lập trình"]
description: "Học cách phát hiện, ném và xử lý ngoại lệ trong Java để ứng dụng luôn ổn định."
---

Ngoại lệ (exception) là những tình huống bất ngờ xảy ra khi chương trình đang chạy, chẳng hạn đọc file không tồn tại hoặc chia cho 0. Nếu không xử lý, ứng dụng sẽ dừng đột ngột và trải nghiệm người dùng bị ảnh hưởng. Với Java, cơ chế exception giúp chúng ta kiểm soát lỗi thay vì để chúng phá hỏng toàn bộ hệ thống.

## Phân loại ngoại lệ

- **Checked Exception**: Bắt buộc xử lý trong compile-time, ví dụ `IOException`, `SQLException`.  
- **Unchecked Exception**: Xảy ra trong runtime, như `NullPointerException`, `IllegalArgumentException`.  
- **Error**: Đề cập đến lỗi nghiêm trọng (thiếu bộ nhớ), thường khó phục hồi.

Hiểu phân loại giúp bạn nhận biết khi nào cần `try-catch`, khi nào nên để ngoại lệ lan truyền lên lớp gọi.

## Cấu trúc try-catch-finally

```java
import java.nio.file.Files;
import java.nio.file.Path;

public class DocFileAnToan {
    public static void main(String[] args) {
        Path duongDan = Path.of("du-lieu.txt");

        try {
            String noiDung = Files.readString(duongDan);
            System.out.println("Nội dung file: " + noiDung);
        } catch (Exception e) {
            System.err.println("Không thể đọc file: " + e.getMessage());
        } finally {
            System.out.println("Đóng tài nguyên nếu cần ở đây.");
        }
    }
}
```

Trong ví dụ, khối `try` chứa đoạn code có nguy cơ lỗi. Nếu việc đọc file thất bại, `catch` sẽ bắt ngoại lệ và in thông báo thân thiện. Khối `finally` chạy cho dù có lỗi hay không, giúp bạn đóng kết nối, giải phóng tài nguyên.

## Tự tạo ngoại lệ

Đôi khi bạn muốn thông báo điều kiện bất thường của riêng dự án. Hãy tự định nghĩa ngoại lệ bằng cách kế thừa `RuntimeException` hoặc `Exception`.

```java
class TuoiKhongHopLeException extends RuntimeException {
    public TuoiKhongHopLeException(String message) {
        super(message);
    }
}

class DangKyHocVien {
    public void dangKy(String hoTen, int tuoi) {
        if (tuoi < 16) {
            throw new TuoiKhongHopLeException("Học viên phải từ 16 tuổi trở lên.");
        }
        System.out.println("Chào mừng " + hoTen + " đến với lớp Java!");
    }
}
```

Khi sử dụng, nếu tuổi không đạt yêu cầu, chương trình sẽ ném ngoại lệ rõ ràng. Điều này giúp bạn tách biệt luồng xử lý chính và luồng xử lý lỗi một cách sạch sẽ.

## Nguyên tắc viết code an toàn

1. **Không bắt tất cả ngoại lệ** bằng `catch (Exception e)` nếu bạn biết rõ từng lỗi, vì sẽ khó truy dấu sự cố.  
2. **Ghi log chi tiết** với thư viện như SLF4J để phục vụ việc debug và hỗ trợ kỹ thuật.  
3. **Không bỏ trống khối catch**; ít nhất hãy cung cấp thông báo người dùng có thể hiểu.  
4. **Sử dụng try-with-resources** khi làm việc với IO để tự động đóng tài nguyên.

## Kết luận

Xử lý ngoại lệ không chỉ là kỹ thuật cứu lỗi mà còn là nghệ thuật khiến ứng dụng thân thiện, dễ bảo trì. Khi bạn chủ động dự đoán và quản lý tình huống bất thường, sản phẩm của bạn sẽ vận hành ổn định và tạo dựng niềm tin với người dùng. Vì vậy, hãy luôn đặt câu hỏi “Điều gì sẽ xảy ra nếu đoạn code này thất bại?” và chuẩn bị kế hoạch ứng phó ngay từ bây giờ.
