### Understanding the Difference between Authentication and Authorization  
**Hiểu Sự Khác Biệt Giữa Xác Thực và Phân Quyền**

In the world of **APIs** (Application Programming Interfaces), it's crucial to understand the difference between **authentication** and **authorization**. These terms often come up together, but they serve different purposes. Let's break down each term for better clarity.

[Trong thế giới của **API** (Giao diện Lập trình Ứng dụng), việc hiểu sự khác biệt giữa **xác thực** và **phân quyền** là rất quan trọng. Các thuật ngữ này thường xuất hiện cùng nhau, nhưng chúng có mục đích khác nhau. Hãy cùng tìm hiểu từng thuật ngữ để có cái nhìn rõ hơn.]

---

### 1. What is Authentication?  
1. Xác Thực Là Gì?

**Authentication** is the process of proving your identity using **credentials**, such as a username and password. For example, when you log into your email account, you provide a username and password. By doing so, you are **authenticated** and gain access to all the resources available in your account.

[Xác thực là quá trình chứng minh danh tính của bạn bằng cách sử dụng **thông tin xác thực**, chẳng hạn như tên đăng nhập và mật khẩu. Ví dụ, khi bạn đăng nhập vào tài khoản email của mình, bạn cung cấp tên đăng nhập và mật khẩu. Bằng cách này, bạn đã được **xác thực** và có quyền truy cập tất cả các tài nguyên có sẵn trong tài khoản của mình.]

**Example**: Using a username and password to log into an email account.  
[Ví dụ: Sử dụng tên đăng nhập và mật khẩu để đăng nhập vào tài khoản email.]

---

### 2. What is Authorization?  
2. Phân Quyền Là Gì?

**Authorization** is the process of determining what resources a user is allowed to access. It has nothing to do with proving your identity but focuses on the **level of access** you are granted. For example, you may have photos on a fictional website called myphotos.com. Some of these photos are in a private folder, while others are in a public folder. You only want to give access to the photos in your public folder to other users. Thus, other users are **authorized** to view only the public photos.

[Phân quyền là quá trình xác định người dùng được phép truy cập vào những tài nguyên nào. Nó không liên quan đến việc chứng minh danh tính của bạn mà tập trung vào **mức độ truy cập** mà bạn được cấp. Ví dụ, bạn có một số bức ảnh trên một trang web giả định tên là myphotos.com. Một số bức ảnh này nằm trong thư mục riêng tư, trong khi số khác nằm trong thư mục công khai. Bạn chỉ muốn cho phép người dùng khác truy cập vào các bức ảnh trong thư mục công khai. Vì vậy, người dùng khác chỉ được **phân quyền** để xem các bức ảnh công khai.]

**Example**: Giving users access only to the public photos in your account.  
[Ví dụ: Cho phép người dùng chỉ truy cập vào các bức ảnh công khai trong tài khoản của bạn.]

---

### 3. Types of Authentication and Authorization in APIs  
3. Các Loại Xác Thực và Phân Quyền Trong API

Let's explore different types of **authentication** and **authorization** used in the API world, with real-life examples to illustrate their usage.

[Hãy cùng khám phá các loại **xác thực** và **phân quyền** khác nhau được sử dụng trong thế giới **API**, cùng với các ví dụ thực tế để minh họa cách sử dụng của chúng.]

#### 3.1 No Authentication  
3.1 Không Xác Thực

In this scenario, there is **no authentication** and **no authorization** involved. The user can access all resources without restrictions. An example of this is the Google search page. When you enter a search term like “tuna,” Google provides you with all search results without verifying your identity or limiting your access.

[Trong trường hợp này, không có **xác thực** và **phân quyền** nào được thực hiện. Người dùng có thể truy cập tất cả các tài nguyên mà không bị giới hạn. Ví dụ về trường hợp này là trang tìm kiếm Google. Khi bạn nhập một cụm từ tìm kiếm như “cá ngừ,” Google cung cấp cho bạn tất cả các kết quả tìm kiếm mà không cần xác minh danh tính hay hạn chế quyền truy cập của bạn.]

**Example**: Google Search.  
[Ví dụ: Tìm kiếm Google.]

#### 3.2 Basic Authentication  
3.2 Xác Thực Cơ Bản

This involves using credentials such as a **username** and **password** to access full resources without any restrictions. There is **authentication**, but no **authorization**. An example is logging into your email account. Once authenticated, you gain full access to your email without any limitations.

[Đây là quá trình sử dụng **thông tin xác thực** như **tên đăng nhập** và **mật khẩu** để truy cập đầy đủ tài nguyên mà không có bất kỳ giới hạn nào. Có **xác thực**, nhưng không có **phân quyền**. Ví dụ, khi đăng nhập vào tài khoản email của mình, sau khi được **xác thực**, bạn có quyền truy cập đầy đủ vào email mà không bị hạn chế.]

**Example**: Logging into your email account using a username and password.  
[Ví dụ: Đăng nhập vào tài khoản email bằng cách sử dụng tên đăng nhập và mật khẩu.]

#### 3.3 Bearer Token  
3.3 Mã Thông Báo Bearer

With a **bearer token**, **authorization** is granted based on the possession of a token. This token grants access to specific resources without requiring the user to prove their identity. For instance, you can give someone access to your public photos using a bearer token. The issue with this method is that anyone with the token can access your resources, which raises security concerns.

[Với **mã thông báo Bearer**, việc **phân quyền** được thực hiện dựa trên việc sở hữu mã thông báo. Mã thông báo này cho phép truy cập vào các tài nguyên cụ thể mà không yêu cầu người dùng chứng minh danh tính. Ví dụ, bạn có thể cho phép ai đó truy cập vào các bức ảnh công khai của mình bằng cách sử dụng mã thông báo Bearer. Vấn đề với phương pháp này là bất kỳ ai có mã thông báo đều có thể truy cập tài nguyên của bạn, điều này làm tăng lo ngại về **bảo mật**.]

**Example**: Using a bearer token to access photos in a public folder.  
[Ví dụ: Sử dụng mã thông báo Bearer để truy cập vào các bức ảnh trong thư mục công khai.]

#### 3.4 OAuth (Open Authorization)  
3.4 OAuth (Phân Quyền Mở)

**OAuth** is a more secure form of **authorization**. It involves both **authentication** and **authorization**. You can grant a third-party app limited access to specific resources without giving them full access to your account. For example, when using the Waze app for directions, you allow the app to access only your location while restricting access to other resources like messages or photos.

[**OAuth** là một hình thức **phân quyền** an toàn hơn. Nó bao gồm cả **xác thực** và **phân quyền**. Bạn có thể cho phép một ứng dụng bên thứ ba truy cập hạn chế vào các tài nguyên cụ thể mà không cung cấp quyền truy cập đầy đủ vào tài khoản của mình. Ví dụ, khi sử dụng ứng dụng Waze để chỉ đường, bạn chỉ cho phép ứng dụng này truy cập **vị trí** của mình, trong khi hạn chế quyền truy cập vào các tài nguyên khác như tin nhắn hoặc ảnh.]

**Example**: Allowing the Waze app to access only your location for navigation.  
[Ví dụ: Cho phép ứng dụng Waze chỉ truy cập vị trí của bạn để chỉ đường.]

#### 3.5 Two-Factor Authentication (2FA)  
3.5 Xác Thực Hai Yếu Tố (2FA)

With **Two-Factor Authentication**, the user must log in using two different **credentials**. First, they enter their username and password. Then, they must provide a second form of **authentication**, such as a code from a physical device or an authentication app. This method is used for high-security environments like banking or government systems.

[Với **Xác Thực Hai Yếu Tố**, người dùng phải đăng nhập bằng hai **thông tin xác thực** khác nhau. Đầu tiên, họ nhập **tên đăng nhập** và **mật khẩu**. Sau đó, họ phải cung cấp một hình thức xác thực thứ hai, chẳng hạn như mã từ thiết bị vật lý hoặc ứng dụng xác thực. Phương pháp này được sử dụng cho các môi trường có tính **bảo mật** cao như hệ thống **ngân hàng** hoặc **chính phủ**.]

**Example**: Logging into a bank account using both a password and a code from a physical device.  
[Ví dụ: Đăng nhập vào tài khoản ngân hàng bằng cách sử dụng cả mật khẩu và mã từ thiết bị vật lý.]

---

### 4. Summary  
4. Tóm Lược

Understanding the difference between **authentication** and **authorization** is crucial in API usage.

[Hiểu sự khác biệt giữa **xác thực** và **phân quyền** là rất quan trọng trong việc sử dụng **API**.]

- **Authentication**: Proving your identity using credentials.  
[Xác thực: Chứng minh danh tính của bạn bằng cách sử dụng **

thông tin xác thực**.]

- **Authorization**: Granting limited access to specific resources.  
[Phân quyền: Cấp quyền truy cập giới hạn vào các tài nguyên cụ thể.]
