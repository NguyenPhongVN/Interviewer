## What’s the application and controller lifecycle?

The application and controller lifecycle in iOS development involves several stages that manage the state and behavior of the app and its view controllers. Here is an overview of each lifecycle:

### Application Lifecycle

The application lifecycle is managed by the `UIApplication` class and its delegate, `UIApplicationDelegate`. The key stages in the application lifecycle are:

1. **Not Running**: The app has not been launched or was terminated by the system.
2. **Inactive**: The app is running in the foreground but not receiving events (e.g., an incoming call or SMS message).
3. **Active**: The app is running in the foreground and receiving events.
4. **Background**: The app is running in the background and executing code.
5. **Suspended**: The app is in the background but not executing code.

Key methods in `UIApplicationDelegate`:

```swift
import UIKit

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {
    var window: UIWindow?

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        // Called when the app has finished launching
        return true
    }

    func applicationWillResignActive(_ application: UIApplication) {
        // Called when the app is about to move from active to inactive state
    }

    func applicationDidEnterBackground(_ application: UIApplication) {
        // Called when the app enters the background
    }

    func applicationWillEnterForeground(_ application: UIApplication) {
        // Called when the app is about to enter the foreground
    }

    func applicationDidBecomeActive(_ application: UIApplication) {
        // Called when the app becomes active
    }

    func applicationWillTerminate(_ application: UIApplication) {
        // Called when the app is about to terminate
    }
}
```

### View Controller Lifecycle

The view controller lifecycle is managed by the `UIViewController` class. The key stages in the view controller lifecycle are:

1. **Initialization**: The view controller is created.
2. **Loading the View**: The view controller's view is loaded into memory.
3. **Appearing**: The view controller's view is about to appear on the screen.
4. **Disappearing**: The view controller's view is about to disappear from the screen.
5. **Deinitialization**: The view controller is deallocated.

Key methods in `UIViewController`:

```swift
import UIKit

class ViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
        // Called after the view has been loaded
    }

    override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        // Called just before the view appears on the screen
    }

    override func viewDidAppear(_ animated: Bool) {
        super.viewDidAppear(animated)
        // Called just after the view appears on the screen
    }

    override func viewWillDisappear(_ animated: Bool) {
        super.viewWillDisappear(animated)
        // Called just before the view disappears from the screen
    }

    override func viewDidDisappear(_ animated: Bool) {
        super.viewDidDisappear(animated)
        // Called just after the view disappears from the screen
    }

    deinit {
        // Called just before the view controller is deallocated
    }
}
```

These methods allow you to manage the state and behavior of your app and view controllers at different points in their lifecycle.

## When would you choose to use a collection view rather than a table view?

You would choose to use a collection view rather than a table view in the following scenarios:

1. **Custom Layouts**: Collection views provide more flexibility in terms of layout. You can create custom layouts by subclassing `UICollectionViewLayout`. This is useful when you need a grid layout, a circular layout, or any other non-linear layout.

2. **Multiple Columns**: If you need to display items in multiple columns, a collection view is more suitable. Table views are designed for single-column layouts, while collection views can easily handle multiple columns.

3. **Complex Item Sizes**: When the items you need to display have varying sizes, a collection view is a better choice. Collection views can handle items of different sizes more gracefully than table views.

4. **Interactive Content**: Collection views are more suitable for interactive content, such as photo galleries, where you might need to support pinch-to-zoom, drag-and-drop, or other gestures.

5. **Supplementary Views**: Collection views support supplementary views, such as headers and footers, which can be used to display additional information. While table views also support headers and footers, collection views provide more flexibility in their placement and customization.

6. **Performance**: For large datasets, collection views can offer better performance due to their more efficient reuse of cells and views.

Example of a collection view setup:

```swift
import UIKit

class MyCollectionViewController: UICollectionViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
        collectionView.register(UICollectionViewCell.self, forCellWithReuseIdentifier: "cell")
    }

    override func collectionView(_ collectionView: UICollectionView, numberOfItemsInSection section: Int) -> Int {
        return 20
    }

    override func collectionView(_ collectionView: UICollectionView, cellForItemAt indexPath: IndexPath) -> UICollectionViewCell {
        let cell = collectionView.dequeueReusableCell(withReuseIdentifier: "cell", for: indexPath)
        cell.backgroundColor = .blue
        return cell
    }
}
```

In summary, you should choose a collection view over a table view when you need more flexibility in layout, support for multiple columns, varying item sizes, interactive content, supplementary views, or better performance for large datasets.

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