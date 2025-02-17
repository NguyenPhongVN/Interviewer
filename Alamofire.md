# Các Tính Năng Của Alamofire
Alamofire là một thư viện mạng mạnh mẽ cho Swift. Dưới đây là một số tính năng chính của Alamofire:

## 1. Yêu Cầu HTTP
- Hỗ trợ các phương thức HTTP như GET, POST, PUT, DELETE, PATCH.
- Dễ dàng cấu hình các yêu cầu với các tham số, headers, và encoding.

## 2. Xử Lý Phản Hồi
- Tự động chuyển đổi dữ liệu phản hồi thành các kiểu dữ liệu Swift.
- Hỗ trợ xử lý JSON, plist, và dữ liệu thô.

## 3. Quản Lý Phiên
- Hỗ trợ quản lý phiên làm việc với URLSession.
- Cung cấp các tùy chọn cấu hình phiên làm việc.

## 4. Tải Lên Và Tải Xuống
- Hỗ trợ tải lên và tải xuống các tệp tin.
- Cung cấp tiến trình tải lên và tải xuống.

## 5. Xác Thực
- Hỗ trợ xác thực HTTP Basic và HTTP Digest.
- Hỗ trợ xác thực dựa trên mã thông báo (token).

## 6. Quản Lý Mạng
- Tự động xử lý các lỗi mạng và retry.
- Hỗ trợ theo dõi trạng thái mạng.

## 7. Mã Hóa Và Giải Mã
- Hỗ trợ mã hóa và giải mã dữ liệu với các chuẩn mã hóa phổ biến.

## 8. Tiện Ích
- Cung cấp các tiện ích để dễ dàng làm việc với dữ liệu mạng.
- Hỗ trợ các tiện ích để kiểm tra và gỡ lỗi.

## 9. Các Tính Năng Khác
- **Chuỗi Yêu Cầu / Phản Hồi**: Cho phép chuỗi nhiều phương thức yêu cầu và phản hồi lại với nhau để có mã sạch hơn và dễ đọc hơn.
- **Tuần Tự Hóa Tham Số và Phản Hồi JSON**: Tự động xử lý mã hóa và giải mã JSON.
- **Xác Thực**: Hỗ trợ nhiều phương thức xác thực bao gồm HTTP Basic, HTTP Digest, và OAuth.
- **Khả Năng Theo Dõi Mạng**: Giám sát trạng thái kết nối mạng và cung cấp các callback khi có thay đổi.
- **Xác Thực Yêu Cầu**: Dễ dàng xác thực các yêu cầu và phản hồi.
- **Bộ Nhớ Đệm Phản Hồi**: Hỗ trợ sẵn cho việc lưu trữ phản hồi.
- **Tải Lên Tệp Tin Đa Phần**: Đơn giản hóa quá trình tải lên tệp tin với multipart/form-data.
- **Theo Dõi Tiến Trình Tải Xuống**: Theo dõi tiến trình của yêu cầu tải xuống.
- **Tài Liệu Chi Tiết**: Tài liệu chi tiết và các ví dụ để giúp bạn bắt đầu nhanh chóng.

### Ví Dụ Sử Dụng:
```swift
import Alamofire

// Thực hiện yêu cầu GET
AF.request("https://api.example.com/get").responseJSON { response in
    switch response.result {
    case .success(let value):
        print("Response JSON: \(value)")
    case .failure(let error):
        print("Error: \(error)")
    }
}

// Thực hiện yêu cầu POST với tham số
let parameters: [String: Any] = [
    "foo": "bar",
    "baz": ["a", "b", "c"]
]

AF.request("https://api.example.com/post", method: .post, parameters: parameters, encoding: JSONEncoding.default).responseJSON { response in
    switch response.result {
    case .success(let value):
        print("Response JSON: \(value)")
    case .failure(let error):
        print("Error: \(error)")
    }
}

// Thực hiện yêu cầu tải lên tệp tin
let fileURL = Bundle.main.url(forResource: "file", withExtension: "txt")!

AF.upload(fileURL, to: "https://api.example.com/upload").responseJSON { response in
    switch response.result {
    case .success(let value):
        print("Response JSON: \(value)")
    case .failure(let error):
        print("Error: \(error)")
    }
}

// Thực hiện yêu cầu tải xuống tệp tin
AF.download("https://api.example.com/download").responseData { response in
    switch response.result {
    case .success(let data):
        print("Downloaded file data: \(data)")
    case .failure(let error):
        print("Error: \(error)")
    }
}
```
