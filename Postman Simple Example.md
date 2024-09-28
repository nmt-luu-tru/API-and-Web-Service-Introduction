### Thêm Một Chút Về Postman  
[Just a Little Bit More About Postman]

**Postman** thực chất là một trình duyệt, giống như **Internet Explorer** hay **Firefox**.

[**Postman** is essentially a browser, like **Internet Explorer** or **Firefox**.]

Tuy nhiên, điểm khác biệt của Postman là chúng ta có thể thực hiện các **cuộc gọi API** trực tiếp mà không cần đến giao diện người dùng.

[However, the difference with Postman is that we can make direct **API calls** without the need for a user interface.]

Ví dụ: Trang tìm kiếm của Google là một giao diện.

[For example: The Google search page is an interface.]

Khi thực hiện các tìm kiếm trên **trình duyệt** của **Internet Explorer** hoặc **Firefox**, chúng ta sử dụng giao diện này.

[When performing searches on **Internet Explorer** or **Firefox** browser, we use this interface.]

Nhưng với Postman, chúng ta không cần sử dụng giao diện đó.

[But with Postman, we don't have to use that interface.]

Chúng ta có thể thực hiện các **cuộc gọi API** theo nhiều cách khác nhau và quan sát điều gì sẽ xảy ra khi những **API** đó được gọi.

[We can make **API calls** in a variety of ways and see what happens when those **APIs** are called.]

Nói một cách khác, giống như bạn đang nhìn vào những gì diễn ra “bên dưới mui xe” của một **cuộc gọi API**.

[In other words, it's like looking underneath the hood of what's happening in an **API call**.]

Tôi thích ghim những ứng dụng mình sử dụng thường xuyên vào **thanh tác vụ** của **Windows**.

[I like to pin my most used applications on the **Windows** **taskbar**.]

Nếu bạn đang sử dụng **Windows**, bạn có thể ghim Postman vào **thanh tác vụ** bằng cách: vào **màn hình chính**, nhấp chuột phải vào **Postman**, và chọn **Pin to Taskbar**.

[If you are using **Windows**, you can pin Postman to the **taskbar** by going to the **home screen**, right-clicking on **Postman**, and selecting **Pin to Taskbar**.]

Việc này sẽ đưa biểu tượng Postman xuống **thanh tác vụ**.

[This will place the Postman icon on the **taskbar**.]

Vậy là bạn có thể dễ dàng mở Postman chỉ bằng một cú nhấp chuột.

[So you can easily open Postman with just one click.]

---

### Ví Dụ Đầu Tiên Với Postman  
[First Example with Postman]

#### 1. Gửi Yêu Cầu Tới Máy Chủ eBay  
[1. Sending a Request to eBay Server]

Giờ chúng ta đã cài đặt xong **Postman**, hãy xem ví dụ đầu tiên.

[Now that we've installed **Postman**, let's look at our first example.]

Trong trường hợp này, chúng ta sẽ gửi một yêu cầu từ **Postman** đến máy chủ của **eBay**.

[In this case, we are going to send a request from **Postman** to an **eBay** server.]

Chúng ta sẽ gửi một URL **www.ebay.com**.

[We will send the URL **www.ebay.com**.]

Máy chủ của eBay sẽ phản hồi lại một **body** chứa nội dung của trang web cùng với một **header** chứa thông tin bổ sung về nội dung mà họ đang gửi.

[eBay's server will respond with a **body** containing the content of the webpage along with a **header** containing additional information about what they are sending back.]

#### 2. Thực Hiện Yêu Cầu GET  
[2. Performing a GET Request]

- Nhấp vào biểu tượng **Postman** từ **thanh tác vụ** để mở ứng dụng.  
  [Click on the **Postman** icon from the **taskbar** to open the application.]

- Nhập URL: **www.ebay.com** vào ô URL trên Postman.  
  [Enter the URL: **www.ebay.com** in the URL field on Postman.]

- Chọn phương thức **GET** (nghĩa là chúng ta chỉ lấy thông tin).  
  [Select the **GET** method (meaning we are just retrieving information).]

- Chúng ta không thêm **tham số** (parameter) nào như `q=tool` mà chỉ lấy **trang chủ**.  
  [We are not adding any **parameters** like `q=tool` but just retrieving the **homepage**.]

- Nhấp vào **Send** để gửi yêu cầu.  
  [Click on **Send** to send the request.]

#### 3. Phân Tích Kết Quả  
[3. Analyzing the Results]

Máy chủ của **eBay** sẽ phản hồi lại chúng ta với một **body** và một **header**.

[The **eBay** server will respond with a **body** and a **header**.]

- **Body** chứa **HTML** của trang web, được sử dụng để tạo nên giao diện trang web.  
  [The **Body** contains the **HTML** of the webpage, which is used to create the webpage's interface.]

- Chế độ **Pretty** giúp hiển thị HTML với định dạng dễ đọc hơn bằng cách sắp xếp theo các tab.  
  [The **Pretty** mode helps display the HTML in a more readable format by organizing it with tabs.]

- **Raw** hiển thị toàn bộ dưới dạng văn bản thô.  
  [**Raw** displays everything as plain text.]

- **Preview** cho phép bạn xem nội dung sẽ trông như thế nào trên một trình duyệt.  
  [**Preview** allows you to see how the content will look in a browser.]

**Header** sẽ cung cấp thêm thông tin về loại dữ liệu mà máy chủ gửi lại (ví dụ: HTML, charset) và thời gian trả lời yêu cầu.

[The **Header** will provide additional information about the type of data the server sends back (e.g., HTML, charset) and the response time.]

#### 4. Tổng Kết Ví Dụ Đầu Tiên  
[4. Conclusion of the First Example]

Qua ví dụ này, bạn có thể thấy cách Postman thực hiện một **yêu cầu GET** đơn giản và phân tích phản hồi từ máy chủ.

[Through this example, you can see how Postman makes a simple **GET request** and analyzes the server's response.]

Hãy tiếp tục thử nghiệm với các URL khác để khám phá thêm các tính năng của Postman.

[Continue experimenting with other URLs to explore more features of Postman.]
