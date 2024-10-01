https://(fu.)udemy.com/course/api-and-web-service-introduction/learn/lecture/18545180#overview
# Tạo API với Amazon Web Services (AWS)

Trong bài giảng này, chúng ta sẽ tìm hiểu về cách tạo API sử dụng Amazon Web Services (AWS). Bài giảng bao gồm các khái niệm cơ bản về điện toán đám mây, ảo hóa, các dịch vụ AWS, và hướng dẫn từng bước tạo API bằng công cụ **API Gateway** của AWS.

## Amazon Web Services là gì?

**Amazon Web Services** (AWS) là một nền tảng cung cấp dịch vụ điện toán đám mây, cho phép bạn thực hiện các tác vụ tính toán mà không cần phải có phần cứng riêng. Tất cả các quá trình xử lý, từ phần cứng, hệ điều hành đến phần mềm, đều được thực hiện trên nền tảng đám mây của Amazon, giúp tiết kiệm chi phí và dễ dàng mở rộng.

- **Cloud** ở đây nghĩa là toàn bộ các quá trình xử lý và lưu trữ dữ liệu đều diễn ra trên internet. Bạn không cần đầu tư phần cứng hay cơ sở hạ tầng vật lý tại chỗ.
- **Ưu điểm của điện toán đám mây**:
  - **Chi phí cố định**: Bạn có thể thanh toán một khoản phí cố định hàng tháng và không phải lo lắng về việc vượt quá giới hạn chi phí.
  - **Tính linh hoạt và mở rộng**: Dễ dàng thêm tài nguyên như máy chủ mới mà không cần phải triển khai phần cứng phức tạp.

Ví dụ: Khi cần thêm 100 máy chủ mới, các nhà cung cấp dịch vụ đám mây có thể dễ dàng bổ sung tài nguyên này, trong khi đó nếu bạn tự triển khai, chi phí và thời gian sẽ rất lớn.

## Ảo hóa là gì?

**Ảo hóa** (Virtualization) là việc tách biệt phần cứng khỏi hệ điều hành. Trong ảo hóa, một phần cứng vật lý có thể chạy nhiều hệ điều hành khác nhau thông qua một công cụ gọi là **hypervisor**.

- **Type 1 Hypervisor**: Là hypervisor được cài đặt trực tiếp trên phần cứng. Ví dụ, bạn có thể chạy đồng thời hệ điều hành Windows và Linux trên một máy chủ.
- **Type 2 Hypervisor**: Là hypervisor được cài đặt trên một hệ điều hành hiện có. Ví dụ, bạn cài đặt Windows trên máy tính Mac thông qua một hypervisor như VMware hoặc VirtualBox.

## Dịch vụ API Gateway của AWS

API Gateway là một dịch vụ của AWS cho phép bạn xây dựng, triển khai và quản lý các API. Với API Gateway, bạn có thể tạo các loại API khác nhau như REST API, HTTP API và WebSocket API.

- **REST API**: Sử dụng phổ biến cho các giao tiếp giữa máy chủ và máy khách thông qua giao thức HTTP.
- **HTTP API**: Tương tự như REST API nhưng tối ưu hơn về độ trễ và chi phí.
- **WebSocket API**: Cho phép duy trì kết nối hai chiều liên tục giữa máy khách và máy chủ. Phù hợp với các ứng dụng thời gian thực như chơi game hoặc nhắn tin.

### Bắt đầu với Amazon API Gateway

1. **Tạo tài khoản AWS**:
   - Truy cập trang [Amazon Web Services](https://aws.amazon.com), nhấn vào nút "Create an AWS Account".
   - Điền thông tin tài khoản (email, mật khẩu) và chọn loại tài khoản "Personal".
   - Cung cấp thông tin thanh toán (thẻ tín dụng). AWS có gói miễn phí cho người dùng mới và bạn có thể xóa tài khoản sau khi hoàn tất để tránh bị tính phí.

2. **Truy cập API Gateway**:
   - Sau khi đăng nhập vào AWS Management Console, tìm kiếm và chọn **API Gateway** trong danh sách các dịch vụ.
   - Chọn "Build" để bắt đầu tạo API đầu tiên.

### Tạo REST API trong AWS

1. **Chọn loại API**: REST API.
2. **Đặt tên cho API**: Ví dụ "Pizza API".
3. **Tạo tài nguyên (resource)**:
   - Tạo tài nguyên chính (ví dụ: `/pizza`) để quản lý đơn hàng pizza.
   - Tạo các phương thức cho tài nguyên: `GET`, `POST` để lấy thông tin hoặc tạo đơn hàng mới.

### Tạo Lambda Function để xử lý API

AWS cung cấp một dịch vụ gọi là **Lambda** để chạy mã nguồn mà không cần quản lý máy chủ. Lambda function sẽ được sử dụng để xử lý các yêu cầu từ API.

1. **Tạo Lambda function**:
   - Chọn ngôn ngữ lập trình (ví dụ: Node.js).
   - Đặt tên cho Lambda (ví dụ: `PizzaGetFunction` để lấy thông tin đơn hàng và `PizzaPostFunction` để tạo đơn hàng).
2. **Viết mã xử lý**: Mã nguồn sẽ thực hiện truy vấn thông tin từ cơ sở dữ liệu (DynamoDB) hoặc tạo mới đơn hàng trong bảng `Pizza`.

### Kết nối Lambda với API Gateway

- Chọn API Gateway là trigger (bộ kích hoạt) cho Lambda function.
- Cấu hình phương thức `GET` để lấy thông tin từ cơ sở dữ liệu và `POST` để tạo đơn hàng mới.
- Kiểm tra bằng cách gửi yêu cầu từ API Gateway và quan sát kết quả trả về từ Lambda function.

## Tạo cơ sở dữ liệu NoSQL với DynamoDB

1. **Tạo bảng DynamoDB**:
   - Đặt tên bảng là `Pizza` với khóa chính là `OrderID`.
   - Thêm một số cột như `Size` và `Topping`.
2. **Thêm dữ liệu vào bảng**: Thêm các bản ghi với thông tin đơn hàng như `OrderID=1`, `Size=Small`, `Topping=Onions`.

## Kiểm tra API với Postman

1. **Nhập Swagger file vào Postman**:
   - AWS API Gateway hỗ trợ xuất API thành file Swagger. File này có thể được nhập vào Postman để kiểm thử.
2. **Gửi yêu cầu `GET`** để lấy thông tin đơn hàng:
   - Ví dụ: `/pizza/1` để lấy thông tin đơn hàng có `OrderID=1`.
3. **Gửi yêu cầu `POST`** để tạo đơn hàng mới:
   - Gửi yêu cầu với nội dung JSON như `{"OrderID": "13", "Size": "Large", "Topping": "Pineapple"}`.

## Triển khai và xóa tài khoản AWS

Sau khi hoàn tất tạo API, bạn cần triển khai (deploy) API để nó có thể được truy cập từ bên ngoài. Nếu bạn chỉ muốn thực hành mà không sử dụng thực tế, bạn có thể xóa tài khoản AWS để tránh bị tính phí không mong muốn.

## Kết luận

Trong bài giảng này, chúng ta đã đi qua quy trình chi tiết từ việc tạo tài khoản AWS, cấu hình API Gateway, tạo Lambda function, kết nối với cơ sở dữ liệu DynamoDB và kiểm thử API trên Postman. Việc sử dụng API Gateway và Lambda giúp bạn xây dựng các API mạnh mẽ mà không cần lo lắng về cơ sở hạ tầng hay máy chủ.
