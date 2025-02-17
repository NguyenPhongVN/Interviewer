# Subject trong Combine

`Subject` là một publisher trong Combine framework của Apple, cho phép bạn phát ra các giá trị mới cho các subscriber của nó. Có hai loại `Subject` chính:

1. **PassthroughSubject**: Chỉ phát ra các giá trị mới cho các subscriber hiện tại.
2. **CurrentValueSubject**: Giữ lại giá trị hiện tại và phát ra giá trị đó cho các subscriber mới.

## Ví dụ về PassthroughSubject

```swift
import Combine

let subject = PassthroughSubject<String, Never>()

let subscription = subject.sink { value in
    print("Received value: \(value)")
}

subject.send("Hello")
subject.send("World")
```

## Ví dụ về CurrentValueSubject

```swift
import Combine

let subject = CurrentValueSubject<String, Never>("Initial Value")

let subscription1 = subject.sink { value in
    print("Subscription 1 received value: \(value)")
}

subject.send("Hello")

let subscription2 = subject.sink { value in
    print("Subscription 2 received value: \(value)")
}

subject.send("World")
```

Trong ví dụ trên, `subscription2` sẽ nhận được giá trị "Hello" ngay khi nó được tạo ra, vì `CurrentValueSubject` giữ lại giá trị hiện tại của nó.

## Kết luận

`Subject` là một công cụ mạnh mẽ trong Combine để phát ra các giá trị mới và quản lý các subscriber. Hiểu rõ cách sử dụng `PassthroughSubject` và `CurrentValueSubject` sẽ giúp bạn tận dụng tối đa khả năng của Combine framework.


## Trong Combine framework của Swift, `Publisher` và `Subscriber` là hai khái niệm cơ bản để quản lý và xử lý dữ liệu không đồng bộ.

### Publisher

`Publisher` là một giao thức (protocol) đại diện cho một nguồn dữ liệu có thể phát ra một chuỗi các giá trị theo thời gian. Một `Publisher` có thể phát ra ba loại sự kiện:
1. **Giá trị** (`Output`): Đây là dữ liệu mà `Publisher` phát ra.
2. **Hoàn thành** (`Completion`): Đây là sự kiện báo hiệu rằng `Publisher` đã hoàn thành việc phát ra dữ liệu.
3. **Lỗi** (`Failure`): Đây là sự kiện báo hiệu rằng có lỗi xảy ra trong quá trình phát ra dữ liệu.

Ví dụ về một `Publisher` đơn giản:
```swift
import Combine

let publisher = Just("Hello, Combine!")
```

### Subscriber

`Subscriber` là một giao thức đại diện cho một đối tượng có thể nhận và xử lý các giá trị và sự kiện từ một `Publisher`. Một `Subscriber` phải tuân theo hai giao thức con:
1. **Input**: Loại dữ liệu mà `Subscriber` có thể nhận.
2. **Failure**: Loại lỗi mà `Subscriber` có thể xử lý.

Ví dụ về một `Subscriber` đơn giản:
```swift
import Combine

let subscriber = Subscribers.Sink<String, Never>(
    receiveCompletion: { completion in
        print("Received completion: \(completion)")
    },
    receiveValue: { value in
        print("Received value: \(value)")
    }
)
```

### Kết hợp Publisher và Subscriber

Để kết nối một `Publisher` với một `Subscriber`, bạn sử dụng phương thức `subscribe(_:)`:
```swift
publisher.subscribe(subscriber)
```

Hoặc sử dụng cú pháp tiện lợi hơn với `sink`:
```swift
publisher.sink(
    receiveCompletion: { completion in
        print("Received completion: \(completion)")
    },
    receiveValue: { value in
        print("Received value: \(value)")
    }
)
```

### Kết luận

Hiểu rõ cách sử dụng `Publisher` và `Subscriber` trong Combine sẽ giúp bạn quản lý và xử lý dữ liệu không đồng bộ một cách hiệu quả trong các ứng dụng Swift.