https://(fu.)udemy.com/course/api-and-web-service-introduction/learn/lecture/13689018#overview  
### Giới Thiệu về **Digest Authentication**

**Digest Authentication** là một phương thức xác thực nâng cao được sử dụng để bảo mật thông tin đăng nhập khi bạn muốn truy cập vào các tài nguyên bảo vệ trên web hoặc API. Thay vì gửi trực tiếp **username** và **password** như phương thức **Basic Authentication**, **Digest Authentication** sử dụng một **digest** để mã hóa thông tin đăng nhập. Điều này giúp bảo vệ thông tin tốt hơn khi truyền tải qua Internet.

### Nguyên Tắc Hoạt Động của **Digest Authentication**

1. **Gửi yêu cầu ban đầu**: Khi bạn cố gắng truy cập vào một tài nguyên cần bảo mật, máy chủ (server) sẽ trả về một thông báo **401 Unauthorized** kèm theo một thông điệp yêu cầu xác thực (`WWW-Authenticate: Digest`). Thông điệp này chứa các thông tin như:
   - **Realm**: Môi trường xác thực, ví dụ như tên miền.
   - **Nonce**: Một giá trị ngẫu nhiên chỉ được sử dụng một lần.
   - **Qop**: Chất lượng bảo vệ (Quality of Protection).
   - **Algorithm**: Thuật toán băm được sử dụng, ví dụ `MD5`.

2. **Tạo Digest**: Dựa vào các thông tin từ thông điệp phản hồi của máy chủ, máy khách (client) sẽ tạo một chuỗi **digest**. Chuỗi này bao gồm:
   - **Username** và **Password** đã được mã hóa.
   - **Nonce** (giá trị ngẫu nhiên) mà máy chủ đã cung cấp.
   - **URI** của tài nguyên đang yêu cầu.
   - **Method** của yêu cầu HTTP, ví dụ như `GET` hoặc `POST`.
   
   Các thông tin trên sẽ được kết hợp và băm lại bằng thuật toán (thường là MD5) để tạo ra một **digest** hợp lệ.

3. **Gửi lại yêu cầu với Digest**: Máy khách gửi lại yêu cầu cùng với thông tin **Authorization Header** chứa **digest** đã tạo. Dạng tiêu đề này như sau:

   ```
   Authorization: Digest username="user", realm="example.com", nonce="5b5f...b4e2", uri="/data", response="6c1d...35a7"
   ```
   
   Trong đó:
   - **username**: Tên đăng nhập của người dùng.
   - **realm**: Môi trường xác thực.
   - **nonce**: Giá trị nonce từ máy chủ.
   - **uri**: Đường dẫn của tài nguyên đang truy cập.
   - **response**: Chuỗi digest đã mã hóa.

4. **Máy chủ kiểm tra Digest**: Máy chủ nhận được yêu cầu và sử dụng các thông tin như **nonce**, **uri**, **username**, và **password** đã lưu trữ để tạo một **digest** giống như của máy khách. Nếu hai chuỗi **digest** này trùng khớp, máy chủ sẽ xác nhận rằng người dùng có quyền truy cập vào tài nguyên và trả lại tài nguyên yêu cầu với mã trạng thái **200 OK**.

### Ví Dụ Cụ Thể với **Postman**

#### Bước 1: Truy cập API mà không có xác thực

Giả sử bạn muốn truy cập vào API `https://postman-echo.com/get` mà không có thông tin xác thực. Bạn gửi yêu cầu **GET** đến API và nhận được mã phản hồi:

```
HTTP/1.1 401 Unauthorized
```

Điều này có nghĩa là máy chủ yêu cầu xác thực bằng **Digest Authentication**.

#### Bước 2: Tạo và gửi Digest với thông tin xác thực

Trong **Postman**, bạn chọn tab **Authorization** và chọn loại xác thực là **Digest Auth**. Sau đó, điền thông tin **username** và **password** vào các trường tương ứng, ví dụ:

- **Username**: `postman`
- **Password**: `password`

Nhấn **Send**, và bạn sẽ thấy rằng yêu cầu đã được chấp nhận với mã phản hồi:

```
HTTP/1.1 200 OK
```

Điều này chứng tỏ bạn đã xác thực thành công và truy cập được tài nguyên yêu cầu.

### Ưu Điểm của **Digest Authentication**

1. **Bảo mật tốt hơn so với Basic Authentication**: Với **Digest Authentication**, thông tin đăng nhập không được gửi trực tiếp mà được băm bằng thuật toán như **MD5**. Điều này giúp hạn chế việc thông tin đăng nhập bị đánh cắp nếu có kẻ xấu theo dõi gói tin (packet sniffing).

2. **Sử dụng giá trị nonce**: `Nonce` là một giá trị ngẫu nhiên chỉ sử dụng một lần. Điều này giúp ngăn chặn các cuộc tấn công lặp lại (replay attack), nơi mà kẻ tấn công có thể gửi lại yêu cầu cũ để truy cập tài nguyên mà không cần biết thông tin đăng nhập.

### Hạn Chế của **Digest Authentication**

1. **Dễ bị tấn công nếu mật khẩu yếu**: Nếu mật khẩu được chọn quá yếu, kẻ tấn công có thể sử dụng kỹ thuật brute-force để tìm ra mật khẩu.

2. **Bị lỗi thời**: Mặc dù tốt hơn so với **Basic Authentication**, nhưng **Digest Authentication** không còn phổ biến như trước. Các phương thức bảo mật hiện đại hơn như **OAuth 2.0** hoặc **JWT** đã thay thế phần lớn nhu cầu sử dụng **Digest Authentication**.

3. **Không hỗ trợ nhiều loại mã hóa**: **Digest Authentication** chủ yếu sử dụng thuật toán **MD5**, vốn đã được chứng minh là có nhiều lỗ hổng bảo mật. Nếu thuật toán này bị phá vỡ, thông tin xác thực có thể bị đánh cắp.

### Tổng Kết

**Digest Authentication** cung cấp một phương thức xác thực bảo mật hơn so với **Basic Authentication** bằng cách sử dụng **digest** thay cho việc gửi trực tiếp **username** và **password**. Tuy nhiên, với sự ra đời của các phương thức xác thực tiên tiến hơn, nó dần trở nên ít được sử dụng và chỉ nên áp dụng trong các hệ thống không yêu cầu mức độ bảo mật cao.
