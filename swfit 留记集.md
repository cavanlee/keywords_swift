###@discardableResult###

```swift
@discardableResult
func discardTest() -> Bool {
        return true
    }
```

swift中所定义的函数如果有返回值的话,调用的时候必须有一个接收方,否则编译器会报一个警告```Result of call to 'discardTest()' is unused```,在方法前加上 ```@discardableResult```，此时不接收这个函数的返回值就不会有警告了。

另外，也可以用一个通配符接收方法返回值,可以达到同样的目的。

```swift
_ = discardTest()
```

### mutating###

`structure,enumeration,class`是 Swift 这门语言中的三种类型，其中`structure`和`enumeration`归属于值类型(`value type`)，而`class`是引用类型(`reference type`)。此处与 OC 不同的是，`structure`和`enumeration`是可以拥有方法的，种种方法可以为实例方法，也可以为类方法。

Swift 官方教程中这些说明：

```swift
“Structures and enumerations are value types. By default, the properties of a value type  
 cannot be modified from within its instance methods.”
```

也就是说，虽然结构体和枚举可以定义自己的方法，但是默认情况下，实例方法中是不可以修改值类型的属性。

举个例子，我们定义一个结构体，声明一个结构体变量，和一个实例方法，然后在该方法中修改结构体变量，如下：

```swift
  struct CStruct {
        var cx: Float = 0
        func modifyCx() -> Float {
            cx += 100
            // abort: Left side of mutating operator isn't mutable: 'self' is immutable
            return cx
        }
    }
```

如果要想修改实例变量需要在方法名前添加关键字 `mutating`.

```swift
 struct CStruct {
        var cx: Float = 0
        mutating func modifyCx() -> Float {
            cx += 100
            return cx
        }
    }
```

### inout###

对于 swift 中 `inout`关键字，我们通过实例来说明：

* 普通方法，不使用 inout 关键字，系统给出异常

```swift
   var value: Int = 50

    override func viewDidLoad() {
        super.viewDidLoad()
        print(value)
        inoutTest(aValue: value)
        print(value)
    }
    func inoutTest(aValue: Int) {
        aValue = 10
        // aborting: Cannot assign to value: 'aValue' is a 'let' constant
    }
```

* 使用 inout 关键字来修饰参数

```swift
    var value: Int = 50

    override func viewDidLoad() {
        super.viewDidLoad()
        print(value) // print result is 50
        inoutTest(aValue: &value)
        print(value) // print result is 10
    }
    func inoutTest(aValue: inout Int) {
        aValue = 10
    }
```

### defer###

`defer`的作用简单来说，就是 defer block 里的代码会在函数 return 之前执行，无论函数是从哪个分支 return 的，还是有 throw，还是自然而然走到最后一行。

```swift
// 执行顺序：impossible-finally-handle error
func deferTest() {
        do {
            defer {
                print("finally")
            }
            print("impossible")
            throw MyError.SampleError
        } catch {
            print("handle error")
        }
    }

// 执行顺序：impossible-handle error-finally
 func deferTest() {
        defer {
            print("finally")
        }
        do {
            print("impossible")
            throw MyError.SampleError
        } catch {
            print("handle error")
        }
    }
```

论起实际作用，比如说在函数块中做清尾工作，回收变量等，使用 defer 再好不过了。

### @noescape###

`@noescape`，这是一个从 Swift 1.2 引入的关键字，它是专门用于修饰函数闭包这种参数类型的，当出现这个参数时，它表示该闭包不会跳出这个函数调用的生命期：即函数调用完之后，这个闭包的生命期也结束了。

```swift
public func map<T>(@noescape transform: (Self.Generator.Element) throws -> T) rethrows -> [T]
```

以下是 Apple 官方文档原文：

>A new @noescape attribute may be used on closure parameters to functions. This indicates that the parameter is only ever called (or passed as an @noescape parameter in a call), which means that it cannot outlive the lifetime of the call. This enables some minor performance optimizations, but more importantly disables the self. requirement in closure arguments.

### rethrows/throws###

[TODO](https://www.jianshu.com/p/802ff8969952)

