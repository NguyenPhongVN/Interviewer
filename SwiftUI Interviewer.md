## State và Binding khác nhau như thế nào?

Trong SwiftUI, `@State` và `@Binding` là hai property wrappers được sử dụng để quản lý và truyền dữ liệu giữa các view. Dưới đây là sự khác biệt giữa chúng:

### `@State`
- **Mục đích**: `@State` được sử dụng để khai báo một trạng thái nội bộ của một view. Nó cho phép SwiftUI theo dõi và tự động cập nhật giao diện người dùng khi giá trị của trạng thái thay đổi.
- **Phạm vi**: `@State` chỉ có thể được sử dụng bên trong một view và không thể được chia sẻ trực tiếp giữa các view khác nhau.
- **Sử dụng**: Thường được sử dụng cho các giá trị trạng thái đơn giản, như các biến boolean, số nguyên, chuỗi, v.v.

#### Ví dụ về `@State`:
```swift


import SwiftUI

struct ContentView: View {
    @State private var isOn: Bool = false

    var body: some View {
        VStack {
            Toggle("Switch", isOn: $isOn)
            Text(isOn ? "Switch is ON" : "Switch is OFF")
        }
    }
}
```

### `@Binding`
- **Mục đích**: `@Binding` được sử dụng để tạo một liên kết hai chiều giữa một view và một nguồn dữ liệu bên ngoài. Nó cho phép một view đọc và ghi giá trị của một trạng thái được quản lý bởi một view khác.
- **Phạm vi**: `@Binding` cho phép chia sẻ trạng thái giữa các view khác nhau, giúp các view con có thể thay đổi trạng thái của view cha.
- **Sử dụng**: Thường được sử dụng khi bạn cần truyền dữ liệu từ view cha xuống view con và cho phép view con thay đổi dữ liệu đó.

#### Ví dụ về `@Binding`:
```swift
import SwiftUI

struct ContentView: View {
    @State private var isOn: Bool = false

    var body: some View {
        VStack {
            ToggleView(isOn: $isOn)
            Text(isOn ? "Switch is ON" : "Switch is OFF")
        }
    }
}

struct ToggleView: View {
    @Binding var isOn: Bool

    var body: some View {
        Toggle("Switch", isOn: $isOn)
    }
}
```

### Tóm tắt sự khác biệt:
- **`@State`**:
  - Quản lý trạng thái nội bộ của một view.
  - Không thể chia sẻ trực tiếp giữa các view khác nhau.
  - Thường được sử dụng cho các giá trị trạng thái đơn giản.

- **`@Binding`**:
  - Tạo liên kết hai chiều giữa một view và một nguồn dữ liệu bên ngoài.
  - Cho phép chia sẻ trạng thái giữa các view khác nhau.
  - Thường được sử dụng khi cần truyền dữ liệu từ view cha xuống view con và cho phép view con thay đổi dữ liệu đó.

Việc sử dụng `@State` và `@Binding` giúp bạn quản lý trạng thái và truyền dữ liệu một cách hiệu quả trong các ứng dụng SwiftUI.