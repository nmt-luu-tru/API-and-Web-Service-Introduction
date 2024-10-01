https://(fu.)udemy.com/course/api-and-web-service-introduction/learn/lecture/15979974#overview  
# Gọi API bằng các ngôn ngữ lập trình

Trong phần này, chúng ta sẽ tìm hiểu cách gọi API bằng các ngôn ngữ lập trình khác nhau. Trước đó, chúng ta đã sử dụng công cụ Postman (một công cụ dựa trên trình duyệt) để thực hiện các yêu cầu API. Nhưng làm thế nào để gọi API bằng mã nguồn trong một ngôn ngữ lập trình cụ thể? Hãy cùng tìm hiểu các phương thức và tài nguyên có sẵn để hỗ trợ việc này.

## Gọi API bằng ngôn ngữ lập trình

Khi bạn muốn gọi một API bằng mã nguồn, bạn cần phải thực hiện các bước như sau:

1. **Chọn ngôn ngữ lập trình**: Bạn có thể sử dụng các ngôn ngữ như JavaScript, Python, Java, C#, PHP, hoặc bất kỳ ngôn ngữ nào hỗ trợ giao thức HTTP.
2. **Thiết lập yêu cầu**: Bạn cần xác định các thành phần cơ bản của một yêu cầu API, bao gồm:
   - **URL** của API (thường bao gồm base URL và endpoint).
   - **Phương thức HTTP**: GET, POST, PUT, DELETE, v.v.
   - **Headers**: Thông tin bổ sung như định dạng dữ liệu, token xác thực.
   - **Body** (nếu cần): Dữ liệu cần gửi đến API, ví dụ như JSON hoặc XML.
3. **Thực hiện yêu cầu**: Sử dụng thư viện hoặc mô-đun HTTP của ngôn ngữ lập trình để gửi yêu cầu và nhận phản hồi từ API.

### Ví dụ gọi API bằng Python

Python là một ngôn ngữ phổ biến và có thư viện `requests` hỗ trợ mạnh mẽ cho việc gọi API. Sau đây là một ví dụ sử dụng OAuth 2.0 để gọi API Google:

```python
import requests

# URL của API và token xác thực (thay bằng token của bạn)
url = 'https://www.googleapis.com/gmail/v1/users/me/messages'
access_token = 'Bearer YOUR_ACCESS_TOKEN'

# Headers bao gồm thông tin xác thực
headers = {
    'Authorization': access_token
}

# Gửi yêu cầu GET đến API
response = requests.get(url, headers=headers)

# Kiểm tra trạng thái phản hồi và hiển thị kết quả
if response.status_code == 200:
    print("Kết quả:", response.json())
else:
    print("Lỗi:", response.status_code, response.text)
```

### Ví dụ gọi API bằng JavaScript

JavaScript có thể gọi API thông qua `fetch` hoặc `axios`. Sau đây là ví dụ sử dụng `fetch`:

```javascript
const url = 'https://www.googleapis.com/gmail/v1/users/me/messages';
const token = 'Bearer YOUR_ACCESS_TOKEN';

fetch(url, {
    method: 'GET',
    headers: {
        'Authorization': token
    }
})
.then(response => response.json())
.then(data => console.log("Kết quả:", data))
.catch(error => console.error("Lỗi:", error));
```

### Tìm kiếm ví dụ từ tài liệu API

Ngoài việc sử dụng Postman để kiểm thử, bạn cũng có thể tìm kiếm ví dụ về cách gọi API từ tài liệu của từng API cụ thể. Tài liệu API thường cung cấp:

- Mô tả chi tiết về các phương thức, URL và định dạng dữ liệu.
- Các ví dụ mã nguồn cho nhiều ngôn ngữ lập trình như Python, JavaScript, Java, C#, v.v.
- Hướng dẫn cấu hình xác thực và xử lý lỗi khi gọi API.

### Liên hệ với nhà cung cấp API

Nếu bạn không tìm thấy ví dụ về cách gọi API trong tài liệu, bạn có thể liên hệ trực tiếp với nhà cung cấp API để nhận hỗ trợ. Họ thường sẵn sàng cung cấp thêm thông tin và ví dụ cụ thể để giúp bạn tích hợp API vào dự án của mình.

## Tổng kết

Trong phần này, chúng ta đã tìm hiểu cách gọi API bằng các ngôn ngữ lập trình phổ biến và những tài nguyên có thể hỗ trợ quá trình này. Hãy luôn nhớ rằng việc gọi API có thể được thực hiện bằng nhiều ngôn ngữ khác nhau, và Postman chỉ là một trong những công cụ giúp bạn kiểm thử nhanh chóng. Việc nắm vững kiến thức cơ bản về API sẽ giúp bạn dễ dàng chuyển đổi giữa các ngôn ngữ và công cụ khác nhau để phát triển ứng dụng.
