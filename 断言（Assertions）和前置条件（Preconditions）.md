### 基础知识

Swift 是一门新的开发语言，用于开发 iOS，macOS，watchOS 和 tvOS App。虽然是一门新的开发语言，但是你会发现和之前所使用的 C 和 Objective-C 会有很多相似之处。

对于 C 和 Objective-C 中存在的基本类型，例如`Int`对应`Intergers`,`Double、Float`对应浮点数，`Bool`对应`BOOL`，用`String`类型来处理文本数据。Swift 同样提供了分厂有用的集合类型，例如`Array、Set、Dictionary`。(关于集合，可以查阅[集合类型](https://www.baidu.com))

和 C 语言类似，在 Swift 中使用不同的变量来存储值，并且广泛使用了值不可变的变量，这些不可变类型的变量称作常量。当有些值不需要修改的时候，可以使用常量来声明，这样能使代码更安全、更清晰。

除了这些常用的类型，Swift 引入了在 Objective-C 中没有的类型，比如`tuples`(元祖)。`Tuples`可以允许你创建或者传递一组不同类型的集合，比如作为函数的返回值时，你可以用一个元组返回多个同类型或者不同类型的值。

Swift 为了处理没有值的情况引入了可选类型的概念，所谓的可选类型，也就是说一个变量有可能值为 x，也有可能根本就没有值。这和 Objective-C 中使用空指针 nil 类似，唯一的区别就是 Swift 中可选类型适用范围为所有类型，而 Objective-C 中的空指针只适用于类对象。和 Objective-C 中的空指针 nil 相比，Swift 中的可选类型（`optionals`）表现的更出色，也更加的安全，也是 Swift 中核心功能之一。

Swift 是一种强类型语言，这意味着 Swift 可以让你清楚的知道值的类型。如果你的代码期望得到一个String，类型安全会阻止你不小心传入一个Int。同样的，如果你的代码期望得到一个String，类型安全会阻止你意外传入一个可选的String。类型安全可以帮助你在开发阶段尽早发现并修正错误。

###常量和变量

常量和变量将一个特殊类型的值和变量名关联起来，例如（`maximumNumberOfLoginAttempts `和`WelcomeMessage`分别对应值`10`和字符串`"Hello"`）。常量和变量的区别在于，前者的值一旦初始化就不能更改，而后者可以重新赋值变更。

####常量和变量的声明

常量和变量必须在声明之后才能使用。Swift 中常量的声明使用关键字`let`，变量的声明使用关键字`var`，例如我们要使用常量和变量记录用户尝试登陆的次数：

```swift
let maximumNumberOfLoginAttempts = 10
var currentLoginAttempt = 0
```

以上代码片段我们可以理解为：“我们声明一个常量名为`maximumNumberOfLoginAttempts`的常量，并且常量值为10。然后又声明了一个变量名为`currentLoginAttempt`的变量，其初始值为0”。

在这个例子中，用户最大尝试登陆次数被定义为一个常量，因为登陆次数的最大值在业务中，基本上是不会变动的。用户当前登录次数被声明为一个变量，因为这个值在每次登录失败后都是需要进行+1操作的。

你也可以再一行内声明多个变量或者常量，中间使用逗号分隔。例如：

```swift
var x = 0.0, y = 0.0, z = 0.0
```

>注意：
>
>Swift 中，如果一个被存储的值不会改变，始终建议你使用`let`关键字将其声明为一个常量。使用变量仅仅适用于被存储的值会发生变化的情况。

#### 类型注解

当声明一个常量或者变量时，你可以为该常量或变量指定一个类型，以存储指定类型的值。在常量或变量名后使用冒号分割，然后使用一个空格，后面指定类型。例如：

```swift
var welcomeMessage: String
```

以上的代码片段可以解释为：“声明一个`String`类型，变量名为`welcomeMessage`的变量”。另外，为一个变量指定类型，可以让我们知道该变量只能存储该指定类的值。

我们也可以为`welcomeMessage`赋予初始值，例如：

```Swift
welcomeMessage = "Hello"
```

我们也可以在一行内使用逗号分隔定义多个同类型的变量，类型声明则要写到最后一个变量名之后。例如：

```swift
var red, green, blue: Double
```

>注意：
>
>在编码的过程中，其实很少为变量指定类型。如果你为一个常量或变量进行了初始化，Swift 基本上可以根据初始值推断出该常量或变量的类型，详细的介绍可以在[类型安全和类型推断](https://www.baidu.com)章节中找到。在以上我们提供的举例中，`welcomeMessage`因为没有提供初始值，所以我们需要为变量`welcomeMessage`指定一个`String`类型。

#### 常量和变量的命名规范

常量和变量的命名几乎可以涵盖任何的字符，甚至可以使用 Unicode 字符来作为变量名。

```swift
let π = 3.14159
let 你好 = "你好世界"
let 🐶🐮 = "dogcow"
```

常量和变量的命名不可以包含空格、数学符号、箭头、私有 Unicode 编码、连线和制表符，不可以以数字开头，但是可以在常量与变量名的其他地方包含数字。

在声明某一类型的常量和变量的后，就不能再同一作用域内使用相同的名字进行重复定义，或者更改其类型，以及常量转换变量，变量转换常量都是不允许的。

>注意：
>
>如果你要使用系统关键字作为常量或者变量名，那么你需要在该关键字前后加上"`",以此作为区分。但是在编码的过程中，始终不建议使用系统关键字来声明常量或者变量名。

对于已经声明过的变量，我们可以重新赋予同类型新值。例如下面例子，变量`fridendlyWelcome`的值从`Hello!`变为`Bonjour!`。

```swift
var friendlyWelcome = "Hello!"
friendlyWelcome = "Bonjour!"
// friendlyWelcome is now "Bonjour!"
```

和变量不同的是，常量的值一旦初始化之后是不能更改的。如果你尝试修改一个常量的值，就会出现编译错误。

```swift
let languageName = "Swift"
languageName = "Swift++"
// This is a compile-time error: languageName cannot be changed.
```

#### 常量和变量的打印

我们可以使用`print(_:separator:terminator:)`函数将常量或者变量输入到控制台。例如：

```swift
print(friendlyWelcome)
// Prints "Bonjour!"
```

`print(_:separator:terminator:)`是一个全局的函数，print函数可以输出一个或多个值到适当输出区的全局函数。在 Xcode 中，print 函数可以将输出结果输出到 Xcode 的控制台面板。该函数中`sepatator`和`terminator`两个参数均有默认值，所以在我们使用该函数时，我们可以忽略这两个参数。默认情况下，该函数通过添加换行符来结束当前行。如果不想换行，可以传递一个空字符串给terminator参数。例如，`print(someValue, terminator:"")`。关于参数默认值的更多信息，请参考[默认参数值](https://www.baidu.com)。

Swift 用*字符串插值（string interpolation）*的方式把常量名或者变量名当做占位符加入到长字符串中，Swift 会用当前常量或变量的值替换这些占位符。将常量或变量名放入圆括号中，并在开括号前使用反斜杠将其转义：

```swift
print("The current value of friendlyWelcome is \(friendlyWelcome)")
// Prints "The current value of friendlyWelcome is Bonjour!"
```

>注意：
>
>字符串插值所有可用的选项，请参考[字符串插值](https://www.baidu.com)。

### 断言（Assertions）和前置条件（Preconditions）

 Swift 中的断言和前置条件在运行时进行检查判断。 在某段将要执行的代码前