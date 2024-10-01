# Hướng Dẫn Sử Dụng JSP Để Tạo Checkbox Trong Form HTML

## 1. Giới Thiệu

Trong video này, chúng ta sẽ học cách sử dụng **JSP** để tạo các biểu mẫu HTML với các ô chọn (checkboxes). Checkbox cho phép người dùng chọn nhiều tùy chọn trong một nhóm các lựa chọn có sẵn, mang lại sự linh hoạt hơn so với radio buttons. Điều này hữu ích khi bạn muốn người dùng có thể chọn nhiều lựa chọn mà không bị giới hạn chỉ một lựa chọn duy nhất.

### Nội Dung Bài Học

- **Demo Checkbox**: Xem checkbox hoạt động như thế nào.
- **Mã HTML Cho Checkbox**: Tìm hiểu cách xây dựng checkbox trong HTML.
- **Ví Dụ JSP Hoàn Chỉnh**: Kết hợp checkbox với JSP để xử lý dữ liệu người dùng.

## 2. Checkbox Trong HTML Là Gì?

**Checkboxes** là các phần tử trong biểu mẫu HTML cho phép người dùng chọn một hoặc nhiều tùy chọn từ một nhóm các lựa chọn có sẵn. Khi một checkbox được chọn, nó sẽ giữ trạng thái được chọn cho đến khi người dùng bỏ chọn nó.

### 2.1. Ví Dụ Checkbox

Giả sử chúng ta có một biểu mẫu cho phép học sinh nhập tên và chọn các ngôn ngữ lập trình yêu thích. Các tùy chọn ngôn ngữ có thể bao gồm: Java, PHP, C#, hoặc Ruby. Khi học sinh chọn một hoặc nhiều ngôn ngữ và nhấn nút **Submit**, dữ liệu sẽ được gửi đến một trang JSP để xử lý và hiển thị lại thông tin đã chọn.

### 2.2. Cấu Trúc HTML Cho Checkbox

Dưới đây là cấu trúc HTML cơ bản để tạo checkboxes:

```html
<form action="student-checkbox-response.jsp" method="post">
    <label for="firstName">First Name:</label>
    <input type="text" name="firstName"><br><br>

    <label for="lastName">Last Name:</label>
    <input type="text" name="lastName"><br><br>

    <p>Favorite Programming Languages:</p>
    <input type="checkbox" name="favoriteLanguage" value="Java"> Java<br>
    <input type="checkbox" name="favoriteLanguage" value="PHP"> PHP<br>
    <input type="checkbox" name="favoriteLanguage" value="C#"> C#<br>
    <input type="checkbox" name="favoriteLanguage" value="Ruby"> Ruby<br><br>

    <input type="submit" value="Submit">
</form>
```

Trong đoạn mã trên:
- **`<input type="checkbox">`**: Tạo một checkbox.
- **`name="favoriteLanguage"`**: Tất cả các checkboxes trong cùng một nhóm phải có cùng thuộc tính `name` để dễ dàng xử lý dữ liệu trên server.
- **`value="Java"`**, **`value="PHP"`**, vv.: Giá trị sẽ được gửi đến server khi checkbox đó được chọn.

## 3. Tạo Trang HTML Cho Biểu Mẫu Checkbox

Chúng ta sẽ tạo một trang HTML để thu thập thông tin từ học sinh, bao gồm họ tên và các ngôn ngữ lập trình yêu thích mà họ chọn.

### 3.1. Tạo Tệp `student-checkbox-form.html`

1. **Mở Dự Án**: Sử dụng Eclipse và mở dự án hiện tại của bạn, ví dụ: `jspdemo`.
2. **Tạo Tệp Mới**:
   - Nhấp chuột phải vào thư mục **WebContent**.
   - Chọn **New > File**.
   - Đặt tên tệp là `student-checkbox-form.html` và nhấn **Finish**.
3. **Thêm Mã HTML**:
   - Mở tệp `student-checkbox-form.html`.
   - Thêm đoạn mã HTML sau:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Student Checkbox Form</title>
</head>
<body>
    <h2>Student Information Form</h2>
    <form action="student-checkbox-response.jsp" method="post">
        <label for="firstName">First Name:</label>
        <input type="text" name="firstName"><br><br>

        <label for="lastName">Last Name:</label>
        <input type="text" name="lastName"><br><br>

        <p>Favorite Programming Languages:</p>
        <input type="checkbox" name="favoriteLanguage" value="Java"> Java<br>
        <input type="checkbox" name="favoriteLanguage" value="PHP"> PHP<br>
        <input type="checkbox" name="favoriteLanguage" value="C#"> C#<br>
        <input type="checkbox" name="favoriteLanguage" value="Ruby"> Ruby<br><br>

        <input type="submit" value="Submit">
    </form>
</body>
</html>
```

## 4. Tạo Trang JSP Để Xử Lý Dữ Liệu Biểu Mẫu

Trang JSP này sẽ nhận dữ liệu từ biểu mẫu HTML, xử lý nó và hiển thị lại thông tin đã chọn.

### 4.1. Tạo Tệp `student-checkbox-response.jsp`

1. **Tạo Tệp Mới**:
   - Nhấp chuột phải vào thư mục **WebContent**.
   - Chọn **New > File**.
   - Đặt tên tệp là `student-checkbox-response.jsp` và nhấn **Finish**.
2. **Thêm Mã JSP**:
   - Mở tệp `student-checkbox-response.jsp`.
   - Thêm đoạn mã JSP sau:

```jsp
<%@ page import="java.util.Arrays" %>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Student Confirmation</title>
</head>
<body>
    <h2>Student Confirmation</h2>
    <p>The student's name is: ${param.firstName} ${param.lastName}</p>
    <p>The student's favorite programming languages are:</p>
    <ul>
        <%
            // Lấy các giá trị từ các checkbox đã chọn
            String[] languages = request.getParameterValues("favoriteLanguage");
            if (languages != null) {
                for (String lang : languages) {
        %>
                    <li><%= lang %></li>
        <%
                }
            } else {
        %>
                <li>No language selected.</li>
        <%
            }
        %>
    </ul>
</body>
</html>
```

Trong đoạn mã trên:
- **`${param.firstName}`** và **`${param.lastName}`**: Lấy giá trị từ các trường `firstName` và `lastName` của biểu mẫu.
- **`request.getParameterValues("favoriteLanguage")`**: Lấy tất cả các giá trị từ các checkbox `favoriteLanguage` mà học sinh đã chọn. Phương thức này trả về một mảng `String[]` vì người dùng có thể chọn nhiều giá trị.
- **Vòng lặp `for`**: Duyệt qua từng ngôn ngữ đã chọn và hiển thị chúng trong danh sách không thứ tự (`<ul>`).

## 5. Chạy Ứng Dụng Và Kiểm Tra Kết Quả

Sau khi đã tạo các tệp cần thiết, chúng ta sẽ chạy ứng dụng để kiểm tra xem mọi thứ hoạt động như mong đợi.

### 5.1. Chạy Trang `student-checkbox-form.html`

1. **Mở Trang Form**:
   - Nhấp chuột phải vào tệp `student-checkbox-form.html`.
   - Chọn **Run As > Run on Server**.
   - Chọn máy chủ Tomcat đã được cấu hình và nhấn **Finish**.
2. **Điền Thông Tin Và Chọn Ngôn Ngữ**:
   - Nhập `First Name`: Ví dụ `Ajay`.
   - Nhập `Last Name`: Ví dụ `Rao`.
   - Chọn `Favorite Programming Languages`: Ví dụ chọn `PHP` và `Ruby`.
3. **Gửi Biểu Mẫu**:
   - Nhấn nút **Submit**.

### 5.2. Kiểm Tra Trang Xác Nhận `student-checkbox-response.jsp`

Khi bạn gửi biểu mẫu, trang `student-checkbox-response.jsp` sẽ được tải và hiển thị thông tin đã nhập:

```
Student Confirmation

The student's name is: Ajay Rao
The student's favorite programming languages are:
- PHP
- Ruby
```

Nếu người dùng không chọn bất kỳ ngôn ngữ nào, danh sách sẽ hiển thị:

```
Student Confirmation

The student's name is: John Doe
The student's favorite programming languages are:
- No language selected.
```

## 6. Tổng Kết

Trong video này, chúng ta đã học cách:

1. **Tạo Biểu Mẫu HTML Với Checkbox**:
   - Sử dụng thẻ `<input type="checkbox">` để tạo các lựa chọn cho người dùng.
   - Đảm bảo tất cả các checkboxes trong cùng một nhóm có cùng thuộc tính `name` để dễ dàng xử lý dữ liệu trên server.

2. **Xử Lý Dữ Liệu Với JSP**:
   - Sử dụng phương thức `request.getParameterValues("favoriteLanguage")` để lấy tất cả các giá trị từ các checkbox đã chọn.
   - Duyệt qua mảng các giá trị và hiển thị chúng trên trang xác nhận.

### Những Điều Bạn Có Thể Làm Tiếp Theo

- **Thêm Các Checkbox Khác**: Thử thêm nhiều lựa chọn hơn hoặc các nhóm checkbox khác trong biểu mẫu.
- **Xử Lý Lỗi**: Thêm các kiểm tra để đảm bảo người dùng đã chọn ít nhất một tùy chọn trước khi gửi biểu mẫu.
- **Tích Hợp Với Backend**: Kết nối JSP với cơ sở dữ liệu để lưu trữ thông tin người dùng hoặc xử lý các tác vụ phức tạp hơn.
- **Sử Dụng Session Tracking**: Kết hợp với session tracking để lưu trữ dữ liệu người dùng trong suốt phiên làm việc.

Hãy tiếp tục thực hành và khám phá thêm các tính năng của JSP để xây dựng các ứng dụng web mạnh mẽ và linh hoạt!
