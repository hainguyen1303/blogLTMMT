---
title: "DOM là gì? Cách JavaScript tương tác với trang web"
date: 2025-10-16
draft: false
tags: ["Java", "JavaScript", "Lập trình"]
description: "Giải thích Document Object Model và cách dùng JavaScript để đọc, sửa nội dung trang web."
---

Khi bạn mở một trang web, trình duyệt không chỉ hiển thị HTML tĩnh mà còn xây dựng một cấu trúc dữ liệu gọi là Document Object Model (DOM). DOM giống như phiên bản “sống” của trang, nơi JavaScript có thể đọc, chỉnh sửa và phản hồi các sự kiện của người dùng. Hiểu DOM giúp bạn biến những trang HTML tĩnh trở nên tương tác và thông minh.

## DOM là gì?

DOM là mô hình cây biểu diễn mọi phần tử trên trang web. Mỗi thẻ HTML được chuyển thành một node với mối quan hệ cha – con rõ ràng. Nhờ đó, JavaScript có thể duyệt cây, tìm phần tử cụ thể và cập nhật nội dung theo nhu cầu.

### Tại sao DOM quan trọng?

- Cho phép cập nhật nội dung mà không tải lại trang.  
- Lắng nghe hành vi người dùng (click, gõ phím, cuộn).  
- Tạo hiệu ứng, popup, modal, hoặc bất kỳ tương tác nào bạn tưởng tượng được.

## Ví dụ thao tác DOM

```javascript
const nutDangKy = document.querySelector("#dang-ky");
const thongBao = document.querySelector(".thong-bao");

nutDangKy.addEventListener("click", () => {
  thongBao.textContent = "Cảm ơn bạn đã đăng ký nhận bản tin Java & JavaScript!";
  thongBao.classList.add("hien-thi");
});
```

Đoạn code trên lấy hai phần tử DOM bằng `querySelector`, gắn sự kiện `click`, cập nhật nội dung và thêm lớp CSS để hiển thị thông báo. Đây là nền tảng của mọi tương tác front-end.

## Các thao tác DOM thường gặp

1. **Tìm phần tử**: dùng `getElementById`, `querySelector`, `querySelectorAll`.  
2. **Đổi nội dung**: cập nhật `textContent`, `innerHTML`, hoặc thuộc tính như `src`, `href`.  
3. **Thay đổi style**: sử dụng `classList` để thêm/bớt lớp CSS.  
4. **Xử lý sự kiện**: `addEventListener` cho click, input, submit, keydown, v.v.

### Mẹo tối ưu

- **Hạn chế thao tác DOM quá nhiều lần**: gom thay đổi vào fragment hoặc sử dụng virtual DOM framework.  
- **Làm sạch sự kiện** khi phần tử bị xóa để tránh rò rỉ bộ nhớ.  
- **Tách phần xử lý logic** khỏi DOM để dễ bảo trì.

## DOM và các framework hiện đại

Các framework như React, Vue hay Svelte đều dựa trên DOM nhưng cung cấp cách tiếp cận “ảo” để tối ưu hiệu năng. Tuy vậy, việc nắm chắc DOM thuần vẫn rất quan trọng, bởi nó giúp bạn hiểu cách framework hoạt động bên dưới và xử lý các tình huống đặc biệt mà thư viện không hỗ trợ sẵn.

## Kết luận

DOM chính là cầu nối giữa HTML và JavaScript. Khi bạn hiểu cách cây DOM được tạo và biết cách thao tác nó, bạn có thể xây dựng trải nghiệm người dùng phong phú mà không cần reload trang. Hãy thử tạo một form liên hệ nhỏ, thêm thông báo thành công như ví dụ trên để cảm nhận sức mạnh của DOM nhé!
