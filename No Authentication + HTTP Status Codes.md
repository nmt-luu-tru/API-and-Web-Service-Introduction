### Tìm Hiểu Về Postman  
[Let's Talk About Postman]

**Postman** có thể được sử dụng như một **web app** trên trình duyệt, hoặc như một **native app** cài đặt trực tiếp trên hệ điều hành của bạn.

[**Postman** can be used as a **web app** in the browser or as a **native app** installed directly on your operating system.]

Ở đây bạn có thể thấy Postman đang được sử dụng trong trình duyệt, và bạn cũng có thể dùng **native app** dành riêng cho hệ điều hành của mình.

[Here, you can see Postman being used in a browser, and you can also use the **native app** specific to your operating system.]

**Native app** có khả năng truy cập hệ điều hành tốt hơn và thường hoạt động hiệu quả hơn so với chỉ sử dụng Internet.

[**Native apps** can access the operating system more effectively and generally work better than just using the Internet.]

---

### Ví Dụ Về Yêu Cầu API Với Postman  
[API Request Example with Postman]

#### 1. Tạo Yêu Cầu API Không Cần Xác Thực  
[1. Creating an API Request Using No Auth]

Chúng ta sẽ tạo một **yêu cầu API** sử dụng loại **authorization** là **No Auth**.

[We are going to create an **API request** using the **authorization** type **No Auth**.]

Điều này có nghĩa là không cần **xác thực**.

[This means that no **authentication** is needed.]

**Xác thực** có nghĩa là chứng minh bạn là ai.

[**Authentication** means proving who you are.]

Nó cũng đồng nghĩa với việc không có **authorization**.

[It also means that there's no **authorization**.]

Không có **authorization** nghĩa là không bị hạn chế quyền truy cập hoặc giới hạn những gì bạn có thể làm.

[No **authorization** means that there's no restriction or limitation on what you can do.]

Một ví dụ điển hình của **yêu cầu API** không cần **xác thực** và không có **authorization** là **trang tìm kiếm của Google**.

[A typical example of an **API request** with no **authentication** and no **authorization** is the **Google search page**.]

Bạn không cần chứng minh danh tính và không bị hạn chế quyền tìm kiếm.

[You don't need to prove your identity and you're not restricted in your search.]

#### 2. Gửi Yêu Cầu Tới Google  
[2. Sending a Request to Google]

- Nhập URL: **www.google.com** vào ô URL của Postman.  
  [Enter the URL: **www.google.com** in the URL field of Postman.]

- Chọn phương thức **GET**.  
  [Select the **GET** method.]

- Nhấp vào **Send**.  
  [Click on **Send**.]

Google sẽ phản hồi lại một **body** chứa nội dung của trang web và một **header** chứa thông tin bổ sung.

[Google will respond with a **body** containing the content of the webpage and a **header** containing additional information.]

Kết quả hiển thị sẽ khác với những gì bạn thấy trên các trình duyệt chuyên nghiệp như **Firefox** hay **Google Chrome**.

[The result will look different from what you see in professional browsers like **Firefox** or **Google Chrome**.]

---

### Mã Trạng Thái (Status Codes)  
[Status Codes]

Trong phản hồi của Google, chúng ta có thể thấy một **mã trạng thái** (status code).

[In Google's response, we can see a **status code**.]

Mã trạng thái là mã **HTTP** được trả về sau khi bạn thực hiện yêu cầu **HTTP**.

[Status codes are **HTTP** codes returned after you make an **HTTP request**.]

**HTTP** có bốn phần chính:

1. **Dòng bắt đầu** (Start Line): chứa mã trạng thái.  
   [**Start Line**: contains the status code.]

2. **Phần tiêu đề** (Header Section): chứa các tiêu đề bổ sung như loại dữ liệu, charset, v.v.  
   [**Header Section**: contains additional headers like data type, charset, etc.]

3. **Dòng trắng** (Blank Line): phân cách phần tiêu đề và phần nội dung.  
   [**Blank Line**: separates the header section from the body.]

4. **Phần nội dung** (Body): chứa kết quả hoặc nội dung phản hồi.  
   [**Body**: contains the result or content of the response.]

Mã trạng thái được chia thành năm loại:

[Status codes are divided into five categories:]

1. **1xx**: Mã thông báo (Informational).  
   [**1xx**: Informational codes.]

2. **2xx**: Thành công (Success).  
   [**2xx**: Success codes.]

3. **3xx**: Chuyển hướng (Redirection).  
   [**3xx**: Redirection codes.]

4. **4xx**: Lỗi của máy khách (Client Error).  
   [**4xx**: Client Error codes.]

5. **5xx**: Lỗi của máy chủ (Server Error).  
   [**5xx**: Server Error codes.]

---

### Ví Dụ Về Các Mã Trạng Thái  
[Examples of Status Codes]

- **100 Continue**: Đang tiếp tục xử lý yêu cầu.  
  [**100 Continue**: Continuing to process the request.]

- **200 OK**: Mọi thứ đều ổn, yêu cầu thành công.  
  [**200 OK**: Everything is fine, the request was successful.]

- **404 Not Found**: Máy chủ không tìm thấy tài nguyên yêu cầu.  
  [**404 Not Found**: The server could not find the requested resource.]

- **500 Internal Server Error**: Lỗi nội bộ máy chủ.  
  [**500 Internal Server Error**: Internal server error.]

#### 1. Ví Dụ 404 Not Found  
[Example of 404 Not Found]

Khi bạn nhập URL **www.google.com** kèm theo một chuỗi ký tự không có ý nghĩa, Google sẽ phản hồi với mã **404 Not Found**.

[When you enter the URL **www.google.com** with a random string, Google will respond with a **404 Not Found** status code.]

Điều này có nghĩa là máy chủ Google nhận được yêu cầu nhưng không tìm thấy tài nguyên yêu cầu.

[This means that Google's server received the request but could not find the requested resource.]

#### 2. Ví Dụ Mã Trạng Thái Khác  
[Example of Other Status Codes]

Khi bạn gửi yêu cầu tới một máy chủ với **Postman**, phản hồi có thể là một **image** hoặc một **XML** thay vì **HTML**.

[When you send a request to a server with **Postman**, the response could be an **image** or **XML** instead of **HTML**.]

Trong phần **Headers**, bạn sẽ thấy thông tin về kiểu dữ liệu được trả về, ví dụ: **image/jpeg**.

[In the **Headers** section, you will see information about the type of data being returned, such as **image/jpeg**.]

---

### Tổng Kết  
[Conclusion]

**Postman** giúp bạn hiểu rõ hơn về **cuộc gọi API**, kiểm tra kết quả và phân tích các phản hồi của máy chủ một cách chi tiết.

[**Postman** helps you better understand **API calls**, check the results, and analyze server responses in detail.]

Tiếp tục khám phá các tính năng của Postman để làm quen và thực hiện nhiều ví dụ khác.

[Continue exploring Postman's features to familiarize yourself and perform more examples.]
