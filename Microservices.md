https://(fu.)udemy.com/course/api-and-web-service-introduction/learn/lecture/16836318#overview  
# Microservices: Khái Niệm và Ứng Dụng

Microservices là một khái niệm quan trọng trong việc phát triển và triển khai phần mềm, đặc biệt trong các ứng dụng có quy mô lớn. Trong phần này, chúng ta sẽ tìm hiểu khái niệm microservices, cách thức hoạt động, sự khác biệt giữa kiến trúc microservices và monolith, cũng như những ưu và nhược điểm của microservices.

## Microservices là gì?

Cụm từ **microservices** có thể được chia thành ba thành phần:

1. **Micro**: Nghĩa là nhỏ bé, đại diện cho việc phân chia hệ thống thành những phần nhỏ hơn.
2. **Service**: Đại diện cho dịch vụ hoặc API. Đây là những chương trình hoặc chức năng mà hệ thống cung cấp.
3. **S**: Biểu thị sự số nhiều, có nghĩa là có nhiều dịch vụ hoặc API được sử dụng.

Do đó, khi nói đến microservices, chúng ta đang nói về một kiến trúc phần mềm được tạo thành từ nhiều API hoặc dịch vụ nhỏ hoạt động độc lập với nhau, mỗi dịch vụ đảm nhận một nhiệm vụ cụ thể trong hệ thống.

### So Sánh Kiến Trúc Monolith và Microservices

#### Kiến Trúc Monolith

- **Monolith** là kiến trúc truyền thống, nơi mà toàn bộ hệ thống phần mềm được phát triển và triển khai dưới dạng một khối duy nhất. Tất cả các chức năng như thanh toán, đăng nhập, đánh giá sản phẩm, quản lý tài khoản đều được đặt trong cùng một chương trình và một cơ sở dữ liệu duy nhất.

- Từ “monolith” có nghĩa là “một khối” (mono = một, lith = đá). Tương tự như một khối đá lớn, kiến trúc monolith không dễ dàng chia nhỏ hay thay đổi một phần mà không ảnh hưởng đến toàn bộ hệ thống.

#### Kiến Trúc Microservices

- Trong kiến trúc microservices, mỗi chức năng của hệ thống như thanh toán, đăng nhập, đánh giá sản phẩm đều được tách ra thành những dịch vụ độc lập, có thể hoạt động riêng lẻ. Mỗi dịch vụ có thể sử dụng một cơ sở dữ liệu riêng hoặc chia sẻ cơ sở dữ liệu chung.

- Các dịch vụ này giao tiếp với nhau thông qua giao thức HTTP hoặc các phương thức truyền thông khác như hàng đợi (queue). Điều này giúp các dịch vụ có thể được phát triển, triển khai và bảo trì độc lập mà không ảnh hưởng đến toàn bộ hệ thống.

#### Ví Dụ Minh Họa

Giả sử bạn đang mua hàng trên Amazon. Với kiến trúc **Monolith**:

- Tất cả các chức năng như tìm kiếm sản phẩm, thanh toán, và quản lý đơn hàng đều được đặt chung trong một chương trình lớn.
- Khi bạn truy cập vào `amazon.com/shop?q=autoparts` để tìm kiếm phụ tùng ô tô, chương trình xử lý việc tìm kiếm, tính năng thanh toán và lưu trữ thông tin tài khoản người dùng đều nằm trong cùng một hệ thống.

Với kiến trúc **Microservices**:

- Tính năng tìm kiếm, thanh toán và quản lý tài khoản sẽ được tách riêng thành từng dịch vụ:
  - **Payment API**: Quản lý các giao dịch thanh toán.
  - **Account API**: Quản lý thông tin người dùng.
  - **Review API**: Quản lý đánh giá sản phẩm.
- Mỗi API này có thể được phát triển bởi các đội ngũ khác nhau, sử dụng ngôn ngữ lập trình khác nhau, và có thể hoạt động độc lập mà không ảnh hưởng đến các dịch vụ còn lại.

## Ưu Điểm và Nhược Điểm của Microservices

### Ưu Điểm

1. **Khả năng mở rộng linh hoạt (Scalability)**:
   - Với microservices, bạn có thể mở rộng từng dịch vụ tùy thuộc vào nhu cầu sử dụng. Ví dụ, nếu `Payment API` được sử dụng nhiều hơn `Review API`, bạn chỉ cần mở rộng `Payment API` mà không cần phải mở rộng toàn bộ hệ thống.

2. **Độc lập ngôn ngữ lập trình (Language Independence)**:
   - Mỗi dịch vụ có thể được viết bằng ngôn ngữ lập trình riêng, phù hợp với nhu cầu của đội ngũ phát triển hoặc yêu cầu chức năng.

3. **Quản lý đội ngũ nhỏ và chuyên biệt (Specialized Teams)**:
   - Bạn có thể có một đội ngũ nhỏ, chuyên sâu phát triển cho từng dịch vụ riêng biệt, dễ dàng quản lý và phân công nhiệm vụ.

4. **Triển khai và bảo trì độc lập**:
   - Bạn có thể triển khai, cập nhật hoặc sửa lỗi cho từng dịch vụ mà không ảnh hưởng đến các dịch vụ khác trong hệ thống.

### Nhược Điểm

1. **Thiếu sự nhất quán (Lack of Consistency)**:
   - Khi các dịch vụ được phát triển bởi các đội ngũ khác nhau, có thể dẫn đến tình trạng thiếu nhất quán về mã nguồn, quy trình phát triển và giao tiếp giữa các dịch vụ.

2. **Phức tạp trong giao tiếp giữa các dịch vụ**:
   - Khi số lượng dịch vụ tăng lên, việc quản lý giao tiếp và dữ liệu giữa các dịch vụ trở nên phức tạp hơn, yêu cầu thiết kế hệ thống phân tán và xử lý lỗi phức tạp.

3. **Khó khăn trong việc tích hợp và kiểm thử (Integration and Testing)**:
   - Việc kiểm thử và tích hợp các microservices đòi hỏi nhiều thời gian và công cụ hơn so với monolith, đặc biệt khi cần kiểm tra sự tương tác giữa các dịch vụ.

4. **Tốn kém chi phí triển khai và quản lý**:
   - Vì mỗi microservice có thể chạy trên nhiều máy chủ hoặc container riêng biệt, việc quản lý hạ tầng, tài nguyên và chi phí có thể tốn kém hơn.

### Khi Nào Nên Sử Dụng Microservices?

Không phải tất cả các hệ thống đều phù hợp với microservices. Trước khi quyết định sử dụng kiến trúc này, bạn nên cân nhắc một số yếu tố:

- **Quy mô hệ thống**: Microservices phù hợp với các hệ thống lớn, có nhiều chức năng phức tạp và yêu cầu mở rộng linh hoạt.
- **Đội ngũ phát triển**: Bạn cần có đội ngũ phát triển và vận hành có kinh nghiệm trong việc quản lý các hệ thống phân tán.
- **Yêu cầu về hiệu suất và thời gian**: Nếu yêu cầu hệ thống xử lý nhanh và có độ trễ thấp, microservices có thể không phải là lựa chọn tốt do độ phức tạp trong giao tiếp giữa các dịch vụ.

## Kết Luận

Microservices mang lại nhiều lợi ích về khả năng mở rộng và linh hoạt trong phát triển phần mềm, nhưng cũng đi kèm với nhiều thách thức về quản lý và triển khai. Việc chọn lựa kiến trúc microservices hay monolith phụ thuộc vào nhu cầu cụ thể của hệ thống và khả năng quản lý của đội ngũ phát triển. Bạn nên cân nhắc kỹ lưỡng để lựa chọn kiến trúc phù hợp nhằm đảm bảo hiệu quả và sự phát triển bền vững của hệ thống.
