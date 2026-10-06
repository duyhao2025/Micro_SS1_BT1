# BÀI TẬP 1 - TẦM QUAN TRỌNG CỦA KIẾN TRÚC & THUỘC TÍNH CHẤT LƯỢNG

## 1. Tại sao trước khi bắt đầu một dự án, việc chọn kiến trúc lại là bước sống còn?

Kiến trúc phần mềm là nền tảng định hình cách hệ thống được tổ chức, các thành phần giao tiếp với nhau và cách hệ thống phát triển trong tương lai.

Việc lựa chọn kiến trúc ngay từ đầu rất quan trọng vì:

### 1.1. Ảnh hưởng trực tiếp đến khả năng mở rộng

Một hệ thống có kiến trúc phù hợp sẽ dễ dàng mở rộng khi số lượng người dùng và dữ liệu tăng lên.

Ví dụ: một ứng dụng bán hàng ban đầu chỉ có vài trăm người dùng nhưng sau này có thể tăng lên hàng triệu người dùng. Nếu kiến trúc không hỗ trợ khả năng mở rộng, hệ thống có thể trở nên chậm hoặc quá tải.

### 1.2. Ảnh hưởng đến khả năng bảo trì

Kiến trúc tốt giúp chia hệ thống thành các thành phần có trách nhiệm rõ ràng. Khi cần sửa hoặc thêm chức năng, developer có thể thay đổi một phần mà ít ảnh hưởng đến những phần còn lại.

Ngược lại, nếu hệ thống được xây dựng thiếu cấu trúc, code có thể trở thành Big Ball of Mud, rất khó sửa chữa và phát triển.

### 1.3. Ảnh hưởng đến chi phí phát triển

Một quyết định kiến trúc sai có thể khiến doanh nghiệp phải tốn nhiều thời gian và chi phí để sửa chữa về sau.

Ví dụ, nếu một hệ thống Monolith được thiết kế quá chặt chẽ, khi hệ thống phát triển lớn có thể rất khó tách thành các service độc lập.

Vì vậy, chi phí thay đổi kiến trúc thường cao hơn rất nhiều so với việc cân nhắc kiến trúc ngay từ đầu.

### 1.4. Ảnh hưởng đến chất lượng hệ thống

Kiến trúc quyết định nhiều thuộc tính chất lượng như:

* Performance
* Scalability
* Availability
* Security
* Maintainability
* Reliability

Do đó, kiến trúc không chỉ quyết định hệ thống "chạy được hay không" mà còn quyết định hệ thống có thể hoạt động tốt trong thực tế hay không.

### 1.5. Ảnh hưởng đến khả năng phát triển lâu dài

Một startup có thể cần ra mắt sản phẩm nhanh, nhưng nếu chỉ tập trung vào tốc độ phát triển ban đầu mà bỏ qua kiến trúc, hệ thống có thể gặp Technical Debt lớn.

Vì vậy, cần cân bằng giữa tốc độ đưa sản phẩm ra thị trường và khả năng phát triển lâu dài.

### Kết luận

Có thể xem kiến trúc phần mềm là "bộ khung" của hệ thống. Một kiến trúc phù hợp giúp dự án dễ phát triển, mở rộng, bảo trì và giảm chi phí trong tương lai.

Do đó, lựa chọn kiến trúc không nên chỉ dựa vào công nghệ đang phổ biến mà phải dựa trên yêu cầu nghiệp vụ và các thuộc tính chất lượng mà hệ thống cần đạt được.

---

# 2. Các loại kiến trúc phần mềm

Một số kiến trúc phần mềm phổ biến:

## 2.1. Layered Architecture

Hệ thống được chia thành nhiều tầng, mỗi tầng có trách nhiệm riêng.

Ví dụ:

```text
Presentation Layer
        ↓
Business Layer
        ↓
Data Access Layer
        ↓
Database
```

Ưu điểm:

* Dễ hiểu.
* Dễ phát triển với các hệ thống vừa và nhỏ.
* Phân chia trách nhiệm rõ ràng.

Nhược điểm:

* Các tầng có thể phụ thuộc chặt chẽ vào nhau.
* Khi hệ thống lớn, việc mở rộng có thể gặp khó khăn.

---

## 2.2. Monolithic Architecture

Toàn bộ chức năng của ứng dụng được xây dựng và triển khai như một hệ thống thống nhất.

Ví dụ:

```text
                Application
                     |
        ┌────────────┼────────────┐
        ↓            ↓            ↓
      User         Order        Payment
        └────────────┼────────────┘
                     ↓
                  Database
```

Ưu điểm:

* Đơn giản để phát triển ban đầu.
* Dễ triển khai.
* Dễ debug trong các hệ thống nhỏ.

Nhược điểm:

* Khó mở rộng khi hệ thống rất lớn.
* Một thay đổi có thể ảnh hưởng đến toàn bộ hệ thống.
* Việc scale từng chức năng riêng biệt khó khăn.

---

## 2.3. Microservices Architecture

Hệ thống được chia thành nhiều service độc lập. Mỗi service đảm nhiệm một nghiệp vụ cụ thể.

Ví dụ:

```text
User Service
Order Service
Payment Service
Product Service
Shipping Service
```

Các service giao tiếp với nhau thông qua API hoặc message broker.

Ưu điểm:

* Có thể phát triển và triển khai độc lập.
* Có thể scale từng service.
* Cho phép sử dụng công nghệ khác nhau cho từng service.

Nhược điểm:

* Kiến trúc phức tạp hơn.
* Phải xử lý giao tiếp qua network.
* Khó quản lý dữ liệu phân tán.
* Yêu cầu DevOps và monitoring tốt.

---

## 2.4. Event-Driven Architecture

Các thành phần trong hệ thống giao tiếp với nhau thông qua event.

Ví dụ:

```text
Order Created
      ↓
Message Broker
      ↓
 ┌────┼─────┐
 ↓    ↓     ↓
Payment Inventory Notification
```

Khi một sự kiện xảy ra, các service quan tâm đến sự kiện đó có thể xử lý độc lập.

Ưu điểm:

* Giảm sự phụ thuộc trực tiếp giữa các service.
* Có khả năng mở rộng tốt.
* Phù hợp với hệ thống cần xử lý nhiều sự kiện.

Nhược điểm:

* Khó debug.
* Khó kiểm soát luồng xử lý.
* Có thể phát sinh vấn đề về eventual consistency.

---

# 3. Quality Attributes của phần mềm

Quality Attributes là những đặc tính dùng để đánh giá chất lượng của một hệ thống phần mềm ngoài việc hệ thống có thực hiện đúng chức năng hay không.

## 3.1. Scalability - Khả năng mở rộng

Là khả năng hệ thống đáp ứng khi số lượng người dùng, request hoặc dữ liệu tăng lên.

Ví dụ:

Một website có 10.000 người dùng nhưng sau khi quảng cáo thành công tăng lên 1 triệu người dùng. Hệ thống cần có khả năng mở rộng để đáp ứng lượng truy cập này.

---

## 3.2. Availability - Tính sẵn sàng

Là khả năng hệ thống hoạt động và phục vụ người dùng khi cần.

Ví dụ:

Một hệ thống thanh toán cần hoạt động gần như liên tục. Nếu hệ thống thường xuyên bị downtime sẽ ảnh hưởng trực tiếp đến doanh thu.

---

## 3.3. Reliability - Độ tin cậy

Là khả năng hệ thống hoạt động chính xác và ổn định trong một khoảng thời gian nhất định.

Ví dụ:

Hệ thống ngân hàng phải đảm bảo giao dịch được xử lý chính xác và không tự ý mất dữ liệu.

---

## 3.4. Performance - Hiệu năng

Đánh giá tốc độ phản hồi và khả năng xử lý request của hệ thống.

Ví dụ:

API tìm kiếm sản phẩm nên trả kết quả trong thời gian ngắn thay vì mất nhiều giây cho mỗi request.

---

## 3.5. Maintainability - Khả năng bảo trì

Là khả năng dễ sửa lỗi, cập nhật hoặc thêm chức năng mới.

Một hệ thống có code được tổ chức tốt, các module có trách nhiệm rõ ràng sẽ dễ bảo trì hơn.

---

## 3.6. Security - Bảo mật

Đảm bảo hệ thống bảo vệ dữ liệu và ngăn chặn các truy cập trái phép.

Ví dụ:

* Authentication
* Authorization
* Mã hóa dữ liệu
* Bảo vệ thông tin người dùng
* Chống các cuộc tấn công phổ biến

---

## 3.7. Usability - Tính dễ sử dụng

Đánh giá mức độ dễ học, dễ hiểu và dễ sử dụng của hệ thống đối với người dùng.

Ví dụ:

Một ứng dụng thương mại điện tử cần có giao diện rõ ràng để người dùng dễ dàng tìm kiếm và mua sản phẩm.

---

## 3.8. Testability - Khả năng kiểm thử

Là mức độ dễ dàng kiểm tra hệ thống để phát hiện lỗi.

Kiến trúc tốt thường giúp các module có thể được kiểm thử độc lập.

---

## 3.9. Modifiability - Khả năng thay đổi

Là khả năng thay đổi một phần của hệ thống mà không gây ảnh hưởng lớn đến các phần khác.

Ví dụ:

Có thể thay đổi phương thức thanh toán từ một nhà cung cấp sang nhà cung cấp khác mà không cần sửa toàn bộ hệ thống.

---

## 3.10. Deployability - Khả năng triển khai

Là mức độ dễ dàng đưa phiên bản mới của hệ thống lên môi trường production.

Kiến trúc tốt giúp giảm rủi ro khi triển khai và hỗ trợ việc phát hành phiên bản mới nhanh hơn.

---

# 4. Mối quan hệ giữa kiến trúc tốt và sự thành công của dự án

Kiến trúc phần mềm và chất lượng hệ thống có mối quan hệ rất chặt chẽ.

Có thể mô tả:

```text
Business Requirements
        ↓
Quality Attributes
        ↓
Architectural Decisions
        ↓
System Design
        ↓
Software Quality
        ↓
Project Success
```

Ví dụ, nếu doanh nghiệp yêu cầu hệ thống có thể phục vụ hàng triệu người dùng thì kiến trúc phải hỗ trợ Scalability.

Nếu doanh nghiệp yêu cầu hệ thống hoạt động 24/7 thì Availability và Reliability phải được ưu tiên.

Do đó, không tồn tại một kiến trúc tốt nhất cho mọi dự án. Kiến trúc tốt là kiến trúc phù hợp với yêu cầu nghiệp vụ, quy mô hệ thống, ngân sách, nhân lực và các Quality Attributes quan trọng.

## Kết luận

Kiến trúc phần mềm là một trong những quyết định quan trọng nhất trong vòng đời dự án. Việc lựa chọn đúng kiến trúc ngay từ đầu giúp hệ thống dễ phát triển, bảo trì, mở rộng và đáp ứng các yêu cầu chất lượng.

Ngược lại, một kiến trúc không phù hợp có thể tạo ra Technical Debt, làm tăng chi phí phát triển và gây khó khăn cho việc mở rộng hệ thống.

Vì vậy, doanh nghiệp không nên chỉ lựa chọn kiến trúc dựa trên xu hướng công nghệ mà cần lựa chọn dựa trên nhu cầu thực tế của hệ thống.
