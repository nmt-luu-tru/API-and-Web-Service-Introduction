https://(fu.)udemy.com/course/api-and-web-service-introduction/learn/lecture/16743170#overview  
# Webhooks: Khái niệm và Cách Hoạt Động

Webhooks là một khái niệm phổ biến trong việc kết nối và tích hợp các ứng dụng thông qua internet. Chúng được sử dụng rộng rãi để tự động hóa các quy trình và cung cấp thông báo theo thời gian thực khi có sự kiện xảy ra. Hãy cùng tìm hiểu về webhooks và cách chúng hoạt động.

## Webhooks là gì?

Webhooks là sự kết hợp của hai từ: **web** và **hook**.

- **Web**: Ở đây đại diện cho web service, là một dịch vụ cung cấp giao tiếp qua internet, sử dụng giao thức HTTP.
- **Hook**: Nghĩa là "móc nối" hay kết nối với một sự kiện cụ thể.

Do đó, **webhook** có thể hiểu là một dịch vụ web được kích hoạt khi có sự kiện cụ thể xảy ra, chẳng hạn như:
- Thanh toán hoàn tất.
- Một chuyến bay bị trì hoãn.
- Một gói hàng đang được giao.
- Đăng nhập bất thường vào tài khoản của bạn.
- Giá sản phẩm bạn quan tâm giảm xuống dưới 100 USD.

### Cách Hoạt Động của Webhooks

Webhooks thường được gọi là "Reverse API" hay "API ngược". Điều này có nghĩa là thay vì bạn gửi yêu cầu đến một API và nhận phản hồi, thì với webhooks, chính API sẽ gửi yêu cầu đến bạn khi một sự kiện xảy ra.

#### Ví dụ Minh Họa:

1. **Sự kiện**: Bạn đăng nhập vào tài khoản ngân hàng của mình từ một địa chỉ IP bất thường.
2. **Kích hoạt webhook**: Ngân hàng nhận thấy sự đăng nhập bất thường này và lập tức kích hoạt webhook để gửi thông báo đến điện thoại của bạn.
3. **Gửi yêu cầu HTTP**: Ngân hàng gửi một yêu cầu HTTP đến API trên điện thoại của bạn để tạo ra một tin nhắn thông báo rằng có một đăng nhập bất thường.
4. **Nhận phản hồi**: API trên điện thoại của bạn gửi lại phản hồi cho ngân hàng để xác nhận rằng thông báo đã được gửi thành công.

Webhooks hoạt động dựa trên giao thức HTTP để gửi thông báo theo thời gian thực khi một sự kiện xảy ra. Đây là sự khác biệt với cách sử dụng API thông thường, nơi bạn phải tự gửi yêu cầu để lấy dữ liệu.

### Các Thành Phần Cơ Bản của Webhook

1. **Sự kiện**: Một hành động hoặc thay đổi trạng thái kích hoạt webhook. Ví dụ, một đơn hàng hoàn tất, một người dùng đăng ký mới, hoặc một lỗi thanh toán xảy ra.
   
2. **Endpoint (Điểm cuối)**: Là URL mà bạn cấu hình để webhook gửi thông báo đến. Đây có thể là URL của một server hoặc một địa chỉ IP trên mạng của bạn.

3. **Payload (Nội dung)**: Dữ liệu được gửi đến endpoint khi sự kiện xảy ra. Thường thì payload sẽ ở dạng JSON chứa các thông tin chi tiết về sự kiện.

4. **Response (Phản hồi)**: Khi endpoint nhận được yêu cầu HTTP từ webhook, nó có thể gửi phản hồi lại để xác nhận hoặc xử lý dữ liệu.

### Ví Dụ Thực Tế của Webhooks

#### 1. Thông báo đăng nhập bất thường vào tài khoản ngân hàng

Giả sử bạn đăng nhập vào tài khoản ngân hàng từ một địa chỉ IP bất thường, ngân hàng sẽ kích hoạt webhook gửi thông báo đến điện thoại hoặc email của bạn. Điều này giúp bạn biết rằng có một hành động đáng ngờ đang diễn ra và có thể bảo vệ tài khoản của mình.

- **Sự kiện**: Đăng nhập bất thường.
- **Payload**: Địa chỉ IP đăng nhập, thời gian, vị trí đăng nhập.
- **Endpoint**: API trên điện thoại di động hoặc địa chỉ email của bạn.
- **Response**: Xác nhận đã nhận thông báo.

#### 2. Thông báo cập nhật trạng thái đơn hàng

Khi một đơn hàng trên trang thương mại điện tử của bạn chuyển sang trạng thái "Đã giao hàng", webhook có thể gửi thông báo đến hệ thống quản lý kho hoặc khách hàng.

- **Sự kiện**: Đơn hàng chuyển trạng thái "Đã giao hàng".
- **Payload**: ID đơn hàng, thời gian giao hàng, thông tin khách hàng.
- **Endpoint**: URL của hệ thống quản lý kho hoặc địa chỉ email khách hàng.
- **Response**: Xác nhận đã nhận thông báo.

### So Sánh Webhooks với API Thông Thường

#### API Thông Thường:

- Hoạt động theo mô hình **yêu cầu - phản hồi**. Người dùng gửi yêu cầu (request) và nhận lại phản hồi (response).
- Người dùng phải chủ động gửi yêu cầu để lấy dữ liệu.

#### Webhooks:

- Hoạt động theo mô hình **sự kiện - phản hồi**. Khi một sự kiện xảy ra, hệ thống tự động gửi yêu cầu đến endpoint mà không cần sự chủ động từ người dùng.
- Dữ liệu được gửi đi theo thời gian thực khi sự kiện xảy ra.

### Tại Sao Sử Dụng Webhooks?

- **Tiết kiệm tài nguyên**: Không cần liên tục kiểm tra (polling) trạng thái của hệ thống bằng các yêu cầu API, từ đó giảm tải cho hệ thống.
- **Phản hồi theo thời gian thực**: Webhooks giúp bạn nhận được thông tin ngay lập tức khi sự kiện xảy ra mà không cần đợi.
- **Dễ dàng tích hợp**: Webhooks giúp kết nối các hệ thống khác nhau với nhau mà không cần viết thêm nhiều mã nguồn phức tạp.

### Cách Thiết Lập Webhook

1. **Tạo Endpoint**: Xây dựng một URL để tiếp nhận các yêu cầu từ webhook. Ví dụ, bạn có thể sử dụng một server với Node.js hoặc PHP để xử lý.
2. **Cấu hình Webhook trên hệ thống**: Thêm URL của endpoint vào hệ thống quản lý webhook của dịch vụ mà bạn muốn theo dõi (ví dụ: Stripe, Shopify, GitHub).
3. **Xử lý Payload**: Khi nhận được thông báo, kiểm tra nội dung payload và thực hiện hành động tương ứng (lưu vào cơ sở dữ liệu, gửi email, kích hoạt quy trình nội bộ).
4. **Gửi Phản Hồi (Response)**: Xác nhận rằng bạn đã nhận thông báo thành công bằng cách gửi phản hồi HTTP 200 OK trở lại webhook.

## Tổng kết

Webhooks là một công cụ mạnh mẽ để tự động hóa và tích hợp các ứng dụng thông qua sự kiện thời gian thực. Chúng giúp hệ thống của bạn phản ứng nhanh chóng với những thay đổi mà không cần liên tục kiểm tra dữ liệu. Điều này giúp tiết kiệm tài nguyên và mang lại trải nghiệm người dùng tốt hơn.
