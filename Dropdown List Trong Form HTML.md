# Tạo Dropdown List Trong Form HTML

## 1. Giới Thiệu

Dropdown list (hay danh sách lựa chọn) là một phần quan trọng trong các biểu mẫu HTML, cho phép người dùng chọn một trong các giá trị được xác định trước. Trong video này, chúng ta sẽ học cách tạo một dropdown list trong form HTML và xử lý dữ liệu người dùng chọn bằng JSP.

## 2. Ví Dụ Dropdown List

Giả sử chúng ta có một biểu mẫu cho phép người dùng nhập họ tên và chọn quốc gia của mình. Khi nhấn nút **Submit**, dữ liệu sẽ được gửi đến một trang JSP để xử lý và hiển thị lại thông tin mà người dùng đã chọn.

### Ví Dụ Dropdown List
```html
<form action="student-dropdown-response.jsp">
    <label for="firstName">First Name:</label>
    <input type="text" name="firstName"><br><br>

    <label for="lastName">Last Name:</label>
    <input type="text" name="lastName"><br><br>

    <label for="country">Country:</label>
    <select name="country">
        <option>Brazil</option>
        <option>France</option>
        <option>Germany</option>
        <option>India</option>
    </select><br><br>

    <input type="submit" value="Submit">
</form>
```

Trong đoạn mã trên:
- `select` là thẻ dùng để tạo dropdown list, và `name` là tên của trường dữ liệu mà ta sẽ đọc trong JSP.
- `option` là các tùy chọn mà người dùng có thể chọn trong dropdown list.

## 3. Tạo Trang HTML Cho Form

Đầu tiên, chúng ta sẽ tạo một trang HTML để thu thập thông tin từ người dùng, bao gồm họ tên và quốc gia mà họ chọn.

### 3.1 Tạo Trang `student-dropdown-form.html`
- Tạo một tệp HTML mới có tên `student-dropdown-form.html`.
- Nội dung trang HTML sẽ như sau:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Student Form with Dropdown</title>
</head>
<body>
    <h2>Student Information</h2>
    <form action="student-dropdown-response.jsp">
        <label for="firstName">First Name:</label>
        <input type="text" name="firstName"><br><br>

        <label for="lastName">Last Name:</label>
        <input type="text" name="lastName"><br><br>

        <label for="country">Country:</label>
        <select name="country">
            <option>Brazil</option>
            <option>France</option>
            <option>Germany</option>
            <option>India</option>
        </select><br><br>

        <input type="submit" value="Submit">
    </form>
</body>
</html>
```

Trong ví dụ trên:
- `action="student-dropdown-response.jsp"` chỉ định rằng khi người dùng nhấn nút **Submit**, dữ liệu sẽ được gửi đến trang `student-dropdown-response.jsp` để xử lý.

### 3.2 Tạo Trang JSP Để Xử Lý Dữ Liệu
Tạo một tệp JSP có tên `student-dropdown-response.jsp` để xử lý và hiển thị lại dữ liệu mà người dùng đã nhập.

#### Nội Dung Trang `student-dropdown-response.jsp`
```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Student Confirmation</title>
</head>
<body>
    <h2>Student Confirmation</h2>
    <p>The student's name is: ${param.firstName} ${param.lastName}</p>
    <p>The student's country is: ${param.country}</p>
</body>
</html>
```

Trong đoạn mã trên:
- `${param.firstName}`, `${param.lastName}`, và `${param.country}` là cú pháp để đọc dữ liệu từ form HTML mà người dùng đã nhập và hiển thị chúng trên trang JSP.

## 4. Chạy Ứng Dụng Và Kiểm Tra Kết Quả

Khi bạn chạy `student-dropdown-form.html` và nhập thông tin vào biểu mẫu:
1. **Nhập tên và họ**: Ví dụ `John Doe`.
2. **Chọn quốc gia**: Ví dụ `India`.
3. Nhấn nút **Submit**.

Kết quả sẽ được hiển thị trên `student-dropdown-response.jsp` như sau:

```
The student's name is: John Doe
The student's country is: India
```

## 5. Tổng Kết

- **Tạo Dropdown List**: Sử dụng thẻ `<select>` và `<option>` để tạo danh sách lựa chọn cho người dùng.
- **Kết Nối Form HTML và JSP**: Sử dụng thuộc tính `action` trong thẻ `<form>` để chỉ định trang JSP xử lý dữ liệu.
- **Xử Lý Dữ Liệu Với JSP**: Sử dụng cú pháp `${param.<tên_trường>}` để đọc và hiển thị dữ liệu từ form HTML.

Video này đã giúp bạn hiểu cách tạo dropdown list trong form HTML và cách xử lý dữ liệu đó bằng JSP. Trong các video tiếp theo, chúng ta sẽ tiếp tục tìm hiểu về các tính năng khác của JSP để xây dựng các ứng dụng web phức tạp hơn.
