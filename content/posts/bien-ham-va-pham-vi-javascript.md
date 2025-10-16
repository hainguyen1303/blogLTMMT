---
title: "Biến, hàm và phạm vi (scope) trong JavaScript"
date: 2025-10-16
draft: false
tags: ["Java", "JavaScript", "Lập trình"]
description: "Khám phá cách khai báo biến, định nghĩa hàm và quản lý phạm vi trong JavaScript."
---

Hiểu rõ biến, hàm và phạm vi giúp bạn tránh nhiều lỗi khó chịu trong JavaScript. Không ít lần tôi chứng kiến người mới vô tình “đè” biến toàn cục hoặc không hiểu vì sao hàm không truy cập được biến bên ngoài. Bài viết này sẽ giải thích từng khái niệm một cách dễ hiểu, kèm theo ví dụ để bạn tự kiểm chứng.

## Khai báo biến trong JavaScript

JavaScript hiện đại cung cấp ba cách khai báo: `var`, `let`, `const`. Điểm khác biệt chính là phạm vi và khả năng gán lại giá trị.

- `var`: phạm vi hàm, có hoisting, dễ gây lỗi nếu dùng chung với nhiều hàm.  
- `let`: phạm vi khối (`block`), cho phép gán lại giá trị.  
- `const`: phạm vi khối, không cho gán lại, nhưng vẫn có thể thay đổi thuộc tính của object.

## Hàm (Function)

Hàm là khối mã tái sử dụng được. Bạn có thể định nghĩa hàm bằng function declaration, function expression hoặc arrow function. Mỗi cách có ưu điểm riêng nhưng quan trọng là chọn phong cách nhất quán và dễ đọc.

### Ví dụ kết hợp biến và hàm

```javascript
function tinhTienGiaoDich(soLuong, donGia) {
  const thue = 0.1; // 10%
  let tong = soLuong * donGia;
  tong += tong * thue;
  return tong;
}

const soLuong = 3;
const donGia = 150_000;
console.log(`Tổng tiền phải trả: ${tinhTienGiaoDich(soLuong, donGia)} VND`);
```

Trong ví dụ, `thue` được khai báo bằng `const` vì tỷ lệ thuế cố định, trong khi `tong` dùng `let` vì giá trị thay đổi trong quá trình tính toán.

## Phạm vi (Scope)

Phạm vi quyết định biến được truy cập ở đâu. JavaScript có ba cấp độ:

1. **Global scope**: biến có thể truy cập mọi nơi.  
2. **Function scope**: biến chỉ dùng được trong hàm nơi nó được khai báo.  
3. **Block scope**: áp dụng cho `let` và `const`, giới hạn trong cặp `{}` gần nhất.

### Minh họa phạm vi

```javascript
const lop = "JavaScript 101";

function thongBao() {
  const giangVien = "Hai Nguyen";
  if (true) {
    let phongHoc = "Phòng Zoom A";
    console.log(`${giangVien} dạy ${lop} tại ${phongHoc}`);
  }
  // console.log(phongHoc); // Lỗi vì phongHoc chỉ tồn tại trong block if
}

thongBao();
```

Sử dụng `const` và `let` giúp bạn tránh lạm dụng biến toàn cục. Đồng thời, nhớ không truy cập biến ngoài phạm vi của nó để tránh `ReferenceError`.

## Lời khuyên thực hành

- **Tránh dùng `var`** trừ khi phải làm việc với mã legacy.  
- **Đặt tên biến rõ nghĩa** để dễ bảo trì.  
- **Giữ hàm ngắn gọn**: mỗi hàm nên đảm nhận một nhiệm vụ duy nhất.  
- **Sử dụng linter** như ESLint để phát hiện lỗi phạm vi tự động.

## Kết luận

Biết cách quản lý biến, hàm và phạm vi là bước quan trọng để viết JavaScript sạch và đáng tin cậy. Bạn sẽ tự tin hơn khi làm việc với các framework front-end hay backend trên Node.js vì mọi thứ đều dựa trên nền tảng này. Hãy thử viết một mini project, như ứng dụng ghi chú, để luyện tập các khái niệm vừa học nhé!
