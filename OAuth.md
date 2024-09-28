### Tìm Hiểu Về OAuth  
[Let's Talk About OAuth]

OAuth là gì?

[Tell me, what is OAuth?]

OAuth (Open Authorization) là một giao thức cho phép một ứng dụng (gọi là **client**) có quyền truy cập giới hạn vào tài nguyên mà không cần chia sẻ trực tiếp thông tin đăng nhập (username và password) của người dùng (chủ sở hữu tài nguyên). 

[OAuth (Open Authorization) is a protocol that allows an application (called a **client**) to have limited access to resources without directly sharing the user’s (resource owner) login information (username and password).]

---

### 1. Giới Thiệu Về OAuth  
[1. Introduction to OAuth]

Một ví dụ đơn giản về OAuth là khi bạn có các bức ảnh trên một website như **myphotos.com**, bạn có thể phân loại chúng thành **ảnh công khai** và **ảnh riêng tư**. Bạn muốn chia sẻ **ảnh công khai** với một ứng dụng khác, nhưng không muốn ứng dụng đó truy cập vào **ảnh riêng tư**. Đó là lúc bạn sử dụng OAuth để cấp quyền cho ứng dụng đó, cho phép truy cập giới hạn vào **ảnh công khai** mà không cần chia sẻ tài khoản của bạn.

[A simple example of OAuth is when you have photos on a website like **myphotos.com**, you can categorize them into **public photos** and **private photos**. You want to share your **public photos** with another application, but you don’t want that app to access your **private photos**. That’s when you use OAuth to grant the app limited access to **public photos** without sharing your account credentials.]

OAuth sẽ cấp quyền truy cập **giới hạn** này bằng cách sử dụng một thứ gọi là **mã thông báo truy cập** (access token).

[OAuth will grant this **limited access** by using something called an **access token**.]

---

### 2. Các Vai Trò Chính Trong OAuth  
[2. Key Roles in OAuth]

Trong OAuth, có bốn vai trò chính:

[In OAuth, there are four main roles:]

1. **Chủ sở hữu tài nguyên (Resource Owner)**: Người sở hữu tài nguyên cần được bảo vệ (ví dụ: ảnh trên website).  
   [**Resource Owner**: The person who owns the resources to be protected (e.g., photos on a website).]  
   
2. **Máy chủ tài nguyên (Resource Server)**: Cung cấp tài nguyên khi nhận được **mã thông báo truy cập** hợp lệ.  
   [**Resource Server**: Provides the resources when it receives a valid **access token**.]  
   
3. **Máy khách (Client)**: Ứng dụng muốn truy cập vào tài nguyên của chủ sở hữu.  
   [**Client**: The application that wants to access the resource owner’s resources.]  
   
4. **Máy chủ cấp quyền (Authorization Server)**: Xác thực danh tính của chủ sở hữu và cấp **mã thông báo truy cập** cho máy khách.  
   [**Authorization Server**: Authenticates the identity of the resource owner and issues **access tokens** to the client.]

---

### 3. Cách Hoạt Động Của OAuth  
[3. How OAuth Works]

Khi máy khách muốn truy cập vào tài nguyên của chủ sở hữu, quy trình cơ bản như sau:

[When the client wants to access the resource owner’s resources, the basic process is as follows:]

1. **Yêu cầu quyền truy cập**: Máy khách gửi một yêu cầu tới chủ sở hữu tài nguyên để xin quyền truy cập vào tài nguyên của họ.  
   [**Request Access**: The client sends a request to the resource owner asking for permission to access their resources.]  
   
2. **Cấp quyền**: Chủ sở hữu tài nguyên đồng ý và máy khách nhận được một **mã xác thực** (authorization code).  
   [**Grant Access**: The resource owner agrees, and the client receives an **authorization code**.]  
   
3. **Đổi mã xác thực lấy mã thông báo**: Máy khách gửi mã xác thực này tới máy chủ cấp quyền để đổi lấy **mã thông báo truy cập**.  
   [**Exchange Code for Token**: The client sends this authorization code to the authorization server to exchange it for an **access token**.]  
   
4. **Truy cập tài nguyên**: Máy khách sử dụng mã thông báo truy cập này để truy cập vào tài nguyên trên máy chủ tài nguyên.  
   [**Access Resources**: The client uses this access token to access the resources on the resource server.]

#### 3.1 Ví Dụ Về OAuth  
[3.1 Example of OAuth]

Giả sử bạn có ảnh trên tài khoản Google. Một ứng dụng như Facebook muốn lấy các ảnh công khai từ tài khoản của bạn để đăng lên Facebook. Bạn sẽ sử dụng OAuth để cấp quyền cho Facebook chỉ truy cập vào **ảnh công khai** của bạn, mà không phải toàn bộ tài khoản Google.

[Suppose you have photos on your Google account. An app like Facebook wants to retrieve your public photos from your account to post on Facebook. You would use OAuth to grant Facebook access to your **public photos** only, without giving access to your entire Google account.]

---

### 4. Các Loại Quyền Cấp Trong OAuth  
[4. Types of Authorization Grants in OAuth]

Có bốn loại quyền cấp chính trong OAuth:

[There are four main types of authorization grants in OAuth:]

1. **Authorization Code Grant**  
   [Authorization Code Grant]  
   - Máy khách xin quyền từ chủ sở hữu tài nguyên qua máy chủ cấp quyền, rồi đổi mã xác thực để lấy mã thông báo truy cập.  
   [The client requests permission from the resource owner through the authorization server, then exchanges the authorization code for an access token.]

2. **Implicit Grant**  
   [Implicit Grant]  
   - Phù hợp cho ứng dụng chạy trong trình duyệt và không yêu cầu đổi mã xác thực. Máy khách nhận trực tiếp mã thông báo truy cập.  
   [Suitable for applications running in the browser and does not require an authorization code exchange. The client directly receives the access token.]

3. **Resource Owner Password Credentials Grant**  
   [Resource Owner Password Credentials Grant]  
   - Máy khách sử dụng thông tin đăng nhập của chủ sở hữu tài nguyên để yêu cầu mã thông báo truy cập từ máy chủ cấp quyền.  
   [The client uses the resource owner's credentials to request an access token from the authorization server.]

4. **Client Credentials Grant**  
   [Client Credentials Grant]  
   - Dùng khi máy khách đã được xác thực trước với máy chủ cấp quyền và không cần thông tin từ chủ sở hữu tài nguyên.  
   [Used when the client has been pre-authenticated with the authorization server and does not require the resource owner's information.]

---

### 5. Mã Thông Báo Truy Cập và Mã Làm Mới  
[5. Access Tokens and Refresh Tokens]

- **Mã Thông Báo Truy Cập** (Access Token): Cho phép máy khách truy cập vào tài nguyên được bảo vệ trong thời gian ngắn.  
  [**Access Token**: Allows the client to access protected resources for a short period of time.]  

- **Mã Làm Mới** (Refresh Token): Được sử dụng để lấy mã thông báo truy cập mới khi mã cũ hết hạn. Mã này thường có thời hạn dài hơn mã thông báo truy cập.  
  [**Refresh Token**: Used to obtain a new access token when the old one expires. It usually has a longer lifespan than the access token.]

Ví dụ: Nếu mã thông báo truy cập có thời hạn một tháng và mã làm mới có thời hạn 12 tháng, bạn có thể sử dụng mã làm mới để lấy 12 mã thông báo truy cập mới, mỗi khi mã cũ hết hạn.

[For example: If the access token is valid for one month and the refresh token is valid for 12 months, you can use the refresh token to get 12 new access tokens, each time the old one expires.]

---

### 6. Tổng Quan Về OAuth 2.0  
[6. Overview of OAuth 2.0]

OAuth 2.0 là phiên bản mới nhất, không xây dựng trên OAuth 1.0 và chỉ sử dụng **HTTP** để truyền dữ liệu. Nó cung cấp một lớp phân quyền giúp bảo vệ tài nguyên của người dùng mà không cần chia sẻ thông tin nhạy cảm.

[OAuth 2.0 is the latest version, not built on OAuth 1.0 and only uses **HTTP** to transmit data. It provides an authorization layer that helps protect users' resources without sharing sensitive information.]

Nếu muốn tìm hiểu thêm, bạn có thể tham khảo tài liệu RFC 6749 để nắm rõ các chi tiết kỹ thuật.

[If you want to learn more, you can refer to RFC 6749 for the technical details.]
