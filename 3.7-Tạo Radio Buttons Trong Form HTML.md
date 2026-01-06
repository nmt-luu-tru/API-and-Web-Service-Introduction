# Hướng Dẫn Sử Dụng JSP Để Tạo Radio Buttons Trong Form HTML

## 1. Giới Thiệu

Trong video này, chúng ta sẽ học cách sử dụng **JSP** để tạo các biểu mẫu HTML với các nút radio (radio buttons). Radio buttons là các thành phần quan trọng trong các biểu mẫu, cho phép người dùng chọn một trong nhiều tùy chọn có sẵn. Chúng thường được sử dụng để thu thập thông tin lựa chọn từ người dùng, chẳng hạn như chọn ngôn ngữ lập trình yêu thích, giới tính, hoặc các tùy chọn khác.

### Nội Dung Bài Học

- **Demo Radio Buttons**: Xem radio buttons hoạt động như thế nào.
- **Mã HTML Cho Radio Buttons**: Tìm hiểu cách xây dựng radio buttons trong HTML.
- **Ví Dụ JSP Hoàn Chỉnh**: Kết hợp radio buttons với JSP để xử lý dữ liệu người dùng.

## 2. Radio Buttons Trong HTML Là Gì?

**Radio buttons** là các phần tử trong biểu mẫu HTML cho phép người dùng chọn một tùy chọn duy nhất từ một nhóm các lựa chọn có sẵn. Khi một radio button được chọn, các radio buttons khác trong cùng nhóm sẽ tự động bị bỏ chọn.

### 2.1. Ví Dụ Radio Buttons

Giả sử chúng ta có một biểu mẫu cho phép học sinh nhập tên và chọn ngôn ngữ lập trình yêu thích. Các tùy chọn ngôn ngữ có thể bao gồm: Java, PHP, C#, hoặc Ruby. Khi học sinh chọn một ngôn ngữ và nhấn nút **Submit**, dữ liệu sẽ được gửi đến một trang JSP để xử lý và hiển thị lại thông tin đã chọn.

### 2.2. Cấu Trúc HTML Cho Radio Buttons

Dưới đây là cấu trúc HTML cơ bản để tạo radio buttons:

```html
<form action="student-radio-response.jsp" method="post">
    <label for="firstName">First Name:</label>
    <input type="text" name="firstName"><br><br>

    <label for="lastName">Last Name:</label>
    <input type="text" name="lastName"><br><br>

    <p>Favorite Programming Language:</p>
    <input type="radio" name="favoriteLanguage" value="Java"> Java<br>
    <input type="radio" name="favoriteLanguage" value="PHP"> PHP<br>
    <input type="radio" name="favoriteLanguage" value="C#"> C#<br>
    <input type="radio" name="favoriteLanguage" value="Ruby"> Ruby<br><br>

    <input type="submit" value="Submit">
</form>
```

Trong đoạn mã trên:
- **`<input type="radio">`**: Tạo một radio button.
- **`name="favoriteLanguage"`**: Tất cả các radio buttons trong cùng một nhóm phải có cùng thuộc tính `name` để đảm bảo chỉ có thể chọn một tùy chọn duy nhất.
- **`value="Java"`**, **`value="PHP"`**, vv.: Giá trị sẽ được gửi đến server khi tùy chọn đó được chọn.

## 3. Tạo Trang HTML Cho Biểu Mẫu Radio Buttons

Chúng ta sẽ tạo một trang HTML để thu thập thông tin từ học sinh, bao gồm họ tên và ngôn ngữ lập trình yêu thích.

### 3.1. Tạo Tệp `student-radio-form.html`

1. **Mở Dự Án**: Sử dụng Eclipse và mở dự án hiện tại của bạn, ví dụ: `jspdemo`.
2. **Tạo Tệp Mới**:
   - Nhấp chuột phải vào thư mục **WebContent**.
   - Chọn **New > File**.
   - Đặt tên tệp là `student-radio-form.html` và nhấn **Finish**.
3. **Thêm Mã HTML**:
   - Mở tệp `student-radio-form.html`.
   - Thêm đoạn mã HTML sau:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Student Radio Form</title>
</head>
<body>
    <h2>Student Information Form</h2>
    <form action="student-radio-response.jsp" method="post">
        <label for="firstName">First Name:</label>
        <input type="text" name="firstName"><br><br>

        <label for="lastName">Last Name:</label>
        <input type="text" name="lastName"><br><br>

        <p>Favorite Programming Language:</p>
        <input type="radio" name="favoriteLanguage" value="Java"> Java<br>
        <input type="radio" name="favoriteLanguage" value="PHP"> PHP<br>
        <input type="radio" name="favoriteLanguage" value="C#"> C#<br>
        <input type="radio" name="favoriteLanguage" value="Ruby"> Ruby<br><br>

        <input type="submit" value="Submit">
    </form>
</body>
</html>
```

## 4. Tạo Trang JSP Để Xử Lý Dữ Liệu Biểu Mẫu

Trang JSP này sẽ nhận dữ liệu từ biểu mẫu HTML, xử lý nó và hiển thị lại thông tin đã chọn.

### 4.1. Tạo Tệp `student-radio-response.jsp`

1. **Tạo Tệp Mới**:
   - Nhấp chuột phải vào thư mục **WebContent**.
   - Chọn **New > File**.
   - Đặt tên tệp là `student-radio-response.jsp` và nhấn **Finish**.
2. **Thêm Mã JSP**:
   - Mở tệp `student-radio-response.jsp`.
   - Thêm đoạn mã JSP sau:

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Student Confirmation</title>
</head>
<body>
    <h2>Student Confirmation</h2>
    <p>The student's name is: ${param.firstName} ${param.lastName}</p>
    <p>The student's favorite programming language is: ${param.favoriteLanguage}</p>
</body>
</html>
```

Trong đoạn mã trên:
- **`${param.firstName}`** và **`${param.lastName}`**: Lấy giá trị từ các trường `firstName` và `lastName` của biểu mẫu.
- **`${param.favoriteLanguage}`**: Lấy giá trị từ radio button `favoriteLanguage` mà học sinh đã chọn.

## 5. Chạy Ứng Dụng Và Kiểm Tra Kết Quả

Sau khi đã tạo các tệp cần thiết, chúng ta sẽ chạy ứng dụng để kiểm tra xem mọi thứ hoạt động như mong đợi.

### 5.1. Chạy Trang `student-radio-form.html`

1. **Mở Trang Form**:
   - Nhấp chuột phải vào tệp `student-radio-form.html`.
   - Chọn **Run As > Run on Server**.
   - Chọn máy chủ Tomcat đã được cấu hình và nhấn **Finish**.
2. **Điền Thông Tin Và Chọn Ngôn Ngữ**:
   - Nhập `First Name`: Ví dụ `John`.
   - Nhập `Last Name`: Ví dụ `Doe`.
   - Chọn `Favorite Programming Language`: Ví dụ `PHP`.
3. **Gửi Biểu Mẫu**:
   - Nhấn nút **Submit**.

### 5.2. Kiểm Tra Trang Xác Nhận `student-radio-response.jsp`

Khi bạn gửi biểu mẫu, trang `student-radio-response.jsp` sẽ được tải và hiển thị thông tin đã nhập:

```
Student Confirmation

The student's name is: John Doe
The student's favorite programming language is: PHP
```

## 6. Kết Luận

Trong video này, chúng ta đã học cách:

1. **Tạo Biểu Mẫu HTML Với Radio Buttons**:
   - Sử dụng thẻ `<input type="radio">` để tạo các lựa chọn duy nhất cho người dùng.
   - Đảm bảo tất cả các radio buttons trong cùng một nhóm có cùng thuộc tính `name` để chỉ cho phép chọn một tùy chọn duy nhất.

2. **Xử Lý Dữ Liệu Với JSP**:
   - Sử dụng cú pháp `${param.<tên_trường>}` để truy xuất dữ liệu từ biểu mẫu HTML.
   - Hiển thị thông tin đã nhập và lựa chọn của người dùng trên trang xác nhận.

### Những Điều Bạn Có Thể Làm Tiếp Theo

- **Thêm Các Radio Buttons Khác**: Thử thêm nhiều lựa chọn hơn hoặc các nhóm radio buttons khác trong biểu mẫu.
- **Xử Lý Lỗi**: Thêm các kiểm tra để đảm bảo người dùng đã chọn một tùy chọn trước khi gửi biểu mẫu.
- **Tích Hợp Với Backend**: Kết nối JSP với cơ sở dữ liệu để lưu trữ thông tin người dùng hoặc xử lý các tác vụ phức tạp hơn.

Hãy tiếp tục thực hành và khám phá thêm các tính năng của JSP để xây dựng các ứng dụng web mạnh mẽ và linh hoạt!
