# Databases Used in iOS

## Core Data
Core Data is an object graph and persistence framework provided by Apple. It allows data to be organized into a model and provides powerful tools for managing and persisting that data.

### Features
- Object graph management
- Data persistence
- Schema migration
- Querying and filtering

## SQLite
SQLite is a C-language library that provides a lightweight, disk-based database. It is built into iOS and can be used directly via the SQLite C API or through higher-level frameworks.

### Features
- Lightweight and fast
- Self-contained and serverless
- ACID-compliant transactions
- Full-featured SQL support

## Realm
Realm is a mobile database that runs directly inside phones, tablets, or wearables. It is designed for simplicity and speed.

### Features
- Easy to use
- High performance
- Cross-platform
- Reactive architecture

## Firebase Realtime Database
Firebase Realtime Database is a cloud-hosted NoSQL database that lets you store and sync data between your users in real-time.

### Features
- Real-time synchronization
- Offline support
- NoSQL data structure
- Integrated with Firebase services

## CloudKit
CloudKit is Apple's cloud database service that allows apps to store and retrieve data in iCloud.

### Features
- Seamless iCloud integration
- Data sharing across devices
- Security and privacy
- Server-side logic with CloudKit functions

## Sự khác biệt giữa Core Data và SQLite

### Core Data
- **Mục đích**: Core Data là một framework quản lý đối tượng và lưu trữ dữ liệu, không chỉ là một cơ sở dữ liệu.
- **Mô hình hóa dữ liệu**: Core Data sử dụng mô hình đối tượng để quản lý dữ liệu.
- **Tính năng**: Hỗ trợ quản lý đồ thị đối tượng, di chuyển schema, và các truy vấn phức tạp.
- **Tích hợp**: Tích hợp sâu với các công nghệ của Apple như iCloud và SwiftUI.
- **Hiệu suất**: Tối ưu hóa cho các thao tác trên đối tượng và bộ nhớ.

### SQLite
- **Mục đích**: SQLite là một thư viện C cung cấp cơ sở dữ liệu nhẹ, dựa trên đĩa.
- **Mô hình hóa dữ liệu**: SQLite sử dụng mô hình quan hệ với các bảng, hàng và cột.
- **Tính năng**: Hỗ trợ giao dịch ACID, SQL đầy đủ tính năng, và không cần máy chủ.
- **Tích hợp**: Có thể được sử dụng trực tiếp qua API C hoặc thông qua các framework cấp cao hơn.
- **Hiệu suất**: Tối ưu hóa cho các thao tác truy vấn SQL và lưu trữ dữ liệu trên đĩa.

### Tóm tắt
- **Core Data**: Tốt cho quản lý đối tượng và tích hợp với các công nghệ của Apple.
- **SQLite**: Tốt cho các ứng dụng cần cơ sở dữ liệu SQL nhẹ và không cần máy chủ.


## Cơ chế lưu của RealmSwift

RealmSwift sử dụng một cơ chế lưu trữ dựa trên tệp nhị phân để đảm bảo hiệu suất cao và tính nhất quán của dữ liệu. Dưới đây là một số đặc điểm chính của cơ chế lưu trữ này:

### Đặc điểm
- **Tệp nhị phân**: Dữ liệu được lưu trữ trong các tệp nhị phân, giúp truy cập nhanh chóng và hiệu quả.
- **Giao dịch**: Hỗ trợ các giao dịch ACID để đảm bảo tính nhất quán và an toàn của dữ liệu.
- **Phiên bản hóa**: Mỗi thay đổi trong cơ sở dữ liệu được ghi lại dưới dạng phiên bản, cho phép dễ dàng hoàn tác và quản lý lịch sử thay đổi.
- **Đồng bộ hóa**: Hỗ trợ đồng bộ hóa dữ liệu giữa các thiết bị và máy chủ thông qua Realm Object Server.

### Lợi ích
- **Hiệu suất cao**: Truy cập dữ liệu nhanh chóng và hiệu quả nhờ cơ chế lưu trữ nhị phân.
- **Đơn giản**: Dễ dàng sử dụng với API thân thiện và tích hợp tốt với Swift.
- **Đa nền tảng**: Hỗ trợ nhiều nền tảng khác nhau, bao gồm iOS, Android, và các ứng dụng đa nền tảng khác.
- **Bảo mật**: Dữ liệu được mã hóa để đảm bảo an toàn và bảo mật.

RealmSwift là một lựa chọn tuyệt vời cho các ứng dụng di động cần hiệu suất cao và quản lý dữ liệu đơn giản.

## Realm lưu trữ dữ liệu dưới dạng các đối tượng (objects)
Đúng vậy, Realm lưu trữ dữ liệu dưới dạng các đối tượng (objects). Điều này có nghĩa là bạn có thể làm việc với dữ liệu của mình theo cách tương tự như khi bạn làm việc với các đối tượng trong ngôn ngữ lập trình của mình (ví dụ: Swift hoặc Kotlin). Điều này giúp cho việc truy cập và quản lý dữ liệu trở nên trực quan và dễ dàng hơn.

Dưới đây là một ví dụ về cách định nghĩa một model trong RealmSwift:

```swift
import RealmSwift

class Dog: Object {
    @objc dynamic var name = ""
    @objc dynamic var age = 0
}
```

Và cách sử dụng model này để lưu trữ dữ liệu:

```swift
let myDog = Dog()
myDog.name = "Rex"
myDog.age = 1

let realm = try! Realm()
try! realm.write {
    realm.add(myDog)
}
```

Trong ví dụ này, `Dog` là một đối tượng Realm và dữ liệu được lưu trữ dưới dạng các thuộc tính của đối tượng này.

## Keychain

Keychain là một dịch vụ lưu trữ an toàn được cung cấp bởi Apple, cho phép các ứng dụng lưu trữ dữ liệu nhạy cảm như mật khẩu, khóa mã hóa, và các thông tin bảo mật khác.

### Mục đích sử dụng
- **Bảo mật**: Lưu trữ thông tin nhạy cảm một cách an toàn.
- **Tiện lợi**: Truy cập dễ dàng vào thông tin bảo mật từ các ứng dụng.
- **Tích hợp**: Tích hợp sâu với hệ điều hành iOS và macOS.

### Keychain lưu dữ liệu dạng gì?
Keychain lưu trữ dữ liệu dưới dạng các cặp khóa-giá trị (key-value pairs). Dữ liệu có thể bao gồm:
- Mật khẩu (passwords)
- Khóa mã hóa (encryption keys)
- Chứng chỉ (certificates)
- Thông tin đăng nhập (login credentials)

Dữ liệu được mã hóa và bảo vệ bởi hệ điều hành, đảm bảo rằng chỉ các ứng dụng được ủy quyền mới có thể truy cập.

Dưới đây là một ví dụ về cách lưu trữ và truy xuất mật khẩu trong Keychain:

```swift
import Security

// Lưu trữ mật khẩu
/// Saves a password for a given service and account.
/// 
/// - Parameters:
///   - service: The name of the service for which the password is being saved.
///   - account: The account name associated with the service.
///   - password: The password to be saved.
func savePassword(service: String, account: String, password: String) {
    let data = password.data(using: .utf8)!
    let query: [String: Any] = [
        kSecClass as String: kSecClassGenericPassword,
        kSecAttrService as String: service,
        kSecAttrAccount as String: account,
        kSecValueData as String: data
    ]
    SecItemAdd(query as CFDictionary, nil)
}

// Truy xuất mật khẩu
/// Retrieves the password for a given service and account.
///
/// - Parameters:
///   - service: The name of the service for which the password is being retrieved.
///   - account: The account name associated with the service.
/// - Returns: The password as a `String` if found, otherwise `nil`.
func getPassword(service: String, account: String) -> String? {
    let query: [String: Any] = [
        kSecClass as String: kSecClassGenericPassword,
        kSecAttrService as String: service,
        kSecAttrAccount as String: account,
        kSecReturnData as String: true,
        kSecMatchLimit as String: kSecMatchLimitOne
    ]
    var dataTypeRef: AnyObject?
    let status = SecItemCopyMatching(query as CFDictionary, &dataTypeRef)
    if status == errSecSuccess, let data = dataTypeRef as? Data {
        return String(data: data, encoding: .utf8)
    }
    return nil
}
```