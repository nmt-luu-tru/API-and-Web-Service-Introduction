https://(fu.)udemy.com/course/api-and-web-service-introduction/learn/lecture/13659940#overview
### Khái Niệm và Cách Thức Hoạt Động của **Basic Authentication**

**Basic Authentication** là một phương thức xác thực đơn giản trong môi trường web, nơi mà người dùng phải cung cấp **tên đăng nhập** (username) và **mật khẩu** (password) để chứng minh danh tính của mình. Cách thức này được gọi là "basic" vì tính đơn giản của nó so với các phương thức xác thực khác như **OAuth** hoặc **JWT**.

### Cách Hoạt Động của **Basic Authentication**

Khi bạn muốn truy cập vào một **API** hoặc một **web server** nào đó yêu cầu xác thực, bạn cần gửi thông tin **username** và **password** của mình qua một tiêu đề (**header**) đặc biệt trong yêu cầu (**request**) HTTP. Thông tin này sẽ được mã hóa theo dạng **Base64** trước khi gửi đi. Dưới đây là cách mà **Basic Authentication** hoạt động chi tiết:

1. **Gửi yêu cầu (request)**: Khi bạn gửi một yêu cầu đến một server yêu cầu **Basic Authentication**, server sẽ trả lại mã phản hồi (response) với mã trạng thái **401 Unauthorized**. Điều này có nghĩa là bạn chưa cung cấp thông tin xác thực hoặc thông tin xác thực không hợp lệ.

2. **Cung cấp thông tin xác thực**: Bạn cần gửi lại yêu cầu của mình với thông tin **username** và **password** được đính kèm trong phần **Authorization Header** của yêu cầu HTTP. Phần **header** này có định dạng như sau:

   ```
   Authorization: Basic <base64_encoded_username_and_password>
   ```
   
   Ví dụ: Nếu **username** là `user` và **password** là `pass`, thì phần **header** sẽ được mã hóa thành:

   ```
   Authorization: Basic dXNlcjpwYXNz
   ```
   
   Ở đây, `dXNlcjpwYXNz` là chuỗi ký tự được mã hóa theo chuẩn **Base64** của `user:pass`.

3. **Xác thực và phản hồi**: Server sẽ kiểm tra thông tin **username** và **password** đã được mã hóa. Nếu thông tin hợp lệ, server sẽ cho phép bạn truy cập và gửi lại tài nguyên (**resource**) mà bạn yêu cầu. Nếu không, bạn sẽ nhận được mã trạng thái **401 Unauthorized** kèm theo thông báo lỗi.

### Ví Dụ Cụ Thể về **Basic Authentication**

Giả sử bạn có một API tại địa chỉ `https://api.example.com/data` và server yêu cầu xác thực với **Basic Authentication**. Bạn có thể gửi yêu cầu xác thực bằng cách sử dụng công cụ như **Postman** hoặc cURL:

#### Sử Dụng Postman

1. Mở Postman và tạo một **request** mới.
2. Chọn phương thức **GET** và nhập URL `https://api.example.com/data`.
3. Chuyển đến tab **Authorization** và chọn loại xác thực **Basic Auth**.
4. Nhập **username** và **password** của bạn.
5. Nhấn **Send** để gửi yêu cầu.

Nếu thông tin xác thực đúng, bạn sẽ nhận được phản hồi với mã trạng thái **200 OK** cùng với dữ liệu mà bạn yêu cầu.

#### Sử Dụng cURL

Bạn cũng có thể sử dụng lệnh cURL từ dòng lệnh như sau:

```bash
curl -u username:password https://api.example.com/data
```

Trong lệnh trên, cURL sẽ tự động thêm phần **Authorization Header** với thông tin xác thực đã được mã hóa theo chuẩn **Base64**.

### Lợi Ích và Hạn Chế của **Basic Authentication**

#### Lợi Ích
- **Dễ triển khai**: Vì chỉ cần cung cấp **username** và **password**, không yêu cầu cấu hình phức tạp.
- **Hỗ trợ rộng rãi**: Hầu hết các máy chủ web và API đều hỗ trợ **Basic Authentication**.

#### Hạn Chế
- **Bảo mật thấp**: Thông tin xác thực được mã hóa bằng **Base64**, nhưng **Base64** chỉ là một phương thức mã hóa, không phải là phương thức bảo mật. Thông tin có thể dễ dàng được giải mã và đánh cắp.
- **Nguy cơ bị tấn công**: Việc gửi **username** và **password** qua Internet, dù đã được mã hóa theo chuẩn **Base64**, vẫn dễ bị tấn công kiểu **Man-in-the-Middle** nếu không sử dụng **HTTPS**.

### Cách Bảo Mật Khi Sử Dụng **Basic Authentication**

Để tăng cường bảo mật khi sử dụng **Basic Authentication**, bạn cần tuân thủ các nguyên tắc sau:

1. **Sử dụng HTTPS**: HTTPS mã hóa toàn bộ kết nối giữa máy khách (client) và máy chủ (server), đảm bảo rằng thông tin **username** và **password** của bạn được bảo mật trong quá trình truyền tải.
   
2. **Hạn chế quyền truy cập**: Chỉ sử dụng **Basic Authentication** cho các tài nguyên không quan trọng hoặc các tài nguyên chỉ dành cho người dùng nội bộ.

3. **Sử dụng thêm các phương thức xác thực khác**: Kết hợp **Basic Authentication** với các phương thức xác thực khác như **OAuth** hoặc **JWT** để tăng cường bảo mật.

### Tổng Kết

**Basic Authentication** là một phương thức xác thực đơn giản và dễ triển khai nhưng lại có nhiều lỗ hổng bảo mật. Do đó, nó thường được sử dụng trong các trường hợp không yêu cầu bảo mật cao hoặc làm nền tảng cho các phương thức xác thực khác. Để sử dụng an toàn, bạn nên luôn kết hợp với **HTTPS** và cân nhắc việc chuyển sang các phương thức xác thực an toàn hơn như **OAuth 2.0** hoặc **JWT**.
