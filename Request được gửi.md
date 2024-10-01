Khi người dùng nhấn nút **Submit** trong biểu mẫu HTML, một yêu cầu (request) sẽ được tạo ra và gửi đến máy chủ (server). Dưới đây là chi tiết về **request** được gửi:

### 1. **Loại Request:**
- **Request** này là một **HTTP POST request**.
- Thuộc tính `method="post"` trong thẻ `<form>` chỉ định rằng trình duyệt sẽ gửi dữ liệu dưới dạng POST thay vì GET. 
- POST request được dùng để gửi dữ liệu từ client (trình duyệt) đến server để xử lý và thường được sử dụng trong các biểu mẫu nhập liệu (form) hoặc khi cần truyền tải dữ liệu lớn hơn.

### 2. **URL của Request:**
- Thuộc tính `action="student-response.jsp"` chỉ định URL mà request sẽ được gửi đến.
- Trong trường hợp này, request sẽ được gửi đến tệp `student-response.jsp` trên server, theo đường dẫn hiện tại của trang.
- Nếu đường dẫn đầy đủ của trang hiện tại là `http://localhost:8080/StudentApp/form.html`, thì request sẽ được gửi đến `http://localhost:8080/StudentApp/student-response.jsp`.

### 3. **Dữ liệu được gửi trong Request:**
- Khi người dùng nhấn **Submit**, dữ liệu từ các trường trong biểu mẫu sẽ được thu thập và gửi đi.
- Dữ liệu được gửi dưới dạng **cặp khóa-giá trị (key-value pairs)**:
  - `firstName`: Giá trị mà người dùng nhập vào trường `First Name`.
  - `lastName`: Giá trị mà người dùng nhập vào trường `Last Name`.

- Giả sử người dùng nhập:
  - `First Name: John`
  - `Last Name: Doe`
  
  Dữ liệu gửi đi sẽ trông như sau:
  ```
  firstName=John&lastName=Doe
  ```

- Dữ liệu này được đặt trong **phần thân (body)** của POST request, không hiển thị trên URL như với GET request.

### 4. **Headers của Request:**
- POST request sẽ có một số thông tin (headers) đi kèm để cho server biết cách xử lý dữ liệu, ví dụ:
  - `Content-Type`: Loại nội dung mà client gửi đến server (thường là `application/x-www-form-urlencoded` cho biểu mẫu HTML).
  - `Content-Length`: Độ dài của dữ liệu được gửi (số byte).

### 5. **Ví dụ về Request:**
Dưới đây là ví dụ về request được gửi khi nhấn nút Submit:

```
POST /StudentApp/student-response.jsp HTTP/1.1
Host: localhost:8080
Content-Type: application/x-www-form-urlencoded
Content-Length: 27

firstName=John&lastName=Doe
```

- **Dòng đầu tiên (Request Line)**: `POST /StudentApp/student-response.jsp HTTP/1.1`
  - `POST`: Loại HTTP request.
  - `/StudentApp/student-response.jsp`: URL tương đối của tài nguyên mà yêu cầu được gửi đến.
  - `HTTP/1.1`: Phiên bản giao thức HTTP.

- **Dòng `Host`**: Cho biết tên máy chủ và cổng (`localhost:8080`).
- **Dòng `Content-Type`**: Định dạng của dữ liệu được gửi (ở đây là `application/x-www-form-urlencoded`).
- **Dòng `Content-Length`**: Độ dài của dữ liệu (ở đây là 27 byte).
- **Phần thân (Body)**: Chứa dữ liệu biểu mẫu dưới dạng `firstName=John&lastName=Doe`.

### 6. **Các thuộc tính trong Request:**
- Request có các thuộc tính quan trọng như:
  - **URL**: Đường dẫn đến tài nguyên trên server (`/StudentApp/student-response.jsp`).
  - **HTTP Method**: Phương thức HTTP được sử dụng (POST).
  - **Headers**: Thông tin bổ sung để server hiểu cách xử lý request (như `Content-Type`, `Content-Length`, v.v.).
  - **Body**: Chứa dữ liệu được gửi từ client (trong ví dụ là `firstName=John&lastName=Doe`).

### 7. **Server tiếp nhận Request và xử lý:**
- Server (Tomcat, GlassFish, v.v.) sẽ tiếp nhận request này, chuyển nó cho tệp `student-response.jsp`.
- Tệp `student-response.jsp` sẽ xử lý dữ liệu, ví dụ:
  ```jsp
  <%
  String firstName = request.getParameter("firstName");
  String lastName = request.getParameter("lastName");
  %>
  ```
- Server sẽ trả về một trang HTML khác hoặc xử lý thêm tùy theo logic của bạn.

### **Tóm lại:**
- Khi bạn nhấn **Submit**, một **POST request** sẽ được gửi từ trình duyệt đến server với URL đích là `student-response.jsp`.
- Request này chứa dữ liệu từ biểu mẫu (`firstName` và `lastName`) và các thông tin tiêu đề (headers).
- Server sẽ nhận request này và xử lý dữ liệu dựa trên logic trong tệp `student-response.jsp`.
