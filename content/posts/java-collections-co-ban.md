---
title: "Java Collections – List, Set, Map là gì và dùng khi nào"
date: 2025-10-16
draft: false
tags: ["Java", "JavaScript", "Lập trình"]
categories: ["Lập trình"]
description: "Giải thích các cấu trúc List, Set, Map trong Java Collections Framework và cách chọn đúng công cụ."
image: "/images/posts/java-collections-co-ban.jpg"
---

Khi dữ liệu vượt quá mức vài biến đơn lẻ, Java Collections Framework sẽ trở thành trợ thủ đắc lực cho bạn. Bộ sưu tập này cung cấp các cấu trúc dữ liệu đã được tối ưu sẵn, giúp việc lưu trữ, truy xuất và xử lý trở nên hiệu quả. Ba nhân vật quan trọng nhất mà lập trình viên nào cũng phải nắm là `List`, `Set` và `Map`.

## List – Khi cần giữ thứ tự

`List` lưu các phần tử theo thứ tự chèn vào và cho phép trùng lặp. Đây là lựa chọn lý tưởng khi bạn cần một danh sách học viên, lịch sử giao dịch, hay bất kỳ dữ liệu nào mà vị trí và thứ tự quan trọng.

### Khi nào nên chọn List?

- Cần truy cập phần tử theo chỉ số.  
- Cho phép phần tử trùng lặp.  
- Muốn duy trì thứ tự ban đầu của dữ liệu.  

```java
import java.util.ArrayList;
import java.util.List;

public class ViDuList {
    public static void main(String[] args) {
        List<String> chuongTrinh = new ArrayList<>();
        chuongTrinh.add("Java cơ bản");
        chuongTrinh.add("Spring Boot");
        chuongTrinh.add("Java cơ bản"); // trùng lặp được phép

        chuongTrinh.forEach(System.out::println);
    }
}
```

## Set – Khi cần duy nhất

`Set` đảm bảo mỗi phần tử xuất hiện tối đa một lần và không cam kết về thứ tự. Đây là lựa chọn phù hợp để lưu danh sách email đăng ký, mã sản phẩm hoặc từ khóa mà bạn không muốn trùng lặp.

### Lựa chọn phổ biến

- `HashSet`: hiệu năng cao, không đảm bảo thứ tự.  
- `LinkedHashSet`: giữ thứ tự chèn.  
- `TreeSet`: sắp xếp tăng dần theo tự nhiên hoặc bộ so sánh tùy chỉnh.  

## Map – Khi cần cặp khóa/giá trị

`Map` giúp bạn ánh xạ một khóa (key) đến một giá trị (value). Ví dụ, ánh xạ mã khóa học đến tên giảng viên, hoặc username đến thông tin profile.

```java
import java.util.HashMap;
import java.util.Map;

public class ViDuMap {
    public static void main(String[] args) {
        Map<String, String> giangVien = new HashMap<>();
        giangVien.put("JAVA101", "Hai Nguyen");
        giangVien.put("JS201", "Lan Pham");

        System.out.println("Giảng viên khóa JAVA101: " + giangVien.get("JAVA101"));
        giangVien.forEach((maKhoaHoc, ten) ->
            System.out.printf("%s được phụ trách bởi %s%n", maKhoaHoc, ten)
        );
    }
}
```

## Chọn cấu trúc nào?

Hãy tự hỏi:

1. **Có cho phép trùng lặp không?** Nếu không, dùng `Set`.  
2. **Có cần truy cập bằng khóa?** Nếu có, dùng `Map`.  
3. **Có quan tâm tới thứ tự?** Nếu có, chọn `List` hoặc `LinkedHashSet`, `LinkedHashMap`.  

Ngoài ra, cân nhắc hiệu năng: `ArrayList` nhanh khi duyệt, nhưng `LinkedList` phù hợp nếu bạn chèn/xóa ở đầu danh sách thường xuyên. Với `Map`, nếu cần sắp xếp khóa tự động, hãy chọn `TreeMap`.

## Kết luận

Java Collections Framework giống như hộp công cụ đa năng. Hiểu rõ mỗi cấu trúc giúp bạn viết code gọn, dễ đọc và tối ưu hơn. Hãy thử xây dựng một mini project như quản lý thư viện, nơi bạn sử dụng `List` cho danh sách sách, `Set` cho thể loại, và `Map` để ánh xạ người mượn với cuốn sách đang giữ. Qua thực hành, bạn sẽ cảm nhận rõ sức mạnh của bộ công cụ này.
