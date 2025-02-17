## Difference between let var in Swift and const in Objective-C?

## Difference between struct and class?

## Difference between class and actor?


In Swift and Objective-C, `let`, `var`, and `const` are used to declare constants and variables, but they have different syntax and usage. Here are the differences between them in both languages:

### Swift
In Swift, `let` and `var` are used to declare constants and variables, respectively. Swift does not have a `const` keyword.

#### `let`
- **Definition**: `let` is used to declare a constant, which means the value cannot be changed once it is set.
- **Immutability**: The value assigned to a `let` constant is immutable.
- **Usage**: Use `let` when you know that the value will not change after it is initially set.

#### Example of `let`:
```swift
let constantValue = 10
// constantValue = 20  // Error: Cannot assign to value: 'constantValue' is a 'let' constant
```

#### `var`
- **Definition**: `var` is used to declare a variable, which means the value can be changed after it is set.
- **Mutability**: The value assigned to a `var` variable is mutable.
- **Usage**: Use `var` when you need to change the value after it is initially set.

#### Example of `var`:
```swift
var variableValue = 10
variableValue = 20  // This is allowed because 'variableValue' is a 'var' variable
```

### Objective-C
In Objective-C, `const` is used to declare constants, and variables are declared using standard variable declarations. Objective-C does not have `let` and `var` keywords.

#### `const`
- **Definition**: `const` is used to declare a constant, which means the value cannot be changed once it is set.
- **Immutability**: The value assigned to a `const` variable is immutable.
- **Usage**: Use `const` when you know that the value will not change after it is initially set.

#### Example of `const`:
```objective-c
const int constantValue = 10;
// constantValue = 20;  // Error: Cannot assign to variable 'constantValue' with const-qualified type 'const int'
```

#### Variables
- **Definition**: Variables are declared using standard variable declarations, and their values can be changed after they are set.
- **Mutability**: The value assigned to a variable is mutable.
- **Usage**: Use standard variable declarations when you need to change the value after it is initially set.

#### Example of a variable:
```objective-c
int variableValue = 10;
variableValue = 20;  // This is allowed because 'variableValue' is a standard variable
```

### Summary of Differences:
- **Swift**:
  - **`let`**: Declares a constant. The value cannot be changed once it is set.
  - **`var`**: Declares a variable. The value can be changed after it is set.
  - **No `const` keyword**: Swift uses `let` for constants.

- **Objective-C**:
  - **`const`**: Declares a constant. The value cannot be changed once it is set.
  - **Standard variable declarations**: Used to declare variables. The value can be changed after it is set.
  - **No `let` and `var` keywords**: Objective-C uses standard variable declarations and `const` for constants.

Understanding these differences helps in writing code that adheres to the conventions and best practices of each language.


## How is a dictionary different from an array?

In Swift, dictionaries and arrays are both collection types, but they have different characteristics and use cases. Here are the key differences between a dictionary and an array:

### Dictionary
- **Definition**: A dictionary is an unordered collection that stores key-value pairs. Each value is associated with a unique key.
- **Access**: Values are accessed using their keys.
- **Uniqueness**: Keys must be unique within a dictionary.
- **Order**: Dictionaries do not maintain the order of their elements.
- **Use Case**: Use a dictionary when you need to look up values based on unique keys.

#### Example of a Dictionary:
```swift


var studentGrades: [String: String] = [
    "Alice": "A",
    "Bob": "B",
    "Charlie": "C"
]

// Accessing a value using a key
if let grade = studentGrades["Alice"] {
    print("Alice's grade: \(grade)")
}

// Adding a new key-value pair
studentGrades["David"] = "B"

// Iterating over a dictionary
for (student, grade) in studentGrades {
    print("\(student): \(grade)")
}
```

### Array
- **Definition**: An array is an ordered collection that stores multiple values of the same type.
- **Access**: Values are accessed using their index positions.
- **Uniqueness**: Values do not need to be unique within an array.
- **Order**: Arrays maintain the order of their elements.
- **Use Case**: Use an array when you need to store a list of items in a specific order.

#### Example of an Array:
```swift


var fruits: [String] = ["Apple", "Banana", "Cherry"]

// Accessing a value using an index
let firstFruit = fruits[0]
print("First fruit: \(firstFruit)")

// Adding a new element
fruits.append("Date")

// Iterating over an array
for fruit in fruits {
    print(fruit)
}
```

### Summary of Differences:
- **Structure**:
  - **Dictionary**: Stores key-value pairs.
  - **Array**: Stores values in a specific order.
- **Access**:
  - **Dictionary**: Access values using keys.
  - **Array**: Access values using index positions.
- **Order**:
  - **Dictionary**: Unordered collection.
  - **Array**: Ordered collection.
- **Uniqueness**:
  - **Dictionary**: Keys must be unique.
  - **Array**: Values do not need to be unique.

Choosing between a dictionary and an array depends on your specific use case and how you need to access and manage the data in your collection.

### 
In Swift, `private` and `fileprivate` are two access control levels that determine the visibility and accessibility of properties, methods, and other members within your code. Here are the key differences between them:

### `private`
- **Scope**: `private` restricts the use of an entity to the enclosing declaration (such as a class, struct, or extension) and to extensions of that declaration within the same file.
- **Usage**: Use `private` when you want to hide implementation details and ensure that the entity is only accessible within the specific scope where it is declared.

#### Example of `private`:
```swift


class MyClass {
    private var privateProperty = "Private Property"

    private func privateMethod() {
        print(privateProperty)
    }

    func publicMethod() {
        privateMethod()
    }
}

// Extension of the same class within the same file
extension MyClass {
    func anotherMethod() {
        // Can access privateProperty and privateMethod because this extension is in the same file
        print(privateProperty)
        privateMethod()
    }
}

let myClass = MyClass()
myClass.publicMethod()  // Can call
myClass.anotherMethod()  // Can call
// myClass.privateMethod()  // Error: Cannot call because privateMethod is private
// print(myClass.privateProperty)  // Error: Cannot access because privateProperty is private
```

### `fileprivate`
- **Scope**: `fileprivate` allows the use of an entity anywhere within the same source file.
- **Usage**: Use `fileprivate` when you need to share code between multiple declarations within the same file but want to restrict access from outside the file.

#### Example of `fileprivate`:
```swift


class MyClass {
    fileprivate var fileprivateProperty = "Fileprivate Property"

    fileprivate func fileprivateMethod() {
        print(fileprivateProperty)
    }

    func publicMethod() {
        fileprivateMethod()
    }
}

// Another class in the same file
class AnotherClass {
    func accessFileprivate() {
        let myClass = MyClass()
        // Can access fileprivateProperty and fileprivateMethod because they are in the same file
        print(myClass.fileprivateProperty)
        myClass.fileprivateMethod()
    }
}

let anotherClass = AnotherClass()
anotherClass.accessFileprivate()  // Can call
```

### Summary of Differences:
- **`private`**:
  - Restricts access to the enclosing declaration and extensions of that declaration within the same file.
  - Use when you want to hide implementation details and ensure that the entity is only accessible within the specific scope where it is declared.

- **`fileprivate`**:
  - Allows access anywhere within the same source file.
  - Use when you need to share code between multiple declarations within the same file but want to restrict access from outside the file.

Choosing between `private` and `fileprivate` depends on the level of encapsulation and access control you need for your code.

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

Trong Swift, `class`, `struct`, `enum`, và `actor` là các kiểu dữ liệu khác nhau, mỗi loại có các đặc điểm và cách sử dụng riêng. Dưới đây là mô tả chi tiết về từng loại:

### Class
- **Definition**: `class` là một kiểu dữ liệu tham chiếu (reference type) cho phép bạn tạo các đối tượng có thể được chia sẻ và thay đổi.
- **Features**:
  - Hỗ trợ kế thừa (inheritance).
  - Được quản lý bộ nhớ bằng ARC (Automatic Reference Counting).
  - Có thể có các phương thức khởi tạo (initializers), phương thức (methods), và thuộc tính (properties).
- **Usage**: Sử dụng `class` khi bạn cần tạo các đối tượng có thể được chia sẻ và thay đổi, hoặc khi bạn cần kế thừa.

#### Example of `class`:
```swift


class Animal {
    var name: String

    init(name: String) {
        self.name = name
    }

    func makeSound() {
        print("Some generic animal sound")
    }
}

class Dog: Animal {
    override func makeSound() {
        print("Bark")
    }
}

let dog = Dog(name: "Buddy")
dog.makeSound()  // Output: Bark
```

### Struct
- **Definition**: `struct` là một kiểu dữ liệu giá trị (value type) cho phép bạn tạo các đối tượng không thể thay đổi (immutable) hoặc có thể thay đổi (mutable) nhưng không được chia sẻ.
- **Features**:
  - Không hỗ trợ kế thừa.
  - Được lưu trữ trên stack, giúp truy cập nhanh hơn.
  - Có thể có các phương thức khởi tạo, phương thức, và thuộc tính.
- **Usage**: Sử dụng `struct` khi bạn cần tạo các đối tượng không cần kế thừa và không cần chia sẻ.

#### Example of `struct`:
```swift


struct Point {
    var x: Int
    var y: Int

    func distance(to point: Point) -> Double {
        let dx = Double(x - point.x)
        let dy = Double(y - point.y)
        return sqrt(dx * dx + dy * dy)
    }
}

let point1 = Point(x: 0, y: 0)
let point2 = Point(x: 3, y: 4)
print(point1.distance(to: point2))  // Output: 5.0
```

### Enum
- **Definition**: `enum` là một kiểu dữ liệu cho phép bạn định nghĩa một nhóm các giá trị liên quan với nhau.
- **Features**:
  - Có thể có các phương thức và thuộc tính.
  - Có thể có các giá trị liên kết (associated values) và các giá trị nguyên (raw values).
- **Usage**: Sử dụng `enum` khi bạn cần tạo một nhóm các giá trị liên quan với nhau.

#### Example of `enum`:
```swift


enum Direction {
    case north
    case south
    case east
    case west

    func description() -> String {
        switch self {
        case .north:
            return "North"
        case .south:
            return "South"
        case .east:
            return "East"
        case .west:
            return "West"
        }
    }
}

let direction = Direction.north
print(direction.description())  // Output: North
```

### Actor
- **Definition**: `actor` là một kiểu dữ liệu mới trong Swift 5.5, được thiết kế để quản lý trạng thái một cách an toàn trong môi trường đa luồng (concurrent).
- **Features**:
  - Đảm bảo an toàn dữ liệu trong môi trường đa luồng.
  - Các phương thức và thuộc tính của `actor` được bảo vệ khỏi truy cập đồng thời không an toàn.
- **Usage**: Sử dụng `actor` khi bạn cần quản lý trạng thái một cách an toàn trong môi trường đa luồng.

#### Example of `actor`:
```swift


actor BankAccount {
    private var balance: Double = 0.0

    func deposit(amount: Double) {
        balance += amount
    }

    func withdraw(amount: Double) -> Bool {
        if balance >= amount {
            balance -= amount
            return true
        } else {
            return false
        }
    }

    func getBalance() -> Double {
        return balance
    }
}

let account = BankAccount()
Task {
    await account.deposit(amount: 100.0)
    let success = await account.withdraw(amount: 50.0)
    print("Withdrawal successful: \(success)")
    print("Balance: \(await account.getBalance())")
}
```

### Tóm tắt
- **Class**: Kiểu tham chiếu, hỗ trợ kế thừa, quản lý bộ nhớ bằng ARC.
- **Struct**: Kiểu giá trị, không hỗ trợ kế thừa, lưu trữ trên stack.
- **Enum**: Nhóm các giá trị liên quan, có thể có phương thức và thuộc tính.
- **Actor**: Kiểu dữ liệu an toàn trong môi trường đa luồng, bảo vệ trạng thái khỏi truy cập đồng thời không an toàn.

Mỗi loại có các đặc điểm và cách sử dụng riêng, giúp bạn lựa chọn phù hợp với yêu cầu của ứng dụng.


## What are computed and stored properties?

In Swift, properties are used to associate values with a particular class, struct, or enum. There are two main types of properties: stored properties and computed properties.

### Stored Properties

Stored properties store constant or variable values as part of an instance of a class or struct. They can be either variable stored properties (declared with `var`) or constant stored properties (declared with `let`).

Example of stored properties:

```swift
struct Person {
    var firstName: String
    var lastName: String
    let birthYear: Int
}

var person = Person(firstName: "John", lastName: "Doe", birthYear: 1990)
person.firstName = "Jane" // Allowed because firstName is a variable stored property
// person.birthYear = 1991 // Error: Cannot assign to property: 'birthYear' is a 'let' constant
```

### Computed Properties

Computed properties do not store a value directly. Instead, they provide a getter and an optional setter to retrieve and set other properties and values indirectly. Computed properties are always declared with `var`, as their value is not stored and can change.

Example of computed properties:

```swift
struct Rectangle {
    var width: Double
    var height: Double

    var area: Double {
        return width * height
    }

    var perimeter: Double {
        return 2 * (width + height)
    }
}

let rect = Rectangle(width: 10.0, height: 5.0)
print("Area: \(rect.area)") // Output: Area: 50.0
print("Perimeter: \(rect.perimeter)") // Output: Perimeter: 30.0
```

### Differences Between Stored and Computed Properties

1. **Storage**:
   - Stored properties store actual values in memory.
   - Computed properties calculate values on the fly and do not store them.

2. **Declaration**:
   - Stored properties can be declared with `var` or `let`.
   - Computed properties are always declared with `var`.

3. **Usage**:
   - Stored properties are used to store constant or variable values.
   - Computed properties are used to perform calculations or return derived values based on other properties.

In summary, stored properties are used to store values, while computed properties are used to calculate values dynamically based on other properties.

## What are the access modifiers in Swift?

In Swift, access control restricts access to parts of your code from code in other source files and modules. Swift provides five different access levels for entities (such as properties, methods, classes, structs, and enums):

1. **open**:
   - The highest (least restrictive) access level.
   - Allows entities to be accessed and subclassed outside the defining module.
   - Only applicable to classes and class members.
   - Classes marked as `open` can be subclassed, and methods marked as `open` can be overridden in any module.

2. **public**:
   - Allows entities to be accessed outside the defining module but not subclassed or overridden.
   - Suitable for APIs and libraries where you want to expose functionality but prevent modification.

3. **internal**:
   - The default access level if no access modifier is specified.
   - Allows entities to be accessed within the same module but not outside it.
   - Suitable for most use cases where you want to encapsulate implementation details within a module.

4. **fileprivate**:
   - Restricts access to entities within the same source file.
   - Suitable for sharing code between multiple declarations within the same file but not outside it.

5. **private**:
   - The most restrictive access level.
   - Restricts access to entities within the same declaration (class, struct, or extension) and its extensions within the same file.
   - Suitable for hiding implementation details and ensuring encapsulation within a specific scope.

### Example of Access Modifiers:

```swift
// Open access
open class OpenClass {
    open func openMethod() {
        print("Open method")
    }
}

// Public access
public class PublicClass {
    public func publicMethod() {
        print("Public method")
    }
}

// Internal access (default)
class InternalClass {
    func internalMethod() {
        print("Internal method")
    }
}

// Fileprivate access
fileprivate class FileprivateClass {
    fileprivate func fileprivateMethod() {
        print("Fileprivate method")
    }
}

// Private access
class PrivateClass {
    private func privateMethod() {
        print("Private method")
    }
}

// Usage examples
let openInstance = OpenClass()
openInstance.openMethod() // Accessible

let publicInstance = PublicClass()
publicInstance.publicMethod() // Accessible

let internalInstance = InternalClass()
internalInstance.internalMethod() // Accessible within the same module

let fileprivateInstance = FileprivateClass()
fileprivateInstance.fileprivateMethod() // Accessible within the same file

let privateInstance = PrivateClass()
// privateInstance.privateMethod() // Error: 'privateMethod' is inaccessible due to 'private' protection level
```

### Summary of Access Modifiers:
- **open**: Accessible and subclassable outside the defining module.
- **public**: Accessible outside the defining module but not subclassable or overridable.
- **internal**: Accessible within the same module (default).
- **fileprivate**: Accessible within the same source file.
- **private**: Accessible within the same declaration and its extensions within the same file.

Choosing the appropriate access level helps you encapsulate implementation details, control the visibility of your code, and maintain a clean and modular codebase.

## What are the default access levels in Swift?

In Swift, if you do not specify an access level for an entity (such as a class, struct, enum, property, or method), it defaults to `internal` access. This means that the entity is accessible within the same module but not from outside the module.

### Internal Access (Default)

- **Definition**: `internal` access allows entities to be accessed anywhere within the same module.
- **Usage**: This is the default access level if no access modifier is specified. It is suitable for most use cases where you want to encapsulate implementation details within a module but still allow access to other parts of the module.

#### Example of Internal Access:

```swift
class InternalClass {
    func internalMethod() {
        print("Internal method")
    }
}

struct InternalStruct {
    var internalProperty: Int
}

enum InternalEnum {
    case caseOne
    case caseTwo
}

let internalInstance = InternalClass()
internalInstance.internalMethod() // Accessible within the same module

let internalStruct = InternalStruct(internalProperty: 10)
print(internalStruct.internalProperty) // Accessible within the same module

let internalEnum = InternalEnum.caseOne
print(internalEnum) // Accessible within the same module
```

### Summary of Default Access Levels:

- **internal**: The default access level if no access modifier is specified. Entities are accessible within the same module but not from outside the module.

Using the default `internal` access level helps you encapsulate implementation details within a module while still allowing access to other parts of the module. If you need to restrict access further or expose entities to other modules, you can specify other access levels such as `private`, `fileprivate`, `public`, or `open`.


