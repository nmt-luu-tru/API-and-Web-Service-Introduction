https://(fu.)udemy.com/course/api-and-web-service-introduction/learn/lecture/13748536#overview  
# OAuth là gì?

**OAuth** là một phương pháp ủy quyền cho phép bạn không cần trực tiếp truy cập vào API mà giao trách nhiệm này cho một ứng dụng khác để tương tác với API thay bạn.

## Cách thức hoạt động của OAuth

Khi bạn muốn gọi một API, bình thường bạn phải trực tiếp kết nối với API đó. Ví dụ, nếu bạn muốn tìm đường đi bằng ứng dụng Waze, Waze sẽ cung cấp chỉ dẫn trên điện thoại của bạn. Điều này có nghĩa là bạn đang gọi một chương trình cụ thể của Waze trên máy chủ của Waze thông qua giao thức HTTP, bằng cách cung cấp vị trí của bạn. Máy chủ Waze sẽ xử lý thông tin và trả về chỉ dẫn phù hợp với vị trí của bạn. 

Việc tương tác trực tiếp với API như vậy rất phức tạp và đòi hỏi bạn phải thiết lập nhiều thứ. OAuth xuất hiện nhằm giảm bớt công việc này bằng cách cho phép một ứng dụng trung gian (thường gọi là app) thực hiện việc kết nối với API thay bạn. Ứng dụng này sẽ lấy vị trí của bạn và thực hiện yêu cầu đến máy chủ Waze để lấy chỉ dẫn, rồi trả kết quả lại cho bạn.

Ví dụ:

- Bạn có thể tải xuống ứng dụng Waze trên điện thoại di động và ứng dụng này sẽ thực hiện mọi công việc tìm đường thay bạn.
- Các ứng dụng khác như Viber, Translate, Pandora cũng hoạt động theo cách tương tự để thực hiện nhắn tin, dịch ngôn ngữ hay phát nhạc.

## Phân biệt OAuth và Basic Authentication

Trong **Basic Authentication**, bạn phải cung cấp tên đăng nhập và mật khẩu trực tiếp cho API. API sẽ trả lại kết quả tương ứng. Tuy nhiên, phương pháp này có rủi ro về bảo mật vì thông tin nhạy cảm của bạn sẽ phải gửi qua mạng.

Trong khi đó, với **OAuth**, bạn không cần phải gửi tên đăng nhập và mật khẩu cho API. Thay vào đó, bạn ủy quyền cho một ứng dụng trung gian tiếp cận API bằng cách sử dụng một mã ủy quyền (authorization code) hoặc mã truy cập (access token). Ứng dụng này sẽ thực hiện việc gọi API và lấy dữ liệu cần thiết thay bạn.

## Ý nghĩa của OAuth

OAuth là từ viết tắt của "Open Authorization". 

- **Open**: có nghĩa là mở, cho phép người khác truy cập.
- **Authorization**: nghĩa là ủy quyền hoặc cấp phép truy cập nhưng chỉ trong phạm vi giới hạn.

Ví dụ, bạn mở cửa nhà để bạn bè đến ăn tối, nhưng bạn không cho phép họ sử dụng máy tính hoặc tắm rửa trong nhà bạn. Tương tự, trong thế giới API, bạn cho phép một ứng dụng truy cập vào một số tài nguyên nhất định mà không cần tiết lộ thông tin nhạy cảm như tên đăng nhập hay mật khẩu.

## Ví dụ sử dụng OAuth với Gmail API

### Bước 1: Tạo một tài khoản Gmail

Trước tiên, bạn sẽ tạo một tài khoản Gmail bằng cách truy cập [accounts.google.com](https://accounts.google.com), chọn "Create Account" và điền các thông tin cần thiết. Sau khi tạo xong tài khoản, bạn có thể đăng nhập và gửi một email thử nghiệm để đảm bảo tài khoản hoạt động bình thường.

### Bước 2: Sử dụng OAuth Playground

Google cung cấp một công cụ gọi là **OAuth Playground** để bạn có thể thử nghiệm OAuth. Bạn sẽ chọn Gmail API và các phương thức liên quan như `insert`, `compose`, `read`, hoặc `send` để tương tác với tài khoản Gmail của mình. Sau đó, bạn phải ủy quyền (authorize) cho ứng dụng bằng cách nhấn vào nút "Authorize APIs". Quá trình này sẽ yêu cầu bạn đăng nhập bằng tài khoản Google mà bạn đã tạo và cho phép ứng dụng truy cập vào các tài nguyên email của bạn.

### Bước 3: Lấy mã truy cập (Access Token)

Khi bạn cấp quyền cho ứng dụng, Google sẽ cung cấp cho bạn một mã ủy quyền (authorization code). Bạn sẽ sử dụng mã này để lấy **Access Token**. Access Token này sẽ hết hạn sau một khoảng thời gian, vì vậy bạn có thể dùng **Refresh Token** để lấy Access Token mới mà không cần phải ủy quyền lại.

### Bước 4: Gửi yêu cầu đến API

Sau khi có Access Token, bạn có thể gửi yêu cầu đến API bằng cách thiết lập một yêu cầu HTTP đến Google với thông tin người dùng và token bạn đã có. Bạn có thể sử dụng các công cụ như **Postman** hoặc viết mã Python để thực hiện yêu cầu này. Ví dụ:

- URL của Gmail API sẽ là: `https://mail.google.com/`
- Bearer Token sẽ được gửi kèm trong phần header của yêu cầu HTTP để xác thực bạn là người được cấp quyền.

### Ví dụ thực hiện với Postman

1. Copy URL của Gmail API và dán vào Postman.
2. Chọn phương thức là **GET**.
3. Thêm Access Token vào phần **Authorization**.
4. Nhấn **Send** và bạn sẽ nhận được phản hồi từ Gmail API với thông tin email của bạn.

## Tại sao OAuth phổ biến?

OAuth được ra mắt vào năm 2006 và hiện nay rất phổ biến vì những ưu điểm vượt trội:
- **Bảo mật cao**: Không yêu cầu tên đăng nhập hay mật khẩu.
- **Tiện lợi**: Cho phép các ứng dụng hoạt động thay bạn, tiết kiệm thời gian và công sức.

Khi bạn muốn tích hợp OAuth vào một dự án mà không có sẵn ứng dụng trung gian, bạn cần phải tạo ra một ứng dụng và sử dụng nó để giao tiếp với API như là một trung gian đại diện cho người dùng.

## Kết luận

OAuth là một phương pháp ủy quyền mở giúp bạn bảo mật hơn khi sử dụng API. Nó cho phép một ứng dụng thực hiện yêu cầu API thay bạn mà không cần tiết lộ thông tin nhạy cảm. Điều này giúp bạn dễ dàng sử dụng các dịch vụ khác nhau như nhắn tin, phát nhạc, hoặc tìm đường mà không phải lo lắng về bảo mật.
