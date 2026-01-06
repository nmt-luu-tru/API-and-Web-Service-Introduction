Quá trình tương tác giữa **client (trình duyệt)** và **server** thường diễn ra như sau:

### 1. **Quá trình gửi yêu cầu (Request) từ trình duyệt đến server:**
- Khi người dùng nhập thông tin vào biểu mẫu HTML và nhấn nút **Submit**, trình duyệt sẽ gửi yêu cầu (HTTP request) đến máy chủ (server) được chỉ định trong thuộc tính `action` của thẻ `<form>`. Trong trường hợp của bạn:

    ```html
    <form action="student-response.jsp" method="post">
    ```
  - Điều này có nghĩa là trình duyệt sẽ gửi yêu cầu đến tệp `student-response.jsp` trên server.

### 2. **Server xử lý yêu cầu bằng tệp JSP:**
- **Server** (ví dụ: Apache Tomcat, GlassFish) tiếp nhận yêu cầu từ trình duyệt. 
- Server sẽ xác định rằng yêu cầu này được định tuyến đến tệp `student-response.jsp`.
- Tệp JSP (`student-response.jsp`) được **biên dịch thành một Servlet** (một lớp Java đặc biệt) nếu chưa được biên dịch trước đó.
- Servlet này sẽ thực thi mã Java bên trong tệp JSP để xử lý yêu cầu. Nó có thể:
  - Lấy dữ liệu được gửi từ form bằng phương thức `request.getParameter()`.
  - Tương tác với cơ sở dữ liệu.
  - Thực hiện logic nghiệp vụ (business logic).
  - Tạo ra nội dung (HTML, JSON, v.v.) để phản hồi lại trình duyệt.

### 3. **Server phản hồi kết quả cho trình duyệt (Response):**
- Sau khi tệp JSP hoàn tất xử lý yêu cầu, nó sẽ **trả về một phản hồi (HTTP response)** cho trình duyệt.
- Phản hồi này có thể là:
  - Một trang HTML được tạo ra từ tệp JSP (thông thường nhất).
  - Dữ liệu JSON/XML hoặc bất kỳ định dạng nào khác nếu đó là API.
  - Hoặc server có thể chuyển hướng (redirect) đến một trang khác nếu cần.

- Ví dụ: Nếu `student-response.jsp` tạo ra một trang HTML chứa tên người dùng, trình duyệt sẽ hiển thị trang này cho người dùng:

    ```jsp
    <%
    String firstName = request.getParameter("firstName");
    String lastName = request.getParameter("lastName");
    %>
    <html>
    <body>
        <h2>Welcome, <%= firstName %> <%= lastName %>!</h2>
    </body>
    </html>
    ```

### 4. **Tương tác giữa client và server:**
- Client và server sẽ tiếp tục tương tác với nhau thông qua các yêu cầu (requests) và phản hồi (responses). Tệp JSP sẽ đóng vai trò xử lý những yêu cầu này tại server và gửi lại phản hồi tương ứng cho client.

### **Tóm tắt:**
- **Trình duyệt (client)** gửi request chứa dữ liệu người dùng đến **server**.
- **Server** xử lý request bằng cách sử dụng tệp JSP và tạo ra phản hồi.
- **Server** gửi phản hồi lại cho **trình duyệt**, và trình duyệt hiển thị kết quả cho người dùng.

Trong quá trình này, các tệp JSP là các thành phần xử lý và định dạng dữ liệu phía server, chứ không phải là server trực tiếp. Mọi tương tác giữa client và server đều diễn ra thông qua các request và response, và JSP sẽ giúp xử lý logic server-side, tạo ra nội dung động để phản hồi lại client.
