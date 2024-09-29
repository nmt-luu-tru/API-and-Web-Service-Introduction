https://(fu.)udemy.com/course/api-and-web-service-introduction/learn/lecture/13705026#overview  
### Tìm Hiểu Về **Bearer Token**

**Bearer Token** là một thuật ngữ quan trọng khi làm việc với API, đặc biệt là trong các ứng dụng xác thực và ủy quyền hiện đại. Để hiểu rõ hơn về **Bearer Token**, chúng ta sẽ phân tích từng phần của cụm từ này.

### 1. **Giải Nghĩa Cụm Từ "Bearer Token"**

- **Bearer**: Trong ngữ cảnh này, từ "bearer" có nghĩa là người nắm giữ hoặc sở hữu. Ví dụ, bạn có thể là người sở hữu một chiếc vé xem phim, vé đó cho phép bạn vào rạp chiếu phim. Tương tự, một người nắm giữ token sẽ có quyền truy cập vào tài nguyên của API.
  
- **Token**: Token là một chuỗi ký tự được sử dụng để truy cập vào tài nguyên hoặc dịch vụ. Token có thể coi là một dạng giấy thông hành, chứng thực rằng bạn có quyền thực hiện một hành động hoặc truy cập vào một tài nguyên nhất định.

Khi ghép lại, **Bearer Token** là một loại mã thông báo (token) mà bất kỳ ai nắm giữ đều có thể sử dụng nó để truy cập vào các tài nguyên mà token đó được cấp quyền, không phân biệt người sử dụng.

### 2. **Nguồn Gốc và Cách Hoạt Động Của Bearer Token**

**Bearer Token** xuất phát từ tiêu chuẩn **OAuth 2.0**, được quy định trong tài liệu RFC 6750. Nó được tạo ra như một phương thức xác thực đơn giản và hiệu quả để sử dụng trong việc gọi API. **Bearer Token** cho phép ứng dụng client (máy khách) truy cập vào tài nguyên mà không cần gửi lại thông tin đăng nhập như **username** hay **password** mỗi lần yêu cầu.

### 3. **Cách Sử Dụng Bearer Token**

Khi một **Bearer Token** được tạo ra và cấp cho client, client có thể gửi token này kèm theo các yêu cầu HTTP để chứng minh quyền truy cập của mình. Cụ thể:

1. **Tạo Bearer Token**: Máy khách nhận được token sau khi hoàn tất quá trình xác thực, ví dụ qua quy trình **OAuth 2.0**.
2. **Gửi Bearer Token**: Client gửi yêu cầu đến API bằng cách đính kèm token vào tiêu đề (header) của yêu cầu HTTP:
   
   ```
   Authorization: Bearer {token_value}
   ```

   Ví dụ:

   ```
   Authorization: Bearer abc123xyz456
   ```

3. **Xác Minh Bearer Token**: API nhận được yêu cầu, kiểm tra token và xác định xem token có hợp lệ không, có quyền truy cập tài nguyên không, và nếu hợp lệ thì sẽ cung cấp tài nguyên tương ứng.

### 4. **Ví Dụ Sử Dụng Bearer Token với Postman**

Giả sử bạn muốn kiểm tra Bearer Token với một API giả lập, bạn có thể sử dụng Postman như sau:

1. **Bước 1**: Truy cập vào `https://httpbin.org/bearer` mà không đính kèm token. API sẽ trả về phản hồi với mã trạng thái:

   ```
   HTTP/1.1 401 Unauthorized
   ```

   Điều này có nghĩa là bạn không có quyền truy cập do chưa cung cấp token.

2. **Bước 2**: Trong Postman, chọn tab **Authorization**, sau đó chọn kiểu xác thực **Bearer Token** và nhập giá trị token, ví dụ `secretpassword`.

3. **Bước 3**: Nhấn **Send** để gửi yêu cầu đến API. Kết quả sẽ là phản hồi với mã trạng thái:

   ```
   HTTP/1.1 200 OK
   ```

   Điều này cho thấy bạn đã xác thực thành công và có quyền truy cập vào tài nguyên.

### 5. **Ưu Điểm và Nhược Điểm Của Bearer Token**

#### Ưu Điểm:

- **Dễ Sử Dụng**: **Bearer Token** chỉ cần đính kèm vào tiêu đề yêu cầu HTTP mà không cần gửi lại thông tin đăng nhập như **username** hay **password**.
- **Tăng Bảo Mật**: Token có thể được tạo ra với thời hạn sử dụng nhất định, giúp giảm nguy cơ bị tấn công nếu token bị lộ.

#### Nhược Điểm:

- **Không Ràng Buộc Người Sử Dụng**: Bất kỳ ai sở hữu token đều có thể truy cập vào tài nguyên, điều này dẫn đến rủi ro bảo mật nếu token bị đánh cắp.
- **Cần Sử Dụng HTTPS**: Để bảo vệ token trong quá trình truyền tải, bạn cần đảm bảo sử dụng **HTTPS** thay vì **HTTP**. HTTPS mã hóa thông tin trong quá trình truyền, giúp ngăn chặn việc đánh cắp token.

### 6. **Ví Dụ Về Tình Huống Nguy Hiểm Khi Sử Dụng Bearer Token**

Giả sử bạn có một Bearer Token cho phép truy cập vào dữ liệu tài chính của công ty. Nếu bạn gửi token này qua kết nối HTTP thay vì HTTPS, kẻ tấn công có thể dễ dàng đánh cắp token của bạn thông qua kỹ thuật nghe trộm gói tin (packet sniffing). Khi đó, bất kỳ ai sở hữu token này đều có thể truy cập vào dữ liệu của công ty mà không cần xác minh thêm bất kỳ thông tin nào.

### 7. **Cách Bảo Vệ Bearer Token**

Để đảm bảo an toàn khi sử dụng Bearer Token, bạn cần tuân thủ các quy tắc sau:

1. **Sử Dụng HTTPS**: Luôn sử dụng HTTPS để truyền tải token nhằm bảo vệ chúng khỏi các cuộc tấn công nghe lén.
2. **Giới Hạn Thời Gian Sử Dụng**: Tạo ra các token có thời hạn ngắn và sử dụng **refresh token** để cấp lại quyền truy cập khi cần.
3. **Bảo Mật Token Trong Quá Trình Lưu Trữ**: Không lưu trữ token ở những nơi dễ truy cập như local storage của trình duyệt hoặc trong mã nguồn.

### 8. **Tổng Kết**

**Bearer Token** là một phương thức xác thực đơn giản và hiệu quả cho phép truy cập vào các API mà không cần gửi thông tin đăng nhập mỗi lần thực hiện yêu cầu. Tuy nhiên, do đặc tính "ai nắm giữ cũng có quyền" của nó, cần phải có những biện pháp bảo vệ cẩn thận khi sử dụng Bearer Token để tránh rủi ro bảo mật.

Khi bạn hiểu rõ về cách thức hoạt động và cách sử dụng **Bearer Token**, bạn sẽ có thể thiết lập và quản lý hệ thống xác thực của mình một cách an toàn và hiệu quả hơn.
