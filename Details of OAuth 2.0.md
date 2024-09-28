https://udemy.com/course/api-and-web-service-introduction/learn/lecture/13970516#overview  
### Chi Tiết Về OAuth 2.0  
[Details of OAuth 2.0]

Trong phần này, chúng ta sẽ tìm hiểu quy trình cấp quyền bằng **authorization code** trong OAuth 2.0, đây là quy trình phổ biến nhất được sử dụng hiện nay.

[In this section, we will explore the authorization code grant process in OAuth 2.0, which is the most commonly used flow.]

---

### 1. Giới Thiệu Về Authorization Code Grant Flow  
[1. Introduction to the Authorization Code Grant Flow]

Trước khi bắt đầu quy trình này, **máy khách (client)** cần phải **đăng ký** với máy chủ cấp quyền và nhận một **ID máy khách (client ID)**. Thông tin này được quy định tại phần 2 của RFC 6749.

[Before this flow begins, the **client** must **register** with the authorization server and obtain a **client ID**. This is described in section 2 of RFC 6749.]

Quy trình này bao gồm **5 bước** (A, B, C, D, và E). Mỗi bước được xác định cụ thể và đóng một vai trò quan trọng trong việc cấp quyền truy cập tài nguyên cho máy khách.

[This process consists of **5 steps** (A, B, C, D, and E). Each step is defined specifically and plays a crucial role in granting access to resources for the client.]

---

### 2. Các Bước Trong Authorization Code Grant Flow  
[2. Steps in the Authorization Code Grant Flow]

#### 2.1. Bước A - Yêu Cầu Cấp Quyền  
[Step A - Authorization Request]

Máy khách cung cấp **điểm cuối cấp quyền (authorization endpoint)** cho người dùng thông qua **user-agent** (hầu hết là trình duyệt). Người dùng sẽ **nhấp** vào liên kết đến điểm cuối này, và liên kết sẽ chuyển hướng người dùng đến **máy chủ cấp quyền**. Khi người dùng được chuyển đến máy chủ cấp quyền, yêu cầu này mang theo **ID máy khách** và **URI chuyển hướng (redirect URI)**.

[The client provides an **authorization endpoint** to the user through the **user-agent** (usually a browser). The user **clicks** on the link to this endpoint, which redirects them to the **authorization server**. When the user is redirected to the authorization server, this request carries along the **client ID** and **redirect URI**.]

#### 2.2. Bước B - Xác Thực Người Dùng  
[Step B - User Authentication]

Tại máy chủ cấp quyền, người dùng sẽ **đăng nhập** nếu chưa đăng nhập trước đó. Sau khi xác thực thành công, máy chủ cấp quyền gửi **mã xác thực (authorization code)** cùng với **URI chuyển hướng** về cho máy khách.

[At the authorization server, the user will **log in** if they are not already logged in. After successful authentication, the authorization server sends an **authorization code** along with the **redirect URI** back to the client.]

#### 2.3. Bước C - Nhận Mã Xác Thực  
[Step C - Receiving the Authorization Code]

Người dùng được chuyển hướng về máy khách cùng với **mã xác thực**. Máy khách sau đó sử dụng mã này để gửi đến máy chủ cấp quyền và yêu cầu **mã thông báo truy cập (access token)**.

[The user is redirected back to the client along with the **authorization code**. The client then uses this code to send it to the authorization server and request an **access token**.]

#### 2.4. Bước D - Yêu Cầu Mã Thông Báo Truy Cập  
[Step D - Access Token Request]

Máy khách gửi mã xác thực đến máy chủ cấp quyền thông qua phương thức **HTTP POST** hoặc **GET**. Máy chủ cấp quyền xác thực yêu cầu và nếu hợp lệ, sẽ trả về **mã thông báo truy cập**.

[The client sends the authorization code to the authorization server via **HTTP POST** or **GET** methods. The authorization server validates the request and, if valid, returns an **access token**.]

#### 2.5. Bước E - Nhận Mã Thông Báo Truy Cập  
[Step E - Receiving the Access Token]

Máy chủ cấp quyền gửi **mã thông báo truy cập** và tùy chọn thêm **mã làm mới (refresh token)** cho máy khách. Máy khách sử dụng mã thông báo này để truy cập tài nguyên được bảo vệ trên máy chủ tài nguyên.

[The authorization server sends the **access token** and optionally a **refresh token** to the client. The client uses this access token to access protected resources on the resource server.]

---

### 3. Chi Tiết Về Client Registration  
[3. Details on Client Registration]

**Client registration** là quá trình máy khách đăng ký với máy chủ cấp quyền để lấy **client ID** và **client secret** (nếu loại máy khách là bảo mật - confidential).

[**Client registration** is the process where the client registers with the authorization server to obtain a **client ID** and **client secret** (if the client type is confidential).]

Máy khách gửi một yêu cầu **HTTP** với các thông tin sau:

[The client sends an **HTTP** request with the following information:]

- **Loại máy khách (client type)**: Có thể là **public** hoặc **confidential** tùy vào loại ứng dụng (ứng dụng gốc là public, ứng dụng web là confidential).  
  [**Client type**: Can be **public** or **confidential** depending on the type of application (native apps are public, web apps are confidential).]  

- **URI chuyển hướng**: Nơi máy chủ cấp quyền sẽ chuyển hướng người dùng sau khi xác thực.  
  [**Redirect URI**: Where the authorization server will redirect the user after authentication.]  

- **Thông tin bổ sung**: Tên ứng dụng, website, email, logo, v.v. (tùy chọn).  
  [**Additional information**: App name, website, email, logo, etc. (optional).]

Sau khi đăng ký thành công, máy khách sẽ nhận được **client ID** và **client secret** (nếu loại máy khách là confidential).

[Upon successful registration, the client receives a **client ID** and **client secret** (if the client type is confidential).]

---

### 4. Ví Dụ Thực Tiễn Với Google People API  
[4. Practical Example with Google People API]

Trong ví dụ này, chúng ta sẽ sử dụng Google People API để lấy danh bạ từ tài khoản Google của Sword Fisher bằng OAuth 2.0.

[In this example, we will use Google People API to retrieve contacts from Sword Fisher’s Google account using OAuth 2.0.]

1. **Tạo danh bạ**: Sword Fisher tạo hai danh bạ là Crab Fisher và Shrimp Fisher trong tài khoản Google của mình.  
   [**Create Contacts**: Sword Fisher creates two contacts, Crab Fisher and Shrimp Fisher, in their Google account.]  
   
2. **Máy khách Cod Fisher**: Cod Fisher muốn truy cập danh bạ của Sword Fisher qua OAuth 2.0.  
   [**Cod Fisher Client**: Cod Fisher wants to access Sword Fisher’s contacts through OAuth 2.0.]

3. **Sử dụng OAuth Playground**: Cod Fisher sử dụng OAuth Playground để thực hiện quy trình cấp quyền và nhận **mã thông báo truy cập**.  
   [**Using OAuth Playground**: Cod Fisher uses OAuth Playground to perform the authorization flow and obtain an **access token**.]

4. **Gọi Google People API**: Sử dụng **Postman**, Cod Fisher gọi API với **mã thông báo truy cập** và nhận về danh bạ của Sword Fisher.  
   [**Call Google People API**: Using **Postman**, Cod Fisher calls the API with the **access token** and retrieves Sword Fisher’s contacts.]

Ví dụ này cho thấy cách OAuth 2.0 cho phép máy khách truy cập giới hạn vào tài nguyên mà không yêu cầu người dùng cung cấp thông tin đăng nhập trực tiếp.

[This example demonstrates how OAuth 2.0 enables the client to have limited access to resources without requiring the user to provide direct login credentials.]
