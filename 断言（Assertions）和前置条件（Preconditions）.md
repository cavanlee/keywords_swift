### 基础知识

Swift 是一门新的开发语言，用于开发 iOS，macOS，watchOS 和 tvOS App。虽然是一门新的开发语言，但是你会发现和之前所使用的 C 和 Objective-C 会有很多相似之处。

对于 C 和 Objective-C 中存在的基本类型，例如`Int`对应`Intergers`,`Double、Float`对应浮点数，`Bool`对应`BOOL`，用`String`类型来处理文本数据。Swift 同样提供了分厂有用的集合类型，例如`Array、Set、Dictionary`。(关于集合，可以查阅[集合类型](https://www.baidu.com))

和 C 语言类似，在 Swift 中使用不同的变量来存储值，并且广泛使用了值不可变的变量，这些不可变类型的变量称作常量。当有些值不需要修改的时候，可以使用常量来声明，这样能使代码更安全、更清晰。

除了这些常用的类型，Swift 引入了在 Objective-C 中没有的类型，比如`tuples`(元祖)。`Tuples`可以允许你创建或者传递一组不同类型的集合，比如作为函数的返回值时，你可以用一个元组返回多个同类型或者不同类型的值。

Swift 为了处理没有值的情况引入了可选类型的概念，所谓的可选类型，也就是说一个变量有可能值为 x，也有可能根本就没有值。这和 Objective-C 中使用空指针 nil 类似，唯一的区别就是 Swift 中可选类型适用范围为所有类型，而 Objective-C 中的空指针只适用于类对象。和 Objective-C 中的空指针 nil 相比，Swift 中的可选类型（`optionals`）表现的更出色，也更加的安全，也是 Swift 中核心功能之一。

Swift 是一种强类型语言，这意味着 Swift 可以让你清楚的知道值的类型。如果你的代码期望得到一个String，类型安全会阻止你不小心传入一个Int。同样的，如果你的代码期望得到一个String，类型安全会阻止你意外传入一个可选的String。类型安全可以帮助你在开发阶段尽早发现并修正错误。

### 断言（Assertions）和前置条件（Preconditions）

 Swift 中的断言和前置条件在运行时进行检查判断。 在某段将要执行的代码前