Trong một hệ thống ứng dụng web, ba thành phần chính là **Web Browser (Trình duyệt web)**, **Web Server (Máy chủ web)**, và **Database (Cơ sở dữ liệu)** có mối quan hệ chặt chẽ với nhau, tạo thành kiến trúc **3-tier (3 lớp)** để xử lý yêu cầu và phản hồi. Dưới đây là vai trò, mối quan hệ và sự tương tác giữa ba thành phần này:

### 1. **Vai trò của từng thành phần:**

#### **1.1. Web Browser (Trình duyệt web)**
- **Vai trò:** 
  - Web Browser là ứng dụng được sử dụng bởi người dùng cuối (client) để tương tác với các ứng dụng web. Ví dụ: Google Chrome, Mozilla Firefox, Microsoft Edge.
  - Nó gửi yêu cầu (request) đến Web Server thông qua giao thức HTTP/HTTPS và hiển thị nội dung (HTML, CSS, JavaScript) mà Web Server trả về.
  - Ngoài ra, trình duyệt cũng có thể xử lý các đoạn mã JavaScript, lưu trữ cookie, và quản lý phiên làm việc (session) để tăng trải nghiệm người dùng.
  
- **Chức năng chính:**
  - Gửi yêu cầu HTTP/HTTPS đến Web Server thông qua URL.
  - Hiển thị nội dung và giao diện đồ họa của ứng dụng web.
  - Thực thi các mã JavaScript chạy trên client (phía người dùng).
  - Quản lý các session và cookie để duy trì trạng thái (state) của người dùng.

#### **1.2. Web Server (Máy chủ web)**
- **Vai trò:**
  - Web Server là một chương trình hoặc hệ thống phần mềm chịu trách nhiệm nhận, xử lý các yêu cầu HTTP/HTTPS từ Web Browser và gửi phản hồi (response) tương ứng.
  - Web Server chứa mã nguồn của ứng dụng (bao gồm các tệp HTML, CSS, JavaScript, JSP, PHP, ASP.NET, v.v.) và logic xử lý yêu cầu từ phía client.
  - Web Server có thể thực hiện các thao tác như xác thực người dùng, xử lý yêu cầu, lấy dữ liệu từ Database, và tạo ra nội dung động (dynamic content) để phản hồi lại cho client.
  
- **Chức năng chính:**
  - Nhận yêu cầu từ Web Browser.
  - Thực thi các ứng dụng web hoặc script (JSP, PHP, .NET, v.v.) để tạo ra nội dung động.
  - Gửi yêu cầu đến Database nếu cần thiết để truy xuất hoặc lưu trữ dữ liệu.
  - Trả về phản hồi (HTML, JSON, XML, v.v.) đến Web Browser.

#### **1.3. Database (Cơ sở dữ liệu)**
- **Vai trò:**
  - Database là hệ thống lưu trữ dữ liệu có cấu trúc. Đây là nơi lưu trữ toàn bộ dữ liệu của ứng dụng như thông tin người dùng, sản phẩm, đơn hàng, bài viết, v.v.
  - Database cho phép Web Server thực hiện các thao tác CRUD (Create, Read, Update, Delete) để quản lý dữ liệu.
  
- **Chức năng chính:**
  - Lưu trữ và quản lý dữ liệu của ứng dụng.
  - Cung cấp phương thức để Web Server có thể thực hiện các thao tác truy vấn (query), thêm mới, cập nhật, và xóa dữ liệu.
  - Đảm bảo tính toàn vẹn, bảo mật, và hiệu suất của dữ liệu.

### 2. **Mối quan hệ giữa Web Browser, Web Server, và Database:**
- Mối quan hệ giữa ba thành phần này là một kiến trúc **3-tier (3 lớp)**. Mỗi thành phần sẽ đảm nhận một vai trò riêng biệt, nhưng có mối liên kết chặt chẽ với nhau:
  - **Web Browser (Client layer):** Tầng giao diện người dùng (UI layer).
  - **Web Server (Business logic layer):** Tầng xử lý logic nghiệp vụ.
  - **Database (Data layer):** Tầng lưu trữ và quản lý dữ liệu.
  
- Kiến trúc 3-tier giúp tách biệt từng tầng, dễ bảo trì, dễ mở rộng và tăng tính bảo mật cho hệ thống.

### 3. **Sự tương tác giữa Web Browser, Web Server, và Database:**
Sự tương tác giữa Web Browser, Web Server, và Database diễn ra theo các bước cơ bản sau:

1. **Web Browser gửi yêu cầu đến Web Server:**
   - Khi người dùng truy cập vào một trang web (ví dụ: `https://example.com`), Web Browser sẽ gửi một HTTP GET request đến Web Server qua URL tương ứng.
   - Request này có thể chứa thông tin như: cookie, tham số URL, dữ liệu biểu mẫu, hoặc dữ liệu xác thực.

2. **Web Server nhận và xử lý yêu cầu:**
   - Web Server nhận request từ Web Browser và xác định hành động cần thực hiện.
   - Nếu yêu cầu này là một request tĩnh (static request) như tải hình ảnh hoặc CSS, Web Server sẽ trả về ngay lập tức mà không cần truy cập Database.
   - Nếu yêu cầu này là request động (dynamic request), ví dụ: người dùng cần xem thông tin chi tiết của một sản phẩm, Web Server sẽ cần xử lý thêm logic và truy cập Database để lấy dữ liệu.

3. **Web Server gửi yêu cầu đến Database:**
   - Web Server sẽ gửi một **truy vấn (query)** đến Database (ví dụ: "SELECT * FROM products WHERE id = 123") để lấy dữ liệu về sản phẩm mà người dùng yêu cầu.
   - Database xử lý truy vấn, lấy dữ liệu tương ứng và trả kết quả về cho Web Server.

4. **Web Server xử lý dữ liệu và tạo phản hồi:**
   - Web Server nhận dữ liệu từ Database và sử dụng nó để tạo ra nội dung HTML hoặc JSON tùy thuộc vào loại request.
   - Web Server có thể sử dụng các công nghệ như JSP, PHP, hoặc template engines (như Thymeleaf, Mustache) để tạo ra nội dung động và định dạng dữ liệu theo yêu cầu của Web Browser.

5. **Web Server gửi phản hồi (Response) về Web Browser:**
   - Web Server gửi phản hồi HTTP trở lại cho Web Browser.
   - Phản hồi này có thể chứa mã HTML, JSON, hoặc các tài nguyên khác (hình ảnh, video, v.v.) mà Web Browser yêu cầu.

6. **Web Browser hiển thị kết quả:**
   - Web Browser nhận phản hồi từ Web Server và hiển thị nội dung lên giao diện người dùng.
   - Nếu là JSON hoặc dữ liệu động, Web Browser có thể sử dụng JavaScript để hiển thị dữ liệu mà không cần tải lại toàn bộ trang (sử dụng AJAX, Fetch API).

### 4. **Ví dụ cụ thể về sự tương tác:**
Giả sử bạn truy cập vào một trang web bán hàng và tìm kiếm sản phẩm "Laptop":

1. **Bước 1:** Web Browser gửi yêu cầu `GET /search?query=laptop` đến Web Server.
2. **Bước 2:** Web Server nhận yêu cầu và kiểm tra thông tin tìm kiếm `query=laptop`.
3. **Bước 3:** Web Server gửi một truy vấn SQL đến Database, chẳng hạn: `SELECT * FROM products WHERE name LIKE '%laptop%'`.
4. **Bước 4:** Database xử lý truy vấn và trả về danh sách sản phẩm liên quan đến "laptop".
5. **Bước 5:** Web Server nhận kết quả và sử dụng một template HTML hoặc JSON để tạo nội dung hiển thị.
6. **Bước 6:** Web Server gửi phản hồi chứa danh sách sản phẩm về cho Web Browser.
7. **Bước 7:** Web Browser hiển thị danh sách sản phẩm cho người dùng thấy trên trang web.

### **Tóm tắt:**
- **Web Browser** là giao diện người dùng, nhận yêu cầu và hiển thị kết quả.
- **Web Server** là nơi xử lý logic nghiệp vụ, xác định hành động, và tạo ra phản hồi.
- **Database** là nơi lưu trữ dữ liệu và cung cấp dữ liệu theo yêu cầu của Web Server.

Ba thành phần này hoạt động đồng bộ với nhau, đảm bảo dữ liệu được truyền tải chính xác và giao diện người dùng phản ánh đúng trạng thái của hệ thống.
