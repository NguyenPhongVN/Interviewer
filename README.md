## Chỉ ra sự khác biệt giữa let var trong swift và const trong Objective - C ?

### Sự Khác Biệt Giữa `let`, `var` trong Swift và `const` trong Objective-C

Trong Swift và Objective-C, `let`, `var`, và `const` được sử dụng để khai báo các hằng số và biến, nhưng chúng có cú pháp và cách sử dụng khác nhau. Dưới đây là sự khác biệt giữa chúng:

### Swift

#### `let`
- **Định nghĩa**: `let` được sử dụng để khai báo một hằng số, nghĩa là giá trị của nó không thể thay đổi sau khi được gán lần đầu tiên.
- **Tính bất biến**: Giá trị được gán cho một hằng số `let` là bất biến.
- **Sử dụng**: Sử dụng `let` khi bạn biết rằng giá trị sẽ không thay đổi sau khi được khởi tạo.

##### Ví dụ về `let`:
```swift
let constantValue = 10
// constantValue = 20  // Lỗi: Không thể gán giá trị mới cho hằng số 'constantValue'
```

#### `var`
- **Định nghĩa**: `var` được sử dụng để khai báo một biến, nghĩa là giá trị của nó có thể thay đổi sau khi được gán lần đầu tiên.
- **Tính biến đổi**: Giá trị được gán cho một biến `var` là có thể thay đổi.
- **Sử dụng**: Sử dụng `var` khi bạn cần thay đổi giá trị sau khi được khởi tạo.

##### Ví dụ về `var`:
```swift
var variableValue = 10
variableValue = 20  // Điều này được phép vì 'variableValue' là một biến
```

### Objective-C

#### `const`
- **Định nghĩa**: `const` được sử dụng để khai báo một hằng số, nghĩa là giá trị của nó không thể thay đổi sau khi được gán lần đầu tiên.
- **Tính bất biến**: Giá trị được gán cho một biến `const` là bất biến.
- **Sử dụng**: Sử dụng `const` khi bạn biết rằng giá trị sẽ không thay đổi sau khi được khởi tạo.

##### Ví dụ về `const`:
```objective-c
const int constantValue = 10;
// constantValue = 20;  // Lỗi: Không thể gán giá trị mới cho biến 'constantValue' với kiểu 'const int'
```

#### Biến thông thường
- **Định nghĩa**: Biến thông thường được khai báo mà không có từ khóa `const`, và giá trị của nó có thể thay đổi sau khi được gán lần đầu tiên.
- **Tính biến đổi**: Giá trị được gán cho một biến thông thường là có thể thay đổi.
- **Sử dụng**: Sử dụng biến thông thường khi bạn cần thay đổi giá trị sau khi được khởi tạo.

##### Ví dụ về biến thông thường:
```objective-c
int variableValue = 10;
variableValue = 20;  // Điều này được phép vì 'variableValue' là một biến thông thường
```

### Tóm Tắt Sự Khác Biệt
- **Swift**:
  - **`let`**: Khai báo một hằng số. Giá trị không thể thay đổi sau khi được gán.
  - **`var`**: Khai báo một biến. Giá trị có thể thay đổi sau khi được gán.
  - **Không có từ khóa `const`**: Swift sử dụng `let` để khai báo hằng số.

- **Objective-C**:
  - **`const`**: Khai báo một hằng số. Giá trị không thể thay đổi sau khi được gán.
  - **Biến thông thường**: Khai báo một biến. Giá trị có thể thay đổi sau khi được gán.
  - **Không có từ khóa `let` và `var`**: Objective-C sử dụng từ khóa `const` cho hằng số và khai báo biến thông thường cho biến.

Hiểu rõ sự khác biệt này giúp bạn viết mã đúng cú pháp và tuân thủ các quy ước của từng ngôn ngữ.

## Static Typing và Strong Typing

Trong Swift, "static type" và "strong type" là hai khái niệm quan trọng liên quan đến hệ thống kiểu của ngôn ngữ. Dưới đây là giải thích chi tiết về từng khái niệm:

### Static Typing
- **Definition**: Static typing (kiểu tĩnh) có nghĩa là kiểu của biến được xác định tại thời điểm biên dịch (compile time) và không thể thay đổi sau đó.
- **Usage**: Swift sử dụng hệ thống kiểu tĩnh, nghĩa là bạn phải khai báo kiểu của biến khi bạn khai báo nó, hoặc Swift sẽ suy luận kiểu từ giá trị khởi tạo.
- **Benefits**: Giúp phát hiện lỗi sớm trong quá trình biên dịch, cải thiện hiệu suất và đảm bảo tính nhất quán của kiểu dữ liệu.

#### Ví dụ về Static Typing:
```swift
let integer: Int = 10  // Kiểu của biến 'integer' là Int và không thể thay đổi
// integer = "Hello"  // Lỗi: Không thể gán giá trị kiểu String cho biến kiểu Int

var string = "Hello"  // Swift suy luận kiểu của biến 'string' là String
string = "World"  // Đúng: Có thể gán giá trị khác cùng kiểu
// string = 123  // Lỗi: Không thể gán giá trị kiểu Int cho biến kiểu String
```

### Strong Typing
- **Definition**: Strong typing (kiểu mạnh) có nghĩa là ngôn ngữ không cho phép các phép gán hoặc thao tác giữa các kiểu dữ liệu không tương thích mà không có sự chuyển đổi rõ ràng.
- **Usage**: Swift là một ngôn ngữ kiểu mạnh, nghĩa là bạn không thể ngầm chuyển đổi giữa các kiểu dữ liệu khác nhau mà không có sự chuyển đổi rõ ràng.
- **Benefits**: Giúp ngăn chặn lỗi do sự không nhất quán của kiểu dữ liệu và đảm bảo tính an toàn của kiểu.

#### Ví dụ về Strong Typing:
```swift
let number: Int = 10
let text: String = "The number is " + String(number)  // Phải chuyển đổi rõ ràng từ Int sang String
// let invalidText: String = "The number is " + number  // Lỗi: Không thể cộng String và Int trực tiếp

let doubleValue: Double = 3.14
let intValue: Int = Int(doubleValue)  // Phải chuyển đổi rõ ràng từ Double sang Int
```

### Tóm tắt
- **Static Typing**: Kiểu của biến được xác định tại thời điểm biên dịch và không thể thay đổi sau đó. Giúp phát hiện lỗi sớm và cải thiện hiệu suất.
- **Strong Typing**: Ngôn ngữ không cho phép các phép gán hoặc thao tác giữa các kiểu dữ liệu không tương thích mà không có sự chuyển đổi rõ ràng. Giúp ngăn chặn lỗi do sự không nhất quán của kiểu dữ liệu và đảm bảo tính an toàn của kiểu.

Swift sử dụng cả hai khái niệm này để đảm bảo rằng mã nguồn của bạn an toàn, nhất quán và hiệu quả.


## Dynamic dispatch là gì?

Dynamic dispatch là một cơ chế trong lập trình hướng đối tượng, cho phép việc gọi các phương thức được quyết định tại thời điểm chạy (runtime) thay vì tại thời điểm biên dịch (compile time). Điều này cho phép các đối tượng có thể thay đổi hành vi của chúng một cách linh hoạt thông qua việc ghi đè (override) các phương thức trong các lớp con.

### Cách hoạt động của Dynamic Dispatch
Dynamic dispatch sử dụng một bảng ảo (vtable) để lưu trữ các con trỏ đến các phương thức của đối tượng. Khi một phương thức được gọi, chương trình sẽ tra cứu bảng ảo để tìm phương thức phù hợp và thực thi nó. Điều này cho phép các lớp con ghi đè các phương thức của lớp cha và cung cấp các triển khai riêng của chúng.

### Ví dụ về Dynamic Dispatch trong Swift
Trong Swift, dynamic dispatch được sử dụng khi bạn khai báo các phương thức trong các lớp và sử dụng từ khóa `override` để ghi đè các phương thức của lớp cha.

```swift
class Animal {
    func makeSound() {
        print("Some generic animal sound")
    }
}

class Dog: Animal {
    override func makeSound() {
        print("Bark")
    }
}

class Cat: Animal {
    override func makeSound() {
        print("Meow")
    }
}

let animals: [Animal] = [Dog(), Cat()]

for animal in animals {
    animal.makeSound()  // Dynamic dispatch determines the correct method to call at runtime
}
```

### Giải thích:
- **Lớp `Animal`**: Định nghĩa một phương thức `makeSound`.
- **Lớp `Dog` và `Cat`**: Ghi đè phương thức `makeSound` của lớp `Animal`.
- **Mảng `animals`**: Chứa các đối tượng của lớp `Dog` và `Cat`.
- **Vòng lặp `for`**: Gọi phương thức `makeSound` trên từng đối tượng trong mảng. Dynamic dispatch sẽ quyết định phương thức nào sẽ được gọi tại thời điểm chạy, dựa trên kiểu thực sự của đối tượng (`Dog` hoặc `Cat`).

### Lợi ích của Dynamic Dispatch
- **Tính linh hoạt**: Cho phép các lớp con cung cấp các triển khai riêng của các phương thức, giúp mã nguồn dễ mở rộng và bảo trì.
- **Đa hình (Polymorphism)**: Hỗ trợ tính đa hình, cho phép các đối tượng thuộc các lớp khác nhau được xử lý thông qua cùng một giao diện.

### Tóm tắt
Dynamic dispatch là một cơ chế quan trọng trong lập trình hướng đối tượng, cho phép các phương thức được quyết định tại thời điểm chạy, hỗ trợ tính linh hoạt và đa hình trong các ứng dụng.

Dynamic dispatch là một cơ chế trong lập trình hướng đối tượng, cho phép việc gọi các phương thức được quyết định tại thời điểm chạy (runtime) thay vì tại thời điểm biên dịch (compile time). Điều này cho phép các đối tượng có thể thay đổi hành vi của chúng một cách linh hoạt thông qua việc ghi đè (override) các phương thức trong các lớp con.

### Cách hoạt động của Dynamic Dispatch
Dynamic dispatch sử dụng một bảng ảo (vtable) để lưu trữ các con trỏ đến các phương thức của đối tượng. Khi một phương thức được gọi, chương trình sẽ tra cứu bảng ảo để tìm phương thức phù hợp và thực thi nó. Điều này cho phép các lớp con ghi đè các phương thức của lớp cha và cung cấp các triển khai riêng của chúng.

### Ví dụ về Dynamic Dispatch trong Swift
Trong Swift, dynamic dispatch được sử dụng khi bạn khai báo các phương thức trong các lớp và sử dụng từ khóa `override` để ghi đè các phương thức của lớp cha.

```swift
class Animal {
    func makeSound() {
        print("Some generic animal sound")
    }
}

class Dog: Animal {
    override func makeSound() {
        print("Bark")
    }
}

class Cat: Animal {
    override func makeSound() {
        print("Meow")
    }
}

let animals: [Animal] = [Dog(), Cat()]

for animal in animals {
    animal.makeSound()  // Dynamic dispatch determines the correct method to call at runtime
}
```

### Giải thích:
- **Lớp `Animal`**: Định nghĩa một phương thức `makeSound`.
- **Lớp `Dog` và `Cat`**: Ghi đè phương thức `makeSound` của lớp `Animal`.
- **Mảng `animals`**: Chứa các đối tượng của lớp `Dog` và `Cat`.
- **Vòng lặp `for`**: Gọi phương thức `makeSound` trên từng đối tượng trong mảng. Dynamic dispatch sẽ quyết định phương thức nào sẽ được gọi tại thời điểm chạy, dựa trên kiểu thực sự của đối tượng (`Dog` hoặc `Cat`).

### Lợi ích của Dynamic Dispatch
- **Tính linh hoạt**: Cho phép các lớp con cung cấp các triển khai riêng của các phương thức, giúp mã nguồn dễ mở rộng và bảo trì.
- **Đa hình (Polymorphism)**: Hỗ trợ tính đa hình, cho phép các đối tượng thuộc các lớp khác nhau được xử lý thông qua cùng một giao diện.

### Tóm tắt
Dynamic dispatch là một cơ chế quan trọng trong lập trình hướng đối tượng, cho phép các phương thức được quyết định tại thời điểm chạy, hỗ trợ tính linh hoạt và đa hình trong các ứng dụng.

## ARC trong swift là gì ?

### ARC trong Swift là gì?

ARC (Automatic Reference Counting) là một cơ chế quản lý bộ nhớ tự động trong Swift, giúp theo dõi và quản lý bộ nhớ của các đối tượng trong ứng dụng. ARC tự động giải phóng bộ nhớ khi các đối tượng không còn được sử dụng, giúp ngăn chặn rò rỉ bộ nhớ và tối ưu hóa việc sử dụng bộ nhớ.

### Cách hoạt động của ARC
ARC hoạt động bằng cách đếm số lượng tham chiếu mạnh (strong references) đến một đối tượng. Khi số lượng tham chiếu mạnh đến đối tượng giảm về 0, ARC sẽ tự động giải phóng bộ nhớ của đối tượng đó.

### Ví dụ về ARC:

```swift
class Person {
    let name: String

    init(name: String) {
        self.name = name
        print("\(name) is being initialized")
    }

    deinit {
        print("\(name) is being deinitialized")
    }
}

var person1: Person? = Person(name: "John")
var person2: Person? = person1

person1 = nil
person2 = nil
```

### Giải thích:
1. **Khởi tạo đối tượng**:
   - `person1` được khởi tạo với một đối tượng `Person` có tên là "John". Lúc này, số lượng tham chiếu mạnh đến đối tượng này là 1.
   - `person2` được gán bằng `person1`, tăng số lượng tham chiếu mạnh đến đối tượng này lên 2.

2. **Giải phóng đối tượng**:
   - Khi `person1` được gán giá trị `nil`, số lượng tham chiếu mạnh giảm xuống còn 1.
   - Khi `person2` được gán giá trị `nil`, số lượng tham chiếu mạnh giảm xuống còn 0. Lúc này, ARC sẽ tự động giải phóng bộ nhớ của đối tượng `Person`, và phương thức `deinit` sẽ được gọi.

### Các loại tham chiếu trong ARC:
- **Strong Reference**: Tham chiếu mạnh giữ đối tượng trong bộ nhớ cho đến khi tham chiếu này bị hủy.
- **Weak Reference**: Tham chiếu yếu không giữ đối tượng trong bộ nhớ. Nếu tất cả các tham chiếu mạnh đến đối tượng bị hủy, đối tượng sẽ được giải phóng ngay cả khi vẫn còn tham chiếu yếu.
- **Unowned Reference**: Tham chiếu không sở hữu tương tự như tham chiếu yếu, nhưng được sử dụng khi bạn chắc chắn rằng tham chiếu sẽ không bao giờ là `nil` sau khi được khởi tạo.

### Ví dụ về weak và unowned references:

```swift
class Person {
    let name: String
    var apartment: Apartment?

    init(name: String) {
        self.name = name
    }

    deinit {
        print("\(name) is being deinitialized")
    }
}

class Apartment {
    let unit: String
    weak var tenant: Person?

    init(unit: String) {
        self.unit = unit
    }

    deinit {
        print("Apartment \(unit) is being deinitialized")
    }
}

var john: Person? = Person(name: "John")
var unit4A: Apartment? = Apartment(unit: "4A")

john?.apartment = unit4A
unit4A?.tenant = john

john = nil
unit4A = nil
```

### Giải thích:
- **Weak Reference**: Trong ví dụ trên, thuộc tính `tenant` của `Apartment` là một tham chiếu yếu (`weak`). Điều này ngăn chặn vòng tham chiếu mạnh giữa `Person` và `Apartment`, cho phép ARC giải phóng bộ nhớ của cả hai đối tượng khi không còn tham chiếu mạnh nào đến chúng.

ARC giúp quản lý bộ nhớ một cách hiệu quả và tự động, giảm thiểu nguy cơ rò rỉ bộ nhớ và giúp lập trình viên tập trung vào logic của ứng dụng thay vì quản lý bộ nhớ thủ công.


## so sánh weak với unowned, weak và unowned với strong?

Dưới đây là sự so sánh giữa `weak`, `unowned`, và `strong` trong Swift:

1. **weak**:
   - `weak` được sử dụng để khai báo một tham chiếu yếu (weak reference) đến một đối tượng.
   - Tham chiếu yếu không giữ mạnh đối tượng mà nó tham chiếu đến, do đó đối tượng có thể được giải phóng bộ nhớ nếu không còn tham chiếu mạnh nào đến nó.
   - Tham chiếu yếu luôn là tùy chọn (optional) và tự động được gán giá trị `nil` khi đối tượng mà nó tham chiếu đến bị giải phóng bộ nhớ.
   - Sử dụng `weak` khi tham chiếu có thể trở thành `nil` trong vòng đời của nó.

2. **unowned**:
   - `unowned` được sử dụng để khai báo một tham chiếu không sở hữu (unowned reference) đến một đối tượng.
   - Tham chiếu không sở hữu không giữ mạnh đối tượng mà nó tham chiếu đến, nhưng không tự động được gán giá trị `nil` khi đối tượng bị giải phóng bộ nhớ.
   - Tham chiếu không sở hữu không phải là tùy chọn (non-optional) và không kiểm tra an toàn khi truy cập đối tượng đã bị giải phóng bộ nhớ, dẫn đến lỗi runtime nếu đối tượng đã bị giải phóng.
   - Sử dụng `unowned` khi bạn chắc chắn rằng tham chiếu sẽ luôn hợp lệ trong vòng đời của nó.

3. **strong**:
   - `strong` là kiểu tham chiếu mặc định trong Swift.
   - Tham chiếu mạnh giữ mạnh đối tượng mà nó tham chiếu đến, ngăn không cho đối tượng đó bị giải phóng bộ nhớ cho đến khi tất cả các tham chiếu mạnh đến nó bị loại bỏ.
   - Sử dụng `strong` khi bạn muốn đảm bảo rằng đối tượng sẽ tồn tại miễn là có ít nhất một tham chiếu mạnh đến nó.

Dưới đây là ví dụ về cách sử dụng `weak`, `unowned`, và `strong`:

```swift
class Person {
    var name: String
    init(name: String) {
        self.name = name
    }
    var apartment: Apartment?
}

class Apartment {
    var unit: String
    init(unit: String) {
        self.unit = unit
    }
    weak var tenant: Person?
}

var john: Person? = Person(name: "John")
var unit4A: Apartment? = Apartment(unit: "4A")

john?.apartment = unit4A
unit4A?.tenant = john

john = nil
// unit4A?.tenant is now nil

class Customer {
    var name: String
    var card: CreditCard?
    init(name: String) {
        self.name = name
    }
}

class CreditCard {
    var number: UInt64
    unowned var customer: Customer
    init(number: UInt64, customer: Customer) {
        self.number = number
        self.customer = customer
    }
}

var alice: Customer? = Customer(name: "Alice")
alice?.card = CreditCard(number: 1234_5678_9012_3456, customer: alice!)

alice = nil
// Accessing alice?.card.customer will cause a runtime error

class Book {
    var title: String
    var author: Author?
    init(title: String) {
        self.title = title
    }
}

class Author {
    var name: String
    var book: Book?
    init(name: String) {
        self.name = name
    }
}

var book: Book? = Book(title: "Swift Programming")
var author: Author? = Author(name: "John Doe")

book?.author = author
author?.book = book

// Both book and author have strong references to each other
// This can cause a strong reference cycle if not handled properly
```

Trong ví dụ trên, `weak` được sử dụng cho tham chiếu từ `Apartment` đến `Person`, `unowned` được sử dụng cho tham chiếu từ `CreditCard` đến `Customer`, và `strong` được sử dụng cho tham chiếu từ `Book` đến `Author` và ngược lại.

## tại sao nói swift là ngôn ngữ an toàn ?

Swift được coi là một ngôn ngữ lập trình an toàn vì nhiều lý do. Dưới đây là một số lý do chính:

1. **Quản lý bộ nhớ tự động**:
   - Swift sử dụng Automatic Reference Counting (ARC) để quản lý bộ nhớ, giúp ngăn chặn rò rỉ bộ nhớ và giải phóng bộ nhớ không sử dụng một cách tự động.

2. **Kiểm tra kiểu dữ liệu mạnh mẽ**:
   - Swift là một ngôn ngữ có kiểm tra kiểu dữ liệu mạnh mẽ và tĩnh, nghĩa là các lỗi kiểu dữ liệu được phát hiện tại thời điểm biên dịch, giúp giảm thiểu lỗi runtime.

3. **Tùy chọn (Optionals)**:
   - Swift giới thiệu khái niệm tùy chọn (optional) để xử lý các giá trị có thể là `nil`. Điều này giúp ngăn chặn lỗi null pointer (null pointer exceptions) phổ biến trong nhiều ngôn ngữ khác.

4. **Xử lý lỗi an toàn**:
   - Swift cung cấp cơ chế xử lý lỗi mạnh mẽ với `do-catch`, `try`, và `throw`, giúp lập trình viên xử lý các lỗi một cách rõ ràng và an toàn.

5. **Không có con trỏ trần**:
   - Swift không cho phép sử dụng con trỏ trần (raw pointers), giúp ngăn chặn các lỗi liên quan đến con trỏ và bảo mật bộ nhớ.

6. **Kiểm tra biên dịch nghiêm ngặt**:
   - Swift có hệ thống kiểm tra biên dịch nghiêm ngặt, giúp phát hiện nhiều lỗi tiềm ẩn trước khi chạy chương trình.

7. **Tính năng an toàn đa luồng**:
   - Swift cung cấp các tính năng an toàn đa luồng, giúp lập trình viên viết mã an toàn trong môi trường đa luồng.

Dưới đây là ví dụ minh họa một số tính năng an toàn của Swift:

```swift
// Quản lý bộ nhớ tự động với ARC
class Person {
    var name: String
    init(name: String) {
        self.name = name
    }
    var apartment: Apartment?
}

class Apartment {
    var unit: String
    init(unit: String) {
        self.unit = unit
    }
    weak var tenant: Person?
}

// Kiểm tra kiểu dữ liệu mạnh mẽ
let age: Int = 25
// let age: Int = "25" // Lỗi biên dịch

// Tùy chọn (Optionals)
var optionalName: String? = "John"
if let name = optionalName {
    print("Name is \(name)")
} else {
    print("Name is nil")
}

// Xử lý lỗi an toàn
enum FileError: Error {
    case fileNotFound
}

func readFile(filename: String) throws -> String {
    if filename == "notfound.txt" {
        throw FileError.fileNotFound
    }
    return "File content"
}

do {
    let content = try readFile(filename: "notfound.txt")
    print(content)
} catch FileError.fileNotFound {
    print("File not found")
} catch {
    print("An unknown error occurred")
}

// Không có con trỏ trần
// Swift không cho phép sử dụng con trỏ trần như C/C++

// Kiểm tra biên dịch nghiêm ngặt
// let number: Int = "123" // Lỗi biên dịch

// Tính năng an toàn đa luồng
import Dispatch

let queue = DispatchQueue(label: "com.example.myqueue")
queue.async {
    print("Hello from a background thread")
}
```

Swift được thiết kế với nhiều tính năng an toàn để giúp lập trình viên viết mã an toàn và đáng tin cậy hơn.


## chỉ ra sự khác nhau giữa tuple và struct, tuple và struct cái nào nhanh hơn ?

Tuple và struct đều là các kiểu dữ liệu trong Swift, nhưng chúng có một số điểm khác biệt quan trọng:

1. **Tuple**:
   - Tuple là một nhóm các giá trị được gom lại với nhau. Các giá trị này có thể có các kiểu dữ liệu khác nhau.
   - Tuple không có tên cho các thuộc tính của nó, chỉ có các vị trí (index).
   - Tuple thường được sử dụng cho các giá trị tạm thời hoặc các nhóm giá trị nhỏ.
   - Cú pháp của tuple rất đơn giản và ngắn gọn.

2. **Struct**:
   - Struct là một kiểu dữ liệu có cấu trúc, cho phép bạn định nghĩa các thuộc tính và phương thức.
   - Struct có thể có các thuộc tính với tên rõ ràng và có thể có các phương thức để thao tác với dữ liệu.
   - Struct thường được sử dụng cho các đối tượng có cấu trúc phức tạp hơn và cần có các phương thức để thao tác với dữ liệu.
   - Struct có thể tuân theo các giao thức (protocols) và có thể mở rộng (extend).

Về hiệu suất, tuple thường nhanh hơn struct vì tuple đơn giản hơn và không có các tính năng phức tạp như struct. Tuy nhiên, sự khác biệt về hiệu suất thường không đáng kể và phụ thuộc vào ngữ cảnh sử dụng cụ thể. Trong hầu hết các trường hợp, bạn nên chọn kiểu dữ liệu dựa trên tính rõ ràng và dễ bảo trì của mã nguồn hơn là hiệu suất.

Dưới đây là ví dụ về tuple và struct:

```swift
// Tuple example
let personTuple = ("John", 30)
print("Name: \(personTuple.0), Age: \(personTuple.1)")

// Struct example
struct Person {
    var name: String
    var age: Int
}

let personStruct = Person(name: "John", age: 30)
print("Name: \(personStruct.name), Age: \(personStruct.age)")
```

Trong ví dụ trên, tuple được sử dụng để lưu trữ tên và tuổi của một người mà không cần định nghĩa rõ ràng các thuộc tính, trong khi struct cung cấp một cách rõ ràng và có cấu trúc để lưu trữ và truy cập các thuộc tính này.